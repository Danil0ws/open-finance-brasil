# Campo dropReason — Documentação Funcional para Organizações

v 1.0

## **Objetivo**

Este documento descreve a definição funcional, os valores aceitos e as regras de classificação do campo `dropReason` no contexto do reporte de monitoramento da PCM (Plataforma de Coleta de Métricas) do Open Finance Brasil.

Destina-se às **organizações participantes** que atuam no papel SERVER e são responsáveis por reportar o motivo pelo qual um fluxo de consentimento não foi concluído com sucesso (drop).

## **Escopo**

**Regulação aplicável:** IN BCB nº 706, §2.6.2

**Papel responsável pelo reporte:** SERVER (detentora)

## **O que é o dropReason**

O campo `dropReason` indica o **motivo pelo qual um fluxo de consentimento foi interrompido antes da aprovação**, sob a perspectiva da detentora de conta (papel SERVER).

Ele classifica o desfecho do fluxo em função do **estado da credencial e das alçadas do usuário** no momento da tentativa, permitindo ao ecossistema distinguir:

-   Abandono voluntário (credencial apta)
    
-   Ausência de relacionamento (não-cliente)
    
-   Indisponibilidade de credencial (cliente sem acesso temporário)
    
-   Falta de poderes ou identidade divergente
    

O `dropReason` **não** se destina a registrar falhas técnicas de infraestrutura, erros de payload ou estados intermediários de processamento.

## **Valores Aceitos**

Valor

Definição

Classificação

`NONE`

Credencial verificada e apta, alçadas suficientes. O drop ocorreu por outra razão — abandono, expiração de sessão, desistência voluntária do usuário.

Cliente

`NO_CREDENTIAL`

Consulta à base confirmou que o CPF/CNPJ **não possui** credencial autenticadora cadastrada. Ausência comprovada de vínculo — trata-se de não-cliente nos termos da IN 706, §2.6.2.

Não-cliente

`CREDENTIAL_UNAVAILABLE`

O CPF/CNPJ é cliente e possui credencial cadastrada, mas ela está **temporariamente indisponível** para uso, ou uma falha técnica impediu a verificação do estado da credencial havendo indício de vínculo com a instituição.

Cliente

`NO_AUTHORITY`

Credencial verificada com sucesso, porém o titular não possui poderes ou alçadas suficientes para a operação solicitada naquele contexto.

Cliente

`NO_AUTHORITY_PERSON_MISMATCH`

A identidade autenticada diverge da identidade vinculada ao consentimento. Aplicável ao Hybrid Flow (fluxo com redirecionamento).

Cliente

## **Definição Detalhada por Valor**

**NONE**

Indica que a credencial do usuário foi verificada, está ativa e funcional, e que o titular possui alçadas adequadas para a operação — porém o fluxo não foi concluído. O drop decorreu de fatores como:

-   Abandono voluntário (fechou a tela, voltou ao iniciador)
    
-   Expiração de sessão sem interação
    
-   Desistência após visualizar termos ou dados
    
-   Timeout de inatividade
    

Regra: só deve ser utilizado quando a verificação de credencial e alçadas foi concluída com sucesso.

**NO\_CREDENTIAL**

Indica que a consulta à base da instituição **confirmou positivamente** a inexistência de credencial autenticadora para o CPF/CNPJ informado. Representa não-cliente.

Condições obrigatórias para uso:

-   A base de credenciais foi consultada com sucesso
    
-   A resposta confirmou ausência de credencial cadastrada
    

A impossibilidade técnica de consultar a base **NÃO autoriza** o uso de `NO_CREDENTIAL`. Nunca presumir ausência — na dúvida, utilizar `CREDENTIAL_UNAVAILABLE`.

**CREDENTIAL\_UNAVAILABLE**

Indica que o CPF/CNPJ possui vínculo com a instituição (é cliente), mas a credencial não pôde ser utilizada no momento da tentativa. Abrange dois grandes grupos de situação:

**Grupo 1 — Credencial identificada mas indisponível:**

-   Bloqueio por excesso de tentativas
    
-   Bloqueio cautelar ou administrativo
    
-   Certificado digital / token de segurança expirado
    
-   Credencial inativada por inatividade prolongada
    
-   Pendência de KYC / recadastramento
    
-   Segundo fator (2FA) inacessível (dispositivo perdido, SMS não entregue, app não configurado)
    
-   Canal/dispositivo não autorizado para a operação (requer habilitação prévia)
    
-   Senha esquecida (credencial ativa mas inacessível sem fluxo de recuperação)
    

**Grupo 2 — Falha técnica com indício de cliente:**

-   Sistema de credenciais indisponível, mas há evidência de relacionamento (produto contratado, conta ativa, histórico de transações)
    
-   Timeout na consulta à base com indícios de vínculo
    

**Regra geral:** quando há dúvida entre `NO_CREDENTIAL` e `CREDENTIAL_UNAVAILABLE`, utilizar `CREDENTIAL_UNAVAILABLE`. Não presumir ausência.

**NO\_AUTHORITY**

Indica que a credencial foi verificada com sucesso (o usuário se autenticou), mas ele não possui poderes ou alçadas para a operação específica. Exemplos:

-   Usuário PF sem poder de representação para operação PJ
    
-   Aprovação pendente de segundo signatário (múltipla alçada PJ)
    
-   Perfil de acesso insuficiente para o tipo de consentimento
    

**NO\_AUTHORITY\_PERSON\_MISMATCH**

Indica que a pessoa que se autenticou no fluxo **não é a mesma** vinculada ao consentimento. Aplicável exclusivamente ao **Hybrid Flow** (com redirecionamento), onde a transmissora verifica a identidade após autenticação.

## **Hierarquia de Decisão**

O fluxo abaixo orienta a classificação correta:

![image-20260717-183838.png](images/image-20260717-183838.png)

## **Cenários de Fronteira — Classificação Padronizada**

Os cenários abaixo representam situações recorrentes com potencial de divergência interpretativa. A classificação é padronizada para garantir consistência entre organizações:

#

Cenário

Classificação

Justificativa

1

Falha técnica **após** autenticação bem-sucedida (ex.: timeout em etapa posterior à verificação de credencial)

Estado real apurado (`NONE`, `NO_AUTHORITY` etc.)

A verificação de credencial foi concluída; o dropReason reflete o estado da credencial, não a falha técnica

2

Erro HTTP 4xx por payload mal formado (antes de qualquer lookup de credencial)

**Não gerar reporte de drop**

Não representa estado do usuário — é erro de integração

3

Cliente em processo de encerramento de relacionamento

`CREDENTIAL_UNAVAILABLE` se credencial suspensa pelo encerramento; estado real se credencial ainda funcional

Reflete o estado da credencial, não o status administrativo

4

CPF é representante legal de PJ mas não é cliente PF

Na jornada PF → `NO_CREDENTIAL`; na jornada PJ → conforme estado da credencial vinculada à PJ

O contexto da jornada define qual credencial é avaliada

5

Aprovação pendente de 2º signatário (múltipla alçada PJ)

`NO_AUTHORITY`

Poderes insuficientes para aprovação unilateral

6

Senha esquecida (cliente não consegue autenticar)

`CREDENTIAL_UNAVAILABLE`

Credencial existe e está ativa, mas inacessível sem recuperação

7

Dispositivo/canal não autorizado para a operação

`CREDENTIAL_UNAVAILABLE`

Credencial principal existe; canal específico requer habilitação adicional não satisfeita

## **Aplicabilidade por Fluxo**

Fluxo

Enums aplicáveis

Observação

**Redirect (Hybrid Flow)**

Todos os 5 valores

Cenário completo — inclui verificação de identidade

**Sem Redirecionamento**

`NONE`, `NO_CREDENTIAL`, `CREDENTIAL_UNAVAILABLE`, `NO_AUTHORITY`

Sem mismatch (identidade resolvida previamente)

**Pagamentos Automáticos**

`NONE`, `NO_CREDENTIAL`, `CREDENTIAL_UNAVAILABLE`, `NO_AUTHORITY`

Consentimento de longa duração

**CIBA (Desacoplado)**

`NONE`, `CREDENTIAL_UNAVAILABLE`

Consentimento vinculado a titular já identificado

## **Regras Gerais de Reporte**

#

Regra

Descrição

1

**Papel obrigatório**

O `dropReason` é reportado exclusivamente pelo papel SERVER (transmissora/detentora).

2

**Não presumir ausência**

Se não foi possível verificar a base de credenciais, nunca reportar `NO_CREDENTIAL`. Utilizar `CREDENTIAL_UNAVAILABLE`.

3

**Estado real pós-verificação**

Se a verificação de credencial foi concluída, reportar o estado real apurado — mesmo que haja falha técnica em etapa posterior.

4

**Falha técnica ≠ enum de drop**

Não existe enum de falha técnica. Indisponibilidades de infraestrutura são monitoradas por observabilidade (IN 706, §2.1), fora do escopo do `dropReason`.

5

**Payload inválido ≠ drop**

Erros de formação de payload (HTTP 4xx antes de lookup) não constituem drop e não devem gerar reporte.

6

**Um drop por tentativa**

Cada tentativa de consentimento gera no máximo um reporte de `dropReason`.

7

**Na dúvida, CREDENTIAL\_UNAVAILABLE**

Quando a classificação entre `NO_CREDENTIAL` e `CREDENTIAL_UNAVAILABLE` for ambígua, utilizar `CREDENTIAL_UNAVAILABLE`.

## **Referências Normativas**

Documento

Descrição

IN BCB nº 706, §2.6.2

Definição regulatória de cliente e credencial

IN BCB nº 706, §2.1

Observabilidade e disponibilidade de APIs

Swagger PCM (versão vigente)

Especificação técnica do campo `dropReason`

PAR-139 v3.4

Proposta de inclusão do `CREDENTIAL_UNAVAILABLE` e refinamento semântico

## **Histórico de Revisões**

Versão

Data

Descrição

1.0

17/07/2026

Versão inicial — documentação funcional completa do campo `dropReason`

_Este documento é parte da documentação funcional do Open Finance Brasil e deve ser utilizado como referência pelas organizações participantes para implementação e classificação correta do campo dropReason._
