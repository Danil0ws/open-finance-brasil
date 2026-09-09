# v.23.00.00 Jornada Otimizada em Transferências Inteligentes

# Visão geral

A **Jornada Otimizada** é uma experiência integrada que permite ao usuário, em um mesmo fluxo, autorizar a iniciação de pagamentos e o compartilhamento do saldo e limite da conta pagadora afim de dar suporte a esses pagamentos, respeitando que:

-   As autorizações continuam sendo gerenciadas de forma independente.
    
-   A experiência é apresentada ao usuário como parte natural da configuração do pagamento.
    

## Cancelamento de autorizações

O cancelamento segue o impacto esperado do ponto de vista do usuário:

-   O usuário pode interromper o compartilhamento de dados sem cancelar a autorização de pagamento.
    
-   Ao cancelar a autorização de pagamento, o compartilhamento de dados associado deixa de fazer sentido e deve ser cancelado automaticamente.
    

wide760

**Nota**

Caso o usuário cancele o compartilhamento de saldo e limite e deseje posteriormente compartilhar seus dados da conta, será necessário compartilhar seus dados através da jornada completa de **Compartilhamento de Dados** para que a ITP volte a ter acesso a essas informações.

wide760

**Nota**

Consulte a página **Gestão de Transferências Inteligentes** para informações sobre a gestão das autorizações de pagamento e dos compartilhamentos de saldo e limite da conta pagadora concedidos via Jornada Otimizada.

# Fluxos de telas

Os fluxos a seguir ilustram **onde e como** a **Jornada Otimizada** se integra à jornada de **Transferências Inteligentes****,** sem substituir os fluxos completos já descritos nas páginas específicas.

wide760

**Nota**  
Nas interfaces ilustrativas, a Instituição Iniciadora de Transação de Pagamento (ITP) é representada pela marca **Cloud Finance** e a Instituição Detentora de Conta (ID) é representada pela marca **Bratech**.

#### Jornada Otimizada em Transferências Inteligentes

![image-20260826-194429.png](images/image-20260826-194429.png)

# Requisitos e recomendações

Esta seção reúne os requisitos e recomendações aplicáveis ao compartilhamento de saldo e limite da conta pagadora via Jornada Otimizada durante a criação da autorização de pagamento com Transferências Inteligentes.

# Etapas da jornada

1.  Solicitação
    

3.  Confirmação
    

5.  Efetivação
    

wide760

Além dos requisitos e recomendações previstos nesta página, aplicam-se a esta jornada aqueles descritos em:

-   Transferências Inteligentes via hybrid flow;
    
-   Regulamentação e documentos do arranjo de pagamento vigentes.
    

# Etapa 1: Solicitação

760Resumo

Nesta etapa, o usuário:

-   Inicia a jornada de pagamento via Transferências Inteligentes com Pix.
    
-   Escolhe a Instituição Detentora da Conta (ID) que será usada para realizar as transferências.
    
-   Opcionalmente, autoriza o compartilhamento de saldo e limite da conta pagadora via Jornada Otimizada.
    
-   É informado sobre os gatilhos (manuais ou automáticos) que disparam as transferências conforme disponibilizado pela Instituição Iniciadora de Transação de Pagamento (ITP).
    
-   Se desejar, estabelece limites para as transferências .  
    
-   Revisa os dados configurados e visualiza as demais informações que compõem a autorização a ser enviada à ID.  
    

A Instituição Iniciadora de Transação de Pagamento (ITP) deve:

-   Garantir uma experiência clara, segura e informativa.
    
-   Indicar, em algum ponto da jornada, que o serviço é baseado em Open Finance.
    
-   Permitir a seleção eficiente da ID.
    
-   Validar os dados inseridos, ocultando informações sensíveis.
    
-   Preparar a solicitação de iniciação de pagamento para envio à ID.
    
-   Quando aplicável, exibir mensagens de erro claras ao usuário.
    

REQ.PG-02501 a 02503#F4F5F7

## Requisitos - ITP

**Cenário: Compartilhamento de saldo e limite via Jornada Otimizada**

-   `REQ.PG-02501` Permitir o compartilhamento opcional do saldo e limite da conta pagadora do usuário através da Jornada Otimizada.
    
-   `REQ.PG-02502` Exibir a opção de compartilhamento de saldo e limite da conta pagadora desabilitada por padrão.
    
-   `REQ.PG-02503` Permitir que o usuário avance sem obrigá-lo a aceitar o compartilhamento do saldo e limite da conta pagadora através da Jornada Otimizada.
    

![image-20260623-172238.png](images/image-20260623-172238.png)REQ.PG-02504 a 02506

-   `REQ.PG-02504`, na tela de solicitação, que o saldo e o limite estão sendo compartilhados.
    
-   `REQ.PG-02505` Exibir, na tela de solicitação, o escopo dos dados compartilhados.​
    
-   `REQ.PG-02506` Não exibir qualquer aspecto que desvie o foco do usuário em concluir o compartilhamento de saldo e limite da conta pagadora através da Jornada Otimizada, como, por exemplo link, botão, imagem, texto, entre outros.
    

![image-20260623-172409.png](images/image-20260623-172409.png)

* * *

# Etapa 3: Confirmação

760Resumo

Nesta etapa, o usuário:

-   Se autentica na Instituição Detentora de Conta (ID).
    
-   Em caso de múltiplas contas de débito, pode escolher a que deseja usar para fazer o pagamento.
    
-   Revisa as informações da autorização de pagamento e do compartilhamento de saldo e limite da conta pagadora via Jornada Otimizada enviadas pela Instituição Iniciadora de Transação de Pagamento (ITP).
    
-   Confirma a autorização.  
    

A ID deve:

-   Garantir um ambiente seguro para autenticação.
    
-   Exibir o resumo da autorização com informação sobre o compartilhamento do saldo e limite da conta com a ITP.
    
-   Permitir a edição da conta de débito, em caso de múltiplas contas.
    
-   Viabilizar a confirmação com o mínimo de fricção.   
    
-   Quando aplicável, exibir mensagens de erro claras ao usuário.
    
-   Comunicar o resultado da autorização à ITP.
    
-   Enviar notificações ao usuário e, quando aplicável, aos demais aprovadores — em casos de múltiplas alçadas ou falha na conclusão da autorização.
    

REQ.PG-05802 a 05803#F4F5F7

## Requisitos - ID

**Cenário: Compartilhamento de saldo e limite via Jornada Otimizada**

-   `REQ.PG-05802` Informar, na tela de confirmação, que o saldo e o limite da conta estão sendo compartilhados.
    
-   `REQ.PG-05803` Exibir, na tela de confirmação, o escopo dos dados compartilhados.​
    

![image-20260623-172530.png](images/image-20260623-172530.png)

* * *

# Etapa 5: Efetivação

760Resumo

Nesta etapa final da jornada, o usuário:

-   É recebido no ambiente da Instituição Iniciadora de Transação de Pagamento (ITP) onde visualiza o resultado da autorização de pagamento e do compartilhamento de saldo e limite da conta pagadora via Jornada Otimizada.   
    

A ITP deve:

-   Apresentar com clareza o resultado da transação, com mensagens claras de sucesso ou falha.
    
-   Disponibilizar os detalhes da transação e acesso ao comprovante.  
    
-   Quando aplicável, exibir mensagens de erro ou pendências, como autorizações em múltiplas alçadas, transações temporizadas ou indisponibilidade momentânea dos sistemas.
    

wide760#F4F5F7

## Requisitos - ITP

**Cenário: Compartilhamento de saldo e limite via Jornada Otimizada**

REQ.PG-07804

-   `REQ.PG-07804` Informar que o saldo e o limite da conta pagadora estão sendo compartilhados.
    

REQ.PG-07805

-   `REQ.PG-07805` Informar que o compartilhamento de saldo e limite pode ser cancelado a qualquer momento na área de gestão. 
    
    Ex.: Acesse a área de gestão para encerrar o compartilhamento do saldo e limite a qualquer momento e manter a autorização ativa.
    

![image-20260826-191155.png](images/image-20260826-191155.png)true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Transferências Inteligentes

**Jornada**

Jornada Otimizada

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Transparência e clareza, Conveniência e controle, Segurança e privacidade - IN BCB 760

**ID**

`REQ.PG-02501`

**Texto**

Permitir o compartilhamento opcional do saldo e limite da conta pagadora do usuário através da Jornada Otimizada.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Transferências Inteligentes

**Jornada**

Jornada Otimizada

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Transparência e clareza, Conveniência e controle, Segurança e privacidade - IN BCB 760

**ID**

`REQ.PG-02502`

**Texto**

Manter a opção de compartilhamento de saldo e limitea conta pagadora através da Jornada Otimizada desabilitada por padrão.​

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Transferências Inteligentes

**Jornada**

Jornada Otimizada

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Transparência e clareza, Conveniência e controle, Segurança e privacidade - IN BCB 760

**ID**

`REQ.PG-02503`

**Texto**

Permitir que o usuário avance sem obrigá-lo a aceitar o compartilhamento do saldo e limite da conta pagadora através da Jornada Otimizada.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Transferências Inteligentes

**Jornada**

Jornada Otimizada

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Transparência e clareza, Conveniência e controle, Segurança e privacidade - IN BCB 760

**ID**

`REQ.PG-02504`

**Texto**

Informar, na tela de solicitação, que o saldo e o limite estão sendo compartilhados.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Transferências Inteligentes

**Jornada**

Jornada Otimizada

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Transparência e clareza, Conveniência e controle, Segurança e privacidade - IN BCB 760

**ID**

`REQ.PG-02505`

**Texto**

Exibir, na tela de solicitação, o escopo dos dados compartilhados.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Transferências Inteligentes

**Jornada**

Jornada Otimizada

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Transparência e clareza, Conveniência e controle, Segurança e privacidade - IN BCB 760

**ID**

`REQ.PG-02506`

**Texto**

Não exibir qualquer aspecto que desvie o foco do usuário em concluir o compartilhamento de saldo e limite da conta pagadora através da Jornada Otimizada, como, por exemplo link, botão, imagem, texto, entre outros.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Transferências Inteligentes

**Jornada**

Jornada Otimizada

**Proposta**

**Instituição**

ID

**Justificativa**

Experiência do usuário, Transparência e clareza, Conveniência e controle, Segurança e privacidade - IN BCB 760

**ID**

`REQ.PG-05802`

**Texto**

Informar, na tela de confirmação, que o saldo e o limite da conta estão sendo compartilhados.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Transferências Inteligentes

**Jornada**

Jornada Otimizada

**Proposta**

**Instituição**

ID

**Justificativa**

Experiência do usuário, Transparência e clareza, Conveniência e controle, Segurança e privacidade - IN BCB 760

**ID**

`REQ.PG-05803`

**Texto**

Exibir, na tela de confirmação, o escopo dos dados compartilhados.​

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Transferências Inteligentes

**Jornada**

Jornada Otimizada

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Transparência e clareza, Conveniência e controle, Segurança e privacidade - IN BCB 760

**ID**

`REQ.PG-07804`

**Texto**

Informar que o saldo e o limite da conta pagadora estão sendo compartilhados.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Transferências Inteligentes

**Jornada**

Jornada Otimizada

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Transparência e clareza, Conveniência e controle, Segurança e privacidade - IN BCB 760

**ID**

`REQ.PG-07805`

**Texto**

Informar que o compartilhamento de saldo e limite pode ser cancelado a qualquer momento na área de gestão.
