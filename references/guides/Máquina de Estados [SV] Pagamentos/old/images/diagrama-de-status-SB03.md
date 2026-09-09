# diagrama-de-status-SB03

![diagrama-de-status-SB03](diagrama-de-status-SB03.png)

## Texto Extraído

Autorizagao negada

por um dos
autorizadores
na detentora
ou pagamento

cancelado
pelo pagador
na iniciadora

Analise aprovada e
ha mais clientes
Pagamento retido autorizadores
para analise apos
todas as aprovacées

PATC

(PartiallyAcceptedTechnicalCorrect)
Requisigao OK,
aguardando autorizagao multipla

Autorizagao negada por
tempo de autorizagao expirado
ou a transagao foi rejeitada
pela detentora

Pagamento rejeitado
pela detentora
de forma assincrona

POST /pix/payments
(retorno 201)

RCVD

(Received)
Requisigaéo Recebida

Transagao requer
multipla autorizagao

Validagao da requisigao
e da conta de débito

Transagao autorizada
por todos
os autorizadores
e todas as analises
realizadas

ACCP

(AcceptedCustomerProfile)
Pagamento pronto para ser
enviado para liquidagao

Envio do Pix para liquidagao
(interna ou via SPI)

CANC
(Cancelled)
Transagao
Cancelada

N
Pagamento

Pagamento retido
para analise

apos primeira aprovagao

ou aprovagao unica

Pagamento liberado
pela detentora apos
analise da transagao

Rejeitado pela detentora
no momento em que iria
enviar o pix para liquidagao

pelo pagador

cancelado

PDNG
(Pending)

Transagao
Pendente

Pagamento rejeitado
pela detentora
apos analise
da transagao

RJCT

(Rejected)
Transagao
Rejeitada

Pagamento
——— cancelado
pelo pagador

SCHD
(Scheduled)

Pix agendado com sucesso

ACPD

(AcceptedClearingProcessed)

Pix enviado para liquidacao Pix rejeitado durante liquidagao

(interna ou no SPI)

Liquidagao do Pix
(interna ou no SPI)

ACSC

(AcceptedSettlementCompletedDebtorAccount)
Pix liquidado

“@)

---
**Arquivo original:** `diagrama-de-status-SB03.png`
**Tamanho:** 382.97 KB