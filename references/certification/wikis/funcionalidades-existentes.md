# Funcionalidades existentes

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Funcionalidades-existentes](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Funcionalidades-existentes)
**Slug:** `Funcionalidades-existentes`

---


[TOC]

# Execução de um DCR ou utilização de um cliente existente

O Mock TPP pode executar um novo Registro Dinâmico de Cliente (DCR) ou usar um cliente existente fornecendo as informações necessárias.

![image](uploads/d41abd3da05c9872f40eadafa4077e70/image.png)

Se você quiser usar um cliente existente, você precisa preencher o 

- Client ID
- Registration Access Token

Depois de fazer um DCR com sucesso, as informações são armazenadas na sessão local do MongoDB. Mais tarde, pode-se acessá-la indo até "Use Existing Client Information" e vendo as IDs dos clientes.

![image](uploads/eccdc47d51eb3c0de2a601c2e1d1b1c4/image.png) 

Depois de fazer o DCR, você poderá ver mais detalhes sobre quais escopos foram concedidos:

![image](uploads/3d3abc324c7045050399d5a6e2e38a33/image.png)


# Payments - PIX

The Mock TPP currently supports both the regular PIX and PIX Scheduled Payments. It also allows multiple payments to be created against a given server and its status to be checked

[Gravamos um vídeo que explica como o Mock TPP lida com a Fase 3 de Pagamentos - PIX.](https://www.youtube.com/watch?v=RwtOiYdsNaQ)

**As macro etapas existentes para um fluxo de pagamento regular são:**

## Fluxo de pagamento regular
Ao executar o Mock TPP, você será capaz de criar pagamentos PIX que testam todo o processo. Você pode definir suas próprias informações de pagamento ou usar a informação padrão com a qual o Mock Bank foi predefinido. Em cada passo, o Mock TPP registra o que está fazendo, o que é mais fácil de seguir. Você também terá as respostas impressas na U.I. para que possa verificar o status final.


### Início da aplicação > Seleção de bancos > DCR

- Selecione Pagamentos no Menu Principal
- Pegar a lista de participantes que têm payments-consents registrados em seu tipo de Family Type (Back-End) 
- Exibir participantes - Permitir a busca e seleção de um participante (U.I.)
- Realizar um DCR com o participante selecionado (Back-End)
- Solicitar uma nova tela que mostre o ID do cliente para o participante selecionado (U.I)


### PIX Payment convencional

- Selecione Criar Pagamento no Menu Pagamentos (U.I)
- Digite as informações de pagamento necessárias e pressione criar pagamento (U.I)
- Chamar a API de Consentimento (Back-End)
- Exibir a tela à espera do consentimento a ser concedido (U.I.)
- Redirecionar para o A.S. selecionado e aguardar a concessão do Consentimento (Back-End)
- Pesquisa do API Consentimento - Verifique se o status mudou para consumido (Back-End)
- Chamar a API de pagamentos (Back-End)
- Pesquisar o API de pagamentos até que o status de pagamento mude para um estado aceito (Back-End)
- Exibição na tela TPP Mock The Payments/Consents Response or the Error Response (U.I.)
- Volte para o Menu Pagamentos e você poderá ver a Identificação de Consentimento, a Identificação de Pagamento e o Token de Atualização que foram gerados a partir do pagamento executado.


## Fluxo de pagamento PIX programado: 
O Mock TPP suporta pagamentos PIX programados e esta opção pode ser selecionada na visão Detalhes de Pagamento após selecionar Criar Pagamento no menu do Mock TPP. Há também a opção de verificar o status do pagamento após a criação de um pagamento

### Início da aplicação > Seleção de bancos > DCR

- Selecione Pagamentos no Menu Principal
- Recuperar do diretório a lista de participantes que têm pagamentos consentidos registrados em seu tipo de Família API (Back-End) 
- Exibir participantes - Permitir a busca e seleção de um participante (U.I.)
- Realizar um DCR com o participante selecionado (Back-End)
- Solicitar uma nova tela que mostre o ID do cliente para o participante selecionado


### Pagamentos programados

- Selecione Criar Pagamento no Menu Pagamentos (U.I)
- Insira as informações de pagamento necessárias e pressione "Yes" na opção Payment Schedule (U.I)
- Selecione a data de pagamento (Precisa ser D+1) e pressione "Create Payment" (U.I)
- Chamar a API de Consentimento (Back-End)
- Exibir a tela à espera do consentimento a ser concedido (U.I.)
- Redirecionar para o A.S. selecionado e aguardar a concessão do Consentimento (Back-End)
- Pesquisa do API Consentimento - Verifique se o status mudou para consumido (Back-End)
- Chamar a API de pagamentos (Back-End)
- Pesquisa do API de Pagamentos até que o status de Pagamento mude para um SASC (programado) (Back-End)
- Exibição na tela TPP Mock The Payments/Consents Response or the Error Response (U.I.)
- Volte para o Menu Pagamentos e você poderá ver a Identificação de Consentimento, a Identificação de Pagamento e o Token de Atualização que foram gerados a partir do pagamento executado (U.I.)
- Pressione Verificar Status para ver o status do pagamento atual e a data de pagamento (U.I.)

#### Patch 
Há também a opção de revogar um pagamento programado após a criação. O Mock TPP então chama o /patch/endpoint e passa o status de pagamento para o RJCT.

- Selecione Revogar Pagamento no Menu Mock TPP (U.I)
- Preencha as informações do patch e pressione Revogar pagamento (U.I)
- Chame o ponto final do Patch API de Pagamentos (Back-End)
- Volte ao menu Mock TPP e pressione Verificar Status para ver o pagamento programado ser rejeitado (U.I)


# Customer Data

O Mock TPP está sendo desenvolvido para suportar totalmente a Fase 2 de Dados do Cliente. Em sua versão atual, após fazer o DCR ou usar um cliente existente, o usuário é informado sobre as informações de consentimento e então pode usar as APIs da Fase 2

[Gravamos um vídeo que explica como o Mock TPP lida com a Fase 2 Dados do Cliente](https://www.youtube.com/watch?v=gqtyTx98LzU)

### Início da aplicação > Seleção do banco > DCR

- Selecione Dados do Cliente no Menu Principal
- Recuperar do diretório (Back-End) a lista de participantes que têm clientes-pessoais registrados em seu tipo de Família API
- Exibir participantes - Permitir a busca e seleção de um participante (U.I.)
- Realizar um DCR com o participante selecionado (Back-End)
- Solicitar uma nova tela que mostre o ID do cliente para o participante selecionado (U.I)

## Chamando os Consentimentos

- Selecione Personal or Business (PF/PJ), Identification Number, Rel (CPF/CNPJ) (U.I)
- Escolha o que consente a partir da lista disponível (U.I) 
- Enviar pedido de consentimento para o cliente (Back-End)
- Autenticar informações do usuário (U.I)
- Aceitar ou recusar consentimentos escolhidos e consentir o compartilhamento de dados (U.I)
- Se aprovado, vá para o Menu de Resposta ao Consentimento

![image](uploads/d4202ce2aff97775163fde5261edbacb/image.png)



## Chamada de recursos API da Fase 2

No Menu de Resposta Consentida, o usuário pode selecionar qual API da Fase 2 deseja chamar.

![image](uploads/80514584b8acc1e91408bcea525540f9/image.png)

### Recursos (Resources)

Chama o endpoint

```
open-banking/resources/v1/resources/
```

![image](uploads/ecf34b3f78eb7f3438314529491fdbaf/image.png)

### Informações pessoais/negócios (Personal/Business Info)

Endpoints disponíveis
```
open-banking/customers/v1/personal/identifications/
open-banking/customers/v1/personal/financial-relations/
open-banking/customers/v1/personal/qualifications/
```

![image](uploads/35a57f519d949e15504120a46d583084/image.png)

### Contas (Accounts)


Endpoints disponíveis
```
open-banking/accounts/v1/accounts/
open-banking/accounts/v1/accounts/{accountID}
open-banking/accounts/v1/accounts/{accountID}/overdraft-limits
open-banking/accounts/v1/accounts/{accountID}/balances
open-banking/accounts/v1/accounts/{accountID}/transactions
```

![image](uploads/355c131542d451555c5826c2644951f2/image.png)


### Cartão de Crédito (Credit Cards)

Endpoints disponíveis
```
open-banking/credit-cards-accounts/v1/accounts/
open-banking/credit-cards-accounts/v1/accounts/{accountID}
open-banking/credit-cards-accounts/v1/accounts/{accountID}/limit
open-banking/credit-cards-accounts/v1/accounts/{accountID}/transactions
open-banking/credit-cards-accounts/v1/accounts/{accountID}/bills
```


![image](uploads/c2be349d791ef6afa92ecf1d4e4bf324/image.png)

### Operações de Crédito (Credit Operations)

![image](uploads/7388d9faa78a98a8778305c64fc31bca/image.png)

#### Loans

Endpoints disponíveis
```
open-banking/loans/v1/contracts/
open-banking/loans/v1/contracts/{contractId}
open-banking/loans/v1/contracts/{contractId}/warranties
open-banking/loans/v1/contracts/{contractId}/scheduled-instalments
open-banking/loans/v1/contracts/{contractId}/payments
```

![image](uploads/ca3d4466795d12c8ec8e1ff727f50665/image.png)

#### Financings
Endpoints disponíveis
```
open-banking/financings/v1/contracts/
open-banking/financings/v1/contracts/{contractId}
open-banking/financings/v1/contracts/{contractId}/warranties
open-banking/financings/v1/contracts/{contractId}/scheduled-instalments
open-banking/financings/v1/contracts/{contractId}/payments
```

![image](uploads/8c7416829dbc4950dfdc01c2a2a03271/image.png)

#### Unarranged Accounts Overdraft
Endpoints disponíveis
```
open-banking/unarranged-accounts-overdraft/v1/contracts/
open-banking/unarranged-accounts-overdraft/v1/contracts/{contractId}
open-banking/unarranged-accounts-overdraft/v1/contracts/{contractId}/warranties
open-banking/unarranged-accounts-overdraft/v1/contracts/{contractId}/scheduled-instalments
open-banking/unarranged-accounts-overdraft/v1/contracts/{contractId}/payments
```

![image](uploads/130ec644893cc5d99892e91c59e00d8e/image.png)

#### Invoice Financings
Endpoints disponíveis
```
open-banking/invoice-financings/v1/contracts/
open-banking/invoice-financings/v1/contracts/{contractId}
open-banking/invoice-financings/v1/contracts/{contractId}/warranties
open-banking/invoice-financings/v1/contracts/{contractId}/scheduled-instalments
open-banking/invoice-financings/v1/contracts/{contractId}/payments
```

![image](uploads/f7e219fa8d1acd6566fc02aa467e93a3/image.png)

### APIs da Fase 2 Versão 2

O Mock TPP também suporta os novos APIs da Fase 2 V2. Você pode usá-las selecionando a opção "v2" no menu Dados do Cliente.

![image](uploads/e32c4d626c790dab6a1dda2d4b05b0c7/image.png)

O Mock TPP suporta as novas APIs v2 tais como "transações-correntes". Abaixo está um vídeo mostrando o Mock TPP executando a Fase 2 v2 contra o Mock Bank:

<div align="left">
      <a href="https://www.youtube.com/watch?v=kAYFy-kx51g">
         <img src="https://img.youtube.com/vi/kAYFy-kx51g/0.jpg" style="width:100%;">
      </a>
</div>

---

*Conteúdo baixado em 16/09/2026, 15:38:05*
