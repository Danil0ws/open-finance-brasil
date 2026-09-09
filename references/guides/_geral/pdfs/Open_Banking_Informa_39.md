Informe #39 — 13 de agosto de 2021


Os _endpoints_ relacionados ao registro do DCR devem estar protegidos com MTLS e utilizando certificados emitidos pelo ICP Brasil, conforme especificado no documento DCR, seção 6.1.


O certificado EV deve ser usado somente para os serviços que serão utilizados na autorização do
consentimento dos usuários, conforme definido nas especificações de certificados digitais do Open
Banking Brasil, seção 5.2.4.


Orienta-se que as instituições financeiras em não-conformidade com a documentação excluam dos
seus _Authorization Servers_ publicados no diretório **todas as famílias de APIs da Fase 2 até que**
**regularizem sua situação.** Instituições que não consigam se regularizar até segunda-feira (16/08)
devem informar à Estrutura Inicial a previsão de data para regularização, através do e-mail do Secretaria-do (secretariado@openbankingbr.org).


**[SEÇÃO 6.1 - DCR](https://openbanking-brasil.github.io/specs-seguranca/open-banking-brasil-dynamic-client-registration-1_ID1.html#section-6.1)**


**[SEÇÃO 5.2.4 - ESPECIFICAÇÕES DE CERTIFICADOS DIGITAIS](https://openbanking-brasil.github.io/specs-seguranca/open-banking-brasil-certificate-standards-1_ID1.html#section-5.2.4)**


**[ENVIE UM E-MAIL PARA O SECRETRIADO](mailto:Secretariado%20Open%20Banking%20%3csecretariado@openbankingbr.org%3e?subject=Orientacao%20sobre%20Registro%20Dinamico%20de%20Cliente%20(DCR))**


Conforme os padrões de certificado estabelecidos pela ICP Brasil, as ACs têm liberdade para estabelecer a ordem e a inclusão de atributos adicionais no DN do certificado.


Foi detectado que alguns participantes estão utilizando parte das _strings_ do DN contidas dentro do
certificado para fazer o _match_ na autenticação dos certificados de cliente. Este comportamento não
obedece a especificação de padrão de segurança do Open Banking Brasil.


A validação deve seguir a especificação de segurança (Seção 7.1, itens 11 e 12) e a RFC 4514.


**[ESPECIFICAÇÃO DE SEGURANÇA 7.1 - ITENS 11 E 12](https://openbanking-brasil.github.io/specs-seguranca/open-banking-brasil-dynamic-client-registration-1_ID1.html#section-7.1)**


**[LINK DA RFC 4514](https://datatracker.ietf.org/doc/html/rfc4514)**


Durante o go-live, foi identificado que alguns participantes verificam a ordem de elementos dentro
de um objeto do tipo _array_ durante o registro do DCR. Não deve existir validação da orde-nação
dos elementos em nenhum campo do tipo _array_ .


Registros incorretos de _endpoints_ foram detectados no Diretório de Participantes. Alguns exemplos
identificados:


- URL de _well-known_ - há registro de URLs registrados com o valor como ‘’não se aplica”


- Logomarca - há logomarcas como .png ou que não abrem, sendo o correto .svg


- _Endpoints_ (recursos) - há empresas sem _endpoints_ cadastrados


Segundo a Instrução Normativa BCB nº 134, seção 2.8, as instituições participantes devem manter
suas informações cadastrais permanentemente atualizadas no Diretório de Participantes do Open
Banking, observada a regulamentação vigente.


É possível acessar as regras de registro e todas as diretrizes para registro de marca através do
Guia do Diretório.


**[ACESSE O GUIA DO DIRETÓRIO](https://openbanking-brasil.github.io/areadesenvolvedor/#guia-operacional-do-diretorio-central)**


**[ACESSE A IN BCB N° 134](https://www.in.gov.br/en/web/dou/-/instrucao-normativa-bcb-n-134-de-22-de-julho-de-2021-334558536)**


Datas de disponibilização das ferramentas de conformidade para certificação das instituições foram
definidas.


**[ACESSE O CRONOGRAMA DE CERTIFICAÇÃO](https://openbanking-brasil.github.io/areadesenvolvedor/documents/cronograma_certificacao.pdf)**


Conforme Instrução Normativa BCB #133, uma implementação da versão de API do Open Banking
só poderá ser registrada no ambiente produtivo do Diretório caso tenha sido certificada nos testes
de conformidade. Desta forma, as APIs que foram incorretamente publicadas sem que houvesse
homologação funcional prévia serão desabilitadas a partir desta segunda feira 16/08, até que a homologação formal seja realizada com sucesso.


Para cadastrar ou descadastrar um endereço de e-mail para recebimento dos informes com as últimas atualizações do
Open Banking, deve ser enviada requisição para o contato: gt-comunicacao@openbankingbr.org


