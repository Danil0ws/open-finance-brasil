# fluxograma-iniciacao-de-pagamentos

![fluxograma-iniciacao-de-pagamentos](fluxograma-iniciacao-de-pagamentos.png)

## Texto Extraído

5
=

Informa o vinculo de conta que sera utilizado

Solicita o token de acesso

Envia token de acesso

Cria consentimento de pagamento

em estado inicial AWAITING_AUTHORISATION

Consentimento criado

Solicita as opgdes de assinatura FIDO2

Envia as opgées de assinatura FIDO2

Requisita assinatura FIDO2
por meio do challenge

Requisita gesto do usuario para
aprovagao

Realiza o gesto de autenticagao (ex.:

biometria, PIN)

Retorna o resultado positivo da assinatura
FIDO2 e sinais de risco

Envia o resultado assinado do FIDO2
challenge e sinais de risco

Valida as informagoes recebidas,
com o sucesso da operagao altera
o estado do consentimento para
AUTHORISED

Envia token para realizar
pagamento

Solicita a realizagao de pagamento
com token recebido

a erner'vova

Envia confirmagao da
solicitagao do processo de
pagamento que tem como estado

inicial RCVD Executa pagamento
alterando estado para ACSC

Busca informagdes do pagamento executado

Envia mensagem de sucesso
com o estado ACSC

Envia mensagem de sucesso

---
**Arquivo original:** `fluxograma-iniciacao-de-pagamentos.png`
**Tamanho:** 849.04 KB