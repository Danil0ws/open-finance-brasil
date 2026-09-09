# Recomendação Uso de Polling e Controle de Acesso - v3.1.0 - [SV] Pagamentos

:warning:atlassian-warning#FFF0B3

O conteúdo criado nessa página deve ser utilizado pelas instituições que forem participar do desenvolvimento do piloto da jornada sem redirecionamento. Caso a instituição não tenha se voluntariado a participar seguir com a implementação da versão 3.0.0.

A consulta via GET, para verificar o processamento da transação, pode ser efetuada a qualquer momento desde que se respeite os limites da seção "Requisitos não Funcionais". Como sugestão, é indicado que a instituição iniciadora do pagamento implemente um retry exponencial.

### Controle de acesso

O endpoint de consulta de pagamento GET /pix/payments/{​​​paymentId}​​​ deve apenas suportar acesso a partir de access\_token emitido por meio de um _grant\_type_ do tipo `client credentials`, como opção do uso do token vinculado ao consentimento (hybrid flow). Para evitar vazamento de informação, a detentora deve validar que o pagamento consultado pertence ao `client_id` que o criou e, caso haja divergências, retorne um erro HTTP 400.
