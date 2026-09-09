# MQD - Proxy reverso

Para a versão 2.0 do Motor de Qualidade de Dados (MQD) foi implementada uma camada intermediária encarregada de estabelecer uma conexão segura (mTLS) utilizando os certificados da instituição.

Neste arquivo docker compose, incluímos um exemplo de proxy reverso usando NGINX como tecnologia, mas qualquer ferramenta pode ser usada conforme a conveniência da Instituição.

Será necessário que o proxy tenha a capacidade de rodar em modo "transparente", isso significa que a mensagem a ser enviada ao servidor MQD deve ser a mesma recebida em seus endpoints (cabeçalho e corpo).

Da mesma forma, este proxy terá acesso aos arquivos de certificados (Cert e key) da instituição financeira para permitir o estabelecimento de uma conexão segura com o servidor.

### Endpoints

Endpoint

Path

Proxy - Produção

Proxy - Sandbox

Autenticação

/token

[https://mqd.openfinancebrasil.org.br/token](https://mqd.openfinancebrasil.org.br/token)

[https://mqd.sandbox.openfinancebrasil.org.br/token](https://mqd.sandbox.openfinancebrasil.org.br/token)

Envio de Relatório

/report

[https://mqd.openfinancebrasil.org.br/report](https://mqd.openfinancebrasil.org.br/report)

[https://mqd.sandbox.openfinancebrasil.org.br/report](https://mqd.sandbox.openfinancebrasil.org.br/report)

Configuração

/settings

[https://mqd.openfinancebrasil.org.br/settings](https://mqd.openfinancebrasil.org.br/settings)

[https://mqd.sandbox.openfinancebrasil.org.br/settings](https://mqd.sandbox.openfinancebrasil.org.br/settings)

### Requisitos do Proxy

-   Suportar conexão mTLS com certificados ICP-Brasil
    
-   Modo transparente (não alterar headers nem body)
    
-   Acesso aos arquivos de certificado (.crt e .key) da instituição
    
-   Capacidade de rotear para diferentes paths no servidor MQD
    

### Configuração de Exemplo (NGINX)

Os arquivos de configuração de exemplo estão disponíveis no repositório:

-   **Produção:** `infra/dockerfile/proxy/default.prd.conf`
    
-   **Sandbox:** `infra/dockerfile/proxy/default.sandbox.conf`
    
-   **Desenvolvimento:** `infra/dockerfile/proxy/default.dev.conf`
    

Repositório: [https://github.com/OpenBanking-Brasil/mqd-client](https://github.com/OpenBanking-Brasil/mqd-client)
