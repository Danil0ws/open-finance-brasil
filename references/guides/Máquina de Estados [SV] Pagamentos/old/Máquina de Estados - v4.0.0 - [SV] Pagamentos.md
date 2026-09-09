# Máquina de Estados - v4.0.0 - [SV] Pagamentos

## **Consentimento**

**Os possíveis status do consentimento são:**

-   AWAITING\_AUTHORISATION - Aguardando autorização
    
-   PARTIALLY\_ACCEPTED - Parcialmente aceito
    
-   AUTHORISED - Autorizado
    
-   REJECTED - Rejeitado
    
-   CONSUMED - Consumido
    

![image-20231106-150239.png](images/image-20231106-150239.png)

Algumas definições são importantes para tratar a transição dos estados do consentimento em diferentes momentos do fluxo:

#### AWAITING\_AUTHORISATION

-   O consentimento é sempre criado com o status AWAITING\_AUTHORISATION. Ele pode ser aprovado somente antes do tempo de expiração de 5 minutos, assumindo o status AUTHORISED. Se não, deve assumir o status REJECTED caso expire ou seja cancelado pelo usuário.
    

Lembrando que o usuário pode cancelar o consentimento no lado da detentora de conta e por sua vez ela deve mudar o status do consentimento para REJECTED.

#### PARTIALLY\_ACCEPTED

-   O status indica que o consentimento precisa da confirmação de mais autorizadores para que o processamento da transação possa prosseguir. Para o caso de **pagamento imediato**, todas as aprovações necessárias devem ser realizadas nos canais da detentora até às 23:59 (horário de Brasília) da data de solicitação do pagamento.
    
-   Para o caso de **pagamentos agendados**, o prazo de expiração para consentimentos nesse status não deve ser maior que D-1, sendo D o dia previsto para primeira liquidação.
    

#### AUTHORISED

-   Para o cenário em que o status assumiu AUTHORISED, o tempo máximo do expirationDateTime do consentimento deve assumir "now + 60 minutos". Este é o tempo para consumir o consentimento autorizado, mudando seu status para CONSUMED. Não é possível prorrogar este tempo e a criação de um novo consentimento será necessária para os cenários de insucesso.
    

O tempo do expirationDateTime é garantido com os 15 minutos do access token, sendo possível utilizar mais três refresh tokens até totalizar 60 minutos.

#### REJECTED

-   Em caso de consentimento expirado a Detentora deverá retornar o status REJECTED.
    
-   Em caso de consentimento rejeitado pelo usuário ou por regra de negócio da Detentora, o status deverá ser retornado como REJECTED.
    

#### CONSUMED

-   O consentimento assume o status CONSUMED após ocorrer o processamento da iniciação do pagamento, seja ele com sucesso (HTTP 201) ou ainda em casos de insucesso (HTTP 422) retornados pela Detentora. Para os demais códigos HTTP não há mudança de status do consentimento, o mesmo permanecerá AUTHORISED, respeitando o tempo máximo de expiração do consentimento (60 minutos).
    

### Recomendação uso de polling

A consulta via GET, para verificar o processamento da transação, pode ser efetuada a qualquer momento desde que se respeite o rate limit definido na página Recomendação Uso de Polling e Controle de Acesso.

## **Pagamento: Arranjo Pix**

**Os possíveis status do pagamento Pix, são:**

-   RCVD
    
-   CANC
    
-   ACCP
    
-   ACPD
    
-   RJCT
    
-   ACSC
    
-   PDNG
    
-   SCHD
    

![image-20231122-132520.png](images/image-20231122-132520.png)

Abaixo segue a descrição dos status relacionados a máquina de estados pertinente aos tipos de pagamento Pix:

#### RCVD (Received)

-   O status indica que a requisição de pagamento foi recebida com sucesso pela detentora, mas ainda há validações a serem feitas antes de ser submetida para liquidação.
    

#### CANC (Cancelled)

-   O status indica que a transação Pix pendente foi cancelada com sucesso pelo usuário antes que fosse confirmada (ACCP) ou rejeitada (RJCT) pela detentora.
    

#### ACCP( Accepted Customer Profile)

-   O status indica que todas as verificações necessárias já foram realizadas pela detentora e que a transação está pronta para ser enviada para liquidação (no SPI se for Pix para outra instituição ou internamente se for para outra conta na mesma instituição).
    

#### ACPD (Accepted Clearing Processed)

-   O status indica que a detentora já submeteu a transação para liquidação, mas ainda não tem a confirmação se foi liquidada ou rejeitada.
    

#### RJCT (Rejected)

-   O status indica que a transação foi rejeitada pela detentora ou pelo SPI.
    

#### ACSC (Accepted Settlement Completed Debtor Account)

-   O status indica que a transação foi efetivada pela detentora ou pelo SPI.
    

#### PDNG (Pending)

-   O status indica que a detentora reteve temporariamente a transação Pix para análise.
    

#### SCHD (Scheduled)

-   O status indica que a transação Pix foi agendada com sucesso na detentora.
