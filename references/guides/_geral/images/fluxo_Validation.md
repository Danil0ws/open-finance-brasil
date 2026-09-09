# fluxo_Validation

![fluxo_Validation](fluxo_Validation.png)

## Texto Extraído

Fluxo de Validacao - Motor Qualidade de Dados

INSTITUIGAO FINANCEIRA

Motor Qualidade de Dados (MQD)

MESSAGE_PROCESS_WORKER } | QUEVE_MANAGER } | VALIDATOR |

' ' {© Update ValidantionRules
|. Check Queue '
| 2Get queued Message

|_ 3 Messages

[messages.length times]

| 4 Validate Message ' '

5 Validate Endpoint
6 Unmershal Payload
| 7 Validate Object

8 Retum valid result

=

| 9 Store Result

SS

MESSAGE_PROCESS_WORKER } | QUEUE_MANAGER } | VALIDATOR

---
**Arquivo original:** `fluxo_Validation.png`
**Tamanho:** 34.87 KB