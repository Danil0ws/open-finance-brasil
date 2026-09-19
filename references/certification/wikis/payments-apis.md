# Payments APIs

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Payments-APIs](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Payments-APIs)
**Slug:** `Payments-APIs`

---

# Doing Payments against the Mock Bank

The Raidiam Services Ltd. Mock Bank (hereafter referred to as Mock Bank or MB) is an implementation of several Open Finance Brasil APIs, including the Payment Consent API and the Pix Payment API. Hosted on Raidiam servers, it provides a controlled environment for testing and conformance validation. MB replicates the behavior of the APIs but is not connected to real financial systems (including the Pix payment network) and does not have access to the Central Bank's PIX DICT API.

Because the mock bank Pix Payment implementation is not part of a real payment network, payment requests do not actually result in payments being attempted. Every payment initiated against the mock bank is accepted and, on the first GET, settles to ACSC by default (a future-dated payment moves to SCHD and settles on its scheduled date). Payments only stay in PDNG if forced by specific reserved amounts, listed further below (see 12345.00 / 12345.67 in the single-payment table). This matters because many conformance tests validate how a Pix Payment implementation responds under failure scenarios. These typically involve the rejection of consents or payments due to responses from the DICT, which the mock bank does not interact with. To overcome this during the testing of our test modules, the mock bank can be instructed to respond to payment consent and payment initiation requests in a particular way, by the provision of reserved payment amounts in the payment fields of both consent and payment initiation requests. The details are documented in the next section.

Implementations of Pix Payment APIs can consult the Central Bank PIX DICT API for validation of creditor account details. This validation MAY occur asynchronously, which can result in a payment consent or pix payment request being accepted, but subsequently rejected. There are three points at which a request may fail because of Central Bank PIX DICT API lookup:

1) The bank under test may consult the Central Bank PIX DICT API during the payment consent request, and synchronously reject the consent request as a result
2) The bank under test may consult the Central Bank PIX DICT API during the payment initiation request, and synchronously reject the payment initiation request as a result
3) The bank under test may consult the Central Bank PIX DICT API after the payment initiation request has been accepted, and subsequently move the payment to the RJCT state.

Each of these three scenarios can be forced in the mock bank. Additionally, it is possible to force certain specific error messages for when tests look for a specific failure. The same mechanism can also move a payment to a specific final state after initiation (for example ACSC, RJCT, SCHD or PDNG), as documented below.

# APIs Available

Currently the Mock Bank Status for the implementation of Payments APIs is:

| API | Version | Status | Comments |
|-----|---------|--------|----------|
| Payment Initiation | V5 | Available | Do not include Multiple Consents or Temporization Features. |
| Automatic Payments | V2 | Available | Only V2 is served. Do not include `automatic-payments_api_automatic-pix-consent-edition-account-holder_test-module_v2`. |
| Enrollments | V2 | Available | Do not include `enrollments_api_no-contract_test-module_v1`. |

# Setting different outcomes for the Mock Bank

The Mock Bank reacts to reserved trigger amounts. Each trigger goes in a specific request field, which depends on the API and the stage. For single payments, send the same trigger amount in both the consent and the pix payment. Some triggers act immediately (the API returns the error on the request); others are applied when you later GET the consent or the payment. The sections below are grouped by API; each group states the API, endpoint and field.

## A. Single Pix payments (Payment Initiation V5)

### A1. Reject the consent at creation (immediate)

- **API:** Payment Initiation V5
- **Endpoint:** `POST /open-banking/payments/v5/consents`
- **Field:** `data.payment.amount`

| Value | HTTP | Outcome |
|-------|------|---------|
| `10422.00` | 422 | rejected, no error code |
| `10422.01` | 422 | rejected, `DETALHE_PAGAMENTO_INVALIDO` |
| `10422.02` | 422 | rejected, `FORMA_PAGAMENTO_INVALIDA` |



**Exemplos de request/response:**

<details>
<summary><code>10422.00</code></summary>

**Request** `POST /open-banking/payments/v5/consents`

```json
{
  "loggedUser": {
    "document": {
      "identification": "76109277673",
      "rel": "CPF"
    }
  },
  "creditor": {
    "personType": "PESSOA_NATURAL",
    "cpfCnpj": "76109277673",
    "name": "Recebedor Exemplo"
  },
  "payment": {
    "type": "PIX",
    "currency": "BRL",
    "amount": "10422.00",
    "details": {
      "localInstrument": "DICT",
      "proxy": "76109277673",
      "creditorAccount": {
        "number": "1234567890",
        "ispb": "12345678",
        "issuer": "1774",
        "accountType": "CACC"
      }
    },
    "purpose": "IMMEDIATE",
    "date": "2026-08-25"
  }
}
```

**Response** `HTTP 422`

```json
{
  "iss": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "aud": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "iat": 1787683323,
  "meta": {
    "requestDateTime": "2026-08-25T18:42:03Z"
  },
  "errors": [
    {
      "code": "Forced a 422 for payment consent request",
      "title": "Forced a 422 for payment consent request",
      "detail": "Forced a 422 for payment consent request"
    }
  ],
  "jti": "a6099816-a813-4864-8e4f-bf3f8eba9a84"
}
```

</details>

<details>
<summary><code>10422.01</code></summary>

**Request** `POST /open-banking/payments/v5/consents`

```json
{
  "loggedUser": {
    "document": {
      "identification": "76109277673",
      "rel": "CPF"
    }
  },
  "creditor": {
    "personType": "PESSOA_NATURAL",
    "cpfCnpj": "76109277673",
    "name": "Recebedor Exemplo"
  },
  "payment": {
    "type": "PIX",
    "currency": "BRL",
    "amount": "10422.01",
    "details": {
      "localInstrument": "DICT",
      "proxy": "76109277673",
      "creditorAccount": {
        "number": "1234567890",
        "ispb": "12345678",
        "issuer": "1774",
        "accountType": "CACC"
      }
    },
    "purpose": "IMMEDIATE",
    "date": "2026-08-25"
  }
}
```

**Response** `HTTP 422`

```json
{
  "iss": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "aud": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "iat": 1787683323,
  "meta": {
    "requestDateTime": "2026-08-25T18:42:03Z"
  },
  "errors": [
    {
      "code": "DETALHE_PAGAMENTO_INVALIDO",
      "title": "Detalhe do pagamento inválido.",
      "detail": "DETALHE_PAGAMENTO_INVALIDO"
    }
  ],
  "jti": "bf0bb4c6-2ebd-4504-848e-e3097e616abb"
}
```

</details>

<details>
<summary><code>10422.02</code></summary>

**Request** `POST /open-banking/payments/v5/consents`

```json
{
  "loggedUser": {
    "document": {
      "identification": "76109277673",
      "rel": "CPF"
    }
  },
  "creditor": {
    "personType": "PESSOA_NATURAL",
    "cpfCnpj": "76109277673",
    "name": "Recebedor Exemplo"
  },
  "payment": {
    "type": "PIX",
    "currency": "BRL",
    "amount": "10422.02",
    "details": {
      "localInstrument": "DICT",
      "proxy": "76109277673",
      "creditorAccount": {
        "number": "1234567890",
        "ispb": "12345678",
        "issuer": "1774",
        "accountType": "CACC"
      }
    },
    "purpose": "IMMEDIATE",
    "date": "2026-08-25"
  }
}
```

**Response** `HTTP 422`

```json
{
  "iss": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "aud": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "iat": 1787683323,
  "meta": {
    "requestDateTime": "2026-08-25T18:42:03Z"
  },
  "errors": [
    {
      "code": "FORMA_PAGAMENTO_INVALIDA",
      "title": "Forma do pagamento inválido.",
      "detail": "FORMA_PAGAMENTO_INVALIDA"
    }
  ],
  "jti": "1973226d-7182-4494-b6f7-0c47d90f3010"
}
```

</details>

### A2. Reject the consent at authorisation (returned on GET)

The consent is created normally; on the next GET of the consent the mock returns it with status `REJECTED` and the reason below.

- **API:** Payment Initiation V5
- **Endpoint (to read):** `GET /open-banking/payments/v5/consents/{consentId}`
- **Field:** `data.payment.amount` (set at creation)

| Value | HTTP | Outcome |
|-------|------|---------|
| `300.01` | 200 | consent `REJECTED`, reason `VALOR_INVALIDO` |
| `300.02` | 200 | consent `REJECTED`, reason `NAO_INFORMADO` |
| `300.03` | 200 | consent `REJECTED`, reason `FALHA_INFRAESTRUTURA` |
| `300.04` | 200 | consent `REJECTED`, reason `TEMPO_EXPIRADO_CONSUMO` |
| `300.05` | 200 | consent `REJECTED`, reason `CONTA_NAO_PERMITE_PAGAMENTO` |
| `300.06` | 200 | consent `REJECTED`, reason `NAO_INFORMADO` (detail: account has insufficient balance) |
| `300.07` | 200 | consent `REJECTED`, reason `NAO_INFORMADO` (detail: amount exceeds the customer limit) |
| `300.08` | 200 | consent `REJECTED`, reason `QRCODE_INVALIDO` |
| `1501.00` | 200 | consent `REJECTED`, reason `VALOR_ACIMA_LIMITE` |



**Exemplos de request/response:**

<details>
<summary><code>300.01</code></summary>

**Request** `POST /open-banking/payments/v5/consents`

```json
{
  "loggedUser": {
    "document": {
      "identification": "76109277673",
      "rel": "CPF"
    }
  },
  "creditor": {
    "personType": "PESSOA_NATURAL",
    "cpfCnpj": "76109277673",
    "name": "Recebedor Exemplo"
  },
  "payment": {
    "type": "PIX",
    "currency": "BRL",
    "amount": "300.01",
    "details": {
      "localInstrument": "DICT",
      "proxy": "76109277673",
      "creditorAccount": {
        "number": "1234567890",
        "ispb": "12345678",
        "issuer": "1774",
        "accountType": "CACC"
      }
    },
    "purpose": "IMMEDIATE",
    "date": "2026-08-25"
  }
}
```

**Response** `HTTP 200 (retornado no GET do consent)`

```json
{
  "aud": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "data": {
    "consentId": "urn:raidiambank:payment-consent:5aaf4de1-f7c5-4631-acf8-701ea13fbc85",
    "creationDateTime": "2026-08-25T18:42:03Z",
    "expirationDateTime": "2026-08-25T18:47:03Z",
    "statusUpdateDateTime": "2026-08-25T18:42:04Z",
    "status": "REJECTED",
    "loggedUser": {
      "document": {
        "identification": "76109277673",
        "rel": "CPF"
      }
    },
    "creditor": {
      "personType": "PESSOA_NATURAL",
      "cpfCnpj": "76109277673",
      "name": "Recebedor Exemplo"
    },
    "payment": {
      "type": "PIX",
      "purpose": "IMMEDIATE",
      "date": "2026-08-25",
      "currency": "BRL",
      "amount": "300.01",
      "details": {
        "localInstrument": "DICT",
        "proxy": "76109277673",
        "creditorAccount": {
          "ispb": "12345678",
          "issuer": "1774",
          "number": "1234567890",
          "accountType": "CACC"
        }
      }
    },
    "rejectionReason": {
      "code": "VALOR_INVALIDO",
      "detail": "O valor enviado não é válido para o QR Code informado;"
    }
  },
  "meta": {
    "requestDateTime": "2026-08-25T15:42:04Z"
  },
  "iss": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "links": {
    "self": "https://api.local/open-banking/payments/v5/consents/urn:raidiambank:payment-consent:5aaf4de1-f7c5-4631-acf8-701ea13fbc85"
  },
  "iat": 1787683324,
  "jti": "ec2ef56a-41b0-4cd6-8ca0-bcabfad91a0f"
}
```

</details>

<details>
<summary><code>300.02</code></summary>

**Request** `POST /open-banking/payments/v5/consents`

```json
{
  "loggedUser": {
    "document": {
      "identification": "76109277673",
      "rel": "CPF"
    }
  },
  "creditor": {
    "personType": "PESSOA_NATURAL",
    "cpfCnpj": "76109277673",
    "name": "Recebedor Exemplo"
  },
  "payment": {
    "type": "PIX",
    "currency": "BRL",
    "amount": "300.02",
    "details": {
      "localInstrument": "DICT",
      "proxy": "76109277673",
      "creditorAccount": {
        "number": "1234567890",
        "ispb": "12345678",
        "issuer": "1774",
        "accountType": "CACC"
      }
    },
    "purpose": "IMMEDIATE",
    "date": "2026-08-25"
  }
}
```

**Response** `HTTP 200 (retornado no GET do consent)`

```json
{
  "aud": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "data": {
    "consentId": "urn:raidiambank:payment-consent:bb093bbb-31b3-441f-9775-b899a3486e27",
    "creationDateTime": "2026-08-25T18:42:04Z",
    "expirationDateTime": "2026-08-25T18:47:04Z",
    "statusUpdateDateTime": "2026-08-25T18:42:04Z",
    "status": "REJECTED",
    "loggedUser": {
      "document": {
        "identification": "76109277673",
        "rel": "CPF"
      }
    },
    "creditor": {
      "personType": "PESSOA_NATURAL",
      "cpfCnpj": "76109277673",
      "name": "Recebedor Exemplo"
    },
    "payment": {
      "type": "PIX",
      "purpose": "IMMEDIATE",
      "date": "2026-08-25",
      "currency": "BRL",
      "amount": "300.02",
      "details": {
        "localInstrument": "DICT",
        "proxy": "76109277673",
        "creditorAccount": {
          "ispb": "12345678",
          "issuer": "1774",
          "number": "1234567890",
          "accountType": "CACC"
        }
      }
    },
    "rejectionReason": {
      "code": "NAO_INFORMADO",
      "detail": "Não informada pela detentora de conta;"
    }
  },
  "meta": {
    "requestDateTime": "2026-08-25T15:42:04Z"
  },
  "iss": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "links": {
    "self": "https://api.local/open-banking/payments/v5/consents/urn:raidiambank:payment-consent:bb093bbb-31b3-441f-9775-b899a3486e27"
  },
  "iat": 1787683324,
  "jti": "1661a79c-9817-4ce4-ad9a-95915ddb11fb"
}
```

</details>

<details>
<summary><code>300.03</code></summary>

**Request** `POST /open-banking/payments/v5/consents`

```json
{
  "loggedUser": {
    "document": {
      "identification": "76109277673",
      "rel": "CPF"
    }
  },
  "creditor": {
    "personType": "PESSOA_NATURAL",
    "cpfCnpj": "76109277673",
    "name": "Recebedor Exemplo"
  },
  "payment": {
    "type": "PIX",
    "currency": "BRL",
    "amount": "300.03",
    "details": {
      "localInstrument": "DICT",
      "proxy": "76109277673",
      "creditorAccount": {
        "number": "1234567890",
        "ispb": "12345678",
        "issuer": "1774",
        "accountType": "CACC"
      }
    },
    "purpose": "IMMEDIATE",
    "date": "2026-08-25"
  }
}
```

**Response** `HTTP 200 (retornado no GET do consent)`

```json
{
  "aud": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "data": {
    "consentId": "urn:raidiambank:payment-consent:290acd9a-f825-4404-aa06-e20db3358d63",
    "creationDateTime": "2026-08-25T18:42:04Z",
    "expirationDateTime": "2026-08-25T18:47:04Z",
    "statusUpdateDateTime": "2026-08-25T18:42:04Z",
    "status": "REJECTED",
    "loggedUser": {
      "document": {
        "identification": "76109277673",
        "rel": "CPF"
      }
    },
    "creditor": {
      "personType": "PESSOA_NATURAL",
      "cpfCnpj": "76109277673",
      "name": "Recebedor Exemplo"
    },
    "payment": {
      "type": "PIX",
      "purpose": "IMMEDIATE",
      "date": "2026-08-25",
      "currency": "BRL",
      "amount": "300.03",
      "details": {
        "localInstrument": "DICT",
        "proxy": "76109277673",
        "creditorAccount": {
          "ispb": "12345678",
          "issuer": "1774",
          "number": "1234567890",
          "accountType": "CACC"
        }
      }
    },
    "rejectionReason": {
      "code": "FALHA_INFRAESTRUTURA",
      "detail": "O valor enviado não é válido para o QR Code informado;"
    }
  },
  "meta": {
    "requestDateTime": "2026-08-25T15:42:04Z"
  },
  "iss": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "links": {
    "self": "https://api.local/open-banking/payments/v5/consents/urn:raidiambank:payment-consent:290acd9a-f825-4404-aa06-e20db3358d63"
  },
  "iat": 1787683324,
  "jti": "b6671bb2-b36e-4ba1-83de-eecc447fee7e"
}
```

</details>

<details>
<summary><code>300.04</code></summary>

**Request** `POST /open-banking/payments/v5/consents`

```json
{
  "loggedUser": {
    "document": {
      "identification": "76109277673",
      "rel": "CPF"
    }
  },
  "creditor": {
    "personType": "PESSOA_NATURAL",
    "cpfCnpj": "76109277673",
    "name": "Recebedor Exemplo"
  },
  "payment": {
    "type": "PIX",
    "currency": "BRL",
    "amount": "300.04",
    "details": {
      "localInstrument": "DICT",
      "proxy": "76109277673",
      "creditorAccount": {
        "number": "1234567890",
        "ispb": "12345678",
        "issuer": "1774",
        "accountType": "CACC"
      }
    },
    "purpose": "IMMEDIATE",
    "date": "2026-08-25"
  }
}
```

**Response** `HTTP 200 (retornado no GET do consent)`

```json
{
  "aud": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "data": {
    "consentId": "urn:raidiambank:payment-consent:63a00814-342c-4408-964d-b0b8028a1d8f",
    "creationDateTime": "2026-08-25T18:42:04Z",
    "expirationDateTime": "2026-08-25T18:47:04Z",
    "statusUpdateDateTime": "2026-08-25T18:42:04Z",
    "status": "REJECTED",
    "loggedUser": {
      "document": {
        "identification": "76109277673",
        "rel": "CPF"
      }
    },
    "creditor": {
      "personType": "PESSOA_NATURAL",
      "cpfCnpj": "76109277673",
      "name": "Recebedor Exemplo"
    },
    "payment": {
      "type": "PIX",
      "purpose": "IMMEDIATE",
      "date": "2026-08-25",
      "currency": "BRL",
      "amount": "300.04",
      "details": {
        "localInstrument": "DICT",
        "proxy": "76109277673",
        "creditorAccount": {
          "ispb": "12345678",
          "issuer": "1774",
          "number": "1234567890",
          "accountType": "CACC"
        }
      }
    },
    "rejectionReason": {
      "code": "TEMPO_EXPIRADO_CONSUMO",
      "detail": "Consentimento expirou antes que o usuário pudesse confirmá-lo."
    }
  },
  "meta": {
    "requestDateTime": "2026-08-25T15:42:04Z"
  },
  "iss": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "links": {
    "self": "https://api.local/open-banking/payments/v5/consents/urn:raidiambank:payment-consent:63a00814-342c-4408-964d-b0b8028a1d8f"
  },
  "iat": 1787683324,
  "jti": "d93822b4-733c-4ccb-8795-eddd0d3856bd"
}
```

</details>

<details>
<summary><code>300.05</code></summary>

**Request** `POST /open-banking/payments/v5/consents`

```json
{
  "loggedUser": {
    "document": {
      "identification": "76109277673",
      "rel": "CPF"
    }
  },
  "creditor": {
    "personType": "PESSOA_NATURAL",
    "cpfCnpj": "76109277673",
    "name": "Recebedor Exemplo"
  },
  "payment": {
    "type": "PIX",
    "currency": "BRL",
    "amount": "300.05",
    "details": {
      "localInstrument": "DICT",
      "proxy": "76109277673",
      "creditorAccount": {
        "number": "1234567890",
        "ispb": "12345678",
        "issuer": "1774",
        "accountType": "CACC"
      }
    },
    "purpose": "IMMEDIATE",
    "date": "2026-08-25"
  }
}
```

**Response** `HTTP 200 (retornado no GET do consent)`

```json
{
  "aud": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "data": {
    "consentId": "urn:raidiambank:payment-consent:9cad91bb-feb1-41ad-ba23-06d073a68803",
    "creationDateTime": "2026-08-25T18:42:04Z",
    "expirationDateTime": "2026-08-25T18:47:04Z",
    "statusUpdateDateTime": "2026-08-25T18:42:04Z",
    "status": "REJECTED",
    "loggedUser": {
      "document": {
        "identification": "76109277673",
        "rel": "CPF"
      }
    },
    "creditor": {
      "personType": "PESSOA_NATURAL",
      "cpfCnpj": "76109277673",
      "name": "Recebedor Exemplo"
    },
    "payment": {
      "type": "PIX",
      "purpose": "IMMEDIATE",
      "date": "2026-08-25",
      "currency": "BRL",
      "amount": "300.05",
      "details": {
        "localInstrument": "DICT",
        "proxy": "76109277673",
        "creditorAccount": {
          "ispb": "12345678",
          "issuer": "1774",
          "number": "1234567890",
          "accountType": "CACC"
        }
      }
    },
    "rejectionReason": {
      "code": "CONTA_NAO_PERMITE_PAGAMENTO",
      "detail": "A conta selecionada é do tipo [salario/investimento/liquidação/outros] e não permite realizar esse pagamento."
    }
  },
  "meta": {
    "requestDateTime": "2026-08-25T15:42:04Z"
  },
  "iss": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "links": {
    "self": "https://api.local/open-banking/payments/v5/consents/urn:raidiambank:payment-consent:9cad91bb-feb1-41ad-ba23-06d073a68803"
  },
  "iat": 1787683324,
  "jti": "c9577422-2f07-492d-9de9-9df312a8e445"
}
```

</details>

<details>
<summary><code>300.06</code></summary>

**Request** `POST /open-banking/payments/v5/consents`

```json
{
  "loggedUser": {
    "document": {
      "identification": "76109277673",
      "rel": "CPF"
    }
  },
  "creditor": {
    "personType": "PESSOA_NATURAL",
    "cpfCnpj": "76109277673",
    "name": "Recebedor Exemplo"
  },
  "payment": {
    "type": "PIX",
    "currency": "BRL",
    "amount": "300.06",
    "details": {
      "localInstrument": "DICT",
      "proxy": "76109277673",
      "creditorAccount": {
        "number": "1234567890",
        "ispb": "12345678",
        "issuer": "1774",
        "accountType": "CACC"
      }
    },
    "purpose": "IMMEDIATE",
    "date": "2026-08-25"
  }
}
```

**Response** `HTTP 200 (retornado no GET do consent)`

```json
{
  "aud": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "data": {
    "consentId": "urn:raidiambank:payment-consent:818fd61f-75dc-4baa-8650-835100a76651",
    "creationDateTime": "2026-08-25T18:42:04Z",
    "expirationDateTime": "2026-08-25T18:47:04Z",
    "statusUpdateDateTime": "2026-08-25T18:42:04Z",
    "status": "REJECTED",
    "loggedUser": {
      "document": {
        "identification": "76109277673",
        "rel": "CPF"
      }
    },
    "creditor": {
      "personType": "PESSOA_NATURAL",
      "cpfCnpj": "76109277673",
      "name": "Recebedor Exemplo"
    },
    "payment": {
      "type": "PIX",
      "purpose": "IMMEDIATE",
      "date": "2026-08-25",
      "currency": "BRL",
      "amount": "300.06",
      "details": {
        "localInstrument": "DICT",
        "proxy": "76109277673",
        "creditorAccount": {
          "ispb": "12345678",
          "issuer": "1774",
          "number": "1234567890",
          "accountType": "CACC"
        }
      }
    },
    "rejectionReason": {
      "code": "NAO_INFORMADO",
      "detail": "A conta selecionada não possui saldo suficiente para realizar o pagamento."
    }
  },
  "meta": {
    "requestDateTime": "2026-08-25T15:42:04Z"
  },
  "iss": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "links": {
    "self": "https://api.local/open-banking/payments/v5/consents/urn:raidiambank:payment-consent:818fd61f-75dc-4baa-8650-835100a76651"
  },
  "iat": 1787683324,
  "jti": "acb9c3ed-5b43-4858-82f0-2f9de90086b1"
}
```

</details>

<details>
<summary><code>300.07</code></summary>

**Request** `POST /open-banking/payments/v5/consents`

```json
{
  "loggedUser": {
    "document": {
      "identification": "76109277673",
      "rel": "CPF"
    }
  },
  "creditor": {
    "personType": "PESSOA_NATURAL",
    "cpfCnpj": "76109277673",
    "name": "Recebedor Exemplo"
  },
  "payment": {
    "type": "PIX",
    "currency": "BRL",
    "amount": "300.07",
    "details": {
      "localInstrument": "DICT",
      "proxy": "76109277673",
      "creditorAccount": {
        "number": "1234567890",
        "ispb": "12345678",
        "issuer": "1774",
        "accountType": "CACC"
      }
    },
    "purpose": "IMMEDIATE",
    "date": "2026-08-25"
  }
}
```

**Response** `HTTP 200 (retornado no GET do consent)`

```json
{
  "aud": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "data": {
    "consentId": "urn:raidiambank:payment-consent:1e0709c9-d3d1-42c9-bf36-3140e43525c7",
    "creationDateTime": "2026-08-25T18:42:04Z",
    "expirationDateTime": "2026-08-25T18:47:04Z",
    "statusUpdateDateTime": "2026-08-25T18:42:04Z",
    "status": "REJECTED",
    "loggedUser": {
      "document": {
        "identification": "76109277673",
        "rel": "CPF"
      }
    },
    "creditor": {
      "personType": "PESSOA_NATURAL",
      "cpfCnpj": "76109277673",
      "name": "Recebedor Exemplo"
    },
    "payment": {
      "type": "PIX",
      "purpose": "IMMEDIATE",
      "date": "2026-08-25",
      "currency": "BRL",
      "amount": "300.07",
      "details": {
        "localInstrument": "DICT",
        "proxy": "76109277673",
        "creditorAccount": {
          "ispb": "12345678",
          "issuer": "1774",
          "number": "1234567890",
          "accountType": "CACC"
        }
      }
    },
    "rejectionReason": {
      "code": "NAO_INFORMADO",
      "detail": "O valor ultrapassa o limite estabelecido [na instituição/no arranjo/outro] para permitir a realização de transações pelo cliente."
    }
  },
  "meta": {
    "requestDateTime": "2026-08-25T15:42:04Z"
  },
  "iss": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "links": {
    "self": "https://api.local/open-banking/payments/v5/consents/urn:raidiambank:payment-consent:1e0709c9-d3d1-42c9-bf36-3140e43525c7"
  },
  "iat": 1787683324,
  "jti": "73d3cc27-54a6-4396-9df3-08f27b1288c7"
}
```

</details>

<details>
<summary><code>300.08</code></summary>

**Request** `POST /open-banking/payments/v5/consents`

```json
{
  "loggedUser": {
    "document": {
      "identification": "76109277673",
      "rel": "CPF"
    }
  },
  "creditor": {
    "personType": "PESSOA_NATURAL",
    "cpfCnpj": "76109277673",
    "name": "Recebedor Exemplo"
  },
  "payment": {
    "type": "PIX",
    "currency": "BRL",
    "amount": "300.08",
    "details": {
      "localInstrument": "DICT",
      "proxy": "76109277673",
      "creditorAccount": {
        "number": "1234567890",
        "ispb": "12345678",
        "issuer": "1774",
        "accountType": "CACC"
      }
    },
    "purpose": "IMMEDIATE",
    "date": "2026-08-25"
  }
}
```

**Response** `HTTP 200 (retornado no GET do consent)`

```json
{
  "aud": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "data": {
    "consentId": "urn:raidiambank:payment-consent:3e6254a1-d23c-4813-b9e6-4400acc9fc14",
    "creationDateTime": "2026-08-25T18:42:04Z",
    "expirationDateTime": "2026-08-25T18:47:04Z",
    "statusUpdateDateTime": "2026-08-25T18:42:04Z",
    "status": "REJECTED",
    "loggedUser": {
      "document": {
        "identification": "76109277673",
        "rel": "CPF"
      }
    },
    "creditor": {
      "personType": "PESSOA_NATURAL",
      "cpfCnpj": "76109277673",
      "name": "Recebedor Exemplo"
    },
    "payment": {
      "type": "PIX",
      "purpose": "IMMEDIATE",
      "date": "2026-08-25",
      "currency": "BRL",
      "amount": "300.08",
      "details": {
        "localInstrument": "DICT",
        "proxy": "76109277673",
        "creditorAccount": {
          "ispb": "12345678",
          "issuer": "1774",
          "number": "1234567890",
          "accountType": "CACC"
        }
      }
    },
    "rejectionReason": {
      "code": "QRCODE_INVALIDO",
      "detail": "O QRCode utilizado para a iniciação de pagamento não é válido."
    }
  },
  "meta": {
    "requestDateTime": "2026-08-25T15:42:04Z"
  },
  "iss": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "links": {
    "self": "https://api.local/open-banking/payments/v5/consents/urn:raidiambank:payment-consent:3e6254a1-d23c-4813-b9e6-4400acc9fc14"
  },
  "iat": 1787683324,
  "jti": "606dda80-fb6c-4b65-b956-13b84b386482"
}
```

</details>

<details>
<summary><code>1501.00</code></summary>

**Request** `POST /open-banking/payments/v5/consents`

```json
{
  "loggedUser": {
    "document": {
      "identification": "76109277673",
      "rel": "CPF"
    }
  },
  "creditor": {
    "personType": "PESSOA_NATURAL",
    "cpfCnpj": "76109277673",
    "name": "Recebedor Exemplo"
  },
  "payment": {
    "type": "PIX",
    "currency": "BRL",
    "amount": "1501.00",
    "details": {
      "localInstrument": "DICT",
      "proxy": "76109277673",
      "creditorAccount": {
        "number": "1234567890",
        "ispb": "12345678",
        "issuer": "1774",
        "accountType": "CACC"
      }
    },
    "purpose": "IMMEDIATE",
    "date": "2026-08-25"
  }
}
```

**Response** `HTTP 200 (retornado no GET do consent)`

```json
{
  "aud": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "data": {
    "consentId": "urn:raidiambank:payment-consent:3624f4a3-659c-4fdc-b991-e54d092e58d6",
    "creationDateTime": "2026-08-25T18:42:04Z",
    "expirationDateTime": "2026-08-25T18:47:04Z",
    "statusUpdateDateTime": "2026-08-25T18:42:04Z",
    "status": "REJECTED",
    "loggedUser": {
      "document": {
        "identification": "76109277673",
        "rel": "CPF"
      }
    },
    "creditor": {
      "personType": "PESSOA_NATURAL",
      "cpfCnpj": "76109277673",
      "name": "Recebedor Exemplo"
    },
    "payment": {
      "type": "PIX",
      "purpose": "IMMEDIATE",
      "date": "2026-08-25",
      "currency": "BRL",
      "amount": "1501.00",
      "details": {
        "localInstrument": "DICT",
        "proxy": "76109277673",
        "creditorAccount": {
          "ispb": "12345678",
          "issuer": "1774",
          "number": "1234567890",
          "accountType": "CACC"
        }
      }
    },
    "rejectionReason": {
      "code": "VALOR_ACIMA_LIMITE",
      "detail": "O valor excedeu limite operacional."
    }
  },
  "meta": {
    "requestDateTime": "2026-08-25T15:42:04Z"
  },
  "iss": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "links": {
    "self": "https://api.local/open-banking/payments/v5/consents/urn:raidiambank:payment-consent:3624f4a3-659c-4fdc-b991-e54d092e58d6"
  },
  "iat": 1787683324,
  "jti": "b7905765-792b-4ab4-a168-cce357c2e0f6"
}
```

</details>

### A3. Reject the pix payment at initiation (immediate)

- **API:** Payment Initiation V5
- **Endpoint:** `POST /open-banking/payments/v5/pix/payments`
- **Field:** `data[0].payment.amount` (`data` is an array)

| Value | HTTP | Outcome |
|-------|------|---------|
| `20422.00` | 422 | rejected, "Forced a 422 for payment request" |
| `20422.01` | 422 | rejected, `DETALHE_PAGAMENTO_INVALIDO` |
| `20422.02` | 422 | rejected, `VALOR_INVALIDO` |
| `20422.03` | 422 | rejected, `PAGAMENTO_DIVERGENTE_CONSENTIMENTO` |



**Exemplos de request/response:**

<details>
<summary><code>20422.00</code></summary>

**Request** `POST /open-banking/payments/v5/pix/payments`

```json
[
  {
    "consentId": "urn:raidiambank:payment-consent:9059292a-74d5-4c56-a964-3366ae8f0730",
    "endToEndId": "E13884775202608251842c4c7827faef",
    "creditorAccount": {
      "number": "1234567890",
      "ispb": "12345678",
      "issuer": "1774",
      "accountType": "CACC"
    },
    "localInstrument": "DICT",
    "proxy": "76109277673",
    "payment": {
      "amount": "20422.00",
      "currency": "BRL"
    },
    "cnpjInitiator": "13884775000119",
    "authorisationFlow": "HYBRID_FLOW"
  }
]
```

**Response** `HTTP 422`

```json
{
  "iss": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "aud": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "iat": 1787683324,
  "meta": {
    "requestDateTime": "2026-08-25T18:42:04Z"
  },
  "errors": [
    {
      "code": "Forced a 422 for payment request",
      "title": "Forced a 422 for payment request",
      "detail": "Forced a 422 for payment request"
    }
  ],
  "jti": "0a88f179-3eda-4fca-85b5-fe1fe924fa7a"
}
```

</details>

<details>
<summary><code>20422.01</code></summary>

**Request** `POST /open-banking/payments/v5/pix/payments`

```json
[
  {
    "consentId": "urn:raidiambank:payment-consent:e1f76c7e-a011-437b-8b7b-61b62382aaf6",
    "endToEndId": "E1388477520260825184212975b96c56",
    "creditorAccount": {
      "number": "1234567890",
      "ispb": "12345678",
      "issuer": "1774",
      "accountType": "CACC"
    },
    "localInstrument": "DICT",
    "proxy": "76109277673",
    "payment": {
      "amount": "20422.01",
      "currency": "BRL"
    },
    "cnpjInitiator": "13884775000119",
    "authorisationFlow": "HYBRID_FLOW"
  }
]
```

**Response** `HTTP 422`

```json
{
  "iss": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "aud": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "iat": 1787683324,
  "meta": {
    "requestDateTime": "2026-08-25T18:42:04Z"
  },
  "errors": [
    {
      "code": "DETALHE_PAGAMENTO_INVALIDO",
      "title": "Detalhe do pagamento inválido.",
      "detail": "DETALHE_PAGAMENTO_INVALIDO"
    }
  ],
  "jti": "a7aeb108-905a-403b-b60b-f43477231823"
}
```

</details>

<details>
<summary><code>20422.02</code></summary>

**Request** `POST /open-banking/payments/v5/pix/payments`

```json
[
  {
    "consentId": "urn:raidiambank:payment-consent:f1e022c8-e695-4ef4-8dc0-57420936fe25",
    "endToEndId": "E138847752026082518426c341a44e81",
    "creditorAccount": {
      "number": "1234567890",
      "ispb": "12345678",
      "issuer": "1774",
      "accountType": "CACC"
    },
    "localInstrument": "DICT",
    "proxy": "76109277673",
    "payment": {
      "amount": "20422.02",
      "currency": "BRL"
    },
    "cnpjInitiator": "13884775000119",
    "authorisationFlow": "HYBRID_FLOW"
  }
]
```

**Response** `HTTP 422`

```json
{
  "iss": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "aud": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "iat": 1787683324,
  "meta": {
    "requestDateTime": "2026-08-25T18:42:04Z"
  },
  "errors": [
    {
      "code": "VALOR_INVALIDO",
      "title": "O valor enviado não é válido para o QR Code informado.",
      "detail": "VALOR_INVALIDO"
    }
  ],
  "jti": "3b433b4a-e5ed-4102-9614-c95a7088a7fb"
}
```

</details>

<details>
<summary><code>20422.03</code></summary>

**Request** `POST /open-banking/payments/v5/pix/payments`

```json
[
  {
    "consentId": "urn:raidiambank:payment-consent:7751df18-655a-4994-bac8-80bf5185d9f3",
    "endToEndId": "E1388477520260825184237a872990f8",
    "creditorAccount": {
      "number": "1234567890",
      "ispb": "12345678",
      "issuer": "1774",
      "accountType": "CACC"
    },
    "localInstrument": "DICT",
    "proxy": "76109277673",
    "payment": {
      "amount": "20422.03",
      "currency": "BRL"
    },
    "cnpjInitiator": "13884775000119",
    "authorisationFlow": "HYBRID_FLOW"
  }
]
```

**Response** `HTTP 422`

```json
{
  "iss": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "aud": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "iat": 1787683324,
  "meta": {
    "requestDateTime": "2026-08-25T18:42:04Z"
  },
  "errors": [
    {
      "code": "PAGAMENTO_DIVERGENTE_CONSENTIMENTO",
      "title": "Divergência entre pagamento e consentimento",
      "detail": "PAGAMENTO_DIVERGENTE_CONSENTIMENTO"
    }
  ],
  "jti": "1f32fffb-a8b4-4818-814f-2a9137b7eb9f"
}
```

</details>

### A4. Move the pix payment to a final state after it was accepted

- **API:** Payment Initiation V5
- **Endpoint (to read):** `GET /open-banking/payments/v5/pix/payments/{paymentId}`
- **Field:** `data[0].payment.amount` (the same value sent in the consent)

How to use:

1. Create the consent and initiate the pix payment with the trigger amount. The payment is accepted and returns normally (`RCVD`).
2. Fetch the payment by its `paymentId` with the GET above.
3. On that GET the mock moves the payment to the state below and returns it.

| Value | HTTP | Payment state returned |
|-------|------|------------------------|
| `20201.00` | 200 | `RJCT`, reason `DETALHE_PAGAMENTO_INVALIDO` |
| `20201.10` | 200 | `RJCT`, reason `PAGAMENTO_RECUSADO_DETENTORA` |
| `20201.20` | 200 | `RJCT`, reason `VALOR_INVALIDO` |
| `20201.30` | 200 | `RJCT`, reason `VALOR_ACIMA_LIMITE` |
| `20201.50` | 200 | `RJCT`, reason `COBRANCA_INVALIDA` |
| `999999999.99` | 200 | `RJCT`, reason `SALDO_INSUFICIENTE` |
| `1333.00`-`1333.99` | 200 | `ACSC` |
| `1334.00` | 200 | `ACPD` |
| `1335.00` | 200 | `ACCP` |
| `1336.00` | 200 | `ACSC` |
| `1400.00` | 200 | `SCHD` (if scheduled), then `CANC` (reason `AGENDAMENTO`) 3 minutes after creation |
| `12345.00` | 200 | `PDNG`, then `ACSC` on a GET more than 1 minute later |
| `12345.67` | 200 | `PDNG` |

> `1333.00`-`1333.99`, `1334.00` and `1335.00` also auto-authorise a still-pending consent (skipping the redirect); `1336.00` does not.



**Exemplos de request/response:**

<details>
<summary><code>20201.00</code></summary>

**Request** `POST /open-banking/payments/v5/pix/payments`

```json
[
  {
    "consentId": "urn:raidiambank:payment-consent:72ec4fc0-6fc1-45a8-a711-03f4fb182e16",
    "endToEndId": "E138847752026082518428eefd184949",
    "creditorAccount": {
      "number": "1234567890",
      "ispb": "12345678",
      "issuer": "1774",
      "accountType": "CACC"
    },
    "localInstrument": "DICT",
    "proxy": "76109277673",
    "payment": {
      "amount": "20201.00",
      "currency": "BRL"
    },
    "cnpjInitiator": "13884775000119",
    "authorisationFlow": "HYBRID_FLOW"
  }
]
```

**Response** `HTTP 200 (retornado no GET do pagamento)`

```json
{
  "aud": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "data": {
    "paymentId": "77281e14-be66-4521-81fe-10faf2487ead",
    "endToEndId": "E138847752026082518428eefd184949",
    "consentId": "urn:raidiambank:payment-consent:72ec4fc0-6fc1-45a8-a711-03f4fb182e16",
    "creationDateTime": "2026-08-25T18:42:05Z",
    "statusUpdateDateTime": "2026-08-25T18:42:05Z",
    "proxy": "76109277673",
    "status": "RJCT",
    "rejectionReason": {
      "code": "DETALHE_PAGAMENTO_INVALIDO",
      "detail": "DETALHE_PAGAMENTO_INVALIDO"
    },
    "localInstrument": "DICT",
    "cnpjInitiator": "13884775000119",
    "payment": {
      "amount": "20201.00",
      "currency": "BRL"
    },
    "creditorAccount": {
      "ispb": "12345678",
      "issuer": "1774",
      "number": "1234567890",
      "accountType": "CACC"
    },
    "debtorAccount": {
      "ispb": "12345678",
      "issuer": "6272",
      "number": "94088392",
      "accountType": "CACC"
    },
    "authorisationFlow": "HYBRID_FLOW"
  },
  "meta": {
    "requestDateTime": "2026-08-25T15:42:06Z"
  },
  "iss": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "links": {
    "self": "https://api.local/open-banking/payments/v5/pix/payments/77281e14-be66-4521-81fe-10faf2487ead"
  },
  "iat": 1787683326,
  "jti": "951d1734-f005-4e25-85ce-ca1b11925460"
}
```

</details>

<details>
<summary><code>20201.10</code></summary>

**Request** `POST /open-banking/payments/v5/pix/payments`

```json
[
  {
    "consentId": "urn:raidiambank:payment-consent:5320d692-ae3d-41eb-838c-44b573a8a4a9",
    "endToEndId": "E13884775202608251842db4a433f35a",
    "creditorAccount": {
      "number": "1234567890",
      "ispb": "12345678",
      "issuer": "1774",
      "accountType": "CACC"
    },
    "localInstrument": "DICT",
    "proxy": "76109277673",
    "payment": {
      "amount": "20201.10",
      "currency": "BRL"
    },
    "cnpjInitiator": "13884775000119",
    "authorisationFlow": "HYBRID_FLOW"
  }
]
```

**Response** `HTTP 200 (retornado no GET do pagamento)`

```json
{
  "aud": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "data": {
    "paymentId": "19e2161a-d96a-497e-9bb6-e4d6141c0839",
    "endToEndId": "E13884775202608251842db4a433f35a",
    "consentId": "urn:raidiambank:payment-consent:5320d692-ae3d-41eb-838c-44b573a8a4a9",
    "creationDateTime": "2026-08-25T18:42:07Z",
    "statusUpdateDateTime": "2026-08-25T18:42:07Z",
    "proxy": "76109277673",
    "status": "RJCT",
    "rejectionReason": {
      "code": "PAGAMENTO_RECUSADO_DETENTORA",
      "detail": "PAGAMENTO_RECUSADO_DETENTORA"
    },
    "localInstrument": "DICT",
    "cnpjInitiator": "13884775000119",
    "payment": {
      "amount": "20201.10",
      "currency": "BRL"
    },
    "creditorAccount": {
      "ispb": "12345678",
      "issuer": "1774",
      "number": "1234567890",
      "accountType": "CACC"
    },
    "debtorAccount": {
      "ispb": "12345678",
      "issuer": "6272",
      "number": "94088392",
      "accountType": "CACC"
    },
    "authorisationFlow": "HYBRID_FLOW"
  },
  "meta": {
    "requestDateTime": "2026-08-25T15:42:08Z"
  },
  "iss": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "links": {
    "self": "https://api.local/open-banking/payments/v5/pix/payments/19e2161a-d96a-497e-9bb6-e4d6141c0839"
  },
  "iat": 1787683328,
  "jti": "fde1414c-bea6-47ad-a9ac-4f65499bc26f"
}
```

</details>

<details>
<summary><code>20201.20</code></summary>

**Request** `POST /open-banking/payments/v5/pix/payments`

```json
[
  {
    "consentId": "urn:raidiambank:payment-consent:b3294b28-7eec-4a54-8415-bdc440d6f6d4",
    "endToEndId": "E1388477520260825184212e99dc3d5d",
    "creditorAccount": {
      "number": "1234567890",
      "ispb": "12345678",
      "issuer": "1774",
      "accountType": "CACC"
    },
    "localInstrument": "DICT",
    "proxy": "76109277673",
    "payment": {
      "amount": "20201.20",
      "currency": "BRL"
    },
    "cnpjInitiator": "13884775000119",
    "authorisationFlow": "HYBRID_FLOW"
  }
]
```

**Response** `HTTP 200 (retornado no GET do pagamento)`

```json
{
  "aud": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "data": {
    "paymentId": "e6151eca-bddd-44ec-96bd-5245b4b58c39",
    "endToEndId": "E1388477520260825184212e99dc3d5d",
    "consentId": "urn:raidiambank:payment-consent:b3294b28-7eec-4a54-8415-bdc440d6f6d4",
    "creationDateTime": "2026-08-25T18:42:08Z",
    "statusUpdateDateTime": "2026-08-25T18:42:08Z",
    "proxy": "76109277673",
    "status": "RJCT",
    "rejectionReason": {
      "code": "VALOR_INVALIDO",
      "detail": "VALOR_INVALIDO"
    },
    "localInstrument": "DICT",
    "cnpjInitiator": "13884775000119",
    "payment": {
      "amount": "20201.20",
      "currency": "BRL"
    },
    "creditorAccount": {
      "ispb": "12345678",
      "issuer": "1774",
      "number": "1234567890",
      "accountType": "CACC"
    },
    "debtorAccount": {
      "ispb": "12345678",
      "issuer": "6272",
      "number": "94088392",
      "accountType": "CACC"
    },
    "authorisationFlow": "HYBRID_FLOW"
  },
  "meta": {
    "requestDateTime": "2026-08-25T15:42:09Z"
  },
  "iss": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "links": {
    "self": "https://api.local/open-banking/payments/v5/pix/payments/e6151eca-bddd-44ec-96bd-5245b4b58c39"
  },
  "iat": 1787683329,
  "jti": "d7bdff80-1dcb-4ede-a6ac-a5d9ba41b093"
}
```

</details>

<details>
<summary><code>20201.30</code></summary>

**Request** `POST /open-banking/payments/v5/pix/payments`

```json
[
  {
    "consentId": "urn:raidiambank:payment-consent:d6ebe393-24ee-44b6-8b7a-11f80d73cf75",
    "endToEndId": "E138847752026082518427a2db16d308",
    "creditorAccount": {
      "number": "1234567890",
      "ispb": "12345678",
      "issuer": "1774",
      "accountType": "CACC"
    },
    "localInstrument": "DICT",
    "proxy": "76109277673",
    "payment": {
      "amount": "20201.30",
      "currency": "BRL"
    },
    "cnpjInitiator": "13884775000119",
    "authorisationFlow": "HYBRID_FLOW"
  }
]
```

**Response** `HTTP 200 (retornado no GET do pagamento)`

```json
{
  "aud": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "data": {
    "paymentId": "9dfa79e2-e1d5-42f2-af67-408172f9a32e",
    "endToEndId": "E138847752026082518427a2db16d308",
    "consentId": "urn:raidiambank:payment-consent:d6ebe393-24ee-44b6-8b7a-11f80d73cf75",
    "creationDateTime": "2026-08-25T18:42:09Z",
    "statusUpdateDateTime": "2026-08-25T18:42:09Z",
    "proxy": "76109277673",
    "status": "RJCT",
    "rejectionReason": {
      "code": "VALOR_ACIMA_LIMITE",
      "detail": "VALOR_ACIMA_LIMITE"
    },
    "localInstrument": "DICT",
    "cnpjInitiator": "13884775000119",
    "payment": {
      "amount": "20201.30",
      "currency": "BRL"
    },
    "creditorAccount": {
      "ispb": "12345678",
      "issuer": "1774",
      "number": "1234567890",
      "accountType": "CACC"
    },
    "debtorAccount": {
      "ispb": "12345678",
      "issuer": "6272",
      "number": "94088392",
      "accountType": "CACC"
    },
    "authorisationFlow": "HYBRID_FLOW"
  },
  "meta": {
    "requestDateTime": "2026-08-25T15:42:10Z"
  },
  "iss": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "links": {
    "self": "https://api.local/open-banking/payments/v5/pix/payments/9dfa79e2-e1d5-42f2-af67-408172f9a32e"
  },
  "iat": 1787683330,
  "jti": "e942ce77-8cd0-4406-b075-e0d2cbea82c6"
}
```

</details>

<details>
<summary><code>20201.50</code></summary>

**Request** `POST /open-banking/payments/v5/pix/payments`

```json
[
  {
    "consentId": "urn:raidiambank:payment-consent:729952fe-abf8-42af-bc36-19aab649fd28",
    "endToEndId": "E1388477520260825184230d13196620",
    "creditorAccount": {
      "number": "1234567890",
      "ispb": "12345678",
      "issuer": "1774",
      "accountType": "CACC"
    },
    "localInstrument": "DICT",
    "proxy": "76109277673",
    "payment": {
      "amount": "20201.50",
      "currency": "BRL"
    },
    "cnpjInitiator": "13884775000119",
    "authorisationFlow": "HYBRID_FLOW"
  }
]
```

**Response** `HTTP 200 (retornado no GET do pagamento)`

```json
{
  "aud": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "data": {
    "paymentId": "d71c4360-bd13-48fd-9787-906ed3b195f7",
    "endToEndId": "E1388477520260825184230d13196620",
    "consentId": "urn:raidiambank:payment-consent:729952fe-abf8-42af-bc36-19aab649fd28",
    "creationDateTime": "2026-08-25T18:42:10Z",
    "statusUpdateDateTime": "2026-08-25T18:42:10Z",
    "proxy": "76109277673",
    "status": "RJCT",
    "rejectionReason": {
      "code": "COBRANCA_INVALIDA",
      "detail": "COBRANCA_INVALIDA"
    },
    "localInstrument": "DICT",
    "cnpjInitiator": "13884775000119",
    "payment": {
      "amount": "20201.50",
      "currency": "BRL"
    },
    "creditorAccount": {
      "ispb": "12345678",
      "issuer": "1774",
      "number": "1234567890",
      "accountType": "CACC"
    },
    "debtorAccount": {
      "ispb": "12345678",
      "issuer": "6272",
      "number": "94088392",
      "accountType": "CACC"
    },
    "authorisationFlow": "HYBRID_FLOW"
  },
  "meta": {
    "requestDateTime": "2026-08-25T15:42:11Z"
  },
  "iss": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "links": {
    "self": "https://api.local/open-banking/payments/v5/pix/payments/d71c4360-bd13-48fd-9787-906ed3b195f7"
  },
  "iat": 1787683331,
  "jti": "5f318523-6ab1-431b-9ea7-9adbba68a65d"
}
```

</details>

<details>
<summary><code>999999999.99</code></summary>

**Request** `POST /open-banking/payments/v5/pix/payments`

```json
[
  {
    "consentId": "urn:raidiambank:payment-consent:dcf6f5d5-e451-407f-b1c1-20f5ddb440a1",
    "endToEndId": "E138847752026082518426981a596269",
    "creditorAccount": {
      "number": "1234567890",
      "ispb": "12345678",
      "issuer": "1774",
      "accountType": "CACC"
    },
    "localInstrument": "DICT",
    "proxy": "76109277673",
    "payment": {
      "amount": "999999999.99",
      "currency": "BRL"
    },
    "cnpjInitiator": "13884775000119",
    "authorisationFlow": "HYBRID_FLOW"
  }
]
```

**Response** `HTTP 200 (retornado no GET do pagamento)`

```json
{
  "aud": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "data": {
    "paymentId": "3f754934-a38c-47a5-b6df-9075dbbc6842",
    "endToEndId": "E138847752026082518426981a596269",
    "consentId": "urn:raidiambank:payment-consent:dcf6f5d5-e451-407f-b1c1-20f5ddb440a1",
    "creationDateTime": "2026-08-25T18:42:12Z",
    "statusUpdateDateTime": "2026-08-25T18:42:12Z",
    "proxy": "76109277673",
    "status": "RJCT",
    "rejectionReason": {
      "code": "SALDO_INSUFICIENTE",
      "detail": "SALDO_INSUFICIENTE"
    },
    "localInstrument": "DICT",
    "cnpjInitiator": "13884775000119",
    "payment": {
      "amount": "999999999.99",
      "currency": "BRL"
    },
    "creditorAccount": {
      "ispb": "12345678",
      "issuer": "1774",
      "number": "1234567890",
      "accountType": "CACC"
    },
    "debtorAccount": {
      "ispb": "12345678",
      "issuer": "6272",
      "number": "94088392",
      "accountType": "CACC"
    },
    "authorisationFlow": "HYBRID_FLOW"
  },
  "meta": {
    "requestDateTime": "2026-08-25T15:42:13Z"
  },
  "iss": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "links": {
    "self": "https://api.local/open-banking/payments/v5/pix/payments/3f754934-a38c-47a5-b6df-9075dbbc6842"
  },
  "iat": 1787683333,
  "jti": "116ad332-7a4c-424a-8f08-304c36d42ece"
}
```

</details>

<details>
<summary><code>1333.00</code></summary>

**Request** `POST /open-banking/payments/v5/pix/payments`

```json
[
  {
    "consentId": "urn:raidiambank:payment-consent:e2627a41-51cb-4322-844e-bf7b7c48151c",
    "endToEndId": "E138847752026082518421e6d095bb23",
    "creditorAccount": {
      "number": "1234567890",
      "ispb": "12345678",
      "issuer": "1774",
      "accountType": "CACC"
    },
    "localInstrument": "DICT",
    "proxy": "76109277673",
    "payment": {
      "amount": "1333.00",
      "currency": "BRL"
    },
    "cnpjInitiator": "13884775000119",
    "authorisationFlow": "HYBRID_FLOW"
  }
]
```

**Response** `HTTP 200 (retornado no GET do pagamento)`

```json
{
  "aud": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "data": {
    "paymentId": "8de89f4d-8815-4222-8484-aed19887c055",
    "endToEndId": "E138847752026082518421e6d095bb23",
    "consentId": "urn:raidiambank:payment-consent:e2627a41-51cb-4322-844e-bf7b7c48151c",
    "creationDateTime": "2026-08-25T18:42:13Z",
    "statusUpdateDateTime": "2026-08-25T18:42:13Z",
    "proxy": "76109277673",
    "status": "ACSC",
    "localInstrument": "DICT",
    "cnpjInitiator": "13884775000119",
    "payment": {
      "amount": "1333.00",
      "currency": "BRL"
    },
    "creditorAccount": {
      "ispb": "12345678",
      "issuer": "1774",
      "number": "1234567890",
      "accountType": "CACC"
    },
    "debtorAccount": {
      "ispb": "12345678",
      "issuer": "6272",
      "number": "94088392",
      "accountType": "CACC"
    },
    "authorisationFlow": "HYBRID_FLOW"
  },
  "meta": {
    "requestDateTime": "2026-08-25T15:42:14Z"
  },
  "iss": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "links": {
    "self": "https://api.local/open-banking/payments/v5/pix/payments/8de89f4d-8815-4222-8484-aed19887c055"
  },
  "iat": 1787683334,
  "jti": "28b83589-f15a-47f9-bb58-263f4117143b"
}
```

</details>

<details>
<summary><code>1334.00</code></summary>

**Request** `POST /open-banking/payments/v5/pix/payments`

```json
[
  {
    "consentId": "urn:raidiambank:payment-consent:424d1eb3-8958-432b-bf74-37b578278deb",
    "endToEndId": "E13884775202608251842b003500a4b4",
    "creditorAccount": {
      "number": "1234567890",
      "ispb": "12345678",
      "issuer": "1774",
      "accountType": "CACC"
    },
    "localInstrument": "DICT",
    "proxy": "76109277673",
    "payment": {
      "amount": "1334.00",
      "currency": "BRL"
    },
    "cnpjInitiator": "13884775000119",
    "authorisationFlow": "HYBRID_FLOW"
  }
]
```

**Response** `HTTP 200 (retornado no GET do pagamento)`

```json
{
  "aud": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "data": {
    "paymentId": "10af118f-64b8-4c7e-bfd5-b174c40fbaab",
    "endToEndId": "E13884775202608251842b003500a4b4",
    "consentId": "urn:raidiambank:payment-consent:424d1eb3-8958-432b-bf74-37b578278deb",
    "creationDateTime": "2026-08-25T18:42:14Z",
    "statusUpdateDateTime": "2026-08-25T18:42:14Z",
    "proxy": "76109277673",
    "status": "ACPD",
    "localInstrument": "DICT",
    "cnpjInitiator": "13884775000119",
    "payment": {
      "amount": "1334.00",
      "currency": "BRL"
    },
    "creditorAccount": {
      "ispb": "12345678",
      "issuer": "1774",
      "number": "1234567890",
      "accountType": "CACC"
    },
    "debtorAccount": {
      "ispb": "12345678",
      "issuer": "6272",
      "number": "94088392",
      "accountType": "CACC"
    },
    "authorisationFlow": "HYBRID_FLOW"
  },
  "meta": {
    "requestDateTime": "2026-08-25T15:42:15Z"
  },
  "iss": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "links": {
    "self": "https://api.local/open-banking/payments/v5/pix/payments/10af118f-64b8-4c7e-bfd5-b174c40fbaab"
  },
  "iat": 1787683335,
  "jti": "54a0c0a5-691e-49a4-8e23-eec3897a588c"
}
```

</details>

<details>
<summary><code>1335.00</code></summary>

**Request** `POST /open-banking/payments/v5/pix/payments`

```json
[
  {
    "consentId": "urn:raidiambank:payment-consent:f3ae95ca-6449-47c0-ba76-9f52d3f06632",
    "endToEndId": "E13884775202608251842ea6c9ed5455",
    "creditorAccount": {
      "number": "1234567890",
      "ispb": "12345678",
      "issuer": "1774",
      "accountType": "CACC"
    },
    "localInstrument": "DICT",
    "proxy": "76109277673",
    "payment": {
      "amount": "1335.00",
      "currency": "BRL"
    },
    "cnpjInitiator": "13884775000119",
    "authorisationFlow": "HYBRID_FLOW"
  }
]
```

**Response** `HTTP 200 (retornado no GET do pagamento)`

```json
{
  "aud": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "data": {
    "paymentId": "72ea5dc8-4dd6-49f0-a348-4202845a6b0e",
    "endToEndId": "E13884775202608251842ea6c9ed5455",
    "consentId": "urn:raidiambank:payment-consent:f3ae95ca-6449-47c0-ba76-9f52d3f06632",
    "creationDateTime": "2026-08-25T18:42:15Z",
    "statusUpdateDateTime": "2026-08-25T18:42:15Z",
    "proxy": "76109277673",
    "status": "ACCP",
    "localInstrument": "DICT",
    "cnpjInitiator": "13884775000119",
    "payment": {
      "amount": "1335.00",
      "currency": "BRL"
    },
    "creditorAccount": {
      "ispb": "12345678",
      "issuer": "1774",
      "number": "1234567890",
      "accountType": "CACC"
    },
    "debtorAccount": {
      "ispb": "12345678",
      "issuer": "6272",
      "number": "94088392",
      "accountType": "CACC"
    },
    "authorisationFlow": "HYBRID_FLOW"
  },
  "meta": {
    "requestDateTime": "2026-08-25T15:42:16Z"
  },
  "iss": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "links": {
    "self": "https://api.local/open-banking/payments/v5/pix/payments/72ea5dc8-4dd6-49f0-a348-4202845a6b0e"
  },
  "iat": 1787683336,
  "jti": "26f68c57-806a-4916-9766-d960250b4de0"
}
```

</details>

<details>
<summary><code>1336.00</code></summary>

**Request** `POST /open-banking/payments/v5/pix/payments`

```json
[
  {
    "consentId": "urn:raidiambank:payment-consent:7b46cf6e-b0c0-4f52-ad79-6074cc5d0ac4",
    "endToEndId": "E138847752026082518428079f5ab8a1",
    "creditorAccount": {
      "number": "1234567890",
      "ispb": "12345678",
      "issuer": "1774",
      "accountType": "CACC"
    },
    "localInstrument": "DICT",
    "proxy": "76109277673",
    "payment": {
      "amount": "1336.00",
      "currency": "BRL"
    },
    "cnpjInitiator": "13884775000119",
    "authorisationFlow": "HYBRID_FLOW"
  }
]
```

**Response** `HTTP 200 (retornado no GET do pagamento)`

```json
{
  "aud": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "data": {
    "paymentId": "f14fd1e4-36f5-4b16-bb3f-684db5b51c40",
    "endToEndId": "E138847752026082518428079f5ab8a1",
    "consentId": "urn:raidiambank:payment-consent:7b46cf6e-b0c0-4f52-ad79-6074cc5d0ac4",
    "creationDateTime": "2026-08-25T18:42:16Z",
    "statusUpdateDateTime": "2026-08-25T18:42:16Z",
    "proxy": "76109277673",
    "status": "ACSC",
    "localInstrument": "DICT",
    "cnpjInitiator": "13884775000119",
    "payment": {
      "amount": "1336.00",
      "currency": "BRL"
    },
    "creditorAccount": {
      "ispb": "12345678",
      "issuer": "1774",
      "number": "1234567890",
      "accountType": "CACC"
    },
    "debtorAccount": {
      "ispb": "12345678",
      "issuer": "6272",
      "number": "94088392",
      "accountType": "CACC"
    },
    "authorisationFlow": "HYBRID_FLOW"
  },
  "meta": {
    "requestDateTime": "2026-08-25T15:42:17Z"
  },
  "iss": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "links": {
    "self": "https://api.local/open-banking/payments/v5/pix/payments/f14fd1e4-36f5-4b16-bb3f-684db5b51c40"
  },
  "iat": 1787683337,
  "jti": "7b22c2b1-6242-4a4e-a8a9-75d115ab1dad"
}
```

</details>

<details>
<summary><code>1400.00</code></summary>

**Request** `POST /open-banking/payments/v5/pix/payments`

```json
[
  {
    "consentId": "urn:raidiambank:payment-consent:42febc01-1445-430c-9a90-7ada923e8ec4",
    "endToEndId": "E13884775202608271500802533db71c",
    "creditorAccount": {
      "number": "1234567890",
      "ispb": "12345678",
      "issuer": "1774",
      "accountType": "CACC"
    },
    "localInstrument": "DICT",
    "proxy": "76109277673",
    "payment": {
      "amount": "1400.00",
      "currency": "BRL"
    },
    "cnpjInitiator": "13884775000119",
    "authorisationFlow": "HYBRID_FLOW"
  }
]
```

**Response** `HTTP 200 (retornado no GET do pagamento)`

```json
{
  "aud": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "data": {
    "paymentId": "095b3706-7446-4f70-8522-601d62d608a9",
    "endToEndId": "E13884775202608271500802533db71c",
    "consentId": "urn:raidiambank:payment-consent:42febc01-1445-430c-9a90-7ada923e8ec4",
    "creationDateTime": "2026-08-25T18:42:18Z",
    "statusUpdateDateTime": "2026-08-25T18:42:18Z",
    "proxy": "76109277673",
    "status": "SCHD",
    "localInstrument": "DICT",
    "cnpjInitiator": "13884775000119",
    "payment": {
      "amount": "1400.00",
      "currency": "BRL"
    },
    "creditorAccount": {
      "ispb": "12345678",
      "issuer": "1774",
      "number": "1234567890",
      "accountType": "CACC"
    },
    "debtorAccount": {
      "ispb": "12345678",
      "issuer": "6272",
      "number": "94088392",
      "accountType": "CACC"
    },
    "authorisationFlow": "HYBRID_FLOW"
  },
  "meta": {
    "requestDateTime": "2026-08-25T15:42:19Z"
  },
  "iss": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "links": {
    "self": "https://api.local/open-banking/payments/v5/pix/payments/095b3706-7446-4f70-8522-601d62d608a9"
  },
  "iat": 1787683339,
  "jti": "93359dce-2005-4904-b736-de87342b474a"
}
```

</details>

<details>
<summary><code>12345.00</code></summary>

**Request** `POST /open-banking/payments/v5/pix/payments`

```json
[
  {
    "consentId": "urn:raidiambank:payment-consent:59287dbe-57d2-4705-a981-191b988b7970",
    "endToEndId": "E138847752026082518424caed4cc611",
    "creditorAccount": {
      "number": "1234567890",
      "ispb": "12345678",
      "issuer": "1774",
      "accountType": "CACC"
    },
    "localInstrument": "DICT",
    "proxy": "76109277673",
    "payment": {
      "amount": "12345.00",
      "currency": "BRL"
    },
    "cnpjInitiator": "13884775000119",
    "authorisationFlow": "HYBRID_FLOW"
  }
]
```

**Response** `HTTP 200 (retornado no GET do pagamento)`

```json
{
  "aud": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "data": {
    "paymentId": "42805ff5-87c1-4125-a923-32bd150df475",
    "endToEndId": "E138847752026082518424caed4cc611",
    "consentId": "urn:raidiambank:payment-consent:59287dbe-57d2-4705-a981-191b988b7970",
    "creationDateTime": "2026-08-25T18:42:19Z",
    "statusUpdateDateTime": "2026-08-25T18:42:20Z",
    "proxy": "76109277673",
    "status": "PDNG",
    "localInstrument": "DICT",
    "cnpjInitiator": "13884775000119",
    "payment": {
      "amount": "12345.00",
      "currency": "BRL"
    },
    "creditorAccount": {
      "ispb": "12345678",
      "issuer": "1774",
      "number": "1234567890",
      "accountType": "CACC"
    },
    "debtorAccount": {
      "ispb": "12345678",
      "issuer": "6272",
      "number": "94088392",
      "accountType": "CACC"
    },
    "authorisationFlow": "HYBRID_FLOW"
  },
  "meta": {
    "requestDateTime": "2026-08-25T15:42:20Z"
  },
  "iss": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "links": {
    "self": "https://api.local/open-banking/payments/v5/pix/payments/42805ff5-87c1-4125-a923-32bd150df475"
  },
  "iat": 1787683340,
  "jti": "b363584f-b6ac-4aa7-90f0-a62be4353d23"
}
```

</details>

<details>
<summary><code>12345.67</code></summary>

**Request** `POST /open-banking/payments/v5/pix/payments`

```json
[
  {
    "consentId": "urn:raidiambank:payment-consent:27b27788-cd1f-46c5-b3ea-d79f035853cd",
    "endToEndId": "E13884775202608251842987ec22a889",
    "creditorAccount": {
      "number": "1234567890",
      "ispb": "12345678",
      "issuer": "1774",
      "accountType": "CACC"
    },
    "localInstrument": "DICT",
    "proxy": "76109277673",
    "payment": {
      "amount": "12345.67",
      "currency": "BRL"
    },
    "cnpjInitiator": "13884775000119",
    "authorisationFlow": "HYBRID_FLOW"
  }
]
```

**Response** `HTTP 200 (retornado no GET do pagamento)`

```json
{
  "aud": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "data": {
    "paymentId": "d887c157-fee3-416e-9070-fc253436612e",
    "endToEndId": "E13884775202608251842987ec22a889",
    "consentId": "urn:raidiambank:payment-consent:27b27788-cd1f-46c5-b3ea-d79f035853cd",
    "creationDateTime": "2026-08-25T18:42:20Z",
    "statusUpdateDateTime": "2026-08-25T18:42:20Z",
    "proxy": "76109277673",
    "status": "PDNG",
    "localInstrument": "DICT",
    "cnpjInitiator": "13884775000119",
    "payment": {
      "amount": "12345.67",
      "currency": "BRL"
    },
    "creditorAccount": {
      "ispb": "12345678",
      "issuer": "1774",
      "number": "1234567890",
      "accountType": "CACC"
    },
    "debtorAccount": {
      "ispb": "12345678",
      "issuer": "6272",
      "number": "94088392",
      "accountType": "CACC"
    },
    "authorisationFlow": "HYBRID_FLOW"
  },
  "meta": {
    "requestDateTime": "2026-08-25T15:42:21Z"
  },
  "iss": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "links": {
    "self": "https://api.local/open-banking/payments/v5/pix/payments/d887c157-fee3-416e-9070-fc253436612e"
  },
  "iat": 1787683341,
  "jti": "ee2198ba-a0a0-48da-9c21-f95db25a3354"
}
```

</details>

### A5. Block the client (any payments request)

For the next 10 minutes the mock returns the HTTP status below on every payments request from the same `client_id`.

- **API:** Payment Initiation V5
- **Endpoint:** any payments request (triggered at pix payment initiation)
- **Field:** `data[0].payment.amount`

| Value | HTTP | Outcome |
|-------|------|---------|
| `10429.00` | 429 | client blocked for 10 minutes |
| `10504.00` | 504 | client blocked for 10 minutes |



**Exemplos de request/response:**

<details>
<summary><code>10429.00</code></summary>

**Request** `POST /open-banking/payments/v5/pix/payments`

```json
[
  {
    "consentId": "urn:raidiambank:payment-consent:ab1f62e2-fefe-4910-bec7-b57806517cf1",
    "endToEndId": "E1388477520260825184249817b7506e",
    "creditorAccount": {
      "number": "1234567890",
      "ispb": "12345678",
      "issuer": "1774",
      "accountType": "CACC"
    },
    "localInstrument": "DICT",
    "proxy": "76109277673",
    "payment": {
      "amount": "10429.00",
      "currency": "BRL"
    },
    "cnpjInitiator": "13884775000119",
    "authorisationFlow": "HYBRID_FLOW"
  }
]
```

**Response** `HTTP 429`

```json
{
  "errors": [
    {
      "code": "Too many requests",
      "title": "Too many requests",
      "detail": "Too many requests"
    }
  ],
  "meta": {
    "requestDateTime": "2026-08-25T18:42:25Z"
  }
}
```

</details>

<details>
<summary><code>10504.00</code></summary>

**Request** `POST /open-banking/payments/v5/pix/payments`

```json
[
  {
    "consentId": "urn:raidiambank:payment-consent:fffc3bab-5690-4e4f-b966-d58bfefa7687",
    "endToEndId": "E138847752026082518420879c527b78",
    "creditorAccount": {
      "number": "1234567890",
      "ispb": "12345678",
      "issuer": "1774",
      "accountType": "CACC"
    },
    "localInstrument": "DICT",
    "proxy": "76109277673",
    "payment": {
      "amount": "10504.00",
      "currency": "BRL"
    },
    "cnpjInitiator": "13884775000119",
    "authorisationFlow": "HYBRID_FLOW"
  }
]
```

**Response** `HTTP 504`

```json
{
  "iss": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "aud": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "iat": 1787683345,
  "meta": {
    "requestDateTime": "2026-08-25T18:42:25Z"
  },
  "errors": [
    {
      "code": "Gateway Timeout",
      "title": "Gateway Timeout",
      "detail": "Gateway Timeout"
    }
  ],
  "jti": "a0a29fb0-a32c-41f4-ae98-0bfd89f73272"
}
```

</details>

## B. Automatic Payments (recurring / sweeping, V2)

### B1. Reject the consent at creation (immediate)

- **API:** Automatic Payments V2
- **Endpoint:** `POST /open-banking/automatic-payments/v2/recurring-consents`
- **Field:** `data.recurringConfiguration.sweeping.totalAllowedAmount` (sweeping) or `data.recurringConfiguration.automatic.fixedAmount` (automatic)

| Value | HTTP | Outcome |
|-------|------|---------|
| `10422.00` | 422 | rejected, no error code |
| `10422.01` | 422 | rejected, `DETALHE_PAGAMENTO_INVALIDO` |
| `10422.02` | 422 | rejected, `FORMA_PAGAMENTO_INVALIDA` |



**Exemplos de request/response:**

<details>
<summary><code>10422.00</code></summary>

**Request** `POST /open-banking/automatic-payments/v2/recurring-consents`

```json
{
  "loggedUser": {
    "document": {
      "identification": "76109277673",
      "rel": "CPF"
    }
  },
  "creditors": [
    {
      "personType": "PESSOA_NATURAL",
      "cpfCnpj": "76109277673",
      "name": "Recebedor Exemplo"
    }
  ],
  "recurringConfiguration": {
    "sweeping": {
      "totalAllowedAmount": "10422.00",
      "transactionLimit": "999999.00",
      "startDateTime": "2026-08-25T18:42:21Z",
      "periodicLimits": {
        "day": {
          "quantityLimit": 100,
          "transactionLimit": "999999.00"
        },
        "week": {
          "quantityLimit": 100,
          "transactionLimit": "999999.00"
        },
        "month": {
          "quantityLimit": 100,
          "transactionLimit": "999999.00"
        },
        "year": {
          "quantityLimit": 100,
          "transactionLimit": "999999.00"
        }
      }
    }
  },
  "expirationDateTime": "2026-12-23T18:42:21Z"
}
```

**Response** `HTTP 422`

```json
{
  "iss": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "aud": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "iat": 1787683341,
  "meta": {
    "requestDateTime": "2026-08-25T18:42:21Z"
  },
  "errors": [
    {
      "code": "Forced a 422 for payment consent request",
      "title": "Forced a 422 for payment consent request",
      "detail": "Forced a 422 for payment consent request"
    }
  ],
  "jti": "96e90edc-7b12-4b28-b858-166dde10e26f"
}
```

</details>

<details>
<summary><code>10422.01</code></summary>

**Request** `POST /open-banking/automatic-payments/v2/recurring-consents`

```json
{
  "loggedUser": {
    "document": {
      "identification": "76109277673",
      "rel": "CPF"
    }
  },
  "creditors": [
    {
      "personType": "PESSOA_NATURAL",
      "cpfCnpj": "76109277673",
      "name": "Recebedor Exemplo"
    }
  ],
  "recurringConfiguration": {
    "sweeping": {
      "totalAllowedAmount": "10422.01",
      "transactionLimit": "999999.00",
      "startDateTime": "2026-08-25T18:42:21Z",
      "periodicLimits": {
        "day": {
          "quantityLimit": 100,
          "transactionLimit": "999999.00"
        },
        "week": {
          "quantityLimit": 100,
          "transactionLimit": "999999.00"
        },
        "month": {
          "quantityLimit": 100,
          "transactionLimit": "999999.00"
        },
        "year": {
          "quantityLimit": 100,
          "transactionLimit": "999999.00"
        }
      }
    }
  },
  "expirationDateTime": "2026-12-23T18:42:21Z"
}
```

**Response** `HTTP 422`

```json
{
  "iss": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "aud": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "iat": 1787683341,
  "meta": {
    "requestDateTime": "2026-08-25T18:42:21Z"
  },
  "errors": [
    {
      "code": "DETALHE_PAGAMENTO_INVALIDO",
      "title": "Detalhe do pagamento inválido.",
      "detail": "DETALHE_PAGAMENTO_INVALIDO"
    }
  ],
  "jti": "30083654-dd78-43b9-b538-1adc1435600b"
}
```

</details>

<details>
<summary><code>10422.02</code></summary>

**Request** `POST /open-banking/automatic-payments/v2/recurring-consents`

```json
{
  "loggedUser": {
    "document": {
      "identification": "76109277673",
      "rel": "CPF"
    }
  },
  "creditors": [
    {
      "personType": "PESSOA_NATURAL",
      "cpfCnpj": "76109277673",
      "name": "Recebedor Exemplo"
    }
  ],
  "recurringConfiguration": {
    "sweeping": {
      "totalAllowedAmount": "10422.02",
      "transactionLimit": "999999.00",
      "startDateTime": "2026-08-25T18:42:21Z",
      "periodicLimits": {
        "day": {
          "quantityLimit": 100,
          "transactionLimit": "999999.00"
        },
        "week": {
          "quantityLimit": 100,
          "transactionLimit": "999999.00"
        },
        "month": {
          "quantityLimit": 100,
          "transactionLimit": "999999.00"
        },
        "year": {
          "quantityLimit": 100,
          "transactionLimit": "999999.00"
        }
      }
    }
  },
  "expirationDateTime": "2026-12-23T18:42:21Z"
}
```

**Response** `HTTP 422`

```json
{
  "iss": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "aud": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "iat": 1787683341,
  "meta": {
    "requestDateTime": "2026-08-25T18:42:21Z"
  },
  "errors": [
    {
      "code": "FORMA_PAGAMENTO_INVALIDA",
      "title": "Forma do pagamento inválido.",
      "detail": "FORMA_PAGAMENTO_INVALIDA"
    }
  ],
  "jti": "c0c04376-35f7-4874-8b8b-7b1e797e6b1f"
}
```

</details>

### B2. Reject the recurring payment at initiation, or block the client (immediate)

- **API:** Automatic Payments V2
- **Endpoint:** `POST /open-banking/automatic-payments/v2/pix/recurring-payments`
- **Field:** `data.payment.amount`

| Value | HTTP | Outcome |
|-------|------|---------|
| `10422.00` | 422 | rejected, no error code |
| `10422.01` | 422 | rejected, `DETALHE_PAGAMENTO_INVALIDO` |
| `10429.00` | 429 | client blocked for 10 minutes |
| `10504.00` | 504 | client blocked for 10 minutes |
| `1200.01` | 422 | rejected, `PAGAMENTO_DIVERGENTE_CONSENTIMENTO` (only if the consent has a `businessEntity`) |



**Exemplos de request/response:**

<details>
<summary><code>10422.00</code></summary>

**Request** `POST /open-banking/automatic-payments/v2/pix/recurring-payments`

```json
{
  "recurringConsentId": "urn:raidiambank:payment-consent:a3b11c96-9477-4b92-bb0f-6ebbbdb555a7",
  "date": "2026-08-25",
  "authorisationFlow": "HYBRID_FLOW",
  "cnpjInitiator": "13884775000119",
  "localInstrument": "DICT",
  "proxy": "76109277673",
  "endToEndId": "E138847752026082518426a21aedfaea",
  "ibgeTownCode": "5300108",
  "remittanceInformation": "Exemplo trigger Automatic Payments",
  "transactionIdentification": "transactionIdentification",
  "creditorAccount": {
    "number": "1234567890",
    "ispb": "12345678",
    "issuer": "1774",
    "accountType": "CACC"
  },
  "payment": {
    "amount": "10422.00",
    "currency": "BRL"
  },
  "document": {
    "rel": "CPF",
    "identification": "76109277673"
  }
}
```

**Response** `HTTP 422`

```json
{
  "iss": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "aud": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "iat": 1787683341,
  "meta": {
    "requestDateTime": "2026-08-25T18:42:21Z"
  },
  "errors": [
    {
      "code": "Forced a 422 for payment consent request",
      "title": "Forced a 422 for payment consent request",
      "detail": "Forced a 422 for payment consent request"
    }
  ],
  "jti": "e359d4cc-98c2-4714-9e74-b972ee65d4ec"
}
```

</details>

<details>
<summary><code>10422.01</code></summary>

**Request** `POST /open-banking/automatic-payments/v2/pix/recurring-payments`

```json
{
  "recurringConsentId": "urn:raidiambank:payment-consent:a3b11c96-9477-4b92-bb0f-6ebbbdb555a7",
  "date": "2026-08-25",
  "authorisationFlow": "HYBRID_FLOW",
  "cnpjInitiator": "13884775000119",
  "localInstrument": "DICT",
  "proxy": "76109277673",
  "endToEndId": "E13884775202608251842ac2e2e08ba9",
  "ibgeTownCode": "5300108",
  "remittanceInformation": "Exemplo trigger Automatic Payments",
  "transactionIdentification": "transactionIdentification",
  "creditorAccount": {
    "number": "1234567890",
    "ispb": "12345678",
    "issuer": "1774",
    "accountType": "CACC"
  },
  "payment": {
    "amount": "10422.01",
    "currency": "BRL"
  },
  "document": {
    "rel": "CPF",
    "identification": "76109277673"
  }
}
```

**Response** `HTTP 422`

```json
{
  "iss": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "aud": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "iat": 1787683341,
  "meta": {
    "requestDateTime": "2026-08-25T18:42:21Z"
  },
  "errors": [
    {
      "code": "DETALHE_PAGAMENTO_INVALIDO",
      "title": "Detalhe do pagamento inválido.",
      "detail": "DETALHE_PAGAMENTO_INVALIDO"
    }
  ],
  "jti": "b74e3c46-489b-4cc6-8b50-4cf88dd10692"
}
```

</details>

<details>
<summary><code>10429.00</code></summary>

**Request** `POST /open-banking/automatic-payments/v2/pix/recurring-payments`

```json
{
  "recurringConsentId": "urn:raidiambank:payment-consent:59057cb2-9f02-40ac-ad2d-6fb404d51306",
  "date": "2026-08-25",
  "authorisationFlow": "HYBRID_FLOW",
  "cnpjInitiator": "13884775000119",
  "localInstrument": "DICT",
  "proxy": "76109277673",
  "endToEndId": "E13884775202608251842e6e418b08d8",
  "ibgeTownCode": "5300108",
  "remittanceInformation": "Exemplo trigger Automatic Payments",
  "transactionIdentification": "transactionIdentification",
  "creditorAccount": {
    "number": "1234567890",
    "ispb": "12345678",
    "issuer": "1774",
    "accountType": "CACC"
  },
  "payment": {
    "amount": "10429.00",
    "currency": "BRL"
  },
  "document": {
    "rel": "CPF",
    "identification": "76109277673"
  }
}
```

**Response** `HTTP 429`

```json
{
  "errors": [
    {
      "code": "Too many requests",
      "title": "Too many requests",
      "detail": "Too many requests"
    }
  ],
  "meta": {
    "requestDateTime": "2026-08-25T18:42:25Z"
  }
}
```

</details>

<details>
<summary><code>10504.00</code></summary>

**Request** `POST /open-banking/automatic-payments/v2/pix/recurring-payments`

```json
{
  "recurringConsentId": "urn:raidiambank:payment-consent:59057cb2-9f02-40ac-ad2d-6fb404d51306",
  "date": "2026-08-25",
  "authorisationFlow": "HYBRID_FLOW",
  "cnpjInitiator": "13884775000119",
  "localInstrument": "DICT",
  "proxy": "76109277673",
  "endToEndId": "E13884775202608251842569ed083704",
  "ibgeTownCode": "5300108",
  "remittanceInformation": "Exemplo trigger Automatic Payments",
  "transactionIdentification": "transactionIdentification",
  "creditorAccount": {
    "number": "1234567890",
    "ispb": "12345678",
    "issuer": "1774",
    "accountType": "CACC"
  },
  "payment": {
    "amount": "10504.00",
    "currency": "BRL"
  },
  "document": {
    "rel": "CPF",
    "identification": "76109277673"
  }
}
```

**Response** `HTTP 504`

```json
{
  "iss": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "aud": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "iat": 1787683345,
  "meta": {
    "requestDateTime": "2026-08-25T18:42:25Z"
  },
  "errors": [
    {
      "code": "Gateway Timeout",
      "title": "Gateway Timeout",
      "detail": "Gateway Timeout"
    }
  ],
  "jti": "b79d5f20-7939-4462-bbf6-0a52c8854eae"
}
```

</details>

<details>
<summary><code>1200.01</code></summary>

**Request** `POST /open-banking/automatic-payments/v2/pix/recurring-payments`

```json
{
  "recurringConsentId": "urn:raidiambank:payment-consent:c7fd68fa-5eac-4103-b555-f10e6ac24691",
  "date": "2026-08-25",
  "authorisationFlow": "HYBRID_FLOW",
  "cnpjInitiator": "13884775000119",
  "localInstrument": "DICT",
  "proxy": "12345678000199",
  "endToEndId": "E1388477520260825184234623d20fe8",
  "ibgeTownCode": "5300108",
  "remittanceInformation": "Exemplo trigger Automatic Payments",
  "transactionIdentification": "transactionIdentification",
  "creditorAccount": {
    "number": "1234567890",
    "ispb": "12345678",
    "issuer": "1774",
    "accountType": "CACC"
  },
  "payment": {
    "amount": "1200.01",
    "currency": "BRL"
  },
  "document": {
    "rel": "CPF",
    "identification": "12345678000199"
  }
}
```

**Response** `HTTP 422`

```json
{
  "iss": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "aud": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "iat": 1787683345,
  "meta": {
    "requestDateTime": "2026-08-25T18:42:25Z"
  },
  "errors": [
    {
      "code": "PAGAMENTO_DIVERGENTE_CONSENTIMENTO",
      "title": "Divergência entre pagamento e consentimento",
      "detail": "O CNPJ do loggedUser (Bussiness Entity) não corresponde ao creditor do consentimento"
    }
  ],
  "jti": "ea44b281-73de-4bdb-afcc-c3ebcca762eb"
}
```

</details>

### B3. Move the recurring payment to RJCT after it was accepted

- **API:** Automatic Payments V2
- **Endpoint (to read):** `GET /open-banking/automatic-payments/v2/pix/recurring-payments/{recurringPaymentId}`
- **Field:** `data.payment.amount`

| Value | HTTP | Payment state returned |
|-------|------|------------------------|
| `20201.40` | 200 | `RJCT`, reason `NAO_INFORMADO` |
| `20201.60` | 200 | `RJCT`, reason `NAO_INFORMADO`, payment date set to yesterday |
| `20201.70` | 200 | `RJCT`, reason `NAO_INFORMADO`, payment date set to today |

> All three are skipped when the payment is a retry. Not available for the recurring flow: the `300.xx` table, `1501.00`, and the richer post-initiation RJCT reasons (`20201.00/.10/.20/.30/.50`, `999999999.99`). Otherwise recurring status is driven by the real business rules (periodic and total limits, dates, expiration).



**Exemplos de request/response:**

<details>
<summary><code>20201.40</code></summary>

**Request** `POST /open-banking/automatic-payments/v2/pix/recurring-payments`

```json
{
  "recurringConsentId": "urn:raidiambank:payment-consent:a3b11c96-9477-4b92-bb0f-6ebbbdb555a7",
  "date": "2026-08-25",
  "authorisationFlow": "HYBRID_FLOW",
  "cnpjInitiator": "13884775000119",
  "localInstrument": "DICT",
  "proxy": "76109277673",
  "endToEndId": "E13884775202608251842092f56e6290",
  "ibgeTownCode": "5300108",
  "remittanceInformation": "Exemplo trigger Automatic Payments",
  "transactionIdentification": "transactionIdentification",
  "creditorAccount": {
    "number": "1234567890",
    "ispb": "12345678",
    "issuer": "1774",
    "accountType": "CACC"
  },
  "payment": {
    "amount": "20201.40",
    "currency": "BRL"
  },
  "document": {
    "rel": "CPF",
    "identification": "76109277673"
  }
}
```

**Response** `HTTP 200 (retornado no GET do pagamento)`

```json
{
  "aud": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "data": {
    "recurringPaymentId": "89c89ebe-8fb5-41e6-8b24-d0683f2fd664",
    "recurringConsentId": "urn:raidiambank:payment-consent:a3b11c96-9477-4b92-bb0f-6ebbbdb555a7",
    "endToEndId": "E13884775202608251842092f56e6290",
    "date": "2026-08-25",
    "creationDateTime": "2026-08-25T18:42:21Z",
    "statusUpdateDateTime": "2026-08-25T18:42:21Z",
    "status": "RJCT",
    "rejectionReason": {
      "code": "NAO_INFORMADO",
      "detail": "NAO_INFORMADO"
    },
    "cnpjInitiator": "13884775000119",
    "payment": {
      "amount": "20201.40",
      "currency": "BRL"
    },
    "remittanceInformation": "Exemplo trigger Automatic Payments",
    "creditorAccount": {
      "ispb": "12345678",
      "issuer": "1774",
      "number": "1234567890",
      "accountType": "CACC"
    },
    "authorisationFlow": "HYBRID_FLOW",
    "localInstrument": "DICT",
    "transactionIdentification": "transactionIdentification",
    "document": {
      "identification": "76109277673",
      "rel": "CPF"
    }
  },
  "meta": {
    "requestDateTime": "2026-08-25T18:42:22Z"
  },
  "iss": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "links": {
    "self": "https://api.local/open-banking/automatic-payments/v2/pix/recurring-payments/89c89ebe-8fb5-41e6-8b24-d0683f2fd664"
  },
  "iat": 1787683342,
  "jti": "f7ea4611-e57a-4525-ab76-64a07197e67b"
}
```

</details>

<details>
<summary><code>20201.60</code></summary>

**Request** `POST /open-banking/automatic-payments/v2/pix/recurring-payments`

```json
{
  "recurringConsentId": "urn:raidiambank:payment-consent:a3b11c96-9477-4b92-bb0f-6ebbbdb555a7",
  "date": "2026-08-25",
  "authorisationFlow": "HYBRID_FLOW",
  "cnpjInitiator": "13884775000119",
  "localInstrument": "DICT",
  "proxy": "76109277673",
  "endToEndId": "E138847752026082518422f6900c63c4",
  "ibgeTownCode": "5300108",
  "remittanceInformation": "Exemplo trigger Automatic Payments",
  "transactionIdentification": "transactionIdentification",
  "creditorAccount": {
    "number": "1234567890",
    "ispb": "12345678",
    "issuer": "1774",
    "accountType": "CACC"
  },
  "payment": {
    "amount": "20201.60",
    "currency": "BRL"
  },
  "document": {
    "rel": "CPF",
    "identification": "76109277673"
  }
}
```

**Response** `HTTP 200 (retornado no GET do pagamento)`

```json
{
  "aud": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "data": {
    "recurringPaymentId": "84514a86-00f6-485f-a2ce-ac1663709742",
    "recurringConsentId": "urn:raidiambank:payment-consent:a3b11c96-9477-4b92-bb0f-6ebbbdb555a7",
    "endToEndId": "E138847752026082518422f6900c63c4",
    "date": "2026-08-24",
    "creationDateTime": "2026-08-25T18:42:22Z",
    "statusUpdateDateTime": "2026-08-25T18:42:22Z",
    "status": "RJCT",
    "rejectionReason": {
      "code": "NAO_INFORMADO",
      "detail": "NAO_INFORMADO"
    },
    "cnpjInitiator": "13884775000119",
    "payment": {
      "amount": "20201.60",
      "currency": "BRL"
    },
    "remittanceInformation": "Exemplo trigger Automatic Payments",
    "creditorAccount": {
      "ispb": "12345678",
      "issuer": "1774",
      "number": "1234567890",
      "accountType": "CACC"
    },
    "authorisationFlow": "HYBRID_FLOW",
    "localInstrument": "DICT",
    "transactionIdentification": "transactionIdentification",
    "document": {
      "identification": "76109277673",
      "rel": "CPF"
    }
  },
  "meta": {
    "requestDateTime": "2026-08-25T18:42:23Z"
  },
  "iss": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "links": {
    "self": "https://api.local/open-banking/automatic-payments/v2/pix/recurring-payments/84514a86-00f6-485f-a2ce-ac1663709742"
  },
  "iat": 1787683343,
  "jti": "655f8310-a815-43cf-99d2-ac4819adc2eb"
}
```

</details>

<details>
<summary><code>20201.70</code></summary>

**Request** `POST /open-banking/automatic-payments/v2/pix/recurring-payments`

```json
{
  "recurringConsentId": "urn:raidiambank:payment-consent:a3b11c96-9477-4b92-bb0f-6ebbbdb555a7",
  "date": "2026-08-25",
  "authorisationFlow": "HYBRID_FLOW",
  "cnpjInitiator": "13884775000119",
  "localInstrument": "DICT",
  "proxy": "76109277673",
  "endToEndId": "E138847752026082518421795c4faabf",
  "ibgeTownCode": "5300108",
  "remittanceInformation": "Exemplo trigger Automatic Payments",
  "transactionIdentification": "transactionIdentification",
  "creditorAccount": {
    "number": "1234567890",
    "ispb": "12345678",
    "issuer": "1774",
    "accountType": "CACC"
  },
  "payment": {
    "amount": "20201.70",
    "currency": "BRL"
  },
  "document": {
    "rel": "CPF",
    "identification": "76109277673"
  }
}
```

**Response** `HTTP 200 (retornado no GET do pagamento)`

```json
{
  "aud": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "data": {
    "recurringPaymentId": "f0a33f96-adb3-4940-85b2-0ca17a7210f7",
    "recurringConsentId": "urn:raidiambank:payment-consent:a3b11c96-9477-4b92-bb0f-6ebbbdb555a7",
    "endToEndId": "E138847752026082518421795c4faabf",
    "date": "2026-08-25",
    "creationDateTime": "2026-08-25T18:42:23Z",
    "statusUpdateDateTime": "2026-08-25T18:42:23Z",
    "status": "RJCT",
    "rejectionReason": {
      "code": "NAO_INFORMADO",
      "detail": "NAO_INFORMADO"
    },
    "cnpjInitiator": "13884775000119",
    "payment": {
      "amount": "20201.70",
      "currency": "BRL"
    },
    "remittanceInformation": "Exemplo trigger Automatic Payments",
    "creditorAccount": {
      "ispb": "12345678",
      "issuer": "1774",
      "number": "1234567890",
      "accountType": "CACC"
    },
    "authorisationFlow": "HYBRID_FLOW",
    "localInstrument": "DICT",
    "transactionIdentification": "transactionIdentification",
    "document": {
      "identification": "76109277673",
      "rel": "CPF"
    }
  },
  "meta": {
    "requestDateTime": "2026-08-25T18:42:24Z"
  },
  "iss": "74e929d9-33b6-4d85-8ba7-c146c867a817",
  "links": {
    "self": "https://api.local/open-banking/automatic-payments/v2/pix/recurring-payments/f0a33f96-adb3-4940-85b2-0ca17a7210f7"
  },
  "iat": 1787683344,
  "jti": "bfbd00bd-258b-470f-8acd-e2890f6139e5"
}
```

</details>

## C. Enrollments (V2)

An enrollment payment reuses the endpoints above, depending on the consent type:

- Over a single-payment consent: `POST /open-banking/payments/v5/pix/payments`, field `data[0].payment.amount` (section A triggers apply).
- Over a recurring (Pix Automatico) consent: `POST /open-banking/automatic-payments/v2/pix/recurring-payments`, field `data.payment.amount` (section B triggers apply).

## Webhook processing in the Mock Bank

The Mock Bank does not settle payments or send webhooks asynchronously. For a one-time Pix payment, the status webhook is sent when GET /payments/{paymentId} is called (that GET advances the simulated payment and triggers the notification); it is also sent on a PATCH cancellation. Consent and recurring-payment webhooks are sent on the relevant POST, PATCH and GET transitions. Enrollment webhooks are sent on PATCH (state change) and, in the multiple-consents limits case, on GET. In all cases a webhook is sent only if a webhook_uri is registered for the software.

## Alphanumeric CNPJ Payments Test Plan

The `payments_alphanumeric-cnpj_test-plan` validates that CNPJ fields (`businessEntity.document.identification`, `creditor.cpfCnpj`, `cnpjInitiator`) accept alphanumeric values (letters and numbers). The client is embedded from the CNPJ Test profile and is not exposed to the participant.

Against the Mock Bank, use the **Alice Silva** persona, which is the account holder seeded with alphanumeric CNPJs:

| Config field | Value |
|--------------|-------|
| Logged User CPF (`loggedUserIdentification`) | `08116143018` |
| Business Entity CNPJ (`businessEntityIdentification`) | `5W685362006773` (alphanumeric) |
| Debtor Account ISPB | `12345678` |
| Debtor Account Issuer | `1774` |
| Debtor Account Number | `38294750` |
| Debtor Account Type | `CACC` |
| Payment Amount | per the trigger tables above (e.g. `1336.00` to force ACSC) |
| Business or Personal Products | `business` |

> **Note:** The Debtor Account ISPB (`12345678`) and Issuer (`1774`) are **fixed Mock Bank defaults used by every persona**, not specific to Alice. Account type is also a shared default (`CACC`). The only per-persona value is the **Debtor Account Number**, which identifies the account.

Alice's available balance is high, so no amount triggers a balance rejection. The Mock Bank does not validate the `businessEntity` CNPJ against seeded data, so any valid alphanumeric CNPJ is accepted.

For the multiple-consents (joint account) scenario, use the **Gabriel Nunes** persona (CPF `87517400444`, account number `94088393`), which supports multiple authorisations. Leave the multiple-consents fields blank to skip that module.

# Example of Valid Test Configurations

The following JSON objects should be placed in the JSON Configuration field for each respective phase in the Conformance Suite configuration page:

<details>
<summary>JSON Configuration for Payments v5 (Auto Redirect)</summary>

```
{
    "alias": "obbsb",
    "description": "Phase 3 - Payments v5",
    "server": {
        "discoveryUrl": "https://auth.mockbank.openbankingbrasil.org.br/.well-known/openid-configuration"
    },
    "directory": {
        "keystore": "https://keystore.sandbox.directory.openbankingbrasil.org.br/",
"discoveryUrl": "https://auth.directory.openbankingbrasil.org.br/.well-known/openid-configuration",
        "apibase": "https://matls-api.directory.openbankingbrasil.org.br/",
        "client_id": "984e85a9-9001-40eb-97b3-194f5afbd956"
    },
    "client": {
        "jwks": {
            "keys": [
                {
                    "alg": "PS256",
                    "d": "Q9gSOfnkGJnAsV3a94j9ae9ihjqgMwXgVm73VTyEs1u9Jq73pCWX0e9JdeNMKdgKpiJYjyxa3ttxCY58eiGKEi7c50zYRx8YLTL2rIVWqS6JVGpXuzIQutkQDM4AfD72bG3-xT-caSCansGbdEIFJjX32Ujbs1UUoQlE96m3hNOjB5vNyHBWrBUgUGG9_uJiWFG6Lbj8ZGtiihA_PQkzuArLzDvO2OMVHCzIyQ4CwFE1tI9xHFHpioJQXBnymURQvkm3MmEwHRG_KUdABQ55gG32jothy7jOOYAMkvOCejteTZv1nT4dsEj-CBxDBtTI6SerXb11VX8b0suzSBxx0Q",
                    "dp": "S15AOPpOtYgYjfOi2rNojY3NpU-Qobnfnnt_MZEJ2_DS0bGwXSgGJjHOOOAowy1HK0n7-AhXbwhr026sBuicR_Kpj6RkzGVrJug8y9R02FXZwlQpgjSBZdO6C2B1OOvtyKmnKg5q1KdQ7Kx6vYPV7UutOJn6NlH0RbFgG4NGelk",
                    "dq": "oBgBMB54mtrriQCg4YyDY_zf7LW4f6oqiUl3l7odf_ArjVamjHM-boZnhGoVzZ5uXNs03wEdBIc2HLmsoGLVuodcYHjyptmvyPebiH2mavFlUlI8ILG6lkyIhMp3Ri8iXGX2MYlPjP2EawNDMHB6BO0bZ5NugyzxuF_OKhfEFLc",
                    "e": "AQAB",
                    "kid": "-duNE0ZX5NmDkUlgNoqDY5Ve7UdFTA7S25WJSAv8tNQ",
                    "kty": "RSA",
                    "n": "-6Ep5kV0qcQnrxQzbEgMGKQRHnhXlp3ZpAVqQbbzkVG_a1tHLi0V7YAmjf3isXMvdvWjApeShL32gqxgcKDvC5Mnd5ufR1ujzb5lsnYXy-tKMQWnAlCqy7mSuxi8JIBXyZb7CMGU29L32Tvd5MjDh_hSgwnHcTggE-ehqzK5eyvK7DjvlbfCKXgDx94kMcwyI2K0EurahHj9_I3lEQzAt73OocF_z84FQxO87A8Q1cM3nEGyykZPaFyulQ4bf4U2tT_Jfd0ppYX1j194ouPeqMZBsGnxKf4L4QvuberbRpdeOO92HhWHHiwiTuhYxF876-LKgPzqxK-Y1a2_4gsVAw",
                    "p": "_oebNFofSe_8fdotMxUEk7n3pq5eT96rO_VPdHyTZERDrkU0djQf9BLy7DejYoRReuI0AJWkBL9EGBhECaowmx8gTCs43ffQrBDULYB4elmS07ov1pq1STqzqRKbu_INaSGVgxFzhYC_EeFVpB0RPlAUvb1_aQkH79J8VMnp2_U",
                    "q": "_RVEyO9NB6XiJjMz9t6XrNxG01Vguo2VVBLaDJhoi1g7gydUDkNc9twhF1Ifps8Gf3m9aMjjOmYqE5kuWCPBHxkk8cZOm4C2AhVbQxMkZLOyPeJDfKfCi7yJRIfmwqQM5AKosALfN-jW_p746lRhCAps8eH9XF6bjugi_MH1yhc",
                    "qi": "yXG_vCx0xL9DlU7f0Ixub9NSD1QJtAJYxwKyHukw_8f4rHLiZ8eeCerfZfPd7zsPGSqOmY2605MNT1Z2ohYgoRyu05uwstEDKqtgl_uxupfO6AJKCja4paIB-ICvQQXpOY1n9BW6VcDwSylTnv1pKvVnTvxzy5z008wvrafQtFw",
                    "use": "sig"
                },
                {
                    "kty": "RSA",
                    "alg": "PS256",
                    "use": "enc",
                    "kid": "e96744c58188c084310920b152ffb02a392b119a009fb1fa1a656006715e1604",
                    "n": "4eIXvOR1XXo3MT9syMwRZj2ChbV2Qlp_623VCIhYvPtJ5k5rlCr1hP4n0PC49U47pa3UKNs6DYHefHKm9I4h4crgk7zsln2_JP3kK1equqIO1U12Rv4Xbm_2_eqR3hPKcE3il2ky2Neby8OThFnyDwBNKdxI4MvOKm910qQhYns2L4w_i9fjF2z1Wpi6sMPW8IERhkqaBWgoaH9g2obGbNuoYCzEjOWvRb_nVjYKRPqTI2A11kWZ4mVTRkTO4yM1gdI7z8Hsl4fqlEXeVdmMkVJhRvQa-vFfegecgO8nUY2XoOUx_UR51F8PO9bepy-jH16cRDwjLE-2ex7mE_wfMw",
                    "e": "AQAB",
                    "d": "BqovoVF4vww8nA9IuLhnHDlDZFbHov4qZeCecQgcEJNpIxdiqDZuR4EvECsSIgOWOFvwW-lzOI1oHaVNlMvezXU5eoWpnpuEnzHlYHwCzxftNrde5PBZWHC-sAMStvBzJpLw7riNZgWFx_wNmoTQfHqgGQfLyxcB9Pf6v387qiN1wHfSXQshtFiDg_6tBaH6dS1jRAg7_56dQp1wWJeRaqMCg9QeESmo3c-76hnRSMU6fgrONU6qGMSLopv-nirh3H1gZePcXzVgf9cerRMQgV1pWUZEd_iJqTaX8U7wB0txmVF6QzRxR71Ah6nZuV_Rv7X88zB8u0rXOvjeGtuZKQ",
                    "p": "8fN0GXyZnvxba4yoOgdL9ta9pkjjWVu5eTOIyvSgKf09hUSWKL6sKm1N0l68detwzBFpnxObOeUCMnU_BFhJM-s0w5GognaAX6GB5-TzdYHwmsgqAch3-_hi_kZU6A-SLZu7bQFGXTEotQ1zMxVuCMZ7AjTs0CGZrS-vItFYtik",
                    "q": "7v_Ldwh3L9On2CNAefLgs7dyDBAgWrkXOJ9Z1EnrKgMHbqgq5dOixv2ezKNdOUte9G4ve555XTf2sC-p0TF9PNYC0_4KthI8NLik8RtDsQmYJUYw7qfV_YitzGflM2DRr6KaV5SmO_aPWRfzuVWh_6kIQ_GmXf47ASasKVeD_fs",
                    "dp": "Jyi-_q0C9A9mAHcodxPdQJsq4LHlUf4de7dSiX6kOYeKIHqkTv3lQYylTsoUeIVdoTmkPaHfurQM8fu18k8Tsfp8dLarbkodptyt-Mk-eiNIvNRusBExEi_2Xa8maNS0VPtij1boe4bMTtlZbsgmIfd1yzqjpV_6zmPsVZdKY1k",
                    "dq": "qjW-YA3FZGhmtwWUG8Wfxh41uOWbRUFgilDils_2DTuPBX363yc0XGevuqn18KH_BDGc23tnj74VkDDBzlxihvsblILuefDOs_V0csoqEWF128X7f1xEiIXY0SSFFWw0qdMx_IG_SiE0wgzO5QVZlEx7uHfXNkWjHBTAs8jCFhU",
                    "qi": "8W2vDdiA8qDxL2fiJPP2m3NqbjGW7Tf5PsfGo0Gqfv6nWVweuVwsyUNT1AYduZUCvFRG5LRNHqiwZNpNB6XQln1W41GaIqGkHWJkveHhg9xIQmSK2hrX4OnSdyvMiGiB2yvce0FTgQ0OzXuNkIKJKJLP2nAJusNgNcVT7qgKCRA"
                }
            ]
        },
        "org_jwks": {
            "keys": [
                {
                    "d": "BpgLagicLjysglxtDX7bJnOv4-IP-5yyGdL4oOkDCl_-lO8twPDhWLfXNCf2QTs7l1T1GLNUyALKjYDNEvjbpu03_K1dtRwO2ZS4_VHTPhe99Etn1GXntdfcFvQiD9Lz6uzs2-0DOIG_5xWUiVhTUN5HPRfMMXF3ktG2ucTOQqsJU0O2SOohVIvqYH4EDJNIw8qUsu1C2JEDMj79H_8KaXEUVx8tFFLMxmt67a_a7sImXvEaIYhUCu-DMMDrzBc660s_eTcihJ_DkJgYPPWctnmpUClKa4zgABDqGXhPQFfLS4ywGAHnLZF1MyNeKFXpmeJShjNJ5MqjBKJTnFHDQKs",
                    "dp": "CFfrENWCU61YHATfdTy73lt2reMz0dBDicy92s4FqHpcup6O6f5MWGvhpBlLVC-tNA97qzyKExFwxl6c6rf45l8T6GLjy4C2DJEH0pGKeh7-PP7XW1KBvsclbJdSoSj-bOFRomFVGKYhIF3nRnr9-Dvj1k8aEcClPT1E9i9rGI7P",
                    "dq": "BzCeCJQ9pKQVCpyFi50PR8_E7d9uW9nYqJpf0GBT5XdnZ44qnliLAffZmVwcxXh6e_JzIjC0ByJrYKd_dekXLCrsOex1XxqvI7WH6EZ3Nvoe_1835ZgtQ2PsPSvGKifHHPXocKyqqRdT7KlGTXfnpKtezsXPxe63VS-3coE62-_F",
                    "e": "AQAB",
                    "kid": "EKSYJfNcI8Bm22_dP0ziWpTjw9UceAdVjykgwO5BkfE",
                    "kty": "RSA",
                    "n": "oBp-b0EhezRYfisJBL_WA2Yh0Y2zPYHsy8N4G9mddkop-kFJT12XSSBx8GXmyjDL14Wg5vRNA6R_TwXbJbnHnE59uMYiWNi_G7OL6jMsncmYdyBuwl-lDWExaXC5Qg9vYgGnt7d1SthQoiJkduPIiNpniq5p7px-jJYQO4SECUqpeLl9rU_Xvxn5zpFu4dw65wBi4oSDiJ0zujQtxofOmbJCKYTWrPmd8yPlPgwIttP2ZcprMs5Ya57-99NhAealcVptRTOQTEWEOflmurq58Byu7pT64ns-9Su8JPcHMMzxOOVM7KNPuZA7Xa5-1aBd1XrhxkBHIDzUqOpanSlr2uk",
                    "p": "DgL5bOQ5-JXM6Ed_3BRKW2a3EcHB_UjlWPlGGkc0RBeEwlNi6D3PQGZmgTxyGXWA4W3HMi2S2pXx8oxWd9rrw9Uc_BNrIdvkMcU9LnkCvxK-dcHalVrXhv0l1EbQx0mG9LjLsiqmJiJYnUYTuLjO8lJaebSTp-EH2fgTs81_SBKv",
                    "q": "C20t29WtF9yAXt2r5Yu7chtrJUMIsu_TUY2N6p75BWWBB76oNib4Dp5fVePnbTqdSP913dS1K1vHwEAqS_Z_C6vfmaYha6Hguipo5jotTTJoYDxV_xTp1dGWcr8MltBE9ikhLa8xvGVxXjSi4vkqc_TyXlBSHbbBSZtjB32rCLHn",
                    "qi": "BRx-2fqZYWrIzcayN1v10HfzcQaZue-NNZP7Eid81oBBxBrDQmiGdzQLi0BKctjLBr21_GWUgHgEYRym3He5biuDVM0WnyhXYeLLc_pv3bIG6FoPrP4XDZo4GTM4JdVj2im_OQWdXuokFzsZzeVV6H8p46TxpyNDix5oFjmyuB11",
                    "alg": "PS256",
                    "use": "sig"
                },
                {
                    "p": "2a8fRJ7ybF-qtF1zrYzSm7z3C4wNTUMbVYqe44tR9FbKsobqW2tS0iAZf-GJ_SZPcWxkE76gunW7YqMJecGUtXsJ8TTHwjcPQOMYzxnyJu8Q4JOj01YJVrxUY9D0ZzpWM9oTAj1-qoE0w7Dy-XNUc14-HeRlmOkg2tTfrXTVR8c",
                    "kty": "RSA",
                    "q": "0xlPJFRUcBU5j2SKSajVnd4H5p88RSsd4cArMby1ZRuSeHEsX76c6QKAPq7uTfKrTeZic34yzAEUyHloP1fZQYQ2UQn-f6PsTAWdT1Lp5oi2VZCT0yc9-1EGnLAiUCbM9SQQyf2GIVhCiAk_0VuY6le61Pw0U4GssvFJzIrx4as",
                    "d": "GxnizpWcqL1wajD8-Y-8H9-II4UZMKfkgbfwRiLK9uAd8-kEJdO9jdNeMxyytg2saDhxNTeRTkYz_VbBf3p9dGhuYx84d-ZagUbIiU3ho3FCsBRrzQQZw9OQrzPDUzp0-SBn1_GLCf9fo4ysxWHbn9euJVi2fpN_bHlBi1n8fKhdBHYE7X3XJnRYrUXItxZw5sJsqM_boONLxdLAvgmZx5CHft94JZsR6JPwlj9Ba_CuNWX_3OuUGyV0f5_1ICAEYijw9PA8KAW6t5UUYn39_KYL8nF5L1Bh6W1j8eN84I2lcKZNO6Pou064ag_wqGhk4uXuQO1IV8jRFn3-pqhSEQ",
                    "e": "AQAB",
                    "use": "enc",
                    "kid": "c1d7b80ce4b88c4f2cfb68e7a8c45bfff355ae94259bc1a73a95ddbaeaf7c96b",
                    "qi": "pU1IXwiQoFERdzJsx7kSC79Gwhak7uw7OAJCbcfkKE3GSwTWHrKfg5uDZlNvSnNU1Hbpxd0bgc40dFI2aNBML1gyDwTjQplWVJikkFix8E6z_ErSa_D5w5yV4k6CNtt7OzlMXawiZ-ndcuiOs5MkfSRyeB3k5rQmuZjLVzFFlnw",
                    "dp": "Gn4dqBRQHLBn7huRgIWq_Bk7V8RrugN4yChevgKurrYBZUjWLNoa8kfF0rJ4QL7w3DT82QpSNV8utwpwlMjieFPJGfn6dcCNsq_wzQOzXNmrjClrvsSxzkSNYLiFhiqrYxQfTB5_0_B1o3tdls5acM__b1PkqX916CwQLOQTMPE",
                    "alg": "PS256",
                    "dq": "NS0x94fawWVHW6zK_SUvspXkzZ6dMxtaaqza9KuB0ldwvTBdKj09D6FWpvOwCiiwKG55rHhE2YkIMDwNG6_Iha2FdUKcPpEPjFL5vqq3SyBzNfi2lEFVZsKRdNUVv7UWekY8iHV53Vp7YANcdSOq0JWK9e4WTFblJyqLGaCCsAM",
                    "n": "s4DcK4uxKroJPE1R7Te4ppNexbuK3C-Z3MpXFr5hmY43gYIoVMo89jE6OcDiO0Z4rxe8dsH4oYA2vAJQ0IhAaUxYMk2kN01ei761zMQWHLUPLcEKWgipYHy4AgwAUaF7-Glyb0DT1RRcY4f1tEddftxhwXZjeFduj6luVg6fVvXRIRjttybUkIKvf5ShMofVFCF_IyjYlOal4g3DVnCg62dR71WX3fRXSufxrRBG-L61rv2VSMg8pIb1DFiYKDlEXEnTdLk-7goBpTIz3wBsrZgJESSZOn_BG_-fCE0V75rheLMuJd4IGE4H0taVfEQOJKRKBVzc2jAz0sOaVuPY7Q"
                }
            ]
        },
        "client_id": "Jj-hosRwYqvtnQZNph2Ah"
    },
    "mtls": {
        "cert": "-----BEGIN CERTIFICATE-----\nMIIHQDCCBiigAwIBAgIUOyyDtirdgYQIT/eSBtvaP5JRcoswDQYJKoZIhvcNAQEL\nBQAweTELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MS0wKwYDVQQDEyRPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBJc3N1aW5nIENBIC0gRzIwHhcNMjUxMTA1MjAzMjAwWhcN\nMjYxMjA1MjAzMjAwWjCCAUoxCzAJBgNVBAYTAkJSMQswCQYDVQQIEwJVSzEPMA0G\nA1UEBxMGTE9ORE9OMSYwJAYDVQQKEx1PcGVuIEJhbmtpbmcgQnJhc2lsIC0gUmFp\nZGlhbTEtMCsGA1UECxMkYjk2MWM0ZWItNTA5ZC00ZWRmLWFmZWItMzU2NDJiMzgx\nODVkMUMwQQYDVQQDEzpodHRwczovL3dlYi5jb25mb3JtYW5jZS5kaXJlY3Rvcnku\nb3BlbmJhbmtpbmdicmFzaWwub3JnLmJyMRcwFQYDVQQFEw4wMDAwMDAxMDc0Mjg1\nMTEdMBsGA1UEDxMUUHJpdmF0ZSBPcmdhbml6YXRpb24xEzARBgsrBgEEAYI3PAIB\nAxMCVUsxNDAyBgoJkiaJk/IsZAEBEyQ5ODRlODVhOS05MDAxLTQwZWItOTdiMy0x\nOTRmNWFmYmQ5NTYwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQC8bzfe\nH4l2IegWdHsOIooz+nUxpfI5v23ubPsB0P9rLEoPlIn0A7E2zg/b7UCQFvzmzgao\n49DYEbaR5B5rutlRn52rkHufNF2fNEGXgtqrko/Uwf2tGDpve+e6MRuXhyYUEwaq\nMIRL9RCqDSTHFUS+QoNaPdccw9yAQkffEckKoXJA5GYkLvkZ06Vh8R7L6Agjh1VN\ntbT3v+STfrIbSYcEXJoHwWn7vnSewcJm3B1yxpKAVySFbL336yu0cYU8RkZ42SBh\nJmGD96kmJ+vuTXQBs5ZTndbZo6/UO+r3+qaQ8rK1r4qeEYaOwSYh9wsFxpLJIgyC\nwnl0XQQnwjQKKConAgMBAAGjggLrMIIC5zAMBgNVHRMBAf8EAjAAMB0GA1UdDgQW\nBBTLmBupVqnHkdd6f2hhj5mRrTUZnzAfBgNVHSMEGDAWgBR67wuI2HqJ4b0vBD0e\nsdbER0IoPTBZBggrBgEFBQcBAQRNMEswSQYIKwYBBQUHMAGGPWh0dHA6Ly9vY3Nw\nLnBraS1nMi5zYW5kYm94LmRpcmVjdG9yeS5vcGVuYmFua2luZ2JyYXNpbC5vcmcu\nYnIwWAYDVR0fBFEwTzBNoEugSYZHaHR0cDovL2NybC5wa2ktZzIuc2FuZGJveC5k\naXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL2lzc3Vlci5jcmwwRQYD\nVR0RBD4wPII6aHR0cHM6Ly93ZWIuY29uZm9ybWFuY2UuZGlyZWN0b3J5Lm9wZW5i\nYW5raW5nYnJhc2lsLm9yZy5icjAOBgNVHQ8BAf8EBAMCBaAwEwYDVR0lBAwwCgYI\nKwYBBQUHAwIwggF0BgNVHSAEggFrMIIBZzCCAWMGCysGAQQBg7ovcAECMIIBUjCB\n9QYIKwYBBQUHAgIwgegMgeVUaGlzIENlcnRpZmljYXRlIGlzIHNvbGVseSBmb3Ig\ndXNlIHdpdGggT3BlbiBGaW5hbmNlIEJyYXNpbCBzYW5kYm94IEFQSXMgU2Vydmlj\nZXMuIEl0cyByZWNlaXB0LCBwb3NzZXNzaW9uIG9yIHVzZSBjb25zdGl0dXRlcyBh\nY2NlcHRhbmNlIG9mIHRoZSBPcGVuIEZpbmFuY2UgQnJhc2lsIHNhbmRib3ggb2Yg\nQVBJcyBDZXJ0aWZpY2F0ZSBQb2xpY3kgYW5kIHJlbGF0ZWQgZG9jdW1lbnRzIHRo\nZXJlaW4uMFgGCCsGAQUFBwIBFkxodHRwOi8vcmVwb3NpdG9yeS5wa2ktZzIuc2Fu\nZGJveC5kaXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL3BvbGljaWVz\nMA0GCSqGSIb3DQEBCwUAA4IBAQAjJQE5R9iYGgnrEpEOUGNFVqHYs8L8Y1quoglO\nYsz1GhC2bzm7WSo7iRXfil5D8om6BDM+2TsMkvH21yeNnIclIrK/ReDHqkubbWoa\n9awJDNVa6VoNRdCB6dqEiLwZl4p+bacoShQCd113v5B76gVyCPBmId41rDJv/beB\nv7F894KM4LMMkkZGSnrGft9fc8Y2CPN452EgnTh41PhJHK8DVw8mtx704gblJ64B\nwqhogdzyAjY1uz+a3M1gTTCkEEkuhYXYrHDXgz327JRCW2oXKj7oMMszMI5E4uYL\n/QQijgFOoCPdX+/SvXZo7uMl0dtegLOR/oHxOwLuryqBk9mG\n-----END CERTIFICATE-----",
        "key": "-----BEGIN PRIVATE KEY-----\nMIIEvQIBADANBgkqhkiG9w0BAQEFAASCBKcwggSjAgEAAoIBAQC8bzfeH4l2IegW\ndHsOIooz+nUxpfI5v23ubPsB0P9rLEoPlIn0A7E2zg/b7UCQFvzmzgao49DYEbaR\n5B5rutlRn52rkHufNF2fNEGXgtqrko/Uwf2tGDpve+e6MRuXhyYUEwaqMIRL9RCq\nDSTHFUS+QoNaPdccw9yAQkffEckKoXJA5GYkLvkZ06Vh8R7L6Agjh1VNtbT3v+ST\nfrIbSYcEXJoHwWn7vnSewcJm3B1yxpKAVySFbL336yu0cYU8RkZ42SBhJmGD96km\nJ+vuTXQBs5ZTndbZo6/UO+r3+qaQ8rK1r4qeEYaOwSYh9wsFxpLJIgyCwnl0XQQn\nwjQKKConAgMBAAECggEAJwYvf0hvuu/dtVzNKUm87nPVtoEED7KV7TVTrHYgl4z2\nD5D3GvpyxoNZZHYXk1+3Y4NSfMKle0H72e3w4OWy4QUZ7bB/8aIyK2jylpKqf7Lc\nJ7c/NoxYecMi4/wMl06Nc8XW8QMYOvTXTShor/Q3JuH2ewdol9P2Q/e2E7wGszUN\n9Of74KkoQ1bGf8Z3eutjqdP35/n6cETQDoFiqsV8DfHQGCiiNPKWGD2asQDhhRx4\nvh0TGIxvWF5lnSSxvbGsNFUoGWxr8eUH/EGcH1UnHfYL4xhUYqWTEOhM2v/csmzY\nt8o4BntudmXxlfgYU3NyPKkyx7/bVcnW1PJVtoDKkQKBgQDv7j0jjaWt6dJwsKa0\n5XQ4Xga1PbpDb3LWfzZr3IScUxbVytTnOWVXpok4esn4S00iQpAp7FV3YZ/qox7p\ngcOgV7lW6CIShnLgmr4CEt1hV/sRvqddmmgfrY4ZJLy24MSxwBeZiUPNRHKl9RZA\nJr2WsM04JPE4mmf9QOpGjjy71wKBgQDJDguPpQflCGT8s2KNQjBGnWGVfdNHd1vF\nOFP79wkROAEBb2mJsuBBl8Iu3YvImaKAyAln3uqOhQ8rr+y12DqBRgoAyHY3dr46\nlhQFDonNGVdOxrwRnxajKft32W8Tn6pdjuIs4N5q23Luqym5l9PA6h8aa3E+7yeE\ncvRIfqK6MQKBgG4OjED4wpzp+rvybCXictNAXjdY3037m2PE6sPDXZkPjBP5fHus\nGk6Ad8VOncKlV/Z1Lgfs/q9KOr64oH9gJMoyMzQoOyjgP2XD1ZDB8oaqguJ63+7R\n2x1c0Se7cE07AT6/7JNjIZTQ5v41VEWM/75Vz20HlRbvzO+gjVZb/IP1AoGANJwd\nQFhByZe5vTo/dpE0SrYR++kx6Qh9lgzYRR1uXPgXo0WBC0woTGGmqVbFphc1o5c0\nht6Y5/Q/dQIS4b6UCJHIOk46SOckffYZhP0559ZSt0VfnwjPBqEMsV7PJwZnsRWb\nb3zkFngYCgX15B+rhFZ/Dw3AU2SHJaxi6blhYXECgYEAnBAJuYoIfZolppeUZXwp\nAYoTLGMtXnjvX/YFumlEWzjnXLo4Lk9L+lO9sV5BwhQ6klNBARy5TjAedr+Kw0ee\noGh8F964pkF4jy7qBLMkf4/jaEvft/2tg16ELOj74llsd5GPA8Pgzeh1AXtlowwi\nC1Ere9RQ/zspggyX1uEakrI=\n-----END PRIVATE KEY-----\n",
        "ca": "-----BEGIN CERTIFICATE-----\nMIIHFDCCBPygAwIBAgIUZJOYHaqMZR7leKm8iaKrR380T8QwDQYJKoZIhvcNAQEN\nBQAwdjELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MSowKAYDVQQDEyFPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBSb290IENBIC0gRzIwHhcNMjMwMzA5MTQzNjAwWhcNMzMw\nMzA2MTQzNjAwWjB5MQswCQYDVQQGEwJCUjEcMBoGA1UEChMTT3BlbiBGaW5hbmNl\nIEJyYXNpbDEdMBsGA1UECxMUT3BlbiBGaW5hbmNlIHNhbmRib3gxLTArBgNVBAMT\nJE9wZW4gRmluYW5jZSBzYW5kYm94IElzc3VpbmcgQ0EgLSBHMjCCASIwDQYJKoZI\nhvcNAQEBBQADggEPADCCAQoCggEBAJJZYsafIn0x1j8WLDfJ3HSXt65NqnKwGdcW\nn4z4VqdrvcIl6kJM7cjF3ImaN5SLideuK63/QP4tgGilZxooxLE8V8M/uPgGU74K\noTMBuDho6sND/UtHsr/wgkX9+/Kn50vdLbhXZBmvcL+5gtXKDQGR+d1LyaU8EigX\nkhvegMCSyW72PlQ9FetapanOpH0e5+osGRVI9ysm7PFrWE6UOs8EA/d6+v8SwHTW\nbD6iVVgtGnQtm0C4w4H6VVNnFE0F8pSnXQQPzQXMONIFi/UZPSB00H0qnxRvWkw3\nJa7QErS8hdMPGUHQ9N/RujhMhf7tlUArcgod6mc+SYfcI3j1pUcCAwEAAaOCApUw\nggKRMA4GA1UdDwEB/wQEAwIBBjASBgNVHRMBAf8ECDAGAQH/AgEAMB0GA1UdDgQW\nBBR67wuI2HqJ4b0vBD0esdbER0IoPTAfBgNVHSMEGDAWgBQVb9vsej3AhKXXgbWR\nvfmoWNM++jBZBggrBgEFBQcBAQRNMEswSQYIKwYBBQUHMAGGPWh0dHA6Ly9vY3Nw\nLnBraS1nMi5zYW5kYm94LmRpcmVjdG9yeS5vcGVuYmFua2luZ2JyYXNpbC5vcmcu\nYnIwWAYDVR0fBFEwTzBNoEugSYZHaHR0cDovL2NybC5wa2ktZzIuc2FuZGJveC5k\naXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL2lzc3Vlci5jcmwwggF0\nBgNVHSAEggFrMIIBZzCCAWMGCysGAQQBg7ovcAECMIIBUjCB9QYIKwYBBQUHAgIw\ngegMgeVUaGlzIENlcnRpZmljYXRlIGlzIHNvbGVseSBmb3IgdXNlIHdpdGggT3Bl\nbiBGaW5hbmNlIEJyYXNpbCBzYW5kYm94IEFQSXMgU2VydmljZXMuIEl0cyByZWNl\naXB0LCBwb3NzZXNzaW9uIG9yIHVzZSBjb25zdGl0dXRlcyBhY2NlcHRhbmNlIG9m\nIHRoZSBPcGVuIEZpbmFuY2UgQnJhc2lsIHNhbmRib3ggb2YgQVBJcyBDZXJ0aWZp\nY2F0ZSBQb2xpY3kgYW5kIHJlbGF0ZWQgZG9jdW1lbnRzIHRoZXJlaW4uMFgGCCsG\nAQUFBwIBFkxodHRwOi8vcmVwb3NpdG9yeS5wa2ktZzIuc2FuZGJveC5kaXJlY3Rv\ncnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL3BvbGljaWVzMA0GCSqGSIb3DQEB\nDQUAA4ICAQCANeSAlmJy3e9rrgTGShVCyMQhy68j3cAJyFzqCutyNMGHUgFOjAgD\nzIUQZmAepTDJdhJF+BoruBfAIJUr6tD9EBw2MZXiTLHZG9mqtGwsMbeI3o3R9Y3G\nEpGp72jIHw7mtUZdoaWcmgqxCWn6UT9bBKAkdt6KyRepPUy1YI59MZxpVOs5J0s2\nQFd3FRCNxdzgsuGqdxTb1Gre4I5E1vJWcp1Fe/kPdaOgPVC89M6uk3WYTnMNZ20N\n8K0ecXy8+E3K+to35berWn16g1ZrufylX6s2yyxcsUnh5KP1smFd8MePekKIW0SD\n8hqD1MtGQEmzdWrPCT9fZUzONj4VuDcl/vgfKUBsBszTmqwGF34G+663v10KUhga\nkCiIOZtkT9B+aESGAfczQiFO1h4cI52TKwEptfbplrFS2gILrzleqv0JoDDFYVhY\nV5AVDjqeHaniClCi10JdSN11LqNdagpyojN2a2WhVSAigIT3yDeqozlzjgPui/1E\nDt0zBkXd5uFDwNeLUwOribuS3hxVG5Bg73ZJl+UV3ZuAzFFCfkVBz6BeqUusf8+P\n3pqAQ4gzhSWNsTBIsjaVV8ZU8IqxKhBkRUSNjihG2kM8kX9knQvRbCBuuse/dDUe\n4cUJ+wT1omVgq+TWhShOAjsHEa233omXbH7v5igLBEkzzqmM5cAv8Q==\n-----END CERTIFICATE-----\n-----BEGIN CERTIFICATE-----\nMIIFvDCCA6SgAwIBAgIUKhBUxL5Dt4w3xH1V3X1n+x/e3hcwDQYJKoZIhvcNAQEN\nBQAwdjELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MSowKAYDVQQDEyFPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBSb290IENBIC0gRzIwHhcNMjMwMzA5MTQzNjAwWhcNMzgw\nMzA1MTQzNjAwWjB2MQswCQYDVQQGEwJCUjEcMBoGA1UEChMTT3BlbiBGaW5hbmNl\nIEJyYXNpbDEdMBsGA1UECxMUT3BlbiBGaW5hbmNlIHNhbmRib3gxKjAoBgNVBAMT\nIU9wZW4gRmluYW5jZSBzYW5kYm94IFJvb3QgQ0EgLSBHMjCCAiIwDQYJKoZIhvcN\nAQEBBQADggIPADCCAgoCggIBALJFBgmKj3iDF3C8+8smNNQDxLFA9kCcca1iaxQf\nvMI/FKGW2ullHhH+W3EGEajn39QOlccGyrfCONHLqMW53+HAMtwiIvcrJgj72V7D\nnYflO3aaCFwoC31PL1+pMBo88F6jvezZ8BlRnheT7urCs6+onhz8pm0cVNc77U5X\npi8IOJz1QFKecJnFLjG0NiLCzOzjLSo0A8Rue9K/H5fjq+PqKdXG94AoQyFUwlsU\ny4aXbylDz1kRiOSnOlRNPcY/su95pFKQbGgaZZ1fLf89i5PtHAUu92FbD7H7OyYX\nXpZ97La0d7cUH0A4nb+LpOd/f0c8lAN2Ya1B8aKvWiF23q3c8EoAJyhrdkHKe6yI\nYvLC5G5jkbJefeQcp34IgD8T+Tn3aBF7YgmlYUMbnsuokBG28Hr50EAklCclA0bb\n4pmf8nE6y7VQ0CM/bNZd1F9AjxLukkyvkrOD6A6uv+c5KeC+da245dBzsyhiKe9R\nRX5Gkf7NSkDu9b9YkdDaWV6LXxpUA0SmdT9M16yK3XPDKOWBI4gVSB1KuwrOcal/\ndMwFUlxvqdGugRbxDNNukxa0l3JztGg6XYLjEiiYrQ+7HChbUVNlM0l0VZAz4eON\ngYrq2ExUDWlQXiES389/Qz3R3yDk9ib1YsMHwAux2ulCssFVn4EgtnYFfgf3o01J\n3CedAgMBAAGjQjBAMA4GA1UdDwEB/wQEAwIBBjAPBgNVHRMBAf8EBTADAQH/MB0G\nA1UdDgQWBBQVb9vsej3AhKXXgbWRvfmoWNM++jANBgkqhkiG9w0BAQ0FAAOCAgEA\nVPrUd4UDjOhkxOzSN4bMr0cULZJwQPRV8aj99tzdv8Ef44CwLVkLmm7Z2d1uRA9l\n7xbK6W8L1oL95iV4K4o2u4+ZFG7mrOfU2T2wgTfMlIxHDoAxS49flUYkBpQI1Wj4\nJBZ6fKGFVH6PyIio0I2Mx2u80ZX6lPYQ2q4DR6eBUoNt8T8XSWpD4TjroFbOVIp+\nN84alBca/pvW2aF2HwPndrL/Y++HZp3TpdUeBUT757KOZ7hdwf30pxd8qNn8+peb\nbP2h6b9pjKAmS8ciBExJzchhQWJRP6LIdvexTsBQ1HLxlZNrlg66wYT0kuVVzRTa\n0qRvIjQ0ntmhy2DtmE5VFT9O8ahcQL5Ddk8B4dhiy59vjALS6kIUXJ6GCobzRUsQ\na7b7J7nu+PTY+qVo0LsTMO1rVTUXD63gVk8QmPUwnvduk9nxraNpVP+m17BuEcls\nEsoGAAQYcmzOlnZpqhhbTnbsEayW1bMyxkLjBjXpOfBgrvyv5fU/09lP6VB20FJr\nzVPZWr5PTzaaizDDecSKgZ1ANIwXIIwWirwzDqqQb922JtcH+Ca6JJWgrV7+kDCU\ncVzwKVYievjXMCsmRSzDKEgp4n1AgrxcoaH0smD+qA+wzfsMqvEA1iTNW7zdnF0o\n6UJ9rkWxKr+JRZ5jFO+kpKQ1DxfDJZE554aO8AXzYEI=\n-----END CERTIFICATE-----\n"
    },
    "resource": {
        "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
        "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
        "brazilPaymentConsent": {
            "data": {
                "loggedUser": {
                    "document": {
                        "identification": "76109277673",
                        "rel": "CPF"
                    }
                },
                "creditor": {
                    "personType": "PESSOA_NATURAL",
                    "cpfCnpj": "48847377765",
                    "name": "Marco Antonio de Brito"
                },
                "payment": {
                    "type": "PIX",
                    "date": "2021-01-01",
                    "currency": "BRL",
                    "amount": "1333.00",
                    "details": {
                        "localInstrument": "DICT",
                        "proxy": "12345678901",
                        "creditorAccount": {
                            "ispb": "12345678",
                            "issuer": "1774",
                            "number": "1234567890",
                            "accountType": "CACC"
                        }
                    }
                },
                "debtorAccount": {
                    "ispb": "12345678",
                    "issuer": "6272",
                    "number": "94088392",
                    "accountType": "CACC"
                }
            }
        },
        "brazilQrdnPaymentConsent": {
            "data": {
                "loggedUser": {
                    "document": {
                        "identification": "76109277673",
                        "rel": "CPF"
                    }
                },
                "creditor": {
                    "personType": "PESSOA_NATURAL",
                    "cpfCnpj": "48847377765",
                    "name": "Marco Antonio de Brito"
                },
                "payment": {
                    "type": "PIX",
                    "date": "2021-01-01",
                    "currency": "BRL",
                    "amount": "1333.00",
                    "igbeTownCode": "oiweowew",
                    "details": {
                        "localInstrument": "QRDN",
                        "proxy": "cliente-a00001@pix.bcb.gov.br",
                        "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                        "creditorAccount": {
                            "ispb": "12345678",
                            "issuer": "1774",
                            "number": "1234567890",
                            "accountType": "CACC"
                        }
                    }
                },
                "debtorAccount": {
                    "ispb": "12345678",
                    "issuer": "6272",
                    "number": "94088392",
                    "accountType": "CACC"
                }
            }
        },
        "brazilQrdnCnpj": "43142666000197",
        "loggedUserIdentification": "76109277673",
        "debtorAccountIspb": "12345678",
        "debtorAccountIssuer": "1774",
        "debtorAccountNumber": "94088392",
        "debtorAccountType": "CACC",
        "paymentAmount": "1333.00"
    },
    "conditionalResources": {
        "brazilCpfTemporization": "76109277673"
    },
    "browser": [
        {
            "match": "https://auth.mockbank.openbankingbrasil.org.br/auth*",
            "tasks": [
                {
                    "task": "Login",
                    "optional": true,
                    "match": "https://auth.mockbank.openbankingbrasil.org.br/interaction*",
                    "commands": [
                        [
                            "text",
                            "name",
                            "login",
                            "ralph.bragg@gmail.com",
                            "optional"
                        ],
                        [
                            "text",
                            "name",
                            "password",
                            "P@ssword01",
                            "optional"
                        ],
                        [
                            "click",
                            "xpath",
                            "//button[contains(text(),\"Sign in\")]",
                            "optional"
                        ]
                    ]
                },
                {
                    "task": "Consent",
                    "optional": true,
                    "match": "https://auth.mockbank.openbankingbrasil.org.br/interaction*",
                    "commands": [
                        [
                            "wait",
                            "xpath",
                            "//*",
                            60,
                            ".*Before proceeding, we need to confirm some information:*",
                            "update-image-placeholder-optional"
                        ],
                        [
                            "click",
                            "xpath",
                            "//input[@id='consent-toggle']/following-sibling::div[1]"
                        ],
                        [
                            "click",
                            "id",
                            "continue-button"
                        ]
                    ]
                },
                {
                    "task": "Verify Complete",
                    "match": "*/test/*/callback*",
                    "commands": [
                        [
                            "wait",
                            "id",
                            "submission_complete",
                            10
                        ]
                    ]
                }
            ]
        }
    ],
    "override": {
        "payments_api_consents_rejection-reason_test-module_v5": {
            "resource": {
                "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "igbeTownCode": "oiweowew",
                            "details": {
                                "localInstrument": "QRDN",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilQrdnCnpj": "43142666000197",
                "loggedUserIdentification": "76109277673",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "100.00",
                "transactionIdentifier": "E00038166201907261559y6j6"
            },
            "browser": [
                {
                    "match": "https://auth.mockbank.openbankingbrasil.org.br/auth*",
                    "tasks": [
                        {
                            "task": "Login",
                            "optional": true,
                            "match": "https://auth.mockbank.openbankingbrasil.org.br/interaction*",
                            "commands": [
                                [
                                    "text",
                                    "name",
                                    "login",
                                    "ralph.bragg@gmail.com",
                                    "optional"
                                ],
                                [
                                    "text",
                                    "name",
                                    "password",
                                    "P@ssword01",
                                    "optional"
                                ],
                                [
                                    "click",
                                    "xpath",
                                    "//button[contains(text(),\"Sign in\")]",
                                    "optional"
                                ]
                            ]
                        },
                        {
                            "task": "Reject Consent",
                            "optional": true,
                            "match": "https://auth.mockbank.openbankingbrasil.org.br/interaction*",
                            "commands": [
                                [
                                    "wait",
                                    "xpath",
                                    "//*",
                                    10,
                                    ".*Before proceeding, we need to confirm some information:*",
                                    "update-image-placeholder-optional"
                                ],
                                [
                                    "click",
                                    "id",
                                    "cancel-button"
                                ]
                            ]
                        },
                        {
                            "task": "Verify Complete",
                            "match": "*/test/*/callback*",
                            "commands": [
                                [
                                    "wait",
                                    "id",
                                    "submission_complete",
                                    10
                                ]
                            ]
                        }
                    ]
                }
            ]
        },
        "payments_api_invalid-token_test-module_v5": {
            "resource": {
                "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "igbeTownCode": "oiweowew",
                            "details": {
                                "localInstrument": "QRDN",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilQrdnCnpj": "43142666000197",
                "loggedUserIdentification": "76109277673",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "100.00",
                "transactionIdentifier": "E00038166201907261559y6j6"
            }
        },
        "payments_api_pixscheduling-patch-detentora_test-module_v5": {
            "resource": {
                "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "1400.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "1400.00",
                            "igbeTownCode": "oiweowew",
                            "details": {
                                "localInstrument": "QRDN",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilQrdnCnpj": "43142666000197",
                "loggedUserIdentification": "76109277673",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "1400.00",
                "transactionIdentifier": "E00038166201907261559y6j6"
            }
        },
        "payments_api_pixscheduling-patch-iniciadora_test-module_v5": {
            "resource": {
                "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "igbeTownCode": "oiweowew",
                            "details": {
                                "localInstrument": "QRDN",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilQrdnCnpj": "43142666000197",
                "loggedUserIdentification": "76109277673",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "100.00",
                "transactionIdentifier": "E00038166201907261559y6j6"
            }
        },
        "payments_api_pixscheduling-patch-unhappy_test-module_v5": {
            "resource": {
                "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "igbeTownCode": "oiweowew",
                            "details": {
                                "localInstrument": "QRDN",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilQrdnCnpj": "43142666000197",
                "loggedUserIdentification": "76109277673",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "100.00",
                "transactionIdentifier": "E00038166201907261559y6j6"
            }
        },
        "payments_api_pixscheduling-schd-accepted_test-module_v5": {
            "resource": {
                "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "igbeTownCode": "oiweowew",
                            "details": {
                                "localInstrument": "QRDN",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilQrdnCnpj": "43142666000197",
                "loggedUserIdentification": "76109277673",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "100.00",
                "transactionIdentifier": "E00038166201907261559y6j6"
            }
        },
        "payments_api_x-fapi_test-module_v5": {
            "resource": {
                "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "1400.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "1400.00",
                            "igbeTownCode": "oiweowew",
                            "details": {
                                "localInstrument": "QRDN",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilQrdnCnpj": "43142666000197",
                "loggedUserIdentification": "76109277673",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "1400.00",
                "transactionIdentifier": "E00038166201907261559y6j6"
            }
        },
        "payments_api_real-email-invalid-creditor-proxy_test-module_v5": {
            "resource": {
                "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "20201.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "20201.00",
                            "igbeTownCode": "oiweowew",
                            "details": {
                                "localInstrument": "QRDN",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilQrdnCnpj": "43142666000197",
                "loggedUserIdentification": "76109277673",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "20201.00",
                "transactionIdentifier": "E00038166201907261559y6j6"
            }
        },
        "payments_api_fake-email-proxy_test-module_v5": {
            "resource": {
                "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "20201.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "20201.00",
                            "igbeTownCode": "oiweowew",
                            "details": {
                                "localInstrument": "QRDN",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilQrdnCnpj": "43142666000197",
                "loggedUserIdentification": "76109277673",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "20201.00",
                "transactionIdentifier": "E00038166201907261559y6j6"
            }
        },
        "payments_api_consumed-consent_test-module_v5": {
            "resource": {
                "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "1336.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "1336.00",
                            "igbeTownCode": "oiweowew",
                            "details": {
                                "localInstrument": "QRDN",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilQrdnCnpj": "43142666000197",
                "loggedUserIdentification": "76109277673",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "1336.00",
                "transactionIdentifier": "E00038166201907261559y6j6"
            }
        },
        "payments_api_recurring-payments-custom-core_test-module_v5": {
            "resource": {
                "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "igbeTownCode": "oiweowew",
                            "details": {
                                "localInstrument": "QRDN",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilQrdnCnpj": "43142666000197",
                "loggedUserIdentification": "76109277673",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "100.00",
                "transactionIdentifier": "E00038166201907261559y6j6"
            }
        },
        "payments_api_recurring-payments-daily-core_test-module_v5": {
            "resource": {
                "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "igbeTownCode": "oiweowew",
                            "details": {
                                "localInstrument": "QRDN",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilQrdnCnpj": "43142666000197",
                "loggedUserIdentification": "76109277673",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "100.00",
                "transactionIdentifier": "E00038166201907261559y6j6"
            }
        },
        "payments_api_recurring-payments-large-batch_test-module_v5": {
            "resource": {
                "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "igbeTownCode": "oiweowew",
                            "details": {
                                "localInstrument": "QRDN",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilQrdnCnpj": "43142666000197",
                "loggedUserIdentification": "76109277673",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "100.00",
                "transactionIdentifier": "E00038166201907261559y6j6"
            }
        },
        "payments_api_recurring-payments-monthly-core_test-module_v5": {
            "resource": {
                "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "igbeTownCode": "oiweowew",
                            "details": {
                                "localInstrument": "QRDN",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilQrdnCnpj": "43142666000197",
                "loggedUserIdentification": "76109277673",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "100.00",
                "transactionIdentifier": "E00038166201907261559y6j6"
            }
        },
        "payments_api_recurring_payments_weekly_test-module_v5": {
            "resource": {
                "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "igbeTownCode": "oiweowew",
                            "details": {
                                "localInstrument": "QRDN",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilQrdnCnpj": "43142666000197",
                "loggedUserIdentification": "76109277673",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "100.00",
                "transactionIdentifier": "E00038166201907261559y6j6"
            }
        },
        "payments_api_recurring-payments-patch_test-module_v5": {
            "resource": {
                "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "igbeTownCode": "oiweowew",
                            "details": {
                                "localInstrument": "QRDN",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilQrdnCnpj": "43142666000197",
                "loggedUserIdentification": "76109277673",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "100.00",
                "transactionIdentifier": "E00038166201907261559y6j6"
            }
        },
        "payments_api_jti-reuse_test-module_v5": {
            "resource": {
                "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "igbeTownCode": "oiweowew",
                            "details": {
                                "localInstrument": "QRDN",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilQrdnCnpj": "43142666000197",
                "loggedUserIdentification": "76109277673",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "100.00",
                "transactionIdentifier": "E00038166201907261559y6j6"
            }
        },
        "payments_api_idempotency_test-module_v5": {
            "resource": {
                "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "igbeTownCode": "oiweowew",
                            "details": {
                                "localInstrument": "QRDN",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilQrdnCnpj": "43142666000197",
                "loggedUserIdentification": "76109277673",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "100.00",
                "transactionIdentifier": "E00038166201907261559y6j6"
            }
        }
    }
}
```

</details>

<details>
<summary>JSON Configuration for No Redirect Payments v2 (Auto Redirect)</summary>

```
{
    "consent": {
        "productType": "personal"
    },
    "alias": "obbsb",
    "description": "Phase 3 - No Redirect Payments v2",
    "publish": "everything",
    "server": {
        "discoveryUrl": "https://auth.mockbank.openbankingbrasil.org.br/.well-known/openid-configuration"
    },
    "directory": {
        "keystore": "https://keystore.sandbox.directory.openbankingbrasil.org.br/",
        "discoveryUrl": "https://auth.sandbox.directory.openbankingbrasil.org.br/.well-known/openid-configuration",
        "apibase": "https://matls-api.sandbox.directory.openbankingbrasil.org.br/",
        "client_id": "984e85a9-9001-40eb-97b3-194f5afbd956"
    },
    "resource": {
        "resourceUrl": "https://auth.mockbank.openbankingbrasil.org.br/open-banking/payments/v3/pix/payments",
        "consentUrl": "https://auth.mockbank.openbankingbrasil.org.br/open-banking/payments/v3/consents",
        "enrollmentsUrl": "https://auth.mockbank.openbankingbrasil.org.br/open-banking/enrollments/v2/enrollments",
        "webhookWaitTime": "5",
        "brazilPaymentConsent": {
            "data": {
                "loggedUser": {
                    "document": {
                        "identification": "76109277673",
                        "rel": "CPF"
                    }
                },
                "creditor": {
                    "personType": "PESSOA_NATURAL",
                    "cpfCnpj": "48847377765",
                    "name": "Marco Antonio de Brito"
                },
                "payment": {
                    "type": "PIX",
                    "date": "2021-01-01",
                    "currency": "BRL",
                    "amount": "1333.00",
                    "details": {
                        "localInstrument": "DICT",
                        "proxy": "12345678901",
                        "creditorAccount": {
                            "ispb": "12345678",
                            "issuer": "1774",
                            "number": "1234567890",
                            "accountType": "CACC"
                        }
                    }
                },
                "debtorAccount": {
                    "ispb": "12345678",
                    "issuer": "6272",
                    "number": "94088392",
                    "accountType": "CACC"
                }
            }
        },
        "brazilQrdnPaymentConsent": {
            "data": {
                "loggedUser": {
                    "document": {
                        "identification": "76109277673",
                        "rel": "CPF"
                    }
                },
                "creditor": {
                    "personType": "PESSOA_NATURAL",
                    "cpfCnpj": "48847377765",
                    "name": "Marco Antonio de Brito"
                },
                "payment": {
                    "type": "PIX",
                    "date": "2021-01-01",
                    "currency": "BRL",
                    "amount": "1333.00",
                    "igbeTownCode": "oiweowew",
                    "details": {
                        "localInstrument": "QRDN",
                        "proxy": "cliente-a00001@pix.bcb.gov.br",
                        "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                        "creditorAccount": {
                            "ispb": "12345678",
                            "issuer": "1774",
                            "number": "1234567890",
                            "accountType": "CACC"
                        }
                    }
                },
                "debtorAccount": {
                    "ispb": "12345678",
                    "issuer": "6272",
                    "number": "94088392",
                    "accountType": "CACC"
                }
            }
        },
        "brazilCpf": "76109277673",
        "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
        "loggedUserIdentification": "76109277673",
        "debtorAccountIspb": "12345678",
        "debtorAccountIssuer": "1774",
        "debtorAccountNumber": "94088392",
        "debtorAccountType": "CACC",
        "paymentAmount": "100.00"
    },
    "conditionalResources": {
        "brazilCpfJointAccount": "87517400444"
    },
    "client": {
        "jwks": {
            "keys": [
                {
                    "alg": "PS256",
                    "d": "Q9gSOfnkGJnAsV3a94j9ae9ihjqgMwXgVm73VTyEs1u9Jq73pCWX0e9JdeNMKdgKpiJYjyxa3ttxCY58eiGKEi7c50zYRx8YLTL2rIVWqS6JVGpXuzIQutkQDM4AfD72bG3-xT-caSCansGbdEIFJjX32Ujbs1UUoQlE96m3hNOjB5vNyHBWrBUgUGG9_uJiWFG6Lbj8ZGtiihA_PQkzuArLzDvO2OMVHCzIyQ4CwFE1tI9xHFHpioJQXBnymURQvkm3MmEwHRG_KUdABQ55gG32jothy7jOOYAMkvOCejteTZv1nT4dsEj-CBxDBtTI6SerXb11VX8b0suzSBxx0Q",
                    "dp": "S15AOPpOtYgYjfOi2rNojY3NpU-Qobnfnnt_MZEJ2_DS0bGwXSgGJjHOOOAowy1HK0n7-AhXbwhr026sBuicR_Kpj6RkzGVrJug8y9R02FXZwlQpgjSBZdO6C2B1OOvtyKmnKg5q1KdQ7Kx6vYPV7UutOJn6NlH0RbFgG4NGelk",
                    "dq": "oBgBMB54mtrriQCg4YyDY_zf7LW4f6oqiUl3l7odf_ArjVamjHM-boZnhGoVzZ5uXNs03wEdBIc2HLmsoGLVuodcYHjyptmvyPebiH2mavFlUlI8ILG6lkyIhMp3Ri8iXGX2MYlPjP2EawNDMHB6BO0bZ5NugyzxuF_OKhfEFLc",
                    "e": "AQAB",
                    "kid": "-duNE0ZX5NmDkUlgNoqDY5Ve7UdFTA7S25WJSAv8tNQ",
                    "kty": "RSA",
                    "n": "-6Ep5kV0qcQnrxQzbEgMGKQRHnhXlp3ZpAVqQbbzkVG_a1tHLi0V7YAmjf3isXMvdvWjApeShL32gqxgcKDvC5Mnd5ufR1ujzb5lsnYXy-tKMQWnAlCqy7mSuxi8JIBXyZb7CMGU29L32Tvd5MjDh_hSgwnHcTggE-ehqzK5eyvK7DjvlbfCKXgDx94kMcwyI2K0EurahHj9_I3lEQzAt73OocF_z84FQxO87A8Q1cM3nEGyykZPaFyulQ4bf4U2tT_Jfd0ppYX1j194ouPeqMZBsGnxKf4L4QvuberbRpdeOO92HhWHHiwiTuhYxF876-LKgPzqxK-Y1a2_4gsVAw",
                    "p": "_oebNFofSe_8fdotMxUEk7n3pq5eT96rO_VPdHyTZERDrkU0djQf9BLy7DejYoRReuI0AJWkBL9EGBhECaowmx8gTCs43ffQrBDULYB4elmS07ov1pq1STqzqRKbu_INaSGVgxFzhYC_EeFVpB0RPlAUvb1_aQkH79J8VMnp2_U",
                    "q": "_RVEyO9NB6XiJjMz9t6XrNxG01Vguo2VVBLaDJhoi1g7gydUDkNc9twhF1Ifps8Gf3m9aMjjOmYqE5kuWCPBHxkk8cZOm4C2AhVbQxMkZLOyPeJDfKfCi7yJRIfmwqQM5AKosALfN-jW_p746lRhCAps8eH9XF6bjugi_MH1yhc",
                    "qi": "yXG_vCx0xL9DlU7f0Ixub9NSD1QJtAJYxwKyHukw_8f4rHLiZ8eeCerfZfPd7zsPGSqOmY2605MNT1Z2ohYgoRyu05uwstEDKqtgl_uxupfO6AJKCja4paIB-ICvQQXpOY1n9BW6VcDwSylTnv1pKvVnTvxzy5z008wvrafQtFw",
                    "use": "sig"
                },
                {
                    "kty": "RSA",
                    "alg": "PS256",
                    "use": "enc",
                    "kid": "e96744c58188c084310920b152ffb02a392b119a009fb1fa1a656006715e1604",
                    "n": "4eIXvOR1XXo3MT9syMwRZj2ChbV2Qlp_623VCIhYvPtJ5k5rlCr1hP4n0PC49U47pa3UKNs6DYHefHKm9I4h4crgk7zsln2_JP3kK1equqIO1U12Rv4Xbm_2_eqR3hPKcE3il2ky2Neby8OThFnyDwBNKdxI4MvOKm910qQhYns2L4w_i9fjF2z1Wpi6sMPW8IERhkqaBWgoaH9g2obGbNuoYCzEjOWvRb_nVjYKRPqTI2A11kWZ4mVTRkTO4yM1gdI7z8Hsl4fqlEXeVdmMkVJhRvQa-vFfegecgO8nUY2XoOUx_UR51F8PO9bepy-jH16cRDwjLE-2ex7mE_wfMw",
                    "e": "AQAB",
                    "d": "BqovoVF4vww8nA9IuLhnHDlDZFbHov4qZeCecQgcEJNpIxdiqDZuR4EvECsSIgOWOFvwW-lzOI1oHaVNlMvezXU5eoWpnpuEnzHlYHwCzxftNrde5PBZWHC-sAMStvBzJpLw7riNZgWFx_wNmoTQfHqgGQfLyxcB9Pf6v387qiN1wHfSXQshtFiDg_6tBaH6dS1jRAg7_56dQp1wWJeRaqMCg9QeESmo3c-76hnRSMU6fgrONU6qGMSLopv-nirh3H1gZePcXzVgf9cerRMQgV1pWUZEd_iJqTaX8U7wB0txmVF6QzRxR71Ah6nZuV_Rv7X88zB8u0rXOvjeGtuZKQ",
                    "p": "8fN0GXyZnvxba4yoOgdL9ta9pkjjWVu5eTOIyvSgKf09hUSWKL6sKm1N0l68detwzBFpnxObOeUCMnU_BFhJM-s0w5GognaAX6GB5-TzdYHwmsgqAch3-_hi_kZU6A-SLZu7bQFGXTEotQ1zMxVuCMZ7AjTs0CGZrS-vItFYtik",
                    "q": "7v_Ldwh3L9On2CNAefLgs7dyDBAgWrkXOJ9Z1EnrKgMHbqgq5dOixv2ezKNdOUte9G4ve555XTf2sC-p0TF9PNYC0_4KthI8NLik8RtDsQmYJUYw7qfV_YitzGflM2DRr6KaV5SmO_aPWRfzuVWh_6kIQ_GmXf47ASasKVeD_fs",
                    "dp": "Jyi-_q0C9A9mAHcodxPdQJsq4LHlUf4de7dSiX6kOYeKIHqkTv3lQYylTsoUeIVdoTmkPaHfurQM8fu18k8Tsfp8dLarbkodptyt-Mk-eiNIvNRusBExEi_2Xa8maNS0VPtij1boe4bMTtlZbsgmIfd1yzqjpV_6zmPsVZdKY1k",
                    "dq": "qjW-YA3FZGhmtwWUG8Wfxh41uOWbRUFgilDils_2DTuPBX363yc0XGevuqn18KH_BDGc23tnj74VkDDBzlxihvsblILuefDOs_V0csoqEWF128X7f1xEiIXY0SSFFWw0qdMx_IG_SiE0wgzO5QVZlEx7uHfXNkWjHBTAs8jCFhU",
                    "qi": "8W2vDdiA8qDxL2fiJPP2m3NqbjGW7Tf5PsfGo0Gqfv6nWVweuVwsyUNT1AYduZUCvFRG5LRNHqiwZNpNB6XQln1W41GaIqGkHWJkveHhg9xIQmSK2hrX4OnSdyvMiGiB2yvce0FTgQ0OzXuNkIKJKJLP2nAJusNgNcVT7qgKCRA"
                }
            ]
        },
        "org_jwks": {
            "keys": [
                {
                    "d": "BpgLagicLjysglxtDX7bJnOv4-IP-5yyGdL4oOkDCl_-lO8twPDhWLfXNCf2QTs7l1T1GLNUyALKjYDNEvjbpu03_K1dtRwO2ZS4_VHTPhe99Etn1GXntdfcFvQiD9Lz6uzs2-0DOIG_5xWUiVhTUN5HPRfMMXF3ktG2ucTOQqsJU0O2SOohVIvqYH4EDJNIw8qUsu1C2JEDMj79H_8KaXEUVx8tFFLMxmt67a_a7sImXvEaIYhUCu-DMMDrzBc660s_eTcihJ_DkJgYPPWctnmpUClKa4zgABDqGXhPQFfLS4ywGAHnLZF1MyNeKFXpmeJShjNJ5MqjBKJTnFHDQKs",
                    "dp": "CFfrENWCU61YHATfdTy73lt2reMz0dBDicy92s4FqHpcup6O6f5MWGvhpBlLVC-tNA97qzyKExFwxl6c6rf45l8T6GLjy4C2DJEH0pGKeh7-PP7XW1KBvsclbJdSoSj-bOFRomFVGKYhIF3nRnr9-Dvj1k8aEcClPT1E9i9rGI7P",
                    "dq": "BzCeCJQ9pKQVCpyFi50PR8_E7d9uW9nYqJpf0GBT5XdnZ44qnliLAffZmVwcxXh6e_JzIjC0ByJrYKd_dekXLCrsOex1XxqvI7WH6EZ3Nvoe_1835ZgtQ2PsPSvGKifHHPXocKyqqRdT7KlGTXfnpKtezsXPxe63VS-3coE62-_F",
                    "e": "AQAB",
                    "kid": "EKSYJfNcI8Bm22_dP0ziWpTjw9UceAdVjykgwO5BkfE",
                    "kty": "RSA",
                    "n": "oBp-b0EhezRYfisJBL_WA2Yh0Y2zPYHsy8N4G9mddkop-kFJT12XSSBx8GXmyjDL14Wg5vRNA6R_TwXbJbnHnE59uMYiWNi_G7OL6jMsncmYdyBuwl-lDWExaXC5Qg9vYgGnt7d1SthQoiJkduPIiNpniq5p7px-jJYQO4SECUqpeLl9rU_Xvxn5zpFu4dw65wBi4oSDiJ0zujQtxofOmbJCKYTWrPmd8yPlPgwIttP2ZcprMs5Ya57-99NhAealcVptRTOQTEWEOflmurq58Byu7pT64ns-9Su8JPcHMMzxOOVM7KNPuZA7Xa5-1aBd1XrhxkBHIDzUqOpanSlr2uk",
                    "p": "DgL5bOQ5-JXM6Ed_3BRKW2a3EcHB_UjlWPlGGkc0RBeEwlNi6D3PQGZmgTxyGXWA4W3HMi2S2pXx8oxWd9rrw9Uc_BNrIdvkMcU9LnkCvxK-dcHalVrXhv0l1EbQx0mG9LjLsiqmJiJYnUYTuLjO8lJaebSTp-EH2fgTs81_SBKv",
                    "q": "C20t29WtF9yAXt2r5Yu7chtrJUMIsu_TUY2N6p75BWWBB76oNib4Dp5fVePnbTqdSP913dS1K1vHwEAqS_Z_C6vfmaYha6Hguipo5jotTTJoYDxV_xTp1dGWcr8MltBE9ikhLa8xvGVxXjSi4vkqc_TyXlBSHbbBSZtjB32rCLHn",
                    "qi": "BRx-2fqZYWrIzcayN1v10HfzcQaZue-NNZP7Eid81oBBxBrDQmiGdzQLi0BKctjLBr21_GWUgHgEYRym3He5biuDVM0WnyhXYeLLc_pv3bIG6FoPrP4XDZo4GTM4JdVj2im_OQWdXuokFzsZzeVV6H8p46TxpyNDix5oFjmyuB11",
                    "alg": "PS256",
                    "use": "sig"
                },
                {
                    "p": "2a8fRJ7ybF-qtF1zrYzSm7z3C4wNTUMbVYqe44tR9FbKsobqW2tS0iAZf-GJ_SZPcWxkE76gunW7YqMJecGUtXsJ8TTHwjcPQOMYzxnyJu8Q4JOj01YJVrxUY9D0ZzpWM9oTAj1-qoE0w7Dy-XNUc14-HeRlmOkg2tTfrXTVR8c",
                    "kty": "RSA",
                    "q": "0xlPJFRUcBU5j2SKSajVnd4H5p88RSsd4cArMby1ZRuSeHEsX76c6QKAPq7uTfKrTeZic34yzAEUyHloP1fZQYQ2UQn-f6PsTAWdT1Lp5oi2VZCT0yc9-1EGnLAiUCbM9SQQyf2GIVhCiAk_0VuY6le61Pw0U4GssvFJzIrx4as",
                    "d": "GxnizpWcqL1wajD8-Y-8H9-II4UZMKfkgbfwRiLK9uAd8-kEJdO9jdNeMxyytg2saDhxNTeRTkYz_VbBf3p9dGhuYx84d-ZagUbIiU3ho3FCsBRrzQQZw9OQrzPDUzp0-SBn1_GLCf9fo4ysxWHbn9euJVi2fpN_bHlBi1n8fKhdBHYE7X3XJnRYrUXItxZw5sJsqM_boONLxdLAvgmZx5CHft94JZsR6JPwlj9Ba_CuNWX_3OuUGyV0f5_1ICAEYijw9PA8KAW6t5UUYn39_KYL8nF5L1Bh6W1j8eN84I2lcKZNO6Pou064ag_wqGhk4uXuQO1IV8jRFn3-pqhSEQ",
                    "e": "AQAB",
                    "use": "enc",
                    "kid": "c1d7b80ce4b88c4f2cfb68e7a8c45bfff355ae94259bc1a73a95ddbaeaf7c96b",
                    "qi": "pU1IXwiQoFERdzJsx7kSC79Gwhak7uw7OAJCbcfkKE3GSwTWHrKfg5uDZlNvSnNU1Hbpxd0bgc40dFI2aNBML1gyDwTjQplWVJikkFix8E6z_ErSa_D5w5yV4k6CNtt7OzlMXawiZ-ndcuiOs5MkfSRyeB3k5rQmuZjLVzFFlnw",
                    "dp": "Gn4dqBRQHLBn7huRgIWq_Bk7V8RrugN4yChevgKurrYBZUjWLNoa8kfF0rJ4QL7w3DT82QpSNV8utwpwlMjieFPJGfn6dcCNsq_wzQOzXNmrjClrvsSxzkSNYLiFhiqrYxQfTB5_0_B1o3tdls5acM__b1PkqX916CwQLOQTMPE",
                    "alg": "PS256",
                    "dq": "NS0x94fawWVHW6zK_SUvspXkzZ6dMxtaaqza9KuB0ldwvTBdKj09D6FWpvOwCiiwKG55rHhE2YkIMDwNG6_Iha2FdUKcPpEPjFL5vqq3SyBzNfi2lEFVZsKRdNUVv7UWekY8iHV53Vp7YANcdSOq0JWK9e4WTFblJyqLGaCCsAM",
                    "n": "s4DcK4uxKroJPE1R7Te4ppNexbuK3C-Z3MpXFr5hmY43gYIoVMo89jE6OcDiO0Z4rxe8dsH4oYA2vAJQ0IhAaUxYMk2kN01ei761zMQWHLUPLcEKWgipYHy4AgwAUaF7-Glyb0DT1RRcY4f1tEddftxhwXZjeFduj6luVg6fVvXRIRjttybUkIKvf5ShMofVFCF_IyjYlOal4g3DVnCg62dR71WX3fRXSufxrRBG-L61rv2VSMg8pIb1DFiYKDlEXEnTdLk-7goBpTIz3wBsrZgJESSZOn_BG_-fCE0V75rheLMuJd4IGE4H0taVfEQOJKRKBVzc2jAz0sOaVuPY7Q"
                }
            ]
        },
        "client_id": "Jj-hosRwYqvtnQZNph2Ah"
    },
    "mtls": {
        "cert": "-----BEGIN CERTIFICATE-----\nMIIHQDCCBiigAwIBAgIUOyyDtirdgYQIT/eSBtvaP5JRcoswDQYJKoZIhvcNAQEL\nBQAweTELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MS0wKwYDVQQDEyRPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBJc3N1aW5nIENBIC0gRzIwHhcNMjUxMTA1MjAzMjAwWhcN\nMjYxMjA1MjAzMjAwWjCCAUoxCzAJBgNVBAYTAkJSMQswCQYDVQQIEwJVSzEPMA0G\nA1UEBxMGTE9ORE9OMSYwJAYDVQQKEx1PcGVuIEJhbmtpbmcgQnJhc2lsIC0gUmFp\nZGlhbTEtMCsGA1UECxMkYjk2MWM0ZWItNTA5ZC00ZWRmLWFmZWItMzU2NDJiMzgx\nODVkMUMwQQYDVQQDEzpodHRwczovL3dlYi5jb25mb3JtYW5jZS5kaXJlY3Rvcnku\nb3BlbmJhbmtpbmdicmFzaWwub3JnLmJyMRcwFQYDVQQFEw4wMDAwMDAxMDc0Mjg1\nMTEdMBsGA1UEDxMUUHJpdmF0ZSBPcmdhbml6YXRpb24xEzARBgsrBgEEAYI3PAIB\nAxMCVUsxNDAyBgoJkiaJk/IsZAEBEyQ5ODRlODVhOS05MDAxLTQwZWItOTdiMy0x\nOTRmNWFmYmQ5NTYwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQC8bzfe\nH4l2IegWdHsOIooz+nUxpfI5v23ubPsB0P9rLEoPlIn0A7E2zg/b7UCQFvzmzgao\n49DYEbaR5B5rutlRn52rkHufNF2fNEGXgtqrko/Uwf2tGDpve+e6MRuXhyYUEwaq\nMIRL9RCqDSTHFUS+QoNaPdccw9yAQkffEckKoXJA5GYkLvkZ06Vh8R7L6Agjh1VN\ntbT3v+STfrIbSYcEXJoHwWn7vnSewcJm3B1yxpKAVySFbL336yu0cYU8RkZ42SBh\nJmGD96kmJ+vuTXQBs5ZTndbZo6/UO+r3+qaQ8rK1r4qeEYaOwSYh9wsFxpLJIgyC\nwnl0XQQnwjQKKConAgMBAAGjggLrMIIC5zAMBgNVHRMBAf8EAjAAMB0GA1UdDgQW\nBBTLmBupVqnHkdd6f2hhj5mRrTUZnzAfBgNVHSMEGDAWgBR67wuI2HqJ4b0vBD0e\nsdbER0IoPTBZBggrBgEFBQcBAQRNMEswSQYIKwYBBQUHMAGGPWh0dHA6Ly9vY3Nw\nLnBraS1nMi5zYW5kYm94LmRpcmVjdG9yeS5vcGVuYmFua2luZ2JyYXNpbC5vcmcu\nYnIwWAYDVR0fBFEwTzBNoEugSYZHaHR0cDovL2NybC5wa2ktZzIuc2FuZGJveC5k\naXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL2lzc3Vlci5jcmwwRQYD\nVR0RBD4wPII6aHR0cHM6Ly93ZWIuY29uZm9ybWFuY2UuZGlyZWN0b3J5Lm9wZW5i\nYW5raW5nYnJhc2lsLm9yZy5icjAOBgNVHQ8BAf8EBAMCBaAwEwYDVR0lBAwwCgYI\nKwYBBQUHAwIwggF0BgNVHSAEggFrMIIBZzCCAWMGCysGAQQBg7ovcAECMIIBUjCB\n9QYIKwYBBQUHAgIwgegMgeVUaGlzIENlcnRpZmljYXRlIGlzIHNvbGVseSBmb3Ig\ndXNlIHdpdGggT3BlbiBGaW5hbmNlIEJyYXNpbCBzYW5kYm94IEFQSXMgU2Vydmlj\nZXMuIEl0cyByZWNlaXB0LCBwb3NzZXNzaW9uIG9yIHVzZSBjb25zdGl0dXRlcyBh\nY2NlcHRhbmNlIG9mIHRoZSBPcGVuIEZpbmFuY2UgQnJhc2lsIHNhbmRib3ggb2Yg\nQVBJcyBDZXJ0aWZpY2F0ZSBQb2xpY3kgYW5kIHJlbGF0ZWQgZG9jdW1lbnRzIHRo\nZXJlaW4uMFgGCCsGAQUFBwIBFkxodHRwOi8vcmVwb3NpdG9yeS5wa2ktZzIuc2Fu\nZGJveC5kaXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL3BvbGljaWVz\nMA0GCSqGSIb3DQEBCwUAA4IBAQAjJQE5R9iYGgnrEpEOUGNFVqHYs8L8Y1quoglO\nYsz1GhC2bzm7WSo7iRXfil5D8om6BDM+2TsMkvH21yeNnIclIrK/ReDHqkubbWoa\n9awJDNVa6VoNRdCB6dqEiLwZl4p+bacoShQCd113v5B76gVyCPBmId41rDJv/beB\nv7F894KM4LMMkkZGSnrGft9fc8Y2CPN452EgnTh41PhJHK8DVw8mtx704gblJ64B\nwqhogdzyAjY1uz+a3M1gTTCkEEkuhYXYrHDXgz327JRCW2oXKj7oMMszMI5E4uYL\n/QQijgFOoCPdX+/SvXZo7uMl0dtegLOR/oHxOwLuryqBk9mG\n-----END CERTIFICATE-----",
        "key": "-----BEGIN PRIVATE KEY-----\nMIIEvQIBADANBgkqhkiG9w0BAQEFAASCBKcwggSjAgEAAoIBAQC8bzfeH4l2IegW\ndHsOIooz+nUxpfI5v23ubPsB0P9rLEoPlIn0A7E2zg/b7UCQFvzmzgao49DYEbaR\n5B5rutlRn52rkHufNF2fNEGXgtqrko/Uwf2tGDpve+e6MRuXhyYUEwaqMIRL9RCq\nDSTHFUS+QoNaPdccw9yAQkffEckKoXJA5GYkLvkZ06Vh8R7L6Agjh1VNtbT3v+ST\nfrIbSYcEXJoHwWn7vnSewcJm3B1yxpKAVySFbL336yu0cYU8RkZ42SBhJmGD96km\nJ+vuTXQBs5ZTndbZo6/UO+r3+qaQ8rK1r4qeEYaOwSYh9wsFxpLJIgyCwnl0XQQn\nwjQKKConAgMBAAECggEAJwYvf0hvuu/dtVzNKUm87nPVtoEED7KV7TVTrHYgl4z2\nD5D3GvpyxoNZZHYXk1+3Y4NSfMKle0H72e3w4OWy4QUZ7bB/8aIyK2jylpKqf7Lc\nJ7c/NoxYecMi4/wMl06Nc8XW8QMYOvTXTShor/Q3JuH2ewdol9P2Q/e2E7wGszUN\n9Of74KkoQ1bGf8Z3eutjqdP35/n6cETQDoFiqsV8DfHQGCiiNPKWGD2asQDhhRx4\nvh0TGIxvWF5lnSSxvbGsNFUoGWxr8eUH/EGcH1UnHfYL4xhUYqWTEOhM2v/csmzY\nt8o4BntudmXxlfgYU3NyPKkyx7/bVcnW1PJVtoDKkQKBgQDv7j0jjaWt6dJwsKa0\n5XQ4Xga1PbpDb3LWfzZr3IScUxbVytTnOWVXpok4esn4S00iQpAp7FV3YZ/qox7p\ngcOgV7lW6CIShnLgmr4CEt1hV/sRvqddmmgfrY4ZJLy24MSxwBeZiUPNRHKl9RZA\nJr2WsM04JPE4mmf9QOpGjjy71wKBgQDJDguPpQflCGT8s2KNQjBGnWGVfdNHd1vF\nOFP79wkROAEBb2mJsuBBl8Iu3YvImaKAyAln3uqOhQ8rr+y12DqBRgoAyHY3dr46\nlhQFDonNGVdOxrwRnxajKft32W8Tn6pdjuIs4N5q23Luqym5l9PA6h8aa3E+7yeE\ncvRIfqK6MQKBgG4OjED4wpzp+rvybCXictNAXjdY3037m2PE6sPDXZkPjBP5fHus\nGk6Ad8VOncKlV/Z1Lgfs/q9KOr64oH9gJMoyMzQoOyjgP2XD1ZDB8oaqguJ63+7R\n2x1c0Se7cE07AT6/7JNjIZTQ5v41VEWM/75Vz20HlRbvzO+gjVZb/IP1AoGANJwd\nQFhByZe5vTo/dpE0SrYR++kx6Qh9lgzYRR1uXPgXo0WBC0woTGGmqVbFphc1o5c0\nht6Y5/Q/dQIS4b6UCJHIOk46SOckffYZhP0559ZSt0VfnwjPBqEMsV7PJwZnsRWb\nb3zkFngYCgX15B+rhFZ/Dw3AU2SHJaxi6blhYXECgYEAnBAJuYoIfZolppeUZXwp\nAYoTLGMtXnjvX/YFumlEWzjnXLo4Lk9L+lO9sV5BwhQ6klNBARy5TjAedr+Kw0ee\noGh8F964pkF4jy7qBLMkf4/jaEvft/2tg16ELOj74llsd5GPA8Pgzeh1AXtlowwi\nC1Ere9RQ/zspggyX1uEakrI=\n-----END PRIVATE KEY-----\n",
        "ca": "-----BEGIN CERTIFICATE-----\nMIIHFDCCBPygAwIBAgIUZJOYHaqMZR7leKm8iaKrR380T8QwDQYJKoZIhvcNAQEN\nBQAwdjELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MSowKAYDVQQDEyFPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBSb290IENBIC0gRzIwHhcNMjMwMzA5MTQzNjAwWhcNMzMw\nMzA2MTQzNjAwWjB5MQswCQYDVQQGEwJCUjEcMBoGA1UEChMTT3BlbiBGaW5hbmNl\nIEJyYXNpbDEdMBsGA1UECxMUT3BlbiBGaW5hbmNlIHNhbmRib3gxLTArBgNVBAMT\nJE9wZW4gRmluYW5jZSBzYW5kYm94IElzc3VpbmcgQ0EgLSBHMjCCASIwDQYJKoZI\nhvcNAQEBBQADggEPADCCAQoCggEBAJJZYsafIn0x1j8WLDfJ3HSXt65NqnKwGdcW\nn4z4VqdrvcIl6kJM7cjF3ImaN5SLideuK63/QP4tgGilZxooxLE8V8M/uPgGU74K\noTMBuDho6sND/UtHsr/wgkX9+/Kn50vdLbhXZBmvcL+5gtXKDQGR+d1LyaU8EigX\nkhvegMCSyW72PlQ9FetapanOpH0e5+osGRVI9ysm7PFrWE6UOs8EA/d6+v8SwHTW\nbD6iVVgtGnQtm0C4w4H6VVNnFE0F8pSnXQQPzQXMONIFi/UZPSB00H0qnxRvWkw3\nJa7QErS8hdMPGUHQ9N/RujhMhf7tlUArcgod6mc+SYfcI3j1pUcCAwEAAaOCApUw\nggKRMA4GA1UdDwEB/wQEAwIBBjASBgNVHRMBAf8ECDAGAQH/AgEAMB0GA1UdDgQW\nBBR67wuI2HqJ4b0vBD0esdbER0IoPTAfBgNVHSMEGDAWgBQVb9vsej3AhKXXgbWR\nvfmoWNM++jBZBggrBgEFBQcBAQRNMEswSQYIKwYBBQUHMAGGPWh0dHA6Ly9vY3Nw\nLnBraS1nMi5zYW5kYm94LmRpcmVjdG9yeS5vcGVuYmFua2luZ2JyYXNpbC5vcmcu\nYnIwWAYDVR0fBFEwTzBNoEugSYZHaHR0cDovL2NybC5wa2ktZzIuc2FuZGJveC5k\naXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL2lzc3Vlci5jcmwwggF0\nBgNVHSAEggFrMIIBZzCCAWMGCysGAQQBg7ovcAECMIIBUjCB9QYIKwYBBQUHAgIw\ngegMgeVUaGlzIENlcnRpZmljYXRlIGlzIHNvbGVseSBmb3IgdXNlIHdpdGggT3Bl\nbiBGaW5hbmNlIEJyYXNpbCBzYW5kYm94IEFQSXMgU2VydmljZXMuIEl0cyByZWNl\naXB0LCBwb3NzZXNzaW9uIG9yIHVzZSBjb25zdGl0dXRlcyBhY2NlcHRhbmNlIG9m\nIHRoZSBPcGVuIEZpbmFuY2UgQnJhc2lsIHNhbmRib3ggb2YgQVBJcyBDZXJ0aWZp\nY2F0ZSBQb2xpY3kgYW5kIHJlbGF0ZWQgZG9jdW1lbnRzIHRoZXJlaW4uMFgGCCsG\nAQUFBwIBFkxodHRwOi8vcmVwb3NpdG9yeS5wa2ktZzIuc2FuZGJveC5kaXJlY3Rv\ncnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL3BvbGljaWVzMA0GCSqGSIb3DQEB\nDQUAA4ICAQCANeSAlmJy3e9rrgTGShVCyMQhy68j3cAJyFzqCutyNMGHUgFOjAgD\nzIUQZmAepTDJdhJF+BoruBfAIJUr6tD9EBw2MZXiTLHZG9mqtGwsMbeI3o3R9Y3G\nEpGp72jIHw7mtUZdoaWcmgqxCWn6UT9bBKAkdt6KyRepPUy1YI59MZxpVOs5J0s2\nQFd3FRCNxdzgsuGqdxTb1Gre4I5E1vJWcp1Fe/kPdaOgPVC89M6uk3WYTnMNZ20N\n8K0ecXy8+E3K+to35berWn16g1ZrufylX6s2yyxcsUnh5KP1smFd8MePekKIW0SD\n8hqD1MtGQEmzdWrPCT9fZUzONj4VuDcl/vgfKUBsBszTmqwGF34G+663v10KUhga\nkCiIOZtkT9B+aESGAfczQiFO1h4cI52TKwEptfbplrFS2gILrzleqv0JoDDFYVhY\nV5AVDjqeHaniClCi10JdSN11LqNdagpyojN2a2WhVSAigIT3yDeqozlzjgPui/1E\nDt0zBkXd5uFDwNeLUwOribuS3hxVG5Bg73ZJl+UV3ZuAzFFCfkVBz6BeqUusf8+P\n3pqAQ4gzhSWNsTBIsjaVV8ZU8IqxKhBkRUSNjihG2kM8kX9knQvRbCBuuse/dDUe\n4cUJ+wT1omVgq+TWhShOAjsHEa233omXbH7v5igLBEkzzqmM5cAv8Q==\n-----END CERTIFICATE-----\n-----BEGIN CERTIFICATE-----\nMIIFvDCCA6SgAwIBAgIUKhBUxL5Dt4w3xH1V3X1n+x/e3hcwDQYJKoZIhvcNAQEN\nBQAwdjELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MSowKAYDVQQDEyFPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBSb290IENBIC0gRzIwHhcNMjMwMzA5MTQzNjAwWhcNMzgw\nMzA1MTQzNjAwWjB2MQswCQYDVQQGEwJCUjEcMBoGA1UEChMTT3BlbiBGaW5hbmNl\nIEJyYXNpbDEdMBsGA1UECxMUT3BlbiBGaW5hbmNlIHNhbmRib3gxKjAoBgNVBAMT\nIU9wZW4gRmluYW5jZSBzYW5kYm94IFJvb3QgQ0EgLSBHMjCCAiIwDQYJKoZIhvcN\nAQEBBQADggIPADCCAgoCggIBALJFBgmKj3iDF3C8+8smNNQDxLFA9kCcca1iaxQf\nvMI/FKGW2ullHhH+W3EGEajn39QOlccGyrfCONHLqMW53+HAMtwiIvcrJgj72V7D\nnYflO3aaCFwoC31PL1+pMBo88F6jvezZ8BlRnheT7urCs6+onhz8pm0cVNc77U5X\npi8IOJz1QFKecJnFLjG0NiLCzOzjLSo0A8Rue9K/H5fjq+PqKdXG94AoQyFUwlsU\ny4aXbylDz1kRiOSnOlRNPcY/su95pFKQbGgaZZ1fLf89i5PtHAUu92FbD7H7OyYX\nXpZ97La0d7cUH0A4nb+LpOd/f0c8lAN2Ya1B8aKvWiF23q3c8EoAJyhrdkHKe6yI\nYvLC5G5jkbJefeQcp34IgD8T+Tn3aBF7YgmlYUMbnsuokBG28Hr50EAklCclA0bb\n4pmf8nE6y7VQ0CM/bNZd1F9AjxLukkyvkrOD6A6uv+c5KeC+da245dBzsyhiKe9R\nRX5Gkf7NSkDu9b9YkdDaWV6LXxpUA0SmdT9M16yK3XPDKOWBI4gVSB1KuwrOcal/\ndMwFUlxvqdGugRbxDNNukxa0l3JztGg6XYLjEiiYrQ+7HChbUVNlM0l0VZAz4eON\ngYrq2ExUDWlQXiES389/Qz3R3yDk9ib1YsMHwAux2ulCssFVn4EgtnYFfgf3o01J\n3CedAgMBAAGjQjBAMA4GA1UdDwEB/wQEAwIBBjAPBgNVHRMBAf8EBTADAQH/MB0G\nA1UdDgQWBBQVb9vsej3AhKXXgbWRvfmoWNM++jANBgkqhkiG9w0BAQ0FAAOCAgEA\nVPrUd4UDjOhkxOzSN4bMr0cULZJwQPRV8aj99tzdv8Ef44CwLVkLmm7Z2d1uRA9l\n7xbK6W8L1oL95iV4K4o2u4+ZFG7mrOfU2T2wgTfMlIxHDoAxS49flUYkBpQI1Wj4\nJBZ6fKGFVH6PyIio0I2Mx2u80ZX6lPYQ2q4DR6eBUoNt8T8XSWpD4TjroFbOVIp+\nN84alBca/pvW2aF2HwPndrL/Y++HZp3TpdUeBUT757KOZ7hdwf30pxd8qNn8+peb\nbP2h6b9pjKAmS8ciBExJzchhQWJRP6LIdvexTsBQ1HLxlZNrlg66wYT0kuVVzRTa\n0qRvIjQ0ntmhy2DtmE5VFT9O8ahcQL5Ddk8B4dhiy59vjALS6kIUXJ6GCobzRUsQ\na7b7J7nu+PTY+qVo0LsTMO1rVTUXD63gVk8QmPUwnvduk9nxraNpVP+m17BuEcls\nEsoGAAQYcmzOlnZpqhhbTnbsEayW1bMyxkLjBjXpOfBgrvyv5fU/09lP6VB20FJr\nzVPZWr5PTzaaizDDecSKgZ1ANIwXIIwWirwzDqqQb922JtcH+Ca6JJWgrV7+kDCU\ncVzwKVYievjXMCsmRSzDKEgp4n1AgrxcoaH0smD+qA+wzfsMqvEA1iTNW7zdnF0o\n6UJ9rkWxKr+JRZ5jFO+kpKQ1DxfDJZE554aO8AXzYEI=\n-----END CERTIFICATE-----\n"
    },
    "browser": [
        {
            "match": "https://auth.mockbank.openbankingbrasil.org.br/auth*",
            "tasks": [
                {
                    "task": "Login",
                    "optional": true,
                    "match": "https://auth.mockbank.openbankingbrasil.org.br/interaction*",
                    "commands": [
                        [
                            "text",
                            "name",
                            "login",
                            "ralph.bragg@gmail.com",
                            "optional"
                        ],
                        [
                            "text",
                            "name",
                            "password",
                            "P@ssword01",
                            "optional"
                        ],
                        [
                            "click",
                            "xpath",
                            "//button[contains(text(),\"Sign in\")]",
                            "optional"
                        ]
                    ]
                },
                {
                    "task": "Consent",
                    "optional": true,
                    "match": "https://auth.mockbank.openbankingbrasil.org.br/interaction*",
                    "commands": [
                        [
                            "wait",
                            "xpath",
                            "//*",
                            60,
                            ".*Before proceeding, we need to confirm some information:*",
                            "update-image-placeholder-optional"
                        ],
                        [
                            "click",
                            "xpath",
                            "//input[@id='consent-toggle']/following-sibling::div[1]"
                        ],
                        [
                            "click",
                            "id",
                            "continue-button"
                        ]
                    ]
                },
                {
                    "task": "Verify Complete",
                    "match": "*/test/*/callback*",
                    "commands": [
                        [
                            "wait",
                            "id",
                            "submission_complete",
                            10
                        ]
                    ]
                }
            ]
        }
    ]
}
```

</details>

<details>
<summary>JSON Configuration for Automatic Pix/Sweeping Payments v2 (Auto Redirect)</summary>

```
{
    "alias": "obbsb",
    "server": {
        "discoveryUrl": "https://auth.mockbank.openbankingbrasil.org.br/.well-known/openid-configuration"
    },
    "directory": {
        "keystore": "https://keystore.sandbox.directory.openbankingbrasil.org.br/",
        "discoveryUrl": "https://auth.directory.openbankingbrasil.org.br/.well-known/openid-configuration",
        "apibase": "https://matls-api.directory.openbankingbrasil.org.br/",
        "client_id": "984e85a9-9001-40eb-97b3-194f5afbd956"
    },
    "resource": {
        "brazilPaymentConsent": {
            "data": {
                "loggedUser": {
                    "document": {
                        "identification": "76109277673",
                        "rel": "CPF"
                    }
                },
                "creditor": {
                    "personType": "PESSOA_NATURAL",
                    "cpfCnpj": "76109277673",
                    "name": "Ralph Bragg"
                },
                "payment": {
                    "type": "PIX",
                    "date": "2021-01-01",
                    "currency": "BRL",
                    "amount": "1333.00",
                    "details": {
                        "localInstrument": "DICT",
                        "proxy": "12345678901",
                        "creditorAccount": {
                            "ispb": "12345678",
                            "issuer": "1774",
                            "number": "11188222",
                            "accountType": "SVGS"
                        }
                    }
                },
                "debtorAccount": {
                    "ispb": "12345678",
                    "issuer": "6272",
                    "number": "94088392",
                    "accountType": "CACC"
                }
            }
        },
        "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
        "brazilQrdnCnpj": "43142666000197",
        "loggedUserIdentification": "76109277673",
        "debtorAccountIspb": "12345678",
        "debtorAccountIssuer": "1774",
        "debtorAccountNumber": "94088392",
        "debtorAccountType": "CACC",
        "paymentAmount": "1333.00",
        "creditorName": "Ralph Bragg",
        "creditorAccountIspb": "99999004",
        "creditorAccountIssuer": "0001",
        "creditorAccountNumber": "11188222",
        "creditorAccountAccountType": "SVGS",
        "creditorCpfCnpj": "50685362006773",
        "contractDebtorName": "Example",
        "contractDebtorIdentification": "76109277673"
    },
    "consent": {
        "productType": "personal"
    },
    "conditionalResources": {},
    "client": {
        "jwks": {
            "keys": [
                {
                    "alg": "PS256",
                    "d": "Q9gSOfnkGJnAsV3a94j9ae9ihjqgMwXgVm73VTyEs1u9Jq73pCWX0e9JdeNMKdgKpiJYjyxa3ttxCY58eiGKEi7c50zYRx8YLTL2rIVWqS6JVGpXuzIQutkQDM4AfD72bG3-xT-caSCansGbdEIFJjX32Ujbs1UUoQlE96m3hNOjB5vNyHBWrBUgUGG9_uJiWFG6Lbj8ZGtiihA_PQkzuArLzDvO2OMVHCzIyQ4CwFE1tI9xHFHpioJQXBnymURQvkm3MmEwHRG_KUdABQ55gG32jothy7jOOYAMkvOCejteTZv1nT4dsEj-CBxDBtTI6SerXb11VX8b0suzSBxx0Q",
                    "dp": "S15AOPpOtYgYjfOi2rNojY3NpU-Qobnfnnt_MZEJ2_DS0bGwXSgGJjHOOOAowy1HK0n7-AhXbwhr026sBuicR_Kpj6RkzGVrJug8y9R02FXZwlQpgjSBZdO6C2B1OOvtyKmnKg5q1KdQ7Kx6vYPV7UutOJn6NlH0RbFgG4NGelk",
                    "dq": "oBgBMB54mtrriQCg4YyDY_zf7LW4f6oqiUl3l7odf_ArjVamjHM-boZnhGoVzZ5uXNs03wEdBIc2HLmsoGLVuodcYHjyptmvyPebiH2mavFlUlI8ILG6lkyIhMp3Ri8iXGX2MYlPjP2EawNDMHB6BO0bZ5NugyzxuF_OKhfEFLc",
                    "e": "AQAB",
                    "kid": "-duNE0ZX5NmDkUlgNoqDY5Ve7UdFTA7S25WJSAv8tNQ",
                    "kty": "RSA",
                    "n": "-6Ep5kV0qcQnrxQzbEgMGKQRHnhXlp3ZpAVqQbbzkVG_a1tHLi0V7YAmjf3isXMvdvWjApeShL32gqxgcKDvC5Mnd5ufR1ujzb5lsnYXy-tKMQWnAlCqy7mSuxi8JIBXyZb7CMGU29L32Tvd5MjDh_hSgwnHcTggE-ehqzK5eyvK7DjvlbfCKXgDx94kMcwyI2K0EurahHj9_I3lEQzAt73OocF_z84FQxO87A8Q1cM3nEGyykZPaFyulQ4bf4U2tT_Jfd0ppYX1j194ouPeqMZBsGnxKf4L4QvuberbRpdeOO92HhWHHiwiTuhYxF876-LKgPzqxK-Y1a2_4gsVAw",
                    "p": "_oebNFofSe_8fdotMxUEk7n3pq5eT96rO_VPdHyTZERDrkU0djQf9BLy7DejYoRReuI0AJWkBL9EGBhECaowmx8gTCs43ffQrBDULYB4elmS07ov1pq1STqzqRKbu_INaSGVgxFzhYC_EeFVpB0RPlAUvb1_aQkH79J8VMnp2_U",
                    "q": "_RVEyO9NB6XiJjMz9t6XrNxG01Vguo2VVBLaDJhoi1g7gydUDkNc9twhF1Ifps8Gf3m9aMjjOmYqE5kuWCPBHxkk8cZOm4C2AhVbQxMkZLOyPeJDfKfCi7yJRIfmwqQM5AKosALfN-jW_p746lRhCAps8eH9XF6bjugi_MH1yhc",
                    "qi": "yXG_vCx0xL9DlU7f0Ixub9NSD1QJtAJYxwKyHukw_8f4rHLiZ8eeCerfZfPd7zsPGSqOmY2605MNT1Z2ohYgoRyu05uwstEDKqtgl_uxupfO6AJKCja4paIB-ICvQQXpOY1n9BW6VcDwSylTnv1pKvVnTvxzy5z008wvrafQtFw",
                    "use": "sig"
                },
                {
                    "kty": "RSA",
                    "alg": "PS256",
                    "use": "enc",
                    "kid": "e96744c58188c084310920b152ffb02a392b119a009fb1fa1a656006715e1604",
                    "n": "4eIXvOR1XXo3MT9syMwRZj2ChbV2Qlp_623VCIhYvPtJ5k5rlCr1hP4n0PC49U47pa3UKNs6DYHefHKm9I4h4crgk7zsln2_JP3kK1equqIO1U12Rv4Xbm_2_eqR3hPKcE3il2ky2Neby8OThFnyDwBNKdxI4MvOKm910qQhYns2L4w_i9fjF2z1Wpi6sMPW8IERhkqaBWgoaH9g2obGbNuoYCzEjOWvRb_nVjYKRPqTI2A11kWZ4mVTRkTO4yM1gdI7z8Hsl4fqlEXeVdmMkVJhRvQa-vFfegecgO8nUY2XoOUx_UR51F8PO9bepy-jH16cRDwjLE-2ex7mE_wfMw",
                    "e": "AQAB",
                    "d": "BqovoVF4vww8nA9IuLhnHDlDZFbHov4qZeCecQgcEJNpIxdiqDZuR4EvECsSIgOWOFvwW-lzOI1oHaVNlMvezXU5eoWpnpuEnzHlYHwCzxftNrde5PBZWHC-sAMStvBzJpLw7riNZgWFx_wNmoTQfHqgGQfLyxcB9Pf6v387qiN1wHfSXQshtFiDg_6tBaH6dS1jRAg7_56dQp1wWJeRaqMCg9QeESmo3c-76hnRSMU6fgrONU6qGMSLopv-nirh3H1gZePcXzVgf9cerRMQgV1pWUZEd_iJqTaX8U7wB0txmVF6QzRxR71Ah6nZuV_Rv7X88zB8u0rXOvjeGtuZKQ",
                    "p": "8fN0GXyZnvxba4yoOgdL9ta9pkjjWVu5eTOIyvSgKf09hUSWKL6sKm1N0l68detwzBFpnxObOeUCMnU_BFhJM-s0w5GognaAX6GB5-TzdYHwmsgqAch3-_hi_kZU6A-SLZu7bQFGXTEotQ1zMxVuCMZ7AjTs0CGZrS-vItFYtik",
                    "q": "7v_Ldwh3L9On2CNAefLgs7dyDBAgWrkXOJ9Z1EnrKgMHbqgq5dOixv2ezKNdOUte9G4ve555XTf2sC-p0TF9PNYC0_4KthI8NLik8RtDsQmYJUYw7qfV_YitzGflM2DRr6KaV5SmO_aPWRfzuVWh_6kIQ_GmXf47ASasKVeD_fs",
                    "dp": "Jyi-_q0C9A9mAHcodxPdQJsq4LHlUf4de7dSiX6kOYeKIHqkTv3lQYylTsoUeIVdoTmkPaHfurQM8fu18k8Tsfp8dLarbkodptyt-Mk-eiNIvNRusBExEi_2Xa8maNS0VPtij1boe4bMTtlZbsgmIfd1yzqjpV_6zmPsVZdKY1k",
                    "dq": "qjW-YA3FZGhmtwWUG8Wfxh41uOWbRUFgilDils_2DTuPBX363yc0XGevuqn18KH_BDGc23tnj74VkDDBzlxihvsblILuefDOs_V0csoqEWF128X7f1xEiIXY0SSFFWw0qdMx_IG_SiE0wgzO5QVZlEx7uHfXNkWjHBTAs8jCFhU",
                    "qi": "8W2vDdiA8qDxL2fiJPP2m3NqbjGW7Tf5PsfGo0Gqfv6nWVweuVwsyUNT1AYduZUCvFRG5LRNHqiwZNpNB6XQln1W41GaIqGkHWJkveHhg9xIQmSK2hrX4OnSdyvMiGiB2yvce0FTgQ0OzXuNkIKJKJLP2nAJusNgNcVT7qgKCRA"
                }
            ]
        },
        "org_jwks": {
            "keys": [
                {
                    "d": "BpgLagicLjysglxtDX7bJnOv4-IP-5yyGdL4oOkDCl_-lO8twPDhWLfXNCf2QTs7l1T1GLNUyALKjYDNEvjbpu03_K1dtRwO2ZS4_VHTPhe99Etn1GXntdfcFvQiD9Lz6uzs2-0DOIG_5xWUiVhTUN5HPRfMMXF3ktG2ucTOQqsJU0O2SOohVIvqYH4EDJNIw8qUsu1C2JEDMj79H_8KaXEUVx8tFFLMxmt67a_a7sImXvEaIYhUCu-DMMDrzBc660s_eTcihJ_DkJgYPPWctnmpUClKa4zgABDqGXhPQFfLS4ywGAHnLZF1MyNeKFXpmeJShjNJ5MqjBKJTnFHDQKs",
                    "dp": "CFfrENWCU61YHATfdTy73lt2reMz0dBDicy92s4FqHpcup6O6f5MWGvhpBlLVC-tNA97qzyKExFwxl6c6rf45l8T6GLjy4C2DJEH0pGKeh7-PP7XW1KBvsclbJdSoSj-bOFRomFVGKYhIF3nRnr9-Dvj1k8aEcClPT1E9i9rGI7P",
                    "dq": "BzCeCJQ9pKQVCpyFi50PR8_E7d9uW9nYqJpf0GBT5XdnZ44qnliLAffZmVwcxXh6e_JzIjC0ByJrYKd_dekXLCrsOex1XxqvI7WH6EZ3Nvoe_1835ZgtQ2PsPSvGKifHHPXocKyqqRdT7KlGTXfnpKtezsXPxe63VS-3coE62-_F",
                    "e": "AQAB",
                    "kid": "EKSYJfNcI8Bm22_dP0ziWpTjw9UceAdVjykgwO5BkfE",
                    "kty": "RSA",
                    "n": "oBp-b0EhezRYfisJBL_WA2Yh0Y2zPYHsy8N4G9mddkop-kFJT12XSSBx8GXmyjDL14Wg5vRNA6R_TwXbJbnHnE59uMYiWNi_G7OL6jMsncmYdyBuwl-lDWExaXC5Qg9vYgGnt7d1SthQoiJkduPIiNpniq5p7px-jJYQO4SECUqpeLl9rU_Xvxn5zpFu4dw65wBi4oSDiJ0zujQtxofOmbJCKYTWrPmd8yPlPgwIttP2ZcprMs5Ya57-99NhAealcVptRTOQTEWEOflmurq58Byu7pT64ns-9Su8JPcHMMzxOOVM7KNPuZA7Xa5-1aBd1XrhxkBHIDzUqOpanSlr2uk",
                    "p": "DgL5bOQ5-JXM6Ed_3BRKW2a3EcHB_UjlWPlGGkc0RBeEwlNi6D3PQGZmgTxyGXWA4W3HMi2S2pXx8oxWd9rrw9Uc_BNrIdvkMcU9LnkCvxK-dcHalVrXhv0l1EbQx0mG9LjLsiqmJiJYnUYTuLjO8lJaebSTp-EH2fgTs81_SBKv",
                    "q": "C20t29WtF9yAXt2r5Yu7chtrJUMIsu_TUY2N6p75BWWBB76oNib4Dp5fVePnbTqdSP913dS1K1vHwEAqS_Z_C6vfmaYha6Hguipo5jotTTJoYDxV_xTp1dGWcr8MltBE9ikhLa8xvGVxXjSi4vkqc_TyXlBSHbbBSZtjB32rCLHn",
                    "qi": "BRx-2fqZYWrIzcayN1v10HfzcQaZue-NNZP7Eid81oBBxBrDQmiGdzQLi0BKctjLBr21_GWUgHgEYRym3He5biuDVM0WnyhXYeLLc_pv3bIG6FoPrP4XDZo4GTM4JdVj2im_OQWdXuokFzsZzeVV6H8p46TxpyNDix5oFjmyuB11",
                    "alg": "PS256",
                    "use": "sig"
                },
                {
                    "p": "2a8fRJ7ybF-qtF1zrYzSm7z3C4wNTUMbVYqe44tR9FbKsobqW2tS0iAZf-GJ_SZPcWxkE76gunW7YqMJecGUtXsJ8TTHwjcPQOMYzxnyJu8Q4JOj01YJVrxUY9D0ZzpWM9oTAj1-qoE0w7Dy-XNUc14-HeRlmOkg2tTfrXTVR8c",
                    "kty": "RSA",
                    "q": "0xlPJFRUcBU5j2SKSajVnd4H5p88RSsd4cArMby1ZRuSeHEsX76c6QKAPq7uTfKrTeZic34yzAEUyHloP1fZQYQ2UQn-f6PsTAWdT1Lp5oi2VZCT0yc9-1EGnLAiUCbM9SQQyf2GIVhCiAk_0VuY6le61Pw0U4GssvFJzIrx4as",
                    "d": "GxnizpWcqL1wajD8-Y-8H9-II4UZMKfkgbfwRiLK9uAd8-kEJdO9jdNeMxyytg2saDhxNTeRTkYz_VbBf3p9dGhuYx84d-ZagUbIiU3ho3FCsBRrzQQZw9OQrzPDUzp0-SBn1_GLCf9fo4ysxWHbn9euJVi2fpN_bHlBi1n8fKhdBHYE7X3XJnRYrUXItxZw5sJsqM_boONLxdLAvgmZx5CHft94JZsR6JPwlj9Ba_CuNWX_3OuUGyV0f5_1ICAEYijw9PA8KAW6t5UUYn39_KYL8nF5L1Bh6W1j8eN84I2lcKZNO6Pou064ag_wqGhk4uXuQO1IV8jRFn3-pqhSEQ",
                    "e": "AQAB",
                    "use": "enc",
                    "kid": "c1d7b80ce4b88c4f2cfb68e7a8c45bfff355ae94259bc1a73a95ddbaeaf7c96b",
                    "qi": "pU1IXwiQoFERdzJsx7kSC79Gwhak7uw7OAJCbcfkKE3GSwTWHrKfg5uDZlNvSnNU1Hbpxd0bgc40dFI2aNBML1gyDwTjQplWVJikkFix8E6z_ErSa_D5w5yV4k6CNtt7OzlMXawiZ-ndcuiOs5MkfSRyeB3k5rQmuZjLVzFFlnw",
                    "dp": "Gn4dqBRQHLBn7huRgIWq_Bk7V8RrugN4yChevgKurrYBZUjWLNoa8kfF0rJ4QL7w3DT82QpSNV8utwpwlMjieFPJGfn6dcCNsq_wzQOzXNmrjClrvsSxzkSNYLiFhiqrYxQfTB5_0_B1o3tdls5acM__b1PkqX916CwQLOQTMPE",
                    "alg": "PS256",
                    "dq": "NS0x94fawWVHW6zK_SUvspXkzZ6dMxtaaqza9KuB0ldwvTBdKj09D6FWpvOwCiiwKG55rHhE2YkIMDwNG6_Iha2FdUKcPpEPjFL5vqq3SyBzNfi2lEFVZsKRdNUVv7UWekY8iHV53Vp7YANcdSOq0JWK9e4WTFblJyqLGaCCsAM",
                    "n": "s4DcK4uxKroJPE1R7Te4ppNexbuK3C-Z3MpXFr5hmY43gYIoVMo89jE6OcDiO0Z4rxe8dsH4oYA2vAJQ0IhAaUxYMk2kN01ei761zMQWHLUPLcEKWgipYHy4AgwAUaF7-Glyb0DT1RRcY4f1tEddftxhwXZjeFduj6luVg6fVvXRIRjttybUkIKvf5ShMofVFCF_IyjYlOal4g3DVnCg62dR71WX3fRXSufxrRBG-L61rv2VSMg8pIb1DFiYKDlEXEnTdLk-7goBpTIz3wBsrZgJESSZOn_BG_-fCE0V75rheLMuJd4IGE4H0taVfEQOJKRKBVzc2jAz0sOaVuPY7Q"
                }
            ]
        },
        "client_id": "Jj-hosRwYqvtnQZNph2Ah"
    },
    "mtls": {
        "cert": "-----BEGIN CERTIFICATE-----\nMIIHQDCCBiigAwIBAgIUOyyDtirdgYQIT/eSBtvaP5JRcoswDQYJKoZIhvcNAQEL\nBQAweTELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MS0wKwYDVQQDEyRPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBJc3N1aW5nIENBIC0gRzIwHhcNMjUxMTA1MjAzMjAwWhcN\nMjYxMjA1MjAzMjAwWjCCAUoxCzAJBgNVBAYTAkJSMQswCQYDVQQIEwJVSzEPMA0G\nA1UEBxMGTE9ORE9OMSYwJAYDVQQKEx1PcGVuIEJhbmtpbmcgQnJhc2lsIC0gUmFp\nZGlhbTEtMCsGA1UECxMkYjk2MWM0ZWItNTA5ZC00ZWRmLWFmZWItMzU2NDJiMzgx\nODVkMUMwQQYDVQQDEzpodHRwczovL3dlYi5jb25mb3JtYW5jZS5kaXJlY3Rvcnku\nb3BlbmJhbmtpbmdicmFzaWwub3JnLmJyMRcwFQYDVQQFEw4wMDAwMDAxMDc0Mjg1\nMTEdMBsGA1UEDxMUUHJpdmF0ZSBPcmdhbml6YXRpb24xEzARBgsrBgEEAYI3PAIB\nAxMCVUsxNDAyBgoJkiaJk/IsZAEBEyQ5ODRlODVhOS05MDAxLTQwZWItOTdiMy0x\nOTRmNWFmYmQ5NTYwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQC8bzfe\nH4l2IegWdHsOIooz+nUxpfI5v23ubPsB0P9rLEoPlIn0A7E2zg/b7UCQFvzmzgao\n49DYEbaR5B5rutlRn52rkHufNF2fNEGXgtqrko/Uwf2tGDpve+e6MRuXhyYUEwaq\nMIRL9RCqDSTHFUS+QoNaPdccw9yAQkffEckKoXJA5GYkLvkZ06Vh8R7L6Agjh1VN\ntbT3v+STfrIbSYcEXJoHwWn7vnSewcJm3B1yxpKAVySFbL336yu0cYU8RkZ42SBh\nJmGD96kmJ+vuTXQBs5ZTndbZo6/UO+r3+qaQ8rK1r4qeEYaOwSYh9wsFxpLJIgyC\nwnl0XQQnwjQKKConAgMBAAGjggLrMIIC5zAMBgNVHRMBAf8EAjAAMB0GA1UdDgQW\nBBTLmBupVqnHkdd6f2hhj5mRrTUZnzAfBgNVHSMEGDAWgBR67wuI2HqJ4b0vBD0e\nsdbER0IoPTBZBggrBgEFBQcBAQRNMEswSQYIKwYBBQUHMAGGPWh0dHA6Ly9vY3Nw\nLnBraS1nMi5zYW5kYm94LmRpcmVjdG9yeS5vcGVuYmFua2luZ2JyYXNpbC5vcmcu\nYnIwWAYDVR0fBFEwTzBNoEugSYZHaHR0cDovL2NybC5wa2ktZzIuc2FuZGJveC5k\naXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL2lzc3Vlci5jcmwwRQYD\nVR0RBD4wPII6aHR0cHM6Ly93ZWIuY29uZm9ybWFuY2UuZGlyZWN0b3J5Lm9wZW5i\nYW5raW5nYnJhc2lsLm9yZy5icjAOBgNVHQ8BAf8EBAMCBaAwEwYDVR0lBAwwCgYI\nKwYBBQUHAwIwggF0BgNVHSAEggFrMIIBZzCCAWMGCysGAQQBg7ovcAECMIIBUjCB\n9QYIKwYBBQUHAgIwgegMgeVUaGlzIENlcnRpZmljYXRlIGlzIHNvbGVseSBmb3Ig\ndXNlIHdpdGggT3BlbiBGaW5hbmNlIEJyYXNpbCBzYW5kYm94IEFQSXMgU2Vydmlj\nZXMuIEl0cyByZWNlaXB0LCBwb3NzZXNzaW9uIG9yIHVzZSBjb25zdGl0dXRlcyBh\nY2NlcHRhbmNlIG9mIHRoZSBPcGVuIEZpbmFuY2UgQnJhc2lsIHNhbmRib3ggb2Yg\nQVBJcyBDZXJ0aWZpY2F0ZSBQb2xpY3kgYW5kIHJlbGF0ZWQgZG9jdW1lbnRzIHRo\nZXJlaW4uMFgGCCsGAQUFBwIBFkxodHRwOi8vcmVwb3NpdG9yeS5wa2ktZzIuc2Fu\nZGJveC5kaXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL3BvbGljaWVz\nMA0GCSqGSIb3DQEBCwUAA4IBAQAjJQE5R9iYGgnrEpEOUGNFVqHYs8L8Y1quoglO\nYsz1GhC2bzm7WSo7iRXfil5D8om6BDM+2TsMkvH21yeNnIclIrK/ReDHqkubbWoa\n9awJDNVa6VoNRdCB6dqEiLwZl4p+bacoShQCd113v5B76gVyCPBmId41rDJv/beB\nv7F894KM4LMMkkZGSnrGft9fc8Y2CPN452EgnTh41PhJHK8DVw8mtx704gblJ64B\nwqhogdzyAjY1uz+a3M1gTTCkEEkuhYXYrHDXgz327JRCW2oXKj7oMMszMI5E4uYL\n/QQijgFOoCPdX+/SvXZo7uMl0dtegLOR/oHxOwLuryqBk9mG\n-----END CERTIFICATE-----",
        "key": "-----BEGIN PRIVATE KEY-----\nMIIEvQIBADANBgkqhkiG9w0BAQEFAASCBKcwggSjAgEAAoIBAQC8bzfeH4l2IegW\ndHsOIooz+nUxpfI5v23ubPsB0P9rLEoPlIn0A7E2zg/b7UCQFvzmzgao49DYEbaR\n5B5rutlRn52rkHufNF2fNEGXgtqrko/Uwf2tGDpve+e6MRuXhyYUEwaqMIRL9RCq\nDSTHFUS+QoNaPdccw9yAQkffEckKoXJA5GYkLvkZ06Vh8R7L6Agjh1VNtbT3v+ST\nfrIbSYcEXJoHwWn7vnSewcJm3B1yxpKAVySFbL336yu0cYU8RkZ42SBhJmGD96km\nJ+vuTXQBs5ZTndbZo6/UO+r3+qaQ8rK1r4qeEYaOwSYh9wsFxpLJIgyCwnl0XQQn\nwjQKKConAgMBAAECggEAJwYvf0hvuu/dtVzNKUm87nPVtoEED7KV7TVTrHYgl4z2\nD5D3GvpyxoNZZHYXk1+3Y4NSfMKle0H72e3w4OWy4QUZ7bB/8aIyK2jylpKqf7Lc\nJ7c/NoxYecMi4/wMl06Nc8XW8QMYOvTXTShor/Q3JuH2ewdol9P2Q/e2E7wGszUN\n9Of74KkoQ1bGf8Z3eutjqdP35/n6cETQDoFiqsV8DfHQGCiiNPKWGD2asQDhhRx4\nvh0TGIxvWF5lnSSxvbGsNFUoGWxr8eUH/EGcH1UnHfYL4xhUYqWTEOhM2v/csmzY\nt8o4BntudmXxlfgYU3NyPKkyx7/bVcnW1PJVtoDKkQKBgQDv7j0jjaWt6dJwsKa0\n5XQ4Xga1PbpDb3LWfzZr3IScUxbVytTnOWVXpok4esn4S00iQpAp7FV3YZ/qox7p\ngcOgV7lW6CIShnLgmr4CEt1hV/sRvqddmmgfrY4ZJLy24MSxwBeZiUPNRHKl9RZA\nJr2WsM04JPE4mmf9QOpGjjy71wKBgQDJDguPpQflCGT8s2KNQjBGnWGVfdNHd1vF\nOFP79wkROAEBb2mJsuBBl8Iu3YvImaKAyAln3uqOhQ8rr+y12DqBRgoAyHY3dr46\nlhQFDonNGVdOxrwRnxajKft32W8Tn6pdjuIs4N5q23Luqym5l9PA6h8aa3E+7yeE\ncvRIfqK6MQKBgG4OjED4wpzp+rvybCXictNAXjdY3037m2PE6sPDXZkPjBP5fHus\nGk6Ad8VOncKlV/Z1Lgfs/q9KOr64oH9gJMoyMzQoOyjgP2XD1ZDB8oaqguJ63+7R\n2x1c0Se7cE07AT6/7JNjIZTQ5v41VEWM/75Vz20HlRbvzO+gjVZb/IP1AoGANJwd\nQFhByZe5vTo/dpE0SrYR++kx6Qh9lgzYRR1uXPgXo0WBC0woTGGmqVbFphc1o5c0\nht6Y5/Q/dQIS4b6UCJHIOk46SOckffYZhP0559ZSt0VfnwjPBqEMsV7PJwZnsRWb\nb3zkFngYCgX15B+rhFZ/Dw3AU2SHJaxi6blhYXECgYEAnBAJuYoIfZolppeUZXwp\nAYoTLGMtXnjvX/YFumlEWzjnXLo4Lk9L+lO9sV5BwhQ6klNBARy5TjAedr+Kw0ee\noGh8F964pkF4jy7qBLMkf4/jaEvft/2tg16ELOj74llsd5GPA8Pgzeh1AXtlowwi\nC1Ere9RQ/zspggyX1uEakrI=\n-----END PRIVATE KEY-----\n",
        "ca": "-----BEGIN CERTIFICATE-----\nMIIHFDCCBPygAwIBAgIUZJOYHaqMZR7leKm8iaKrR380T8QwDQYJKoZIhvcNAQEN\nBQAwdjELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MSowKAYDVQQDEyFPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBSb290IENBIC0gRzIwHhcNMjMwMzA5MTQzNjAwWhcNMzMw\nMzA2MTQzNjAwWjB5MQswCQYDVQQGEwJCUjEcMBoGA1UEChMTT3BlbiBGaW5hbmNl\nIEJyYXNpbDEdMBsGA1UECxMUT3BlbiBGaW5hbmNlIHNhbmRib3gxLTArBgNVBAMT\nJE9wZW4gRmluYW5jZSBzYW5kYm94IElzc3VpbmcgQ0EgLSBHMjCCASIwDQYJKoZI\nhvcNAQEBBQADggEPADCCAQoCggEBAJJZYsafIn0x1j8WLDfJ3HSXt65NqnKwGdcW\nn4z4VqdrvcIl6kJM7cjF3ImaN5SLideuK63/QP4tgGilZxooxLE8V8M/uPgGU74K\noTMBuDho6sND/UtHsr/wgkX9+/Kn50vdLbhXZBmvcL+5gtXKDQGR+d1LyaU8EigX\nkhvegMCSyW72PlQ9FetapanOpH0e5+osGRVI9ysm7PFrWE6UOs8EA/d6+v8SwHTW\nbD6iVVgtGnQtm0C4w4H6VVNnFE0F8pSnXQQPzQXMONIFi/UZPSB00H0qnxRvWkw3\nJa7QErS8hdMPGUHQ9N/RujhMhf7tlUArcgod6mc+SYfcI3j1pUcCAwEAAaOCApUw\nggKRMA4GA1UdDwEB/wQEAwIBBjASBgNVHRMBAf8ECDAGAQH/AgEAMB0GA1UdDgQW\nBBR67wuI2HqJ4b0vBD0esdbER0IoPTAfBgNVHSMEGDAWgBQVb9vsej3AhKXXgbWR\nvfmoWNM++jBZBggrBgEFBQcBAQRNMEswSQYIKwYBBQUHMAGGPWh0dHA6Ly9vY3Nw\nLnBraS1nMi5zYW5kYm94LmRpcmVjdG9yeS5vcGVuYmFua2luZ2JyYXNpbC5vcmcu\nYnIwWAYDVR0fBFEwTzBNoEugSYZHaHR0cDovL2NybC5wa2ktZzIuc2FuZGJveC5k\naXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL2lzc3Vlci5jcmwwggF0\nBgNVHSAEggFrMIIBZzCCAWMGCysGAQQBg7ovcAECMIIBUjCB9QYIKwYBBQUHAgIw\ngegMgeVUaGlzIENlcnRpZmljYXRlIGlzIHNvbGVseSBmb3IgdXNlIHdpdGggT3Bl\nbiBGaW5hbmNlIEJyYXNpbCBzYW5kYm94IEFQSXMgU2VydmljZXMuIEl0cyByZWNl\naXB0LCBwb3NzZXNzaW9uIG9yIHVzZSBjb25zdGl0dXRlcyBhY2NlcHRhbmNlIG9m\nIHRoZSBPcGVuIEZpbmFuY2UgQnJhc2lsIHNhbmRib3ggb2YgQVBJcyBDZXJ0aWZp\nY2F0ZSBQb2xpY3kgYW5kIHJlbGF0ZWQgZG9jdW1lbnRzIHRoZXJlaW4uMFgGCCsG\nAQUFBwIBFkxodHRwOi8vcmVwb3NpdG9yeS5wa2ktZzIuc2FuZGJveC5kaXJlY3Rv\ncnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL3BvbGljaWVzMA0GCSqGSIb3DQEB\nDQUAA4ICAQCANeSAlmJy3e9rrgTGShVCyMQhy68j3cAJyFzqCutyNMGHUgFOjAgD\nzIUQZmAepTDJdhJF+BoruBfAIJUr6tD9EBw2MZXiTLHZG9mqtGwsMbeI3o3R9Y3G\nEpGp72jIHw7mtUZdoaWcmgqxCWn6UT9bBKAkdt6KyRepPUy1YI59MZxpVOs5J0s2\nQFd3FRCNxdzgsuGqdxTb1Gre4I5E1vJWcp1Fe/kPdaOgPVC89M6uk3WYTnMNZ20N\n8K0ecXy8+E3K+to35berWn16g1ZrufylX6s2yyxcsUnh5KP1smFd8MePekKIW0SD\n8hqD1MtGQEmzdWrPCT9fZUzONj4VuDcl/vgfKUBsBszTmqwGF34G+663v10KUhga\nkCiIOZtkT9B+aESGAfczQiFO1h4cI52TKwEptfbplrFS2gILrzleqv0JoDDFYVhY\nV5AVDjqeHaniClCi10JdSN11LqNdagpyojN2a2WhVSAigIT3yDeqozlzjgPui/1E\nDt0zBkXd5uFDwNeLUwOribuS3hxVG5Bg73ZJl+UV3ZuAzFFCfkVBz6BeqUusf8+P\n3pqAQ4gzhSWNsTBIsjaVV8ZU8IqxKhBkRUSNjihG2kM8kX9knQvRbCBuuse/dDUe\n4cUJ+wT1omVgq+TWhShOAjsHEa233omXbH7v5igLBEkzzqmM5cAv8Q==\n-----END CERTIFICATE-----\n-----BEGIN CERTIFICATE-----\nMIIFvDCCA6SgAwIBAgIUKhBUxL5Dt4w3xH1V3X1n+x/e3hcwDQYJKoZIhvcNAQEN\nBQAwdjELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MSowKAYDVQQDEyFPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBSb290IENBIC0gRzIwHhcNMjMwMzA5MTQzNjAwWhcNMzgw\nMzA1MTQzNjAwWjB2MQswCQYDVQQGEwJCUjEcMBoGA1UEChMTT3BlbiBGaW5hbmNl\nIEJyYXNpbDEdMBsGA1UECxMUT3BlbiBGaW5hbmNlIHNhbmRib3gxKjAoBgNVBAMT\nIU9wZW4gRmluYW5jZSBzYW5kYm94IFJvb3QgQ0EgLSBHMjCCAiIwDQYJKoZIhvcN\nAQEBBQADggIPADCCAgoCggIBALJFBgmKj3iDF3C8+8smNNQDxLFA9kCcca1iaxQf\nvMI/FKGW2ullHhH+W3EGEajn39QOlccGyrfCONHLqMW53+HAMtwiIvcrJgj72V7D\nnYflO3aaCFwoC31PL1+pMBo88F6jvezZ8BlRnheT7urCs6+onhz8pm0cVNc77U5X\npi8IOJz1QFKecJnFLjG0NiLCzOzjLSo0A8Rue9K/H5fjq+PqKdXG94AoQyFUwlsU\ny4aXbylDz1kRiOSnOlRNPcY/su95pFKQbGgaZZ1fLf89i5PtHAUu92FbD7H7OyYX\nXpZ97La0d7cUH0A4nb+LpOd/f0c8lAN2Ya1B8aKvWiF23q3c8EoAJyhrdkHKe6yI\nYvLC5G5jkbJefeQcp34IgD8T+Tn3aBF7YgmlYUMbnsuokBG28Hr50EAklCclA0bb\n4pmf8nE6y7VQ0CM/bNZd1F9AjxLukkyvkrOD6A6uv+c5KeC+da245dBzsyhiKe9R\nRX5Gkf7NSkDu9b9YkdDaWV6LXxpUA0SmdT9M16yK3XPDKOWBI4gVSB1KuwrOcal/\ndMwFUlxvqdGugRbxDNNukxa0l3JztGg6XYLjEiiYrQ+7HChbUVNlM0l0VZAz4eON\ngYrq2ExUDWlQXiES389/Qz3R3yDk9ib1YsMHwAux2ulCssFVn4EgtnYFfgf3o01J\n3CedAgMBAAGjQjBAMA4GA1UdDwEB/wQEAwIBBjAPBgNVHRMBAf8EBTADAQH/MB0G\nA1UdDgQWBBQVb9vsej3AhKXXgbWRvfmoWNM++jANBgkqhkiG9w0BAQ0FAAOCAgEA\nVPrUd4UDjOhkxOzSN4bMr0cULZJwQPRV8aj99tzdv8Ef44CwLVkLmm7Z2d1uRA9l\n7xbK6W8L1oL95iV4K4o2u4+ZFG7mrOfU2T2wgTfMlIxHDoAxS49flUYkBpQI1Wj4\nJBZ6fKGFVH6PyIio0I2Mx2u80ZX6lPYQ2q4DR6eBUoNt8T8XSWpD4TjroFbOVIp+\nN84alBca/pvW2aF2HwPndrL/Y++HZp3TpdUeBUT757KOZ7hdwf30pxd8qNn8+peb\nbP2h6b9pjKAmS8ciBExJzchhQWJRP6LIdvexTsBQ1HLxlZNrlg66wYT0kuVVzRTa\n0qRvIjQ0ntmhy2DtmE5VFT9O8ahcQL5Ddk8B4dhiy59vjALS6kIUXJ6GCobzRUsQ\na7b7J7nu+PTY+qVo0LsTMO1rVTUXD63gVk8QmPUwnvduk9nxraNpVP+m17BuEcls\nEsoGAAQYcmzOlnZpqhhbTnbsEayW1bMyxkLjBjXpOfBgrvyv5fU/09lP6VB20FJr\nzVPZWr5PTzaaizDDecSKgZ1ANIwXIIwWirwzDqqQb922JtcH+Ca6JJWgrV7+kDCU\ncVzwKVYievjXMCsmRSzDKEgp4n1AgrxcoaH0smD+qA+wzfsMqvEA1iTNW7zdnF0o\n6UJ9rkWxKr+JRZ5jFO+kpKQ1DxfDJZE554aO8AXzYEI=\n-----END CERTIFICATE-----\n"
    },
    "browser": [
        {
            "match": "https://auth.mockbank.openbankingbrasil.org.br/auth*",
            "tasks": [
                {
                    "task": "Login",
                    "optional": true,
                    "match": "https://auth.mockbank.openbankingbrasil.org.br/interaction*",
                    "commands": [
                        [
                            "text",
                            "name",
                            "login",
                            "ralph.bragg@gmail.com",
                            "optional"
                        ],
                        [
                            "text",
                            "name",
                            "password",
                            "P@ssword01",
                            "optional"
                        ],
                        [
                            "click",
                            "xpath",
                            "//button[contains(text(),\"Sign in\")]",
                            "optional"
                        ]
                    ]
                },
                {
                    "task": "Consent",
                    "optional": true,
                    "match": "https://auth.mockbank.openbankingbrasil.org.br/interaction*",
                    "commands": [
                        [
                            "wait",
                            "xpath",
                            "//*",
                            60,
                            ".*Before proceeding, we need to confirm some information:*",
                            "update-image-placeholder-optional"
                        ],
                        [
                            "click",
                            "xpath",
                            "//input[@id='consent-toggle']/following-sibling::div[1]"
                        ],
                        [
                            "click",
                            "id",
                            "continue-button"
                        ]
                    ]
                },
                {
                    "task": "Verify Complete",
                    "match": "*/test/*/callback*",
                    "commands": [
                        [
                            "wait",
                            "id",
                            "submission_complete",
                            10
                        ]
                    ]
                }
            ]
        }
    ],
    "override": {
        "automatic-payments_api_automatic-pix-unmatching-loggedUser_test-module_v2-2": {
            "resource": {
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "76109277673",
                            "name": "Ralph Bragg"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "1333.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "11188222",
                                    "accountType": "SVGS"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnCnpj": "43142666000197",
                "loggedUserIdentification": "87517400444",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "1333.00",
                "creditorName": "Ralph Bragg",
                "creditorAccountIspb": "99999004",
                "creditorAccountIssuer": "0001",
                "creditorAccountNumber": "11188222",
                "creditorAccountAccountType": "SVGS",
                "creditorCpfCnpj": "50685362006773",
                "contractDebtorName": "Example",
                "contractDebtorIdentification": "76109277673"
            }
        }
    },
    "automatic-payments_api_multiple-consents-core_test-module_v2n1": {
        "resource": {
            "consentUrl": "https://auth.mockbank.openbankingbrasil.org.br/open-banking/automatic-payments/v2/recurring-consents",
            "brazilPaymentConsent": {
                "data": {
                    "loggedUser": {
                        "document": {
                            "identification": "87517400444",
                            "rel": "CPF"
                        }
                    },
                    "creditor": {
                        "personType": "PESSOA_NATURAL",
                        "cpfCnpj": "87517400444",
                        "name": "Gabriel Nunes"
                    },
                    "payment": {
                        "type": "PIX",
                        "date": "2021-01-01",
                        "currency": "BRL",
                        "amount": "1333.00",
                        "details": {
                            "localInstrument": "DICT",
                            "proxy": "12345678901",
                            "creditorAccount": {
                                "ispb": "12345678",
                                "issuer": "1774",
                                "number": "94088393",
                                "accountType": "CACC"
                            }
                        }
                    },
                    "debtorAccount": {
                        "ispb": "12345678",
                        "issuer": "6272",
                        "number": "94088393",
                        "accountType": "CACC"
                    }
                }
            },
            "brazilOrganizationId": "74e929d9-33b6-4d85-8ba7-c146c867a817",
            "brazilQrdnCnpj": "43142666000197",
            "loggedUserIdentification": "87517400444",
            "debtorAccountIspb": "12345678",
            "debtorAccountIssuer": "1774",
            "debtorAccountNumber": "94088393",
            "debtorAccountType": "CACC",
            "paymentAmount": "1333.00",
            "creditorName": "Gabriel Nunes",
            "creditorAccountIspb": "99999004",
            "creditorAccountIssuer": "0001",
            "creditorAccountNumber": "94088393",
            "creditorAccountAccountType": "CACC",
            "creditorCpfCnpj": "87517400444",
            "contractDebtorName": "Example",
            "contractDebtorIdentification": "87517400444"
        },
        "browser": [
            {
                "match": "https://auth.mockbank.openbankingbrasil.org.br/auth*",
                "tasks": [
                    {
                        "task": "Login",
                        "optional": true,
                        "match": "https://auth.mockbank.openbankingbrasil.org.br/interaction*",
                        "commands": [
                            [
                                "text",
                                "name",
                                "username",
                                "gabriel.nunes@email.com",
                                "optional"
                            ],
                            [
                                "text",
                                "name",
                                "password",
                                "P@ssword01",
                                "optional"
                            ],
                            [
                                "click",
                                "xpath",
                                "//button[contains(text(),\"Sign in\")]",
                                "optional"
                            ]
                        ]
                    },
                    {
                        "task": "Retry Login",
                        "optional": true,
                        "match": "https://auth.mockbank.openbankingbrasil.org.br/interaction*",
                        "commands": [
                            [
                                "text",
                                "name",
                                "username",
                                "gabriel.nunes@email.com",
                                "optional"
                            ],
                            [
                                "text",
                                "name",
                                "password",
                                "P@ssword01",
                                "optional"
                            ],
                            [
                                "click",
                                "xpath",
                                "//button[contains(text(),\"Sign in\")]",
                                "optional"
                            ]
                        ]
                    },
                    {
                        "task": "Consent",
                        "optional": true,
                        "match": "https://auth.mockbank.openbankingbrasil.org.br/interaction*",
                        "commands": [
                            [
                                "wait",
                                "xpath",
                                "//*",
                                10,
                                ".*Before sharing your data, we need to confirm some information:*",
                                "update-image-placeholder-optional"
                            ],
                            [
                                "click",
                                "xpath",
                                "//label[@for='consent']/div[1]/div[1]"
                            ],
                            [
                                "click",
                                "id",
                                "consent"
                            ],
                            [
                                "click",
                                "id",
                                "continue"
                            ]
                        ]
                    },
                    {
                        "task": "Verify Complete",
                        "match": "*/test/*/callback*",
                        "commands": [
                            [
                                "wait",
                                "id",
                                "submission_complete",
                                10
                            ]
                        ]
                    }
                ]
            }
        ]
    },
    "automatic-payments_api_webhook-multiple-consents_test-module_v2n1": {
        "resource": {
            "consentUrl": "https://auth.mockbank.openbankingbrasil.org.br/open-banking/automatic-payments/v2/recurring-consents",
            "webhookWaitTime": "5",
            "brazilPaymentConsent": {
                "data": {
                    "loggedUser": {
                        "document": {
                            "identification": "87517400444",
                            "rel": "CPF"
                        }
                    },
                    "creditor": {
                        "personType": "PESSOA_NATURAL",
                        "cpfCnpj": "87517400444",
                        "name": "Gabriel Nunes"
                    },
                    "payment": {
                        "type": "PIX",
                        "date": "2021-01-01",
                        "currency": "BRL",
                        "amount": "1333.00",
                        "details": {
                            "localInstrument": "DICT",
                            "proxy": "12345678901",
                            "creditorAccount": {
                                "ispb": "12345678",
                                "issuer": "1774",
                                "number": "94088393",
                                "accountType": "CACC"
                            }
                        }
                    },
                    "debtorAccount": {
                        "ispb": "12345678",
                        "issuer": "6272",
                        "number": "94088393",
                        "accountType": "CACC"
                    }
                }
            },
            "brazilOrganizationId": "74e929d9-33b6-4d85-8ba7-c146c867a817",
            "brazilQrdnCnpj": "43142666000197",
            "loggedUserIdentification": "87517400444",
            "debtorAccountIspb": "12345678",
            "debtorAccountIssuer": "1774",
            "debtorAccountNumber": "94088393",
            "debtorAccountType": "CACC",
            "paymentAmount": "1333.00",
            "creditorName": "Gabriel Nunes",
            "creditorAccountIspb": "99999004",
            "creditorAccountIssuer": "0001",
            "creditorAccountNumber": "94088393",
            "creditorAccountAccountType": "CACC",
            "creditorCpfCnpj": "87517400444",
            "contractDebtorName": "Example",
            "contractDebtorIdentification": "87517400444"
        },
        "browser": [
            {
                "match": "https://auth.mockbank.openbankingbrasil.org.br/auth*",
                "tasks": [
                    {
                        "task": "Login",
                        "optional": true,
                        "match": "https://auth.mockbank.openbankingbrasil.org.br/interaction*",
                        "commands": [
                            [
                                "text",
                                "name",
                                "username",
                                "gabriel.nunes@email.com",
                                "optional"
                            ],
                            [
                                "text",
                                "name",
                                "password",
                                "P@ssword01",
                                "optional"
                            ],
                            [
                                "click",
                                "xpath",
                                "//button[contains(text(),\"Sign in\")]",
                                "optional"
                            ]
                        ]
                    },
                    {
                        "task": "Retry Login",
                        "optional": true,
                        "match": "https://auth.mockbank.openbankingbrasil.org.br/interaction*",
                        "commands": [
                            [
                                "text",
                                "name",
                                "username",
                                "gabriel.nunes@email.com",
                                "optional"
                            ],
                            [
                                "text",
                                "name",
                                "password",
                                "P@ssword01",
                                "optional"
                            ],
                            [
                                "click",
                                "xpath",
                                "//button[contains(text(),\"Sign in\")]",
                                "optional"
                            ]
                        ]
                    },
                    {
                        "task": "Consent",
                        "optional": true,
                        "match": "https://auth.mockbank.openbankingbrasil.org.br/interaction*",
                        "commands": [
                            [
                                "wait",
                                "xpath",
                                "//*",
                                10,
                                ".*Before sharing your data, we need to confirm some information:*",
                                "update-image-placeholder-optional"
                            ],
                            [
                                "click",
                                "xpath",
                                "//label[@for='consent']/div[1]/div[1]"
                            ],
                            [
                                "click",
                                "id",
                                "consent"
                            ],
                            [
                                "click",
                                "id",
                                "continue"
                            ]
                        ]
                    },
                    {
                        "task": "Verify Complete",
                        "match": "*/test/*/callback*",
                        "commands": [
                            [
                                "wait",
                                "id",
                                "submission_complete",
                                10
                            ]
                        ]
                    }
                ]
            }
        ]
    },
    "description": "Phase 3 - Automatic Pix/Sweeping Payments v2"
}
```

</details>

<details>
<summary>JSON Configuration for Enrollments Automatic Payments v2 (Auto Redirect)</summary>

```
   {
    "alias": "obbsb",
    "description": "Phase 3 - No Redirect Automatic Payments v2",
    "server": {
        "discoveryUrl": "https://auth.mockbank.poc.raidiam.io/.well-known/openid-configuration"
    },
    "client": {
    "jwks": {
      "keys": [
        {
          "kty": "RSA",
          "kid": "4Ye5cykoqvNKSAw-xublHCau5h8Pn3CZoMHoK4ak1jo",
          "d": "A908FRFgUNsvqa_hwRXCCor2C5dbCoBGyZI0kGOui5nCE9wwWKe2lkol-sMbGvyPPuy-LWFN40WmuqBNspAEo5FDC3oF8d1rC0fXsWIayeymKedNuG3pI_aikD-VPmJJVqNgMhBeuExWpaDGHlXkpxhq1CihhNMe1Ya7NGPa6ADVqoaXw50gL5k4UQc8x6L0MKWKth1Vor6gX-bIGtlGP0SoAaWyx3KtJbhJgrliwRHYM3OXxljZ52nH-4sO8laN0GFm6LKmTCGYBhyEKCRTmPT79Y79oHQHXeOEcJHJI0GgB74Re_97Tn7WGjIHdKIblLjj3_UW17Ds3NfgUQ-DvQ",
          "n": "wUL84Qmzs8xlR_0cxBdnJ9JbV4ZC2dNL-hKV9W7xIbc9ph7XpiUqg3LT4o96bxhu3WLct8GDzB4K4sy8wi1zPJ5n99-LMfbSaTZ33bT-MXJsXDGMZvLhiBGvfPZnbUGvXa9vXb46t6bLtmMsLxsvgNVG40YgTVCFJWRaQlkOWmikRt1oIEko6nmwrKxAzrGOQQncuYDhHrkKmh7uw7Yw4ii2UKdiCSrSzxHK5SF2rLlROC6k4Hbx2uVLwquziteIZf1ugnKGQAqe2BBAxvPR-SSIh22QszM6t7nGWojFu0dO9-g9N2sINpDSjM7IeGi3QtT7T-Zj8kQ5QO2m3HvrJw",
          "e": "AQAB",
          "p": "-zKI9ijtCjk7mwVb5OxrGhFjqOtK-DXXAZ2JoOzWng5YOU51fnkAfkS7ZN5OJ4rTbmzATuQO5NHF7SOHSYUciqSzJkELK_ibQk26zJm9WmYXHAwRmdoGWgR2bA3jQZ-d-Ne7TSP5WSMv28uUV28PtlVvr_QOpkr-bLbu8kBosvs",
          "q": "xPTkIadkO-YHwg4pUC0K046uFoZiagzVI77qgJYUh8q_uzGYYabIIaWt4u_IOJwAZvmevczKHe_iewFQfe_cUzH7jJR_PfNzXmC_F5k1LBOpGaEVr0JY5uGQljRKcqL8KwqtZe5rNcKtX-sbk9KXLz1WPk9mnzsQ2zQvNfknkMU",
          "dp": "mdZxGpAl20UBxAacKK7BSM2tgx3WY_xVGKAqUWu6ZEHUtgPe4P2p16qwOS4MHxteMRpZC_ePR4NQ-9HuYJAs0pvbO2pKNTujmg-Qfw0Icfxj2sFpZheoHCjvfW1j6CSg0m0MQEnvwy9ReAJNbt6NeNUJ-XA2KJF1D49Y9vOLK1E",
          "dq": "l8sZa2qEELn3brLVWkpslqHXP9rwTEV5myQPvWxthD5ZSF8vzsroYS48drNQf3iTwslNc4A6oZn41c4sh_Ltvly-PxlPe6J-XtV3USut1DuOzwbcHIeo1sAvW-QPIIzGhjGjc_StQfC5CDy9s07RYAIIztsI_11ZX2e3nwRYXvU",
          "qi": "1WJTqkmWos-v8k1ix8l0jjZTvXdh2zy-10yOstleXDrL1FfwOI-FEY1-alHV5ap5mcf_K0yT9yhG3-J3uKtLMVT4NMaD96-yx55UHag-QHhZKYI9NUFo_7L8qtQ4tVWJ-Q95IYSaUOmrHi5jq6uKJlg-De8Ct5WrBVoljvxLcKA",
          "alg": "PS256",
          "use": "sig"
        },
        {
          "p": "2a8fRJ7ybF-qtF1zrYzSm7z3C4wNTUMbVYqe44tR9FbKsobqW2tS0iAZf-GJ_SZPcWxkE76gunW7YqMJecGUtXsJ8TTHwjcPQOMYzxnyJu8Q4JOj01YJVrxUY9D0ZzpWM9oTAj1-qoE0w7Dy-XNUc14-HeRlmOkg2tTfrXTVR8c",
          "kty": "RSA",
          "q": "0xlPJFRUcBU5j2SKSajVnd4H5p88RSsd4cArMby1ZRuSeHEsX76c6QKAPq7uTfKrTeZic34yzAEUyHloP1fZQYQ2UQn-f6PsTAWdT1Lp5oi2VZCT0yc9-1EGnLAiUCbM9SQQyf2GIVhCiAk_0VuY6le61Pw0U4GssvFJzIrx4as",
          "d": "GxnizpWcqL1wajD8-Y-8H9-II4UZMKfkgbfwRiLK9uAd8-kEJdO9jdNeMxyytg2saDhxNTeRTkYz_VbBf3p9dGhuYx84d-ZagUbIiU3ho3FCsBRrzQQZw9OQrzPDUzp0-SBn1_GLCf9fo4ysxWHbn9euJVi2fpN_bHlBi1n8fKhdBHYE7X3XJnRYrUXItxZw5sJsqM_boONLxdLAvgmZx5CHft94JZsR6JPwlj9Ba_CuNWX_3OuUGyV0f5_1ICAEYijw9PA8KAW6t5UUYn39_KYL8nF5L1Bh6W1j8eN84I2lcKZNO6Pou064ag_wqGhk4uXuQO1IV8jRFn3-pqhSEQ",
          "e": "AQAB",
          "use": "enc",
          "kid": "c1d7b80ce4b88c4f2cfb68e7a8c45bfff355ae94259bc1a73a95ddbaeaf7c96b",
          "qi": "pU1IXwiQoFERdzJsx7kSC79Gwhak7uw7OAJCbcfkKE3GSwTWHrKfg5uDZlNvSnNU1Hbpxd0bgc40dFI2aNBML1gyDwTjQplWVJikkFix8E6z_ErSa_D5w5yV4k6CNtt7OzlMXawiZ-ndcuiOs5MkfSRyeB3k5rQmuZjLVzFFlnw",
          "dp": "Gn4dqBRQHLBn7huRgIWq_Bk7V8RrugN4yChevgKurrYBZUjWLNoa8kfF0rJ4QL7w3DT82QpSNV8utwpwlMjieFPJGfn6dcCNsq_wzQOzXNmrjClrvsSxzkSNYLiFhiqrYxQfTB5_0_B1o3tdls5acM__b1PkqX916CwQLOQTMPE",
          "alg": "PS256",
          "dq": "NS0x94fawWVHW6zK_SUvspXkzZ6dMxtaaqza9KuB0ldwvTBdKj09D6FWpvOwCiiwKG55rHhE2YkIMDwNG6_Iha2FdUKcPpEPjFL5vqq3SyBzNfi2lEFVZsKRdNUVv7UWekY8iHV53Vp7YANcdSOq0JWK9e4WTFblJyqLGaCCsAM",
          "n": "s4DcK4uxKroJPE1R7Te4ppNexbuK3C-Z3MpXFr5hmY43gYIoVMo89jE6OcDiO0Z4rxe8dsH4oYA2vAJQ0IhAaUxYMk2kN01ei761zMQWHLUPLcEKWgipYHy4AgwAUaF7-Glyb0DT1RRcY4f1tEddftxhwXZjeFduj6luVg6fVvXRIRjttybUkIKvf5ShMofVFCF_IyjYlOal4g3DVnCg62dR71WX3fRXSufxrRBG-L61rv2VSMg8pIb1DFiYKDlEXEnTdLk-7goBpTIz3wBsrZgJESSZOn_BG_-fCE0V75rheLMuJd4IGE4H0taVfEQOJKRKBVzc2jAz0sOaVuPY7Q"
        }
      ]
    },
    "org_jwks": {
      "keys": [
        {
          "kty": "RSA",
          "kid": "4Ye5cykoqvNKSAw-xublHCau5h8Pn3CZoMHoK4ak1jo",
          "d": "A908FRFgUNsvqa_hwRXCCor2C5dbCoBGyZI0kGOui5nCE9wwWKe2lkol-sMbGvyPPuy-LWFN40WmuqBNspAEo5FDC3oF8d1rC0fXsWIayeymKedNuG3pI_aikD-VPmJJVqNgMhBeuExWpaDGHlXkpxhq1CihhNMe1Ya7NGPa6ADVqoaXw50gL5k4UQc8x6L0MKWKth1Vor6gX-bIGtlGP0SoAaWyx3KtJbhJgrliwRHYM3OXxljZ52nH-4sO8laN0GFm6LKmTCGYBhyEKCRTmPT79Y79oHQHXeOEcJHJI0GgB74Re_97Tn7WGjIHdKIblLjj3_UW17Ds3NfgUQ-DvQ",
          "n": "wUL84Qmzs8xlR_0cxBdnJ9JbV4ZC2dNL-hKV9W7xIbc9ph7XpiUqg3LT4o96bxhu3WLct8GDzB4K4sy8wi1zPJ5n99-LMfbSaTZ33bT-MXJsXDGMZvLhiBGvfPZnbUGvXa9vXb46t6bLtmMsLxsvgNVG40YgTVCFJWRaQlkOWmikRt1oIEko6nmwrKxAzrGOQQncuYDhHrkKmh7uw7Yw4ii2UKdiCSrSzxHK5SF2rLlROC6k4Hbx2uVLwquziteIZf1ugnKGQAqe2BBAxvPR-SSIh22QszM6t7nGWojFu0dO9-g9N2sINpDSjM7IeGi3QtT7T-Zj8kQ5QO2m3HvrJw",
          "e": "AQAB",
          "p": "-zKI9ijtCjk7mwVb5OxrGhFjqOtK-DXXAZ2JoOzWng5YOU51fnkAfkS7ZN5OJ4rTbmzATuQO5NHF7SOHSYUciqSzJkELK_ibQk26zJm9WmYXHAwRmdoGWgR2bA3jQZ-d-Ne7TSP5WSMv28uUV28PtlVvr_QOpkr-bLbu8kBosvs",
          "q": "xPTkIadkO-YHwg4pUC0K046uFoZiagzVI77qgJYUh8q_uzGYYabIIaWt4u_IOJwAZvmevczKHe_iewFQfe_cUzH7jJR_PfNzXmC_F5k1LBOpGaEVr0JY5uGQljRKcqL8KwqtZe5rNcKtX-sbk9KXLz1WPk9mnzsQ2zQvNfknkMU",
          "dp": "mdZxGpAl20UBxAacKK7BSM2tgx3WY_xVGKAqUWu6ZEHUtgPe4P2p16qwOS4MHxteMRpZC_ePR4NQ-9HuYJAs0pvbO2pKNTujmg-Qfw0Icfxj2sFpZheoHCjvfW1j6CSg0m0MQEnvwy9ReAJNbt6NeNUJ-XA2KJF1D49Y9vOLK1E",
          "dq": "l8sZa2qEELn3brLVWkpslqHXP9rwTEV5myQPvWxthD5ZSF8vzsroYS48drNQf3iTwslNc4A6oZn41c4sh_Ltvly-PxlPe6J-XtV3USut1DuOzwbcHIeo1sAvW-QPIIzGhjGjc_StQfC5CDy9s07RYAIIztsI_11ZX2e3nwRYXvU",
          "qi": "1WJTqkmWos-v8k1ix8l0jjZTvXdh2zy-10yOstleXDrL1FfwOI-FEY1-alHV5ap5mcf_K0yT9yhG3-J3uKtLMVT4NMaD96-yx55UHag-QHhZKYI9NUFo_7L8qtQ4tVWJ-Q95IYSaUOmrHi5jq6uKJlg-De8Ct5WrBVoljvxLcKA",
          "alg": "PS256",
          "use": "sig"
        },
        {
          "p": "2a8fRJ7ybF-qtF1zrYzSm7z3C4wNTUMbVYqe44tR9FbKsobqW2tS0iAZf-GJ_SZPcWxkE76gunW7YqMJecGUtXsJ8TTHwjcPQOMYzxnyJu8Q4JOj01YJVrxUY9D0ZzpWM9oTAj1-qoE0w7Dy-XNUc14-HeRlmOkg2tTfrXTVR8c",
          "kty": "RSA",
          "q": "0xlPJFRUcBU5j2SKSajVnd4H5p88RSsd4cArMby1ZRuSeHEsX76c6QKAPq7uTfKrTeZic34yzAEUyHloP1fZQYQ2UQn-f6PsTAWdT1Lp5oi2VZCT0yc9-1EGnLAiUCbM9SQQyf2GIVhCiAk_0VuY6le61Pw0U4GssvFJzIrx4as",
          "d": "GxnizpWcqL1wajD8-Y-8H9-II4UZMKfkgbfwRiLK9uAd8-kEJdO9jdNeMxyytg2saDhxNTeRTkYz_VbBf3p9dGhuYx84d-ZagUbIiU3ho3FCsBRrzQQZw9OQrzPDUzp0-SBn1_GLCf9fo4ysxWHbn9euJVi2fpN_bHlBi1n8fKhdBHYE7X3XJnRYrUXItxZw5sJsqM_boONLxdLAvgmZx5CHft94JZsR6JPwlj9Ba_CuNWX_3OuUGyV0f5_1ICAEYijw9PA8KAW6t5UUYn39_KYL8nF5L1Bh6W1j8eN84I2lcKZNO6Pou064ag_wqGhk4uXuQO1IV8jRFn3-pqhSEQ",
          "e": "AQAB",
          "use": "enc",
          "kid": "c1d7b80ce4b88c4f2cfb68e7a8c45bfff355ae94259bc1a73a95ddbaeaf7c96b",
          "qi": "pU1IXwiQoFERdzJsx7kSC79Gwhak7uw7OAJCbcfkKE3GSwTWHrKfg5uDZlNvSnNU1Hbpxd0bgc40dFI2aNBML1gyDwTjQplWVJikkFix8E6z_ErSa_D5w5yV4k6CNtt7OzlMXawiZ-ndcuiOs5MkfSRyeB3k5rQmuZjLVzFFlnw",
          "dp": "Gn4dqBRQHLBn7huRgIWq_Bk7V8RrugN4yChevgKurrYBZUjWLNoa8kfF0rJ4QL7w3DT82QpSNV8utwpwlMjieFPJGfn6dcCNsq_wzQOzXNmrjClrvsSxzkSNYLiFhiqrYxQfTB5_0_B1o3tdls5acM__b1PkqX916CwQLOQTMPE",
          "alg": "PS256",
          "dq": "NS0x94fawWVHW6zK_SUvspXkzZ6dMxtaaqza9KuB0ldwvTBdKj09D6FWpvOwCiiwKG55rHhE2YkIMDwNG6_Iha2FdUKcPpEPjFL5vqq3SyBzNfi2lEFVZsKRdNUVv7UWekY8iHV53Vp7YANcdSOq0JWK9e4WTFblJyqLGaCCsAM",
          "n": "s4DcK4uxKroJPE1R7Te4ppNexbuK3C-Z3MpXFr5hmY43gYIoVMo89jE6OcDiO0Z4rxe8dsH4oYA2vAJQ0IhAaUxYMk2kN01ei761zMQWHLUPLcEKWgipYHy4AgwAUaF7-Glyb0DT1RRcY4f1tEddftxhwXZjeFduj6luVg6fVvXRIRjttybUkIKvf5ShMofVFCF_IyjYlOal4g3DVnCg62dR71WX3fRXSufxrRBG-L61rv2VSMg8pIb1DFiYKDlEXEnTdLk-7goBpTIz3wBsrZgJESSZOn_BG_-fCE0V75rheLMuJd4IGE4H0taVfEQOJKRKBVzc2jAz0sOaVuPY7Q"
        }
      ]
    },
    "client_id": "hcGG31HvR3SqOlHva6XKk"
  },
  "mtls": {
    "cert": "-----BEGIN CERTIFICATE-----\nMIIHPDCCBiSgAwIBAgIUNvdRCFMpnEY83FoXH5To5lgctXcwDQYJKoZIhvcNAQEL\nBQAweTELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MS0wKwYDVQQDEyRPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBJc3N1aW5nIENBIC0gRzIwHhcNMjUxMTA0MTkxMTAwWhcN\nMjYxMjA0MTkxMTAwWjCCAUYxCzAJBgNVBAYTAkJSMQswCQYDVQQIEwJTUDEPMA0G\nA1UEBxMGTE9ORE9OMRwwGgYDVQQKExNPcGVuIEJhbmtpbmcgQnJhc2lsMUMwQQYD\nVQQDEzpodHRwczovL3dlYi5jb25mb3JtYW5jZS5kaXJlY3Rvcnkub3BlbmJhbmtp\nbmdicmFzaWwub3JnLmJyMRcwFQYDVQQFEw40MzE0MjY2NjAwMDE5NzEdMBsGA1UE\nDxMUUHJpdmF0ZSBPcmdhbml6YXRpb24xEzARBgsrBgEEAYI3PAIBAxMCVUsxMzAx\nBgNVBGETKk9GQkJSLTc0ZTkyOWQ5LTMzYjYtNGQ4NS04YmE3LWMxNDZjODY3YTgx\nNzE0MDIGCgmSJomT8ixkAQETJGM1NTI2YjBhLThhM2UtNDczYy04YmY2LWM4NWM4\nZDMxODY4NzCCASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEBALqJVhgtFnm8\n++oVqg3iZjHEDKcgOO6EEXm5Te55w7zTjY7Dk3Wxwy0SnuxJH+LsF0Id2PAm6P2C\nB7QKGqDq3ZRE2+Xmw/plT62k1Cgl+3PoAtTznCMEcwvVIGphEIzXle+0rUd/ZkOh\nly6IkvZpjvCDcDOseXYmjfme5D3THsvPY6do4e8mQLnblg0OM0ik312r0yG0hWSF\n8pQglLrNFKuz9Id8MHpuTil5WxCqwM89Jx5zbzEcrG1swDoR6m2vYoEn/QSZOFjD\nQgKb8/giEklwWCOM/UofsnT+BZvOZYlX5rYw4WQFOA4G3rIJDp+1dupCDSAExKQY\nYnZNwj4H4RECAwEAAaOCAuswggLnMAwGA1UdEwEB/wQCMAAwHQYDVR0OBBYEFNso\nb3tsmRqcmerAXDx/3xtqs5oLMB8GA1UdIwQYMBaAFHrvC4jYeonhvS8EPR6x1sRH\nQig9MFkGCCsGAQUFBwEBBE0wSzBJBggrBgEFBQcwAYY9aHR0cDovL29jc3AucGtp\nLWcyLnNhbmRib3guZGlyZWN0b3J5Lm9wZW5iYW5raW5nYnJhc2lsLm9yZy5icjBY\nBgNVHR8EUTBPME2gS6BJhkdodHRwOi8vY3JsLnBraS1nMi5zYW5kYm94LmRpcmVj\ndG9yeS5vcGVuYmFua2luZ2JyYXNpbC5vcmcuYnIvaXNzdWVyLmNybDBFBgNVHREE\nPjA8gjpodHRwczovL3dlYi5jb25mb3JtYW5jZS5kaXJlY3Rvcnkub3BlbmJhbmtp\nbmdicmFzaWwub3JnLmJyMA4GA1UdDwEB/wQEAwIFoDATBgNVHSUEDDAKBggrBgEF\nBQcDAjCCAXQGA1UdIASCAWswggFnMIIBYwYLKwYBBAGDui9wAQIwggFSMIH1Bggr\nBgEFBQcCAjCB6AyB5VRoaXMgQ2VydGlmaWNhdGUgaXMgc29sZWx5IGZvciB1c2Ug\nd2l0aCBPcGVuIEZpbmFuY2UgQnJhc2lsIHNhbmRib3ggQVBJcyBTZXJ2aWNlcy4g\nSXRzIHJlY2VpcHQsIHBvc3Nlc3Npb24gb3IgdXNlIGNvbnN0aXR1dGVzIGFjY2Vw\ndGFuY2Ugb2YgdGhlIE9wZW4gRmluYW5jZSBCcmFzaWwgc2FuZGJveCBvZiBBUElz\nIENlcnRpZmljYXRlIFBvbGljeSBhbmQgcmVsYXRlZCBkb2N1bWVudHMgdGhlcmVp\nbi4wWAYIKwYBBQUHAgEWTGh0dHA6Ly9yZXBvc2l0b3J5LnBraS1nMi5zYW5kYm94\nLmRpcmVjdG9yeS5vcGVuYmFua2luZ2JyYXNpbC5vcmcuYnIvcG9saWNpZXMwDQYJ\nKoZIhvcNAQELBQADggEBAInsISQT8kn3HHXu9vvur6ki6iLOE5RQDlemlM//Y7Q1\nDr5m7+oWitZxa4I8coDw6NUyIX/ChOKZKV+tZcR63akGqZgI35EKDZlJtc5M7l/m\nfdLLuG9Z27in8dPt1NJeEBSerFcIIcmE4hsoO62XjozKuiZfOgUG5mC8LvMlDaAE\n2prr2vsZCAGbxr6AnSLm4tqzjpSDz8QXnReCMfveFpiNRQclGkF9qP+oI/UX/ogO\n2evThpYJhQGtoYql2QZC5t38LYfRur85PIbHZrH/pCUZyKyU1Mr56t5gIxpdVghU\nRLGSxghjv38mdy/LwaKVwKNmnhJebNwtZ5vHvNuJodM=\n-----END CERTIFICATE-----",
    "key": "-----BEGIN PRIVATE KEY-----\nMIIEvAIBADANBgkqhkiG9w0BAQEFAASCBKYwggSiAgEAAoIBAQC6iVYYLRZ5vPvq\nFaoN4mYxxAynIDjuhBF5uU3uecO8042Ow5N1scMtEp7sSR/i7BdCHdjwJuj9gge0\nChqg6t2URNvl5sP6ZU+tpNQoJftz6ALU85wjBHML1SBqYRCM15XvtK1Hf2ZDoZcu\niJL2aY7wg3AzrHl2Jo35nuQ90x7Lz2OnaOHvJkC525YNDjNIpN9dq9MhtIVkhfKU\nIJS6zRSrs/SHfDB6bk4peVsQqsDPPScec28xHKxtbMA6Eeptr2KBJ/0EmThYw0IC\nm/P4IhJJcFgjjP1KH7J0/gWbzmWJV+a2MOFkBTgOBt6yCQ6ftXbqQg0gBMSkGGJ2\nTcI+B+ERAgMBAAECggEAW5+CnNxkqkYz3I5omWpHdRFNf7eZjzpqlQX6a/T+Ol0V\nLncNEqXObvCzA++FDIKXh/++I3ORRJfebcX6v2itjprmAf4/69lgcjPAi7ngUVW4\nMl44JpEUa07znZzwsqVf/b4a0MAYfIa+CfrGaOd/cM62yYLhpDGa0e4EQQPWoBd1\nePgAszAz7x3FeRkf3GW4qIdcail5y0++RlGBvhvi043BK9RO0AF/9u+JeLYsSaVi\nrS/IoGVWUD+CJeu+xyx04n3a5zzv2DyDUj7Kz6VHRkyYg4lxa/nlOwGnbxwoxpFc\nmrMtmpkREmQ3n4UwqXVV/ajghRJWONU8mJweDvBrKwKBgQDzY8KDsxV4V14/APtp\nRNCeq6GU6mVYr1BqkRvZEUMXQ9MYmTuf7PA03fmJlxOTABBEhI7DK46dg1DQusy3\ng/4TALWlq+dQIfxk3zGbCpcDSTBNsDx9N6uwX8Pu3IFbMJ4G0LlLEReoYGjGfC6J\n9ePwoc65qIT9xxCR59SZiOanVwKBgQDEM36HJkev2irh14mQ/Hz3x5BQN3omsX+3\ni1lA31BZemdG793kFLiWPFNbDtQ2LEWQTGw5+qsDIMLd2cvW+hC1zRivDDEQwFK4\nAmIWjTIwM+RK4b7R4rwU2BFjO9vSxYiB0eW6pT+gmQmqg3UEWqA8AFIpeyylNdup\nforbN2YB1wKBgEEAkK+ZwY8tTkdnXL3lmg32aqYZ381KrSB49sYHXTK2c4drTUhO\nAG0uJ3n+tkSZTL7v5Czt0h3xN0E30nrkrpOmqdzAR3vYR88s6NOuhVxkTJlDCzSq\nDJmDShHeJFIVbu8FCaepvfbDINh5y/geiqz2mf5tqm8Yni1JjDchH/DrAoGAAQ3F\nwDQUbn1dfZkKxByXDz2jKMsjfNG3PeUhtZd9dv2RUHA5YOA7nZL1X6fUu/XA6eV/\nL1CJWprycP6aea0eKdvQJiCKouxlhVd972ESw++DamOMAtSU7ge7EC1iIN+uvAPE\nmBwLG3G2+5N5LWzPL4NQ7agbtUd0xpRHaqYBhkECgYAiGHNGtm01fSXgCYKgge6M\nT7PdEKXU4b1Y/UaBrKokFr1rFK0bBQF/SqRybm862opyK40erawRbL/kvaBc8h3w\nN/w6DuWQg5hSfKfAWbzkMHUs4OPdk/cGB9v1wa01GDNWYWD0cKy1vaJCc5eWM0gU\naipGpudt6UPFmkhfn7NnkA==\n-----END PRIVATE KEY-----",
    "ca": "-----BEGIN CERTIFICATE-----\nMIIHFDCCBPygAwIBAgIUZJOYHaqMZR7leKm8iaKrR380T8QwDQYJKoZIhvcNAQEN\nBQAwdjELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MSowKAYDVQQDEyFPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBSb290IENBIC0gRzIwHhcNMjMwMzA5MTQzNjAwWhcNMzMw\nMzA2MTQzNjAwWjB5MQswCQYDVQQGEwJCUjEcMBoGA1UEChMTT3BlbiBGaW5hbmNl\nIEJyYXNpbDEdMBsGA1UECxMUT3BlbiBGaW5hbmNlIHNhbmRib3gxLTArBgNVBAMT\nJE9wZW4gRmluYW5jZSBzYW5kYm94IElzc3VpbmcgQ0EgLSBHMjCCASIwDQYJKoZI\nhvcNAQEBBQADggEPADCCAQoCggEBAJJZYsafIn0x1j8WLDfJ3HSXt65NqnKwGdcW\nn4z4VqdrvcIl6kJM7cjF3ImaN5SLideuK63/QP4tgGilZxooxLE8V8M/uPgGU74K\noTMBuDho6sND/UtHsr/wgkX9+/Kn50vdLbhXZBmvcL+5gtXKDQGR+d1LyaU8EigX\nkhvegMCSyW72PlQ9FetapanOpH0e5+osGRVI9ysm7PFrWE6UOs8EA/d6+v8SwHTW\nbD6iVVgtGnQtm0C4w4H6VVNnFE0F8pSnXQQPzQXMONIFi/UZPSB00H0qnxRvWkw3\nJa7QErS8hdMPGUHQ9N/RujhMhf7tlUArcgod6mc+SYfcI3j1pUcCAwEAAaOCApUw\nggKRMA4GA1UdDwEB/wQEAwIBBjASBgNVHRMBAf8ECDAGAQH/AgEAMB0GA1UdDgQW\nBBR67wuI2HqJ4b0vBD0esdbER0IoPTAfBgNVHSMEGDAWgBQVb9vsej3AhKXXgbWR\nvfmoWNM++jBZBggrBgEFBQcBAQRNMEswSQYIKwYBBQUHMAGGPWh0dHA6Ly9vY3Nw\nLnBraS1nMi5zYW5kYm94LmRpcmVjdG9yeS5vcGVuYmFua2luZ2JyYXNpbC5vcmcu\nYnIwWAYDVR0fBFEwTzBNoEugSYZHaHR0cDovL2NybC5wa2ktZzIuc2FuZGJveC5k\naXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL2lzc3Vlci5jcmwwggF0\nBgNVHSAEggFrMIIBZzCCAWMGCysGAQQBg7ovcAECMIIBUjCB9QYIKwYBBQUHAgIw\ngegMgeVUaGlzIENlcnRpZmljYXRlIGlzIHNvbGVseSBmb3IgdXNlIHdpdGggT3Bl\nbiBGaW5hbmNlIEJyYXNpbCBzYW5kYm94IEFQSXMgU2VydmljZXMuIEl0cyByZWNl\naXB0LCBwb3NzZXNzaW9uIG9yIHVzZSBjb25zdGl0dXRlcyBhY2NlcHRhbmNlIG9m\nIHRoZSBPcGVuIEZpbmFuY2UgQnJhc2lsIHNhbmRib3ggb2YgQVBJcyBDZXJ0aWZp\nY2F0ZSBQb2xpY3kgYW5kIHJlbGF0ZWQgZG9jdW1lbnRzIHRoZXJlaW4uMFgGCCsG\nAQUFBwIBFkxodHRwOi8vcmVwb3NpdG9yeS5wa2ktZzIuc2FuZGJveC5kaXJlY3Rv\ncnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL3BvbGljaWVzMA0GCSqGSIb3DQEB\nDQUAA4ICAQCANeSAlmJy3e9rrgTGShVCyMQhy68j3cAJyFzqCutyNMGHUgFOjAgD\nzIUQZmAepTDJdhJF+BoruBfAIJUr6tD9EBw2MZXiTLHZG9mqtGwsMbeI3o3R9Y3G\nEpGp72jIHw7mtUZdoaWcmgqxCWn6UT9bBKAkdt6KyRepPUy1YI59MZxpVOs5J0s2\nQFd3FRCNxdzgsuGqdxTb1Gre4I5E1vJWcp1Fe/kPdaOgPVC89M6uk3WYTnMNZ20N\n8K0ecXy8+E3K+to35berWn16g1ZrufylX6s2yyxcsUnh5KP1smFd8MePekKIW0SD\n8hqD1MtGQEmzdWrPCT9fZUzONj4VuDcl/vgfKUBsBszTmqwGF34G+663v10KUhga\nkCiIOZtkT9B+aESGAfczQiFO1h4cI52TKwEptfbplrFS2gILrzleqv0JoDDFYVhY\nV5AVDjqeHaniClCi10JdSN11LqNdagpyojN2a2WhVSAigIT3yDeqozlzjgPui/1E\nDt0zBkXd5uFDwNeLUwOribuS3hxVG5Bg73ZJl+UV3ZuAzFFCfkVBz6BeqUusf8+P\n3pqAQ4gzhSWNsTBIsjaVV8ZU8IqxKhBkRUSNjihG2kM8kX9knQvRbCBuuse/dDUe\n4cUJ+wT1omVgq+TWhShOAjsHEa233omXbH7v5igLBEkzzqmM5cAv8Q==\n-----END CERTIFICATE-----\n-----BEGIN CERTIFICATE-----\nMIIFvDCCA6SgAwIBAgIUKhBUxL5Dt4w3xH1V3X1n+x/e3hcwDQYJKoZIhvcNAQEN\nBQAwdjELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MSowKAYDVQQDEyFPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBSb290IENBIC0gRzIwHhcNMjMwMzA5MTQzNjAwWhcNMzgw\nMzA1MTQzNjAwWjB2MQswCQYDVQQGEwJCUjEcMBoGA1UEChMTT3BlbiBGaW5hbmNl\nIEJyYXNpbDEdMBsGA1UECxMUT3BlbiBGaW5hbmNlIHNhbmRib3gxKjAoBgNVBAMT\nIU9wZW4gRmluYW5jZSBzYW5kYm94IFJvb3QgQ0EgLSBHMjCCAiIwDQYJKoZIhvcN\nAQEBBQADggIPADCCAgoCggIBALJFBgmKj3iDF3C8+8smNNQDxLFA9kCcca1iaxQf\nvMI/FKGW2ullHhH+W3EGEajn39QOlccGyrfCONHLqMW53+HAMtwiIvcrJgj72V7D\nnYflO3aaCFwoC31PL1+pMBo88F6jvezZ8BlRnheT7urCs6+onhz8pm0cVNc77U5X\npi8IOJz1QFKecJnFLjG0NiLCzOzjLSo0A8Rue9K/H5fjq+PqKdXG94AoQyFUwlsU\ny4aXbylDz1kRiOSnOlRNPcY/su95pFKQbGgaZZ1fLf89i5PtHAUu92FbD7H7OyYX\nXpZ97La0d7cUH0A4nb+LpOd/f0c8lAN2Ya1B8aKvWiF23q3c8EoAJyhrdkHKe6yI\nYvLC5G5jkbJefeQcp34IgD8T+Tn3aBF7YgmlYUMbnsuokBG28Hr50EAklCclA0bb\n4pmf8nE6y7VQ0CM/bNZd1F9AjxLukkyvkrOD6A6uv+c5KeC+da245dBzsyhiKe9R\nRX5Gkf7NSkDu9b9YkdDaWV6LXxpUA0SmdT9M16yK3XPDKOWBI4gVSB1KuwrOcal/\ndMwFUlxvqdGugRbxDNNukxa0l3JztGg6XYLjEiiYrQ+7HChbUVNlM0l0VZAz4eON\ngYrq2ExUDWlQXiES389/Qz3R3yDk9ib1YsMHwAux2ulCssFVn4EgtnYFfgf3o01J\n3CedAgMBAAGjQjBAMA4GA1UdDwEB/wQEAwIBBjAPBgNVHRMBAf8EBTADAQH/MB0G\nA1UdDgQWBBQVb9vsej3AhKXXgbWRvfmoWNM++jANBgkqhkiG9w0BAQ0FAAOCAgEA\nVPrUd4UDjOhkxOzSN4bMr0cULZJwQPRV8aj99tzdv8Ef44CwLVkLmm7Z2d1uRA9l\n7xbK6W8L1oL95iV4K4o2u4+ZFG7mrOfU2T2wgTfMlIxHDoAxS49flUYkBpQI1Wj4\nJBZ6fKGFVH6PyIio0I2Mx2u80ZX6lPYQ2q4DR6eBUoNt8T8XSWpD4TjroFbOVIp+\nN84alBca/pvW2aF2HwPndrL/Y++HZp3TpdUeBUT757KOZ7hdwf30pxd8qNn8+peb\nbP2h6b9pjKAmS8ciBExJzchhQWJRP6LIdvexTsBQ1HLxlZNrlg66wYT0kuVVzRTa\n0qRvIjQ0ntmhy2DtmE5VFT9O8ahcQL5Ddk8B4dhiy59vjALS6kIUXJ6GCobzRUsQ\na7b7J7nu+PTY+qVo0LsTMO1rVTUXD63gVk8QmPUwnvduk9nxraNpVP+m17BuEcls\nEsoGAAQYcmzOlnZpqhhbTnbsEayW1bMyxkLjBjXpOfBgrvyv5fU/09lP6VB20FJr\nzVPZWr5PTzaaizDDecSKgZ1ANIwXIIwWirwzDqqQb922JtcH+Ca6JJWgrV7+kDCU\ncVzwKVYievjXMCsmRSzDKEgp4n1AgrxcoaH0smD+qA+wzfsMqvEA1iTNW7zdnF0o\n6UJ9rkWxKr+JRZ5jFO+kpKQ1DxfDJZE554aO8AXzYEI=\n-----END CERTIFICATE-----\n"
    },
    "resource": {
        "enrollmentsUrl": "https://matls-api.mockbank.poc.raidiam.io/open-banking/enrollments/v2/enrollments",
        "loggedUserIdentification": "76109277673",
        "debtorAccountIspb": "12345678",
        "debtorAccountIssuer": "1774",
        "debtorAccountNumber": "94088392",
        "debtorAccountType": "CACC",
        "contractDebtorName": "Example",
        "contractDebtorIdentification": "76109277673",
        "creditorAccountIspb": "99999004",
        "creditorAccountIssuer": "0001",
        "creditorAccountNumber": "11188222",
        "creditorAccountAccountType": "SVGS",
        "creditorCpfCnpj": "50685362006773",
        "paymentAmount": "1333.00",
        "creditorName": "Ralph Bragg",
        "consentUrl": "https://matls-api.mockbank.poc.raidiam.io/open-banking/automatic-payments/v2/recurring-consents",
        "brazilOrganizationId": "74e929d9-33b6-4d85-8ba7-c146c867a817"
    },
    "consent": {
        "productType": "personal"
    },
    "directory": {
        "keystore": "https://keystore.sandbox.directory.openbankingbrasil.org.br/",
        "client_id": "c5526b0a-8a3e-473c-8bf6-c85c8d318687",
        "discoveryUrl": "https://auth.sandbox.directory.openbankingbrasil.org.br/.well-known/openid-configuration",
        "apibase": "https://matls-api.sandbox.directory.openbankingbrasil.org.br/"
    },
    "browser": [
        {
            "match": "https://auth.mockbank.poc.raidiam.io/auth*",
            "tasks": [
                {
                    "task": "Login",
                    "optional": true,
                    "match": "https://auth.mockbank.poc.raidiam.io/interaction*",
                    "commands": [
                        [
                            "text",
                            "name",
                            "username",
                            "ralph.bragg@gmail.com",
                            "optional"
                        ],
                        [
                            "text",
                            "name",
                            "password",
                            "P@ssword01",
                            "optional"
                        ],
                        [
                            "click",
                            "xpath",
                            "//button[contains(text(),\"Sign in\")]",
                            "optional"
                        ]
                    ]
                },
                {
                    "task": "Retry Login",
                    "optional": true,
                    "match": "https://auth.mockbank.poc.raidiam.io/interaction*",
                    "commands": [
                        [
                            "text",
                            "name",
                            "username",
                            "ralph.bragg@gmail.com",
                            "optional"
                        ],
                        [
                            "text",
                            "name",
                            "password",
                            "P@ssword01",
                            "optional"
                        ],
                        [
                            "click",
                            "xpath",
                            "//button[contains(text(),\"Sign in\")]",
                            "optional"
                        ]
                    ]
                },
                {
                    "task": "Consent",
                    "optional": true,
                    "match": "https://auth.mockbank.poc.raidiam.io/interaction*",
                    "commands": [
                        [
                            "wait",
                            "xpath",
                            "//*",
                            10,
                            ".*Before sharing your data, we need to confirm some information:*",
                            "update-image-placeholder-optional"
                        ],
                        [
                            "click",
                            "xpath",
                            "//label[@for='consent']/div[1]/div[1]"
                        ],
                        [
                            "click",
                            "id",
                            "consent"
                        ],
                        [
                            "click",
                            "id",
                            "continue"
                        ]
                    ]
                },
                {
                    "task": "Verify Complete",
                    "match": "*/test/*/callback*",
                    "commands": [
                        [
                            "wait",
                            "id",
                            "submission_complete",
                            10
                        ]
                    ]
                }
            ]
        }
    ]
}
```

</details>

<details>
<summary>JSON Configuration for Optimized Journey Sweeping Payments (Auto Redirect)</summary>

```
{
  "alias": "obbsb",
  "description": "phase3_v1_optimised_journey_automatic_payments",
  "server": {
    "discoveryUrl": "https://auth.mockbank.openbankingbrasil.org.br/.well-known/openid-configuration"
  },
  "directory": {
    "keystore": "https://keystore.sandbox.directory.openbankingbrasil.org.br/",
    "client_id": "984e85a9-9001-40eb-97b3-194f5afbd956"
  },
  "resource": {
    "loggedUserIdentification": "76109277673",
    "creditorName": "Ralph Bragg",
    "creditorAccountIspb": "99999004",
    "creditorAccountIssuer": "0001",
    "creditorAccountNumber": "11188222",
    "creditorAccountAccountType": "SVGS",
    "brazilCpf": "76109277673",
    "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d"
  },
  "consent": {},
  "browser": [
    {
      "match": "https://auth.mockbank.openbankingbrasil.org.br/auth*",
      "tasks": [
        {
          "task": "Login",
          "optional": true,
          "match": "https://auth.mockbank.openbankingbrasil.org.br/interaction*",
          "commands": [
            [
              "text",
              "name",
              "login",
              "ralph.bragg@gmail.com",
              "optional"
            ],
            [
              "text",
              "name",
              "password",
              "P@ssword01",
              "optional"
            ],
            [
              "click",
              "xpath",
              "//button[contains(text(),\"Sign in\")]",
              "optional"
            ]
          ]
        },
        {
          "task": "Consent",
          "optional": true,
          "match": "https://auth.mockbank.openbankingbrasil.org.br/interaction*",
          "commands": [
            [
              "wait",
              "xpath",
              "//*",
              60,
              ".*Before proceeding, we need to confirm some information:*",
              "update-image-placeholder-optional"
            ],
            [
              "click",
              "xpath",
              "//input[@id\u003d\u0027consent-toggle\u0027]/following-sibling::div[1]"
            ],
            [
              "click",
              "id",
              "continue-button"
            ]
          ]
        },
        {
          "task": "Verify Complete",
          "match": "*/test/*/callback*",
          "commands": [
            [
              "wait",
              "id",
              "submission_complete",
              10
            ]
          ]
        }
      ]
    }
  ],
  "client": {
    "jwks": {
      "keys": [
        {
          "alg": "PS256",
          "d": "Q9gSOfnkGJnAsV3a94j9ae9ihjqgMwXgVm73VTyEs1u9Jq73pCWX0e9JdeNMKdgKpiJYjyxa3ttxCY58eiGKEi7c50zYRx8YLTL2rIVWqS6JVGpXuzIQutkQDM4AfD72bG3-xT-caSCansGbdEIFJjX32Ujbs1UUoQlE96m3hNOjB5vNyHBWrBUgUGG9_uJiWFG6Lbj8ZGtiihA_PQkzuArLzDvO2OMVHCzIyQ4CwFE1tI9xHFHpioJQXBnymURQvkm3MmEwHRG_KUdABQ55gG32jothy7jOOYAMkvOCejteTZv1nT4dsEj-CBxDBtTI6SerXb11VX8b0suzSBxx0Q",
          "dp": "S15AOPpOtYgYjfOi2rNojY3NpU-Qobnfnnt_MZEJ2_DS0bGwXSgGJjHOOOAowy1HK0n7-AhXbwhr026sBuicR_Kpj6RkzGVrJug8y9R02FXZwlQpgjSBZdO6C2B1OOvtyKmnKg5q1KdQ7Kx6vYPV7UutOJn6NlH0RbFgG4NGelk",
          "dq": "oBgBMB54mtrriQCg4YyDY_zf7LW4f6oqiUl3l7odf_ArjVamjHM-boZnhGoVzZ5uXNs03wEdBIc2HLmsoGLVuodcYHjyptmvyPebiH2mavFlUlI8ILG6lkyIhMp3Ri8iXGX2MYlPjP2EawNDMHB6BO0bZ5NugyzxuF_OKhfEFLc",
          "e": "AQAB",
          "kid": "-duNE0ZX5NmDkUlgNoqDY5Ve7UdFTA7S25WJSAv8tNQ",
          "kty": "RSA",
          "n": "-6Ep5kV0qcQnrxQzbEgMGKQRHnhXlp3ZpAVqQbbzkVG_a1tHLi0V7YAmjf3isXMvdvWjApeShL32gqxgcKDvC5Mnd5ufR1ujzb5lsnYXy-tKMQWnAlCqy7mSuxi8JIBXyZb7CMGU29L32Tvd5MjDh_hSgwnHcTggE-ehqzK5eyvK7DjvlbfCKXgDx94kMcwyI2K0EurahHj9_I3lEQzAt73OocF_z84FQxO87A8Q1cM3nEGyykZPaFyulQ4bf4U2tT_Jfd0ppYX1j194ouPeqMZBsGnxKf4L4QvuberbRpdeOO92HhWHHiwiTuhYxF876-LKgPzqxK-Y1a2_4gsVAw",
          "p": "_oebNFofSe_8fdotMxUEk7n3pq5eT96rO_VPdHyTZERDrkU0djQf9BLy7DejYoRReuI0AJWkBL9EGBhECaowmx8gTCs43ffQrBDULYB4elmS07ov1pq1STqzqRKbu_INaSGVgxFzhYC_EeFVpB0RPlAUvb1_aQkH79J8VMnp2_U",
          "q": "_RVEyO9NB6XiJjMz9t6XrNxG01Vguo2VVBLaDJhoi1g7gydUDkNc9twhF1Ifps8Gf3m9aMjjOmYqE5kuWCPBHxkk8cZOm4C2AhVbQxMkZLOyPeJDfKfCi7yJRIfmwqQM5AKosALfN-jW_p746lRhCAps8eH9XF6bjugi_MH1yhc",
          "qi": "yXG_vCx0xL9DlU7f0Ixub9NSD1QJtAJYxwKyHukw_8f4rHLiZ8eeCerfZfPd7zsPGSqOmY2605MNT1Z2ohYgoRyu05uwstEDKqtgl_uxupfO6AJKCja4paIB-ICvQQXpOY1n9BW6VcDwSylTnv1pKvVnTvxzy5z008wvrafQtFw",
          "use": "sig"
        },
        {
          "kty": "RSA",
          "alg": "PS256",
          "use": "enc",
          "kid": "e96744c58188c084310920b152ffb02a392b119a009fb1fa1a656006715e1604",
          "n": "4eIXvOR1XXo3MT9syMwRZj2ChbV2Qlp_623VCIhYvPtJ5k5rlCr1hP4n0PC49U47pa3UKNs6DYHefHKm9I4h4crgk7zsln2_JP3kK1equqIO1U12Rv4Xbm_2_eqR3hPKcE3il2ky2Neby8OThFnyDwBNKdxI4MvOKm910qQhYns2L4w_i9fjF2z1Wpi6sMPW8IERhkqaBWgoaH9g2obGbNuoYCzEjOWvRb_nVjYKRPqTI2A11kWZ4mVTRkTO4yM1gdI7z8Hsl4fqlEXeVdmMkVJhRvQa-vFfegecgO8nUY2XoOUx_UR51F8PO9bepy-jH16cRDwjLE-2ex7mE_wfMw",
          "e": "AQAB",
          "d": "BqovoVF4vww8nA9IuLhnHDlDZFbHov4qZeCecQgcEJNpIxdiqDZuR4EvECsSIgOWOFvwW-lzOI1oHaVNlMvezXU5eoWpnpuEnzHlYHwCzxftNrde5PBZWHC-sAMStvBzJpLw7riNZgWFx_wNmoTQfHqgGQfLyxcB9Pf6v387qiN1wHfSXQshtFiDg_6tBaH6dS1jRAg7_56dQp1wWJeRaqMCg9QeESmo3c-76hnRSMU6fgrONU6qGMSLopv-nirh3H1gZePcXzVgf9cerRMQgV1pWUZEd_iJqTaX8U7wB0txmVF6QzRxR71Ah6nZuV_Rv7X88zB8u0rXOvjeGtuZKQ",
          "p": "8fN0GXyZnvxba4yoOgdL9ta9pkjjWVu5eTOIyvSgKf09hUSWKL6sKm1N0l68detwzBFpnxObOeUCMnU_BFhJM-s0w5GognaAX6GB5-TzdYHwmsgqAch3-_hi_kZU6A-SLZu7bQFGXTEotQ1zMxVuCMZ7AjTs0CGZrS-vItFYtik",
          "q": "7v_Ldwh3L9On2CNAefLgs7dyDBAgWrkXOJ9Z1EnrKgMHbqgq5dOixv2ezKNdOUte9G4ve555XTf2sC-p0TF9PNYC0_4KthI8NLik8RtDsQmYJUYw7qfV_YitzGflM2DRr6KaV5SmO_aPWRfzuVWh_6kIQ_GmXf47ASasKVeD_fs",
          "dp": "Jyi-_q0C9A9mAHcodxPdQJsq4LHlUf4de7dSiX6kOYeKIHqkTv3lQYylTsoUeIVdoTmkPaHfurQM8fu18k8Tsfp8dLarbkodptyt-Mk-eiNIvNRusBExEi_2Xa8maNS0VPtij1boe4bMTtlZbsgmIfd1yzqjpV_6zmPsVZdKY1k",
          "dq": "qjW-YA3FZGhmtwWUG8Wfxh41uOWbRUFgilDils_2DTuPBX363yc0XGevuqn18KH_BDGc23tnj74VkDDBzlxihvsblILuefDOs_V0csoqEWF128X7f1xEiIXY0SSFFWw0qdMx_IG_SiE0wgzO5QVZlEx7uHfXNkWjHBTAs8jCFhU",
          "qi": "8W2vDdiA8qDxL2fiJPP2m3NqbjGW7Tf5PsfGo0Gqfv6nWVweuVwsyUNT1AYduZUCvFRG5LRNHqiwZNpNB6XQln1W41GaIqGkHWJkveHhg9xIQmSK2hrX4OnSdyvMiGiB2yvce0FTgQ0OzXuNkIKJKJLP2nAJusNgNcVT7qgKCRA"
        }
      ]
    },
    "org_jwks": {
      "keys": [
        {
          "d": "BpgLagicLjysglxtDX7bJnOv4-IP-5yyGdL4oOkDCl_-lO8twPDhWLfXNCf2QTs7l1T1GLNUyALKjYDNEvjbpu03_K1dtRwO2ZS4_VHTPhe99Etn1GXntdfcFvQiD9Lz6uzs2-0DOIG_5xWUiVhTUN5HPRfMMXF3ktG2ucTOQqsJU0O2SOohVIvqYH4EDJNIw8qUsu1C2JEDMj79H_8KaXEUVx8tFFLMxmt67a_a7sImXvEaIYhUCu-DMMDrzBc660s_eTcihJ_DkJgYPPWctnmpUClKa4zgABDqGXhPQFfLS4ywGAHnLZF1MyNeKFXpmeJShjNJ5MqjBKJTnFHDQKs",
          "dp": "CFfrENWCU61YHATfdTy73lt2reMz0dBDicy92s4FqHpcup6O6f5MWGvhpBlLVC-tNA97qzyKExFwxl6c6rf45l8T6GLjy4C2DJEH0pGKeh7-PP7XW1KBvsclbJdSoSj-bOFRomFVGKYhIF3nRnr9-Dvj1k8aEcClPT1E9i9rGI7P",
          "dq": "BzCeCJQ9pKQVCpyFi50PR8_E7d9uW9nYqJpf0GBT5XdnZ44qnliLAffZmVwcxXh6e_JzIjC0ByJrYKd_dekXLCrsOex1XxqvI7WH6EZ3Nvoe_1835ZgtQ2PsPSvGKifHHPXocKyqqRdT7KlGTXfnpKtezsXPxe63VS-3coE62-_F",
          "e": "AQAB",
          "kid": "EKSYJfNcI8Bm22_dP0ziWpTjw9UceAdVjykgwO5BkfE",
          "kty": "RSA",
          "n": "oBp-b0EhezRYfisJBL_WA2Yh0Y2zPYHsy8N4G9mddkop-kFJT12XSSBx8GXmyjDL14Wg5vRNA6R_TwXbJbnHnE59uMYiWNi_G7OL6jMsncmYdyBuwl-lDWExaXC5Qg9vYgGnt7d1SthQoiJkduPIiNpniq5p7px-jJYQO4SECUqpeLl9rU_Xvxn5zpFu4dw65wBi4oSDiJ0zujQtxofOmbJCKYTWrPmd8yPlPgwIttP2ZcprMs5Ya57-99NhAealcVptRTOQTEWEOflmurq58Byu7pT64ns-9Su8JPcHMMzxOOVM7KNPuZA7Xa5-1aBd1XrhxkBHIDzUqOpanSlr2uk",
          "p": "DgL5bOQ5-JXM6Ed_3BRKW2a3EcHB_UjlWPlGGkc0RBeEwlNi6D3PQGZmgTxyGXWA4W3HMi2S2pXx8oxWd9rrw9Uc_BNrIdvkMcU9LnkCvxK-dcHalVrXhv0l1EbQx0mG9LjLsiqmJiJYnUYTuLjO8lJaebSTp-EH2fgTs81_SBKv",
          "q": "C20t29WtF9yAXt2r5Yu7chtrJUMIsu_TUY2N6p75BWWBB76oNib4Dp5fVePnbTqdSP913dS1K1vHwEAqS_Z_C6vfmaYha6Hguipo5jotTTJoYDxV_xTp1dGWcr8MltBE9ikhLa8xvGVxXjSi4vkqc_TyXlBSHbbBSZtjB32rCLHn",
          "qi": "BRx-2fqZYWrIzcayN1v10HfzcQaZue-NNZP7Eid81oBBxBrDQmiGdzQLi0BKctjLBr21_GWUgHgEYRym3He5biuDVM0WnyhXYeLLc_pv3bIG6FoPrP4XDZo4GTM4JdVj2im_OQWdXuokFzsZzeVV6H8p46TxpyNDix5oFjmyuB11",
          "alg": "PS256",
          "use": "sig"
        },
        {
          "p": "2a8fRJ7ybF-qtF1zrYzSm7z3C4wNTUMbVYqe44tR9FbKsobqW2tS0iAZf-GJ_SZPcWxkE76gunW7YqMJecGUtXsJ8TTHwjcPQOMYzxnyJu8Q4JOj01YJVrxUY9D0ZzpWM9oTAj1-qoE0w7Dy-XNUc14-HeRlmOkg2tTfrXTVR8c",
          "kty": "RSA",
          "q": "0xlPJFRUcBU5j2SKSajVnd4H5p88RSsd4cArMby1ZRuSeHEsX76c6QKAPq7uTfKrTeZic34yzAEUyHloP1fZQYQ2UQn-f6PsTAWdT1Lp5oi2VZCT0yc9-1EGnLAiUCbM9SQQyf2GIVhCiAk_0VuY6le61Pw0U4GssvFJzIrx4as",
          "d": "GxnizpWcqL1wajD8-Y-8H9-II4UZMKfkgbfwRiLK9uAd8-kEJdO9jdNeMxyytg2saDhxNTeRTkYz_VbBf3p9dGhuYx84d-ZagUbIiU3ho3FCsBRrzQQZw9OQrzPDUzp0-SBn1_GLCf9fo4ysxWHbn9euJVi2fpN_bHlBi1n8fKhdBHYE7X3XJnRYrUXItxZw5sJsqM_boONLxdLAvgmZx5CHft94JZsR6JPwlj9Ba_CuNWX_3OuUGyV0f5_1ICAEYijw9PA8KAW6t5UUYn39_KYL8nF5L1Bh6W1j8eN84I2lcKZNO6Pou064ag_wqGhk4uXuQO1IV8jRFn3-pqhSEQ",
          "e": "AQAB",
          "use": "enc",
          "kid": "c1d7b80ce4b88c4f2cfb68e7a8c45bfff355ae94259bc1a73a95ddbaeaf7c96b",
          "qi": "pU1IXwiQoFERdzJsx7kSC79Gwhak7uw7OAJCbcfkKE3GSwTWHrKfg5uDZlNvSnNU1Hbpxd0bgc40dFI2aNBML1gyDwTjQplWVJikkFix8E6z_ErSa_D5w5yV4k6CNtt7OzlMXawiZ-ndcuiOs5MkfSRyeB3k5rQmuZjLVzFFlnw",
          "dp": "Gn4dqBRQHLBn7huRgIWq_Bk7V8RrugN4yChevgKurrYBZUjWLNoa8kfF0rJ4QL7w3DT82QpSNV8utwpwlMjieFPJGfn6dcCNsq_wzQOzXNmrjClrvsSxzkSNYLiFhiqrYxQfTB5_0_B1o3tdls5acM__b1PkqX916CwQLOQTMPE",
          "alg": "PS256",
          "dq": "NS0x94fawWVHW6zK_SUvspXkzZ6dMxtaaqza9KuB0ldwvTBdKj09D6FWpvOwCiiwKG55rHhE2YkIMDwNG6_Iha2FdUKcPpEPjFL5vqq3SyBzNfi2lEFVZsKRdNUVv7UWekY8iHV53Vp7YANcdSOq0JWK9e4WTFblJyqLGaCCsAM",
          "n": "s4DcK4uxKroJPE1R7Te4ppNexbuK3C-Z3MpXFr5hmY43gYIoVMo89jE6OcDiO0Z4rxe8dsH4oYA2vAJQ0IhAaUxYMk2kN01ei761zMQWHLUPLcEKWgipYHy4AgwAUaF7-Glyb0DT1RRcY4f1tEddftxhwXZjeFduj6luVg6fVvXRIRjttybUkIKvf5ShMofVFCF_IyjYlOal4g3DVnCg62dR71WX3fRXSufxrRBG-L61rv2VSMg8pIb1DFiYKDlEXEnTdLk-7goBpTIz3wBsrZgJESSZOn_BG_-fCE0V75rheLMuJd4IGE4H0taVfEQOJKRKBVzc2jAz0sOaVuPY7Q"
        }
      ]
    },
    "client_id": "Jj-hosRwYqvtnQZNph2Ah"
  },
  "mtls": {
    "cert": "-----BEGIN CERTIFICATE-----\nMIIHQDCCBiigAwIBAgIUOyyDtirdgYQIT/eSBtvaP5JRcoswDQYJKoZIhvcNAQEL\nBQAweTELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MS0wKwYDVQQDEyRPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBJc3N1aW5nIENBIC0gRzIwHhcNMjUxMTA1MjAzMjAwWhcN\nMjYxMjA1MjAzMjAwWjCCAUoxCzAJBgNVBAYTAkJSMQswCQYDVQQIEwJVSzEPMA0G\nA1UEBxMGTE9ORE9OMSYwJAYDVQQKEx1PcGVuIEJhbmtpbmcgQnJhc2lsIC0gUmFp\nZGlhbTEtMCsGA1UECxMkYjk2MWM0ZWItNTA5ZC00ZWRmLWFmZWItMzU2NDJiMzgx\nODVkMUMwQQYDVQQDEzpodHRwczovL3dlYi5jb25mb3JtYW5jZS5kaXJlY3Rvcnku\nb3BlbmJhbmtpbmdicmFzaWwub3JnLmJyMRcwFQYDVQQFEw4wMDAwMDAxMDc0Mjg1\nMTEdMBsGA1UEDxMUUHJpdmF0ZSBPcmdhbml6YXRpb24xEzARBgsrBgEEAYI3PAIB\nAxMCVUsxNDAyBgoJkiaJk/IsZAEBEyQ5ODRlODVhOS05MDAxLTQwZWItOTdiMy0x\nOTRmNWFmYmQ5NTYwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQC8bzfe\nH4l2IegWdHsOIooz+nUxpfI5v23ubPsB0P9rLEoPlIn0A7E2zg/b7UCQFvzmzgao\n49DYEbaR5B5rutlRn52rkHufNF2fNEGXgtqrko/Uwf2tGDpve+e6MRuXhyYUEwaq\nMIRL9RCqDSTHFUS+QoNaPdccw9yAQkffEckKoXJA5GYkLvkZ06Vh8R7L6Agjh1VN\ntbT3v+STfrIbSYcEXJoHwWn7vnSewcJm3B1yxpKAVySFbL336yu0cYU8RkZ42SBh\nJmGD96kmJ+vuTXQBs5ZTndbZo6/UO+r3+qaQ8rK1r4qeEYaOwSYh9wsFxpLJIgyC\nwnl0XQQnwjQKKConAgMBAAGjggLrMIIC5zAMBgNVHRMBAf8EAjAAMB0GA1UdDgQW\nBBTLmBupVqnHkdd6f2hhj5mRrTUZnzAfBgNVHSMEGDAWgBR67wuI2HqJ4b0vBD0e\nsdbER0IoPTBZBggrBgEFBQcBAQRNMEswSQYIKwYBBQUHMAGGPWh0dHA6Ly9vY3Nw\nLnBraS1nMi5zYW5kYm94LmRpcmVjdG9yeS5vcGVuYmFua2luZ2JyYXNpbC5vcmcu\nYnIwWAYDVR0fBFEwTzBNoEugSYZHaHR0cDovL2NybC5wa2ktZzIuc2FuZGJveC5k\naXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL2lzc3Vlci5jcmwwRQYD\nVR0RBD4wPII6aHR0cHM6Ly93ZWIuY29uZm9ybWFuY2UuZGlyZWN0b3J5Lm9wZW5i\nYW5raW5nYnJhc2lsLm9yZy5icjAOBgNVHQ8BAf8EBAMCBaAwEwYDVR0lBAwwCgYI\nKwYBBQUHAwIwggF0BgNVHSAEggFrMIIBZzCCAWMGCysGAQQBg7ovcAECMIIBUjCB\n9QYIKwYBBQUHAgIwgegMgeVUaGlzIENlcnRpZmljYXRlIGlzIHNvbGVseSBmb3Ig\ndXNlIHdpdGggT3BlbiBGaW5hbmNlIEJyYXNpbCBzYW5kYm94IEFQSXMgU2Vydmlj\nZXMuIEl0cyByZWNlaXB0LCBwb3NzZXNzaW9uIG9yIHVzZSBjb25zdGl0dXRlcyBh\nY2NlcHRhbmNlIG9mIHRoZSBPcGVuIEZpbmFuY2UgQnJhc2lsIHNhbmRib3ggb2Yg\nQVBJcyBDZXJ0aWZpY2F0ZSBQb2xpY3kgYW5kIHJlbGF0ZWQgZG9jdW1lbnRzIHRo\nZXJlaW4uMFgGCCsGAQUFBwIBFkxodHRwOi8vcmVwb3NpdG9yeS5wa2ktZzIuc2Fu\nZGJveC5kaXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL3BvbGljaWVz\nMA0GCSqGSIb3DQEBCwUAA4IBAQAjJQE5R9iYGgnrEpEOUGNFVqHYs8L8Y1quoglO\nYsz1GhC2bzm7WSo7iRXfil5D8om6BDM+2TsMkvH21yeNnIclIrK/ReDHqkubbWoa\n9awJDNVa6VoNRdCB6dqEiLwZl4p+bacoShQCd113v5B76gVyCPBmId41rDJv/beB\nv7F894KM4LMMkkZGSnrGft9fc8Y2CPN452EgnTh41PhJHK8DVw8mtx704gblJ64B\nwqhogdzyAjY1uz+a3M1gTTCkEEkuhYXYrHDXgz327JRCW2oXKj7oMMszMI5E4uYL\n/QQijgFOoCPdX+/SvXZo7uMl0dtegLOR/oHxOwLuryqBk9mG\n-----END CERTIFICATE-----",
    "key": "-----BEGIN PRIVATE KEY-----\nMIIEvQIBADANBgkqhkiG9w0BAQEFAASCBKcwggSjAgEAAoIBAQC8bzfeH4l2IegW\ndHsOIooz+nUxpfI5v23ubPsB0P9rLEoPlIn0A7E2zg/b7UCQFvzmzgao49DYEbaR\n5B5rutlRn52rkHufNF2fNEGXgtqrko/Uwf2tGDpve+e6MRuXhyYUEwaqMIRL9RCq\nDSTHFUS+QoNaPdccw9yAQkffEckKoXJA5GYkLvkZ06Vh8R7L6Agjh1VNtbT3v+ST\nfrIbSYcEXJoHwWn7vnSewcJm3B1yxpKAVySFbL336yu0cYU8RkZ42SBhJmGD96km\nJ+vuTXQBs5ZTndbZo6/UO+r3+qaQ8rK1r4qeEYaOwSYh9wsFxpLJIgyCwnl0XQQn\nwjQKKConAgMBAAECggEAJwYvf0hvuu/dtVzNKUm87nPVtoEED7KV7TVTrHYgl4z2\nD5D3GvpyxoNZZHYXk1+3Y4NSfMKle0H72e3w4OWy4QUZ7bB/8aIyK2jylpKqf7Lc\nJ7c/NoxYecMi4/wMl06Nc8XW8QMYOvTXTShor/Q3JuH2ewdol9P2Q/e2E7wGszUN\n9Of74KkoQ1bGf8Z3eutjqdP35/n6cETQDoFiqsV8DfHQGCiiNPKWGD2asQDhhRx4\nvh0TGIxvWF5lnSSxvbGsNFUoGWxr8eUH/EGcH1UnHfYL4xhUYqWTEOhM2v/csmzY\nt8o4BntudmXxlfgYU3NyPKkyx7/bVcnW1PJVtoDKkQKBgQDv7j0jjaWt6dJwsKa0\n5XQ4Xga1PbpDb3LWfzZr3IScUxbVytTnOWVXpok4esn4S00iQpAp7FV3YZ/qox7p\ngcOgV7lW6CIShnLgmr4CEt1hV/sRvqddmmgfrY4ZJLy24MSxwBeZiUPNRHKl9RZA\nJr2WsM04JPE4mmf9QOpGjjy71wKBgQDJDguPpQflCGT8s2KNQjBGnWGVfdNHd1vF\nOFP79wkROAEBb2mJsuBBl8Iu3YvImaKAyAln3uqOhQ8rr+y12DqBRgoAyHY3dr46\nlhQFDonNGVdOxrwRnxajKft32W8Tn6pdjuIs4N5q23Luqym5l9PA6h8aa3E+7yeE\ncvRIfqK6MQKBgG4OjED4wpzp+rvybCXictNAXjdY3037m2PE6sPDXZkPjBP5fHus\nGk6Ad8VOncKlV/Z1Lgfs/q9KOr64oH9gJMoyMzQoOyjgP2XD1ZDB8oaqguJ63+7R\n2x1c0Se7cE07AT6/7JNjIZTQ5v41VEWM/75Vz20HlRbvzO+gjVZb/IP1AoGANJwd\nQFhByZe5vTo/dpE0SrYR++kx6Qh9lgzYRR1uXPgXo0WBC0woTGGmqVbFphc1o5c0\nht6Y5/Q/dQIS4b6UCJHIOk46SOckffYZhP0559ZSt0VfnwjPBqEMsV7PJwZnsRWb\nb3zkFngYCgX15B+rhFZ/Dw3AU2SHJaxi6blhYXECgYEAnBAJuYoIfZolppeUZXwp\nAYoTLGMtXnjvX/YFumlEWzjnXLo4Lk9L+lO9sV5BwhQ6klNBARy5TjAedr+Kw0ee\noGh8F964pkF4jy7qBLMkf4/jaEvft/2tg16ELOj74llsd5GPA8Pgzeh1AXtlowwi\nC1Ere9RQ/zspggyX1uEakrI\u003d\n-----END PRIVATE KEY-----\n",
    "ca": "-----BEGIN CERTIFICATE-----\nMIIHFDCCBPygAwIBAgIUZJOYHaqMZR7leKm8iaKrR380T8QwDQYJKoZIhvcNAQEN\nBQAwdjELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MSowKAYDVQQDEyFPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBSb290IENBIC0gRzIwHhcNMjMwMzA5MTQzNjAwWhcNMzMw\nMzA2MTQzNjAwWjB5MQswCQYDVQQGEwJCUjEcMBoGA1UEChMTT3BlbiBGaW5hbmNl\nIEJyYXNpbDEdMBsGA1UECxMUT3BlbiBGaW5hbmNlIHNhbmRib3gxLTArBgNVBAMT\nJE9wZW4gRmluYW5jZSBzYW5kYm94IElzc3VpbmcgQ0EgLSBHMjCCASIwDQYJKoZI\nhvcNAQEBBQADggEPADCCAQoCggEBAJJZYsafIn0x1j8WLDfJ3HSXt65NqnKwGdcW\nn4z4VqdrvcIl6kJM7cjF3ImaN5SLideuK63/QP4tgGilZxooxLE8V8M/uPgGU74K\noTMBuDho6sND/UtHsr/wgkX9+/Kn50vdLbhXZBmvcL+5gtXKDQGR+d1LyaU8EigX\nkhvegMCSyW72PlQ9FetapanOpH0e5+osGRVI9ysm7PFrWE6UOs8EA/d6+v8SwHTW\nbD6iVVgtGnQtm0C4w4H6VVNnFE0F8pSnXQQPzQXMONIFi/UZPSB00H0qnxRvWkw3\nJa7QErS8hdMPGUHQ9N/RujhMhf7tlUArcgod6mc+SYfcI3j1pUcCAwEAAaOCApUw\nggKRMA4GA1UdDwEB/wQEAwIBBjASBgNVHRMBAf8ECDAGAQH/AgEAMB0GA1UdDgQW\nBBR67wuI2HqJ4b0vBD0esdbER0IoPTAfBgNVHSMEGDAWgBQVb9vsej3AhKXXgbWR\nvfmoWNM++jBZBggrBgEFBQcBAQRNMEswSQYIKwYBBQUHMAGGPWh0dHA6Ly9vY3Nw\nLnBraS1nMi5zYW5kYm94LmRpcmVjdG9yeS5vcGVuYmFua2luZ2JyYXNpbC5vcmcu\nYnIwWAYDVR0fBFEwTzBNoEugSYZHaHR0cDovL2NybC5wa2ktZzIuc2FuZGJveC5k\naXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL2lzc3Vlci5jcmwwggF0\nBgNVHSAEggFrMIIBZzCCAWMGCysGAQQBg7ovcAECMIIBUjCB9QYIKwYBBQUHAgIw\ngegMgeVUaGlzIENlcnRpZmljYXRlIGlzIHNvbGVseSBmb3IgdXNlIHdpdGggT3Bl\nbiBGaW5hbmNlIEJyYXNpbCBzYW5kYm94IEFQSXMgU2VydmljZXMuIEl0cyByZWNl\naXB0LCBwb3NzZXNzaW9uIG9yIHVzZSBjb25zdGl0dXRlcyBhY2NlcHRhbmNlIG9m\nIHRoZSBPcGVuIEZpbmFuY2UgQnJhc2lsIHNhbmRib3ggb2YgQVBJcyBDZXJ0aWZp\nY2F0ZSBQb2xpY3kgYW5kIHJlbGF0ZWQgZG9jdW1lbnRzIHRoZXJlaW4uMFgGCCsG\nAQUFBwIBFkxodHRwOi8vcmVwb3NpdG9yeS5wa2ktZzIuc2FuZGJveC5kaXJlY3Rv\ncnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL3BvbGljaWVzMA0GCSqGSIb3DQEB\nDQUAA4ICAQCANeSAlmJy3e9rrgTGShVCyMQhy68j3cAJyFzqCutyNMGHUgFOjAgD\nzIUQZmAepTDJdhJF+BoruBfAIJUr6tD9EBw2MZXiTLHZG9mqtGwsMbeI3o3R9Y3G\nEpGp72jIHw7mtUZdoaWcmgqxCWn6UT9bBKAkdt6KyRepPUy1YI59MZxpVOs5J0s2\nQFd3FRCNxdzgsuGqdxTb1Gre4I5E1vJWcp1Fe/kPdaOgPVC89M6uk3WYTnMNZ20N\n8K0ecXy8+E3K+to35berWn16g1ZrufylX6s2yyxcsUnh5KP1smFd8MePekKIW0SD\n8hqD1MtGQEmzdWrPCT9fZUzONj4VuDcl/vgfKUBsBszTmqwGF34G+663v10KUhga\nkCiIOZtkT9B+aESGAfczQiFO1h4cI52TKwEptfbplrFS2gILrzleqv0JoDDFYVhY\nV5AVDjqeHaniClCi10JdSN11LqNdagpyojN2a2WhVSAigIT3yDeqozlzjgPui/1E\nDt0zBkXd5uFDwNeLUwOribuS3hxVG5Bg73ZJl+UV3ZuAzFFCfkVBz6BeqUusf8+P\n3pqAQ4gzhSWNsTBIsjaVV8ZU8IqxKhBkRUSNjihG2kM8kX9knQvRbCBuuse/dDUe\n4cUJ+wT1omVgq+TWhShOAjsHEa233omXbH7v5igLBEkzzqmM5cAv8Q\u003d\u003d\n-----END CERTIFICATE-----\n-----BEGIN CERTIFICATE-----\nMIIFvDCCA6SgAwIBAgIUKhBUxL5Dt4w3xH1V3X1n+x/e3hcwDQYJKoZIhvcNAQEN\nBQAwdjELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MSowKAYDVQQDEyFPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBSb290IENBIC0gRzIwHhcNMjMwMzA5MTQzNjAwWhcNMzgw\nMzA1MTQzNjAwWjB2MQswCQYDVQQGEwJCUjEcMBoGA1UEChMTT3BlbiBGaW5hbmNl\nIEJyYXNpbDEdMBsGA1UECxMUT3BlbiBGaW5hbmNlIHNhbmRib3gxKjAoBgNVBAMT\nIU9wZW4gRmluYW5jZSBzYW5kYm94IFJvb3QgQ0EgLSBHMjCCAiIwDQYJKoZIhvcN\nAQEBBQADggIPADCCAgoCggIBALJFBgmKj3iDF3C8+8smNNQDxLFA9kCcca1iaxQf\nvMI/FKGW2ullHhH+W3EGEajn39QOlccGyrfCONHLqMW53+HAMtwiIvcrJgj72V7D\nnYflO3aaCFwoC31PL1+pMBo88F6jvezZ8BlRnheT7urCs6+onhz8pm0cVNc77U5X\npi8IOJz1QFKecJnFLjG0NiLCzOzjLSo0A8Rue9K/H5fjq+PqKdXG94AoQyFUwlsU\ny4aXbylDz1kRiOSnOlRNPcY/su95pFKQbGgaZZ1fLf89i5PtHAUu92FbD7H7OyYX\nXpZ97La0d7cUH0A4nb+LpOd/f0c8lAN2Ya1B8aKvWiF23q3c8EoAJyhrdkHKe6yI\nYvLC5G5jkbJefeQcp34IgD8T+Tn3aBF7YgmlYUMbnsuokBG28Hr50EAklCclA0bb\n4pmf8nE6y7VQ0CM/bNZd1F9AjxLukkyvkrOD6A6uv+c5KeC+da245dBzsyhiKe9R\nRX5Gkf7NSkDu9b9YkdDaWV6LXxpUA0SmdT9M16yK3XPDKOWBI4gVSB1KuwrOcal/\ndMwFUlxvqdGugRbxDNNukxa0l3JztGg6XYLjEiiYrQ+7HChbUVNlM0l0VZAz4eON\ngYrq2ExUDWlQXiES389/Qz3R3yDk9ib1YsMHwAux2ulCssFVn4EgtnYFfgf3o01J\n3CedAgMBAAGjQjBAMA4GA1UdDwEB/wQEAwIBBjAPBgNVHRMBAf8EBTADAQH/MB0G\nA1UdDgQWBBQVb9vsej3AhKXXgbWRvfmoWNM++jANBgkqhkiG9w0BAQ0FAAOCAgEA\nVPrUd4UDjOhkxOzSN4bMr0cULZJwQPRV8aj99tzdv8Ef44CwLVkLmm7Z2d1uRA9l\n7xbK6W8L1oL95iV4K4o2u4+ZFG7mrOfU2T2wgTfMlIxHDoAxS49flUYkBpQI1Wj4\nJBZ6fKGFVH6PyIio0I2Mx2u80ZX6lPYQ2q4DR6eBUoNt8T8XSWpD4TjroFbOVIp+\nN84alBca/pvW2aF2HwPndrL/Y++HZp3TpdUeBUT757KOZ7hdwf30pxd8qNn8+peb\nbP2h6b9pjKAmS8ciBExJzchhQWJRP6LIdvexTsBQ1HLxlZNrlg66wYT0kuVVzRTa\n0qRvIjQ0ntmhy2DtmE5VFT9O8ahcQL5Ddk8B4dhiy59vjALS6kIUXJ6GCobzRUsQ\na7b7J7nu+PTY+qVo0LsTMO1rVTUXD63gVk8QmPUwnvduk9nxraNpVP+m17BuEcls\nEsoGAAQYcmzOlnZpqhhbTnbsEayW1bMyxkLjBjXpOfBgrvyv5fU/09lP6VB20FJr\nzVPZWr5PTzaaizDDecSKgZ1ANIwXIIwWirwzDqqQb922JtcH+Ca6JJWgrV7+kDCU\ncVzwKVYievjXMCsmRSzDKEgp4n1AgrxcoaH0smD+qA+wzfsMqvEA1iTNW7zdnF0o\n6UJ9rkWxKr+JRZ5jFO+kpKQ1DxfDJZE554aO8AXzYEI\u003d\n-----END CERTIFICATE-----\n"
  }
}
```

</details>

<details>
<summary>JSON Configuration for Optimised Journey (Auto Redirect)</summary>

```
{
  "alias": "obbsb",
  "description": "phase3_v1_optimised_journey",
  "server": {
    "discoveryUrl": "https://auth.mockbank.openbankingbrasil.org.br/.well-known/openid-configuration"
  },
  "directory": {
    "keystore": "https://keystore.sandbox.directory.openbankingbrasil.org.br/",
    "client_id": "984e85a9-9001-40eb-97b3-194f5afbd956"
  },
  "resource": {
    "loggedUserIdentification": "76109277673",
    "creditorName": "Ralph Bragg",
    "creditorAccountIspb": "99999004",
    "creditorAccountIssuer": "0001",
    "creditorAccountNumber": "11188222",
    "creditorAccountAccountType": "SVGS",
    "brazilCpf": "76109277673",
    "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
    "contractDebtorName": "Example",
    "contractDebtorIdentification": "76109277673",
    "businessEntityIdentification": "50685362006773"
  },
  "consent": {},
  "browser": [
    {
      "match": "https://auth.mockbank.openbankingbrasil.org.br/auth*",
      "tasks": [
        {
          "task": "Login",
          "optional": true,
          "match": "https://auth.mockbank.openbankingbrasil.org.br/interaction*",
          "commands": [
            [
              "text",
              "name",
              "login",
              "ralph.bragg@gmail.com",
              "optional"
            ],
            [
              "text",
              "name",
              "password",
              "P@ssword01",
              "optional"
            ],
            [
              "click",
              "xpath",
              "//button[contains(text(),\"Sign in\")]",
              "optional"
            ]
          ]
        },
        {
          "task": "Consent",
          "optional": true,
          "match": "https://auth.mockbank.openbankingbrasil.org.br/interaction*",
          "commands": [
            [
              "wait",
              "xpath",
              "//*",
              60,
              ".*Before proceeding, we need to confirm some information:*",
              "update-image-placeholder-optional"
            ],
            [
              "click",
              "xpath",
              "//input[@id\u003d\u0027consent-toggle\u0027]/following-sibling::div[1]"
            ],
            [
              "click",
              "id",
              "continue-button"
            ]
          ]
        },
        {
          "task": "Verify Complete",
          "match": "*/test/*/callback*",
          "commands": [
            [
              "wait",
              "id",
              "submission_complete",
              10
            ]
          ]
        }
      ]
    }
  ],
  "client": {
    "jwks": {
      "keys": [
        {
          "alg": "PS256",
          "d": "Q9gSOfnkGJnAsV3a94j9ae9ihjqgMwXgVm73VTyEs1u9Jq73pCWX0e9JdeNMKdgKpiJYjyxa3ttxCY58eiGKEi7c50zYRx8YLTL2rIVWqS6JVGpXuzIQutkQDM4AfD72bG3-xT-caSCansGbdEIFJjX32Ujbs1UUoQlE96m3hNOjB5vNyHBWrBUgUGG9_uJiWFG6Lbj8ZGtiihA_PQkzuArLzDvO2OMVHCzIyQ4CwFE1tI9xHFHpioJQXBnymURQvkm3MmEwHRG_KUdABQ55gG32jothy7jOOYAMkvOCejteTZv1nT4dsEj-CBxDBtTI6SerXb11VX8b0suzSBxx0Q",
          "dp": "S15AOPpOtYgYjfOi2rNojY3NpU-Qobnfnnt_MZEJ2_DS0bGwXSgGJjHOOOAowy1HK0n7-AhXbwhr026sBuicR_Kpj6RkzGVrJug8y9R02FXZwlQpgjSBZdO6C2B1OOvtyKmnKg5q1KdQ7Kx6vYPV7UutOJn6NlH0RbFgG4NGelk",
          "dq": "oBgBMB54mtrriQCg4YyDY_zf7LW4f6oqiUl3l7odf_ArjVamjHM-boZnhGoVzZ5uXNs03wEdBIc2HLmsoGLVuodcYHjyptmvyPebiH2mavFlUlI8ILG6lkyIhMp3Ri8iXGX2MYlPjP2EawNDMHB6BO0bZ5NugyzxuF_OKhfEFLc",
          "e": "AQAB",
          "kid": "-duNE0ZX5NmDkUlgNoqDY5Ve7UdFTA7S25WJSAv8tNQ",
          "kty": "RSA",
          "n": "-6Ep5kV0qcQnrxQzbEgMGKQRHnhXlp3ZpAVqQbbzkVG_a1tHLi0V7YAmjf3isXMvdvWjApeShL32gqxgcKDvC5Mnd5ufR1ujzb5lsnYXy-tKMQWnAlCqy7mSuxi8JIBXyZb7CMGU29L32Tvd5MjDh_hSgwnHcTggE-ehqzK5eyvK7DjvlbfCKXgDx94kMcwyI2K0EurahHj9_I3lEQzAt73OocF_z84FQxO87A8Q1cM3nEGyykZPaFyulQ4bf4U2tT_Jfd0ppYX1j194ouPeqMZBsGnxKf4L4QvuberbRpdeOO92HhWHHiwiTuhYxF876-LKgPzqxK-Y1a2_4gsVAw",
          "p": "_oebNFofSe_8fdotMxUEk7n3pq5eT96rO_VPdHyTZERDrkU0djQf9BLy7DejYoRReuI0AJWkBL9EGBhECaowmx8gTCs43ffQrBDULYB4elmS07ov1pq1STqzqRKbu_INaSGVgxFzhYC_EeFVpB0RPlAUvb1_aQkH79J8VMnp2_U",
          "q": "_RVEyO9NB6XiJjMz9t6XrNxG01Vguo2VVBLaDJhoi1g7gydUDkNc9twhF1Ifps8Gf3m9aMjjOmYqE5kuWCPBHxkk8cZOm4C2AhVbQxMkZLOyPeJDfKfCi7yJRIfmwqQM5AKosALfN-jW_p746lRhCAps8eH9XF6bjugi_MH1yhc",
          "qi": "yXG_vCx0xL9DlU7f0Ixub9NSD1QJtAJYxwKyHukw_8f4rHLiZ8eeCerfZfPd7zsPGSqOmY2605MNT1Z2ohYgoRyu05uwstEDKqtgl_uxupfO6AJKCja4paIB-ICvQQXpOY1n9BW6VcDwSylTnv1pKvVnTvxzy5z008wvrafQtFw",
          "use": "sig"
        },
        {
          "kty": "RSA",
          "alg": "PS256",
          "use": "enc",
          "kid": "e96744c58188c084310920b152ffb02a392b119a009fb1fa1a656006715e1604",
          "n": "4eIXvOR1XXo3MT9syMwRZj2ChbV2Qlp_623VCIhYvPtJ5k5rlCr1hP4n0PC49U47pa3UKNs6DYHefHKm9I4h4crgk7zsln2_JP3kK1equqIO1U12Rv4Xbm_2_eqR3hPKcE3il2ky2Neby8OThFnyDwBNKdxI4MvOKm910qQhYns2L4w_i9fjF2z1Wpi6sMPW8IERhkqaBWgoaH9g2obGbNuoYCzEjOWvRb_nVjYKRPqTI2A11kWZ4mVTRkTO4yM1gdI7z8Hsl4fqlEXeVdmMkVJhRvQa-vFfegecgO8nUY2XoOUx_UR51F8PO9bepy-jH16cRDwjLE-2ex7mE_wfMw",
          "e": "AQAB",
          "d": "BqovoVF4vww8nA9IuLhnHDlDZFbHov4qZeCecQgcEJNpIxdiqDZuR4EvECsSIgOWOFvwW-lzOI1oHaVNlMvezXU5eoWpnpuEnzHlYHwCzxftNrde5PBZWHC-sAMStvBzJpLw7riNZgWFx_wNmoTQfHqgGQfLyxcB9Pf6v387qiN1wHfSXQshtFiDg_6tBaH6dS1jRAg7_56dQp1wWJeRaqMCg9QeESmo3c-76hnRSMU6fgrONU6qGMSLopv-nirh3H1gZePcXzVgf9cerRMQgV1pWUZEd_iJqTaX8U7wB0txmVF6QzRxR71Ah6nZuV_Rv7X88zB8u0rXOvjeGtuZKQ",
          "p": "8fN0GXyZnvxba4yoOgdL9ta9pkjjWVu5eTOIyvSgKf09hUSWKL6sKm1N0l68detwzBFpnxObOeUCMnU_BFhJM-s0w5GognaAX6GB5-TzdYHwmsgqAch3-_hi_kZU6A-SLZu7bQFGXTEotQ1zMxVuCMZ7AjTs0CGZrS-vItFYtik",
          "q": "7v_Ldwh3L9On2CNAefLgs7dyDBAgWrkXOJ9Z1EnrKgMHbqgq5dOixv2ezKNdOUte9G4ve555XTf2sC-p0TF9PNYC0_4KthI8NLik8RtDsQmYJUYw7qfV_YitzGflM2DRr6KaV5SmO_aPWRfzuVWh_6kIQ_GmXf47ASasKVeD_fs",
          "dp": "Jyi-_q0C9A9mAHcodxPdQJsq4LHlUf4de7dSiX6kOYeKIHqkTv3lQYylTsoUeIVdoTmkPaHfurQM8fu18k8Tsfp8dLarbkodptyt-Mk-eiNIvNRusBExEi_2Xa8maNS0VPtij1boe4bMTtlZbsgmIfd1yzqjpV_6zmPsVZdKY1k",
          "dq": "qjW-YA3FZGhmtwWUG8Wfxh41uOWbRUFgilDils_2DTuPBX363yc0XGevuqn18KH_BDGc23tnj74VkDDBzlxihvsblILuefDOs_V0csoqEWF128X7f1xEiIXY0SSFFWw0qdMx_IG_SiE0wgzO5QVZlEx7uHfXNkWjHBTAs8jCFhU",
          "qi": "8W2vDdiA8qDxL2fiJPP2m3NqbjGW7Tf5PsfGo0Gqfv6nWVweuVwsyUNT1AYduZUCvFRG5LRNHqiwZNpNB6XQln1W41GaIqGkHWJkveHhg9xIQmSK2hrX4OnSdyvMiGiB2yvce0FTgQ0OzXuNkIKJKJLP2nAJusNgNcVT7qgKCRA"
        }
      ]
    },
    "org_jwks": {
      "keys": [
        {
          "d": "BpgLagicLjysglxtDX7bJnOv4-IP-5yyGdL4oOkDCl_-lO8twPDhWLfXNCf2QTs7l1T1GLNUyALKjYDNEvjbpu03_K1dtRwO2ZS4_VHTPhe99Etn1GXntdfcFvQiD9Lz6uzs2-0DOIG_5xWUiVhTUN5HPRfMMXF3ktG2ucTOQqsJU0O2SOohVIvqYH4EDJNIw8qUsu1C2JEDMj79H_8KaXEUVx8tFFLMxmt67a_a7sImXvEaIYhUCu-DMMDrzBc660s_eTcihJ_DkJgYPPWctnmpUClKa4zgABDqGXhPQFfLS4ywGAHnLZF1MyNeKFXpmeJShjNJ5MqjBKJTnFHDQKs",
          "dp": "CFfrENWCU61YHATfdTy73lt2reMz0dBDicy92s4FqHpcup6O6f5MWGvhpBlLVC-tNA97qzyKExFwxl6c6rf45l8T6GLjy4C2DJEH0pGKeh7-PP7XW1KBvsclbJdSoSj-bOFRomFVGKYhIF3nRnr9-Dvj1k8aEcClPT1E9i9rGI7P",
          "dq": "BzCeCJQ9pKQVCpyFi50PR8_E7d9uW9nYqJpf0GBT5XdnZ44qnliLAffZmVwcxXh6e_JzIjC0ByJrYKd_dekXLCrsOex1XxqvI7WH6EZ3Nvoe_1835ZgtQ2PsPSvGKifHHPXocKyqqRdT7KlGTXfnpKtezsXPxe63VS-3coE62-_F",
          "e": "AQAB",
          "kid": "EKSYJfNcI8Bm22_dP0ziWpTjw9UceAdVjykgwO5BkfE",
          "kty": "RSA",
          "n": "oBp-b0EhezRYfisJBL_WA2Yh0Y2zPYHsy8N4G9mddkop-kFJT12XSSBx8GXmyjDL14Wg5vRNA6R_TwXbJbnHnE59uMYiWNi_G7OL6jMsncmYdyBuwl-lDWExaXC5Qg9vYgGnt7d1SthQoiJkduPIiNpniq5p7px-jJYQO4SECUqpeLl9rU_Xvxn5zpFu4dw65wBi4oSDiJ0zujQtxofOmbJCKYTWrPmd8yPlPgwIttP2ZcprMs5Ya57-99NhAealcVptRTOQTEWEOflmurq58Byu7pT64ns-9Su8JPcHMMzxOOVM7KNPuZA7Xa5-1aBd1XrhxkBHIDzUqOpanSlr2uk",
          "p": "DgL5bOQ5-JXM6Ed_3BRKW2a3EcHB_UjlWPlGGkc0RBeEwlNi6D3PQGZmgTxyGXWA4W3HMi2S2pXx8oxWd9rrw9Uc_BNrIdvkMcU9LnkCvxK-dcHalVrXhv0l1EbQx0mG9LjLsiqmJiJYnUYTuLjO8lJaebSTp-EH2fgTs81_SBKv",
          "q": "C20t29WtF9yAXt2r5Yu7chtrJUMIsu_TUY2N6p75BWWBB76oNib4Dp5fVePnbTqdSP913dS1K1vHwEAqS_Z_C6vfmaYha6Hguipo5jotTTJoYDxV_xTp1dGWcr8MltBE9ikhLa8xvGVxXjSi4vkqc_TyXlBSHbbBSZtjB32rCLHn",
          "qi": "BRx-2fqZYWrIzcayN1v10HfzcQaZue-NNZP7Eid81oBBxBrDQmiGdzQLi0BKctjLBr21_GWUgHgEYRym3He5biuDVM0WnyhXYeLLc_pv3bIG6FoPrP4XDZo4GTM4JdVj2im_OQWdXuokFzsZzeVV6H8p46TxpyNDix5oFjmyuB11",
          "alg": "PS256",
          "use": "sig"
        },
        {
          "p": "2a8fRJ7ybF-qtF1zrYzSm7z3C4wNTUMbVYqe44tR9FbKsobqW2tS0iAZf-GJ_SZPcWxkE76gunW7YqMJecGUtXsJ8TTHwjcPQOMYzxnyJu8Q4JOj01YJVrxUY9D0ZzpWM9oTAj1-qoE0w7Dy-XNUc14-HeRlmOkg2tTfrXTVR8c",
          "kty": "RSA",
          "q": "0xlPJFRUcBU5j2SKSajVnd4H5p88RSsd4cArMby1ZRuSeHEsX76c6QKAPq7uTfKrTeZic34yzAEUyHloP1fZQYQ2UQn-f6PsTAWdT1Lp5oi2VZCT0yc9-1EGnLAiUCbM9SQQyf2GIVhCiAk_0VuY6le61Pw0U4GssvFJzIrx4as",
          "d": "GxnizpWcqL1wajD8-Y-8H9-II4UZMKfkgbfwRiLK9uAd8-kEJdO9jdNeMxyytg2saDhxNTeRTkYz_VbBf3p9dGhuYx84d-ZagUbIiU3ho3FCsBRrzQQZw9OQrzPDUzp0-SBn1_GLCf9fo4ysxWHbn9euJVi2fpN_bHlBi1n8fKhdBHYE7X3XJnRYrUXItxZw5sJsqM_boONLxdLAvgmZx5CHft94JZsR6JPwlj9Ba_CuNWX_3OuUGyV0f5_1ICAEYijw9PA8KAW6t5UUYn39_KYL8nF5L1Bh6W1j8eN84I2lcKZNO6Pou064ag_wqGhk4uXuQO1IV8jRFn3-pqhSEQ",
          "e": "AQAB",
          "use": "enc",
          "kid": "c1d7b80ce4b88c4f2cfb68e7a8c45bfff355ae94259bc1a73a95ddbaeaf7c96b",
          "qi": "pU1IXwiQoFERdzJsx7kSC79Gwhak7uw7OAJCbcfkKE3GSwTWHrKfg5uDZlNvSnNU1Hbpxd0bgc40dFI2aNBML1gyDwTjQplWVJikkFix8E6z_ErSa_D5w5yV4k6CNtt7OzlMXawiZ-ndcuiOs5MkfSRyeB3k5rQmuZjLVzFFlnw",
          "dp": "Gn4dqBRQHLBn7huRgIWq_Bk7V8RrugN4yChevgKurrYBZUjWLNoa8kfF0rJ4QL7w3DT82QpSNV8utwpwlMjieFPJGfn6dcCNsq_wzQOzXNmrjClrvsSxzkSNYLiFhiqrYxQfTB5_0_B1o3tdls5acM__b1PkqX916CwQLOQTMPE",
          "alg": "PS256",
          "dq": "NS0x94fawWVHW6zK_SUvspXkzZ6dMxtaaqza9KuB0ldwvTBdKj09D6FWpvOwCiiwKG55rHhE2YkIMDwNG6_Iha2FdUKcPpEPjFL5vqq3SyBzNfi2lEFVZsKRdNUVv7UWekY8iHV53Vp7YANcdSOq0JWK9e4WTFblJyqLGaCCsAM",
          "n": "s4DcK4uxKroJPE1R7Te4ppNexbuK3C-Z3MpXFr5hmY43gYIoVMo89jE6OcDiO0Z4rxe8dsH4oYA2vAJQ0IhAaUxYMk2kN01ei761zMQWHLUPLcEKWgipYHy4AgwAUaF7-Glyb0DT1RRcY4f1tEddftxhwXZjeFduj6luVg6fVvXRIRjttybUkIKvf5ShMofVFCF_IyjYlOal4g3DVnCg62dR71WX3fRXSufxrRBG-L61rv2VSMg8pIb1DFiYKDlEXEnTdLk-7goBpTIz3wBsrZgJESSZOn_BG_-fCE0V75rheLMuJd4IGE4H0taVfEQOJKRKBVzc2jAz0sOaVuPY7Q"
        }
      ]
    },
    "client_id": "Jj-hosRwYqvtnQZNph2Ah"
  },
  "mtls": {
    "cert": "-----BEGIN CERTIFICATE-----\nMIIHQDCCBiigAwIBAgIUOyyDtirdgYQIT/eSBtvaP5JRcoswDQYJKoZIhvcNAQEL\nBQAweTELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MS0wKwYDVQQDEyRPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBJc3N1aW5nIENBIC0gRzIwHhcNMjUxMTA1MjAzMjAwWhcN\nMjYxMjA1MjAzMjAwWjCCAUoxCzAJBgNVBAYTAkJSMQswCQYDVQQIEwJVSzEPMA0G\nA1UEBxMGTE9ORE9OMSYwJAYDVQQKEx1PcGVuIEJhbmtpbmcgQnJhc2lsIC0gUmFp\nZGlhbTEtMCsGA1UECxMkYjk2MWM0ZWItNTA5ZC00ZWRmLWFmZWItMzU2NDJiMzgx\nODVkMUMwQQYDVQQDEzpodHRwczovL3dlYi5jb25mb3JtYW5jZS5kaXJlY3Rvcnku\nb3BlbmJhbmtpbmdicmFzaWwub3JnLmJyMRcwFQYDVQQFEw4wMDAwMDAxMDc0Mjg1\nMTEdMBsGA1UEDxMUUHJpdmF0ZSBPcmdhbml6YXRpb24xEzARBgsrBgEEAYI3PAIB\nAxMCVUsxNDAyBgoJkiaJk/IsZAEBEyQ5ODRlODVhOS05MDAxLTQwZWItOTdiMy0x\nOTRmNWFmYmQ5NTYwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQC8bzfe\nH4l2IegWdHsOIooz+nUxpfI5v23ubPsB0P9rLEoPlIn0A7E2zg/b7UCQFvzmzgao\n49DYEbaR5B5rutlRn52rkHufNF2fNEGXgtqrko/Uwf2tGDpve+e6MRuXhyYUEwaq\nMIRL9RCqDSTHFUS+QoNaPdccw9yAQkffEckKoXJA5GYkLvkZ06Vh8R7L6Agjh1VN\ntbT3v+STfrIbSYcEXJoHwWn7vnSewcJm3B1yxpKAVySFbL336yu0cYU8RkZ42SBh\nJmGD96kmJ+vuTXQBs5ZTndbZo6/UO+r3+qaQ8rK1r4qeEYaOwSYh9wsFxpLJIgyC\nwnl0XQQnwjQKKConAgMBAAGjggLrMIIC5zAMBgNVHRMBAf8EAjAAMB0GA1UdDgQW\nBBTLmBupVqnHkdd6f2hhj5mRrTUZnzAfBgNVHSMEGDAWgBR67wuI2HqJ4b0vBD0e\nsdbER0IoPTBZBggrBgEFBQcBAQRNMEswSQYIKwYBBQUHMAGGPWh0dHA6Ly9vY3Nw\nLnBraS1nMi5zYW5kYm94LmRpcmVjdG9yeS5vcGVuYmFua2luZ2JyYXNpbC5vcmcu\nYnIwWAYDVR0fBFEwTzBNoEugSYZHaHR0cDovL2NybC5wa2ktZzIuc2FuZGJveC5k\naXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL2lzc3Vlci5jcmwwRQYD\nVR0RBD4wPII6aHR0cHM6Ly93ZWIuY29uZm9ybWFuY2UuZGlyZWN0b3J5Lm9wZW5i\nYW5raW5nYnJhc2lsLm9yZy5icjAOBgNVHQ8BAf8EBAMCBaAwEwYDVR0lBAwwCgYI\nKwYBBQUHAwIwggF0BgNVHSAEggFrMIIBZzCCAWMGCysGAQQBg7ovcAECMIIBUjCB\n9QYIKwYBBQUHAgIwgegMgeVUaGlzIENlcnRpZmljYXRlIGlzIHNvbGVseSBmb3Ig\ndXNlIHdpdGggT3BlbiBGaW5hbmNlIEJyYXNpbCBzYW5kYm94IEFQSXMgU2Vydmlj\nZXMuIEl0cyByZWNlaXB0LCBwb3NzZXNzaW9uIG9yIHVzZSBjb25zdGl0dXRlcyBh\nY2NlcHRhbmNlIG9mIHRoZSBPcGVuIEZpbmFuY2UgQnJhc2lsIHNhbmRib3ggb2Yg\nQVBJcyBDZXJ0aWZpY2F0ZSBQb2xpY3kgYW5kIHJlbGF0ZWQgZG9jdW1lbnRzIHRo\nZXJlaW4uMFgGCCsGAQUFBwIBFkxodHRwOi8vcmVwb3NpdG9yeS5wa2ktZzIuc2Fu\nZGJveC5kaXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL3BvbGljaWVz\nMA0GCSqGSIb3DQEBCwUAA4IBAQAjJQE5R9iYGgnrEpEOUGNFVqHYs8L8Y1quoglO\nYsz1GhC2bzm7WSo7iRXfil5D8om6BDM+2TsMkvH21yeNnIclIrK/ReDHqkubbWoa\n9awJDNVa6VoNRdCB6dqEiLwZl4p+bacoShQCd113v5B76gVyCPBmId41rDJv/beB\nv7F894KM4LMMkkZGSnrGft9fc8Y2CPN452EgnTh41PhJHK8DVw8mtx704gblJ64B\nwqhogdzyAjY1uz+a3M1gTTCkEEkuhYXYrHDXgz327JRCW2oXKj7oMMszMI5E4uYL\n/QQijgFOoCPdX+/SvXZo7uMl0dtegLOR/oHxOwLuryqBk9mG\n-----END CERTIFICATE-----",
    "key": "-----BEGIN PRIVATE KEY-----\nMIIEvQIBADANBgkqhkiG9w0BAQEFAASCBKcwggSjAgEAAoIBAQC8bzfeH4l2IegW\ndHsOIooz+nUxpfI5v23ubPsB0P9rLEoPlIn0A7E2zg/b7UCQFvzmzgao49DYEbaR\n5B5rutlRn52rkHufNF2fNEGXgtqrko/Uwf2tGDpve+e6MRuXhyYUEwaqMIRL9RCq\nDSTHFUS+QoNaPdccw9yAQkffEckKoXJA5GYkLvkZ06Vh8R7L6Agjh1VNtbT3v+ST\nfrIbSYcEXJoHwWn7vnSewcJm3B1yxpKAVySFbL336yu0cYU8RkZ42SBhJmGD96km\nJ+vuTXQBs5ZTndbZo6/UO+r3+qaQ8rK1r4qeEYaOwSYh9wsFxpLJIgyCwnl0XQQn\nwjQKKConAgMBAAECggEAJwYvf0hvuu/dtVzNKUm87nPVtoEED7KV7TVTrHYgl4z2\nD5D3GvpyxoNZZHYXk1+3Y4NSfMKle0H72e3w4OWy4QUZ7bB/8aIyK2jylpKqf7Lc\nJ7c/NoxYecMi4/wMl06Nc8XW8QMYOvTXTShor/Q3JuH2ewdol9P2Q/e2E7wGszUN\n9Of74KkoQ1bGf8Z3eutjqdP35/n6cETQDoFiqsV8DfHQGCiiNPKWGD2asQDhhRx4\nvh0TGIxvWF5lnSSxvbGsNFUoGWxr8eUH/EGcH1UnHfYL4xhUYqWTEOhM2v/csmzY\nt8o4BntudmXxlfgYU3NyPKkyx7/bVcnW1PJVtoDKkQKBgQDv7j0jjaWt6dJwsKa0\n5XQ4Xga1PbpDb3LWfzZr3IScUxbVytTnOWVXpok4esn4S00iQpAp7FV3YZ/qox7p\ngcOgV7lW6CIShnLgmr4CEt1hV/sRvqddmmgfrY4ZJLy24MSxwBeZiUPNRHKl9RZA\nJr2WsM04JPE4mmf9QOpGjjy71wKBgQDJDguPpQflCGT8s2KNQjBGnWGVfdNHd1vF\nOFP79wkROAEBb2mJsuBBl8Iu3YvImaKAyAln3uqOhQ8rr+y12DqBRgoAyHY3dr46\nlhQFDonNGVdOxrwRnxajKft32W8Tn6pdjuIs4N5q23Luqym5l9PA6h8aa3E+7yeE\ncvRIfqK6MQKBgG4OjED4wpzp+rvybCXictNAXjdY3037m2PE6sPDXZkPjBP5fHus\nGk6Ad8VOncKlV/Z1Lgfs/q9KOr64oH9gJMoyMzQoOyjgP2XD1ZDB8oaqguJ63+7R\n2x1c0Se7cE07AT6/7JNjIZTQ5v41VEWM/75Vz20HlRbvzO+gjVZb/IP1AoGANJwd\nQFhByZe5vTo/dpE0SrYR++kx6Qh9lgzYRR1uXPgXo0WBC0woTGGmqVbFphc1o5c0\nht6Y5/Q/dQIS4b6UCJHIOk46SOckffYZhP0559ZSt0VfnwjPBqEMsV7PJwZnsRWb\nb3zkFngYCgX15B+rhFZ/Dw3AU2SHJaxi6blhYXECgYEAnBAJuYoIfZolppeUZXwp\nAYoTLGMtXnjvX/YFumlEWzjnXLo4Lk9L+lO9sV5BwhQ6klNBARy5TjAedr+Kw0ee\noGh8F964pkF4jy7qBLMkf4/jaEvft/2tg16ELOj74llsd5GPA8Pgzeh1AXtlowwi\nC1Ere9RQ/zspggyX1uEakrI\u003d\n-----END PRIVATE KEY-----\n",
    "ca": "-----BEGIN CERTIFICATE-----\nMIIHFDCCBPygAwIBAgIUZJOYHaqMZR7leKm8iaKrR380T8QwDQYJKoZIhvcNAQEN\nBQAwdjELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MSowKAYDVQQDEyFPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBSb290IENBIC0gRzIwHhcNMjMwMzA5MTQzNjAwWhcNMzMw\nMzA2MTQzNjAwWjB5MQswCQYDVQQGEwJCUjEcMBoGA1UEChMTT3BlbiBGaW5hbmNl\nIEJyYXNpbDEdMBsGA1UECxMUT3BlbiBGaW5hbmNlIHNhbmRib3gxLTArBgNVBAMT\nJE9wZW4gRmluYW5jZSBzYW5kYm94IElzc3VpbmcgQ0EgLSBHMjCCASIwDQYJKoZI\nhvcNAQEBBQADggEPADCCAQoCggEBAJJZYsafIn0x1j8WLDfJ3HSXt65NqnKwGdcW\nn4z4VqdrvcIl6kJM7cjF3ImaN5SLideuK63/QP4tgGilZxooxLE8V8M/uPgGU74K\noTMBuDho6sND/UtHsr/wgkX9+/Kn50vdLbhXZBmvcL+5gtXKDQGR+d1LyaU8EigX\nkhvegMCSyW72PlQ9FetapanOpH0e5+osGRVI9ysm7PFrWE6UOs8EA/d6+v8SwHTW\nbD6iVVgtGnQtm0C4w4H6VVNnFE0F8pSnXQQPzQXMONIFi/UZPSB00H0qnxRvWkw3\nJa7QErS8hdMPGUHQ9N/RujhMhf7tlUArcgod6mc+SYfcI3j1pUcCAwEAAaOCApUw\nggKRMA4GA1UdDwEB/wQEAwIBBjASBgNVHRMBAf8ECDAGAQH/AgEAMB0GA1UdDgQW\nBBR67wuI2HqJ4b0vBD0esdbER0IoPTAfBgNVHSMEGDAWgBQVb9vsej3AhKXXgbWR\nvfmoWNM++jBZBggrBgEFBQcBAQRNMEswSQYIKwYBBQUHMAGGPWh0dHA6Ly9vY3Nw\nLnBraS1nMi5zYW5kYm94LmRpcmVjdG9yeS5vcGVuYmFua2luZ2JyYXNpbC5vcmcu\nYnIwWAYDVR0fBFEwTzBNoEugSYZHaHR0cDovL2NybC5wa2ktZzIuc2FuZGJveC5k\naXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL2lzc3Vlci5jcmwwggF0\nBgNVHSAEggFrMIIBZzCCAWMGCysGAQQBg7ovcAECMIIBUjCB9QYIKwYBBQUHAgIw\ngegMgeVUaGlzIENlcnRpZmljYXRlIGlzIHNvbGVseSBmb3IgdXNlIHdpdGggT3Bl\nbiBGaW5hbmNlIEJyYXNpbCBzYW5kYm94IEFQSXMgU2VydmljZXMuIEl0cyByZWNl\naXB0LCBwb3NzZXNzaW9uIG9yIHVzZSBjb25zdGl0dXRlcyBhY2NlcHRhbmNlIG9m\nIHRoZSBPcGVuIEZpbmFuY2UgQnJhc2lsIHNhbmRib3ggb2YgQVBJcyBDZXJ0aWZp\nY2F0ZSBQb2xpY3kgYW5kIHJlbGF0ZWQgZG9jdW1lbnRzIHRoZXJlaW4uMFgGCCsG\nAQUFBwIBFkxodHRwOi8vcmVwb3NpdG9yeS5wa2ktZzIuc2FuZGJveC5kaXJlY3Rv\ncnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL3BvbGljaWVzMA0GCSqGSIb3DQEB\nDQUAA4ICAQCANeSAlmJy3e9rrgTGShVCyMQhy68j3cAJyFzqCutyNMGHUgFOjAgD\nzIUQZmAepTDJdhJF+BoruBfAIJUr6tD9EBw2MZXiTLHZG9mqtGwsMbeI3o3R9Y3G\nEpGp72jIHw7mtUZdoaWcmgqxCWn6UT9bBKAkdt6KyRepPUy1YI59MZxpVOs5J0s2\nQFd3FRCNxdzgsuGqdxTb1Gre4I5E1vJWcp1Fe/kPdaOgPVC89M6uk3WYTnMNZ20N\n8K0ecXy8+E3K+to35berWn16g1ZrufylX6s2yyxcsUnh5KP1smFd8MePekKIW0SD\n8hqD1MtGQEmzdWrPCT9fZUzONj4VuDcl/vgfKUBsBszTmqwGF34G+663v10KUhga\nkCiIOZtkT9B+aESGAfczQiFO1h4cI52TKwEptfbplrFS2gILrzleqv0JoDDFYVhY\nV5AVDjqeHaniClCi10JdSN11LqNdagpyojN2a2WhVSAigIT3yDeqozlzjgPui/1E\nDt0zBkXd5uFDwNeLUwOribuS3hxVG5Bg73ZJl+UV3ZuAzFFCfkVBz6BeqUusf8+P\n3pqAQ4gzhSWNsTBIsjaVV8ZU8IqxKhBkRUSNjihG2kM8kX9knQvRbCBuuse/dDUe\n4cUJ+wT1omVgq+TWhShOAjsHEa233omXbH7v5igLBEkzzqmM5cAv8Q\u003d\u003d\n-----END CERTIFICATE-----\n-----BEGIN CERTIFICATE-----\nMIIFvDCCA6SgAwIBAgIUKhBUxL5Dt4w3xH1V3X1n+x/e3hcwDQYJKoZIhvcNAQEN\nBQAwdjELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MSowKAYDVQQDEyFPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBSb290IENBIC0gRzIwHhcNMjMwMzA5MTQzNjAwWhcNMzgw\nMzA1MTQzNjAwWjB2MQswCQYDVQQGEwJCUjEcMBoGA1UEChMTT3BlbiBGaW5hbmNl\nIEJyYXNpbDEdMBsGA1UECxMUT3BlbiBGaW5hbmNlIHNhbmRib3gxKjAoBgNVBAMT\nIU9wZW4gRmluYW5jZSBzYW5kYm94IFJvb3QgQ0EgLSBHMjCCAiIwDQYJKoZIhvcN\nAQEBBQADggIPADCCAgoCggIBALJFBgmKj3iDF3C8+8smNNQDxLFA9kCcca1iaxQf\nvMI/FKGW2ullHhH+W3EGEajn39QOlccGyrfCONHLqMW53+HAMtwiIvcrJgj72V7D\nnYflO3aaCFwoC31PL1+pMBo88F6jvezZ8BlRnheT7urCs6+onhz8pm0cVNc77U5X\npi8IOJz1QFKecJnFLjG0NiLCzOzjLSo0A8Rue9K/H5fjq+PqKdXG94AoQyFUwlsU\ny4aXbylDz1kRiOSnOlRNPcY/su95pFKQbGgaZZ1fLf89i5PtHAUu92FbD7H7OyYX\nXpZ97La0d7cUH0A4nb+LpOd/f0c8lAN2Ya1B8aKvWiF23q3c8EoAJyhrdkHKe6yI\nYvLC5G5jkbJefeQcp34IgD8T+Tn3aBF7YgmlYUMbnsuokBG28Hr50EAklCclA0bb\n4pmf8nE6y7VQ0CM/bNZd1F9AjxLukkyvkrOD6A6uv+c5KeC+da245dBzsyhiKe9R\nRX5Gkf7NSkDu9b9YkdDaWV6LXxpUA0SmdT9M16yK3XPDKOWBI4gVSB1KuwrOcal/\ndMwFUlxvqdGugRbxDNNukxa0l3JztGg6XYLjEiiYrQ+7HChbUVNlM0l0VZAz4eON\ngYrq2ExUDWlQXiES389/Qz3R3yDk9ib1YsMHwAux2ulCssFVn4EgtnYFfgf3o01J\n3CedAgMBAAGjQjBAMA4GA1UdDwEB/wQEAwIBBjAPBgNVHRMBAf8EBTADAQH/MB0G\nA1UdDgQWBBQVb9vsej3AhKXXgbWRvfmoWNM++jANBgkqhkiG9w0BAQ0FAAOCAgEA\nVPrUd4UDjOhkxOzSN4bMr0cULZJwQPRV8aj99tzdv8Ef44CwLVkLmm7Z2d1uRA9l\n7xbK6W8L1oL95iV4K4o2u4+ZFG7mrOfU2T2wgTfMlIxHDoAxS49flUYkBpQI1Wj4\nJBZ6fKGFVH6PyIio0I2Mx2u80ZX6lPYQ2q4DR6eBUoNt8T8XSWpD4TjroFbOVIp+\nN84alBca/pvW2aF2HwPndrL/Y++HZp3TpdUeBUT757KOZ7hdwf30pxd8qNn8+peb\nbP2h6b9pjKAmS8ciBExJzchhQWJRP6LIdvexTsBQ1HLxlZNrlg66wYT0kuVVzRTa\n0qRvIjQ0ntmhy2DtmE5VFT9O8ahcQL5Ddk8B4dhiy59vjALS6kIUXJ6GCobzRUsQ\na7b7J7nu+PTY+qVo0LsTMO1rVTUXD63gVk8QmPUwnvduk9nxraNpVP+m17BuEcls\nEsoGAAQYcmzOlnZpqhhbTnbsEayW1bMyxkLjBjXpOfBgrvyv5fU/09lP6VB20FJr\nzVPZWr5PTzaaizDDecSKgZ1ANIwXIIwWirwzDqqQb922JtcH+Ca6JJWgrV7+kDCU\ncVzwKVYievjXMCsmRSzDKEgp4n1AgrxcoaH0smD+qA+wzfsMqvEA1iTNW7zdnF0o\n6UJ9rkWxKr+JRZ5jFO+kpKQ1DxfDJZE554aO8AXzYEI\u003d\n-----END CERTIFICATE-----\n"
  }
}
```

</details>

<details>
<summary>JSON Configuration for Payments v5 APDN/APES (Auto Redirect)</summary>

```
{
  "alias": "obbsb",
  "description": "Phase 3 Payments v5 - pipeline",
  "server": {
    "discoveryUrl": "https://auth.mockbank.openbankingbrasil.org.br/.well-known/openid-configuration"
  },
  "directory": {
    "discoveryUrl": "https://auth.sandbox.directory.openbankingbrasil.org.br/.well-known/openid-configuration",
    "apibase": "https://matls-api.sandbox.directory.openbankingbrasil.org.br/",
    "keystore": "https://keystore.sandbox.directory.openbankingbrasil.org.br/",
    "client_id": "984e85a9-9001-40eb-97b3-194f5afbd956"
  },
  "resource": {
    "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
    "brazilPaymentConsent": {
      "data": {
        "loggedUser": {
          "document": {
            "identification": "76109277673",
            "rel": "CPF"
          }
        },
        "creditor": {
          "personType": "PESSOA_NATURAL",
          "cpfCnpj": "48847377765",
          "name": "Marco Antonio de Brito"
        },
        "payment": {
          "type": "PIX",
          "date": "2021-01-01",
          "currency": "BRL",
          "amount": "1333.00",
          "details": {
            "localInstrument": "DICT",
            "proxy": "12345678901",
            "creditorAccount": {
              "ispb": "12345678",
              "issuer": "1774",
              "number": "1234567890",
              "accountType": "CACC"
            }
          }
        },
        "debtorAccount": {
          "ispb": "12345678",
          "issuer": "6272",
          "number": "94088392",
          "accountType": "CACC"
        }
      }
    },
    "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
    "brazilQrdnPaymentConsent": {
      "data": {
        "loggedUser": {
          "document": {
            "identification": "76109277673",
            "rel": "CPF"
          }
        },
        "creditor": {
          "personType": "PESSOA_NATURAL",
          "cpfCnpj": "48847377765",
          "name": "Marco Antonio de Brito"
        },
        "payment": {
          "type": "PIX",
          "date": "2021-01-01",
          "currency": "BRL",
          "amount": "1333.00",
          "igbeTownCode": "3106200",
          "details": {
            "localInstrument": "QRDN",
            "proxy": "cliente-a00001@pix.bcb.gov.br",
            "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
            "creditorAccount": {
              "ispb": "12345678",
              "issuer": "1774",
              "number": "1234567890",
              "accountType": "CACC"
            }
          }
        },
        "debtorAccount": {
          "ispb": "12345678",
          "issuer": "6272",
          "number": "94088392",
          "accountType": "CACC"
        }
      }
    },
    "brazilApdnPaymentConsent": {
      "data": {
        "loggedUser": {
          "document": {
            "identification": "76109277673",
            "rel": "CPF"
          }
        },
        "creditor": {
          "personType": "PESSOA_NATURAL",
          "cpfCnpj": "48847377765",
          "name": "Marco Antonio de Brito"
        },
        "payment": {
          "type": "PIX",
          "purpose": "IMMEDIATE",
          "date": "2026-04-02",
          "currency": "BRL",
          "amount": "100.00",
          "ibgeTownCode": "3106200",
          "details": {
            "localInstrument": "APDN",
            "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
            "proxy": "cliente-a00001@pix.bcb.gov.br",
            "payloadJWS": "header.payload.signature",
            "creditorAccount": {
              "ispb": "12345678",
              "issuer": "1774",
              "number": "1234567890",
              "accountType": "CACC"
            }
          }
        }
      }
    },
    "brazilQrdnCnpj": "43142666000197",
    "brazilApdnCnpj": "43142666000197",
    "loggedUserIdentification": "76109277673",
    "debtorAccountIspb": "12345678",
    "debtorAccountIssuer": "1774",
    "debtorAccountNumber": "94088392",
    "debtorAccountType": "CACC",
    "paymentAmount": "1333.00",
    "transactionIdentifier": "E00038166201907261559y6j6A"
  },
  "conditionalResources": {
    "brazilCpfTemporization": "76109277673"
  },
  "consent": {},
  "browser": [
    {
      "match": "https://auth.mockbank.openbankingbrasil.org.br/auth*",
      "tasks": [
        {
          "task": "Login",
          "optional": true,
          "match": "https://auth.mockbank.openbankingbrasil.org.br/interaction*",
          "commands": [
            [
              "text",
              "name",
              "login",
              "ralph.bragg@gmail.com",
              "optional"
            ],
            [
              "text",
              "name",
              "password",
              "P@ssword01",
              "optional"
            ],
            [
              "click",
              "xpath",
              "//button[contains(text(),\"Sign in\")]",
              "optional"
            ]
          ]
        },
        {
          "task": "Consent",
          "optional": true,
          "match": "https://auth.mockbank.openbankingbrasil.org.br/interaction*",
          "commands": [
            [
              "wait",
              "xpath",
              "//*",
              60,
              ".*Before proceeding, we need to confirm some information:*",
              "update-image-placeholder-optional"
            ],
            [
              "click",
              "xpath",
              "//input[@id='consent-toggle']/following-sibling::div[1]"
            ],
            [
              "click",
              "id",
              "continue-button"
            ]
          ]
        },
        {
          "task": "Verify Complete",
          "match": "*/test/*/callback*",
          "commands": [
            [
              "wait",
              "id",
              "submission_complete",
              10
            ]
          ]
        }
      ]
    }
  ],
  "client": {
    "jwks": {
      "keys": [
        {
          "alg": "PS256",
          "d": "Q9gSOfnkGJnAsV3a94j9ae9ihjqgMwXgVm73VTyEs1u9Jq73pCWX0e9JdeNMKdgKpiJYjyxa3ttxCY58eiGKEi7c50zYRx8YLTL2rIVWqS6JVGpXuzIQutkQDM4AfD72bG3-xT-caSCansGbdEIFJjX32Ujbs1UUoQlE96m3hNOjB5vNyHBWrBUgUGG9_uJiWFG6Lbj8ZGtiihA_PQkzuArLzDvO2OMVHCzIyQ4CwFE1tI9xHFHpioJQXBnymURQvkm3MmEwHRG_KUdABQ55gG32jothy7jOOYAMkvOCejteTZv1nT4dsEj-CBxDBtTI6SerXb11VX8b0suzSBxx0Q",
          "dp": "S15AOPpOtYgYjfOi2rNojY3NpU-Qobnfnnt_MZEJ2_DS0bGwXSgGJjHOOOAowy1HK0n7-AhXbwhr026sBuicR_Kpj6RkzGVrJug8y9R02FXZwlQpgjSBZdO6C2B1OOvtyKmnKg5q1KdQ7Kx6vYPV7UutOJn6NlH0RbFgG4NGelk",
          "dq": "oBgBMB54mtrriQCg4YyDY_zf7LW4f6oqiUl3l7odf_ArjVamjHM-boZnhGoVzZ5uXNs03wEdBIc2HLmsoGLVuodcYHjyptmvyPebiH2mavFlUlI8ILG6lkyIhMp3Ri8iXGX2MYlPjP2EawNDMHB6BO0bZ5NugyzxuF_OKhfEFLc",
          "e": "AQAB",
          "kid": "-duNE0ZX5NmDkUlgNoqDY5Ve7UdFTA7S25WJSAv8tNQ",
          "kty": "RSA",
          "n": "-6Ep5kV0qcQnrxQzbEgMGKQRHnhXlp3ZpAVqQbbzkVG_a1tHLi0V7YAmjf3isXMvdvWjApeShL32gqxgcKDvC5Mnd5ufR1ujzb5lsnYXy-tKMQWnAlCqy7mSuxi8JIBXyZb7CMGU29L32Tvd5MjDh_hSgwnHcTggE-ehqzK5eyvK7DjvlbfCKXgDx94kMcwyI2K0EurahHj9_I3lEQzAt73OocF_z84FQxO87A8Q1cM3nEGyykZPaFyulQ4bf4U2tT_Jfd0ppYX1j194ouPeqMZBsGnxKf4L4QvuberbRpdeOO92HhWHHiwiTuhYxF876-LKgPzqxK-Y1a2_4gsVAw",
          "p": "_oebNFofSe_8fdotMxUEk7n3pq5eT96rO_VPdHyTZERDrkU0djQf9BLy7DejYoRReuI0AJWkBL9EGBhECaowmx8gTCs43ffQrBDULYB4elmS07ov1pq1STqzqRKbu_INaSGVgxFzhYC_EeFVpB0RPlAUvb1_aQkH79J8VMnp2_U",
          "q": "_RVEyO9NB6XiJjMz9t6XrNxG01Vguo2VVBLaDJhoi1g7gydUDkNc9twhF1Ifps8Gf3m9aMjjOmYqE5kuWCPBHxkk8cZOm4C2AhVbQxMkZLOyPeJDfKfCi7yJRIfmwqQM5AKosALfN-jW_p746lRhCAps8eH9XF6bjugi_MH1yhc",
          "qi": "yXG_vCx0xL9DlU7f0Ixub9NSD1QJtAJYxwKyHukw_8f4rHLiZ8eeCerfZfPd7zsPGSqOmY2605MNT1Z2ohYgoRyu05uwstEDKqtgl_uxupfO6AJKCja4paIB-ICvQQXpOY1n9BW6VcDwSylTnv1pKvVnTvxzy5z008wvrafQtFw",
          "use": "sig"
        },
        {
          "kty": "RSA",
          "alg": "PS256",
          "use": "enc",
          "kid": "e96744c58188c084310920b152ffb02a392b119a009fb1fa1a656006715e1604",
          "n": "4eIXvOR1XXo3MT9syMwRZj2ChbV2Qlp_623VCIhYvPtJ5k5rlCr1hP4n0PC49U47pa3UKNs6DYHefHKm9I4h4crgk7zsln2_JP3kK1equqIO1U12Rv4Xbm_2_eqR3hPKcE3il2ky2Neby8OThFnyDwBNKdxI4MvOKm910qQhYns2L4w_i9fjF2z1Wpi6sMPW8IERhkqaBWgoaH9g2obGbNuoYCzEjOWvRb_nVjYKRPqTI2A11kWZ4mVTRkTO4yM1gdI7z8Hsl4fqlEXeVdmMkVJhRvQa-vFfegecgO8nUY2XoOUx_UR51F8PO9bepy-jH16cRDwjLE-2ex7mE_wfMw",
          "e": "AQAB",
          "d": "BqovoVF4vww8nA9IuLhnHDlDZFbHov4qZeCecQgcEJNpIxdiqDZuR4EvECsSIgOWOFvwW-lzOI1oHaVNlMvezXU5eoWpnpuEnzHlYHwCzxftNrde5PBZWHC-sAMStvBzJpLw7riNZgWFx_wNmoTQfHqgGQfLyxcB9Pf6v387qiN1wHfSXQshtFiDg_6tBaH6dS1jRAg7_56dQp1wWJeRaqMCg9QeESmo3c-76hnRSMU6fgrONU6qGMSLopv-nirh3H1gZePcXzVgf9cerRMQgV1pWUZEd_iJqTaX8U7wB0txmVF6QzRxR71Ah6nZuV_Rv7X88zB8u0rXOvjeGtuZKQ",
          "p": "8fN0GXyZnvxba4yoOgdL9ta9pkjjWVu5eTOIyvSgKf09hUSWKL6sKm1N0l68detwzBFpnxObOeUCMnU_BFhJM-s0w5GognaAX6GB5-TzdYHwmsgqAch3-_hi_kZU6A-SLZu7bQFGXTEotQ1zMxVuCMZ7AjTs0CGZrS-vItFYtik",
          "q": "7v_Ldwh3L9On2CNAefLgs7dyDBAgWrkXOJ9Z1EnrKgMHbqgq5dOixv2ezKNdOUte9G4ve555XTf2sC-p0TF9PNYC0_4KthI8NLik8RtDsQmYJUYw7qfV_YitzGflM2DRr6KaV5SmO_aPWRfzuVWh_6kIQ_GmXf47ASasKVeD_fs",
          "dp": "Jyi-_q0C9A9mAHcodxPdQJsq4LHlUf4de7dSiX6kOYeKIHqkTv3lQYylTsoUeIVdoTmkPaHfurQM8fu18k8Tsfp8dLarbkodptyt-Mk-eiNIvNRusBExEi_2Xa8maNS0VPtij1boe4bMTtlZbsgmIfd1yzqjpV_6zmPsVZdKY1k",
          "dq": "qjW-YA3FZGhmtwWUG8Wfxh41uOWbRUFgilDils_2DTuPBX363yc0XGevuqn18KH_BDGc23tnj74VkDDBzlxihvsblILuefDOs_V0csoqEWF128X7f1xEiIXY0SSFFWw0qdMx_IG_SiE0wgzO5QVZlEx7uHfXNkWjHBTAs8jCFhU",
          "qi": "8W2vDdiA8qDxL2fiJPP2m3NqbjGW7Tf5PsfGo0Gqfv6nWVweuVwsyUNT1AYduZUCvFRG5LRNHqiwZNpNB6XQln1W41GaIqGkHWJkveHhg9xIQmSK2hrX4OnSdyvMiGiB2yvce0FTgQ0OzXuNkIKJKJLP2nAJusNgNcVT7qgKCRA"
        }
      ]
    },
    "org_jwks": {
      "keys": [
        {
          "d": "BpgLagicLjysglxtDX7bJnOv4-IP-5yyGdL4oOkDCl_-lO8twPDhWLfXNCf2QTs7l1T1GLNUyALKjYDNEvjbpu03_K1dtRwO2ZS4_VHTPhe99Etn1GXntdfcFvQiD9Lz6uzs2-0DOIG_5xWUiVhTUN5HPRfMMXF3ktG2ucTOQqsJU0O2SOohVIvqYH4EDJNIw8qUsu1C2JEDMj79H_8KaXEUVx8tFFLMxmt67a_a7sImXvEaIYhUCu-DMMDrzBc660s_eTcihJ_DkJgYPPWctnmpUClKa4zgABDqGXhPQFfLS4ywGAHnLZF1MyNeKFXpmeJShjNJ5MqjBKJTnFHDQKs",
          "dp": "CFfrENWCU61YHATfdTy73lt2reMz0dBDicy92s4FqHpcup6O6f5MWGvhpBlLVC-tNA97qzyKExFwxl6c6rf45l8T6GLjy4C2DJEH0pGKeh7-PP7XW1KBvsclbJdSoSj-bOFRomFVGKYhIF3nRnr9-Dvj1k8aEcClPT1E9i9rGI7P",
          "dq": "BzCeCJQ9pKQVCpyFi50PR8_E7d9uW9nYqJpf0GBT5XdnZ44qnliLAffZmVwcxXh6e_JzIjC0ByJrYKd_dekXLCrsOex1XxqvI7WH6EZ3Nvoe_1835ZgtQ2PsPSvGKifHHPXocKyqqRdT7KlGTXfnpKtezsXPxe63VS-3coE62-_F",
          "e": "AQAB",
          "kid": "EKSYJfNcI8Bm22_dP0ziWpTjw9UceAdVjykgwO5BkfE",
          "kty": "RSA",
          "n": "oBp-b0EhezRYfisJBL_WA2Yh0Y2zPYHsy8N4G9mddkop-kFJT12XSSBx8GXmyjDL14Wg5vRNA6R_TwXbJbnHnE59uMYiWNi_G7OL6jMsncmYdyBuwl-lDWExaXC5Qg9vYgGnt7d1SthQoiJkduPIiNpniq5p7px-jJYQO4SECUqpeLl9rU_Xvxn5zpFu4dw65wBi4oSDiJ0zujQtxofOmbJCKYTWrPmd8yPlPgwIttP2ZcprMs5Ya57-99NhAealcVptRTOQTEWEOflmurq58Byu7pT64ns-9Su8JPcHMMzxOOVM7KNPuZA7Xa5-1aBd1XrhxkBHIDzUqOpanSlr2uk",
          "p": "DgL5bOQ5-JXM6Ed_3BRKW2a3EcHB_UjlWPlGGkc0RBeEwlNi6D3PQGZmgTxyGXWA4W3HMi2S2pXx8oxWd9rrw9Uc_BNrIdvkMcU9LnkCvxK-dcHalVrXhv0l1EbQx0mG9LjLsiqmJiJYnUYTuLjO8lJaebSTp-EH2fgTs81_SBKv",
          "q": "C20t29WtF9yAXt2r5Yu7chtrJUMIsu_TUY2N6p75BWWBB76oNib4Dp5fVePnbTqdSP913dS1K1vHwEAqS_Z_C6vfmaYha6Hguipo5jotTTJoYDxV_xTp1dGWcr8MltBE9ikhLa8xvGVxXjSi4vkqc_TyXlBSHbbBSZtjB32rCLHn",
          "qi": "BRx-2fqZYWrIzcayN1v10HfzcQaZue-NNZP7Eid81oBBxBrDQmiGdzQLi0BKctjLBr21_GWUgHgEYRym3He5biuDVM0WnyhXYeLLc_pv3bIG6FoPrP4XDZo4GTM4JdVj2im_OQWdXuokFzsZzeVV6H8p46TxpyNDix5oFjmyuB11",
          "alg": "PS256",
          "use": "sig"
        },
        {
          "p": "2a8fRJ7ybF-qtF1zrYzSm7z3C4wNTUMbVYqe44tR9FbKsobqW2tS0iAZf-GJ_SZPcWxkE76gunW7YqMJecGUtXsJ8TTHwjcPQOMYzxnyJu8Q4JOj01YJVrxUY9D0ZzpWM9oTAj1-qoE0w7Dy-XNUc14-HeRlmOkg2tTfrXTVR8c",
          "kty": "RSA",
          "q": "0xlPJFRUcBU5j2SKSajVnd4H5p88RSsd4cArMby1ZRuSeHEsX76c6QKAPq7uTfKrTeZic34yzAEUyHloP1fZQYQ2UQn-f6PsTAWdT1Lp5oi2VZCT0yc9-1EGnLAiUCbM9SQQyf2GIVhCiAk_0VuY6le61Pw0U4GssvFJzIrx4as",
          "d": "GxnizpWcqL1wajD8-Y-8H9-II4UZMKfkgbfwRiLK9uAd8-kEJdO9jdNeMxyytg2saDhxNTeRTkYz_VbBf3p9dGhuYx84d-ZagUbIiU3ho3FCsBRrzQQZw9OQrzPDUzp0-SBn1_GLCf9fo4ysxWHbn9euJVi2fpN_bHlBi1n8fKhdBHYE7X3XJnRYrUXItxZw5sJsqM_boONLxdLAvgmZx5CHft94JZsR6JPwlj9Ba_CuNWX_3OuUGyV0f5_1ICAEYijw9PA8KAW6t5UUYn39_KYL8nF5L1Bh6W1j8eN84I2lcKZNO6Pou064ag_wqGhk4uXuQO1IV8jRFn3-pqhSEQ",
          "e": "AQAB",
          "use": "enc",
          "kid": "c1d7b80ce4b88c4f2cfb68e7a8c45bfff355ae94259bc1a73a95ddbaeaf7c96b",
          "qi": "pU1IXwiQoFERdzJsx7kSC79Gwhak7uw7OAJCbcfkKE3GSwTWHrKfg5uDZlNvSnNU1Hbpxd0bgc40dFI2aNBML1gyDwTjQplWVJikkFix8E6z_ErSa_D5w5yV4k6CNtt7OzlMXawiZ-ndcuiOs5MkfSRyeB3k5rQmuZjLVzFFlnw",
          "dp": "Gn4dqBRQHLBn7huRgIWq_Bk7V8RrugN4yChevgKurrYBZUjWLNoa8kfF0rJ4QL7w3DT82QpSNV8utwpwlMjieFPJGfn6dcCNsq_wzQOzXNmrjClrvsSxzkSNYLiFhiqrYxQfTB5_0_B1o3tdls5acM__b1PkqX916CwQLOQTMPE",
          "alg": "PS256",
          "dq": "NS0x94fawWVHW6zK_SUvspXkzZ6dMxtaaqza9KuB0ldwvTBdKj09D6FWpvOwCiiwKG55rHhE2YkIMDwNG6_Iha2FdUKcPpEPjFL5vqq3SyBzNfi2lEFVZsKRdNUVv7UWekY8iHV53Vp7YANcdSOq0JWK9e4WTFblJyqLGaCCsAM",
          "n": "s4DcK4uxKroJPE1R7Te4ppNexbuK3C-Z3MpXFr5hmY43gYIoVMo89jE6OcDiO0Z4rxe8dsH4oYA2vAJQ0IhAaUxYMk2kN01ei761zMQWHLUPLcEKWgipYHy4AgwAUaF7-Glyb0DT1RRcY4f1tEddftxhwXZjeFduj6luVg6fVvXRIRjttybUkIKvf5ShMofVFCF_IyjYlOal4g3DVnCg62dR71WX3fRXSufxrRBG-L61rv2VSMg8pIb1DFiYKDlEXEnTdLk-7goBpTIz3wBsrZgJESSZOn_BG_-fCE0V75rheLMuJd4IGE4H0taVfEQOJKRKBVzc2jAz0sOaVuPY7Q"
        }
      ]
    },
    "client_id": "Jj-hosRwYqvtnQZNph2Ah"
  },
  "mtls": {
    "cert": "-----BEGIN CERTIFICATE-----\nMIIHQDCCBiigAwIBAgIUOyyDtirdgYQIT/eSBtvaP5JRcoswDQYJKoZIhvcNAQEL\nBQAweTELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MS0wKwYDVQQDEyRPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBJc3N1aW5nIENBIC0gRzIwHhcNMjUxMTA1MjAzMjAwWhcN\nMjYxMjA1MjAzMjAwWjCCAUoxCzAJBgNVBAYTAkJSMQswCQYDVQQIEwJVSzEPMA0G\nA1UEBxMGTE9ORE9OMSYwJAYDVQQKEx1PcGVuIEJhbmtpbmcgQnJhc2lsIC0gUmFp\nZGlhbTEtMCsGA1UECxMkYjk2MWM0ZWItNTA5ZC00ZWRmLWFmZWItMzU2NDJiMzgx\nODVkMUMwQQYDVQQDEzpodHRwczovL3dlYi5jb25mb3JtYW5jZS5kaXJlY3Rvcnku\nb3BlbmJhbmtpbmdicmFzaWwub3JnLmJyMRcwFQYDVQQFEw4wMDAwMDAxMDc0Mjg1\nMTEdMBsGA1UEDxMUUHJpdmF0ZSBPcmdhbml6YXRpb24xEzARBgsrBgEEAYI3PAIB\nAxMCVUsxNDAyBgoJkiaJk/IsZAEBEyQ5ODRlODVhOS05MDAxLTQwZWItOTdiMy0x\nOTRmNWFmYmQ5NTYwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQC8bzfe\nH4l2IegWdHsOIooz+nUxpfI5v23ubPsB0P9rLEoPlIn0A7E2zg/b7UCQFvzmzgao\n49DYEbaR5B5rutlRn52rkHufNF2fNEGXgtqrko/Uwf2tGDpve+e6MRuXhyYUEwaq\nMIRL9RCqDSTHFUS+QoNaPdccw9yAQkffEckKoXJA5GYkLvkZ06Vh8R7L6Agjh1VN\ntbT3v+STfrIbSYcEXJoHwWn7vnSewcJm3B1yxpKAVySFbL336yu0cYU8RkZ42SBh\nJmGD96kmJ+vuTXQBs5ZTndbZo6/UO+r3+qaQ8rK1r4qeEYaOwSYh9wsFxpLJIgyC\nwnl0XQQnwjQKKConAgMBAAGjggLrMIIC5zAMBgNVHRMBAf8EAjAAMB0GA1UdDgQW\nBBTLmBupVqnHkdd6f2hhj5mRrTUZnzAfBgNVHSMEGDAWgBR67wuI2HqJ4b0vBD0e\nsdbER0IoPTBZBggrBgEFBQcBAQRNMEswSQYIKwYBBQUHMAGGPWh0dHA6Ly9vY3Nw\nLnBraS1nMi5zYW5kYm94LmRpcmVjdG9yeS5vcGVuYmFua2luZ2JyYXNpbC5vcmcu\nYnIwWAYDVR0fBFEwTzBNoEugSYZHaHR0cDovL2NybC5wa2ktZzIuc2FuZGJveC5k\naXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL2lzc3Vlci5jcmwwRQYD\nVR0RBD4wPII6aHR0cHM6Ly93ZWIuY29uZm9ybWFuY2UuZGlyZWN0b3J5Lm9wZW5i\nYW5raW5nYnJhc2lsLm9yZy5icjAOBgNVHQ8BAf8EBAMCBaAwEwYDVR0lBAwwCgYI\nKwYBBQUHAwIwggF0BgNVHSAEggFrMIIBZzCCAWMGCysGAQQBg7ovcAECMIIBUjCB\n9QYIKwYBBQUHAgIwgegMgeVUaGlzIENlcnRpZmljYXRlIGlzIHNvbGVseSBmb3Ig\ndXNlIHdpdGggT3BlbiBGaW5hbmNlIEJyYXNpbCBzYW5kYm94IEFQSXMgU2Vydmlj\nZXMuIEl0cyByZWNlaXB0LCBwb3NzZXNzaW9uIG9yIHVzZSBjb25zdGl0dXRlcyBh\nY2NlcHRhbmNlIG9mIHRoZSBPcGVuIEZpbmFuY2UgQnJhc2lsIHNhbmRib3ggb2Yg\nQVBJcyBDZXJ0aWZpY2F0ZSBQb2xpY3kgYW5kIHJlbGF0ZWQgZG9jdW1lbnRzIHRo\nZXJlaW4uMFgGCCsGAQUFBwIBFkxodHRwOi8vcmVwb3NpdG9yeS5wa2ktZzIuc2Fu\nZGJveC5kaXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL3BvbGljaWVz\nMA0GCSqGSIb3DQEBCwUAA4IBAQAjJQE5R9iYGgnrEpEOUGNFVqHYs8L8Y1quoglO\nYsz1GhC2bzm7WSo7iRXfil5D8om6BDM+2TsMkvH21yeNnIclIrK/ReDHqkubbWoa\n9awJDNVa6VoNRdCB6dqEiLwZl4p+bacoShQCd113v5B76gVyCPBmId41rDJv/beB\nv7F894KM4LMMkkZGSnrGft9fc8Y2CPN452EgnTh41PhJHK8DVw8mtx704gblJ64B\nwqhogdzyAjY1uz+a3M1gTTCkEEkuhYXYrHDXgz327JRCW2oXKj7oMMszMI5E4uYL\n/QQijgFOoCPdX+/SvXZo7uMl0dtegLOR/oHxOwLuryqBk9mG\n-----END CERTIFICATE-----",
    "key": "-----BEGIN PRIVATE KEY-----\nMIIEvQIBADANBgkqhkiG9w0BAQEFAASCBKcwggSjAgEAAoIBAQC8bzfeH4l2IegW\ndHsOIooz+nUxpfI5v23ubPsB0P9rLEoPlIn0A7E2zg/b7UCQFvzmzgao49DYEbaR\n5B5rutlRn52rkHufNF2fNEGXgtqrko/Uwf2tGDpve+e6MRuXhyYUEwaqMIRL9RCq\nDSTHFUS+QoNaPdccw9yAQkffEckKoXJA5GYkLvkZ06Vh8R7L6Agjh1VNtbT3v+ST\nfrIbSYcEXJoHwWn7vnSewcJm3B1yxpKAVySFbL336yu0cYU8RkZ42SBhJmGD96km\nJ+vuTXQBs5ZTndbZo6/UO+r3+qaQ8rK1r4qeEYaOwSYh9wsFxpLJIgyCwnl0XQQn\nwjQKKConAgMBAAECggEAJwYvf0hvuu/dtVzNKUm87nPVtoEED7KV7TVTrHYgl4z2\nD5D3GvpyxoNZZHYXk1+3Y4NSfMKle0H72e3w4OWy4QUZ7bB/8aIyK2jylpKqf7Lc\nJ7c/NoxYecMi4/wMl06Nc8XW8QMYOvTXTShor/Q3JuH2ewdol9P2Q/e2E7wGszUN\n9Of74KkoQ1bGf8Z3eutjqdP35/n6cETQDoFiqsV8DfHQGCiiNPKWGD2asQDhhRx4\nvh0TGIxvWF5lnSSxvbGsNFUoGWxr8eUH/EGcH1UnHfYL4xhUYqWTEOhM2v/csmzY\nt8o4BntudmXxlfgYU3NyPKkyx7/bVcnW1PJVtoDKkQKBgQDv7j0jjaWt6dJwsKa0\n5XQ4Xga1PbpDb3LWfzZr3IScUxbVytTnOWVXpok4esn4S00iQpAp7FV3YZ/qox7p\ngcOgV7lW6CIShnLgmr4CEt1hV/sRvqddmmgfrY4ZJLy24MSxwBeZiUPNRHKl9RZA\nJr2WsM04JPE4mmf9QOpGjjy71wKBgQDJDguPpQflCGT8s2KNQjBGnWGVfdNHd1vF\nOFP79wkROAEBb2mJsuBBl8Iu3YvImaKAyAln3uqOhQ8rr+y12DqBRgoAyHY3dr46\nlhQFDonNGVdOxrwRnxajKft32W8Tn6pdjuIs4N5q23Luqym5l9PA6h8aa3E+7yeE\ncvRIfqK6MQKBgG4OjED4wpzp+rvybCXictNAXjdY3037m2PE6sPDXZkPjBP5fHus\nGk6Ad8VOncKlV/Z1Lgfs/q9KOr64oH9gJMoyMzQoOyjgP2XD1ZDB8oaqguJ63+7R\n2x1c0Se7cE07AT6/7JNjIZTQ5v41VEWM/75Vz20HlRbvzO+gjVZb/IP1AoGANJwd\nQFhByZe5vTo/dpE0SrYR++kx6Qh9lgzYRR1uXPgXo0WBC0woTGGmqVbFphc1o5c0\nht6Y5/Q/dQIS4b6UCJHIOk46SOckffYZhP0559ZSt0VfnwjPBqEMsV7PJwZnsRWb\nb3zkFngYCgX15B+rhFZ/Dw3AU2SHJaxi6blhYXECgYEAnBAJuYoIfZolppeUZXwp\nAYoTLGMtXnjvX/YFumlEWzjnXLo4Lk9L+lO9sV5BwhQ6klNBARy5TjAedr+Kw0ee\noGh8F964pkF4jy7qBLMkf4/jaEvft/2tg16ELOj74llsd5GPA8Pgzeh1AXtlowwi\nC1Ere9RQ/zspggyX1uEakrI=\n-----END PRIVATE KEY-----\n",
    "ca": "-----BEGIN CERTIFICATE-----\nMIIHFDCCBPygAwIBAgIUZJOYHaqMZR7leKm8iaKrR380T8QwDQYJKoZIhvcNAQEN\nBQAwdjELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MSowKAYDVQQDEyFPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBSb290IENBIC0gRzIwHhcNMjMwMzA5MTQzNjAwWhcNMzMw\nMzA2MTQzNjAwWjB5MQswCQYDVQQGEwJCUjEcMBoGA1UEChMTT3BlbiBGaW5hbmNl\nIEJyYXNpbDEdMBsGA1UECxMUT3BlbiBGaW5hbmNlIHNhbmRib3gxLTArBgNVBAMT\nJE9wZW4gRmluYW5jZSBzYW5kYm94IElzc3VpbmcgQ0EgLSBHMjCCASIwDQYJKoZI\nhvcNAQEBBQADggEPADCCAQoCggEBAJJZYsafIn0x1j8WLDfJ3HSXt65NqnKwGdcW\nn4z4VqdrvcIl6kJM7cjF3ImaN5SLideuK63/QP4tgGilZxooxLE8V8M/uPgGU74K\noTMBuDho6sND/UtHsr/wgkX9+/Kn50vdLbhXZBmvcL+5gtXKDQGR+d1LyaU8EigX\nkhvegMCSyW72PlQ9FetapanOpH0e5+osGRVI9ysm7PFrWE6UOs8EA/d6+v8SwHTW\nbD6iVVgtGnQtm0C4w4H6VVNnFE0F8pSnXQQPzQXMONIFi/UZPSB00H0qnxRvWkw3\nJa7QErS8hdMPGUHQ9N/RujhMhf7tlUArcgod6mc+SYfcI3j1pUcCAwEAAaOCApUw\nggKRMA4GA1UdDwEB/wQEAwIBBjASBgNVHRMBAf8ECDAGAQH/AgEAMB0GA1UdDgQW\nBBR67wuI2HqJ4b0vBD0esdbER0IoPTAfBgNVHSMEGDAWgBQVb9vsej3AhKXXgbWR\nvfmoWNM++jBZBggrBgEFBQcBAQRNMEswSQYIKwYBBQUHMAGGPWh0dHA6Ly9vY3Nw\nLnBraS1nMi5zYW5kYm94LmRpcmVjdG9yeS5vcGVuYmFua2luZ2JyYXNpbC5vcmcu\nYnIwWAYDVR0fBFEwTzBNoEugSYZHaHR0cDovL2NybC5wa2ktZzIuc2FuZGJveC5k\naXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL2lzc3Vlci5jcmwwggF0\nBgNVHSAEggFrMIIBZzCCAWMGCysGAQQBg7ovcAECMIIBUjCB9QYIKwYBBQUHAgIw\ngegMgeVUaGlzIENlcnRpZmljYXRlIGlzIHNvbGVseSBmb3IgdXNlIHdpdGggT3Bl\nbiBGaW5hbmNlIEJyYXNpbCBzYW5kYm94IEFQSXMgU2VydmljZXMuIEl0cyByZWNl\naXB0LCBwb3NzZXNzaW9uIG9yIHVzZSBjb25zdGl0dXRlcyBhY2NlcHRhbmNlIG9m\nIHRoZSBPcGVuIEZpbmFuY2UgQnJhc2lsIHNhbmRib3ggb2YgQVBJcyBDZXJ0aWZp\nY2F0ZSBQb2xpY3kgYW5kIHJlbGF0ZWQgZG9jdW1lbnRzIHRoZXJlaW4uMFgGCCsG\nAQUFBwIBFkxodHRwOi8vcmVwb3NpdG9yeS5wa2ktZzIuc2FuZGJveC5kaXJlY3Rv\ncnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL3BvbGljaWVzMA0GCSqGSIb3DQEB\nDQUAA4ICAQCANeSAlmJy3e9rrgTGShVCyMQhy68j3cAJyFzqCutyNMGHUgFOjAgD\nzIUQZmAepTDJdhJF+BoruBfAIJUr6tD9EBw2MZXiTLHZG9mqtGwsMbeI3o3R9Y3G\nEpGp72jIHw7mtUZdoaWcmgqxCWn6UT9bBKAkdt6KyRepPUy1YI59MZxpVOs5J0s2\nQFd3FRCNxdzgsuGqdxTb1Gre4I5E1vJWcp1Fe/kPdaOgPVC89M6uk3WYTnMNZ20N\n8K0ecXy8+E3K+to35berWn16g1ZrufylX6s2yyxcsUnh5KP1smFd8MePekKIW0SD\n8hqD1MtGQEmzdWrPCT9fZUzONj4VuDcl/vgfKUBsBszTmqwGF34G+663v10KUhga\nkCiIOZtkT9B+aESGAfczQiFO1h4cI52TKwEptfbplrFS2gILrzleqv0JoDDFYVhY\nV5AVDjqeHaniClCi10JdSN11LqNdagpyojN2a2WhVSAigIT3yDeqozlzjgPui/1E\nDt0zBkXd5uFDwNeLUwOribuS3hxVG5Bg73ZJl+UV3ZuAzFFCfkVBz6BeqUusf8+P\n3pqAQ4gzhSWNsTBIsjaVV8ZU8IqxKhBkRUSNjihG2kM8kX9knQvRbCBuuse/dDUe\n4cUJ+wT1omVgq+TWhShOAjsHEa233omXbH7v5igLBEkzzqmM5cAv8Q==\n-----END CERTIFICATE-----\n-----BEGIN CERTIFICATE-----\nMIIFvDCCA6SgAwIBAgIUKhBUxL5Dt4w3xH1V3X1n+x/e3hcwDQYJKoZIhvcNAQEN\nBQAwdjELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MSowKAYDVQQDEyFPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBSb290IENBIC0gRzIwHhcNMjMwMzA5MTQzNjAwWhcNMzgw\nMzA1MTQzNjAwWjB2MQswCQYDVQQGEwJCUjEcMBoGA1UEChMTT3BlbiBGaW5hbmNl\nIEJyYXNpbDEdMBsGA1UECxMUT3BlbiBGaW5hbmNlIHNhbmRib3gxKjAoBgNVBAMT\nIU9wZW4gRmluYW5jZSBzYW5kYm94IFJvb3QgQ0EgLSBHMjCCAiIwDQYJKoZIhvcN\nAQEBBQADggIPADCCAgoCggIBALJFBgmKj3iDF3C8+8smNNQDxLFA9kCcca1iaxQf\nvMI/FKGW2ullHhH+W3EGEajn39QOlccGyrfCONHLqMW53+HAMtwiIvcrJgj72V7D\nnYflO3aaCFwoC31PL1+pMBo88F6jvezZ8BlRnheT7urCs6+onhz8pm0cVNc77U5X\npi8IOJz1QFKecJnFLjG0NiLCzOzjLSo0A8Rue9K/H5fjq+PqKdXG94AoQyFUwlsU\ny4aXbylDz1kRiOSnOlRNPcY/su95pFKQbGgaZZ1fLf89i5PtHAUu92FbD7H7OyYX\nXpZ97La0d7cUH0A4nb+LpOd/f0c8lAN2Ya1B8aKvWiF23q3c8EoAJyhrdkHKe6yI\nYvLC5G5jkbJefeQcp34IgD8T+Tn3aBF7YgmlYUMbnsuokBG28Hr50EAklCclA0bb\n4pmf8nE6y7VQ0CM/bNZd1F9AjxLukkyvkrOD6A6uv+c5KeC+da245dBzsyhiKe9R\nRX5Gkf7NSkDu9b9YkdDaWV6LXxpUA0SmdT9M16yK3XPDKOWBI4gVSB1KuwrOcal/\ndMwFUlxvqdGugRbxDNNukxa0l3JztGg6XYLjEiiYrQ+7HChbUVNlM0l0VZAz4eON\ngYrq2ExUDWlQXiES389/Qz3R3yDk9ib1YsMHwAux2ulCssFVn4EgtnYFfgf3o01J\n3CedAgMBAAGjQjBAMA4GA1UdDwEB/wQEAwIBBjAPBgNVHRMBAf8EBTADAQH/MB0G\nA1UdDgQWBBQVb9vsej3AhKXXgbWRvfmoWNM++jANBgkqhkiG9w0BAQ0FAAOCAgEA\nVPrUd4UDjOhkxOzSN4bMr0cULZJwQPRV8aj99tzdv8Ef44CwLVkLmm7Z2d1uRA9l\n7xbK6W8L1oL95iV4K4o2u4+ZFG7mrOfU2T2wgTfMlIxHDoAxS49flUYkBpQI1Wj4\nJBZ6fKGFVH6PyIio0I2Mx2u80ZX6lPYQ2q4DR6eBUoNt8T8XSWpD4TjroFbOVIp+\nN84alBca/pvW2aF2HwPndrL/Y++HZp3TpdUeBUT757KOZ7hdwf30pxd8qNn8+peb\nbP2h6b9pjKAmS8ciBExJzchhQWJRP6LIdvexTsBQ1HLxlZNrlg66wYT0kuVVzRTa\n0qRvIjQ0ntmhy2DtmE5VFT9O8ahcQL5Ddk8B4dhiy59vjALS6kIUXJ6GCobzRUsQ\na7b7J7nu+PTY+qVo0LsTMO1rVTUXD63gVk8QmPUwnvduk9nxraNpVP+m17BuEcls\nEsoGAAQYcmzOlnZpqhhbTnbsEayW1bMyxkLjBjXpOfBgrvyv5fU/09lP6VB20FJr\nzVPZWr5PTzaaizDDecSKgZ1ANIwXIIwWirwzDqqQb922JtcH+Ca6JJWgrV7+kDCU\ncVzwKVYievjXMCsmRSzDKEgp4n1AgrxcoaH0smD+qA+wzfsMqvEA1iTNW7zdnF0o\n6UJ9rkWxKr+JRZ5jFO+kpKQ1DxfDJZE554aO8AXzYEI=\n-----END CERTIFICATE-----\n"
  }
}
```

</details>

<details>
<summary>JSON Configuration for Payments v5 Withdraw QRES (Auto Redirect)</summary>

```
{
  "alias": "obbsb",
  "description": "Phase 3 Payments v5",
  "server": {
    "discoveryUrl": "https://auth.mockbank.openbankingbrasil.org.br/.well-known/openid-configuration"
  },
  "directory": {
    "discoveryUrl": "https://auth.sandbox.directory.openbankingbrasil.org.br/.well-known/openid-configuration",
    "apibase": "https://matls-api.sandbox.directory.openbankingbrasil.org.br/",
    "keystore": "https://keystore.sandbox.directory.openbankingbrasil.org.br/",
    "client_id": "984e85a9-9001-40eb-97b3-194f5afbd956"
  },
  "resource": {
    "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
    "resourceUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/pix/payments",
    "brazilPaymentConsent": {
      "data": {
        "loggedUser": {
          "document": {
            "identification": "76109277673",
            "rel": "CPF"
          }
        },
        "creditor": {
          "personType": "PESSOA_NATURAL",
          "cpfCnpj": "48847377765",
          "name": "Marco Antonio de Brito"
        },
        "payment": {
          "type": "PIX",
          "date": "2021-01-01",
          "currency": "BRL",
          "amount": "1333.00",
          "details": {
            "localInstrument": "DICT",
            "proxy": "12345678901",
            "creditorAccount": {
              "ispb": "12345678",
              "issuer": "1774",
              "number": "1234567890",
              "accountType": "CACC"
            }
          }
        },
        "debtorAccount": {
          "ispb": "12345678",
          "issuer": "6272",
          "number": "94088392",
          "accountType": "CACC"
        }
      }
    },
    "brazilQresPaymentConsent": {
      "data": {
        "loggedUser": {
          "document": {
            "identification": "76109277673",
            "rel": "CPF"
          }
        },
        "creditor": {
          "personType": "PESSOA_NATURAL",
          "cpfCnpj": "99991111140",
          "name": "Joao Silva"
        },
        "payment": {
          "type": "PIX",
          "date": "2021-01-01",
          "currency": "BRL",
          "amount": "1333.00",
          "details": {
            "localInstrument": "QRES",
            "proxy": "cliente-a00001@pix.bcb.gov.br",
            "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5910Joao Silva6014BELO HORIZONTE62070503***63045243",
            "creditorAccount": {
              "ispb": "99999004",
              "issuer": "0001",
              "number": "12345678",
              "accountType": "CACC"
            }
          }
        },
        "debtorAccount": {
          "ispb": "12345678",
          "issuer": "6272",
          "number": "94088392",
          "accountType": "CACC"
        }
      }
    },
    "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
    "brazilQresCnpj": "99991111140",
    "loggedUserIdentification": "76109277673",
    "debtorAccountIspb": "12345678",
    "debtorAccountIssuer": "1774",
    "debtorAccountNumber": "94088392",
    "debtorAccountType": "CACC",
    "paymentAmount": "1333.00",
    "transactionIdentifier": "E00038166201907261559y6j6A"
  },
  "consent": {},
  "browser": [
    {
      "match": "https://auth.mockbank.openbankingbrasil.org.br/auth*",
      "tasks": [
        {
          "task": "Login",
          "optional": true,
          "match": "https://auth.mockbank.openbankingbrasil.org.br/interaction*",
          "commands": [
            [
              "text",
              "name",
              "login",
              "ralph.bragg@gmail.com",
              "optional"
            ],
            [
              "text",
              "name",
              "password",
              "P@ssword01",
              "optional"
            ],
            [
              "click",
              "xpath",
              "//button[contains(text(),\"Sign in\")]",
              "optional"
            ]
          ]
        },
        {
          "task": "Consent",
          "optional": true,
          "match": "https://auth.mockbank.openbankingbrasil.org.br/interaction*",
          "commands": [
            [
              "wait",
              "xpath",
              "//*",
              60,
              ".*Before proceeding, we need to confirm some information:*",
              "update-image-placeholder-optional"
            ],
            [
              "click",
              "xpath",
              "//input[@id='consent-toggle']/following-sibling::div[1]"
            ],
            [
              "click",
              "id",
              "continue-button"
            ]
          ]
        },
        {
          "task": "Verify Complete",
          "match": "*/test/*/callback*",
          "commands": [
            [
              "wait",
              "id",
              "submission_complete",
              10
            ]
          ]
        }
      ]
    }
  ],
  "client": {
    "jwks": {
      "keys": [
        {
          "alg": "PS256",
          "d": "Q9gSOfnkGJnAsV3a94j9ae9ihjqgMwXgVm73VTyEs1u9Jq73pCWX0e9JdeNMKdgKpiJYjyxa3ttxCY58eiGKEi7c50zYRx8YLTL2rIVWqS6JVGpXuzIQutkQDM4AfD72bG3-xT-caSCansGbdEIFJjX32Ujbs1UUoQlE96m3hNOjB5vNyHBWrBUgUGG9_uJiWFG6Lbj8ZGtiihA_PQkzuArLzDvO2OMVHCzIyQ4CwFE1tI9xHFHpioJQXBnymURQvkm3MmEwHRG_KUdABQ55gG32jothy7jOOYAMkvOCejteTZv1nT4dsEj-CBxDBtTI6SerXb11VX8b0suzSBxx0Q",
          "dp": "S15AOPpOtYgYjfOi2rNojY3NpU-Qobnfnnt_MZEJ2_DS0bGwXSgGJjHOOOAowy1HK0n7-AhXbwhr026sBuicR_Kpj6RkzGVrJug8y9R02FXZwlQpgjSBZdO6C2B1OOvtyKmnKg5q1KdQ7Kx6vYPV7UutOJn6NlH0RbFgG4NGelk",
          "dq": "oBgBMB54mtrriQCg4YyDY_zf7LW4f6oqiUl3l7odf_ArjVamjHM-boZnhGoVzZ5uXNs03wEdBIc2HLmsoGLVuodcYHjyptmvyPebiH2mavFlUlI8ILG6lkyIhMp3Ri8iXGX2MYlPjP2EawNDMHB6BO0bZ5NugyzxuF_OKhfEFLc",
          "e": "AQAB",
          "kid": "-duNE0ZX5NmDkUlgNoqDY5Ve7UdFTA7S25WJSAv8tNQ",
          "kty": "RSA",
          "n": "-6Ep5kV0qcQnrxQzbEgMGKQRHnhXlp3ZpAVqQbbzkVG_a1tHLi0V7YAmjf3isXMvdvWjApeShL32gqxgcKDvC5Mnd5ufR1ujzb5lsnYXy-tKMQWnAlCqy7mSuxi8JIBXyZb7CMGU29L32Tvd5MjDh_hSgwnHcTggE-ehqzK5eyvK7DjvlbfCKXgDx94kMcwyI2K0EurahHj9_I3lEQzAt73OocF_z84FQxO87A8Q1cM3nEGyykZPaFyulQ4bf4U2tT_Jfd0ppYX1j194ouPeqMZBsGnxKf4L4QvuberbRpdeOO92HhWHHiwiTuhYxF876-LKgPzqxK-Y1a2_4gsVAw",
          "p": "_oebNFofSe_8fdotMxUEk7n3pq5eT96rO_VPdHyTZERDrkU0djQf9BLy7DejYoRReuI0AJWkBL9EGBhECaowmx8gTCs43ffQrBDULYB4elmS07ov1pq1STqzqRKbu_INaSGVgxFzhYC_EeFVpB0RPlAUvb1_aQkH79J8VMnp2_U",
          "q": "_RVEyO9NB6XiJjMz9t6XrNxG01Vguo2VVBLaDJhoi1g7gydUDkNc9twhF1Ifps8Gf3m9aMjjOmYqE5kuWCPBHxkk8cZOm4C2AhVbQxMkZLOyPeJDfKfCi7yJRIfmwqQM5AKosALfN-jW_p746lRhCAps8eH9XF6bjugi_MH1yhc",
          "qi": "yXG_vCx0xL9DlU7f0Ixub9NSD1QJtAJYxwKyHukw_8f4rHLiZ8eeCerfZfPd7zsPGSqOmY2605MNT1Z2ohYgoRyu05uwstEDKqtgl_uxupfO6AJKCja4paIB-ICvQQXpOY1n9BW6VcDwSylTnv1pKvVnTvxzy5z008wvrafQtFw",
          "use": "sig"
        },
        {
          "kty": "RSA",
          "alg": "PS256",
          "use": "enc",
          "kid": "e96744c58188c084310920b152ffb02a392b119a009fb1fa1a656006715e1604",
          "n": "4eIXvOR1XXo3MT9syMwRZj2ChbV2Qlp_623VCIhYvPtJ5k5rlCr1hP4n0PC49U47pa3UKNs6DYHefHKm9I4h4crgk7zsln2_JP3kK1equqIO1U12Rv4Xbm_2_eqR3hPKcE3il2ky2Neby8OThFnyDwBNKdxI4MvOKm910qQhYns2L4w_i9fjF2z1Wpi6sMPW8IERhkqaBWgoaH9g2obGbNuoYCzEjOWvRb_nVjYKRPqTI2A11kWZ4mVTRkTO4yM1gdI7z8Hsl4fqlEXeVdmMkVJhRvQa-vFfegecgO8nUY2XoOUx_UR51F8PO9bepy-jH16cRDwjLE-2ex7mE_wfMw",
          "e": "AQAB",
          "d": "BqovoVF4vww8nA9IuLhnHDlDZFbHov4qZeCecQgcEJNpIxdiqDZuR4EvECsSIgOWOFvwW-lzOI1oHaVNlMvezXU5eoWpnpuEnzHlYHwCzxftNrde5PBZWHC-sAMStvBzJpLw7riNZgWFx_wNmoTQfHqgGQfLyxcB9Pf6v387qiN1wHfSXQshtFiDg_6tBaH6dS1jRAg7_56dQp1wWJeRaqMCg9QeESmo3c-76hnRSMU6fgrONU6qGMSLopv-nirh3H1gZePcXzVgf9cerRMQgV1pWUZEd_iJqTaX8U7wB0txmVF6QzRxR71Ah6nZuV_Rv7X88zB8u0rXOvjeGtuZKQ",
          "p": "8fN0GXyZnvxba4yoOgdL9ta9pkjjWVu5eTOIyvSgKf09hUSWKL6sKm1N0l68detwzBFpnxObOeUCMnU_BFhJM-s0w5GognaAX6GB5-TzdYHwmsgqAch3-_hi_kZU6A-SLZu7bQFGXTEotQ1zMxVuCMZ7AjTs0CGZrS-vItFYtik",
          "q": "7v_Ldwh3L9On2CNAefLgs7dyDBAgWrkXOJ9Z1EnrKgMHbqgq5dOixv2ezKNdOUte9G4ve555XTf2sC-p0TF9PNYC0_4KthI8NLik8RtDsQmYJUYw7qfV_YitzGflM2DRr6KaV5SmO_aPWRfzuVWh_6kIQ_GmXf47ASasKVeD_fs",
          "dp": "Jyi-_q0C9A9mAHcodxPdQJsq4LHlUf4de7dSiX6kOYeKIHqkTv3lQYylTsoUeIVdoTmkPaHfurQM8fu18k8Tsfp8dLarbkodptyt-Mk-eiNIvNRusBExEi_2Xa8maNS0VPtij1boe4bMTtlZbsgmIfd1yzqjpV_6zmPsVZdKY1k",
          "dq": "qjW-YA3FZGhmtwWUG8Wfxh41uOWbRUFgilDils_2DTuPBX363yc0XGevuqn18KH_BDGc23tnj74VkDDBzlxihvsblILuefDOs_V0csoqEWF128X7f1xEiIXY0SSFFWw0qdMx_IG_SiE0wgzO5QVZlEx7uHfXNkWjHBTAs8jCFhU",
          "qi": "8W2vDdiA8qDxL2fiJPP2m3NqbjGW7Tf5PsfGo0Gqfv6nWVweuVwsyUNT1AYduZUCvFRG5LRNHqiwZNpNB6XQln1W41GaIqGkHWJkveHhg9xIQmSK2hrX4OnSdyvMiGiB2yvce0FTgQ0OzXuNkIKJKJLP2nAJusNgNcVT7qgKCRA"
        }
      ]
    },
    "org_jwks": {
      "keys": [
        {
          "d": "BpgLagicLjysglxtDX7bJnOv4-IP-5yyGdL4oOkDCl_-lO8twPDhWLfXNCf2QTs7l1T1GLNUyALKjYDNEvjbpu03_K1dtRwO2ZS4_VHTPhe99Etn1GXntdfcFvQiD9Lz6uzs2-0DOIG_5xWUiVhTUN5HPRfMMXF3ktG2ucTOQqsJU0O2SOohVIvqYH4EDJNIw8qUsu1C2JEDMj79H_8KaXEUVx8tFFLMxmt67a_a7sImXvEaIYhUCu-DMMDrzBc660s_eTcihJ_DkJgYPPWctnmpUClKa4zgABDqGXhPQFfLS4ywGAHnLZF1MyNeKFXpmeJShjNJ5MqjBKJTnFHDQKs",
          "dp": "CFfrENWCU61YHATfdTy73lt2reMz0dBDicy92s4FqHpcup6O6f5MWGvhpBlLVC-tNA97qzyKExFwxl6c6rf45l8T6GLjy4C2DJEH0pGKeh7-PP7XW1KBvsclbJdSoSj-bOFRomFVGKYhIF3nRnr9-Dvj1k8aEcClPT1E9i9rGI7P",
          "dq": "BzCeCJQ9pKQVCpyFi50PR8_E7d9uW9nYqJpf0GBT5XdnZ44qnliLAffZmVwcxXh6e_JzIjC0ByJrYKd_dekXLCrsOex1XxqvI7WH6EZ3Nvoe_1835ZgtQ2PsPSvGKifHHPXocKyqqRdT7KlGTXfnpKtezsXPxe63VS-3coE62-_F",
          "e": "AQAB",
          "kid": "EKSYJfNcI8Bm22_dP0ziWpTjw9UceAdVjykgwO5BkfE",
          "kty": "RSA",
          "n": "oBp-b0EhezRYfisJBL_WA2Yh0Y2zPYHsy8N4G9mddkop-kFJT12XSSBx8GXmyjDL14Wg5vRNA6R_TwXbJbnHnE59uMYiWNi_G7OL6jMsncmYdyBuwl-lDWExaXC5Qg9vYgGnt7d1SthQoiJkduPIiNpniq5p7px-jJYQO4SECUqpeLl9rU_Xvxn5zpFu4dw65wBi4oSDiJ0zujQtxofOmbJCKYTWrPmd8yPlPgwIttP2ZcprMs5Ya57-99NhAealcVptRTOQTEWEOflmurq58Byu7pT64ns-9Su8JPcHMMzxOOVM7KNPuZA7Xa5-1aBd1XrhxkBHIDzUqOpanSlr2uk",
          "p": "DgL5bOQ5-JXM6Ed_3BRKW2a3EcHB_UjlWPlGGkc0RBeEwlNi6D3PQGZmgTxyGXWA4W3HMi2S2pXx8oxWd9rrw9Uc_BNrIdvkMcU9LnkCvxK-dcHalVrXhv0l1EbQx0mG9LjLsiqmJiJYnUYTuLjO8lJaebSTp-EH2fgTs81_SBKv",
          "q": "C20t29WtF9yAXt2r5Yu7chtrJUMIsu_TUY2N6p75BWWBB76oNib4Dp5fVePnbTqdSP913dS1K1vHwEAqS_Z_C6vfmaYha6Hguipo5jotTTJoYDxV_xTp1dGWcr8MltBE9ikhLa8xvGVxXjSi4vkqc_TyXlBSHbbBSZtjB32rCLHn",
          "qi": "BRx-2fqZYWrIzcayN1v10HfzcQaZue-NNZP7Eid81oBBxBrDQmiGdzQLi0BKctjLBr21_GWUgHgEYRym3He5biuDVM0WnyhXYeLLc_pv3bIG6FoPrP4XDZo4GTM4JdVj2im_OQWdXuokFzsZzeVV6H8p46TxpyNDix5oFjmyuB11",
          "alg": "PS256",
          "use": "sig"
        },
        {
          "p": "2a8fRJ7ybF-qtF1zrYzSm7z3C4wNTUMbVYqe44tR9FbKsobqW2tS0iAZf-GJ_SZPcWxkE76gunW7YqMJecGUtXsJ8TTHwjcPQOMYzxnyJu8Q4JOj01YJVrxUY9D0ZzpWM9oTAj1-qoE0w7Dy-XNUc14-HeRlmOkg2tTfrXTVR8c",
          "kty": "RSA",
          "q": "0xlPJFRUcBU5j2SKSajVnd4H5p88RSsd4cArMby1ZRuSeHEsX76c6QKAPq7uTfKrTeZic34yzAEUyHloP1fZQYQ2UQn-f6PsTAWdT1Lp5oi2VZCT0yc9-1EGnLAiUCbM9SQQyf2GIVhCiAk_0VuY6le61Pw0U4GssvFJzIrx4as",
          "d": "GxnizpWcqL1wajD8-Y-8H9-II4UZMKfkgbfwRiLK9uAd8-kEJdO9jdNeMxyytg2saDhxNTeRTkYz_VbBf3p9dGhuYx84d-ZagUbIiU3ho3FCsBRrzQQZw9OQrzPDUzp0-SBn1_GLCf9fo4ysxWHbn9euJVi2fpN_bHlBi1n8fKhdBHYE7X3XJnRYrUXItxZw5sJsqM_boONLxdLAvgmZx5CHft94JZsR6JPwlj9Ba_CuNWX_3OuUGyV0f5_1ICAEYijw9PA8KAW6t5UUYn39_KYL8nF5L1Bh6W1j8eN84I2lcKZNO6Pou064ag_wqGhk4uXuQO1IV8jRFn3-pqhSEQ",
          "e": "AQAB",
          "use": "enc",
          "kid": "c1d7b80ce4b88c4f2cfb68e7a8c45bfff355ae94259bc1a73a95ddbaeaf7c96b",
          "qi": "pU1IXwiQoFERdzJsx7kSC79Gwhak7uw7OAJCbcfkKE3GSwTWHrKfg5uDZlNvSnNU1Hbpxd0bgc40dFI2aNBML1gyDwTjQplWVJikkFix8E6z_ErSa_D5w5yV4k6CNtt7OzlMXawiZ-ndcuiOs5MkfSRyeB3k5rQmuZjLVzFFlnw",
          "dp": "Gn4dqBRQHLBn7huRgIWq_Bk7V8RrugN4yChevgKurrYBZUjWLNoa8kfF0rJ4QL7w3DT82QpSNV8utwpwlMjieFPJGfn6dcCNsq_wzQOzXNmrjClrvsSxzkSNYLiFhiqrYxQfTB5_0_B1o3tdls5acM__b1PkqX916CwQLOQTMPE",
          "alg": "PS256",
          "dq": "NS0x94fawWVHW6zK_SUvspXkzZ6dMxtaaqza9KuB0ldwvTBdKj09D6FWpvOwCiiwKG55rHhE2YkIMDwNG6_Iha2FdUKcPpEPjFL5vqq3SyBzNfi2lEFVZsKRdNUVv7UWekY8iHV53Vp7YANcdSOq0JWK9e4WTFblJyqLGaCCsAM",
          "n": "s4DcK4uxKroJPE1R7Te4ppNexbuK3C-Z3MpXFr5hmY43gYIoVMo89jE6OcDiO0Z4rxe8dsH4oYA2vAJQ0IhAaUxYMk2kN01ei761zMQWHLUPLcEKWgipYHy4AgwAUaF7-Glyb0DT1RRcY4f1tEddftxhwXZjeFduj6luVg6fVvXRIRjttybUkIKvf5ShMofVFCF_IyjYlOal4g3DVnCg62dR71WX3fRXSufxrRBG-L61rv2VSMg8pIb1DFiYKDlEXEnTdLk-7goBpTIz3wBsrZgJESSZOn_BG_-fCE0V75rheLMuJd4IGE4H0taVfEQOJKRKBVzc2jAz0sOaVuPY7Q"
        }
      ]
    },
    "client_id": "Jj-hosRwYqvtnQZNph2Ah"
  },
  "mtls": {
    "cert": "-----BEGIN CERTIFICATE-----\nMIIHQDCCBiigAwIBAgIUOyyDtirdgYQIT/eSBtvaP5JRcoswDQYJKoZIhvcNAQEL\nBQAweTELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MS0wKwYDVQQDEyRPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBJc3N1aW5nIENBIC0gRzIwHhcNMjUxMTA1MjAzMjAwWhcN\nMjYxMjA1MjAzMjAwWjCCAUoxCzAJBgNVBAYTAkJSMQswCQYDVQQIEwJVSzEPMA0G\nA1UEBxMGTE9ORE9OMSYwJAYDVQQKEx1PcGVuIEJhbmtpbmcgQnJhc2lsIC0gUmFp\nZGlhbTEtMCsGA1UECxMkYjk2MWM0ZWItNTA5ZC00ZWRmLWFmZWItMzU2NDJiMzgx\nODVkMUMwQQYDVQQDEzpodHRwczovL3dlYi5jb25mb3JtYW5jZS5kaXJlY3Rvcnku\nb3BlbmJhbmtpbmdicmFzaWwub3JnLmJyMRcwFQYDVQQFEw4wMDAwMDAxMDc0Mjg1\nMTEdMBsGA1UEDxMUUHJpdmF0ZSBPcmdhbml6YXRpb24xEzARBgsrBgEEAYI3PAIB\nAxMCVUsxNDAyBgoJkiaJk/IsZAEBEyQ5ODRlODVhOS05MDAxLTQwZWItOTdiMy0x\nOTRmNWFmYmQ5NTYwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQC8bzfe\nH4l2IegWdHsOIooz+nUxpfI5v23ubPsB0P9rLEoPlIn0A7E2zg/b7UCQFvzmzgao\n49DYEbaR5B5rutlRn52rkHufNF2fNEGXgtqrko/Uwf2tGDpve+e6MRuXhyYUEwaq\nMIRL9RCqDSTHFUS+QoNaPdccw9yAQkffEckKoXJA5GYkLvkZ06Vh8R7L6Agjh1VN\ntbT3v+STfrIbSYcEXJoHwWn7vnSewcJm3B1yxpKAVySFbL336yu0cYU8RkZ42SBh\nJmGD96kmJ+vuTXQBs5ZTndbZo6/UO+r3+qaQ8rK1r4qeEYaOwSYh9wsFxpLJIgyC\nwnl0XQQnwjQKKConAgMBAAGjggLrMIIC5zAMBgNVHRMBAf8EAjAAMB0GA1UdDgQW\nBBTLmBupVqnHkdd6f2hhj5mRrTUZnzAfBgNVHSMEGDAWgBR67wuI2HqJ4b0vBD0e\nsdbER0IoPTBZBggrBgEFBQcBAQRNMEswSQYIKwYBBQUHMAGGPWh0dHA6Ly9vY3Nw\nLnBraS1nMi5zYW5kYm94LmRpcmVjdG9yeS5vcGVuYmFua2luZ2JyYXNpbC5vcmcu\nYnIwWAYDVR0fBFEwTzBNoEugSYZHaHR0cDovL2NybC5wa2ktZzIuc2FuZGJveC5k\naXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL2lzc3Vlci5jcmwwRQYD\nVR0RBD4wPII6aHR0cHM6Ly93ZWIuY29uZm9ybWFuY2UuZGlyZWN0b3J5Lm9wZW5i\nYW5raW5nYnJhc2lsLm9yZy5icjAOBgNVHQ8BAf8EBAMCBaAwEwYDVR0lBAwwCgYI\nKwYBBQUHAwIwggF0BgNVHSAEggFrMIIBZzCCAWMGCysGAQQBg7ovcAECMIIBUjCB\n9QYIKwYBBQUHAgIwgegMgeVUaGlzIENlcnRpZmljYXRlIGlzIHNvbGVseSBmb3Ig\ndXNlIHdpdGggT3BlbiBGaW5hbmNlIEJyYXNpbCBzYW5kYm94IEFQSXMgU2Vydmlj\nZXMuIEl0cyByZWNlaXB0LCBwb3NzZXNzaW9uIG9yIHVzZSBjb25zdGl0dXRlcyBh\nY2NlcHRhbmNlIG9mIHRoZSBPcGVuIEZpbmFuY2UgQnJhc2lsIHNhbmRib3ggb2Yg\nQVBJcyBDZXJ0aWZpY2F0ZSBQb2xpY3kgYW5kIHJlbGF0ZWQgZG9jdW1lbnRzIHRo\nZXJlaW4uMFgGCCsGAQUFBwIBFkxodHRwOi8vcmVwb3NpdG9yeS5wa2ktZzIuc2Fu\nZGJveC5kaXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL3BvbGljaWVz\nMA0GCSqGSIb3DQEBCwUAA4IBAQAjJQE5R9iYGgnrEpEOUGNFVqHYs8L8Y1quoglO\nYsz1GhC2bzm7WSo7iRXfil5D8om6BDM+2TsMkvH21yeNnIclIrK/ReDHqkubbWoa\n9awJDNVa6VoNRdCB6dqEiLwZl4p+bacoShQCd113v5B76gVyCPBmId41rDJv/beB\nv7F894KM4LMMkkZGSnrGft9fc8Y2CPN452EgnTh41PhJHK8DVw8mtx704gblJ64B\nwqhogdzyAjY1uz+a3M1gTTCkEEkuhYXYrHDXgz327JRCW2oXKj7oMMszMI5E4uYL\n/QQijgFOoCPdX+/SvXZo7uMl0dtegLOR/oHxOwLuryqBk9mG\n-----END CERTIFICATE-----",
    "key": "-----BEGIN PRIVATE KEY-----\nMIIEvQIBADANBgkqhkiG9w0BAQEFAASCBKcwggSjAgEAAoIBAQC8bzfeH4l2IegW\ndHsOIooz+nUxpfI5v23ubPsB0P9rLEoPlIn0A7E2zg/b7UCQFvzmzgao49DYEbaR\n5B5rutlRn52rkHufNF2fNEGXgtqrko/Uwf2tGDpve+e6MRuXhyYUEwaqMIRL9RCq\nDSTHFUS+QoNaPdccw9yAQkffEckKoXJA5GYkLvkZ06Vh8R7L6Agjh1VNtbT3v+ST\nfrIbSYcEXJoHwWn7vnSewcJm3B1yxpKAVySFbL336yu0cYU8RkZ42SBhJmGD96km\nJ+vuTXQBs5ZTndbZo6/UO+r3+qaQ8rK1r4qeEYaOwSYh9wsFxpLJIgyCwnl0XQQn\nwjQKKConAgMBAAECggEAJwYvf0hvuu/dtVzNKUm87nPVtoEED7KV7TVTrHYgl4z2\nD5D3GvpyxoNZZHYXk1+3Y4NSfMKle0H72e3w4OWy4QUZ7bB/8aIyK2jylpKqf7Lc\nJ7c/NoxYecMi4/wMl06Nc8XW8QMYOvTXTShor/Q3JuH2ewdol9P2Q/e2E7wGszUN\n9Of74KkoQ1bGf8Z3eutjqdP35/n6cETQDoFiqsV8DfHQGCiiNPKWGD2asQDhhRx4\nvh0TGIxvWF5lnSSxvbGsNFUoGWxr8eUH/EGcH1UnHfYL4xhUYqWTEOhM2v/csmzY\nt8o4BntudmXxlfgYU3NyPKkyx7/bVcnW1PJVtoDKkQKBgQDv7j0jjaWt6dJwsKa0\n5XQ4Xga1PbpDb3LWfzZr3IScUxbVytTnOWVXpok4esn4S00iQpAp7FV3YZ/qox7p\ngcOgV7lW6CIShnLgmr4CEt1hV/sRvqddmmgfrY4ZJLy24MSxwBeZiUPNRHKl9RZA\nJr2WsM04JPE4mmf9QOpGjjy71wKBgQDJDguPpQflCGT8s2KNQjBGnWGVfdNHd1vF\nOFP79wkROAEBb2mJsuBBl8Iu3YvImaKAyAln3uqOhQ8rr+y12DqBRgoAyHY3dr46\nlhQFDonNGVdOxrwRnxajKft32W8Tn6pdjuIs4N5q23Luqym5l9PA6h8aa3E+7yeE\ncvRIfqK6MQKBgG4OjED4wpzp+rvybCXictNAXjdY3037m2PE6sPDXZkPjBP5fHus\nGk6Ad8VOncKlV/Z1Lgfs/q9KOr64oH9gJMoyMzQoOyjgP2XD1ZDB8oaqguJ63+7R\n2x1c0Se7cE07AT6/7JNjIZTQ5v41VEWM/75Vz20HlRbvzO+gjVZb/IP1AoGANJwd\nQFhByZe5vTo/dpE0SrYR++kx6Qh9lgzYRR1uXPgXo0WBC0woTGGmqVbFphc1o5c0\nht6Y5/Q/dQIS4b6UCJHIOk46SOckffYZhP0559ZSt0VfnwjPBqEMsV7PJwZnsRWb\nb3zkFngYCgX15B+rhFZ/Dw3AU2SHJaxi6blhYXECgYEAnBAJuYoIfZolppeUZXwp\nAYoTLGMtXnjvX/YFumlEWzjnXLo4Lk9L+lO9sV5BwhQ6klNBARy5TjAedr+Kw0ee\noGh8F964pkF4jy7qBLMkf4/jaEvft/2tg16ELOj74llsd5GPA8Pgzeh1AXtlowwi\nC1Ere9RQ/zspggyX1uEakrI=\n-----END PRIVATE KEY-----\n",
    "ca": "-----BEGIN CERTIFICATE-----\nMIIHFDCCBPygAwIBAgIUZJOYHaqMZR7leKm8iaKrR380T8QwDQYJKoZIhvcNAQEN\nBQAwdjELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MSowKAYDVQQDEyFPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBSb290IENBIC0gRzIwHhcNMjMwMzA5MTQzNjAwWhcNMzMw\nMzA2MTQzNjAwWjB5MQswCQYDVQQGEwJCUjEcMBoGA1UEChMTT3BlbiBGaW5hbmNl\nIEJyYXNpbDEdMBsGA1UECxMUT3BlbiBGaW5hbmNlIHNhbmRib3gxLTArBgNVBAMT\nJE9wZW4gRmluYW5jZSBzYW5kYm94IElzc3VpbmcgQ0EgLSBHMjCCASIwDQYJKoZI\nhvcNAQEBBQADggEPADCCAQoCggEBAJJZYsafIn0x1j8WLDfJ3HSXt65NqnKwGdcW\nn4z4VqdrvcIl6kJM7cjF3ImaN5SLideuK63/QP4tgGilZxooxLE8V8M/uPgGU74K\noTMBuDho6sND/UtHsr/wgkX9+/Kn50vdLbhXZBmvcL+5gtXKDQGR+d1LyaU8EigX\nkhvegMCSyW72PlQ9FetapanOpH0e5+osGRVI9ysm7PFrWE6UOs8EA/d6+v8SwHTW\nbD6iVVgtGnQtm0C4w4H6VVNnFE0F8pSnXQQPzQXMONIFi/UZPSB00H0qnxRvWkw3\nJa7QErS8hdMPGUHQ9N/RujhMhf7tlUArcgod6mc+SYfcI3j1pUcCAwEAAaOCApUw\nggKRMA4GA1UdDwEB/wQEAwIBBjASBgNVHRMBAf8ECDAGAQH/AgEAMB0GA1UdDgQW\nBBR67wuI2HqJ4b0vBD0esdbER0IoPTAfBgNVHSMEGDAWgBQVb9vsej3AhKXXgbWR\nvfmoWNM++jBZBggrBgEFBQcBAQRNMEswSQYIKwYBBQUHMAGGPWh0dHA6Ly9vY3Nw\nLnBraS1nMi5zYW5kYm94LmRpcmVjdG9yeS5vcGVuYmFua2luZ2JyYXNpbC5vcmcu\nYnIwWAYDVR0fBFEwTzBNoEugSYZHaHR0cDovL2NybC5wa2ktZzIuc2FuZGJveC5k\naXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL2lzc3Vlci5jcmwwggF0\nBgNVHSAEggFrMIIBZzCCAWMGCysGAQQBg7ovcAECMIIBUjCB9QYIKwYBBQUHAgIw\ngegMgeVUaGlzIENlcnRpZmljYXRlIGlzIHNvbGVseSBmb3IgdXNlIHdpdGggT3Bl\nbiBGaW5hbmNlIEJyYXNpbCBzYW5kYm94IEFQSXMgU2VydmljZXMuIEl0cyByZWNl\naXB0LCBwb3NzZXNzaW9uIG9yIHVzZSBjb25zdGl0dXRlcyBhY2NlcHRhbmNlIG9m\nIHRoZSBPcGVuIEZpbmFuY2UgQnJhc2lsIHNhbmRib3ggb2YgQVBJcyBDZXJ0aWZp\nY2F0ZSBQb2xpY3kgYW5kIHJlbGF0ZWQgZG9jdW1lbnRzIHRoZXJlaW4uMFgGCCsG\nAQUFBwIBFkxodHRwOi8vcmVwb3NpdG9yeS5wa2ktZzIuc2FuZGJveC5kaXJlY3Rv\ncnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL3BvbGljaWVzMA0GCSqGSIb3DQEB\nDQUAA4ICAQCANeSAlmJy3e9rrgTGShVCyMQhy68j3cAJyFzqCutyNMGHUgFOjAgD\nzIUQZmAepTDJdhJF+BoruBfAIJUr6tD9EBw2MZXiTLHZG9mqtGwsMbeI3o3R9Y3G\nEpGp72jIHw7mtUZdoaWcmgqxCWn6UT9bBKAkdt6KyRepPUy1YI59MZxpVOs5J0s2\nQFd3FRCNxdzgsuGqdxTb1Gre4I5E1vJWcp1Fe/kPdaOgPVC89M6uk3WYTnMNZ20N\n8K0ecXy8+E3K+to35berWn16g1ZrufylX6s2yyxcsUnh5KP1smFd8MePekKIW0SD\n8hqD1MtGQEmzdWrPCT9fZUzONj4VuDcl/vgfKUBsBszTmqwGF34G+663v10KUhga\nkCiIOZtkT9B+aESGAfczQiFO1h4cI52TKwEptfbplrFS2gILrzleqv0JoDDFYVhY\nV5AVDjqeHaniClCi10JdSN11LqNdagpyojN2a2WhVSAigIT3yDeqozlzjgPui/1E\nDt0zBkXd5uFDwNeLUwOribuS3hxVG5Bg73ZJl+UV3ZuAzFFCfkVBz6BeqUusf8+P\n3pqAQ4gzhSWNsTBIsjaVV8ZU8IqxKhBkRUSNjihG2kM8kX9knQvRbCBuuse/dDUe\n4cUJ+wT1omVgq+TWhShOAjsHEa233omXbH7v5igLBEkzzqmM5cAv8Q==\n-----END CERTIFICATE-----\n-----BEGIN CERTIFICATE-----\nMIIFvDCCA6SgAwIBAgIUKhBUxL5Dt4w3xH1V3X1n+x/e3hcwDQYJKoZIhvcNAQEN\nBQAwdjELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MSowKAYDVQQDEyFPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBSb290IENBIC0gRzIwHhcNMjMwMzA5MTQzNjAwWhcNMzgw\nMzA1MTQzNjAwWjB2MQswCQYDVQQGEwJCUjEcMBoGA1UEChMTT3BlbiBGaW5hbmNl\nIEJyYXNpbDEdMBsGA1UECxMUT3BlbiBGaW5hbmNlIHNhbmRib3gxKjAoBgNVBAMT\nIU9wZW4gRmluYW5jZSBzYW5kYm94IFJvb3QgQ0EgLSBHMjCCAiIwDQYJKoZIhvcN\nAQEBBQADggIPADCCAgoCggIBALJFBgmKj3iDF3C8+8smNNQDxLFA9kCcca1iaxQf\nvMI/FKGW2ullHhH+W3EGEajn39QOlccGyrfCONHLqMW53+HAMtwiIvcrJgj72V7D\nnYflO3aaCFwoC31PL1+pMBo88F6jvezZ8BlRnheT7urCs6+onhz8pm0cVNc77U5X\npi8IOJz1QFKecJnFLjG0NiLCzOzjLSo0A8Rue9K/H5fjq+PqKdXG94AoQyFUwlsU\ny4aXbylDz1kRiOSnOlRNPcY/su95pFKQbGgaZZ1fLf89i5PtHAUu92FbD7H7OyYX\nXpZ97La0d7cUH0A4nb+LpOd/f0c8lAN2Ya1B8aKvWiF23q3c8EoAJyhrdkHKe6yI\nYvLC5G5jkbJefeQcp34IgD8T+Tn3aBF7YgmlYUMbnsuokBG28Hr50EAklCclA0bb\n4pmf8nE6y7VQ0CM/bNZd1F9AjxLukkyvkrOD6A6uv+c5KeC+da245dBzsyhiKe9R\nRX5Gkf7NSkDu9b9YkdDaWV6LXxpUA0SmdT9M16yK3XPDKOWBI4gVSB1KuwrOcal/\ndMwFUlxvqdGugRbxDNNukxa0l3JztGg6XYLjEiiYrQ+7HChbUVNlM0l0VZAz4eON\ngYrq2ExUDWlQXiES389/Qz3R3yDk9ib1YsMHwAux2ulCssFVn4EgtnYFfgf3o01J\n3CedAgMBAAGjQjBAMA4GA1UdDwEB/wQEAwIBBjAPBgNVHRMBAf8EBTADAQH/MB0G\nA1UdDgQWBBQVb9vsej3AhKXXgbWRvfmoWNM++jANBgkqhkiG9w0BAQ0FAAOCAgEA\nVPrUd4UDjOhkxOzSN4bMr0cULZJwQPRV8aj99tzdv8Ef44CwLVkLmm7Z2d1uRA9l\n7xbK6W8L1oL95iV4K4o2u4+ZFG7mrOfU2T2wgTfMlIxHDoAxS49flUYkBpQI1Wj4\nJBZ6fKGFVH6PyIio0I2Mx2u80ZX6lPYQ2q4DR6eBUoNt8T8XSWpD4TjroFbOVIp+\nN84alBca/pvW2aF2HwPndrL/Y++HZp3TpdUeBUT757KOZ7hdwf30pxd8qNn8+peb\nbP2h6b9pjKAmS8ciBExJzchhQWJRP6LIdvexTsBQ1HLxlZNrlg66wYT0kuVVzRTa\n0qRvIjQ0ntmhy2DtmE5VFT9O8ahcQL5Ddk8B4dhiy59vjALS6kIUXJ6GCobzRUsQ\na7b7J7nu+PTY+qVo0LsTMO1rVTUXD63gVk8QmPUwnvduk9nxraNpVP+m17BuEcls\nEsoGAAQYcmzOlnZpqhhbTnbsEayW1bMyxkLjBjXpOfBgrvyv5fU/09lP6VB20FJr\nzVPZWr5PTzaaizDDecSKgZ1ANIwXIIwWirwzDqqQb922JtcH+Ca6JJWgrV7+kDCU\ncVzwKVYievjXMCsmRSzDKEgp4n1AgrxcoaH0smD+qA+wzfsMqvEA1iTNW7zdnF0o\n6UJ9rkWxKr+JRZ5jFO+kpKQ1DxfDJZE554aO8AXzYEI=\n-----END CERTIFICATE-----\n"
  }
}
```

</details>

<details>
<summary>JSON Configuration for Payments v5 Change QRDN (Auto Redirect)</summary>

```
{
  "alias": "obbsb",
  "description": "Phase 3 Payments v5 - pipeline",
  "server": {
    "discoveryUrl": "https://auth.mockbank.openbankingbrasil.org.br/.well-known/openid-configuration"
  },
  "directory": {
    "discoveryUrl": "https://auth.sandbox.directory.openbankingbrasil.org.br/.well-known/openid-configuration",
    "apibase": "https://matls-api.sandbox.directory.openbankingbrasil.org.br/",
    "keystore": "https://keystore.sandbox.directory.openbankingbrasil.org.br/",
    "client_id": "984e85a9-9001-40eb-97b3-194f5afbd956"
  },
  "resource": {
    "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
    "brazilPaymentConsent": {
      "data": {
        "loggedUser": {
          "document": {
            "identification": "76109277673",
            "rel": "CPF"
          }
        },
        "creditor": {
          "personType": "PESSOA_NATURAL",
          "cpfCnpj": "48847377765",
          "name": "Marco Antonio de Brito"
        },
        "payment": {
          "type": "PIX",
          "date": "2021-01-01",
          "currency": "BRL",
          "amount": "1333.00",
          "details": {
            "localInstrument": "DICT",
            "proxy": "12345678901",
            "creditorAccount": {
              "ispb": "12345678",
              "issuer": "1774",
              "number": "1234567890",
              "accountType": "CACC"
            }
          }
        },
        "debtorAccount": {
          "ispb": "12345678",
          "issuer": "6272",
          "number": "94088392",
          "accountType": "CACC"
        }
      }
    },
    "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
    "brazilQrdnPaymentConsent": {
      "data": {
        "loggedUser": {
          "document": {
            "identification": "76109277673",
            "rel": "CPF"
          }
        },
        "creditor": {
          "personType": "PESSOA_NATURAL",
          "cpfCnpj": "48847377765",
          "name": "Marco Antonio de Brito"
        },
        "payment": {
          "type": "PIX",
          "currency": "BRL",
          "amount": "1333.00",
          "originalValue": "1000.00",
          "changeValue": "333.00",
          "igbeTownCode": "oiweowew",
          "details": {
            "localInstrument": "QRDN",
            "proxy": "cliente-a00001@pix.bcb.gov.br",
            "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
            "payloadJWS": "header.payload.signature",
            "creditorAccount": {
              "ispb": "12345678",
              "issuer": "1774",
              "number": "1234567890",
              "accountType": "CACC"
            }
          }
        },
        "debtorAccount": {
          "ispb": "12345678",
          "issuer": "6272",
          "number": "94088392",
          "accountType": "CACC"
        }
      }
    },
    "brazilQrdnCnpj": "43142666000197",
    "loggedUserIdentification": "76109277673",
    "debtorAccountIspb": "12345678",
    "debtorAccountIssuer": "1774",
    "debtorAccountNumber": "94088392",
    "debtorAccountType": "CACC",
    "paymentAmount": "1333.00",
    "transactionIdentifier": "E00038166201907261iuhiuhuih559y6j6"
  },
  "conditionalResources": {
    "brazilCpfTemporization": "76109277673"
  },
  "consent": {},
  "browser": [
    {
      "match": "https://auth.mockbank.openbankingbrasil.org.br/auth*",
      "tasks": [
        {
          "task": "Login",
          "optional": true,
          "match": "https://auth.mockbank.openbankingbrasil.org.br/interaction*",
          "commands": [
            [
              "text",
              "name",
              "login",
              "ralph.bragg@gmail.com",
              "optional"
            ],
            [
              "text",
              "name",
              "password",
              "P@ssword01",
              "optional"
            ],
            [
              "click",
              "xpath",
              "//button[contains(text(),\"Sign in\")]",
              "optional"
            ]
          ]
        },
        {
          "task": "Consent",
          "optional": true,
          "match": "https://auth.mockbank.openbankingbrasil.org.br/interaction*",
          "commands": [
            [
              "wait",
              "xpath",
              "//*",
              60,
              ".*Before proceeding, we need to confirm some information:*",
              "update-image-placeholder-optional"
            ],
            [
              "click",
              "xpath",
              "//input[@id='consent-toggle']/following-sibling::div[1]"
            ],
            [
              "click",
              "id",
              "continue-button"
            ]
          ]
        },
        {
          "task": "Verify Complete",
          "match": "*/test/*/callback*",
          "commands": [
            [
              "wait",
              "id",
              "submission_complete",
              10
            ]
          ]
        }
      ]
    }
  ],
  "client": {
    "jwks": {
      "keys": [
        {
          "alg": "PS256",
          "d": "Q9gSOfnkGJnAsV3a94j9ae9ihjqgMwXgVm73VTyEs1u9Jq73pCWX0e9JdeNMKdgKpiJYjyxa3ttxCY58eiGKEi7c50zYRx8YLTL2rIVWqS6JVGpXuzIQutkQDM4AfD72bG3-xT-caSCansGbdEIFJjX32Ujbs1UUoQlE96m3hNOjB5vNyHBWrBUgUGG9_uJiWFG6Lbj8ZGtiihA_PQkzuArLzDvO2OMVHCzIyQ4CwFE1tI9xHFHpioJQXBnymURQvkm3MmEwHRG_KUdABQ55gG32jothy7jOOYAMkvOCejteTZv1nT4dsEj-CBxDBtTI6SerXb11VX8b0suzSBxx0Q",
          "dp": "S15AOPpOtYgYjfOi2rNojY3NpU-Qobnfnnt_MZEJ2_DS0bGwXSgGJjHOOOAowy1HK0n7-AhXbwhr026sBuicR_Kpj6RkzGVrJug8y9R02FXZwlQpgjSBZdO6C2B1OOvtyKmnKg5q1KdQ7Kx6vYPV7UutOJn6NlH0RbFgG4NGelk",
          "dq": "oBgBMB54mtrriQCg4YyDY_zf7LW4f6oqiUl3l7odf_ArjVamjHM-boZnhGoVzZ5uXNs03wEdBIc2HLmsoGLVuodcYHjyptmvyPebiH2mavFlUlI8ILG6lkyIhMp3Ri8iXGX2MYlPjP2EawNDMHB6BO0bZ5NugyzxuF_OKhfEFLc",
          "e": "AQAB",
          "kid": "-duNE0ZX5NmDkUlgNoqDY5Ve7UdFTA7S25WJSAv8tNQ",
          "kty": "RSA",
          "n": "-6Ep5kV0qcQnrxQzbEgMGKQRHnhXlp3ZpAVqQbbzkVG_a1tHLi0V7YAmjf3isXMvdvWjApeShL32gqxgcKDvC5Mnd5ufR1ujzb5lsnYXy-tKMQWnAlCqy7mSuxi8JIBXyZb7CMGU29L32Tvd5MjDh_hSgwnHcTggE-ehqzK5eyvK7DjvlbfCKXgDx94kMcwyI2K0EurahHj9_I3lEQzAt73OocF_z84FQxO87A8Q1cM3nEGyykZPaFyulQ4bf4U2tT_Jfd0ppYX1j194ouPeqMZBsGnxKf4L4QvuberbRpdeOO92HhWHHiwiTuhYxF876-LKgPzqxK-Y1a2_4gsVAw",
          "p": "_oebNFofSe_8fdotMxUEk7n3pq5eT96rO_VPdHyTZERDrkU0djQf9BLy7DejYoRReuI0AJWkBL9EGBhECaowmx8gTCs43ffQrBDULYB4elmS07ov1pq1STqzqRKbu_INaSGVgxFzhYC_EeFVpB0RPlAUvb1_aQkH79J8VMnp2_U",
          "q": "_RVEyO9NB6XiJjMz9t6XrNxG01Vguo2VVBLaDJhoi1g7gydUDkNc9twhF1Ifps8Gf3m9aMjjOmYqE5kuWCPBHxkk8cZOm4C2AhVbQxMkZLOyPeJDfKfCi7yJRIfmwqQM5AKosALfN-jW_p746lRhCAps8eH9XF6bjugi_MH1yhc",
          "qi": "yXG_vCx0xL9DlU7f0Ixub9NSD1QJtAJYxwKyHukw_8f4rHLiZ8eeCerfZfPd7zsPGSqOmY2605MNT1Z2ohYgoRyu05uwstEDKqtgl_uxupfO6AJKCja4paIB-ICvQQXpOY1n9BW6VcDwSylTnv1pKvVnTvxzy5z008wvrafQtFw",
          "use": "sig"
        },
        {
          "kty": "RSA",
          "alg": "PS256",
          "use": "enc",
          "kid": "e96744c58188c084310920b152ffb02a392b119a009fb1fa1a656006715e1604",
          "n": "4eIXvOR1XXo3MT9syMwRZj2ChbV2Qlp_623VCIhYvPtJ5k5rlCr1hP4n0PC49U47pa3UKNs6DYHefHKm9I4h4crgk7zsln2_JP3kK1equqIO1U12Rv4Xbm_2_eqR3hPKcE3il2ky2Neby8OThFnyDwBNKdxI4MvOKm910qQhYns2L4w_i9fjF2z1Wpi6sMPW8IERhkqaBWgoaH9g2obGbNuoYCzEjOWvRb_nVjYKRPqTI2A11kWZ4mVTRkTO4yM1gdI7z8Hsl4fqlEXeVdmMkVJhRvQa-vFfegecgO8nUY2XoOUx_UR51F8PO9bepy-jH16cRDwjLE-2ex7mE_wfMw",
          "e": "AQAB",
          "d": "BqovoVF4vww8nA9IuLhnHDlDZFbHov4qZeCecQgcEJNpIxdiqDZuR4EvECsSIgOWOFvwW-lzOI1oHaVNlMvezXU5eoWpnpuEnzHlYHwCzxftNrde5PBZWHC-sAMStvBzJpLw7riNZgWFx_wNmoTQfHqgGQfLyxcB9Pf6v387qiN1wHfSXQshtFiDg_6tBaH6dS1jRAg7_56dQp1wWJeRaqMCg9QeESmo3c-76hnRSMU6fgrONU6qGMSLopv-nirh3H1gZePcXzVgf9cerRMQgV1pWUZEd_iJqTaX8U7wB0txmVF6QzRxR71Ah6nZuV_Rv7X88zB8u0rXOvjeGtuZKQ",
          "p": "8fN0GXyZnvxba4yoOgdL9ta9pkjjWVu5eTOIyvSgKf09hUSWKL6sKm1N0l68detwzBFpnxObOeUCMnU_BFhJM-s0w5GognaAX6GB5-TzdYHwmsgqAch3-_hi_kZU6A-SLZu7bQFGXTEotQ1zMxVuCMZ7AjTs0CGZrS-vItFYtik",
          "q": "7v_Ldwh3L9On2CNAefLgs7dyDBAgWrkXOJ9Z1EnrKgMHbqgq5dOixv2ezKNdOUte9G4ve555XTf2sC-p0TF9PNYC0_4KthI8NLik8RtDsQmYJUYw7qfV_YitzGflM2DRr6KaV5SmO_aPWRfzuVWh_6kIQ_GmXf47ASasKVeD_fs",
          "dp": "Jyi-_q0C9A9mAHcodxPdQJsq4LHlUf4de7dSiX6kOYeKIHqkTv3lQYylTsoUeIVdoTmkPaHfurQM8fu18k8Tsfp8dLarbkodptyt-Mk-eiNIvNRusBExEi_2Xa8maNS0VPtij1boe4bMTtlZbsgmIfd1yzqjpV_6zmPsVZdKY1k",
          "dq": "qjW-YA3FZGhmtwWUG8Wfxh41uOWbRUFgilDils_2DTuPBX363yc0XGevuqn18KH_BDGc23tnj74VkDDBzlxihvsblILuefDOs_V0csoqEWF128X7f1xEiIXY0SSFFWw0qdMx_IG_SiE0wgzO5QVZlEx7uHfXNkWjHBTAs8jCFhU",
          "qi": "8W2vDdiA8qDxL2fiJPP2m3NqbjGW7Tf5PsfGo0Gqfv6nWVweuVwsyUNT1AYduZUCvFRG5LRNHqiwZNpNB6XQln1W41GaIqGkHWJkveHhg9xIQmSK2hrX4OnSdyvMiGiB2yvce0FTgQ0OzXuNkIKJKJLP2nAJusNgNcVT7qgKCRA"
        }
      ]
    },
    "org_jwks": {
      "keys": [
        {
          "d": "BpgLagicLjysglxtDX7bJnOv4-IP-5yyGdL4oOkDCl_-lO8twPDhWLfXNCf2QTs7l1T1GLNUyALKjYDNEvjbpu03_K1dtRwO2ZS4_VHTPhe99Etn1GXntdfcFvQiD9Lz6uzs2-0DOIG_5xWUiVhTUN5HPRfMMXF3ktG2ucTOQqsJU0O2SOohVIvqYH4EDJNIw8qUsu1C2JEDMj79H_8KaXEUVx8tFFLMxmt67a_a7sImXvEaIYhUCu-DMMDrzBc660s_eTcihJ_DkJgYPPWctnmpUClKa4zgABDqGXhPQFfLS4ywGAHnLZF1MyNeKFXpmeJShjNJ5MqjBKJTnFHDQKs",
          "dp": "CFfrENWCU61YHATfdTy73lt2reMz0dBDicy92s4FqHpcup6O6f5MWGvhpBlLVC-tNA97qzyKExFwxl6c6rf45l8T6GLjy4C2DJEH0pGKeh7-PP7XW1KBvsclbJdSoSj-bOFRomFVGKYhIF3nRnr9-Dvj1k8aEcClPT1E9i9rGI7P",
          "dq": "BzCeCJQ9pKQVCpyFi50PR8_E7d9uW9nYqJpf0GBT5XdnZ44qnliLAffZmVwcxXh6e_JzIjC0ByJrYKd_dekXLCrsOex1XxqvI7WH6EZ3Nvoe_1835ZgtQ2PsPSvGKifHHPXocKyqqRdT7KlGTXfnpKtezsXPxe63VS-3coE62-_F",
          "e": "AQAB",
          "kid": "EKSYJfNcI8Bm22_dP0ziWpTjw9UceAdVjykgwO5BkfE",
          "kty": "RSA",
          "n": "oBp-b0EhezRYfisJBL_WA2Yh0Y2zPYHsy8N4G9mddkop-kFJT12XSSBx8GXmyjDL14Wg5vRNA6R_TwXbJbnHnE59uMYiWNi_G7OL6jMsncmYdyBuwl-lDWExaXC5Qg9vYgGnt7d1SthQoiJkduPIiNpniq5p7px-jJYQO4SECUqpeLl9rU_Xvxn5zpFu4dw65wBi4oSDiJ0zujQtxofOmbJCKYTWrPmd8yPlPgwIttP2ZcprMs5Ya57-99NhAealcVptRTOQTEWEOflmurq58Byu7pT64ns-9Su8JPcHMMzxOOVM7KNPuZA7Xa5-1aBd1XrhxkBHIDzUqOpanSlr2uk",
          "p": "DgL5bOQ5-JXM6Ed_3BRKW2a3EcHB_UjlWPlGGkc0RBeEwlNi6D3PQGZmgTxyGXWA4W3HMi2S2pXx8oxWd9rrw9Uc_BNrIdvkMcU9LnkCvxK-dcHalVrXhv0l1EbQx0mG9LjLsiqmJiJYnUYTuLjO8lJaebSTp-EH2fgTs81_SBKv",
          "q": "C20t29WtF9yAXt2r5Yu7chtrJUMIsu_TUY2N6p75BWWBB76oNib4Dp5fVePnbTqdSP913dS1K1vHwEAqS_Z_C6vfmaYha6Hguipo5jotTTJoYDxV_xTp1dGWcr8MltBE9ikhLa8xvGVxXjSi4vkqc_TyXlBSHbbBSZtjB32rCLHn",
          "qi": "BRx-2fqZYWrIzcayN1v10HfzcQaZue-NNZP7Eid81oBBxBrDQmiGdzQLi0BKctjLBr21_GWUgHgEYRym3He5biuDVM0WnyhXYeLLc_pv3bIG6FoPrP4XDZo4GTM4JdVj2im_OQWdXuokFzsZzeVV6H8p46TxpyNDix5oFjmyuB11",
          "alg": "PS256",
          "use": "sig"
        },
        {
          "p": "2a8fRJ7ybF-qtF1zrYzSm7z3C4wNTUMbVYqe44tR9FbKsobqW2tS0iAZf-GJ_SZPcWxkE76gunW7YqMJecGUtXsJ8TTHwjcPQOMYzxnyJu8Q4JOj01YJVrxUY9D0ZzpWM9oTAj1-qoE0w7Dy-XNUc14-HeRlmOkg2tTfrXTVR8c",
          "kty": "RSA",
          "q": "0xlPJFRUcBU5j2SKSajVnd4H5p88RSsd4cArMby1ZRuSeHEsX76c6QKAPq7uTfKrTeZic34yzAEUyHloP1fZQYQ2UQn-f6PsTAWdT1Lp5oi2VZCT0yc9-1EGnLAiUCbM9SQQyf2GIVhCiAk_0VuY6le61Pw0U4GssvFJzIrx4as",
          "d": "GxnizpWcqL1wajD8-Y-8H9-II4UZMKfkgbfwRiLK9uAd8-kEJdO9jdNeMxyytg2saDhxNTeRTkYz_VbBf3p9dGhuYx84d-ZagUbIiU3ho3FCsBRrzQQZw9OQrzPDUzp0-SBn1_GLCf9fo4ysxWHbn9euJVi2fpN_bHlBi1n8fKhdBHYE7X3XJnRYrUXItxZw5sJsqM_boONLxdLAvgmZx5CHft94JZsR6JPwlj9Ba_CuNWX_3OuUGyV0f5_1ICAEYijw9PA8KAW6t5UUYn39_KYL8nF5L1Bh6W1j8eN84I2lcKZNO6Pou064ag_wqGhk4uXuQO1IV8jRFn3-pqhSEQ",
          "e": "AQAB",
          "use": "enc",
          "kid": "c1d7b80ce4b88c4f2cfb68e7a8c45bfff355ae94259bc1a73a95ddbaeaf7c96b",
          "qi": "pU1IXwiQoFERdzJsx7kSC79Gwhak7uw7OAJCbcfkKE3GSwTWHrKfg5uDZlNvSnNU1Hbpxd0bgc40dFI2aNBML1gyDwTjQplWVJikkFix8E6z_ErSa_D5w5yV4k6CNtt7OzlMXawiZ-ndcuiOs5MkfSRyeB3k5rQmuZjLVzFFlnw",
          "dp": "Gn4dqBRQHLBn7huRgIWq_Bk7V8RrugN4yChevgKurrYBZUjWLNoa8kfF0rJ4QL7w3DT82QpSNV8utwpwlMjieFPJGfn6dcCNsq_wzQOzXNmrjClrvsSxzkSNYLiFhiqrYxQfTB5_0_B1o3tdls5acM__b1PkqX916CwQLOQTMPE",
          "alg": "PS256",
          "dq": "NS0x94fawWVHW6zK_SUvspXkzZ6dMxtaaqza9KuB0ldwvTBdKj09D6FWpvOwCiiwKG55rHhE2YkIMDwNG6_Iha2FdUKcPpEPjFL5vqq3SyBzNfi2lEFVZsKRdNUVv7UWekY8iHV53Vp7YANcdSOq0JWK9e4WTFblJyqLGaCCsAM",
          "n": "s4DcK4uxKroJPE1R7Te4ppNexbuK3C-Z3MpXFr5hmY43gYIoVMo89jE6OcDiO0Z4rxe8dsH4oYA2vAJQ0IhAaUxYMk2kN01ei761zMQWHLUPLcEKWgipYHy4AgwAUaF7-Glyb0DT1RRcY4f1tEddftxhwXZjeFduj6luVg6fVvXRIRjttybUkIKvf5ShMofVFCF_IyjYlOal4g3DVnCg62dR71WX3fRXSufxrRBG-L61rv2VSMg8pIb1DFiYKDlEXEnTdLk-7goBpTIz3wBsrZgJESSZOn_BG_-fCE0V75rheLMuJd4IGE4H0taVfEQOJKRKBVzc2jAz0sOaVuPY7Q"
        }
      ]
    },
    "client_id": "Jj-hosRwYqvtnQZNph2Ah"
  },
  "mtls": {
    "cert": "-----BEGIN CERTIFICATE-----\nMIIHQDCCBiigAwIBAgIUOyyDtirdgYQIT/eSBtvaP5JRcoswDQYJKoZIhvcNAQEL\nBQAweTELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MS0wKwYDVQQDEyRPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBJc3N1aW5nIENBIC0gRzIwHhcNMjUxMTA1MjAzMjAwWhcN\nMjYxMjA1MjAzMjAwWjCCAUoxCzAJBgNVBAYTAkJSMQswCQYDVQQIEwJVSzEPMA0G\nA1UEBxMGTE9ORE9OMSYwJAYDVQQKEx1PcGVuIEJhbmtpbmcgQnJhc2lsIC0gUmFp\nZGlhbTEtMCsGA1UECxMkYjk2MWM0ZWItNTA5ZC00ZWRmLWFmZWItMzU2NDJiMzgx\nODVkMUMwQQYDVQQDEzpodHRwczovL3dlYi5jb25mb3JtYW5jZS5kaXJlY3Rvcnku\nb3BlbmJhbmtpbmdicmFzaWwub3JnLmJyMRcwFQYDVQQFEw4wMDAwMDAxMDc0Mjg1\nMTEdMBsGA1UEDxMUUHJpdmF0ZSBPcmdhbml6YXRpb24xEzARBgsrBgEEAYI3PAIB\nAxMCVUsxNDAyBgoJkiaJk/IsZAEBEyQ5ODRlODVhOS05MDAxLTQwZWItOTdiMy0x\nOTRmNWFmYmQ5NTYwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQC8bzfe\nH4l2IegWdHsOIooz+nUxpfI5v23ubPsB0P9rLEoPlIn0A7E2zg/b7UCQFvzmzgao\n49DYEbaR5B5rutlRn52rkHufNF2fNEGXgtqrko/Uwf2tGDpve+e6MRuXhyYUEwaq\nMIRL9RCqDSTHFUS+QoNaPdccw9yAQkffEckKoXJA5GYkLvkZ06Vh8R7L6Agjh1VN\ntbT3v+STfrIbSYcEXJoHwWn7vnSewcJm3B1yxpKAVySFbL336yu0cYU8RkZ42SBh\nJmGD96kmJ+vuTXQBs5ZTndbZo6/UO+r3+qaQ8rK1r4qeEYaOwSYh9wsFxpLJIgyC\nwnl0XQQnwjQKKConAgMBAAGjggLrMIIC5zAMBgNVHRMBAf8EAjAAMB0GA1UdDgQW\nBBTLmBupVqnHkdd6f2hhj5mRrTUZnzAfBgNVHSMEGDAWgBR67wuI2HqJ4b0vBD0e\nsdbER0IoPTBZBggrBgEFBQcBAQRNMEswSQYIKwYBBQUHMAGGPWh0dHA6Ly9vY3Nw\nLnBraS1nMi5zYW5kYm94LmRpcmVjdG9yeS5vcGVuYmFua2luZ2JyYXNpbC5vcmcu\nYnIwWAYDVR0fBFEwTzBNoEugSYZHaHR0cDovL2NybC5wa2ktZzIuc2FuZGJveC5k\naXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL2lzc3Vlci5jcmwwRQYD\nVR0RBD4wPII6aHR0cHM6Ly93ZWIuY29uZm9ybWFuY2UuZGlyZWN0b3J5Lm9wZW5i\nYW5raW5nYnJhc2lsLm9yZy5icjAOBgNVHQ8BAf8EBAMCBaAwEwYDVR0lBAwwCgYI\nKwYBBQUHAwIwggF0BgNVHSAEggFrMIIBZzCCAWMGCysGAQQBg7ovcAECMIIBUjCB\n9QYIKwYBBQUHAgIwgegMgeVUaGlzIENlcnRpZmljYXRlIGlzIHNvbGVseSBmb3Ig\ndXNlIHdpdGggT3BlbiBGaW5hbmNlIEJyYXNpbCBzYW5kYm94IEFQSXMgU2Vydmlj\nZXMuIEl0cyByZWNlaXB0LCBwb3NzZXNzaW9uIG9yIHVzZSBjb25zdGl0dXRlcyBh\nY2NlcHRhbmNlIG9mIHRoZSBPcGVuIEZpbmFuY2UgQnJhc2lsIHNhbmRib3ggb2Yg\nQVBJcyBDZXJ0aWZpY2F0ZSBQb2xpY3kgYW5kIHJlbGF0ZWQgZG9jdW1lbnRzIHRo\nZXJlaW4uMFgGCCsGAQUFBwIBFkxodHRwOi8vcmVwb3NpdG9yeS5wa2ktZzIuc2Fu\nZGJveC5kaXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL3BvbGljaWVz\nMA0GCSqGSIb3DQEBCwUAA4IBAQAjJQE5R9iYGgnrEpEOUGNFVqHYs8L8Y1quoglO\nYsz1GhC2bzm7WSo7iRXfil5D8om6BDM+2TsMkvH21yeNnIclIrK/ReDHqkubbWoa\n9awJDNVa6VoNRdCB6dqEiLwZl4p+bacoShQCd113v5B76gVyCPBmId41rDJv/beB\nv7F894KM4LMMkkZGSnrGft9fc8Y2CPN452EgnTh41PhJHK8DVw8mtx704gblJ64B\nwqhogdzyAjY1uz+a3M1gTTCkEEkuhYXYrHDXgz327JRCW2oXKj7oMMszMI5E4uYL\n/QQijgFOoCPdX+/SvXZo7uMl0dtegLOR/oHxOwLuryqBk9mG\n-----END CERTIFICATE-----",
    "key": "-----BEGIN PRIVATE KEY-----\nMIIEvQIBADANBgkqhkiG9w0BAQEFAASCBKcwggSjAgEAAoIBAQC8bzfeH4l2IegW\ndHsOIooz+nUxpfI5v23ubPsB0P9rLEoPlIn0A7E2zg/b7UCQFvzmzgao49DYEbaR\n5B5rutlRn52rkHufNF2fNEGXgtqrko/Uwf2tGDpve+e6MRuXhyYUEwaqMIRL9RCq\nDSTHFUS+QoNaPdccw9yAQkffEckKoXJA5GYkLvkZ06Vh8R7L6Agjh1VNtbT3v+ST\nfrIbSYcEXJoHwWn7vnSewcJm3B1yxpKAVySFbL336yu0cYU8RkZ42SBhJmGD96km\nJ+vuTXQBs5ZTndbZo6/UO+r3+qaQ8rK1r4qeEYaOwSYh9wsFxpLJIgyCwnl0XQQn\nwjQKKConAgMBAAECggEAJwYvf0hvuu/dtVzNKUm87nPVtoEED7KV7TVTrHYgl4z2\nD5D3GvpyxoNZZHYXk1+3Y4NSfMKle0H72e3w4OWy4QUZ7bB/8aIyK2jylpKqf7Lc\nJ7c/NoxYecMi4/wMl06Nc8XW8QMYOvTXTShor/Q3JuH2ewdol9P2Q/e2E7wGszUN\n9Of74KkoQ1bGf8Z3eutjqdP35/n6cETQDoFiqsV8DfHQGCiiNPKWGD2asQDhhRx4\nvh0TGIxvWF5lnSSxvbGsNFUoGWxr8eUH/EGcH1UnHfYL4xhUYqWTEOhM2v/csmzY\nt8o4BntudmXxlfgYU3NyPKkyx7/bVcnW1PJVtoDKkQKBgQDv7j0jjaWt6dJwsKa0\n5XQ4Xga1PbpDb3LWfzZr3IScUxbVytTnOWVXpok4esn4S00iQpAp7FV3YZ/qox7p\ngcOgV7lW6CIShnLgmr4CEt1hV/sRvqddmmgfrY4ZJLy24MSxwBeZiUPNRHKl9RZA\nJr2WsM04JPE4mmf9QOpGjjy71wKBgQDJDguPpQflCGT8s2KNQjBGnWGVfdNHd1vF\nOFP79wkROAEBb2mJsuBBl8Iu3YvImaKAyAln3uqOhQ8rr+y12DqBRgoAyHY3dr46\nlhQFDonNGVdOxrwRnxajKft32W8Tn6pdjuIs4N5q23Luqym5l9PA6h8aa3E+7yeE\ncvRIfqK6MQKBgG4OjED4wpzp+rvybCXictNAXjdY3037m2PE6sPDXZkPjBP5fHus\nGk6Ad8VOncKlV/Z1Lgfs/q9KOr64oH9gJMoyMzQoOyjgP2XD1ZDB8oaqguJ63+7R\n2x1c0Se7cE07AT6/7JNjIZTQ5v41VEWM/75Vz20HlRbvzO+gjVZb/IP1AoGANJwd\nQFhByZe5vTo/dpE0SrYR++kx6Qh9lgzYRR1uXPgXo0WBC0woTGGmqVbFphc1o5c0\nht6Y5/Q/dQIS4b6UCJHIOk46SOckffYZhP0559ZSt0VfnwjPBqEMsV7PJwZnsRWb\nb3zkFngYCgX15B+rhFZ/Dw3AU2SHJaxi6blhYXECgYEAnBAJuYoIfZolppeUZXwp\nAYoTLGMtXnjvX/YFumlEWzjnXLo4Lk9L+lO9sV5BwhQ6klNBARy5TjAedr+Kw0ee\noGh8F964pkF4jy7qBLMkf4/jaEvft/2tg16ELOj74llsd5GPA8Pgzeh1AXtlowwi\nC1Ere9RQ/zspggyX1uEakrI=\n-----END PRIVATE KEY-----\n",
    "ca": "-----BEGIN CERTIFICATE-----\nMIIHFDCCBPygAwIBAgIUZJOYHaqMZR7leKm8iaKrR380T8QwDQYJKoZIhvcNAQEN\nBQAwdjELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MSowKAYDVQQDEyFPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBSb290IENBIC0gRzIwHhcNMjMwMzA5MTQzNjAwWhcNMzMw\nMzA2MTQzNjAwWjB5MQswCQYDVQQGEwJCUjEcMBoGA1UEChMTT3BlbiBGaW5hbmNl\nIEJyYXNpbDEdMBsGA1UECxMUT3BlbiBGaW5hbmNlIHNhbmRib3gxLTArBgNVBAMT\nJE9wZW4gRmluYW5jZSBzYW5kYm94IElzc3VpbmcgQ0EgLSBHMjCCASIwDQYJKoZI\nhvcNAQEBBQADggEPADCCAQoCggEBAJJZYsafIn0x1j8WLDfJ3HSXt65NqnKwGdcW\nn4z4VqdrvcIl6kJM7cjF3ImaN5SLideuK63/QP4tgGilZxooxLE8V8M/uPgGU74K\noTMBuDho6sND/UtHsr/wgkX9+/Kn50vdLbhXZBmvcL+5gtXKDQGR+d1LyaU8EigX\nkhvegMCSyW72PlQ9FetapanOpH0e5+osGRVI9ysm7PFrWE6UOs8EA/d6+v8SwHTW\nbD6iVVgtGnQtm0C4w4H6VVNnFE0F8pSnXQQPzQXMONIFi/UZPSB00H0qnxRvWkw3\nJa7QErS8hdMPGUHQ9N/RujhMhf7tlUArcgod6mc+SYfcI3j1pUcCAwEAAaOCApUw\nggKRMA4GA1UdDwEB/wQEAwIBBjASBgNVHRMBAf8ECDAGAQH/AgEAMB0GA1UdDgQW\nBBR67wuI2HqJ4b0vBD0esdbER0IoPTAfBgNVHSMEGDAWgBQVb9vsej3AhKXXgbWR\nvfmoWNM++jBZBggrBgEFBQcBAQRNMEswSQYIKwYBBQUHMAGGPWh0dHA6Ly9vY3Nw\nLnBraS1nMi5zYW5kYm94LmRpcmVjdG9yeS5vcGVuYmFua2luZ2JyYXNpbC5vcmcu\nYnIwWAYDVR0fBFEwTzBNoEugSYZHaHR0cDovL2NybC5wa2ktZzIuc2FuZGJveC5k\naXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL2lzc3Vlci5jcmwwggF0\nBgNVHSAEggFrMIIBZzCCAWMGCysGAQQBg7ovcAECMIIBUjCB9QYIKwYBBQUHAgIw\ngegMgeVUaGlzIENlcnRpZmljYXRlIGlzIHNvbGVseSBmb3IgdXNlIHdpdGggT3Bl\nbiBGaW5hbmNlIEJyYXNpbCBzYW5kYm94IEFQSXMgU2VydmljZXMuIEl0cyByZWNl\naXB0LCBwb3NzZXNzaW9uIG9yIHVzZSBjb25zdGl0dXRlcyBhY2NlcHRhbmNlIG9m\nIHRoZSBPcGVuIEZpbmFuY2UgQnJhc2lsIHNhbmRib3ggb2YgQVBJcyBDZXJ0aWZp\nY2F0ZSBQb2xpY3kgYW5kIHJlbGF0ZWQgZG9jdW1lbnRzIHRoZXJlaW4uMFgGCCsG\nAQUFBwIBFkxodHRwOi8vcmVwb3NpdG9yeS5wa2ktZzIuc2FuZGJveC5kaXJlY3Rv\ncnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL3BvbGljaWVzMA0GCSqGSIb3DQEB\nDQUAA4ICAQCANeSAlmJy3e9rrgTGShVCyMQhy68j3cAJyFzqCutyNMGHUgFOjAgD\nzIUQZmAepTDJdhJF+BoruBfAIJUr6tD9EBw2MZXiTLHZG9mqtGwsMbeI3o3R9Y3G\nEpGp72jIHw7mtUZdoaWcmgqxCWn6UT9bBKAkdt6KyRepPUy1YI59MZxpVOs5J0s2\nQFd3FRCNxdzgsuGqdxTb1Gre4I5E1vJWcp1Fe/kPdaOgPVC89M6uk3WYTnMNZ20N\n8K0ecXy8+E3K+to35berWn16g1ZrufylX6s2yyxcsUnh5KP1smFd8MePekKIW0SD\n8hqD1MtGQEmzdWrPCT9fZUzONj4VuDcl/vgfKUBsBszTmqwGF34G+663v10KUhga\nkCiIOZtkT9B+aESGAfczQiFO1h4cI52TKwEptfbplrFS2gILrzleqv0JoDDFYVhY\nV5AVDjqeHaniClCi10JdSN11LqNdagpyojN2a2WhVSAigIT3yDeqozlzjgPui/1E\nDt0zBkXd5uFDwNeLUwOribuS3hxVG5Bg73ZJl+UV3ZuAzFFCfkVBz6BeqUusf8+P\n3pqAQ4gzhSWNsTBIsjaVV8ZU8IqxKhBkRUSNjihG2kM8kX9knQvRbCBuuse/dDUe\n4cUJ+wT1omVgq+TWhShOAjsHEa233omXbH7v5igLBEkzzqmM5cAv8Q==\n-----END CERTIFICATE-----\n-----BEGIN CERTIFICATE-----\nMIIFvDCCA6SgAwIBAgIUKhBUxL5Dt4w3xH1V3X1n+x/e3hcwDQYJKoZIhvcNAQEN\nBQAwdjELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MSowKAYDVQQDEyFPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBSb290IENBIC0gRzIwHhcNMjMwMzA5MTQzNjAwWhcNMzgw\nMzA1MTQzNjAwWjB2MQswCQYDVQQGEwJCUjEcMBoGA1UEChMTT3BlbiBGaW5hbmNl\nIEJyYXNpbDEdMBsGA1UECxMUT3BlbiBGaW5hbmNlIHNhbmRib3gxKjAoBgNVBAMT\nIU9wZW4gRmluYW5jZSBzYW5kYm94IFJvb3QgQ0EgLSBHMjCCAiIwDQYJKoZIhvcN\nAQEBBQADggIPADCCAgoCggIBALJFBgmKj3iDF3C8+8smNNQDxLFA9kCcca1iaxQf\nvMI/FKGW2ullHhH+W3EGEajn39QOlccGyrfCONHLqMW53+HAMtwiIvcrJgj72V7D\nnYflO3aaCFwoC31PL1+pMBo88F6jvezZ8BlRnheT7urCs6+onhz8pm0cVNc77U5X\npi8IOJz1QFKecJnFLjG0NiLCzOzjLSo0A8Rue9K/H5fjq+PqKdXG94AoQyFUwlsU\ny4aXbylDz1kRiOSnOlRNPcY/su95pFKQbGgaZZ1fLf89i5PtHAUu92FbD7H7OyYX\nXpZ97La0d7cUH0A4nb+LpOd/f0c8lAN2Ya1B8aKvWiF23q3c8EoAJyhrdkHKe6yI\nYvLC5G5jkbJefeQcp34IgD8T+Tn3aBF7YgmlYUMbnsuokBG28Hr50EAklCclA0bb\n4pmf8nE6y7VQ0CM/bNZd1F9AjxLukkyvkrOD6A6uv+c5KeC+da245dBzsyhiKe9R\nRX5Gkf7NSkDu9b9YkdDaWV6LXxpUA0SmdT9M16yK3XPDKOWBI4gVSB1KuwrOcal/\ndMwFUlxvqdGugRbxDNNukxa0l3JztGg6XYLjEiiYrQ+7HChbUVNlM0l0VZAz4eON\ngYrq2ExUDWlQXiES389/Qz3R3yDk9ib1YsMHwAux2ulCssFVn4EgtnYFfgf3o01J\n3CedAgMBAAGjQjBAMA4GA1UdDwEB/wQEAwIBBjAPBgNVHRMBAf8EBTADAQH/MB0G\nA1UdDgQWBBQVb9vsej3AhKXXgbWRvfmoWNM++jANBgkqhkiG9w0BAQ0FAAOCAgEA\nVPrUd4UDjOhkxOzSN4bMr0cULZJwQPRV8aj99tzdv8Ef44CwLVkLmm7Z2d1uRA9l\n7xbK6W8L1oL95iV4K4o2u4+ZFG7mrOfU2T2wgTfMlIxHDoAxS49flUYkBpQI1Wj4\nJBZ6fKGFVH6PyIio0I2Mx2u80ZX6lPYQ2q4DR6eBUoNt8T8XSWpD4TjroFbOVIp+\nN84alBca/pvW2aF2HwPndrL/Y++HZp3TpdUeBUT757KOZ7hdwf30pxd8qNn8+peb\nbP2h6b9pjKAmS8ciBExJzchhQWJRP6LIdvexTsBQ1HLxlZNrlg66wYT0kuVVzRTa\n0qRvIjQ0ntmhy2DtmE5VFT9O8ahcQL5Ddk8B4dhiy59vjALS6kIUXJ6GCobzRUsQ\na7b7J7nu+PTY+qVo0LsTMO1rVTUXD63gVk8QmPUwnvduk9nxraNpVP+m17BuEcls\nEsoGAAQYcmzOlnZpqhhbTnbsEayW1bMyxkLjBjXpOfBgrvyv5fU/09lP6VB20FJr\nzVPZWr5PTzaaizDDecSKgZ1ANIwXIIwWirwzDqqQb922JtcH+Ca6JJWgrV7+kDCU\ncVzwKVYievjXMCsmRSzDKEgp4n1AgrxcoaH0smD+qA+wzfsMqvEA1iTNW7zdnF0o\n6UJ9rkWxKr+JRZ5jFO+kpKQ1DxfDJZE554aO8AXzYEI=\n-----END CERTIFICATE-----\n"
  }
}
```

</details>

<details>
<summary>JSON Configuration for Payments v5 Alphanumeric CNPJ (Auto Redirect)</summary>

```
{
    "alias": "obbsb",
    "description": "Phase 3 Payments v5 - pipeline",
    "server": {
        "discoveryUrl": "https://auth.mockbank.openbankingbrasil.org.br/.well-known/openid-configuration",
        "authorisationServerId": "7844e311-aa1f-4f67-9475-cbd989310b3e"
    },
    "directory": {
        "discoveryUrl": "https://auth.sandbox.directory.openbankingbrasil.org.br/.well-known/openid-configuration",
        "apibase": "https://matls-api.sandbox.directory.openbankingbrasil.org.br/",
        "keystore": "https://keystore.sandbox.directory.openbankingbrasil.org.br/",
        "client_id": "984e85a9-9001-40eb-97b3-194f5afbd956"
    },
    "resource": {
        "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
        "brazilPaymentConsent": {
            "data": {
                "loggedUser": {
                    "document": {
                        "identification": "76109277673",
                        "rel": "CPF"
                    }
                },
                "creditor": {
                    "personType": "PESSOA_NATURAL",
                    "cpfCnpj": "48847377765",
                    "name": "Marco Antonio de Brito"
                },
                "payment": {
                    "type": "PIX",
                    "date": "2021-01-01",
                    "currency": "BRL",
                    "amount": "1333.00",
                    "details": {
                        "localInstrument": "DICT",
                        "proxy": "12345678901",
                        "creditorAccount": {
                            "ispb": "12345678",
                            "issuer": "1774",
                            "number": "1234567890",
                            "accountType": "CACC"
                        }
                    }
                },
                "debtorAccount": {
                    "ispb": "12345678",
                    "issuer": "6272",
                    "number": "94088392",
                    "accountType": "CACC"
                }
            }
        },
        "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
        "brazilQrdnPaymentConsent": {
            "data": {
                "loggedUser": {
                    "document": {
                        "identification": "76109277673",
                        "rel": "CPF"
                    }
                },
                "creditor": {
                    "personType": "PESSOA_NATURAL",
                    "cpfCnpj": "48847377765",
                    "name": "Marco Antonio de Brito"
                },
                "payment": {
                    "type": "PIX",
                    "purpose": "IMMEDIATE",
                    "date": "2021-01-01",
                    "currency": "BRL",
                    "amount": "1333.00",
                    "ibgeTownCode": "5300108",
                    "details": {
                        "localInstrument": "QRDN",
                        "proxy": "cliente-a00001@pix.bcb.gov.br",
                        "qrCode": "00020101021226900014br.gov.bcb.pix0129cliente-a00001@pix.bcb.gov.br2535pix.bcb.gov.br/qr/v2/cobv/12345678952040000530398654071333.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***630451C3",
                        "payloadJWS": "header.payload.signature",
                        "creditorAccount": {
                            "ispb": "12345678",
                            "issuer": "1774",
                            "number": "1234567890",
                            "accountType": "CACC"
                        }
                    }
                },
                "debtorAccount": {
                    "ispb": "12345678",
                    "issuer": "6272",
                    "number": "94088392",
                    "accountType": "CACC"
                }
            }
        },
        "brazilQresPaymentConsent": {
            "data": {
                "loggedUser": {
                    "document": {
                        "identification": "76109277673",
                        "rel": "CPF"
                    }
                },
                "creditor": {
                    "personType": "PESSOA_NATURAL",
                    "cpfCnpj": "99991111140",
                    "name": "Joao Silva"
                },
                "payment": {
                    "type": "PIX",
                    "date": "2021-01-01",
                    "currency": "BRL",
                    "amount": "1333.00",
                    "details": {
                        "localInstrument": "QRES",
                        "proxy": "cliente-a00001@pix.bcb.gov.br",
                        "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5910Joao Silva6014BELO HORIZONTE62070503***63045243",
                        "creditorAccount": {
                            "ispb": "99999004",
                            "issuer": "0001",
                            "number": "12345678",
                            "accountType": "CACC"
                        }
                    }
                },
                "debtorAccount": {
                    "ispb": "12345678",
                    "issuer": "6272",
                    "number": "94088392",
                    "accountType": "CACC"
                }
            }
        },
        "brazilApdnPaymentConsent": {
            "data": {
                "loggedUser": {
                    "document": {
                        "identification": "76109277673",
                        "rel": "CPF"
                    }
                },
                "creditor": {
                    "personType": "PESSOA_NATURAL",
                    "cpfCnpj": "48847377765",
                    "name": "Marco Antonio de Brito"
                },
                "payment": {
                    "type": "PIX",
                    "purpose": "IMMEDIATE",
                    "date": "2026-04-02",
                    "currency": "BRL",
                    "amount": "100.00",
                    "ibgeTownCode": "3106200",
                    "details": {
                        "localInstrument": "APDN",
                        "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                        "proxy": "cliente-a00001@pix.bcb.gov.br",
                        "payloadJWS": "header.payload.signature",
                        "creditorAccount": {
                            "ispb": "12345678",
                            "issuer": "1774",
                            "number": "1234567890",
                            "accountType": "CACC"
                        }
                    }
                }
            }
        },
        "brazilQrdnCnpj": "43142666000197",
        "brazilApdnCnpj": "43142666000197",
        "loggedUserIdentification": "76109277673",
        "debtorAccountIspb": "12345678",
        "debtorAccountIssuer": "1774",
        "debtorAccountNumber": "94088392",
        "debtorAccountType": "CACC",
        "paymentAmount": "1333.00",
        "transactionIdentifier": "E00038166201907261559y6j6A"
    },
    "conditionalResources": {
        "brazilCpfTemporization": "76109277673"
    },
    "consent": {},
    "browser": [
        {
            "match": "https://auth.mockbank.openbankingbrasil.org.br/auth*",
            "tasks": [
                {
                    "task": "Login",
                    "optional": true,
                    "match": "https://auth.mockbank.openbankingbrasil.org.br/interaction*",
                    "commands": [
                        [
                            "text",
                            "name",
                            "login",
                            "ralph.bragg@gmail.com",
                            "optional"
                        ],
                        [
                            "text",
                            "name",
                            "password",
                            "P@ssword01",
                            "optional"
                        ],
                        [
                            "click",
                            "xpath",
                            "//button[contains(text(),\"Sign in\")]",
                            "optional"
                        ]
                    ]
                },
                {
                    "task": "Consent",
                    "optional": true,
                    "match": "https://auth.mockbank.openbankingbrasil.org.br/interaction*",
                    "commands": [
                        [
                            "wait",
                            "xpath",
                            "//*",
                            60,
                            ".*Before proceeding, we need to confirm some information:*",
                            "update-image-placeholder-optional"
                        ],
                        [
                            "click",
                            "xpath",
                            "//input[@id='consent-toggle']/following-sibling::div[1]"
                        ],
                        [
                            "click",
                            "id",
                            "continue-button"
                        ]
                    ]
                },
                {
                    "task": "Verify Complete",
                    "match": "*/test/*/callback*",
                    "commands": [
                        [
                            "wait",
                            "id",
                            "submission_complete",
                            10
                        ]
                    ]
                }
            ]
        }
    ],
    "override": {
        "payments_api_consents_rejection-reason_test-module_v5": {
            "resource": {
                "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "purpose": "IMMEDIATE",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "ibgeTownCode": "5300108",
                            "details": {
                                "localInstrument": "QRDN",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br5204000053039865406100.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                                "payloadJWS": "header.payload.signature",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilQrdnCnpj": "43142666000197",
                "brazilQresPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "99991111140",
                            "name": "Joao Silva"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "1333.00",
                            "details": {
                                "localInstrument": "QRES",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5910Joao Silva6014BELO HORIZONTE62070503***63045243",
                                "creditorAccount": {
                                    "ispb": "99999004",
                                    "issuer": "0001",
                                    "number": "12345678",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "loggedUserIdentification": "76109277673",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "100.00",
                "transactionIdentifier": "E00038166201907261559y6j6"
            },
            "browser": [
                {
                    "match": "https://auth.mockbank.openbankingbrasil.org.br/auth*",
                    "tasks": [
                        {
                            "task": "Login",
                            "optional": true,
                            "match": "https://auth.mockbank.openbankingbrasil.org.br/interaction*",
                            "commands": [
                                [
                                    "text",
                                    "name",
                                    "login",
                                    "ralph.bragg@gmail.com",
                                    "optional"
                                ],
                                [
                                    "text",
                                    "name",
                                    "password",
                                    "P@ssword01",
                                    "optional"
                                ],
                                [
                                    "click",
                                    "xpath",
                                    "//button[contains(text(),\"Sign in\")]",
                                    "optional"
                                ]
                            ]
                        },
                        {
                            "task": "Reject Consent",
                            "optional": true,
                            "match": "https://auth.mockbank.openbankingbrasil.org.br/interaction*",
                            "commands": [
                                [
                                    "wait",
                                    "xpath",
                                    "//*",
                                    60,
                                    ".*Before proceeding, we need to confirm some information:*",
                                    "update-image-placeholder-optional"
                                ],
                                [
                                    "click",
                                    "id",
                                    "cancel-button"
                                ]
                            ]
                        },
                        {
                            "task": "Verify Complete",
                            "match": "*/test/*/callback*",
                            "commands": [
                                [
                                    "wait",
                                    "id",
                                    "submission_complete",
                                    10
                                ]
                            ]
                        }
                    ]
                }
            ]
        },
        "payments_api_invalid-token_test-module_v5": {
            "resource": {
                "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "1.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "purpose": "IMMEDIATE",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "1.00",
                            "ibgeTownCode": "5300108",
                            "details": {
                                "localInstrument": "QRDN",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654041.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                                "payloadJWS": "header.payload.signature",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilQrdnCnpj": "43142666000197",
                "brazilQresPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "99991111140",
                            "name": "Joao Silva"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "1333.00",
                            "details": {
                                "localInstrument": "QRES",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5910Joao Silva6014BELO HORIZONTE62070503***63045243",
                                "creditorAccount": {
                                    "ispb": "99999004",
                                    "issuer": "0001",
                                    "number": "12345678",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "loggedUserIdentification": "76109277673",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "1.00",
                "transactionIdentifier": "E00038166201907261559y6j6"
            }
        },
        "payments_api_pixscheduling-patch-detentora_test-module_v5": {
            "resource": {
                "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "1400.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "purpose": "IMMEDIATE",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "1400.00",
                            "ibgeTownCode": "5300108",
                            "details": {
                                "localInstrument": "QRDN",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071400.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                                "payloadJWS": "header.payload.signature",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilQrdnCnpj": "43142666000197",
                "brazilQresPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "99991111140",
                            "name": "Joao Silva"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "1333.00",
                            "details": {
                                "localInstrument": "QRES",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5910Joao Silva6014BELO HORIZONTE62070503***63045243",
                                "creditorAccount": {
                                    "ispb": "99999004",
                                    "issuer": "0001",
                                    "number": "12345678",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "loggedUserIdentification": "76109277673",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "1400.00",
                "transactionIdentifier": "E00038166201907261559y6j6"
            }
        },
        "payments_api_pixscheduling-patch-iniciadora_test-module_v5": {
            "resource": {
                "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "purpose": "IMMEDIATE",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "ibgeTownCode": "5300108",
                            "details": {
                                "localInstrument": "QRDN",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br5204000053039865406100.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                                "payloadJWS": "header.payload.signature",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilQrdnCnpj": "43142666000197",
                "brazilQresPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "99991111140",
                            "name": "Joao Silva"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "1333.00",
                            "details": {
                                "localInstrument": "QRES",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5910Joao Silva6014BELO HORIZONTE62070503***63045243",
                                "creditorAccount": {
                                    "ispb": "99999004",
                                    "issuer": "0001",
                                    "number": "12345678",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "loggedUserIdentification": "76109277673",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "100.00",
                "transactionIdentifier": "E00038166201907261559y6j6"
            }
        },
        "payments_api_pixscheduling-patch-unhappy_test-module_v5": {
            "resource": {
                "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "1.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "purpose": "IMMEDIATE",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "1.00",
                            "ibgeTownCode": "5300108",
                            "details": {
                                "localInstrument": "QRDN",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654041.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                                "payloadJWS": "header.payload.signature",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilQrdnCnpj": "43142666000197",
                "brazilQresPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "99991111140",
                            "name": "Joao Silva"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "1333.00",
                            "details": {
                                "localInstrument": "QRES",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5910Joao Silva6014BELO HORIZONTE62070503***63045243",
                                "creditorAccount": {
                                    "ispb": "99999004",
                                    "issuer": "0001",
                                    "number": "12345678",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "loggedUserIdentification": "76109277673",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "1.00",
                "transactionIdentifier": "E00038166201907261559y6j6"
            }
        },
        "payments_api_pixscheduling-schd-accepted_test-module_v5": {
            "resource": {
                "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "purpose": "IMMEDIATE",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "ibgeTownCode": "5300108",
                            "details": {
                                "localInstrument": "QRDN",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br5204000053039865406100.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                                "payloadJWS": "header.payload.signature",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilQrdnCnpj": "43142666000197",
                "brazilQresPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "99991111140",
                            "name": "Joao Silva"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "1333.00",
                            "details": {
                                "localInstrument": "QRES",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5910Joao Silva6014BELO HORIZONTE62070503***63045243",
                                "creditorAccount": {
                                    "ispb": "99999004",
                                    "issuer": "0001",
                                    "number": "12345678",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "loggedUserIdentification": "76109277673",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "100.00",
                "transactionIdentifier": "E00038166201907261559y6j6"
            }
        },
        "payments_api_x-fapi_test-module_v5": {
            "resource": {
                "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "1400.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "purpose": "IMMEDIATE",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "1400.00",
                            "ibgeTownCode": "5300108",
                            "details": {
                                "localInstrument": "QRDN",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071400.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                                "payloadJWS": "header.payload.signature",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilQrdnCnpj": "43142666000197",
                "brazilQresPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "99991111140",
                            "name": "Joao Silva"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "1333.00",
                            "details": {
                                "localInstrument": "QRES",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5910Joao Silva6014BELO HORIZONTE62070503***63045243",
                                "creditorAccount": {
                                    "ispb": "99999004",
                                    "issuer": "0001",
                                    "number": "12345678",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "loggedUserIdentification": "76109277673",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "1400.00",
                "transactionIdentifier": "E00038166201907261559y6j6"
            }
        },
        "payments_api_real-email-invalid-creditor-proxy_test-module_v5": {
            "resource": {
                "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "20201.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "purpose": "IMMEDIATE",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "20201.00",
                            "ibgeTownCode": "5300108",
                            "details": {
                                "localInstrument": "QRDN",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br520400005303986540820201.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                                "payloadJWS": "header.payload.signature",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilQrdnCnpj": "43142666000197",
                "brazilQresPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "99991111140",
                            "name": "Joao Silva"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "1333.00",
                            "details": {
                                "localInstrument": "QRES",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5910Joao Silva6014BELO HORIZONTE62070503***63045243",
                                "creditorAccount": {
                                    "ispb": "99999004",
                                    "issuer": "0001",
                                    "number": "12345678",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "loggedUserIdentification": "76109277673",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "20201.00",
                "transactionIdentifier": "E00038166201907261559y6j6"
            }
        },
        "payments_api_fake-email-proxy_test-module_v5": {
            "resource": {
                "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "20201.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "purpose": "IMMEDIATE",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "20201.00",
                            "ibgeTownCode": "5300108",
                            "details": {
                                "localInstrument": "QRDN",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br520400005303986540820201.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                                "payloadJWS": "header.payload.signature",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilQrdnCnpj": "43142666000197",
                "brazilQresPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "99991111140",
                            "name": "Joao Silva"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "1333.00",
                            "details": {
                                "localInstrument": "QRES",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5910Joao Silva6014BELO HORIZONTE62070503***63045243",
                                "creditorAccount": {
                                    "ispb": "99999004",
                                    "issuer": "0001",
                                    "number": "12345678",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "loggedUserIdentification": "76109277673",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "20201.00",
                "transactionIdentifier": "E00038166201907261559y6j6"
            }
        },
        "payments_api_consumed-consent_test-module_v5": {
            "resource": {
                "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "1336.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "purpose": "IMMEDIATE",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "1336.00",
                            "ibgeTownCode": "5300108",
                            "details": {
                                "localInstrument": "QRDN",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071336.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                                "payloadJWS": "header.payload.signature",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilQrdnCnpj": "43142666000197",
                "brazilQresPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "99991111140",
                            "name": "Joao Silva"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "1333.00",
                            "details": {
                                "localInstrument": "QRES",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5910Joao Silva6014BELO HORIZONTE62070503***63045243",
                                "creditorAccount": {
                                    "ispb": "99999004",
                                    "issuer": "0001",
                                    "number": "12345678",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "loggedUserIdentification": "76109277673",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "1336.00",
                "transactionIdentifier": "E00038166201907261559y6j6"
            }
        },
        "payments_api_recurring-payments-custom-core_test-module_v5": {
            "resource": {
                "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "purpose": "IMMEDIATE",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "ibgeTownCode": "5300108",
                            "details": {
                                "localInstrument": "QRDN",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br5204000053039865406100.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                                "payloadJWS": "header.payload.signature",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilQrdnCnpj": "43142666000197",
                "brazilQresPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "99991111140",
                            "name": "Joao Silva"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "1333.00",
                            "details": {
                                "localInstrument": "QRES",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5910Joao Silva6014BELO HORIZONTE62070503***63045243",
                                "creditorAccount": {
                                    "ispb": "99999004",
                                    "issuer": "0001",
                                    "number": "12345678",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "loggedUserIdentification": "76109277673",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "100.00",
                "transactionIdentifier": "E00038166201907261559y6j6"
            }
        },
        "payments_api_recurring-payments-daily-core_test-module_v5": {
            "resource": {
                "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "purpose": "IMMEDIATE",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "ibgeTownCode": "5300108",
                            "details": {
                                "localInstrument": "QRDN",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br5204000053039865406100.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                                "payloadJWS": "header.payload.signature",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilQrdnCnpj": "43142666000197",
                "brazilQresPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "99991111140",
                            "name": "Joao Silva"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "1333.00",
                            "details": {
                                "localInstrument": "QRES",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5910Joao Silva6014BELO HORIZONTE62070503***63045243",
                                "creditorAccount": {
                                    "ispb": "99999004",
                                    "issuer": "0001",
                                    "number": "12345678",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "loggedUserIdentification": "76109277673",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "100.00",
                "transactionIdentifier": "E00038166201907261559y6j6"
            }
        },
        "payments_api_recurring-payments-large-batch_test-module_v5": {
            "resource": {
                "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "purpose": "IMMEDIATE",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "ibgeTownCode": "5300108",
                            "details": {
                                "localInstrument": "QRDN",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br5204000053039865406100.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                                "payloadJWS": "header.payload.signature",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilQrdnCnpj": "43142666000197",
                "brazilQresPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "99991111140",
                            "name": "Joao Silva"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "1333.00",
                            "details": {
                                "localInstrument": "QRES",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5910Joao Silva6014BELO HORIZONTE62070503***63045243",
                                "creditorAccount": {
                                    "ispb": "99999004",
                                    "issuer": "0001",
                                    "number": "12345678",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "loggedUserIdentification": "76109277673",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "100.00",
                "transactionIdentifier": "E00038166201907261559y6j6"
            }
        },
        "payments_api_recurring-payments-monthly-core_test-module_v5": {
            "resource": {
                "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "purpose": "IMMEDIATE",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "ibgeTownCode": "5300108",
                            "details": {
                                "localInstrument": "QRDN",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br5204000053039865406100.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                                "payloadJWS": "header.payload.signature",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilQrdnCnpj": "43142666000197",
                "brazilQresPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "99991111140",
                            "name": "Joao Silva"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "1333.00",
                            "details": {
                                "localInstrument": "QRES",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5910Joao Silva6014BELO HORIZONTE62070503***63045243",
                                "creditorAccount": {
                                    "ispb": "99999004",
                                    "issuer": "0001",
                                    "number": "12345678",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "loggedUserIdentification": "76109277673",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "100.00",
                "transactionIdentifier": "E00038166201907261559y6j6"
            }
        },
        "payments_api_recurring_payments_weekly_test-module_v5": {
            "resource": {
                "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "purpose": "IMMEDIATE",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "ibgeTownCode": "5300108",
                            "details": {
                                "localInstrument": "QRDN",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br5204000053039865406100.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                                "payloadJWS": "header.payload.signature",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilQrdnCnpj": "43142666000197",
                "brazilQresPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "99991111140",
                            "name": "Joao Silva"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "1333.00",
                            "details": {
                                "localInstrument": "QRES",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5910Joao Silva6014BELO HORIZONTE62070503***63045243",
                                "creditorAccount": {
                                    "ispb": "99999004",
                                    "issuer": "0001",
                                    "number": "12345678",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "loggedUserIdentification": "76109277673",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "100.00",
                "transactionIdentifier": "E00038166201907261559y6j6"
            }
        },
        "payments_api_recurring-payments-patch_test-module_v5": {
            "resource": {
                "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "purpose": "IMMEDIATE",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "ibgeTownCode": "5300108",
                            "details": {
                                "localInstrument": "QRDN",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br5204000053039865406100.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                                "payloadJWS": "header.payload.signature",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilQrdnCnpj": "43142666000197",
                "brazilQresPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "99991111140",
                            "name": "Joao Silva"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "1333.00",
                            "details": {
                                "localInstrument": "QRES",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5910Joao Silva6014BELO HORIZONTE62070503***63045243",
                                "creditorAccount": {
                                    "ispb": "99999004",
                                    "issuer": "0001",
                                    "number": "12345678",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "loggedUserIdentification": "76109277673",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "100.00",
                "transactionIdentifier": "E00038166201907261559y6j6"
            }
        },
        "payments_api_jti-reuse_test-module_v5": {
            "resource": {
                "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "purpose": "IMMEDIATE",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "ibgeTownCode": "5300108",
                            "details": {
                                "localInstrument": "QRDN",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br5204000053039865406100.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                                "payloadJWS": "header.payload.signature",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilQrdnCnpj": "43142666000197",
                "brazilQresPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "99991111140",
                            "name": "Joao Silva"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "1333.00",
                            "details": {
                                "localInstrument": "QRES",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5910Joao Silva6014BELO HORIZONTE62070503***63045243",
                                "creditorAccount": {
                                    "ispb": "99999004",
                                    "issuer": "0001",
                                    "number": "12345678",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "loggedUserIdentification": "76109277673",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "100.00",
                "transactionIdentifier": "E00038166201907261559y6j6"
            }
        },
        "payments_api_idempotency_test-module_v5": {
            "resource": {
                "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "purpose": "IMMEDIATE",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "ibgeTownCode": "5300108",
                            "details": {
                                "localInstrument": "QRDN",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br5204000053039865406100.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                                "payloadJWS": "header.payload.signature",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilQrdnCnpj": "43142666000197",
                "brazilQresPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "99991111140",
                            "name": "Joao Silva"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "1333.00",
                            "details": {
                                "localInstrument": "QRES",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5910Joao Silva6014BELO HORIZONTE62070503***63045243",
                                "creditorAccount": {
                                    "ispb": "99999004",
                                    "issuer": "0001",
                                    "number": "12345678",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "loggedUserIdentification": "76109277673",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "100.00",
                "transactionIdentifier": "E00038166201907261559y6j6"
            }
        },
        "payments_api_consent-bulk-cancel_negative_timezone_test-module_v5": {
            "resource": {
                "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "purpose": "IMMEDIATE",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "ibgeTownCode": "5300108",
                            "details": {
                                "localInstrument": "QRDN",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br5204000053039865406100.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                                "payloadJWS": "header.payload.signature",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilQrdnCnpj": "43142666000197",
                "brazilQresPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "99991111140",
                            "name": "Joao Silva"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "1333.00",
                            "details": {
                                "localInstrument": "QRES",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5910Joao Silva6014BELO HORIZONTE62070503***63045243",
                                "creditorAccount": {
                                    "ispb": "99999004",
                                    "issuer": "0001",
                                    "number": "12345678",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "loggedUserIdentification": "76109277673",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "100.00",
                "transactionIdentifier": "E00038166201907261559y6j6"
            }
        },
        "payments_api_unmatching-loggedUser_test-module_v5": {
            "resource": {
                "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "1333.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "purpose": "IMMEDIATE",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "1333.00",
                            "ibgeTownCode": "5300108",
                            "details": {
                                "localInstrument": "QRDN",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                                "payloadJWS": "header.payload.signature",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilQrdnCnpj": "43142666000197",
                "brazilQresPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "99991111140",
                            "name": "Joao Silva"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "1333.00",
                            "details": {
                                "localInstrument": "QRES",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5910Joao Silva6014BELO HORIZONTE62070503***63045243",
                                "creditorAccount": {
                                    "ispb": "99999004",
                                    "issuer": "0001",
                                    "number": "12345678",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "loggedUserIdentification": "87517400444",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "1333.00",
                "transactionIdentifier": "E00038166201907261559y6j6"
            }
        },
        "payments_api_pix-change-qrdn_test-module_v5": {
            "resource": {
                "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "1333.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "currency": "BRL",
                            "amount": "1333.00",
                            "ibgeTownCode": "3106200",
                            "details": {
                                "localInstrument": "QRDN",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                                "payloadJWS": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ2YWxvciI6eyJvcmlnaW5hbCI6IjEwMDAuMDAiLCJyZXRpcmFkYSI6eyJ0cm9jbyI6eyJ2YWxvciI6IjMzMy4wMCIsIm1vZGFsaWRhZGVBZ2VudGUiOiJBR1RFQyIsInByZXN0YWRvckRvU2Vydmljb0RlU2FxdWUiOiIxMjM0NTY3OCJ9fX19.Ulfjtw599R6Adencrp6rmoxPjIn5R3JwwT8vHKBaMDM",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilQrdnCnpj": "43142666000197",
                "brazilQresPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "99991111140",
                            "name": "Joao Silva"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "1333.00",
                            "details": {
                                "localInstrument": "QRES",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5910Joao Silva6014BELO HORIZONTE62070503***63045243",
                                "creditorAccount": {
                                    "ispb": "99999004",
                                    "issuer": "0001",
                                    "number": "12345678",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "loggedUserIdentification": "76109277673",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "1333.00",
                "transactionIdentifier": "E00038166201907261559y6j6A"
            }
        },
        "payments_api_pix-withdraw-exceeds-limit_test-module_v5": {
            "resource": {
                "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "1500.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "purpose": "IMMEDIATE",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "1500.00",
                            "ibgeTownCode": "5300108",
                            "details": {
                                "localInstrument": "QRDN",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071500.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                                "payloadJWS": "header.payload.signature",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilQrdnCnpj": "43142666000197",
                "brazilQresPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "99991111140",
                            "name": "Joao Silva"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "1333.00",
                            "details": {
                                "localInstrument": "QRES",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5910Joao Silva6014BELO HORIZONTE62070503***63045243",
                                "creditorAccount": {
                                    "ispb": "99999004",
                                    "issuer": "0001",
                                    "number": "12345678",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "loggedUserIdentification": "76109277673",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "1500.00",
                "transactionIdentifier": "E00038166201907261559y6j6"
            },
            "browser": [
                {
                    "match": "https://auth.mockbank.openbankingbrasil.org.br/auth*",
                    "tasks": [
                        {
                            "task": "Login",
                            "optional": true,
                            "match": "https://auth.mockbank.openbankingbrasil.org.br/interaction*",
                            "commands": [
                                [
                                    "text",
                                    "name",
                                    "login",
                                    "ralph.bragg@gmail.com",
                                    "optional"
                                ],
                                [
                                    "text",
                                    "name",
                                    "password",
                                    "P@ssword01",
                                    "optional"
                                ],
                                [
                                    "click",
                                    "xpath",
                                    "//button[contains(text(),\"Sign in\")]",
                                    "optional"
                                ]
                            ]
                        },
                        {
                            "task": "Consent",
                            "optional": true,
                            "match": "https://auth.mockbank.openbankingbrasil.org.br/interaction*",
                            "commands": [
                                [
                                    "wait",
                                    "xpath",
                                    "//*",
                                    60,
                                    ".*Before proceeding, we need to confirm some information:*",
                                    "update-image-placeholder-optional"
                                ],
                                [
                                    "click",
                                    "xpath",
                                    "//input[@id='consent-toggle']/following-sibling::div[1]"
                                ],
                                [
                                    "click",
                                    "id",
                                    "continue-button"
                                ]
                            ]
                        },
                        {
                            "task": "Verify Complete",
                            "match": "*/test/*/callback*",
                            "commands": [
                                [
                                    "wait",
                                    "id",
                                    "submission_complete",
                                    10
                                ]
                            ]
                        }
                    ]
                },
                {
                    "match": "https://auth.mockbank.openbankingbrasil.org.br/auth*",
                    "tasks": [
                        {
                            "task": "Login",
                            "optional": true,
                            "match": "https://auth.mockbank.openbankingbrasil.org.br/interaction*",
                            "commands": [
                                [
                                    "text",
                                    "name",
                                    "login",
                                    "ralph.bragg@gmail.com",
                                    "optional"
                                ],
                                [
                                    "text",
                                    "name",
                                    "password",
                                    "P@ssword01",
                                    "optional"
                                ],
                                [
                                    "click",
                                    "xpath",
                                    "//button[contains(text(),\"Sign in\")]",
                                    "optional"
                                ]
                            ]
                        },
                        {
                            "task": "Reject Consent",
                            "optional": true,
                            "match": "https://auth.mockbank.openbankingbrasil.org.br/interaction*",
                            "commands": [
                                [
                                    "wait",
                                    "xpath",
                                    "//*",
                                    60,
                                    ".*Before proceeding, we need to confirm some information:*",
                                    "update-image-placeholder-optional"
                                ],
                                [
                                    "click",
                                    "id",
                                    "cancel-button"
                                ]
                            ]
                        },
                        {
                            "task": "Verify Complete",
                            "match": "*/test/*/callback*",
                            "commands": [
                                [
                                    "wait",
                                    "id",
                                    "submission_complete",
                                    10
                                ]
                            ]
                        }
                    ]
                }
            ]
        },
        "payments_api_apes-good-happy-path-with-txid_test-module_v5": {
            "resource": {
                "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "purpose": "IMMEDIATE",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "ibgeTownCode": "5300108",
                            "details": {
                                "localInstrument": "QRDN",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br5204000053039865406100.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                                "payloadJWS": "header.payload.signature",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilQrdnCnpj": "43142666000197",
                "brazilQresPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "99991111140",
                            "name": "Joao Silva"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "1333.00",
                            "details": {
                                "localInstrument": "QRES",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5910Joao Silva6014BELO HORIZONTE62070503***63045243",
                                "creditorAccount": {
                                    "ispb": "99999004",
                                    "issuer": "0001",
                                    "number": "12345678",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "loggedUserIdentification": "76109277673",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "100.00",
                "transactionIdentifier": "E00038166201907261559y6j6"
            }
        },
        "payments_api_apes-good-happy-path-without-txid_test-module_v5": {
            "resource": {
                "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "purpose": "IMMEDIATE",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "ibgeTownCode": "5300108",
                            "details": {
                                "localInstrument": "QRDN",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br5204000053039865406100.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                                "payloadJWS": "header.payload.signature",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilQrdnCnpj": "43142666000197",
                "brazilQresPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "99991111140",
                            "name": "Joao Silva"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "1333.00",
                            "details": {
                                "localInstrument": "QRES",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5910Joao Silva6014BELO HORIZONTE62070503***63045243",
                                "creditorAccount": {
                                    "ispb": "99999004",
                                    "issuer": "0001",
                                    "number": "12345678",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "loggedUserIdentification": "76109277673",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "100.00"
            }
        },
        "payments_api_apes-mismatched-consent-payment_test-module_v5": {
            "resource": {
                "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "purpose": "IMMEDIATE",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "ibgeTownCode": "5300108",
                            "details": {
                                "localInstrument": "QRDN",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br5204000053039865406100.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                                "payloadJWS": "header.payload.signature",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilQrdnCnpj": "43142666000197",
                "brazilQresPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "99991111140",
                            "name": "Joao Silva"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "1333.00",
                            "details": {
                                "localInstrument": "QRES",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5910Joao Silva6014BELO HORIZONTE62070503***63045243",
                                "creditorAccount": {
                                    "ispb": "99999004",
                                    "issuer": "0001",
                                    "number": "12345678",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "loggedUserIdentification": "76109277673",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "100.00",
                "transactionIdentifier": "E00038166201907261559y6j6"
            }
        },
        "payments_api_apes-code-unhappy-path-required_test-module_v5": {
            "resource": {
                "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/payments/v5/consents",
                "brazilPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2021-01-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "details": {
                                "localInstrument": "DICT",
                                "proxy": "12345678901",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
                "brazilQrdnPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "48847377765",
                            "name": "Marco Antonio de Brito"
                        },
                        "payment": {
                            "type": "PIX",
                            "purpose": "IMMEDIATE",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "100.00",
                            "ibgeTownCode": "5300108",
                            "details": {
                                "localInstrument": "QRDN",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br5204000053039865406100.005802BR5922Marco Antonio de Brito6014BELO HORIZONTE62070503***6304B62D",
                                "payloadJWS": "header.payload.signature",
                                "creditorAccount": {
                                    "ispb": "12345678",
                                    "issuer": "1774",
                                    "number": "1234567890",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "brazilQrdnCnpj": "43142666000197",
                "brazilQresPaymentConsent": {
                    "data": {
                        "loggedUser": {
                            "document": {
                                "identification": "76109277673",
                                "rel": "CPF"
                            }
                        },
                        "creditor": {
                            "personType": "PESSOA_NATURAL",
                            "cpfCnpj": "99991111140",
                            "name": "Joao Silva"
                        },
                        "payment": {
                            "type": "PIX",
                            "date": "2024-02-01",
                            "currency": "BRL",
                            "amount": "1333.00",
                            "details": {
                                "localInstrument": "QRES",
                                "proxy": "cliente-a00001@pix.bcb.gov.br",
                                "qrCode": "00020126510014BR.GOV.BCB.PIX0129cliente-a00001@pix.bcb.gov.br52040000530398654071333.005802BR5910Joao Silva6014BELO HORIZONTE62070503***63045243",
                                "creditorAccount": {
                                    "ispb": "99999004",
                                    "issuer": "0001",
                                    "number": "12345678",
                                    "accountType": "CACC"
                                }
                            }
                        },
                        "debtorAccount": {
                            "ispb": "12345678",
                            "issuer": "6272",
                            "number": "94088392",
                            "accountType": "CACC"
                        }
                    }
                },
                "loggedUserIdentification": "76109277673",
                "debtorAccountIspb": "12345678",
                "debtorAccountIssuer": "1774",
                "debtorAccountNumber": "94088392",
                "debtorAccountType": "CACC",
                "paymentAmount": "100.00",
                "transactionIdentifier": "E00038166201907261559y6j6"
            }
        }
    },
    "client": {
        "jwks": {
            "keys": [
                {
                    "alg": "PS256",
                    "d": "Q9gSOfnkGJnAsV3a94j9ae9ihjqgMwXgVm73VTyEs1u9Jq73pCWX0e9JdeNMKdgKpiJYjyxa3ttxCY58eiGKEi7c50zYRx8YLTL2rIVWqS6JVGpXuzIQutkQDM4AfD72bG3-xT-caSCansGbdEIFJjX32Ujbs1UUoQlE96m3hNOjB5vNyHBWrBUgUGG9_uJiWFG6Lbj8ZGtiihA_PQkzuArLzDvO2OMVHCzIyQ4CwFE1tI9xHFHpioJQXBnymURQvkm3MmEwHRG_KUdABQ55gG32jothy7jOOYAMkvOCejteTZv1nT4dsEj-CBxDBtTI6SerXb11VX8b0suzSBxx0Q",
                    "dp": "S15AOPpOtYgYjfOi2rNojY3NpU-Qobnfnnt_MZEJ2_DS0bGwXSgGJjHOOOAowy1HK0n7-AhXbwhr026sBuicR_Kpj6RkzGVrJug8y9R02FXZwlQpgjSBZdO6C2B1OOvtyKmnKg5q1KdQ7Kx6vYPV7UutOJn6NlH0RbFgG4NGelk",
                    "dq": "oBgBMB54mtrriQCg4YyDY_zf7LW4f6oqiUl3l7odf_ArjVamjHM-boZnhGoVzZ5uXNs03wEdBIc2HLmsoGLVuodcYHjyptmvyPebiH2mavFlUlI8ILG6lkyIhMp3Ri8iXGX2MYlPjP2EawNDMHB6BO0bZ5NugyzxuF_OKhfEFLc",
                    "e": "AQAB",
                    "kid": "-duNE0ZX5NmDkUlgNoqDY5Ve7UdFTA7S25WJSAv8tNQ",
                    "kty": "RSA",
                    "n": "-6Ep5kV0qcQnrxQzbEgMGKQRHnhXlp3ZpAVqQbbzkVG_a1tHLi0V7YAmjf3isXMvdvWjApeShL32gqxgcKDvC5Mnd5ufR1ujzb5lsnYXy-tKMQWnAlCqy7mSuxi8JIBXyZb7CMGU29L32Tvd5MjDh_hSgwnHcTggE-ehqzK5eyvK7DjvlbfCKXgDx94kMcwyI2K0EurahHj9_I3lEQzAt73OocF_z84FQxO87A8Q1cM3nEGyykZPaFyulQ4bf4U2tT_Jfd0ppYX1j194ouPeqMZBsGnxKf4L4QvuberbRpdeOO92HhWHHiwiTuhYxF876-LKgPzqxK-Y1a2_4gsVAw",
                    "p": "_oebNFofSe_8fdotMxUEk7n3pq5eT96rO_VPdHyTZERDrkU0djQf9BLy7DejYoRReuI0AJWkBL9EGBhECaowmx8gTCs43ffQrBDULYB4elmS07ov1pq1STqzqRKbu_INaSGVgxFzhYC_EeFVpB0RPlAUvb1_aQkH79J8VMnp2_U",
                    "q": "_RVEyO9NB6XiJjMz9t6XrNxG01Vguo2VVBLaDJhoi1g7gydUDkNc9twhF1Ifps8Gf3m9aMjjOmYqE5kuWCPBHxkk8cZOm4C2AhVbQxMkZLOyPeJDfKfCi7yJRIfmwqQM5AKosALfN-jW_p746lRhCAps8eH9XF6bjugi_MH1yhc",
                    "qi": "yXG_vCx0xL9DlU7f0Ixub9NSD1QJtAJYxwKyHukw_8f4rHLiZ8eeCerfZfPd7zsPGSqOmY2605MNT1Z2ohYgoRyu05uwstEDKqtgl_uxupfO6AJKCja4paIB-ICvQQXpOY1n9BW6VcDwSylTnv1pKvVnTvxzy5z008wvrafQtFw",
                    "use": "sig"
                },
                {
                    "kty": "RSA",
                    "alg": "PS256",
                    "use": "enc",
                    "kid": "e96744c58188c084310920b152ffb02a392b119a009fb1fa1a656006715e1604",
                    "n": "4eIXvOR1XXo3MT9syMwRZj2ChbV2Qlp_623VCIhYvPtJ5k5rlCr1hP4n0PC49U47pa3UKNs6DYHefHKm9I4h4crgk7zsln2_JP3kK1equqIO1U12Rv4Xbm_2_eqR3hPKcE3il2ky2Neby8OThFnyDwBNKdxI4MvOKm910qQhYns2L4w_i9fjF2z1Wpi6sMPW8IERhkqaBWgoaH9g2obGbNuoYCzEjOWvRb_nVjYKRPqTI2A11kWZ4mVTRkTO4yM1gdI7z8Hsl4fqlEXeVdmMkVJhRvQa-vFfegecgO8nUY2XoOUx_UR51F8PO9bepy-jH16cRDwjLE-2ex7mE_wfMw",
                    "e": "AQAB",
                    "d": "BqovoVF4vww8nA9IuLhnHDlDZFbHov4qZeCecQgcEJNpIxdiqDZuR4EvECsSIgOWOFvwW-lzOI1oHaVNlMvezXU5eoWpnpuEnzHlYHwCzxftNrde5PBZWHC-sAMStvBzJpLw7riNZgWFx_wNmoTQfHqgGQfLyxcB9Pf6v387qiN1wHfSXQshtFiDg_6tBaH6dS1jRAg7_56dQp1wWJeRaqMCg9QeESmo3c-76hnRSMU6fgrONU6qGMSLopv-nirh3H1gZePcXzVgf9cerRMQgV1pWUZEd_iJqTaX8U7wB0txmVF6QzRxR71Ah6nZuV_Rv7X88zB8u0rXOvjeGtuZKQ",
                    "p": "8fN0GXyZnvxba4yoOgdL9ta9pkjjWVu5eTOIyvSgKf09hUSWKL6sKm1N0l68detwzBFpnxObOeUCMnU_BFhJM-s0w5GognaAX6GB5-TzdYHwmsgqAch3-_hi_kZU6A-SLZu7bQFGXTEotQ1zMxVuCMZ7AjTs0CGZrS-vItFYtik",
                    "q": "7v_Ldwh3L9On2CNAefLgs7dyDBAgWrkXOJ9Z1EnrKgMHbqgq5dOixv2ezKNdOUte9G4ve555XTf2sC-p0TF9PNYC0_4KthI8NLik8RtDsQmYJUYw7qfV_YitzGflM2DRr6KaV5SmO_aPWRfzuVWh_6kIQ_GmXf47ASasKVeD_fs",
                    "dp": "Jyi-_q0C9A9mAHcodxPdQJsq4LHlUf4de7dSiX6kOYeKIHqkTv3lQYylTsoUeIVdoTmkPaHfurQM8fu18k8Tsfp8dLarbkodptyt-Mk-eiNIvNRusBExEi_2Xa8maNS0VPtij1boe4bMTtlZbsgmIfd1yzqjpV_6zmPsVZdKY1k",
                    "dq": "qjW-YA3FZGhmtwWUG8Wfxh41uOWbRUFgilDils_2DTuPBX363yc0XGevuqn18KH_BDGc23tnj74VkDDBzlxihvsblILuefDOs_V0csoqEWF128X7f1xEiIXY0SSFFWw0qdMx_IG_SiE0wgzO5QVZlEx7uHfXNkWjHBTAs8jCFhU",
                    "qi": "8W2vDdiA8qDxL2fiJPP2m3NqbjGW7Tf5PsfGo0Gqfv6nWVweuVwsyUNT1AYduZUCvFRG5LRNHqiwZNpNB6XQln1W41GaIqGkHWJkveHhg9xIQmSK2hrX4OnSdyvMiGiB2yvce0FTgQ0OzXuNkIKJKJLP2nAJusNgNcVT7qgKCRA"
                }
            ]
        },
        "org_jwks": {
            "keys": [
                {
                    "d": "BpgLagicLjysglxtDX7bJnOv4-IP-5yyGdL4oOkDCl_-lO8twPDhWLfXNCf2QTs7l1T1GLNUyALKjYDNEvjbpu03_K1dtRwO2ZS4_VHTPhe99Etn1GXntdfcFvQiD9Lz6uzs2-0DOIG_5xWUiVhTUN5HPRfMMXF3ktG2ucTOQqsJU0O2SOohVIvqYH4EDJNIw8qUsu1C2JEDMj79H_8KaXEUVx8tFFLMxmt67a_a7sImXvEaIYhUCu-DMMDrzBc660s_eTcihJ_DkJgYPPWctnmpUClKa4zgABDqGXhPQFfLS4ywGAHnLZF1MyNeKFXpmeJShjNJ5MqjBKJTnFHDQKs",
                    "dp": "CFfrENWCU61YHATfdTy73lt2reMz0dBDicy92s4FqHpcup6O6f5MWGvhpBlLVC-tNA97qzyKExFwxl6c6rf45l8T6GLjy4C2DJEH0pGKeh7-PP7XW1KBvsclbJdSoSj-bOFRomFVGKYhIF3nRnr9-Dvj1k8aEcClPT1E9i9rGI7P",
                    "dq": "BzCeCJQ9pKQVCpyFi50PR8_E7d9uW9nYqJpf0GBT5XdnZ44qnliLAffZmVwcxXh6e_JzIjC0ByJrYKd_dekXLCrsOex1XxqvI7WH6EZ3Nvoe_1835ZgtQ2PsPSvGKifHHPXocKyqqRdT7KlGTXfnpKtezsXPxe63VS-3coE62-_F",
                    "e": "AQAB",
                    "kid": "EKSYJfNcI8Bm22_dP0ziWpTjw9UceAdVjykgwO5BkfE",
                    "kty": "RSA",
                    "n": "oBp-b0EhezRYfisJBL_WA2Yh0Y2zPYHsy8N4G9mddkop-kFJT12XSSBx8GXmyjDL14Wg5vRNA6R_TwXbJbnHnE59uMYiWNi_G7OL6jMsncmYdyBuwl-lDWExaXC5Qg9vYgGnt7d1SthQoiJkduPIiNpniq5p7px-jJYQO4SECUqpeLl9rU_Xvxn5zpFu4dw65wBi4oSDiJ0zujQtxofOmbJCKYTWrPmd8yPlPgwIttP2ZcprMs5Ya57-99NhAealcVptRTOQTEWEOflmurq58Byu7pT64ns-9Su8JPcHMMzxOOVM7KNPuZA7Xa5-1aBd1XrhxkBHIDzUqOpanSlr2uk",
                    "p": "DgL5bOQ5-JXM6Ed_3BRKW2a3EcHB_UjlWPlGGkc0RBeEwlNi6D3PQGZmgTxyGXWA4W3HMi2S2pXx8oxWd9rrw9Uc_BNrIdvkMcU9LnkCvxK-dcHalVrXhv0l1EbQx0mG9LjLsiqmJiJYnUYTuLjO8lJaebSTp-EH2fgTs81_SBKv",
                    "q": "C20t29WtF9yAXt2r5Yu7chtrJUMIsu_TUY2N6p75BWWBB76oNib4Dp5fVePnbTqdSP913dS1K1vHwEAqS_Z_C6vfmaYha6Hguipo5jotTTJoYDxV_xTp1dGWcr8MltBE9ikhLa8xvGVxXjSi4vkqc_TyXlBSHbbBSZtjB32rCLHn",
                    "qi": "BRx-2fqZYWrIzcayN1v10HfzcQaZue-NNZP7Eid81oBBxBrDQmiGdzQLi0BKctjLBr21_GWUgHgEYRym3He5biuDVM0WnyhXYeLLc_pv3bIG6FoPrP4XDZo4GTM4JdVj2im_OQWdXuokFzsZzeVV6H8p46TxpyNDix5oFjmyuB11",
                    "alg": "PS256",
                    "use": "sig"
                },
                {
                    "p": "2a8fRJ7ybF-qtF1zrYzSm7z3C4wNTUMbVYqe44tR9FbKsobqW2tS0iAZf-GJ_SZPcWxkE76gunW7YqMJecGUtXsJ8TTHwjcPQOMYzxnyJu8Q4JOj01YJVrxUY9D0ZzpWM9oTAj1-qoE0w7Dy-XNUc14-HeRlmOkg2tTfrXTVR8c",
                    "kty": "RSA",
                    "q": "0xlPJFRUcBU5j2SKSajVnd4H5p88RSsd4cArMby1ZRuSeHEsX76c6QKAPq7uTfKrTeZic34yzAEUyHloP1fZQYQ2UQn-f6PsTAWdT1Lp5oi2VZCT0yc9-1EGnLAiUCbM9SQQyf2GIVhCiAk_0VuY6le61Pw0U4GssvFJzIrx4as",
                    "d": "GxnizpWcqL1wajD8-Y-8H9-II4UZMKfkgbfwRiLK9uAd8-kEJdO9jdNeMxyytg2saDhxNTeRTkYz_VbBf3p9dGhuYx84d-ZagUbIiU3ho3FCsBRrzQQZw9OQrzPDUzp0-SBn1_GLCf9fo4ysxWHbn9euJVi2fpN_bHlBi1n8fKhdBHYE7X3XJnRYrUXItxZw5sJsqM_boONLxdLAvgmZx5CHft94JZsR6JPwlj9Ba_CuNWX_3OuUGyV0f5_1ICAEYijw9PA8KAW6t5UUYn39_KYL8nF5L1Bh6W1j8eN84I2lcKZNO6Pou064ag_wqGhk4uXuQO1IV8jRFn3-pqhSEQ",
                    "e": "AQAB",
                    "use": "enc",
                    "kid": "c1d7b80ce4b88c4f2cfb68e7a8c45bfff355ae94259bc1a73a95ddbaeaf7c96b",
                    "qi": "pU1IXwiQoFERdzJsx7kSC79Gwhak7uw7OAJCbcfkKE3GSwTWHrKfg5uDZlNvSnNU1Hbpxd0bgc40dFI2aNBML1gyDwTjQplWVJikkFix8E6z_ErSa_D5w5yV4k6CNtt7OzlMXawiZ-ndcuiOs5MkfSRyeB3k5rQmuZjLVzFFlnw",
                    "dp": "Gn4dqBRQHLBn7huRgIWq_Bk7V8RrugN4yChevgKurrYBZUjWLNoa8kfF0rJ4QL7w3DT82QpSNV8utwpwlMjieFPJGfn6dcCNsq_wzQOzXNmrjClrvsSxzkSNYLiFhiqrYxQfTB5_0_B1o3tdls5acM__b1PkqX916CwQLOQTMPE",
                    "alg": "PS256",
                    "dq": "NS0x94fawWVHW6zK_SUvspXkzZ6dMxtaaqza9KuB0ldwvTBdKj09D6FWpvOwCiiwKG55rHhE2YkIMDwNG6_Iha2FdUKcPpEPjFL5vqq3SyBzNfi2lEFVZsKRdNUVv7UWekY8iHV53Vp7YANcdSOq0JWK9e4WTFblJyqLGaCCsAM",
                    "n": "s4DcK4uxKroJPE1R7Te4ppNexbuK3C-Z3MpXFr5hmY43gYIoVMo89jE6OcDiO0Z4rxe8dsH4oYA2vAJQ0IhAaUxYMk2kN01ei761zMQWHLUPLcEKWgipYHy4AgwAUaF7-Glyb0DT1RRcY4f1tEddftxhwXZjeFduj6luVg6fVvXRIRjttybUkIKvf5ShMofVFCF_IyjYlOal4g3DVnCg62dR71WX3fRXSufxrRBG-L61rv2VSMg8pIb1DFiYKDlEXEnTdLk-7goBpTIz3wBsrZgJESSZOn_BG_-fCE0V75rheLMuJd4IGE4H0taVfEQOJKRKBVzc2jAz0sOaVuPY7Q"
                }
            ]
        },
        "client_id": "Jj-hosRwYqvtnQZNph2Ah"
    },
    "mtls": {
        "cert": "-----BEGIN CERTIFICATE-----\nMIIHQDCCBiigAwIBAgIUOyyDtirdgYQIT/eSBtvaP5JRcoswDQYJKoZIhvcNAQEL\nBQAweTELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MS0wKwYDVQQDEyRPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBJc3N1aW5nIENBIC0gRzIwHhcNMjUxMTA1MjAzMjAwWhcN\nMjYxMjA1MjAzMjAwWjCCAUoxCzAJBgNVBAYTAkJSMQswCQYDVQQIEwJVSzEPMA0G\nA1UEBxMGTE9ORE9OMSYwJAYDVQQKEx1PcGVuIEJhbmtpbmcgQnJhc2lsIC0gUmFp\nZGlhbTEtMCsGA1UECxMkYjk2MWM0ZWItNTA5ZC00ZWRmLWFmZWItMzU2NDJiMzgx\nODVkMUMwQQYDVQQDEzpodHRwczovL3dlYi5jb25mb3JtYW5jZS5kaXJlY3Rvcnku\nb3BlbmJhbmtpbmdicmFzaWwub3JnLmJyMRcwFQYDVQQFEw4wMDAwMDAxMDc0Mjg1\nMTEdMBsGA1UEDxMUUHJpdmF0ZSBPcmdhbml6YXRpb24xEzARBgsrBgEEAYI3PAIB\nAxMCVUsxNDAyBgoJkiaJk/IsZAEBEyQ5ODRlODVhOS05MDAxLTQwZWItOTdiMy0x\nOTRmNWFmYmQ5NTYwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQC8bzfe\nH4l2IegWdHsOIooz+nUxpfI5v23ubPsB0P9rLEoPlIn0A7E2zg/b7UCQFvzmzgao\n49DYEbaR5B5rutlRn52rkHufNF2fNEGXgtqrko/Uwf2tGDpve+e6MRuXhyYUEwaq\nMIRL9RCqDSTHFUS+QoNaPdccw9yAQkffEckKoXJA5GYkLvkZ06Vh8R7L6Agjh1VN\ntbT3v+STfrIbSYcEXJoHwWn7vnSewcJm3B1yxpKAVySFbL336yu0cYU8RkZ42SBh\nJmGD96kmJ+vuTXQBs5ZTndbZo6/UO+r3+qaQ8rK1r4qeEYaOwSYh9wsFxpLJIgyC\nwnl0XQQnwjQKKConAgMBAAGjggLrMIIC5zAMBgNVHRMBAf8EAjAAMB0GA1UdDgQW\nBBTLmBupVqnHkdd6f2hhj5mRrTUZnzAfBgNVHSMEGDAWgBR67wuI2HqJ4b0vBD0e\nsdbER0IoPTBZBggrBgEFBQcBAQRNMEswSQYIKwYBBQUHMAGGPWh0dHA6Ly9vY3Nw\nLnBraS1nMi5zYW5kYm94LmRpcmVjdG9yeS5vcGVuYmFua2luZ2JyYXNpbC5vcmcu\nYnIwWAYDVR0fBFEwTzBNoEugSYZHaHR0cDovL2NybC5wa2ktZzIuc2FuZGJveC5k\naXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL2lzc3Vlci5jcmwwRQYD\nVR0RBD4wPII6aHR0cHM6Ly93ZWIuY29uZm9ybWFuY2UuZGlyZWN0b3J5Lm9wZW5i\nYW5raW5nYnJhc2lsLm9yZy5icjAOBgNVHQ8BAf8EBAMCBaAwEwYDVR0lBAwwCgYI\nKwYBBQUHAwIwggF0BgNVHSAEggFrMIIBZzCCAWMGCysGAQQBg7ovcAECMIIBUjCB\n9QYIKwYBBQUHAgIwgegMgeVUaGlzIENlcnRpZmljYXRlIGlzIHNvbGVseSBmb3Ig\ndXNlIHdpdGggT3BlbiBGaW5hbmNlIEJyYXNpbCBzYW5kYm94IEFQSXMgU2Vydmlj\nZXMuIEl0cyByZWNlaXB0LCBwb3NzZXNzaW9uIG9yIHVzZSBjb25zdGl0dXRlcyBh\nY2NlcHRhbmNlIG9mIHRoZSBPcGVuIEZpbmFuY2UgQnJhc2lsIHNhbmRib3ggb2Yg\nQVBJcyBDZXJ0aWZpY2F0ZSBQb2xpY3kgYW5kIHJlbGF0ZWQgZG9jdW1lbnRzIHRo\nZXJlaW4uMFgGCCsGAQUFBwIBFkxodHRwOi8vcmVwb3NpdG9yeS5wa2ktZzIuc2Fu\nZGJveC5kaXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL3BvbGljaWVz\nMA0GCSqGSIb3DQEBCwUAA4IBAQAjJQE5R9iYGgnrEpEOUGNFVqHYs8L8Y1quoglO\nYsz1GhC2bzm7WSo7iRXfil5D8om6BDM+2TsMkvH21yeNnIclIrK/ReDHqkubbWoa\n9awJDNVa6VoNRdCB6dqEiLwZl4p+bacoShQCd113v5B76gVyCPBmId41rDJv/beB\nv7F894KM4LMMkkZGSnrGft9fc8Y2CPN452EgnTh41PhJHK8DVw8mtx704gblJ64B\nwqhogdzyAjY1uz+a3M1gTTCkEEkuhYXYrHDXgz327JRCW2oXKj7oMMszMI5E4uYL\n/QQijgFOoCPdX+/SvXZo7uMl0dtegLOR/oHxOwLuryqBk9mG\n-----END CERTIFICATE-----",
        "key": "-----BEGIN PRIVATE KEY-----\nMIIEvQIBADANBgkqhkiG9w0BAQEFAASCBKcwggSjAgEAAoIBAQC8bzfeH4l2IegW\ndHsOIooz+nUxpfI5v23ubPsB0P9rLEoPlIn0A7E2zg/b7UCQFvzmzgao49DYEbaR\n5B5rutlRn52rkHufNF2fNEGXgtqrko/Uwf2tGDpve+e6MRuXhyYUEwaqMIRL9RCq\nDSTHFUS+QoNaPdccw9yAQkffEckKoXJA5GYkLvkZ06Vh8R7L6Agjh1VNtbT3v+ST\nfrIbSYcEXJoHwWn7vnSewcJm3B1yxpKAVySFbL336yu0cYU8RkZ42SBhJmGD96km\nJ+vuTXQBs5ZTndbZo6/UO+r3+qaQ8rK1r4qeEYaOwSYh9wsFxpLJIgyCwnl0XQQn\nwjQKKConAgMBAAECggEAJwYvf0hvuu/dtVzNKUm87nPVtoEED7KV7TVTrHYgl4z2\nD5D3GvpyxoNZZHYXk1+3Y4NSfMKle0H72e3w4OWy4QUZ7bB/8aIyK2jylpKqf7Lc\nJ7c/NoxYecMi4/wMl06Nc8XW8QMYOvTXTShor/Q3JuH2ewdol9P2Q/e2E7wGszUN\n9Of74KkoQ1bGf8Z3eutjqdP35/n6cETQDoFiqsV8DfHQGCiiNPKWGD2asQDhhRx4\nvh0TGIxvWF5lnSSxvbGsNFUoGWxr8eUH/EGcH1UnHfYL4xhUYqWTEOhM2v/csmzY\nt8o4BntudmXxlfgYU3NyPKkyx7/bVcnW1PJVtoDKkQKBgQDv7j0jjaWt6dJwsKa0\n5XQ4Xga1PbpDb3LWfzZr3IScUxbVytTnOWVXpok4esn4S00iQpAp7FV3YZ/qox7p\ngcOgV7lW6CIShnLgmr4CEt1hV/sRvqddmmgfrY4ZJLy24MSxwBeZiUPNRHKl9RZA\nJr2WsM04JPE4mmf9QOpGjjy71wKBgQDJDguPpQflCGT8s2KNQjBGnWGVfdNHd1vF\nOFP79wkROAEBb2mJsuBBl8Iu3YvImaKAyAln3uqOhQ8rr+y12DqBRgoAyHY3dr46\nlhQFDonNGVdOxrwRnxajKft32W8Tn6pdjuIs4N5q23Luqym5l9PA6h8aa3E+7yeE\ncvRIfqK6MQKBgG4OjED4wpzp+rvybCXictNAXjdY3037m2PE6sPDXZkPjBP5fHus\nGk6Ad8VOncKlV/Z1Lgfs/q9KOr64oH9gJMoyMzQoOyjgP2XD1ZDB8oaqguJ63+7R\n2x1c0Se7cE07AT6/7JNjIZTQ5v41VEWM/75Vz20HlRbvzO+gjVZb/IP1AoGANJwd\nQFhByZe5vTo/dpE0SrYR++kx6Qh9lgzYRR1uXPgXo0WBC0woTGGmqVbFphc1o5c0\nht6Y5/Q/dQIS4b6UCJHIOk46SOckffYZhP0559ZSt0VfnwjPBqEMsV7PJwZnsRWb\nb3zkFngYCgX15B+rhFZ/Dw3AU2SHJaxi6blhYXECgYEAnBAJuYoIfZolppeUZXwp\nAYoTLGMtXnjvX/YFumlEWzjnXLo4Lk9L+lO9sV5BwhQ6klNBARy5TjAedr+Kw0ee\noGh8F964pkF4jy7qBLMkf4/jaEvft/2tg16ELOj74llsd5GPA8Pgzeh1AXtlowwi\nC1Ere9RQ/zspggyX1uEakrI=\n-----END PRIVATE KEY-----\n",
        "ca": "-----BEGIN CERTIFICATE-----\nMIIHFDCCBPygAwIBAgIUZJOYHaqMZR7leKm8iaKrR380T8QwDQYJKoZIhvcNAQEN\nBQAwdjELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MSowKAYDVQQDEyFPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBSb290IENBIC0gRzIwHhcNMjMwMzA5MTQzNjAwWhcNMzMw\nMzA2MTQzNjAwWjB5MQswCQYDVQQGEwJCUjEcMBoGA1UEChMTT3BlbiBGaW5hbmNl\nIEJyYXNpbDEdMBsGA1UECxMUT3BlbiBGaW5hbmNlIHNhbmRib3gxLTArBgNVBAMT\nJE9wZW4gRmluYW5jZSBzYW5kYm94IElzc3VpbmcgQ0EgLSBHMjCCASIwDQYJKoZI\nhvcNAQEBBQADggEPADCCAQoCggEBAJJZYsafIn0x1j8WLDfJ3HSXt65NqnKwGdcW\nn4z4VqdrvcIl6kJM7cjF3ImaN5SLideuK63/QP4tgGilZxooxLE8V8M/uPgGU74K\noTMBuDho6sND/UtHsr/wgkX9+/Kn50vdLbhXZBmvcL+5gtXKDQGR+d1LyaU8EigX\nkhvegMCSyW72PlQ9FetapanOpH0e5+osGRVI9ysm7PFrWE6UOs8EA/d6+v8SwHTW\nbD6iVVgtGnQtm0C4w4H6VVNnFE0F8pSnXQQPzQXMONIFi/UZPSB00H0qnxRvWkw3\nJa7QErS8hdMPGUHQ9N/RujhMhf7tlUArcgod6mc+SYfcI3j1pUcCAwEAAaOCApUw\nggKRMA4GA1UdDwEB/wQEAwIBBjASBgNVHRMBAf8ECDAGAQH/AgEAMB0GA1UdDgQW\nBBR67wuI2HqJ4b0vBD0esdbER0IoPTAfBgNVHSMEGDAWgBQVb9vsej3AhKXXgbWR\nvfmoWNM++jBZBggrBgEFBQcBAQRNMEswSQYIKwYBBQUHMAGGPWh0dHA6Ly9vY3Nw\nLnBraS1nMi5zYW5kYm94LmRpcmVjdG9yeS5vcGVuYmFua2luZ2JyYXNpbC5vcmcu\nYnIwWAYDVR0fBFEwTzBNoEugSYZHaHR0cDovL2NybC5wa2ktZzIuc2FuZGJveC5k\naXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL2lzc3Vlci5jcmwwggF0\nBgNVHSAEggFrMIIBZzCCAWMGCysGAQQBg7ovcAECMIIBUjCB9QYIKwYBBQUHAgIw\ngegMgeVUaGlzIENlcnRpZmljYXRlIGlzIHNvbGVseSBmb3IgdXNlIHdpdGggT3Bl\nbiBGaW5hbmNlIEJyYXNpbCBzYW5kYm94IEFQSXMgU2VydmljZXMuIEl0cyByZWNl\naXB0LCBwb3NzZXNzaW9uIG9yIHVzZSBjb25zdGl0dXRlcyBhY2NlcHRhbmNlIG9m\nIHRoZSBPcGVuIEZpbmFuY2UgQnJhc2lsIHNhbmRib3ggb2YgQVBJcyBDZXJ0aWZp\nY2F0ZSBQb2xpY3kgYW5kIHJlbGF0ZWQgZG9jdW1lbnRzIHRoZXJlaW4uMFgGCCsG\nAQUFBwIBFkxodHRwOi8vcmVwb3NpdG9yeS5wa2ktZzIuc2FuZGJveC5kaXJlY3Rv\ncnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL3BvbGljaWVzMA0GCSqGSIb3DQEB\nDQUAA4ICAQCANeSAlmJy3e9rrgTGShVCyMQhy68j3cAJyFzqCutyNMGHUgFOjAgD\nzIUQZmAepTDJdhJF+BoruBfAIJUr6tD9EBw2MZXiTLHZG9mqtGwsMbeI3o3R9Y3G\nEpGp72jIHw7mtUZdoaWcmgqxCWn6UT9bBKAkdt6KyRepPUy1YI59MZxpVOs5J0s2\nQFd3FRCNxdzgsuGqdxTb1Gre4I5E1vJWcp1Fe/kPdaOgPVC89M6uk3WYTnMNZ20N\n8K0ecXy8+E3K+to35berWn16g1ZrufylX6s2yyxcsUnh5KP1smFd8MePekKIW0SD\n8hqD1MtGQEmzdWrPCT9fZUzONj4VuDcl/vgfKUBsBszTmqwGF34G+663v10KUhga\nkCiIOZtkT9B+aESGAfczQiFO1h4cI52TKwEptfbplrFS2gILrzleqv0JoDDFYVhY\nV5AVDjqeHaniClCi10JdSN11LqNdagpyojN2a2WhVSAigIT3yDeqozlzjgPui/1E\nDt0zBkXd5uFDwNeLUwOribuS3hxVG5Bg73ZJl+UV3ZuAzFFCfkVBz6BeqUusf8+P\n3pqAQ4gzhSWNsTBIsjaVV8ZU8IqxKhBkRUSNjihG2kM8kX9knQvRbCBuuse/dDUe\n4cUJ+wT1omVgq+TWhShOAjsHEa233omXbH7v5igLBEkzzqmM5cAv8Q==\n-----END CERTIFICATE-----\n-----BEGIN CERTIFICATE-----\nMIIFvDCCA6SgAwIBAgIUKhBUxL5Dt4w3xH1V3X1n+x/e3hcwDQYJKoZIhvcNAQEN\nBQAwdjELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MSowKAYDVQQDEyFPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBSb290IENBIC0gRzIwHhcNMjMwMzA5MTQzNjAwWhcNMzgw\nMzA1MTQzNjAwWjB2MQswCQYDVQQGEwJCUjEcMBoGA1UEChMTT3BlbiBGaW5hbmNl\nIEJyYXNpbDEdMBsGA1UECxMUT3BlbiBGaW5hbmNlIHNhbmRib3gxKjAoBgNVBAMT\nIU9wZW4gRmluYW5jZSBzYW5kYm94IFJvb3QgQ0EgLSBHMjCCAiIwDQYJKoZIhvcN\nAQEBBQADggIPADCCAgoCggIBALJFBgmKj3iDF3C8+8smNNQDxLFA9kCcca1iaxQf\nvMI/FKGW2ullHhH+W3EGEajn39QOlccGyrfCONHLqMW53+HAMtwiIvcrJgj72V7D\nnYflO3aaCFwoC31PL1+pMBo88F6jvezZ8BlRnheT7urCs6+onhz8pm0cVNc77U5X\npi8IOJz1QFKecJnFLjG0NiLCzOzjLSo0A8Rue9K/H5fjq+PqKdXG94AoQyFUwlsU\ny4aXbylDz1kRiOSnOlRNPcY/su95pFKQbGgaZZ1fLf89i5PtHAUu92FbD7H7OyYX\nXpZ97La0d7cUH0A4nb+LpOd/f0c8lAN2Ya1B8aKvWiF23q3c8EoAJyhrdkHKe6yI\nYvLC5G5jkbJefeQcp34IgD8T+Tn3aBF7YgmlYUMbnsuokBG28Hr50EAklCclA0bb\n4pmf8nE6y7VQ0CM/bNZd1F9AjxLukkyvkrOD6A6uv+c5KeC+da245dBzsyhiKe9R\nRX5Gkf7NSkDu9b9YkdDaWV6LXxpUA0SmdT9M16yK3XPDKOWBI4gVSB1KuwrOcal/\ndMwFUlxvqdGugRbxDNNukxa0l3JztGg6XYLjEiiYrQ+7HChbUVNlM0l0VZAz4eON\ngYrq2ExUDWlQXiES389/Qz3R3yDk9ib1YsMHwAux2ulCssFVn4EgtnYFfgf3o01J\n3CedAgMBAAGjQjBAMA4GA1UdDwEB/wQEAwIBBjAPBgNVHRMBAf8EBTADAQH/MB0G\nA1UdDgQWBBQVb9vsej3AhKXXgbWRvfmoWNM++jANBgkqhkiG9w0BAQ0FAAOCAgEA\nVPrUd4UDjOhkxOzSN4bMr0cULZJwQPRV8aj99tzdv8Ef44CwLVkLmm7Z2d1uRA9l\n7xbK6W8L1oL95iV4K4o2u4+ZFG7mrOfU2T2wgTfMlIxHDoAxS49flUYkBpQI1Wj4\nJBZ6fKGFVH6PyIio0I2Mx2u80ZX6lPYQ2q4DR6eBUoNt8T8XSWpD4TjroFbOVIp+\nN84alBca/pvW2aF2HwPndrL/Y++HZp3TpdUeBUT757KOZ7hdwf30pxd8qNn8+peb\nbP2h6b9pjKAmS8ciBExJzchhQWJRP6LIdvexTsBQ1HLxlZNrlg66wYT0kuVVzRTa\n0qRvIjQ0ntmhy2DtmE5VFT9O8ahcQL5Ddk8B4dhiy59vjALS6kIUXJ6GCobzRUsQ\na7b7J7nu+PTY+qVo0LsTMO1rVTUXD63gVk8QmPUwnvduk9nxraNpVP+m17BuEcls\nEsoGAAQYcmzOlnZpqhhbTnbsEayW1bMyxkLjBjXpOfBgrvyv5fU/09lP6VB20FJr\nzVPZWr5PTzaaizDDecSKgZ1ANIwXIIwWirwzDqqQb922JtcH+Ca6JJWgrV7+kDCU\ncVzwKVYievjXMCsmRSzDKEgp4n1AgrxcoaH0smD+qA+wzfsMqvEA1iTNW7zdnF0o\n6UJ9rkWxKr+JRZ5jFO+kpKQ1DxfDJZE554aO8AXzYEI=\n-----END CERTIFICATE-----\n"
    }
}
```

</details>



---

*Conteúdo baixado em 16/09/2026, 15:38:16*
