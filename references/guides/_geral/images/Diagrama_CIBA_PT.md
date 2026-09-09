# Diagrama_CIBA_PT

![Diagrama_CIBA_PT](Diagrama_CIBA_PT.png)

## Texto Extraído

Creditor

do pagamento

9
<<async>>
30) http 200 (OK)

29) Processament
<q -------------------------------

22) Valida certificado SSL

5) Valida certificado SSL
e scopes

e scopes
23) Gera access_token

6) Gera access_token
26) Validagdes de

negocio

AUTHORISED

O
—
Oo
—
c
fo)
—
fo)
Q

10) Status do consentimento
q_id)

AWAITING AUTHORISATION
20) Status do consentimento
28) Status do consentimento

CONSUMED

O
7)
S)
<
{eo}
fe)
{S
oO
E
oO
1@))
Oo
Qa
Oo
To
n
=)
2
Oo
£
a
=
oO

pe
)

FAPI CIBA

de pagamento
openid

awaiting...

payments)

/payments/<version>/pix/payments

payments/<version>/pix/payments/

21) POST /token (Pedido de
(paymentld)

24) access_token scope:

(payments, openid)

©
pa
cS
=
DS
©
E
9
S)
Cc
®
x<
e)
£
2)
n
®
3)
3)
©

8) POST /payments/<version>
13) Response: auth_req_id

/consents
12) Back Channel HTTP:

3) Estabelece mTLS

4) POST /token (Pedido de

' access_token e sco

payments

ee

' 9) http 201 (created)

11) Response: consentid,

autenticagao

' 25) POST

' 27) http 201 (created)

ee
33) http 200 (Ok)

status
(Accepted Settlement Completed
Até que esteja em um dos seguintes status: ACSC, RJCT, PATC, PDNG

ou SCHD

--------------------------------p'

Iniciadora

[pooling]

34) Exibe o retorno ao usuario de
acordo com o status atual do

a
=
wi
c
2
o
2
I
6
Zz
=
n
=)
a
2)
=
)
+

19) Interagao: aceite do usuario

1) Seleciona detentora +
dados de pagamento e envia
15) Acessar app ou site

a solicitagao
16) Ul: autenticagao

4 ----------------------------------

18) Ul: autorizagao

sq ----------------------------------

pagamento

Aplicagao Detentora

---
**Arquivo original:** `Diagrama_CIBA_PT.png`
**Tamanho:** 1179.12 KB