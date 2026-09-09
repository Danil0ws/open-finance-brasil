# MQD Troubleshooting - MQD

Este documento lista os problemas mais comuns encontrados durante a instalação e operação do MQD, com orientações para diagnóstico e resolução.

* * *

# Problemas na Requisição

#### Erro: "serverOrgId: Not found or bad format."

**Sintoma:** Resposta HTTP 400 ao enviar request ao `/ValidateResponse`.

**Causa:** O header `serverOrgId` não foi enviado ou não está em formato UUID v4 válido.

**Solução:**

-   Verifique se o header está presente na requisição
    
-   O formato deve ser UUID v4: `xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx`
    
-   O valor deve ser um Organisation ID válido no Diretório Central
    

* * *

#### Erro: "endpointName: Not found or bad format."

**Sintoma:** Resposta HTTP 400 ao enviar request ao `/ValidateResponse`.

**Causa:** O header `endpointName` está ausente ou com formato incorreto.

**Solução:**

-   Consulte a Tabela de endpoints validados pelo MQD
    
-   O endpoint deve ser informado sem query parameters
    
-   Path parameters devem ser genéricos: `/accounts/v2/accounts/{accountId}`
    
-   Não incluir a base URL, apenas o path relativo
    

* * *

#### Erro: "endpointName: Unsupported endpoint."

**Sintoma:** Resposta HTTP 400 indicando que o endpoint não é suportado.

**Causa:** O endpoint informado não faz parte da lista de endpoints validados pelo MQD na versão de configuração atual.

**Solução:**

-   Verifique a lista de endpoints suportados na documentação
    
-   Se for um endpoint novo, pode ser necessário aguardar a atualização da configuração no servidor central
    
-   Use o header `versionHeader` se estiver em período de convivência
    

* * *

# Problemas de Performance

#### Container com alto consumo de memória

**Sintoma:** O container MQD atinge o limite de memória configurado e é reiniciado (OOMKilled) ou fica lento.

**Causa:** Volume alto de mensagens sendo processadas na fila interna, ou muitas validações de schemas complexos (ex: investimentos, seguros) sendo processadas simultaneamente.

**Solução:**

-   Aumente os recursos de memória no `docker-compose.yaml`:
    
    true
-   Considere escalar horizontalmente (múltiplas instâncias)
    
-   Monitore o volume de requisições e ajuste a infraestrutura proporcionalmente
    
-   Evite acumular requisições em lote — envie ao MQD em tempo real
    

* * *

#### Container com alto consumo de CPU

**Sintoma:** CPU constantemente acima de 80%.

**Causa:** Volume muito alto de validações simultâneas. A validação de JSON Schema é computacionalmente intensiva para payloads grandes.

**Solução:**

-   Aumente o limite de CPU no `docker-compose.yaml`
    
-   Monitore via `docker stats`
    
-   Verifique se não há um backlog acumulado sendo processado de uma vez
    

* * *

# Problemas de Conectividade

#### Relatórios não estão sendo enviados ao servidor central

**Sintoma:** O MQD processa validações normalmente, mas os relatórios não chegam ao servidor central (sem dados no painel de IQD).

**Causas possíveis:**

1.  Proxy NGINX não configurado corretamente
    
2.  Certificados mTLS expirados ou inválidos
    
3.  Variável `PROXY_URL` apontando para endereço incorreto
    
4.  Firewall bloqueando conexão de saída
    

**Diagnóstico:**

-   Configure `LOGGING_LEVEL=DEBUG` para ver logs detalhados do envio
    
-   Verifique os logs do proxy NGINX: `docker logs <nginx-container>`
    
-   Teste conectividade com o servidor central via curl pelo proxy
    
-   Verifique validade dos certificados em `/etc/ssl/`
    

**Solução:**

-   Corrija a configuração do proxy (`default.prd.conf`, `default.sandbox.conf`)
    
-   Renove certificados expirados
    
-   Verifique regras de firewall para saída HTTPS (porta 443)
    

* * *

**Erro de autenticação (token)**

**Sintoma:** Logs indicam falha ao obter token ou "401 Unauthorized" no envio de relatórios.

**Causa:** Credenciais de autenticação inválidas ou expiradas no Keycloak.

**Solução:**

-   Verifique se o `SERVER_ORG_ID` configurado corresponde a um client válido no Keycloak do ecossistema
    
-   Solicite reconfiguração das credenciais via Portal de Suporte
    

* * *

# Problemas de Validação

#### Validação retornando muitos erros (falsos positivos)

**Sintoma:** O MQD reporta erros de validação em payloads que parecem corretos.

**Causas possíveis:**

1.  A versão do schema no MQD é diferente da versão da API sendo validada
    
2.  A API retornou campos opcionais em formato inesperado
    
3.  Regex incompatível entre a spec e a implementação
    

**Solução:**

-   Use o header `versionHeader` para especificar a versão exata da API
    
-   Verifique se o MQD está atualizado com a última versão disponível
    
-   Em caso de divergência entre a spec e a implementação da API, abra um ticket no canal do Slack informando o endpoint e a evidência
    

* * *

#### Validação não detecta erros conhecidos

**Sintoma:** Payloads com erros evidentes passam pela validação sem serem reportados.

**Causa:** O MQD valida apenas a estrutura (JSON Schema) — não valida regras de negócio ou consistência entre campos.

**Escopo de validação do MQD:**

-   ✅ Tipos de dados (string, number, boolean, array, object)
    
-   ✅ Campos obrigatórios (required)
    
-   ✅ Padrões regex (pattern)
    
-   ✅ Limites de tamanho (maxLength, minLength, minItems, maxItems)
    
-   ✅ Valores permitidos (enum)
    
-   ✅ Propriedades não permitidas (additionalProperties: false)
    
-   ❌ Regras de negócio (ex: data de vencimento > data atual)
    
-   ❌ Consistência entre campos
    
-   ❌ Validação de valores numéricos contra limites de negócio
    

* * *

# Diagnóstico Geral

#### Como ativar logs detalhados

Configure a variável de ambiente `LOGGING_LEVEL`:

wide1800true

Reinicie o container após a alteração. Os logs ficam disponíveis via `docker logs <container-name>`.

* * *

#### Como verificar se o MQD está processando

1.  Envie uma requisição de teste:
    

wide1800true

2.  Resposta esperada: HTTP 200 com body `{}`
    
3.  Se receber 200, o MQD está operacional e enfileirando mensagens
    

* * *

# Problemas de Configuração

#### Configuração não sincroniza (schemas desatualizados)

**Sintoma:** O MQD está validando contra uma versão antiga da API, ou logs indicam erro ao tentar obter `/settings`.

**Causas possíveis:**

1.  Falha de conectividade com o servidor central (mesmas causas de "relatórios não enviados")
    
2.  Token expirado ou inválido
    
3.  Servidor central temporariamente indisponível
    

**Diagnóstico:**

-   Verifique nos logs (DEBUG) se há erro na chamada GET /settings
    
-   Verifique se o token está sendo obtido com sucesso
    
-   O MQD continua operando com a última configuração válida (não para)
    

**Solução:**

-   Corrija a conectividade/certificados (mesmas soluções de envio de relatórios)
    
-   Reinicie o container para forçar uma nova tentativa de sincronização
    
-   A configuração será atualizada automaticamente quando a conectividade retornar
    

* * *

# Suporte

Para dúvidas não cobertas neste documento:

-   **Portal de Suporte:** [https://openfinancebrasil.atlassian.net/servicedesk/customer/portal/1/group/17](https://openfinancebrasil.atlassian.net/servicedesk/customer/portal/1/group/17)
