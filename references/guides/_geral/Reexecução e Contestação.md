# Reexecução e Contestação

Antes de abrir o ticket de reexecução ou contestação, é importante realizar as seguintes verificações e ações:

1.  Acesse o ticket e baixe os logs/evidências disponíveis.
    
2.  Analise a ocorrência para identificar a origem da falha.
    
3.  Verifique se o problema está relacionado à aplicação, integração ou processamento sob responsabilidade da sua equipe.
    
4.  Avalie se houve interferência externa, erro operacional ou inconsistência na execução.
    
5.  Após a análise, utilize a matriz de decisão abaixo para definir a ação adequada.
    

## **Como decidir a ação correta?**

Problema identificado

Análise / Critério

Ação

Falha relacionada à aplicação

A análise dos logs indica falha no comportamento da aplicação, erro de implementação ou integração, processamento fora do esperado ou algum problema interno no ambiente (ex.: solicitação de deleção de client).

Corrigir o problema internamente e solicitar a reexecução por meio de um ticket.

Falha não relacionada à aplicação

A análise indica que a falha ocorreu por um problema na ferramenta, execução ou por alguma condição externa à aplicação. Exemplos: PF/PJ indefinido, AS ID/marca incorretos, conta credora incorreta, saldo insuficiente de forma inconsistente, evidências inadequadas ou divergência nos critérios de execução.

Abrir um ticket de contestação, informando as referências necessárias e classificando a ocorrência como técnica ou operacional.

## **Ticket de Reexecução**

Conforme citado acima, solicite a **reexecução** quando a falha estiver relacionada à **implementação, integração ou ambiente da instituição**. Antes da solicitação, o problema deve ser **corrigido e validado internamente**.

**Importante:** O SLA do ticket de notificação permanece pausado até a conclusão da reexecução.

**Exemplos de situações que podem exigir reexecução:**

-   **Erro de implementação/integração:** Necessária reexecução devido a falha na integração entre sistemas durante a implantação.
    
-   **Processamento fora do esperado:** Necessária reexecução devido a inconsistência identificada: ex. quando a API espera que a resposta seja 201 e obtém o retorno 400. (para conferir quais Clients não devem ser deletados, consulte a página de especificações de APIs)
    
-   Status de pagamento fora do esperado: “ACSC (1° Etapa), SCHD, PDNG, ACPD, ACCP, CANC e RCVD” ..
    
-   Deleção acidental de client vinculado aos Software Statements. (para conferir quais Clients não devem ser deletados, consulte a página Deleção de Client).
    

A correção foi aplicada pela instituição e validada internamente, e o ambiente encontra-se pronto para uma nova validação. Dessa forma, prosseguir com a abertura do ticket de reexecução.

## **Como abrir um ticket de reexecução ?**

**Caminho no** [Service Desk](https://servicedesk.openfinancebrasil.org.br/Login.jsp?navLanguage=pt-BR)**:**

**Ação**

**Caminho Exato**

Reexecução

Requisição > Reexecução > FVP Manual – Testes Restritos

![att\_0\_for\_2065040244.png](images/att_0_for_2065040244.png)

**Para o preenchimento do formulário de reexecução, siga as orientações abaixo:**

-   Instituição Requerente: _Identificação da instituição_
    
-   Título: _Solicitação de Reexecução - Ticket FVP #123_
    
-   Número do ticket gerado pela FVP: _#123 ( obs: Utilize o número do ticket da FVP relacionado à desconformidade que está sendo contestada ou seja ticket da notificação original)_
    
-   Descrição da solicitação: _**Ref. Ticket #123.** A instituição corrigiu a inconsistência identificada e realizou validações internas com sucesso. O ambiente está pronto para nova validação. Solicito a reexecução do módulo de teste._
    

Conforme o print do formulário de abertura abaixo:

![att\_1\_for\_2065040244.png](images/att_1_for_2065040244.png)

Após a abertura do ticket de reexecução, o SLA do ticket de notificação original será pausado, permanecendo no status "Aguardando Reexecução/Contestação" até a conclusão da nova execução pelo fornecedor de testes. O resultado dessa nova execução determinará o próximo passo do processo

## **Resultados da Contestação**

-   **Teste imediato/curta duração:**
    

**Sucesso:** A reexecução confirmou a regularização da não conformidade reportada. Será incluída uma nota no ticket de notificação original, com as evidências de sucesso anexadas, e o chamado será atualizado para o status **Atendimento Encerrado.**

**Falha: (Não Conformidade Mantida):** A reexecução confirmou a persistência da não conformidade reportada. O ticket de reexecução será encerrado e o ticket de notificação original retomará a contagem do SLA. A instituição deverá analisar o cenário, realizar as correções necessárias e, conforme aplicável, solicitar uma nova reexecução ou abrir um ticket de contestação.

-   **Teste de longa duração:**
    

**Sucesso (Conformidade Validada):**Em testes de longa duração, a primeira etapa será registrada no ticket de reexecução. As etapas seguintes serão processadas automaticamente, conforme aplicável. O resultado da validação somente poderá ser determinado após a conclusão de todas as etapas previstas. Sucessos parciais não encerram o ticket. Após a conclusão do fluxo e a validação da conformidade, será registrada uma nota no ticket de notificação original com as evidências de sucesso, e o chamado será atualizado para o status **Atendimento Encerrado**.

**Falha (Não Conformidade Mantida):**Em testes de longa duração, a falha somente poderá ser confirmada após a conclusão de todas as etapas previstas no fluxo. Caso a não conformidade persista, o ticket de reexecução será encerrado, o ticket de notificação original retomará a contagem do SLA e a instituição deverá realizar as correções necessárias, solicitando nova reexecução ou contestação, quando aplicável.

## **Testes de Longa Duração**

Nos ciclos da FVP Manual – Testes Restritos, alguns cenários são classificados como Testes de Longa Duração. Quando uma falha é identificada, um ticket é encaminhado à instituição com as evidências da execução. Nesses casos, o encerramento do ticket depende da obtenção de uma reexecução bem-sucedida realizada pelo fornecedor de testes em suas etapas.

Aqui estão exemplos de módulo de teste de longa duração: _credit-portability\_api\_accepted\_settlement; payments\_api\_automatic-pix-scheduling; automatic-payments\_api\_automatic-pix-scheduling; automatic-payments\_api\_automatic-pix-scheduling-retry; automatic-payments\_api\_automatic-pix-verification;_

wide760

**Importante:** Antes de solicitar uma Reexecução ou Contestação relacionada a esse tipo de cenário, consulte a página Fluxo de Ticket - Testes de longa Duração para verificar as particularidades e critérios aplicáveis ao processo.

Em casos de problemas em testes de longa duração, verifique se houve a exclusão inadvertida de **clients vinculados aos Software Statements**. Se confirmado, o client correspondente também deverá ser excluído na ferramenta FVP. Para mais informações, consulte a página Deleção de Clients.

## **Ticket de Contestação**

A contestação deve ser utilizada quando a instituição identificar indícios de que a falha não foi causada por sua implementação e desejar uma revisão do resultado.

As solicitações passam por uma análise especializada para validação das evidências apresentadas.

### **Direcionamento da análise**

**Erro Técnico**  
Quando houver indícios de falha na ferramenta de validação ou comportamento da suíte de testes, o chamado será direcionado para a fila **N2 – Conformance Suite** para investigação técnica.

**Erro Operacional**  
Quando houver indícios de falha ocorrida durante a execução dos testes ou no processo de notificação, o chamado será direcionado para a fila **N3 (Fornecedores de Testes)**, categorizado como **Erro Operacional**.

### **Exemplos de Erro Técnico**

-   **Falso negativo:** o teste indica falha, mas as evidências demonstram que o comportamento da instituição ocorreu conforme esperado, não era para ter falhado.
    
-   Inconsistências na ferramenta de certificação: Fornecer uma resposta correta, conforme solicitado pela documentação oficial, mas a ferramenta indicar que ela está incorreta.
    

### **Exemplos de Erro Operacional**

-   **Erro operacional na execução ou no processo de notificação:** execução incorreta do cenário, configuração inadequada do teste ou comunicação equivocada do resultado
    
-   **Utilização de dados incorretos no cenário de validação:** uso de informações inválidas ou divergentes do cenário previsto, comprometendo o resultado da validação.
    

**Atenção:** É fundamental selecionar a categoria correta ao abrir o chamado no Service Desk. Isso garante o direcionamento adequado da solicitação e evita encerramentos indevidos ou atrasos no atendimento. Caso tenha alguma dúvida sobre os erros tecnicos e operacionais, ou queira ver mais exemplos, consulte a nossa página de Link: _**Erros comuns**_

## **Como abrir um ticket de contestação ?**

Antes de registrar a solicitação, recomenda-se que a instituição realize as seguintes verificações:

-   Analise as evidências recebidas junto à notificação da desconformidade;
    
-   Valide os logs, payloads e respostas envolvidos na execução do cenário;
    
-   Reproduza internamente o cenário reportado para confirmar o comportamento observado; _exceto testes de longa duração_.
    
-   Compare o comportamento obtido internamente com o comportamento reportado pelo fornecedor de testes; _exceto testes de longa duração_.
    
-   Reúna evidências que sustentem tecnicamente a contestação, como logs, capturas de tela, Payloads ou referências da especificação aplicável.
    

wide760

**Importante:** Contestações acompanhadas de evidências objetivas e análises prévias tendem a permitir uma avaliação mais rápida e assertiva da solicitação.

Feita a análise e confirmada a divergência identificada, prosseguir com a abertura do ticket de contestação.

**Caminho no** [Service Desk](https://servicedesk.openfinancebrasil.org.br/Login.jsp?navLanguage=pt-BR)**:**

**Ação**

**Caminho Exato**

Contestação

Requisição > Contestação > FVP Manual – Testes Restritos

![att\_2\_for\_2065040244.png](images/att_2_for_2065040244.png)

**Para o preenchimento do formulário de reexecução, siga as orientações abaixo:**

-   **Instituição Requerente:** _Identificação da instituição_
    
-   **Título:** _Solicitação de Reexecução - Ticket FVP #123_
    
-   **Número do ticket para contestação:** _#123 ( obs: Utilize o Número do ticket para contestação relacionado ao ticket da notificação original)_
    
-   **Motivo da Contestação:**
    
-   **Erro Operacional: “**Selecione esta opção quando a contestação estiver relacionada à execução do teste ou ao processo de abertura do ticket de notificação.”
    

**Exemplo de descrição:**

_A execução está com parâmetros diferentes dos previstos para a validação. As evidências anexadas demonstram divergência entre os dados utilizados no teste e os dados esperados para o cenário._

-   **Erro Técnico: “**Selecione esta opção quando houver indícios de comportamento incorreto da ferramenta ou dos mecanismos de validação.”
    

**Exemplo de descrição:**

_A instituição reproduziu o cenário internamente e obteve resultado aderente à especificação. As evidências anexadas indicam possível falso negativo durante a validação._

-   **Descrição da solicitação:** _“Evidências do ticket #123 mostram AS ID incorreto; logs internos comprovam processamento correto."_
    
-   **Anexos:** _Evidências Comprovatórias: Logs internos da aplicação; Prints de reprodução; Payloads/respostas API; Comparativo: "Teste reportou X, mas sistema retornou Y";_
    

_“A qualidade das evidências determina o sucesso. Estrutura analisa com base nisso, sem provas técnicas, contestação é rejeitada”._

formulário de abertura abaixo:

![att\_3\_for\_2065040244.png](images/att_3_for_2065040244.png)

Após a abertura do ticket de contestação, a solicitação é direcionada para a fila da Estrutura do Open Finance, responsável pela análise técnica do caso.

Essa etapa tem como objetivo avaliar a procedência da contestação de forma imparcial, com base nas evidências apresentadas e nos resultados obtidos durante a validação.

**Importante:** acompanhe o status do ticket durante a análise. Caso a contestação seja considerada improcedente, o SLA do ticket original será retomado.

## **Resultados da Contestação**

A decisão é comunicada no ticket de contestação:

**Resultado**

**Significado**

**Próximo Passo**

**Procedente**

A falha reportada não é de responsabilidade da instituição, caracterizando, por exemplo, um falso negativo ou problema no processo de validação.

Encerramento do ticket original;

Tratativa interna da ferramenta, execução ou processo de validação.

**Improcedente**

A análise confirma que a falha reportada é válida e de responsabilidade da instituição.

Realizar os ajustes necessários; solicitar a reexecução do teste; O SLA do ticket original volta a ser contabilizado.

**Importante:**

Se a contestação estiver vinculada a um ticket original e for necessário seguir com nova validação, será aberto um ticket de reexecução como "nova execução" associado ao ticket original e encaminhá-lo para a fila do fornecedor de testes. O ticket de contestação, nesse caso, é encerrado.

**Considerações Críticas**

-   **Classificação adequada:** a categorização como erro técnico ou operacional influencia diretamente a equipe responsável, a priorização e o tempo de atendimento.
    
-   **Qualidade das evidências:** evidências claras e consistentes aceleram a análise e reduzem retrabalho.
    
-   **Escopo de aplicação:** o processo de contestação aplica-se exclusivamente aos Testes Restritos. Para Testes Abertos, a correção deve ser tratada internamente pela instituição.
    

# **Ficou com dúvida?**

Caso a instituição:

-   Tenha dúvidas sobre qual fluxo utilizar;
    
-   Necessite orientação antes de abrir uma Reexecução ou Contestação;
    
-   Identifique um comportamento não previsto na documentação;
    
-   Deseje esclarecer questões relacionadas ao processo de certificação;
    

Deve abrir uma **Solicitação de Informação** pelos canais oficiais de atendimento: Solicitação de Serviço → Solicitação de Informações → Conformidade → Ferramenta de Validação em Produção.

Para mais informações, consulte a nossa página Dúvidas comuns.

As informações contidas neste documento estão fundamentadas na [Instrução Normativa BCB nº 588](data/references/Instrução_Normativa_BCB_588.md), de 31 de janeiro de 2025, publicada pelo Banco Central do Brasil, e refletem as orientações vigentes relacionadas aos serviços e processos da Estrutura de Governança do Open Finance.

## Fluxo de Contestação:

![att\_2\_for\_2064581488.jpeg](images/att_2_for_2064581488.jpeg)

## Fluxo de Reexecução:

![att\_3\_for\_2064581488.jpeg](images/att_3_for_2064581488.jpeg)
