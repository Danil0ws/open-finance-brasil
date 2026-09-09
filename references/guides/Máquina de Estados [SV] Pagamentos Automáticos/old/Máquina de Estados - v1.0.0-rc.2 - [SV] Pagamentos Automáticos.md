# Máquina de Estados - v1.0.0-rc.2 - [SV] Pagamentos Automáticos

**A implementação e certificação do Pix Automático está pausada no momento. O produto Transferência Inteligentes (Sweeping Accounts) continua disponível para implementação e certificação.**

## **Consentimento**

**Os possíveis status do consentimento são:**

-   AWAITING\_AUTHORISATION - Aguardando autorização
    
-   PARTIALLY\_ACCEPTED - Parcialmente aceito
    
-   AUTHORISED - Autorizado
    
-   REJECTED - Rejeitado
    
-   REVOKED - Revogado
    
-   CONSUMED - Consumido
    

![image-20231106-150119.png](images/image-20231106-150119.png)

Algumas definições são importantes para tratar a transição dos estados do consentimento em diferentes momentos do fluxo:

#### AWAITING\_AUTHORISATION

-   O consentimento é sempre criado com o status AWAITING\_AUTHORISATION. Ele pode ser aprovado somente antes do tempo de expiração de 5 minutos, assumindo o status AUTHORISED. Se não, deve assumir o status REJECTED caso expire ou seja cancelado pelo usuário.
    

Lembrando que o usuário pode cancelar o consentimento no lado da detentora de conta e por sua vez ela deve mudar o status do consentimento para REJECTED.

#### PARTIALLY\_ACCEPTED

-   O status indica que o consentimento precisa da confirmação de mais autorizadores para que o processamento da transação possa prosseguir. Esse não possui prazo de expiração e a alteração desse status depende da política de cada detentora de conta.
    

#### AUTHORISED

-   Para o cenário em que o status assumiu AUTHORISED, o tempo máximo do consentimento deve assumir é "(expirationDateTime) - (startDateTime)" . Este é o tempo para consumir o consentimento autorizado, mudando seu status para CONSUMED. É possível prorrogar este tempo editando o consentimento. Caso necessário alterar um campo que não é passível de edição, a criação de um novo consentimento será necessária.
    
-   O expirationDateTime pode ser definido ou não pelo usuário, caso não seja definido, o consentimento não tem data para ser consumido. É possível que o usuário edite esse campo e defina um expirationDateTime posteriormente.
    

#### REJECTED

-   Em caso de consentimento expirado a Detentora deverá retornar o status REJECTED.
    
-   Em caso de consentimento rejeitado pelo usuário ou por regra de negócio da Detentora, o status deverá ser retornado como REJECTED.
    
-   Caso um consentimento possua um pagamento imediato e este falhar, o consentimento deverá assumir o status REJECTED.
    

#### REVOKED

-   Apenas consentimentos em AUTHORISED podem trafegar para REVOKED.
    
-   Em casos de consentimento revogado pelo usuário, pelo detentor ou pelo iniciador, o detentor deve retornar o status REVOKED.
    

#### CONSUMED

-   A detentora de conta deve ativamente realizar a mudança do status do consentimento de AUTHORISED para CONSUMED quando a data de expiração do consentimento for ultrapassada.
    
-   O consentimento para Sweeping Accounts deve ser movido para CONSUMED caso o somatório dos valores transacionados igualem o valor máximo definido para o consentimento (campo "/data/recurringConfiguration/sweeping/totalAllowedAmount").
    

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
    

![image-20231122-132829.png](images/image-20231122-132829.png)

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
