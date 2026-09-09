# Limites operacionais

É facultado às instituições participantes implementarem um limite de acesso mensal por _endpoint_ e por cliente.

Em _endpoints_ que acessem recursos ou produtos, os limites serão também considerados por recurso ou produto.

A contabilização dos acessos deve ser realizada por:

I. mês

II. endpoint

III. objeto mais granular referenciado na chamada (consentimento/recurso/produto)

IV. cliente (CPF ou CNPJ)

V. instituição consumidora da informação

Por exemplo: uma instituição receptora ‘A’ pode acessar um endpoint ‘B’, acessando o recurso ‘C’, de um cliente “D” da instituição transmissora ‘E’, no mínimo ‘N’ vezes (ou chamadas) com sucesso por mês.

Aplicabilidade dos limites operacionais: todos _endpoints_ das APIs do tipo Dados Cadastrais e Transacionais (conforme classificação de Tipo), destes excetuam-se aqueles _endpoints_ das APIs de Consentimento (_Consents_) e Recursos (_Resources_). As APIs de Segurança, de Dados Abertos e de Serviços (como de Iniciação de Pagamento) não podem ter restrições de limites operacionais.

A implementação dos limites operacionais é opcional pelas instituições transmissoras, mas, uma vez que sejam implementados, devem garantir o consumo mínimo. É facultada à instituição a possibilidade de ampliar esses limites, mas vedada a implementação de limites inferiores aos estabelecidos.

Os valores mínimos de limites operacionais a serem considerados, por _endpoint_, que devem ser iguais ou maiores que os abaixo, de acordo com a classificação de frequência de utilização:

I. 8 chamadas ao mês, para endpoint classificado como de baixa frequência

II. 30 chamadas ao mês, para _endpoint_ classificados como de média frequência

III. 120 chamadas ao mês, para _endpoint_ classificado como de média-alta frequência

IV. 240 chamadas ao mês, para _endpoint_ classificado como de alta frequência

V. 420 chamadas ao mês, para os seguintes _endpoints_ da API de Contas: ‘Saldos da conta’ e ‘Limites da conta’

Só deverão ser contabilizadas nos limites operacionais requisições respondidas com HTTP _Status_ _Code_ 2XX, sendo que as requisições adicionais a um endpoint para fins de paginação não devem ser contabilizadas.

As requisições que excederem os limites operacionais deverão ser respondidas com o HTTP _Status_ _Code_ 423.

Todas as requisições autenticadas em _endpoints_ sujeitos ao limite operacional devem possuir o atributo _x-fapi-interaction-id_ preenchido no seu _header_ pela receptora, que deve ser copiado pela transmissora nos _headers_ da resposta. Essa definição objetiva permitir um adequado rastreamento de divergências que podem ocorrer entre transmissoras e receptoras associadas ao limite operacional.

## Paginação no contexto dos limites operacionais

Para a não contabilização de rechamadas, considerando que eventuais chamadas que possuam paginação devam ser interpretadas como uma única chamada, foi estabelecido a criação de um _query_ _parameter_ adicional para funcionar como identificador de rechamadas.

-   Esse novo parâmetro deve ter o nome _pagination-key_.
    
-   Cabe à Transmissora criar o identificador e enviá-lo via HATEOAS no retorno da chamada.
    
-   O tempo máximo de utilização do identificador pelo Receptor é de 60 minutos.
    
-   A Transmissora deve implementar validações para garantir a coerência da utilização do identificador, de acordo com as regras de limites operacionais.
    
-   Caso a Receptora utilize um _pagination-key_ inválido ou expirado, a Transmissora deverá gerar um novo _pagination-key_ retornando o resultado com sucesso. Esta chamada será contabilizada para os limites operacionais.
    
-   Essa implementação deve ser realizada em todos _endpoints_ atuais com paginação.
    
-   A Transmissora poderá gerar um único ID para controle das chamadas das próximas páginas.
    

![image-20221027-175924.png](images/image-20221027-175924.png)

## Exemplo do uso do pagination-key

**Primeira chamada**

GET /accounts/v2/accounts/12345678/transactions?page=1&page-size=1000

**Próximas chamadas**

GET /accounts/v2/accounts/12345678/transactions?page=2&page-size=1000&pagination-key=123456
