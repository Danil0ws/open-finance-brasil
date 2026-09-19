# Payment

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Payment](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Payment)
**Slug:** `Payment`

---

Find payment endpoint for the selected bank from the directory of participants

```
    const paymentEndpoint = getEndpoint(
      selectedAuthServer,
      'payments-pix',
      'open-banking/payments/v1/pix/payments$'
    );
```
Payment endpoint found
```
    let date = new Date();
    const offset = date.getTimezoneOffset();
    date = new Date(date.getTime() - offset * 60 * 1000);

```
Create payment object

```
    const payment = {
      creditorAccount: createdConsent.data.payment.details.creditorAccount,
      localInstrument: createdConsent.data.payment.details.localInstrument,
      proxy: createdConsent.data.payment.details.proxy,
      remittanceInformation: 'Making a payment',
      cnpjInitiator: '59285411000113',
      payment: {
        amount: createdConsent.data.payment.amount,
        currency: createdConsent.data.payment.currency,
      },
    };

```

Signing payment

```
const jwt = await new jose.SignJWT({ data: payment })
      .setProtectedHeader({ alg: 'PS256', typ: 'JWT', kid: privateJwk.kid })
      .setIssuedAt()
      .setIssuer(config.data.organisation_id)
      .setJti(nanoid())
      .setAudience(paymentEndpoint)
      .setExpirationTime('5m')
      .sign(key);
```
Create payment resource using the signed payment JWT 
```
et paymentResponse = await client.requestResource(
      `${paymentEndpoint}`,
      tokenSet,
      {
        body: jwt,
        method: 'POST',
        headers: {
          'content-type': 'application/jwt',
          'x-idempotency-key': nanoid(),
        },
      }
    );
    paymentLog('Payment resource created successfully %O', paymentResponse.body.toString());
    paymentLog('Validate payment response as it is a JWT');
    paymentLog('Retrieve the keyset for the bank (this has already been done and could be cached)');
    //Retrieve the keyset of the sending bank
    const JWKS = await jose.createRemoteJWKSet(
      new URL(
        `https://keystore.sandbox.directory.openbankingbrasil.org.br/${selectedOrganisation.OrganisationId}/application.jwks`
      )
    );
```

Validate the jwt came from the correct bank and was meant to be sent to me

```
let { payload } = await jose.jwtVerify(
      paymentResponse.body.toString(),
      JWKS,
      {
        issuer: selectedOrganisation.OrganisationId,
        audience: config.data.organisation_id,
        clockTolerance: 2,
      }
    );
    paymentLog('Payment response extracted and validated');

```

Check for payment's state

```
let x = 0;
    while (!['ACSP', 'ACCC', 'RJCT'].includes(payload.data.status)) {
      paymentLog(
        'Payment still not in a valid end state. Status: %O. Will check again to see if it has gone through.', payload.data.status
      );
      paymentLog(payload);
      paymentLog(
        'Use the self link on the payment to retrieve the latest record status. %O', payload.links.self
      );
      paymentResponse = await client.requestResource(
        payload.links.self,
        tokenSet,
        {
          headers: { accept: 'application/jwt', 'x-idempotency-key': nanoid() },
        }
      );
      
      paymentLog(
        'Validate and extract the payment response from the bank'
      );
      ({ payload } = await jose.jwtVerify(
        paymentResponse.body.toString(),
        JWKS,
        {
          issuer: selectedOrganisation.OrganisationId,
          audience: config.data.organisation_id,
          clockTolerance: 2,
        }
      ));
      x = x + 1;
      if (x > 5) {
        paymentLog(
          'Payment has not reached final state after 5 iterations, failing'
        );
        payload = { msg: 'Unable To Complete Payment', payload: payload };
        payload.stringify = JSON.stringify(payload);
        return res.render('cb', { claims: tokenSet.claims(), payload });
      }
    }

    paymentLog('Payment has reached a final state of',payload.data.status);
    paymentLog(payload);
    payload.stringify = JSON.stringify(payload);
    paymentLog('Payment execution complete');
    return res.render('cb', { claims: tokenSet.claims(), payload });
  });
```

Defining make payment view:

```
app.post('/makepayment', async (req, res) => {
    if (req.body.bank) {
      //Setup the client
      consentLog('Customer has select bank issuer to use %O', req.body.bank);
      const { fapiClient, localIssuer } = await setupClient(req.body.bank);
      consentLog('Client created, ready to talk to the chosen bank');
      client = fapiClient;
      issuer = localIssuer;
    }
    else {
      throw Error('No bank was selected');
    }
```

---

*Conteúdo baixado em 16/09/2026, 15:38:15*
