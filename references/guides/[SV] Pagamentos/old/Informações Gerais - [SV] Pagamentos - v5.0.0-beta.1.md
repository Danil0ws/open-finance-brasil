# Informações Gerais - [SV] Pagamentos - v5.0.0-beta.1

23

## **Visão geral**

A API tem como objetivo coletar o consentimento e realizar a iniciação de pagamento entre bancos, instituições financeiras e é acessível também à estabelecimentos comerciais participantes do Open Finance Brasil.

Os recursos estão disponíveis para pagadores que possuem registro em uma instituição detentora de conta participante do Open Finance, independentemente de serem pessoa física ou jurídica.

## **Criar consentimento para iniciação de pagamento** : (POST /payments/v5/consents)

Método para a criação do consentimento para iniciação de pagamento.

### **Dicionário de dados**

Campos de resposta do endpoint de `/consents`

[Fazer download do dicionário de dados](data/references/openapi/dictionary-paymentsPostConsents_v4.md)

## **Consultar consentimento para iniciação de pagamento** : (GET /payments/v5/consents/{consentId})

Método para consultar o consentimento para iniciação de pagamento.

### **Dicionário de dados**

Campos de resposta do endpoint de `/consents/{consentId}`

[Fazer download do dicionário de dados](data/references/openapi/dictionary-paymentsGetConsentsConsentId_v4.md)

## **Pix - Criar iniciação de pagamento** : (POST /payments/v5/pix/payments)

Método para a criação de uma iniciação de pagamento.

### **Dicionário de dados**

Campos de resposta do endpoint de `/pix/payments`

[Fazer download do dicionário de dados](data/references/openapi/dictionary-paymentsPostPixPayments_v4.md)

## **Pix - Consultar iniciação de pagamento** : (GET /payments/v5/pix/payments/{paymentId})

Método para consultar uma iniciação de pagamento.

### **Dicionário de dados**

Campos de resposta do endpoint de `/pix/payments/{paymentId}`.

[Fazer download do dicionário de dados](data/references/openapi/dictionary-paymentsGetPixPaymentsPaymentId_v4.md)

## **Pix - Cancelar iniciação de pagamento** : (PATCH /payments/v5/pix/payments/{paymentId})

Método para cancelar uma iniciação de pagamento.

### **Dicionário de dados**

Campos de resposta do endpoint de `/pix/payments/{paymentId}`.

[Fazer download do dicionário de dados](data/references/openapi/dictionary-paymentsPatchPixPaymentsPaymentId_v4.md)

## **Pix - Cancelar iniciação de pagamentos** : (PATCH /payments/v5/consents/{consentId}/pix/payments)

Método para cancelar todos os pagamentos referentes ao mesmo consentimento.

### **Dicionário de dados**

Campos de resposta do endpoint de `/consents/{consentId}/pix/payments`.

[Fazer download do dicionário de dados](data/references/openapi/dictionary-paymentsPatchPixPaymentsConsentId_v4.md)
