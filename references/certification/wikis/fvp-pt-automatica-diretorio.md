# Diretorio

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/PT/Automatica/Diretorio](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/PT/Automatica/Diretorio)
**Slug:** `FVP/PT/Automatica/Diretorio`

---

---
title: Testes de Diretório
---

[← FVP Automática](FVP/PT/Automatica)

# FVP Automática - Testes de Diretório

Esta categoria reúne os módulos que validam o cadastro do participante no Diretório de Participantes, confirmando que o Authorisation Server e os dados exigidos estão presentes e consistentes. A lista abaixo descreve cada módulo e o que ele verifica.

## Módulos e o que esperar
| Módulo de teste | O que verifica |
| --- | --- |
| directory_api_server-registration_test_module_v2 | Certifica o registro do servidor de autorização no Diretório: certificações de segurança e funcionais, metadados, logo, escopos versus famílias de API e Domain ROLEs. |
| directory_api_server-security-certification_test-module | Certifica que o servidor de autorização tem ao menos uma Certificação de Segurança ativa no Diretório, incluindo a certificação exigida BR-OF Adv. OP w/ Private Key, PAR (FAPI-BR v2), e que a URI da certificação segue a estrutura esperada para a data de início. |
| directory_api_server-functional-certification-uri_test-module | Certifica que, para cada API Resource do servidor com URI de certificação, exceto as famílias de dados abertos da Fase 1, a URI segue a estrutura de submissões funcionais da família e da versão maior declarada, conforme a data de início da certificação. |
| directory_api_server-family-completeness_test-module | Certifica que os endpoints obrigatórios de cada família de API estão registrados, com a flag FamilyComplete não definida como False, aceitando na família accounts apenas a ausência do endpoint opcional /accounts/{accountId}/reserved-balances. |
| directory_api_server-scope-family-coverage_test-module | Verifica que cada escopo suportado no well-known, exceto openid e os escopos obrigatórios, tem a família de API correspondente publicada pelo servidor, reportando todas as falhas juntas. |
| directory_api_server-family-scope-coverage_test-module | Verifica que cada família de API publicada pelo servidor tem o escopo correspondente suportado no well-known, reportando todas as falhas juntas. |
| directory_api_server-mandatory-scopes_test-module | Verifica que, se a organização possui o Domain ROLE DADOS, todos os escopos obrigatórios estão presentes no well-known. |
| directory_api_server-scope-role_test-module | Verifica que, para cada escopo suportado no well-known, a organização possui o Domain ROLE correspondente no Diretório. |
| directory_api_server-presentation-metadata_test-module | Verifica que o servidor foi registrado com metadados válidos, chamando a CustomerFriendlyLogoUri registrada e validando o logo conforme as UX Guidelines. |
| directory_api_certification-status_test-module | Verifica que o status das certificações de cada API Resource está corretamente registrado no Diretório. |

[Baixar a planilha desta categoria](uploads/9e7bba58ac4f2c85a06ba2fe372a651e/FVP-Directory-tests.xlsx)

---

[↑ FVP Automática](FVP/PT/Automatica) · [◀ Testes de DCR](FVP/PT/Automatica/DCR) · [Testes de Produto ▶](FVP/PT/Automatica/Produto)


---

*Conteúdo baixado em 16/09/2026, 15:37:52*
