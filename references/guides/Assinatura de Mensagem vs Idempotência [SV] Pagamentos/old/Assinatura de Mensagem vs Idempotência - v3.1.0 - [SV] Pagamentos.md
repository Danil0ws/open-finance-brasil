# Assinatura de Mensagem vs Idempotência - v3.1.0 - [SV] Pagamentos

:warning:atlassian-warning#FFF0B3

O conteúdo criado nessa página deve ser utilizado pelas instituições que forem participar do desenvolvimento do piloto da jornada sem redirecionamento. Caso a instituição não tenha se voluntariado a participar seguir com a implementação da versão 3.0.0.

O claim jti inserido dentro do JWT da assinatura da mensagem tem como objetivo evitar ataques de repetição e não é utilizado para o controle da idempotência. Desta forma ele deverá ser gerado a cada nova requisição realizada às APIs, independentemente desta ser a requisição para a criação de uma nova operação ou ser a requisição para confirmação de execução de uma operação anterior (idempotente).

As validações referentes a assinatura de mensagens devem preceder as validações de idempotência.
