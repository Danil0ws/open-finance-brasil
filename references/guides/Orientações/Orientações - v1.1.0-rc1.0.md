# Orientações - v1.1.0-rc1.0

## **Agendamento de Pagamento**

-   **Mecanismo de retentativas de liquidação de pagamentos agendados**
    

No momento de liquidação de pagamento agendado é possível ter falhas sistêmicas ou violações de regras de negócio. Como por exemplo, ausência de saldo na conta do pagador para realizar a liquidação. Neste contexto é interessante às detentoras de conta a adoção de políticas de retentativas de liquidação.

O arranjo PIX não define nada a respeito deste tema, por consequência, o Open Finance deixa livre para cada detentora adote a política de retentativa que mais fizer sentido para ela.

-   **Revogação do consentimento**
    

Com a inclusão da funcionalidade de agendamento do pagamento é interessante facultar às partes envolvidas na transação a possibilidade de cancelamento do mesmo, desde que até um dia antes da sua liquidação. Esse mecanismo será oferecido a partir da revogação de consentimentos para pagamentos agendados.

Considerando a diretriz do controle do agendamento pela detentora de conta e as necessidades dos envolvidos na transação é possível os seguintes cenários de jornadas de revogação:

1.  **Revogação pelo usuário na iniciadora** através da área de gestão de pagamentos do Open Finance (Consulte o guia de UX do Open Finance para maiores detalhes);
    
2.  **Revogação pelo usuário na detentora** através da área de gestão de pagamentos do open Finance (Consulte o guia de UX do Open Finance para maiores detalhes);
    
3.  **Revogação pelo usuário na detentora** através da área de gestão do PIX (Consulte o guia de UX do arranjo PIX para maiores detalhes);
    
4.  **Revogação pela iniciadora** sem a presença do usuário;
    
5.  **Revogação pela detentora** sem a presença do usuário.
    

-   **Regras funcionais**
    
    -   **Código: RN001**
        
    -   **Descrição**: Ao revogar um consentimento o pagamento associado deverá ir para o status **RJCT** e campo **rejectionReason** deverá ter o valor **CONSENT\_REVOKED**.
        
    -   **Endpoint**: [Revogar consentimento](https://openbankingbrasil.atlassian.net/wiki/spaces/DraftOF/pages/48726154/Informa+es+Gerais+-+Pagamentos+-+v1.1.0-rc1.0#Revogar-consentimento-de-pagamento:-\(PATCH-/payments/v1/consents/{consentId}\))
        

**Post/Consents**

-   **Exemplo - PIX normal**
    

{  
"alg": "PS256",  
"typ": "JWT",  
"kid": "PWAi5ruQcHfzPzq2JFdpY7nAUh6LzTTQtDBUpOM37JQ"  
}  
{  
"aud": "3449bf21-0b07-48e6-b6fc-13eb161a9901",  
"iss": "ca1b98e1-97a2-43db-947f-8a08054c342e",  
"jti": "a2fd393c-107a-4ad4-be22-3cfeeea90efe",  
"iat": 1628257737",  
"data": {  
"consentId": "urn:bancoex:C1DD33123",  
"creationDateTime": "2021-05-21T08:30:00Z",  
"expirationDateTime": "2021-05-21T08:30:00Z",  
"statusUpdateDateTime": "2021-05-21T08:30:00Z",  
"status": "AWAITING\_AUTHORISATION",  
"loggedUser": {  
"document": {  
"identification": "11111111111",  
"rel": "CPF"  
}  
},  
"businessEntity": {,  
"document": {  
"identification": "11111111111111",  
"rel": "CNPJ",  
}  
},  
"creditor": {  
"personType": "PESSOA\_NATURAL",  
"cpfCnpj": "58764789000137",  
"name": "Marco Antonio de Brito"  
},  
"payment": {  
"type": "PIX",  
"date": "2021-01-01",  
"currency": "BRL",  
"amount": "100000.12",  
"ibgeTownCode": "5300108",  
"details": {  
"localInstrument": "DICT",  
"qrCode": "00020104141234567890123426660014BR.GOV.BCB.PIX014466756C616E6F32303139406578616D706C652E636F6  
D27300012\\nBR.COM.OUTRO011001234567895204000053039865406123.455802BR5915NOMEDORECEBEDOR6008  
BRASILIA61087007490062\\n530515RP12345678-201950300017BR.GOV.BCB.BRCODE01051.0.08045  
0014BR.GOV.BCB.PIX0123PADRAO.URL.PIX/0123AB\\nCD81390012BR.COM.OUTRO01190123.ABC  
D.3456.WXYZ6304EB76\\n",  
"proxy": "12345678901",  
"creditorAccount": {  
"ispb": "12345678",  
"issuer": "1774",  
"number": "1234567890",  
"accountType": "CACC",  
}  
}  
},  
"debtorAccount": {  
"ispb": "12345678",  
"issuer": "1774",  
"number": "1234567890",  
"accountType": "CACC",  
}  
},  
"links": {  
"self": "[https://api.banco.com.br/open-banking/payments/v1/consents](https://api.banco.com.br/open-banking/payments/v1/consents)",  
},  
"meta": {  
"totalRecords": 1,  
"totalPages": 1,  
"requestDateTime": "2021-05-21T08:30:00Z",  
}  
}

-   **Exemplo - PIX agendado**
    

{  
"alg": "PS256",  
"typ": "JWT",  
"kid": "PWAi5ruQcHfzPzq2JFdpY7nAUh6LzTTQtDBUpOM37JQ"  
}  
{  
"aud": "3449bf21-0b07-48e6-b6fc-13eb161a9901",  
"iss": "ca1b98e1-97a2-43db-947f-8a08054c342e",  
"jti": "a2fd393c-107a-4ad4-be22-3cfeeea90efe",  
"iat": 1628257737",  
"data": {  
"consentId": "urn:bancoex:C1DD33123",  
"creationDateTime": "2021-05-21T08:30:00Z",  
"expirationDateTime": "2021-05-21T08:30:00Z",  
"statusUpdateDateTime": "2021-05-21T08:30:00Z",  
"status": "AWAITING\_AUTHORISATION",  
"loggedUser": {  
"document": {  
"identification": "11111111111",  
"rel": "CPF"  
}  
},  
"businessEntity": {,  
"document": {  
"identification": "11111111111111",  
"rel": "CNPJ",  
}  
},  
"creditor": {  
"personType": "PESSOA\_NATURAL",  
"cpfCnpj": "58764789000137",  
"name": "Marco Antonio de Brito"  
},  
"payment": {  
"type": "PIX",  
"schedule": {  
"single": {  
"date": "2021-01-01"  
}  
},  
"currency": "BRL",  
"amount": "100000.12",  
"ibgeTownCode": "5300108",  
"details": {  
"localInstrument": "DICT",  
"qrCode": "00020104141234567890123426660014BR.GOV.BCB.PIX014466756C616E6F32303139406578616D706C652E636F6  
D27300012\\nBR.COM.OUTRO011001234567895204000053039865406123.455802BR5915NOMEDORECEBEDOR6008  
BRASILIA61087007490062\\n530515RP12345678-201950300017BR.GOV.BCB.BRCODE01051.0.08045  
0014BR.GOV.BCB.PIX0123PADRAO.URL.PIX/0123AB\\nCD81390012BR.COM.OUTRO01190123.AB  
CD.3456.WXYZ6304EB76\\n",  
"proxy": "12345678901",  
"creditorAccount": {  
"ispb": "12345678",  
"issuer": "1774",  
"number": "1234567890",  
"accountType": "CACC",  
}  
}  
},  
"debtorAccount": {  
"ispb": "12345678",  
"issuer": "1774",  
"number": "1234567890",  
"accountType": "CACC",  
}  
},  
"links": {  
"self": "[https://api.banco.com.br/open-banking/payments/v1/consents](https://api.banco.com.br/open-banking/payments/v1/consents)",  
},  
"meta": {  
"totalRecords": 1,  
"totalPages": 1,  
"requestDateTime": "2021-05-21T08:30:00Z",  
}  
}
