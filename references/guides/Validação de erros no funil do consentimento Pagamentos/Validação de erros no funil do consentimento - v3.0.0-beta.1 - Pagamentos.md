# Validação de erros no funil do consentimento - v3.0.0-beta.1 - Pagamentos

Na tabela abaixo, é possível observar quais são os possíveis retornos do campo rejectionReason podem ser enviados em cada etapa envolvida com o consentimento, no fluxo de pagamentos:

**Etapas do funil do consentimento**

**Code**

(5) Início da autenticação

FALHA\_INFRAESTRUTURA  
TEMPO\_EXPIRADO\_AUTORIZAÇAO

(6) Conclusão da autenticação

FALHA\_INFRAESTRUTURA  
TEMPO\_EXPIRADO\_AUTORIZAÇAO  
REJEITADO\_USUARIO

(7) Autorização do cliente

FALHA\_INFRAESTRUTURA  
CONTAS\_ORIGEM\_DESTINO\_IGUAIS  
CONTA\_SALARIO  
SALDO\_INSUFICIENTE  
VALOR\_ACIMA\_LIMITE  
QRCODE\_INVALIDO

(8) _Authorisation code_ emitido

FALHA\_INFRAESTRUTURA  
TEMPO\_EXPIRADO\_CONSUMO
