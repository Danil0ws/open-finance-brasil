# DCR

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/PT/Automatica/DCR](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/PT/Automatica/DCR)
**Slug:** `FVP/PT/Automatica/DCR`

---

---
title: Testes de DCR
---

[← FVP Automática](FVP/PT/Automatica)

# FVP Automática - Testes de DCR

Esta categoria reúne os módulos que validam o Dynamic Client Registration, ou seja, o registro, a atualização e a remoção de clientes no servidor de autorização do participante. A lista abaixo descreve cada módulo e o que ele verifica.

## Módulos e o que esperar
| Módulo de teste | O que verifica |
| --- | --- |
| dcr_api_fvp-fapi1-advanced-final-brazil-dcr-no-authorization-flow_happy-flow_test-module | Fluxo feliz do DCR sem interação do navegador: obtém o software statement no Diretório e registra um novo cliente no servidor de autorização. |
| dcr_api_fvp-fapi1-advanced-final-brazil-dcr-no-authorization-flow_happy-flow-1_test-module | Executa o DCR com os membros de 'grant_types' em ordem diferente do fluxo feliz padrão e incluindo o parâmetro opcional 'scope'; o registro deve ser aceito. |
| dcr_api_fvp-fapi1-advanced-final-brazil-dcr-no-authorization-flow_happy-flow-2_test-module | Executa o DCR com os membros da string 'scope' em ordem diferente da outra variante de fluxo feliz; o registro deve ser aceito. |
| dcr_api_fvp-fapi1-advanced-final-brazil-dcr-no-authorization-flow_client-delete_test-module | Registra um cliente e verifica o comportamento das operações GET e DELETE após a exclusão do cliente. |
| dcr_api_fvp-fapi1-advanced-final-brazil-dcr-no-authorization-flow_invalid-registration-accesstoken_test-module | Registra um cliente e verifica o comportamento das operações GET e DELETE quando um access token inválido é usado. |
| dcr_api_fvp-fapi1-advanced-final-brazil-dcr-no-authorization-flow_invalid-ss-signature_test-module | Executa o DCR com um software statement de assinatura inválida; o servidor deve rejeitar a tentativa de registro. |
| dcr_api_fvp-fapi1-advanced-final-brazil-dcr-no-authorization-flow_no-software-statement_test-module | Executa o DCR sem incluir o software statement (seus valores vão no corpo da requisição); o servidor deve rejeitar o registro. |
| dcr_api_fvp-fapi1-advanced-final-brazil-dcr-no-authorization-flow_no-mtls_test-module | Executa o DCR sem apresentar certificado TLS de cliente; o servidor deve rejeitar o registro e também as chamadas GET e DELETE feitas sem certificado. |
| dcr_api_fvp-fapi1-advanced-final-brazil-dcr-no-authorization-flow_bad-mtls_test-module | Executa o DCR apresentando um certificado TLS de cliente não confiável; o servidor deve rejeitar o registro e também as chamadas GET e DELETE feitas com o certificado inválido. |
| dcr_api_fvp-fapi1-advanced-final-brazil-dcr-no-authorization-flow_client-config_test-module | Registra um cliente e altera a redirect uri via PUT RFC7592 (ambas presentes no software statement), que deve ser aceito; PUTs com autenticação inválida devem ser rejeitados e a redirect uri não pode mudar. |
| dcr_api_fvp-fapi1-advanced-final-brazil-dcr-no-authorization-flow_client_config-bad-jwks-uri_test-module | Registra um cliente e tenta alterar o jwks_uri para um valor inválido via PUT; o servidor deve retornar o erro 'invalid_client_metadata'. |
| dcr_api_fvp-fapi1-advanced-final-brazil-dcr-no-authorization-flow_client-config-invalid-jwks-value_test-module | Registra um cliente e tenta adicionar um jwks por valor via PUT; o servidor deve retornar o erro 'invalid_client_metadata'. |
| dcr_api_fvp-fapi1-advanced-final-brazil-dcr-no-authorization-flow_client-config-invalid-redirect-uri_test-module | Registra um cliente e tenta adicionar via PUT uma redirect uri ausente no software statement; o servidor deve retornar o erro 'invalid_client_metadata'. |
| dcr_api_fvp-fapi1-advanced-final-brazil-dcr-no-authorization-flow_no-redirect-uri_test-module | Executa o DCR sem incluir a redirect uri no corpo da requisição; o servidor deve rejeitar o registro. |
| dcr_api_fvp-fapi1-advanced-final-brazil-dcr-no-authorization-flow_invalid-redirect-uri_test-module | Executa o DCR solicitando uma redirect uri ausente no software statement; o servidor deve rejeitar o registro. |
| dcr_api_fvp-fapi1-advanced-final-brazil-dcr-no-authorization-flow_invalid-jwks-uri_test-module | Executa o DCR solicitando um jwks uri não hospedado no Diretório do Open Finance Brasil; o servidor deve rejeitar o registro. |
| dcr_api_fvp-fapi1-advanced-final-brazil-dcr-no-authorization-flow_invalid-jwks-value_test-module | Executa o DCR passando um jwks por valor; o servidor deve rejeitar o registro. |
| dcr_api_fvp-unhappy-tls-client-auth_test_module | Tenta registrar um cliente com 'token_endpoint_auth_method':'tls_client_auth'; o servidor deve rejeitar com HTTP 400 (ou, se retornar 201, ter ajustado o método para 'private_key_jwt' conforme a RFC 7591). |
| dcr_api_fvp-sandbox-credentials_test-module | Confirma que credenciais do Sandbox são rejeitadas no DCR: o servidor não deve aceitar o registro (201) com certificados de outro ambiente. |
| dcr_api_fvp-no-subject-type_test-module | Registra um cliente e faz um PUT RFC7592 sem os campos opcionais subject_type e sector_identifier_uri, que deve ser aceito. |
| dcr_api_fvp-multiple-clients_test-module | Verifica que o servidor não permite dois clientes com as mesmas credenciais: o primeiro DCR retorna 201 e o segundo, 400. |
| dcr_api_fvp-revoked-certificate_test-module | Executa o fluxo de DCR apresentando um certificado revogado. O servidor deve recusar o registro e responder 400. |

[Baixar a planilha desta categoria](uploads/e4af4028e10a68181c365f691f8819e9/FVP-DCR-tests.xlsx)

---

[↑ FVP Automática](FVP/PT/Automatica) · [◀ FVP Automática](FVP/PT/Automatica) · [Testes de Diretório ▶](FVP/PT/Automatica/Diretorio)


---

*Conteúdo baixado em 16/09/2026, 15:37:51*
