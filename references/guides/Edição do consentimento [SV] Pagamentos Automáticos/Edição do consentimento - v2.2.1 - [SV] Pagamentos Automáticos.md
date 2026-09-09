# Edição do consentimento - v2.2.1 - [SV] Pagamentos Automáticos

## Campos passíveis de edição e suas condições:

Os produtos transferências inteligentes e Pix Automáticos possuem características de edição de campos que podem ser realizadas em ambiente do detentor e/ou iniciador.  
Nas tabelas abaixo foram listados os campos, o ambiente em que será editado (iniciadora ou detentora), o tipo de mudança (ex. aumentar valor, reduzir prazo), se o usuário precisará estar presente e ser redirecionado ou não para confirmar essa alteração. Apenas consentimentos em estado AUTHORISED podem ser editados, independente do produto.

## 1\. Pix Automático

Para o produto Pix Automático, ou seja, onde o objeto “**recurringConfiguration**”, no momento de criação do consentimento, foi preenchido com o objeto “**automatic**” no seu oneOf.

### Campos passiveis de edição na Iniciadora:

**Campo**

**Presença do usuário**

**Anuência do usuário?**

**Quem edita?**

**Campo preenchido inicialmente?**

**Tipo de alteração**

**Exige redirecionamento?**

**Exemplo**

**Webhook**

creditors/name

Não necessário

Não

Recebedor

Sim

Alterar o nome do recebedor

Não

Trocar o nome do recebedor de NET para Claro

\-

expirationDateTime

Necessário

Sim

Recebedor

Sim

Reduzir o prazo

Não

Data final do consentimento ser alterada de 10/02/2024 para 10/01/2024

\-

expirationDateTime

Necessário

Sim

Recebedor

Sim

Aumentar o prazo

Não

Data final do consentimento ser alterada de 10/02/2024 para 10/02/2025

\-

expirationDateTime

Necessário

Sim

Recebedor

Sim

Aumentar o prazo indeterminadamente

Não

Data final do consentimento ser alterada de 10/02/2024 sem prazo definido

\-

maximumVariableAmount

Necessário

Sim

Usuário Pagador

Sim

Aumentar o valor

Não

Limite por transação vai de R$200 para R$300

\-

maximumVariableAmount

Necessário

Sim

Usuário Pagador

Sim

Reduzir o valor

Obs.: respeitando o valor mínimo definido pelo recebedor

Não

Limite por transação vai de R$200 para R$100

\-

maximumVariableAmount

Necessário

Sim

Usuário Pagador

Não

Definir o valor

Não

Usuário não definiu um limite por transação no momento do consentimento e depois define como R$100

\-

maximumVariableAmount

Necessário

Sim

Usuário Pagador

Sim

Tornar o limite indeterminado

Não

Com limite definido, usuário decide remover e tornar o consentimento passível de qualquer valor de cobrança

\-

### Campos passiveis de edição na Detentora:

**Campo**

**Presença do usuário**

**Anuência do usuário?**

**Quem edita?¹**

**Campo preenchido inicialmente?**

**Tipo de alteração**

**Exige redirecionamento?**

**Exemplo**

**Webhook**

maximumVariableAmount

Necessário

Sim

Usuário Pagador

Sim

Aumentar o valor

Não

Limite por transação vai de R$200 para R$300

\-

maximumVariableAmount

Necessário

Sim

Usuário Pagador

Sim

Reduzir o valor

Não

Limite por transação vai de R$200 para R$100

\-

maximumVariableAmount

Necessário

Sim

Usuário Pagador

Não

Definir o valor

Não

Usuário não definiu um limite por transação no momento do consentimento e depois define como R$100

\-

maximumVariableAmount

Necessário

Sim

Usuário Pagador

Sim

Tornar o limite indeterminado

Não

Com limite definido, usuário decide remover e tornar o consentimento passível de qualquer valor de cobrança

\-

useOverdraftLimit

Necessário

Sim

Usuário Pagador

Sim

Ativar ou desativar

Não

Usuário optou por utilizar ou não utilizar o cheque especial

\-

## 2\. Transferências Inteligentes

Para o produto Transferências inteligentes, ou seja, onde o objeto “**recurringConfiguration**”, no momento de criação do consentimento, foi preenchido com o objeto “**sweeping**” no seu oneOf.

No momento, não há edições possíveis no ambiente da instituição iniciadora.

### Campos passiveis de edição na Detentora:

**Campo**

**Presença do usuário**

**Anuência do usuário?**

**Quem edita?¹**

**Campo preenchido inicialmente?**

**Tipo de alteração**

**Exige redirecionamento?**

**Exemplo**

**Webhook**

useOverdraftLimit

Necessário

Sim

Usuário

Sim

Ativar ou desativar

Não

Usuário optou por utilizar ou não utilizar o cheque especial

\-
