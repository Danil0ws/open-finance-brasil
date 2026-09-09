# v.23.00.00 Pagamentos via CIBA

# Visão geral

CIBA (Client Initiated Backchannel Authentication ou Autenticação de Backchannel Iniciada pelo Usuário, em português), é um dos mais recentes padrões da OpenID Foundation. Serve para definir novos fluxos de autenticação e autorização, que são categorizados como “fluxo desacoplado”. Ele oferece novas formas de obter o consentimento do usuário final.

* * *

# Como funciona a jornada CIBA?

![image-20251022-202414.png](images/image-20251022-202414.png)

* * *

# Requisitos e recomendações de Pagamentos via CIBA

Esta seção reúne os requisitos e recomendações aplicáveis às jornadas de pagamento com Pix via Open Finance via CIBA.

## Etapas da jornada

1.  **Solicitação**
    

3.  **Confirmação**
    

**Nota**

Além dos requisitos e recomendações previstos neste capítulo, aplicam-se a esta jornada aqueles descritos em:

-   **Pix via Hybrid Flow****;**
    
-   **Pix com vencimento através de QR Code dinâmico via Hybrid Flow****;**
    
-   **Pix Agendado via Hybrid Flow****;**
    
-   **Pix Automático via Hybrid Flow****;**
    
-   **Pix Saque e Pix Troco via Hybrid Flow****;**
    
-   **Transferências Inteligentes via Hybrid Flow****;**
    
-   Regulamentação e documentos do arranjo de pagamento vigentes.
    

Em caso de conflito, prevalecem os requisitos e recomendações deste capítulo.

* * *

# Etapa 1: Solicitação

Solicitação de Iniciação de Transação de Pagamento na Instituição Iniciadora de Transação de Pagamento (ITP) para jornadas com CIBA.

**Nota**  
Estes requisitos tem o objetivo de, em uma compra futura, permitir que a Iniciadora de Pagamentos mostre a conta salva ao usuário, possibilitando uma jornada de confirmação de pagamento facilitada através do CIBA (_Client Initiated Backchannel Authentication_). O prazo de vencimento da autorização determinado pela Instituição Detentora de Conta por meio das regras previstas no manual de experiência tem extensão mínima de 6 meses, podendo ser indeterminado a depender da escolha da Instituição Detentora de Conta

REQ.PG-11500 a 11800#F4F5F7

## Requisitos - ITP

**Cenário: Pré-requisitos da jornada via CIBA**

-   `REQ.PG-11500` Permitir o salvamento prévio da origem de débito (conta) da Instituição Detentora de Conta na Instituição Iniciadora de Pagamento.
    
-   `REQ.PG-11600` Garantir que ambas as instituições envolvidas tenham suporte para CIBA.
    
-   `REQ.PG-11700` Antes do redirecionamento e da resposta da autorização do pagamento, apresentar ao usuário a possibilidade de “lembrar” esta Instituição para pagamentos futuros simplificados.
    
-   `REQ.PG-11800` Ao apresentar a possibilidade de salvar uma conta, explicar os benefícios da funcionalidade através de uma mensagem, respeitando o tom de voz de cada instituição.
    

![image-20260624-144430.png](images/image-20260624-144430.png)

REQ.PG-11900 a 12100

**Cenário: Solicitação de transação de pagamento via CIBA**

**Para jornadas nas quais sejam utilizadas contas previamente salvas com CIBA**

-   `REQ.PG-11900` Como não há redirecionamento automático em CIBA, não aplicar os requisitos das etapas de direcionamento e redirecionamento à jornada CIBA.
    
-   `REQ.PG-12000` Com exceção dos requisitos das etapas de direcionamento e redirecionamento e os requisitos confiltantes desta página, aplicar os demais requisitos das jornadas de pagamento à jornada CIBA.
    
-   `REQ.PG-12100` Caso exista, sempre permitir que o usuário possa selecionar outra forma de pagamento ou seguir o fluxo de Open Finance com outra Detentora de Conta.
    

![image-20260624-145210.png](images/image-20260624-145210.png)REQ.PG-12200 a 12400

-   `REQ.PG-12200` Após a escolha de uma ID salva, apresentar um aviso orientando sobre a necessidade de confirmação do pagamento na ID.
    
-   `REQ.PG-12300` Após a escolha de uma ID salva, apresentar um aviso informando que o usuário tem até 5 minutos para confirmar a operação.
    
-   `REQ.PG-12400` Após a escolha de uma ID salva, apresentar um aviso orientando o usuário a não fechar a tela de checkout da ITP.
    

![image-20260624-145039.png](images/image-20260624-145039.png)REC.PG-03900#F4F5F7

## Recomendações - ITP

**Cenário: Geral**

-   `REC.PG-03900` Apresentar ao usuário a possibilidade de pagamento mais rápido selecionando uma ID que já processou um pagamento anterior.
    

![image-20260624-145318.png](images/image-20260624-145318.png)

* * *

# Etapa 3: Confirmação

Confirmação do pagamento na Instituição Detentora de Conta (ID) para jornadas com CIBA.

REQ.PG-12500#F4F5F7

## Requisitos - ID

**Cenário: Revisão e confirmação de transação de pagamento via CIBA**

**Para jornadas nas quais sejam utilizadas contas previamente salvas com CIBA**

-   `REQ.PG-12500` Notificar o usuário sobre a pendência de pagamento pelo canal eletrônico padrão da instituição. Ex.: SMS, push, e-mail etc.
    

![image-20260624-150140.png](images/image-20260624-150140.png)REQ.PG-12600

-   `REQ.PG-12600` Ao clicar na notificação, possibilitar que o usuário continue a jornada no ambiente da Instituição Detentora de Conta.
    

REQ.PG-12700

-   `REQ.PG-12700` Após a autenticação, direcionar o usuário para a tela de confirmação do pagamento.
    

![image-20260624-150247.png](images/image-20260624-150247.png)

REQ.PG-12800

-   `REQ.PG-12800` Se, ao invés de clicar na notificação, o usuário acessar manualmente o canal digital da ID, sinalizar, com destaque, que há uma pendência de confirmação de pagamento.
    

![image-20260624-150457.png](images/image-20260624-150457.png)REQ.PG-12900

-   `REQ.PG-12900` Após a confirmação, orientar o usuário a voltar para a ITP para verificar a confirmação do pagamento.
    

![image-20260624-150427.png](images/image-20260624-150427.png)

**Nota**  
Lembramos a possibilidade de facilitar ainda mais a jornada com CIBA, permitindo que o usuário aprove a transação clicando na notificação e/ou usando a biometria do dispositivo e/ou capturando a identificação do dispositivo, a critério dos requisitos de segurança e autenticação da Detentora.    
Requisitos e recomendações referentes à gestão de contas salvas estão disponíveis em "Gestão de contas salvas em CIBA"

* * *

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Agendado, Pix Automático, Pix Saque e Pix Troco e Transferências Inteligentes

**Jornada**

CIBA

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.PG-11600`

**Texto**

Permitir o salvamento prévio da origem de débito (conta) da Instituição Detentora de Conta na Instituição Iniciadora de Pagamento.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Agendado, Pix Automático, Pix Saque e Pix Troco e Transferências Inteligentes

**Jornada**

CIBA

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.PG-11700`

**Texto**

Garantir que ambas as instituições envolvidas tenham suporte para CIBA.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Agendado, Pix Automático, Pix Saque e Pix Troco e Transferências Inteligentes

**Jornada**

CIBA

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.PG-11800`

**Texto**

Antes do redirecionamento e da resposta da autorização do pagamento, apresentar ao usuário a possibilidade de “lembrar” esta Instituição para pagamentos futuros simplificados.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Agendado, Pix Automático, Pix Saque e Pix Troco e Transferências Inteligentes

**Jornada**

CIBA

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.PG-11900`

**Texto**

Ao apresentar a possibilidade de salvar uma conta, explicar os benefícios da funcionalidade através de uma mensagem, respeitando o tom de voz de cada instituição.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Agendado, Pix Automático, Pix Saque e Pix Troco e Transferências Inteligentes

**Jornada**

CIBA

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.PG-12000`

**Texto**

Como não há redirecionamento automático em CIBA, não aplicar os requisitos das etapas de direcionamento e redirecionamento à jornada CIBA.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Agendado, Pix Automático, Pix Saque e Pix Troco e Transferências Inteligentes

**Jornada**

CIBA

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.PG-12100`

**Texto**

Com exceção dos requisitos das etapas de direcionamento e redirecionamento e os requisitos confiltantes desta página, aplicar os demais requisitos das jornadas de pagamento à jornada CIBA.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Agendado, Pix Automático, Pix Saque e Pix Troco e Transferências Inteligentes

**Jornada**

CIBA

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.PG-12200`

**Texto**

Caso exista, sempre permitir que o usuário possa selecionar outra forma de pagamento ou seguir o fluxo de Open Finance com outra Detentora de Conta.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Agendado, Pix Automático, Pix Saque e Pix Troco e Transferências Inteligentes

**Jornada**

CIBA

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.PG-12300`

**Texto**

Após a escolha de uma ID salva, apresentar um aviso orientando sobre a necessidade de confirmação do pagamento na ID.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Agendado, Pix Automático, Pix Saque e Pix Troco e Transferências Inteligentes

**Jornada**

CIBA

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.PG-12400`

**Texto**

Após a escolha de uma ID salva, apresentar um aviso informando que o usuário tem até 5 minutos para confirmar a operação.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Agendado, Pix Automático, Pix Saque e Pix Troco e Transferências Inteligentes

**Jornada**

CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.PG-12500`

**Texto**

Notificar o usuário sobre a pendência de pagamento pelo canal eletrônico padrão da instituição. Ex.: SMS, push, e-mail etc.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Agendado, Pix Automático, Pix Saque e Pix Troco e Transferências Inteligentes

**Jornada**

CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.PG-12600`

**Texto**

Ao clicar na notificação, possibilitar que o usuário continue a jornada no ambiente da Instituição Detentora de Conta.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Agendado, Pix Automático, Pix Saque e Pix Troco e Transferências Inteligentes

**Jornada**

CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.PG-12700`

**Texto**

Após a autenticação, direcionar o usuário para a tela de confirmação do pagamento.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Agendado, Pix Automático, Pix Saque e Pix Troco e Transferências Inteligentes

**Jornada**

CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.PG-12800`

**Texto**

Se, ao invés de clicar na notificação, o usuário acessar manualmente o canal digital da ID, sinalizar, com destaque, que há uma pendência de confirmação de pagamento.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Agendado, Pix Automático, Pix Saque e Pix Troco e Transferências Inteligentes

**Jornada**

CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.PG-12900`

**Texto**

Após a confirmação, orientar o usuário a voltar para a ITP para verificar a confirmação do pagamento.
