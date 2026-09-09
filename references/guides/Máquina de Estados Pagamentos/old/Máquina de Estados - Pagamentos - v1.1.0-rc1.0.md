# Máquina de Estados  - Pagamentos - v1.1.0-rc1.0

#### Os possíveis status do consentimento são:

AWAITING\_AUTHORISATION - Aguardando autorização AUTHORISED - Autorizado REJECTED - Rejeitado CONSUMED - Consumido REVOKED - Revogado

![state-machine\_phase3\_v04-c5fd3c8e.png](images/state-machine_phase3_v04-c5fd3c8e.png)

Algumas definições são importantes para tratar a transição dos estados do consentimento em diferentes momentos do fluxo:

#### AWAITING\_AUTHORISATION

-   O consentimento é sempre criado com o status AWAITING\_AUTHORISATION. Ele pode ser aprovado antes do tempo de expiração de 5 minutos, assumindo o status AUTHORISED. Se não, deve assumir o status REJECTED caso expire ou seja cancelado pelo usuário.
    

#### AUTHORISED

-   Para o cenário em que o status assumiu AUTHORISED, o tempo máximo do expirationDateTime do consentimento deve assumir "now + 60 minutos". Este é o tempo para consumir o consentimento autorizado, mudando seu status para CONSUMED. Não é possível prorrogar este tempo e a criação de um novo consentimento será necessária para os cenários de insucesso. O tempo do expirationDateTime é garantido com os 15 minutos do access token, sendo possível utilizar mais três refresh tokens até totalizar 60 minutos.
    

##### REJECTED

-   Em caso de consentimento expirado a Detentora deverá retornar o status REJECTED.
    
-   Em caso de consentimento rejeitado pelo usuário ou por regra de negócio da Detentora, o status deverá ser retornado como REJECTED.
    

#### CONSUMED

-   O consentimento assume o status CONSUMED após ocorrer o processamento da iniciação do pagamento, seja ele com sucesso (HTTP 201) ou ainda em casos de insucesso (HTTP 422) retornados pela Detentora. Para os demais códigos HTTP não há mudança de status do consentimento, o mesmo permanecerá AUTHORISED, respeitando o tempo máximo de expiração do consentimento (60 minutos).
    

#### REVOKED

-   O estado REVOKED existirá somente quando a revogação for realizada pelo Usuário ou Iniciadora ou Detentora (somente para consentimentos de agendamento).
    

**Os possíveis status do pagamento PIX, são:**

PDNG, PART, ACSP, ACSC, ACCC e RJCT.

**Pagamento PIX**

![state-machine\_phase3\_pix\_payment-e4960e5b.png](images/state-machine_phase3_pix_payment-e4960e5b.png)

**Os possíveis status do pagamento PIX agendamento, são:**

PDNG, SASP, SASC, PART, ACSP, ACSC, ACCC e RJCT.

**Pagamento PIX agendamento**

![state-machine\_phase3\_pix\_scheduling\_payment\_v2-9ed90256.png](images/state-machine_phase3_pix_scheduling_payment_v2-9ed90256.png)

Abaixo segue a descrição dos status relacionados a máquina de estados pertinente aos tipos de pagamento PIX e PIX agendamento:

#### PDNG (PENDING)

-   O status informa que a iniciação de pagamento ou transação de pagamento está pendente. Checagens adicionais em realização.
    

#### SASP (SCHEDULE\_ACCEPTED\_SETTLEMENT\_IN\_PROCESS) - **somente para PIX agendamento**.

-   O status informa que o agendamento está em processamento.
    

#### SASC (SCHEDULE\_ACCEPTED\_SETTLEMENT\_COMPLETED) - **somente para PIX agendamento**.

-   O status informa que o agendamento foi realizado com sucesso.
    

#### PART (PARTIALLY ACCEPTED)

-   O status informa que fluxo de pagamento está aguardando autorização múltipla alçada.
    

#### ACSP (ACCEPTED\_SETTLEMENT\_IN\_PROCESS)

-   O status informa que a iniciação de pagamento foi aceita e o processamento do pagamento foi iniciado.
    

#### ACSC (ACCEPTED\_SETTLEMENT\_COMPLETED\_DEBITOR\_ACCOUNT)

-   O status informa que o débito foi realizado na conta do pagador.
    

#### ACCC (ACCEPTED\_SETTLEMENT\_COMPLETED)

-   O status informa que foi realizado um crédito na instituição de destino.
    

#### RJCT (REJECTED)

-   O status informa que a instrução de pagamento foi rejeitada.
