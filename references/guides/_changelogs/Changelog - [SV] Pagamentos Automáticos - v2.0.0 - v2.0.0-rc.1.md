# Changelog - [SV] Pagamentos Automáticos - v2.0.0 - v2.0.0-rc.1

## Alterações na seção de orientações do swagger

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

/info

Alterado - "description"

Alteração

API de Iniciação de Pagamentos automáticos, responsável por viabilizar as operações de iniciação de pagamentos automáticos (Pix au...

API de Iniciação de Pagamentos automáticos, responsável por viabilizar as operações de iniciação de pagamentos automáticos (Pix au...

## GET /pix/recurring-payments

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/items/date

Alterado - "description"

Alteração

Data em que o pagamento será realizado.

Data em que o pagamento será realizado. Uma string com a utilização de timezone UTC-3 (UTC time format).

get/responses/200/data/items/endToEndId

Alterado - "example"

Alteração

E9040088820210128000800123873170

E9040088820241225150000123873170

## POST /pix/recurring-payments

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/requestBody/data/date

Alterado - "description"

Alteração

Data em que o pagamento será realizado.

Data em que o pagamento será realizado. Uma string com a utilização de timezone UTC-3 (UTC time format).

post/requestBody/data/endToEndId

Alterado - "example"

Alteração

E9040088820210128000800123873170

E9040088820241225150000123873170

post/requestBody/data/creditorAccount

Alterado - "description"

Alteração

Objeto que contém a identificação da conta de destino do beneficiário/recebedor.

Objeto que contém a identificação da conta de destino do beneficiário/recebedor.

\[Restrição\] - Se /data/paymentReference = "zero", as informações da conta de crédito enviadas (/data/creditorAccount) devem ser iguais as presentes na conta de crédito informada na criação do consentimento(\`/data/recurringConfiguration/automatic/firstPayment/creditorAccount\`)

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/201/data/date

Alterado - "description"

Alteração

Data em que o recurso foi criado. Uma string com a utilização de timezone UTC(UTC time format).

Data em que o pagamento será realizado. Uma string com a utilização de timezone UTC-3 (UTC time format).

post/responses/201/data/endToEndId

Alterado - "example"

Alteração

E9040088820210128000800123873170

E9040088820241225150000123873170

post/responses/201/data/cancellation/cancelledBy/document/identification

Alterado - "maxLength"

Alteração

11

14

post/responses/201/data/debtorAccount/properties

Removido obrigatóriedade no campo 'issuer'

Remoção

required

## GET /pix/recurring-payments/{recurringPaymentId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/date

Alterado - "description"

Alteração

Data em que o pagamento será realizado.

Data em que o pagamento será realizado. Uma string com a utilização de timezone UTC-3 (UTC time format).

get/responses/200/data/endToEndId

Alterado - "example"

Alteração

E9040088820210128000800123873170

E9040088820241225150000123873170

get/responses/200/data/cancellation/cancelledBy/document/identification

Alterado - "maxLength"

Alteração

11

14

get/responses/200/data/debtorAccount/properties

Removido obrigatóriedade no campo 'issuer'

Remoção

required

## PATCH /pix/recurring-payments/{recurringPaymentId}

### request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch/responses/200/data/cancellation/cancelledBy/document/identification

Alterado - "maxLength"

Alteração

11

14

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch/responses/200/data/date

Alterado - "description"

Alteração

Data em que o recurso foi criado. Uma string com a utilização de timezone UTC(UTC time format).

Data em que o pagamento será realizado. Uma string com a utilização de timezone UTC-3 (UTC time format).

patch/responses/200/data/endToEndId

Alterado - "example"

Alteração

E9040088820210128000800123873170

E9040088820241225150000123873170

patch/requestBody/data/cancellation/cancelledBy/document/identification

Alterado - "maxLength"

Alteração

11

14

patch/responses/200/data/debtorAccount/properties

Removido obrigatóriedade no campo 'issuer'

Remoção

required

patch/responses/422/errors/items/code

Alterado - "description"

Alteração

-   PAGAMENTO\_NAO\_PERMITE\_CANCELAMENTO: Pagamento está com um status que não permite cancelamento
    
-   CANCELAMENTO\_FORA\_PERIODO\_PERMITIDO: O usuário solicitou o cancelamento fora da janela de tempo permitido.
    

-   PAGAMENTO\_NAO\_PERMITE\_CANCELAMENTO: Pagamento está com um status que não permite cancelamento.
    
-   CANCELAMENTO\_FORA\_PERIODO\_PERMITIDO: O usuário solicitou o cancelamento fora da janela de tempo permitido.
    
-   PARAMETRO\_INVALIDO: Os parâmetros informados não obedecem a formatação especificada.
    
-   PARAMETRO\_NAO\_INFORMADO: Algum ou todos os campos obrigatórios não foram informados.
    

patch/responses/422/errors/items/code/enum

Adicionado - "PARAMETRO\_INVALIDO"

Adição

enum

patch/responses/422/errors/items/code/enum

Adicionado - "PARAMETRO\_NAO\_INFORMADO"

Adição

enum

patch/responses/422/errors/items/detail

Alterado - "description"

Alteração

-   PAGAMENTO\_NAO\_PERMITE\_CANCELAMENTO: Pagamento está com um status que não permite cancelamento
    
-   CANCELAMENTO\_FORA\_PERIODO\_PERMITIDO: O usuário solicitou o cancelamento fora da janela de tempo permitido.
    

-   PAGAMENTO\_NAO\_PERMITE\_CANCELAMENTO: Pagamento está com um status que não permite cancelamento.
    
-   CANCELAMENTO\_FORA\_PERIODO\_PERMITIDO: O usuário solicitou o cancelamento fora da janela de tempo permitido.
    
-   PARAMETRO\_INVALIDO: Os parâmetros informados não obedecem a formatação especificada.
    
-   PARAMETRO\_NAO\_INFORMADO: Algum ou todos os campos obrigatórios não foram informados.
    

patch/responses/422/errors/items/title

Alterado - "description"

Alteração

-   PAGAMENTO\_NAO\_PERMITE\_CANCELAMENTO: Pagamento está com um status que não permite cancelamento
    
-   CANCELAMENTO\_FORA\_PERIODO\_PERMITIDO: O usuário solicitou o cancelamento fora da janela de tempo permitido.
    

-   PAGAMENTO\_NAO\_PERMITE\_CANCELAMENTO: Pagamento está com um status que não permite cancelamento.
    
-   CANCELAMENTO\_FORA\_PERIODO\_PERMITIDO: O usuário solicitou o cancelamento fora da janela de tempo permitido.
    
-   PARAMETRO\_INVALIDO: Os parâmetros informados não obedecem a formatação especificada.
    
-   PARAMETRO\_NAO\_INFORMADO: Algum ou todos os campos obrigatórios não foram informados.
    

## POST /recurring-consents

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/firstPayment

Alterado - "description"

Alteração

Definições para o primeiro pagamento. É considerado como o pagamento da adesão ao serviço pelo usuário pagador. Para casos em que conta recebedora e conta pagadora pertencem ao mesmo detentor, este deve garantir que a conta de crédito informada pertence ao titular do CNPJ enviado no campo “/data/creditors/cpfCnpj”. A conta de crédito informada no momento do primeiro pagamento deve ser a mesma informada dentro deste objeto. Caso não respeitado, o detentor deve rejeitar o pagamento com o motivo DETALHE\_PAGAMENTO\_INVALIDO, sincronamente (HTTP 422) ou assincronamente (HTTP 200).

Definições para o primeiro pagamento. É considerado como o pagamento da adesão ao serviço pelo usuário pagador.

\[Restrição\] Para casos em que conta recebedora e conta pagadora pertencem ao mesmo detentor (/data/debtorAccount/ispb = /data/recurringConfiguration/automatic/firstPayment/creditorAccount/ispb), o detentor deve garantir que a conta de crédito informada pertence ao titular do CNPJ enviado no campo “/data/creditors/cpfCnpj”.

post/requestBody/data/creditors/items

Alterado - "description"

Alteração

Objeto contendo os dados do recebedor (creditor). Em casos de transferências inteligentes para clientes PJ, os CNPJs informados devem possuir a mesma raiz do CNPJ enviado no campo /data/businessEntity/document/identification. Em casos de transferências inteligentes para clientes PN, deve-se aceitar apenas um item no array e este item deve conter as informações do recebedor. O CPF informado deve ser o mesmo do /data/loggedUser/document/identification. Caso alguma das regras mencionadas não sejam seguidas, o detentor deve rejeitar a solicitação (sincronamente) com o erro DETALHE\_PAGAMENTO\_INVALIDO, e o detalhe deve ser preenchido com a informação referente ao erro.

\[Restrição\] Caso o consentimento de longa duração seja para o produto Pix Automático (“automatic” selecionado no oneOf do objeto “/data/recurringConfiguration”), apenas um recebedor é permitido e esse deve ser pessoa jurídica.

Objeto contendo os dados do recebedor (creditor).

\*\*Regras para Transferências inteligentes:\*\*

1.  Para clientes pessoa física/natural:
    

-   Deve aceitar apenas um item no array; e;
    
-   O CPF informado deve ser o mesmo do \`/data/loggedUser/document/identification\`.
    

2.  Para clientes pessoa jurídica:
    

-   Não há limite para quantidade de itens no array; e;
    
-   O(s) CNPJ informado deve possuir a mesma raiz do CNPJ enviado no campo \`/data/businessEntity/document/identification\`.
    

\*\*Regras para Pix Automático:\*\*

-   Apenas um item é permitido no array; e;
    
-   O documento informado deve ser de um recebedor pessoa jurídica.
    

post/requestBody/data/debtorAccount

Alterado - "description"

Alteração

Objeto que contém a identificação da conta de origem do pagador.  
As informações quanto à conta de origem do pagador poderão ser trazidas no consentimento para a detentora, caso a iniciadora tenha coletado essas informações do cliente. Do contrário, será coletada na detentora e trazida para a iniciadora como resposta à criação do pagamento.

Objeto que contém a identificação da conta de origem do pagador.

-   Caso a ITP tenha coletado as informações de conta do usuário pagador, essas poderão ser enviadas no consentimento para a detentora neste objeto, ou;
    
-   Se não coletado pelo ITP, o usuário pagador precisará definir durante a autorização do consentimento.
    
-   Mesmo se enviado pela ITP, o usuário pagador pode alterar durante a autorização do consentimento.
    

post/requestBody/data/expirationDateTime

Alterado - "description"

Alteração

Data e hora em que o consentimento deve deixar de ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https://datatracker.ietf.org/doc/html/rfc3339), sempre com a utilização de timezone UTC(UTC time format).

Data e hora em que o consentimento deve deixar de ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https://datatracker.ietf.org/doc/html/rfc3339), sempre com a utilização de timezone UTC (UTC time format).

\[Restrição\] Caso o consentimento seja para Pix Automático ("automatic" selecionado no oneOf "/data/recurringConfiguration/") o horário de expiração do consentimento precisa ser às 23:59:59 (UTC).

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/firstPayment

Alterado - "description"

Alteração

Definições para o primeiro pagamento. É considerado como o pagamento da adesão ao serviço pelo usuário pagador. Para casos em que conta recebedora e conta pagadora pertencem ao mesmo detentor, este deve garantir que a conta de crédito informada pertence ao titular do CNPJ enviado no campo “/data/creditors/cpfCnpj”. A conta de crédito informada no momento do primeiro pagamento deve ser a mesma informada dentro deste objeto. Caso não respeitado, o detentor deve rejeitar o pagamento com o motivo DETALHE\_PAGAMENTO\_INVALIDO, sincronamente (HTTP 422) ou assincronamente (HTTP 200).

Definições para o primeiro pagamento. É considerado como o pagamento da adesão ao serviço pelo usuário pagador.

\[Restrição\] Para casos em que conta recebedora e conta pagadora pertencem ao mesmo detentor (/data/debtorAccount/ispb = /data/recurringConfiguration/automatic/firstPayment/creditorAccount/ispb), o detentor deve garantir que a conta de crédito informada pertence ao titular do CNPJ enviado no campo “/data/creditors/cpfCnpj”.

post/responses/201/data/creditors/items

Alterado - "description"

Alteração

Objeto contendo os dados do recebedor (creditor). Em casos de transferências inteligentes para clientes PJ, os CNPJs informados devem possuir a mesma raiz do CNPJ enviado no campo /data/businessEntity/document/identification. Em casos de transferências inteligentes para clientes PN, deve-se aceitar apenas um item no array e este item deve conter as informações do recebedor. O CPF informado deve ser o mesmo do /data/loggedUser/document/identification. Caso alguma das regras mencionadas não sejam seguidas, o detentor deve rejeitar a solicitação (sincronamente) com o erro DETALHE\_PAGAMENTO\_INVALIDO, e o detalhe deve ser preenchido com a informação referente ao erro.

\[Restrição\] Caso o consentimento de longa duração seja para o produto Pix Automático (“automatic” selecionado no oneOf do objeto “/data/recurringConfiguration”), apenas um recebedor é permitido e esse deve ser pessoa jurídica.

Objeto contendo os dados do recebedor (creditor).

\*\*Regras para Transferências inteligentes:\*\*

1.  Para clientes pessoa física/natural:
    

-   Deve aceitar apenas um item no array; e;
    
-   O CPF informado deve ser o mesmo do \`/data/loggedUser/document/identification\`.
    

2.  Para clientes pessoa jurídica:
    

-   Não há limite para quantidade de itens no array; e;
    
-   O(s) CNPJ informado deve possuir a mesma raiz do CNPJ enviado no campo \`/data/businessEntity/document/identification\`.
    

\*\*Regras para Pix Automático:\*\*

-   Apenas um item é permitido no array; e;
    
-   O documento informado deve ser de um recebedor pessoa jurídica.
    

post/responses/201/data/debtorAccount

Alterado - "description"

Alteração

Objeto que contém a identificação da conta de origem do pagador. As informações quanto à conta de origem do pagador poderão ser trazidas no consentimento para a detentora, caso a iniciadora tenha coletado essas informações do cliente.  
Do contrário, será coletada na detentora e trazida para a iniciadora como resposta à criação do pagamento.

\[Restrições\]

-   Objeto obrigatório que deverá ser retornado quando o consentimento estiver ou passar pelo status AUTHORISED;
    

Objeto que contém a identificação da conta de origem do pagador.

-   Caso a ITP tenha coletado as informações de conta do usuário pagador, essas poderão ser enviadas no consentimento para a detentora neste objeto, ou;
    
-   Se não coletado pelo ITP, o usuário pagador precisará definir durante a autorização do consentimento.
    
-   Mesmo se enviado pela ITP, o usuário pagador pode alterar durante a autorização do consentimento.
    

\[Restrições\]

-   Objeto obrigatório que deverá ser retornado quando o consentimento estiver ou passar pelo status AUTHORISED;
    

post/responses/201/data/statusUpdateDateTime

Alterado - "description"

Alteração

Data e hora em que o consentimento deve passar a ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https://datatracker.ietf.org/doc/html/rfc3339), sempre com a utilização de timezone UTC(UTC time format).

\[Restrição\] Caso esse campo não seja enviado pelo iniciador na requisição, o detentor deve preencher esse campo com o mesmo valor atribuído ao campo /data/creationDateTime. Caso o campo /data/startDateTime enviado seja anterior ao valor do campo /data/creationDateTime, o detentor deve substituir o valor do campo /data/startDateTime pelo valor do campo /data/creationDateTime

Data e hora em que o consentimento teve o status atualizado. Uma string com data e hora conforme especificação \[RFC-3339\](https://datatracker.ietf.org/doc/html/rfc3339), sempre com a utilização de timezone UTC(UTC time format).

post/responses/201

Alterado - "description"

Alteração

Objeto contendo as informações de consentimento para a iniciação de pagamento individual.

Objeto contendo as informações de consentimento para iniciação de pagamento automático.

post/responses/201/data/expirationDateTime

Alterado - "description"

Alteração

Data e hora em que o consentimento deve deixar de ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https://datatracker.ietf.org/doc/html/rfc3339), sempre com a utilização de timezone UTC(UTC time format).

Data e hora em que o consentimento deve deixar de ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https://datatracker.ietf.org/doc/html/rfc3339), sempre com a utilização de timezone UTC (UTC time format).

\[Restrição\] Caso o consentimento seja para Pix Automático ("automatic" selecionado no oneOf "/data/recurringConfiguration/") o horário de expiração do consentimento precisa ser às 23:59:59 (UTC).

## GET /recurring-consents/{recurringConsentId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/minimumVariableAmount

Alterado - "description"

Alteração

Valor definido pelo usuário recebedor. Se o usuário pagador atribuir um valor máximo para os pagamentos daquela autorização, ele ...

Valor definido pelo usuário recebedor. Se o usuário pagador atribuir um valor máximo para os pagamentos daquela autorização (camp...

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/firstPayment

Alterado - "description"

Alteração

Definições para o primeiro pagamento. É considerado como o pagamento da adesão ao serviço pelo usuário pagador. Para casos em que conta recebedora e conta pagadora pertencem ao mesmo detentor, este deve garantir que a conta de crédito informada pertence ao titular do CNPJ enviado no campo “/data/creditors/cpfCnpj”. A conta de crédito informada no momento do primeiro pagamento deve ser a mesma informada dentro deste objeto. Caso não respeitado, o detentor deve rejeitar o pagamento com o motivo DETALHE\_PAGAMENTO\_INVALIDO, sincronamente (HTTP 422) ou assincronamente (HTTP 200).

Definições para o primeiro pagamento. É considerado como o pagamento da adesão ao serviço pelo usuário pagador.

\[Restrição\] Para casos em que conta recebedora e conta pagadora pertencem ao mesmo detentor (/data/debtorAccount/ispb = /data/recurringConfiguration/automatic/firstPayment/creditorAccount/ispb), o detentor deve garantir que a conta de crédito informada pertence ao titular do CNPJ enviado no campo “/data/creditors/cpfCnpj”.

get/responses/200/data/creditors/items

Alterado - "description"

Alteração

Objeto contendo os dados do recebedor (creditor). Em casos de transferências inteligentes para clientes PJ, os CNPJs informados devem possuir a mesma raiz do CNPJ enviado no campo /data/businessEntity/document/identification. Em casos de transferências inteligentes para clientes PN, deve-se aceitar apenas um item no array e este item deve conter as informações do recebedor. O CPF informado deve ser o mesmo do /data/loggedUser/document/identification. Caso alguma das regras mencionadas não sejam seguidas, o detentor deve rejeitar a solicitação (sincronamente) com o erro DETALHE\_PAGAMENTO\_INVALIDO, e o detalhe deve ser preenchido com a informação referente ao erro.

\[Restrição\] Caso o consentimento de longa duração seja para o produto Pix Automático (“automatic” selecionado no oneOf do objeto “/data/recurringConfiguration”), apenas um recebedor é permitido e esse deve ser pessoa jurídica.

Objeto contendo os dados do recebedor (creditor).

\*\*Regras para Transferências inteligentes:\*\*

1.  Para clientes pessoa física/natural:
    

-   Deve aceitar apenas um item no array; e;
    
-   O CPF informado deve ser o mesmo do \`/data/loggedUser/document/identification\`.
    

2.  Para clientes pessoa jurídica:
    

-   Não há limite para quantidade de itens no array; e;
    
-   O(s) CNPJ informado deve possuir a mesma raiz do CNPJ enviado no campo \`/data/businessEntity/document/identification\`.
    

\*\*Regras para Pix Automático:\*\*

-   Apenas um item é permitido no array; e;
    
-   O documento informado deve ser de um recebedor pessoa jurídica.
    

get/responses/200/data/debtorAccount

Alterado - "description"

Alteração

Objeto que contém a identificação da conta de origem do pagador. As informações quanto à conta de origem do pagador poderão ser trazidas no consentimento para a detentora, caso a iniciadora tenha coletado essas informações do cliente.  
Do contrário, será coletada na detentora e trazida para a iniciadora como resposta à criação do pagamento.

\[Restrições\]

-   Objeto obrigatório que deverá ser retornado quando o consentimento estiver ou passar pelo status AUTHORISED;
    

Objeto que contém a identificação da conta de origem do pagador.

-   Caso a ITP tenha coletado as informações de conta do usuário pagador, essas poderão ser enviadas no consentimento para a detentora neste objeto, ou;
    
-   Se não coletado pelo ITP, o usuário pagador precisará definir durante a autorização do consentimento.
    
-   Mesmo se enviado pela ITP, o usuário pagador pode alterar durante a autorização do consentimento.
    

\[Restrições\]

-   Objeto obrigatório que deverá ser retornado quando o consentimento estiver ou passar pelo status AUTHORISED;
    

get/responses/200

Alterado - "description"

Alteração

Objeto contendo as informações de consentimento para a iniciação de pagamento individual.

Objeto contendo as informações de consentimento para iniciação de pagamento automático.

get/responses/200/data/expirationDateTime

Alterado - "description"

Alteração

Data e hora em que o consentimento deve deixar de ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https://datatracker.ietf.org/doc/html/rfc3339), sempre com a utilização de timezone UTC(UTC time format).

Data e hora em que o consentimento deve deixar de ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https://datatracker.ietf.org/doc/html/rfc3339), sempre com a utilização de timezone UTC (UTC time format).

\[Restrição\] Caso o consentimento seja para Pix Automático ("automatic" selecionado no oneOf "/data/recurringConfiguration/") o horário de expiração do consentimento precisa ser às 23:59:59 (UTC).

## PATCH /recurring-consents/{recurringConsentId}

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch

Alterado - "description"

Alteração

Método para rejeitar, revogar ou editar um consentimento de longa duração: 1 - Informações sobre a revogação: - Caso bem sucedid...

Método para rejeitar, revogar ou editar um consentimento de longa duração: 1 - Informações sobre a revogação: - Caso bem sucedid...

patch/requestBody/data/oneOf/0/loggedUser/document/identification

Alterado - "description"

Alteração

Número do documento de identificação oficial do pagador ou recebedor, pessoa natural ou jurídica.

Número do documento de identificação oficial do usuário logado na instituição iniciadora.

patch/requestBody/data/oneOf/0/loggedUser/document/identification

Alterado - "pattern"

Alteração

^(?:\\d{11}|\\d{14})$

^(\\d{11})$

patch/requestBody/data/oneOf/0/loggedUser/document/rel

Alterado - "description"

Alteração

Tipo de documento de identificação oficial do pagador ou recebedor, pessoa natural ou jurídica.

Tipo do documento de identificação oficial do usuário logado na instituição iniciadora.

patch/requestBody/data/oneOf/0/loggedUser/document/rel/enum

Removido - "CNPJ"

Remoção

enum

patch/requestBody/data/oneOf/0/creditors/items

Alterado - "description"

Alteração

Objeto contendo os dados do recebedor (creditor).

\[Restrição\] Caso o consentimento de longa duração seja para o produto Pix Automático (“automatic” selecionado no oneOf do objeto “/data/recurringConfiguration”), apenas um recebedor é permitido e esse deve ser pessoa jurídica.

Objeto contendo os dados do recebedor (creditor).

\*\*Regras para Transferências inteligentes:\*\*

1.  Para clientes pessoa física/natural:
    

-   Deve aceitar apenas um item no array; e;
    
-   O CPF informado deve ser o mesmo do \`/data/loggedUser/document/identification\`.
    

2.  Para clientes pessoa jurídica:
    

-   Não há limite para quantidade de itens no array; e;
    
-   O(s) CNPJ informado deve possuir a mesma raiz do CNPJ enviado no campo \`/data/businessEntity/document/identification\`.
    

\*\*Regras para Pix Automático:\*\*

-   Apenas um item é permitido no array; e;
    
-   O documento informado deve ser de um recebedor pessoa jurídica.
    

patch/requestBody/data/oneOf/0/expirationDateTime

Alterado - "description"

Alteração

Data e hora em que o consentimento deve deixar de ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https://datatracker.ietf.org/doc/html/rfc3339), sempre com a utilização de timezone UTC(UTC time format).

\[Restrição\] Caso esse campo não seja enviado, a instituição detentora deve considerar a extensão do prazo para um período indeterminado; ou;

Caso enviado, esse campo deve ser, no mínimo, D, sendo D o dia da requisição.

Data e hora em que o consentimento deve deixar de ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https://datatracker.ietf.org/doc/html/rfc3339), sempre com a utilização de timezone UTC(UTC time format).

\[Restrição\] Caso esse campo não seja enviado, a instituição detentora deve considerar a extensão do prazo para um período indeterminado; ou;

Caso enviado, esse campo deve ser, no mínimo, D, sendo D o dia da requisição e o horário deve ser às 23:59:59 (UTC).

patch/requestBody/data/oneOf/0/riskSignals

Alterado - "description"

Alteração

Sinais de risco para iniciação de pagamentos automáticos \[Restrição\] Deve ser enviado quando o consentimento for para o produto P...

Sinais de risco para iniciação de pagamentos automáticos \[Restrição\] Deve ser enviado quando o consentimento for para o produto P...

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/minimumVariableAmount

Alterado - "description"

Alteração

Valor definido pelo usuário recebedor. Se o usuário pagador atribuir um valor máximo para os pagamentos daquela autorização, ele ...

Valor definido pelo usuário recebedor. Se o usuário pagador atribuir um valor máximo para os pagamentos daquela autorização (camp...

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/firstPayment

Alterado - "description"

Alteração

Definições para o primeiro pagamento. É considerado como o pagamento da adesão ao serviço pelo usuário pagador. Para casos em que conta recebedora e conta pagadora pertencem ao mesmo detentor, este deve garantir que a conta de crédito informada pertence ao titular do CNPJ enviado no campo “/data/creditors/cpfCnpj”. A conta de crédito informada no momento do primeiro pagamento deve ser a mesma informada dentro deste objeto. Caso não respeitado, o detentor deve rejeitar o pagamento com o motivo DETALHE\_PAGAMENTO\_INVALIDO, sincronamente (HTTP 422) ou assincronamente (HTTP 200).

Definições para o primeiro pagamento. É considerado como o pagamento da adesão ao serviço pelo usuário pagador.

\[Restrição\] Para casos em que conta recebedora e conta pagadora pertencem ao mesmo detentor (/data/debtorAccount/ispb = /data/recurringConfiguration/automatic/firstPayment/creditorAccount/ispb), o detentor deve garantir que a conta de crédito informada pertence ao titular do CNPJ enviado no campo “/data/creditors/cpfCnpj”.

patch/responses/200/data/creditors/items

Alterado - "description"

Alteração

Objeto contendo os dados do recebedor (creditor). Em casos de transferências inteligentes para clientes PJ, os CNPJs informados devem possuir a mesma raiz do CNPJ enviado no campo /data/businessEntity/document/identification. Em casos de transferências inteligentes para clientes PN, deve-se aceitar apenas um item no array e este item deve conter as informações do recebedor. O CPF informado deve ser o mesmo do /data/loggedUser/document/identification. Caso alguma das regras mencionadas não sejam seguidas, o detentor deve rejeitar a solicitação (sincronamente) com o erro DETALHE\_PAGAMENTO\_INVALIDO, e o detalhe deve ser preenchido com a informação referente ao erro.

\[Restrição\] Caso o consentimento de longa duração seja para o produto Pix Automático (“automatic” selecionado no oneOf do objeto “/data/recurringConfiguration”), apenas um recebedor é permitido e esse deve ser pessoa jurídica.

Objeto contendo os dados do recebedor (creditor).

\*\*Regras para Transferências inteligentes:\*\*

1.  Para clientes pessoa física/natural:
    

-   Deve aceitar apenas um item no array; e;
    
-   O CPF informado deve ser o mesmo do \`/data/loggedUser/document/identification\`.
    

2.  Para clientes pessoa jurídica:
    

-   Não há limite para quantidade de itens no array; e;
    
-   O(s) CNPJ informado deve possuir a mesma raiz do CNPJ enviado no campo \`/data/businessEntity/document/identification\`.
    

\*\*Regras para Pix Automático:\*\*

-   Apenas um item é permitido no array; e;
    
-   O documento informado deve ser de um recebedor pessoa jurídica.
    

patch/responses/200/data/debtorAccount

Alterado - "description"

Alteração

Objeto que contém a identificação da conta de origem do pagador. As informações quanto à conta de origem do pagador poderão ser trazidas no consentimento para a detentora, caso a iniciadora tenha coletado essas informações do cliente.  
Do contrário, será coletada na detentora e trazida para a iniciadora como resposta à criação do pagamento.

\[Restrições\]

-   Objeto obrigatório que deverá ser retornado quando o consentimento estiver ou passar pelo status AUTHORISED;
    

Objeto que contém a identificação da conta de origem do pagador.

-   Caso a ITP tenha coletado as informações de conta do usuário pagador, essas poderão ser enviadas no consentimento para a detentora neste objeto, ou;
    
-   Se não coletado pelo ITP, o usuário pagador precisará definir durante a autorização do consentimento.
    
-   Mesmo se enviado pela ITP, o usuário pagador pode alterar durante a autorização do consentimento.
    

\[Restrições\]

-   Objeto obrigatório que deverá ser retornado quando o consentimento estiver ou passar pelo status AUTHORISED;
    

patch/responses/200

Alterado - "description"

Alteração

Objeto contendo as informações de consentimento para a iniciação de pagamento individual.

Objeto contendo as informações de consentimento para iniciação de pagamento automático.

patch/responses/200/data/expirationDateTime

Alterado - "description"

Alteração

Data e hora em que o consentimento deve deixar de ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https://datatracker.ietf.org/doc/html/rfc3339), sempre com a utilização de timezone UTC(UTC time format).

Data e hora em que o consentimento deve deixar de ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https://datatracker.ietf.org/doc/html/rfc3339), sempre com a utilização de timezone UTC (UTC time format).

\[Restrição\] Caso o consentimento seja para Pix Automático ("automatic" selecionado no oneOf "/data/recurringConfiguration/") o horário de expiração do consentimento precisa ser às 23:59:59 (UTC).

patch/responses/422/errors/items/code

Alterado - "description"

Alteração

-   PAGAMENTO\_NAO\_PERMITE\_CANCELAMENTO: Pagamento está com um status que não permite cancelamento
    
-   CANCELAMENTO\_FORA\_PERIODO\_PERMITIDO: O usuário solicitou o cancelamento fora da janela de tempo permitido.
    

-   PAGAMENTO\_NAO\_PERMITE\_CANCELAMENTO: Pagamento está com um status que não permite cancelamento.
    
-   CANCELAMENTO\_FORA\_PERIODO\_PERMITIDO: O usuário solicitou o cancelamento fora da janela de tempo permitido.
    
-   PARAMETRO\_INVALIDO: Os parâmetros informados não obedecem a formatação especificada.
    
-   PARAMETRO\_NAO\_INFORMADO: Algum ou todos os campos obrigatórios não foram informados.
    

patch/responses/422/errors/items/code/enum

Adicionado - "PARAMETRO\_INVALIDO"

Adição

enum

patch/responses/422/errors/items/code/enum

Adicionado - "PARAMETRO\_NAO\_INFORMADO"

Adição

enum

patch/responses/422/errors/items/detail

Alterado - "description"

Alteração

-   PAGAMENTO\_NAO\_PERMITE\_CANCELAMENTO: Pagamento está com um status que não permite cancelamento
    
-   CANCELAMENTO\_FORA\_PERIODO\_PERMITIDO: O usuário solicitou o cancelamento fora da janela de tempo permitido.
    

-   PAGAMENTO\_NAO\_PERMITE\_CANCELAMENTO: Pagamento está com um status que não permite cancelamento.
    
-   CANCELAMENTO\_FORA\_PERIODO\_PERMITIDO: O usuário solicitou o cancelamento fora da janela de tempo permitido.
    
-   PARAMETRO\_INVALIDO: Os parâmetros informados não obedecem a formatação especificada.
    
-   PARAMETRO\_NAO\_INFORMADO: Algum ou todos os campos obrigatórios não foram informados.
    

patch/responses/422/errors/items/title

Alterado - "description"

Alteração

-   PAGAMENTO\_NAO\_PERMITE\_CANCELAMENTO: Pagamento está com um status que não permite cancelamento
    
-   CANCELAMENTO\_FORA\_PERIODO\_PERMITIDO: O usuário solicitou o cancelamento fora da janela de tempo permitido.
    

-   PAGAMENTO\_NAO\_PERMITE\_CANCELAMENTO: Pagamento está com um status que não permite cancelamento.
    
-   CANCELAMENTO\_FORA\_PERIODO\_PERMITIDO: O usuário solicitou o cancelamento fora da janela de tempo permitido.
    
-   PARAMETRO\_INVALIDO: Os parâmetros informados não obedecem a formatação especificada.
    
-   PARAMETRO\_NAO\_INFORMADO: Algum ou todos os campos obrigatórios não foram informados.
