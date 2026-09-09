# Edição do consentimento - v1.0.0-rc.1 - [SV] Pagamentos Automáticos

**A implementação e certificação do Pix Automático está pausada no momento. O produto Transferência Inteligentes (Sweeping Accounts) continua disponível para implementação e certificação.**

## Campos passíveis de edição e suas condições:

Nesta versão, será permitida apenas a edição de consentimentos para o produto Pix Automático, ou seja, onde o campo “recurringConfiguration”, no momento de criação do consentimento, foi preenchido com o objeto “automatic” no seu oneOf.

Na tabela abaixo, foram listados os campos, o ambiente em que será editado (iniciadora ou detentora), o tipo de mudança (aumentar valor limite ou reduzir valor limite) e se o usuário precisará ser redirecionado ou não para confirmar essa alteração.

### Campos passiveis de edição na Iniciadora:

**Campo**

**Presença do usuário**

**Campo preenchido inicialmente?**

**Tipo de alteração**

**Alteração na:**

**Exige redirecionamento?**

**Exemplo**

**Webhook**

creditors/name

Não necessário

sim

Alterar o nome do recebedor

Iniciadora

Não

Trocar o nome do recebedor de NET para Claro

\-

startDateTime

Necessário

sim

Antecipação ou Postergação do início da vigência

Iniciadora

Não

Data inicial do consentimento ser alterada de 10/02/2024 para 15/02/2024

\-

expirationDateTime

Necessário

sim

Reduzir o prazo

Iniciadora

Não

Data final do consentimento ser alterada de 10/02/2024 para 10/01/2024

\-

expirationDateTime

Necessário

sim

Aumentar o prazo

Iniciadora

Não

Data final do consentimento ser alterada de 10/02/2024 para 10/02/2025

\-

expirationDateTime

Necessário

sim

Aumentar o prazo indeterminadamente

Iniciadora

Não

Data final do consentimento ser alterada de 10/02/2024 sem prazo definido

\-

transactionLimit

Necessário

sim

Aumentar o valor

Iniciadora

Não

Limite por transação vai de R$200 para R$300

\-

transactionLimit

Necessário

sim

Reduzir o valor

Iniciadora

Não

Limite por transação vai de R$200 para R$100

\-

dayOfMonth

Necessário

sim

Alterar a data da cobrança recorrente

Iniciadora

Não

Usuário altera a data da liquidação de "todo dia 10" para "todo dia 15"

\-

### Campos passiveis de edição na Detentora:

**Campo**

**Presença do usuário**

**Campo preenchido inicialmente?**

**Tipo de alteração**

**Alteração na:**

**Exige redirecionamento?**

**Exemplo**

**Webhook**

debtorAccount

Necessário

sim

Alterar conta de pagamento

Detentora

Não

Usuário altera a conta de débito do pagamento

Sim

transactionLimit

Necessário

sim

Aumentar o valor

Detentora

Não

Limite por transação vai de R$200 para R$300

Sim

transactionLimit

Necessário

sim

Reduzir o valor

Detentora

Não

Limite por transação vai de R$200 para R$100

Sim

transactionLimit

Necessário

não

Definir o valor

Detentora

Não

Usuário não definiu um limite por transação no momento do consentimento e depois define como R$100

Sim
