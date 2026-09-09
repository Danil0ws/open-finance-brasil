# Informações Gerais - API Comum (Discovery) -  v2.0.1

### Contexto:

APIs de Status, de _Outages_ e Métricas são comuns a todos os participantes do Open Finance Brasil, independentemente da fase de adesão.​

Relatórios e Métricas

Situação do Ambiente

Deve dar acesso a dados sobre a disponibilidade atual das implementações das APIs, bem como a dados sobre indisponibilidades programadas.

Métricas

Deve dar acesso a dados de performance de todas as APIs disponibilizadas.

Sendo assim:

1.  Todas as instituições devem publicar essas APIs que monitoram a situação do ambiente;
    
2.  API Comum (Discovery) deve reportar os dados de disponibilidade e indisponibilidade programada de **todas as APIs** que a instituição oferece;
    
3.  API Comum (Discovery) deve ser atualizada conforme lançamento de novas APIs pela instituição ou atualização das APIs já existentes.
    

## GET /discovery/v2/status.

### Visão geral

A instituição deve disponibilizar o código de status de todas as suas APIs nesse endpoint

### Visão de alto nível das estruturas de dados

![comuns - alto nivel.png](images/comuns%20-%20alto%20nivel.png)

### Dicionário de dados

[Fazer download do dicionário de dados](data/references/openapi/dictionary-getStatus_v2.md)

### Exemplo de código

Na estrutura de retorno exemplificada abaixo, o campo "explanation" opcionalmente pode conter os endpoints indisponíveis, além da explicação sobre os motivos:

## GET /discovery/v2/outages.

### Visão geral

A instituição deve disponibilizar previamente a previsão de indisponibilidade agendada dos seus serviços através desse endpoint.

### Visão de alto nível das estruturas de dados

### Dicionário de dados

[Fazer download do dicionário de dados](data/references/openapi/dictionary-getOutage_v2.md)

### Exemplo de código

Na estrutura de retorno exemplificada abaixo, o campo "explanation" opcionalmente pode conter os endpoints indisponíveis, além da explicação sobre os motivos:

", "first": "https://api.banco.com.br/open-banking/channels/v2/", "prev": "https://api.banco.com.br/open-banking/channels/v2/", "next": "https://api.banco.com.br/open-banking/channels/v2/", "last": "https://api.banco.com.br/open-banking/channels/v2/" }, "meta": { "totalRecords": 1, "totalPages": 1 } }\]\]>
