# Informações Gerais - Pagamentos - v1.2.0

23

## **Visão geral**

A API tem como objetivo coletar o consentimento e realizar a iniciação de pagamento entre bancos e instituições financeiras e acessível também à estabelecimentos comerciais participantes do Open Finance Brasil.

Os recursos estão disponíveis para pagadores que possuem vínculo com uma instituição detentora de conta participante do Open Finance, independentemente de serem pessoa física ou jurídica.

## **Criar consentimento para iniciação de pagamento** : (POST /payments/v1/consents)

Método para a criação do consentimento para iniciação de pagamento.

### **Dicionário de dados**

Campos de resposta do endpoint de `/consents`

[Fazer download do dicionário de dados](data/references/openapi/dictionary-paymentsPostConsents_v1.md)

## **Consultar consentimento para iniciação de pagamento** : (GET /payments/v1/consents/{consentId})

Método para consultar o consentimento para iniciação de pagamento.

### **Dicionário de dados**

Campos de resposta do endpoint de `/consents`

[Fazer download do dicionário de dados](data/references/openapi/dictionary-paymentsGetConsentsConsentId_v1.md)

## **Pix - Criar iniciação de pagamento** : (POST /payments/v1/pix/payments)

Método para a criação de uma iniciação de pagamento.

### **Dicionário de dados**

Campos de resposta do endpoint de `/pix/payments`

[Fazer download do dicionário de dados](data/references/openapi/dictionary-paymentsPostPixPayments_v1.md)

## **Pix - Consultar iniciação de pagamento** : (GET /payments/v1/pix/payments/{paymentId})

Método para consultar uma iniciação de pagamento.

### **Dicionário de dados**

Campos de resposta do endpoint de `/pix/payments`.

[Fazer download do dicionário de dados](data/references/openapi/dictionary-paymentsGetPixPaymentsPaymentId_v1.md)
