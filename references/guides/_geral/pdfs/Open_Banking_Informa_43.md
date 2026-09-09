Informe #43 — 20 de agosto de 2021


Informamos que o formato do campo _tls_client_auth_subject_dn_ dos certificados de cliente deve
ser o “nome curto”, conforme padrão DCR Brasil e em conformidade com a RFC 4514 e com o documento Padrão de Certificados Open Banking Brasil (vide exemplos abaixo).


As instituições receptoras e as transmissoras que optaram pelo uso de _tls_client_auth_ (FAPI 1.0
parte 2 - _advanced_, seção 5.2.2, item 14), com suporte apenas a “nome longo”, precisam realizar
as adequações para suportar o “nome curto” o quanto antes, pois instituições que não tiverem implementado desta forma correm risco de não conseguirem se comunicar com as demais instituições.


Seguem abaixo exemplos de DN usando “nome curto” para certificados utilizados no Open Banking
Brasil:


Em resposta a questionamentos anteriores de algumas instituições, esclarecemos que, conforme
especificado no item 14 da seção 5.2.2 do FAPI 1.0 parte 2 ( _advanced_ ), cabe à detentora de conta decidir se deseja implementar _tls_client_auth_ ou _private_key_jwt_, com ou sem PAR
( _pushed authorisation request_ ).


Cabe ao iniciador decidir qual método ele irá utilizar em detrimento ao parceiro com o qual irá se
comunicar.


Os métodos suportados por cada instituição estão publicados em seus respectivos documentos
de _well-known_ e também publicados no site da OpenID Foundation, na área de certificados no padrão FAPI Brasil


**[SITE DE CERTIFICADOS PADRÃO FAPI](https://openid.net/certification/#FAPI)**


Para cadastrar ou descadastrar um endereço de e-mail para recebimento dos informes com as últimas atualizações do
Open Banking, deve ser enviada requisição para o contato: gt-comunicacao@openbankingbr.org


