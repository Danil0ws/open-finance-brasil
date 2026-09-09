# v.23.00.00 Jornada Otimizada em Vinculação de Conta (JSR)

# Visão geral

A **Jornada Otimizada** é uma experiência integrada que permite ao usuário, em um mesmo fluxo, autorizar a vinculação de conta, na ITP, e o compartilhamento do saldo e limite da conta pagadora (ID) afim de dar suporte a esses pagamentos, respeitando que:

-   As autorizações continuam sendo gerenciadas de forma independente.
    
-   A experiência é apresentada ao usuário como parte natural da configuração do pagamento.
    

## Cancelamento de autorizações

O cancelamento segue o impacto esperado do ponto de vista do usuário:

-   O usuário pode interromper o compartilhamento de dados sem cancelar o vínculo de conta existente.
    
-   Ao cancelar o vínculo de conta, o compartilhamento de dados associado deixa de fazer sentido e deve ser cancelado automaticamente.
    

wide760

**Nota**

Se o usuário cancelar o compartilhamento de saldo e limite concedido via Jornada Otimizada e desejar posteriormente compartilhar seus dados da conta utilizada para pagamento, ele deverá compartilhar seus dados através da jornada completa de **Compartilhamento de Dados** para que a ITP volte a ter acesso a essas informações.

wide760

**Nota**

Consulte a página **Gestão de Vinculação de Conta (JSR)** para informações sobre a gestão das vinculações de conta e dos compartilhamentos de saldo e limite da conta pagadora concedidos via Jornada Otimizada.

# Fluxos de telas da Jornada Otimizada

Os fluxos a seguir ilustram **onde e como** a **Jornada Otimizada** se integra à jornada de **Vinculação de Conta**, sem substituir os fluxos completos já descritos nos capítulos específicos.

wide760

**Nota**  
Nas interfaces ilustrativas, a Instituição Iniciadora de Transação de Pagamento (ITP) é representada pela marca **Cloud Finance** e a Instituição Detentora de Conta (ID) é representada pela marca **Bratech**.

**Jornada Otimizada** **em Vinculação de Conta**

![image-20260220-205450.png](images/image-20260220-205450.png)

* * *

# Requisitos e recomendações

Esta seção reúne os requisitos e recomendações aplicáveis ao compartilhamento de saldo e limite da conta pagadora via Jornada Otimizada durante a Vinculação de Conta.

# Etapas da jornada

1.  Solicitação
    

3.  Confirmação
    

5.  Efetivação
    

## Cenário de referência

-   Vinculação de Conta imediata entre ITP, dispositivo e ID com compartilhamento de saldo e limite da conta pagadora.
    
-   Alçada simples.
    
-   Redirecionamento entre instituições no mesmo dispositivo.
    

> Jornadas que envolvam troca de dispositivo devem observar as regras específicas previstas nas páginas correspondentes.

wide760

Além dos requisitos e recomendações previstos nesta página, aplicam-se a esta jornada aqueles descritos em:

-   Vinculação de Conta (JSR);
    
-   Regulamentação e documentos do arranjo de pagamento vigentes.
    

# Etapa 1: Solicitação

760Resumo-   Nesta etapa, o usuário:
    
    -   Inicia a jornada de vinculação de conta na Instituição Iniciadora de Transação de Pagamento (ITP).
        
    -   Escolhe a Instituição Detentora de Conta (ID) que será utilizada para realizar os pagamentos sem redirecionamento.  
        
    -   Opcionalmente, autoriza o compartilhamento de saldo e limite da conta pagadora via Jornada Otimizada.
        
    -   Revisa os dados configurados e visualiza as demais informações que compõem a solicitação a ser enviada à ID.  
        
    
    A ITP deve:
    
    -   Garantir uma experiência clara, segura e informativa.
        
    -   Indicar, em algum ponto da jornada, que o serviço é baseado em Open Finance.
        
    -   Permitir a seleção eficiente da ID.
        
    -   Validar os dados inseridos, ocultar informações sensíveis.
        
    -   Preparar a solicitação de vinculação de conta para envio à ID.
        
    -   Quando aplicável, exibir mensagens de erro claras ao usuário. REQ.VC-00700 a 01100#F4F5F7

## Requisitos - ITP

**Cenário: Compartilhamento de saldo e limite via Jornada Otimizada**

-   `REQ.VC-00700` Permitir o compartilhamento opcional do saldo e limite da conta pagadora do usuário através da Jornada Otimizada.
    
-   `REQ.VC-00800` Exibir a opção de compartilhamento de saldo e limite da conta pagadora desabilitada por padrão.
    
-   `REQ.VC-00900` Informar, na tela de solicitação, que o saldo e o limite estão sendo compartilhados.
    
-   `REQ.VC-01000` Exibir, na tela de solicitação, o escopo dos dados compartilhados.​
    
-   `REQ.VC-01100` Não exibir qualquer aspecto que desvie o foco do usuário de confirmar o compartilhamento de saldo e limite da conta de débito, como, por exemplo link, botão, imagem, texto, entre outros.
    

![image-20260610-184136.png](images/image-20260610-184136.png)

* * *

# Etapa 3: Confirmação

760Resumo

Nesta etapa, o usuário:

-   Se autentica na Instituição Detentora de Conta (ID).
    
-   Em caso de múltiplas contas de débito, pode escolher a que deseja vincular.
    
-   Revisa as informações do vínculo enviadas pela Instituição Iniciadora de Transação de Pagamento (ITP).
    
-   Confirma a vinculação.  
    

A ID deve:

-   Garantir um ambiente seguro para autenticação.
    
-   Exibir o resumo da vinculação com informação sobre o compartilhamento do saldo e limite da conta com a ITP.
    
-   Permitir a edição da conta de débito, em caso de múltiplas contas.
    
-   Viabilizar a confirmação com o mínimo de fricção.   
    
-   Quando aplicável, exibir mensagens de erro claras ao usuário.
    
-   Comunicar o resultado da autorização à ITP.
    

REQ.VC-05600 a 05700#F4F5F7

## Requisitos - ID

**Cenário: Compartilhamento de saldo e limite da conta via Jornada Otimizada**

-   `REQ.VC-05600` Informar, na tela de confirmação, que o saldo e o limite da conta estão sendo compartilhados.
    
-   `REQ.VC-05700` Exibir, na tela de confirmação, o escopo dos dados compartilhados.​
    

![image-20260713-173200.png](images/image-20260713-173200.png)

* * *

# Etapa 5: Efetivação

760Resumo

Nesta etapa final da jornada, o usuário:

-   É recebido no ambiente da Instituição Iniciadora de Transação de Pagamento (ITP) onde visualiza o resultado da vinculação de conta e do compartilhamento de saldo e limite da conta pagadora via Jornada Otimizada.   
    

A ITP deve:

-   Apresentar com clareza o resultado da transação, com mensagens claras de sucesso ou falha.
    
-   Disponibilizar os detalhes da transação e acesso ao comprovante.  
    
-   Quando aplicável, exibir mensagens de erro ou pendências, como autorizações em múltiplas alçadas, transações temporizadas ou indisponibilidade momentânea dos sistemas.
    

#F4F5F7

## Requisitos - ITP

**Cenário: Compartilhamento do saldo e limite da conta via Jornada Otimizada**

-   `REQ.VC-07100` Informar que o compartilhamento de saldo e limite pode ser cancelado a qualquer momento na área de gestão. 
    
-   `REQ.VC-07200` Informar que o cancelamento do compartilhamento de saldo e limite não cancela o vínculo de conta.
    
-   `REQ.VC-07300` Informar que o cancelamento do vínculo também cancela o compartilhamento de saldo e limite.
    

![image-20260624-171913.png](images/image-20260624-171913.png)true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Jornada Otimizada em Vinculação de Conta (JSR)

**Jornada**

Hybrid flow e hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

IN BCB 760

**ID**

`REQ.VC-00700`

**Texto**

Permitir o compartilhamento opcional do saldo e limite da conta pagadora do usuário através da Jornada Otimizada.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Jornada Otimizada em Vinculação de Conta (JSR)

**Jornada**

Hybrid flow e hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

IN BCB 760

**ID**

`REQ.VC-00800`

**Texto**

Exibir a opção de compartilhamento de saldo e limite da conta pagadora desabilitada por padrão.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Jornada Otimizada em Vinculação de Conta (JSR)

**Jornada**

Hybrid flow e hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

IN BCB 760

**ID**

`REQ.VC-00900`

**Texto**

Informar, na tela de solicitação, que o saldo e o limite estão sendo compartilhados.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Jornada Otimizada em Vinculação de Conta (JSR)

**Jornada**

Hybrid flow e hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

IN BCB 760

**ID**

`REQ.VC-01000`

**Texto**

Exibir, na tela de solicitação, o escopo dos dados compartilhados.​

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Jornada Otimizada em Vinculação de Conta (JSR)

**Jornada**

Hybrid flow e hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

IN BCB 760

**ID**

`REQ.VC-01100`

**Texto**

Não exibir qualquer aspecto que desvie o foco do usuário de confirmar o compartilhamento de saldo e limite da conta de débito, como, por exemplo link, botão, imagem, texto, entre outros.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Jornada Otimizada em Vinculação de Conta (JSR)

**Jornada**

Hybrid flow e hybrid flow com hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

IN BCB 760

**ID**

`REQ.VC-05600`

**Texto**

Informar, na tela de confirmação, que o saldo e o limite da conta estão sendo compartilhados.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Jornada Otimizada em Vinculação de Conta (JSR)

**Jornada**

Hybrid flow e hybrid flow com hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

IN BCB 760

**ID**

`REQ.VC-05700`

**Texto**

Exibir, na tela de confirmação, o escopo dos dados compartilhados.​

trueListe as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Jornada Otimizada em Vinculação de Conta (JSR)

**Jornada**

Hybrid flow e hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

IN BCB 760

**ID**

`REQ.VC-07100`

**Texto**

Informar que o compartilhamento de saldo e limite pode ser cancelado a qualquer momento na área de gestão. true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Jornada Otimizada em Vinculação de Conta (JSR)

**Jornada**

Hybrid flow e hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

IN BCB 760

**ID**

`REQ.VC-07200`

**Texto**

Informar que o cancelamento do compartilhamento de saldo e limite não cancela o vínculo de conta.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Jornada Otimizada em Vinculação de Conta (JSR)

**Jornada**

Hybrid flow e hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

IN BCB 760

**ID**

`REQ.VC-07300`

**Texto**

Informar que o cancelamento do vínculo também cancela o compartilhamento de saldo e limite.
