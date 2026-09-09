# Máquina de Estados - v1.0.0 - [PC] Portabilidade de Crédito - CPC.

# **Estados da Portabilidade de Crédito Pessoal Clean**

##### _\*A atualização da máquina de estado é de responsabilidade da credora, por ser a detentora dos contratos._

# RECEIVED

Estado inicial da portabilidade de crédito.

Este estado indica que o pedido de portabilidade foi recebido pela instituição credora. O pedido permanece neste estado até o início do próximo dia útil e deverá ser movido automaticamente para o estado **PENDING**.

Isso significa que:

Caso o pedido seja registrado em qualquer horário de um dia útil (ex.: 14:00), ele permanecerá no estado **RECEIVED** até 00:00. Somente a partir desse momento a máquina de estados será atualizada automaticamente para **PENDING**, em um processo de responsabilidade da instituição credora, iniciando-se assim a próxima etapa do processo.

Caso o cliente solicite o cancelamento do pedido de portabilidade no canal digital da instituição proponente ou da instituição credora, a portabilidade deverá ser movida para o estado **CANCELLED**. No caso de solicitação realizada no canal da instituição proponente, essa informação deverá ser previamente comunicada à instituição credora.

* * *

# PENDING

Indica que o pedido de portabilidade está na fase de contraproposta pela instituição credora.

Nesta etapa, a instituição credora possui prazo máximo de **3 dias úteis**, contados a partir do momento em que a máquina entra nesse estado.

Atualizações na máquina de estados feitas após as **10:00 horas** de cada dia serão processadas apenas no próximo dia útil.

A contraproposta pode ser apresentada ao cliente por qualquer canal de comunicação (telefone, e-mail, aplicativo etc.). Porém, o aceite da contraproposta será considerado válido somente se realizado no canal digital da instituição credora.

## Possíveis desfechos do estado PENDING

### Cliente aceita a contraproposta

Caso o cliente aceite a contraproposta até as **09:00 horas do terceiro dia útil**, no canal digital da instituição credora, o pedido de portabilidade deverá ser movido para o estado **REJECTED**.

### Cliente solicita o cancelamento via credora

O cliente poderá solicitar o cancelamento do pedido de portabilidade por meio do canal digital da instituição credora, enquanto a solicitação estiver no estado PENDING. Caso essa solicitação seja realizada nessa condição, o pedido de portabilidade deverá ser alterado para o estado **CANCELLED**.

### Cliente solicita o cancelamento via proponente

O cliente poderá solicitar o cancelamento do pedido de portabilidade por meio do canal digital da instituição proponente. Caso a solicitação ocorra nesse estado, a informação deverá ser devidamente comunicada à instituição credora.

### Expiração do prazo de contraproposta

Caso nenhuma ação seja realizada pela instituição credora até as **10:00 horas do terceiro dia útil**, a máquina de estados deverá ser atualizada para o estado **ACCEPTED\_SETTLEMENT\_IN\_PROGRESS**.

A instituição credora poderá, a seu critério, ofertar uma contraproposta e/ou antecipar o processo de atualização da máquina de estados.

Caso a instituição opte por antecipar a atualização da máquina de estados para **ACCEPTED\_SETTLEMENT\_IN\_PROGRESS**, a alteração deverá ocorrer até **10:00 de cada dia útil**. Alterações realizadas após esse horário somente produzirão efeito no próximo dia útil.

* * *

# ACCEPTED\_SETTLEMENT\_IN\_PROGRESS

Indica que a contraproposta não foi aceita pelo cliente ou que a instituição credora não apresentou contraproposta dentro do prazo estabelecido.

Nesta etapa, a instituição proponente deverá realizar a liquidação do contrato **no mesmo dia** em que o pedido entrar neste estado.

Após realizar a liquidação do contrato via **STR0052**, recomenda-se que a proponente comunique a liquidação à instituição credora via **API padronizada**.  
A máquina de estados será atualizada para **ACCEPTED\_SETTLEMENT\_COMPLETED**.

Caso a instituição proponente não realize a liquidação do contrato, a instituição credora deve atualizar a máquina de estados, para **REJECTED**, informando o motivo **PORTABILIDADE\_CANCELADA\_POR\_FALTA\_DE\_LIQUIDACAO**.

Nesta etapa o cliente pode solicitar o cancelamento do pedido de portabilidade somente no canal digital da instituição proponente e desde que o contrato ainda não tenha sido liquidado. É de dever da instituição proponente, informar o cancelamento a instituição credora.

* * *

# ACCEPTED\_SETTLEMENT\_COMPLETED

Indica que a instituição proponente realizou a liquidação do contrato e comunicou a operação à instituição credora.

A partir da entrada neste estado, inicia-se o prazo máximo de **2 dias úteis** para conclusão total do processo de portabilidade. Para garantir previsibilidade operacional e evitar atrasos no processo de liquidação, devem ser respeitadas as regras abaixo:

Em caso de inconsistências, o pedido deverá ser movido imediatamente para o estado **PAYMENT\_ISSUE**.

Caso a liquidação esteja correta, a credora deverá mover o pedido para **PORTABILITY\_COMPLETED**.

**Importante:** A transição para **PAYMENT\_ISSUE** não interrompe nem reinicia o prazo de **2 dias úteis** para conclusão do processo.

* * *

# PAYMENT\_ISSUE

Indica que a instituição credora identificou inconsistências e deverá estornar o pagamento via **STR0010**, informando o motivo **DIVERGENCIA\_DE\_PAGAMENTO\_EFETUADO**.

Caso a instituição proponente realize o ajuste dentro do prazo estabelecido e a instituição credora reconheça a regularização da liquidação, o pedido deverá ser movido para **ACCEPTED\_SETTLEMENT\_COMPLETED**, para que a etapa de validação seja refeita.

Caso a instituição proponente não realize os ajustes necessários, a instituição credora deverá rejeitar o pedido de portabilidade, movendo o estado para **REJECTED**, informando o motivo **DECURSO\_DO\_PRAZO\_PARA\_PAGAMENTO**.

* * *

# PORTABILITY\_COMPLETED

Indica que o pedido de portabilidade foi concluído com sucesso.

Isso significa que:

-   A instituição credora confirmou a quitação do contrato.
    
-   O processo de portabilidade foi finalizado.
    
-   A partir dessa etapa, o contrato da IF Proponente deverá ser efetivado**.**
    

* * *

# CANCELLED

Indica que o pedido de portabilidade foi cancelado pelo cliente.

O cliente pode solicitar o cancelamento do pedido de portabilidade no canal digital da instituição credora enquanto estiver no estado **PENDING** e caso isso aconteça a portabilidade deverá ser movida para o estado **CANCELLED**.

Caso o cliente solicite o cancelamento do pedido de portabilidade no canal digital da instituição proponente, no estado **ACCEPTED\_SETTLEMENT\_IN\_PROGRESS** e **antes da quitação do contrato**, essa informação deverá ser previamente comunicada à instituição credora e a portabilidade deverá ser movida para o estado **CANCELLED**. 

* * *

# REJECTED

Indica que o pedido de portabilidade foi rejeitado.

Isso pode ocorrer, entre outros motivos, nas seguintes situações:

-   O cliente aceitou a contraproposta da instituição credora.
    
-   A instituição proponente recusou a liquidação quando o valor atualizado do contrato ultrapassou **15% do valor originalmente informado**.
    
-   As inconsistências registradas no estado **PAYMENT\_ISSUE** não foram resolvidas dentro do prazo estabelecido.
    

* * *

### **Mapeamento por motivo de rejeição:**

**Máquina de Estados**

-   **data.status**
    

**Motivo da Rejeição**

-   **data.statusReason.reasonType**
    

-   **data.rejection.reason.type**
    

**Responsável pela solicitação da rejeição**

-   **data.rejection.rejectedBy**
    

REJECTED

POLITICA\_DE\_CREDITO

PROPONENTE

RETENCAO\_DO\_CLIENTE

CREDORA

CONTRATO\_JA\_LIQUIDADO

CREDORA

SALDO\_DEVEDOR\_ATUALIZADO\_SUBSTANCIALMENTE\_DIVERGENTE

PROPONENTE

DECURSO\_DO\_PRAZO\_PARA\_PAGAMENTO

CREDORA

PORTABILIDADE\_CANCELADA\_POR\_FALTA\_DE\_LIQUIDACAO

CREDORA

PORTABILIDADE\_EM\_ANDAMENTO

CREDORA

MODALIDADE\_DA\_OPERACAO\_INCOMPATIVEL

CREDORA

CLIENTE\_COM\_ACAO\_JUDICIAL

CREDORA

OUTROS

CREDORA, PROPONENTE

CANCELLED

CANCELADO\_PELO\_CLIENTE

USUARIO

PAYMENT\_ISSUE

DIVERGENCIA\_DE\_PAGAMENTO\_EFETUADO

CREDORA

OUTROS

CREDORA
