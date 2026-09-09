# Recomendação Uso de Polling e Controle de Acesso - v2.0.0-beta.1 - [SV] Pagamentos Automáticos

A consulta via GET, para verificar o processamento da transação, pode ser efetuada a qualquer momento desde que se respeite os limites da seção "Requisitos não Funcionais". Como sugestão, é indicado que a instituição iniciadora do pagamento implemente um retry exponencial.

### Controle de acesso

O endpoint de consulta de pagamento `GET /pix/recurring-payments/{recurringPaymentId}` deve apenas suportar acesso a partir de `access_token` emitido por meio de um `grant_type` do tipo `client credentials`, como opção do uso do token vinculado ao consentimento (hybrid flow). Para evitar vazamento de informação, a detentora deve validar que o pagamento consultado pertence ao `client_id` que o criou e, caso haja divergências, retorne um erro HTTP 400.
