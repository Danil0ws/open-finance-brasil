# Edição do consentimento - v2.0.0-rc.1 - [SV] Pagamentos Automáticos

## Campos passíveis de edição e suas condições:

Nesta versão, será permitida apenas a edição de consentimentos para o produto Pix Automático, ou seja, onde o campo “recurringConfiguration”, no momento de criação do consentimento, foi preenchido com o objeto “automatic” no seu oneOf.

Na tabela abaixo, foram listados os campos, o ambiente em que será editado (iniciadora ou detentora), o tipo de mudança (aumentar valor limite ou reduzir valor limite) e se o usuário precisará ser redirecionado ou não para confirmar essa alteração.

### Campos passiveis de edição na Iniciadora:

**Campo**

**Presença do usuário**

**Anuência do usuário?**

**Quem edita?¹**

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

Usuário

Sim

Aumentar o valor

Não

Limite por transação vai de R$200 para R$300

\-

maximumVariableAmount

Necessário

Sim

Usuário

Sim

Reduzir o valor

Obs.: respeitando o valor mínimo definido pelo recebedor

Não

Limite por transação vai de R$200 para R$100

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

Usuário

Sim

Aumentar o valor

Não

Limite por transação vai de R$200 para R$300

\-

maximumVariableAmount

Necessário

Sim

Usuário

Sim

Reduzir o valor

Não

Limite por transação vai de R$200 para R$100

\-

maximumVariableAmount

Necessário

Sim

Usuário

Não

Definir o valor

Não

Usuário não definiu um limite por transação no momento do consentimento e depois define como R$100

\-

useOverdraftLimit

Necessário

Sim

Usuário

Sim

Ativar ou desativar

Não

Usuário optou por utilizar ou não utilizar o cheque especial

\-
