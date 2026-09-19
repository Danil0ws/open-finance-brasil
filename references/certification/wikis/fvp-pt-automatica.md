# Automatica

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/PT/Automatica](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/PT/Automatica)
**Slug:** `FVP/PT/Automatica`

---

---
title: FVP Automática
---

[← FVP](FVP/PT)

# FVP Automática

A FVP Automática é executada diariamente contra todos os Authorization Servers cadastrados no Diretório, com início às 04:00 Z, e cobre as verificações que não dependem da jornada do usuário, como o registro dinâmico de cliente (DCR), a conformidade FAPI, os testes funcionais e o cadastro no Diretório. Ou seja, ela é composta por módulos de testes que não chegam à etapa de redirecionamento. Quando um servidor falha em uma verificação, é aberto um chamado no Service Desk do participante. Os módulos estão organizados nas três categorias apresentadas abaixo:

## Categorias
- [Testes de DCR](FVP/PT/Automatica/DCR)
- [Testes de Diretório](FVP/PT/Automatica/Diretorio)
- [Testes de Produto](FVP/PT/Automatica/Produto)

## Planilha
[Baixar a planilha com todos os módulos automáticos](uploads/486703dbffe6f5f8418cb0693efeb399/FVP-Automatic-tests.xlsx)

## Histórico de alterações

<details>
<summary>2026 - 12 alterações</summary>

**21/08 · Planos** - Pagamentos v4 deixou de ser executado na FVP Automática

Os dez cenários de pagamentos que rodavam em duplicidade, uma vez na versão 4 e uma vez na versão 5, passaram a rodar apenas na versão 5: consentimento com usuário mal logado, datas de agendamento, limite de consentimento de recorrência, quantidade personalizada divergente, DICT, MANU, QRES, verificação de assinatura, consentimento negativo e JWT no cabeçalho accept. A cobertura não mudou, o que saiu foi a repetição na versão 4.

**13/08 · Planos** - Módulo de token inválido da portabilidade de crédito renomeado

O módulo de token inválido da portabilidade de crédito passou a se chamar fvp_credit-portability_api_invalid_token_test-module_v1. O nome anterior terminava em v3-3 e não correspondia à versão da API que o módulo testa.

**03/08 · Planos** - Oito novas verificações do Diretório na FVP Automática

O plano automático passou a executar oito módulos de Diretório, cada um verificando um ponto que antes não era reportado em separado: completude da família de APIs, cobertura entre escopos e famílias nos dois sentidos, URI de certificação funcional, escopos obrigatórios, metadados de apresentação, papel do escopo e certificação de segurança. O resultado deixa de ser um único módulo aprovado ou reprovado e passa a apontar qual verificação falhou.

**29/07 · Comportamento** - Jornada Otimizada ignorada quando não há endpoint de consentimentos

O módulo de permissões inválidas da Jornada Otimizada é ignorado quando a detentora não publica o endpoint de consentimentos de dados.

**22/07 · Comportamento** - Portabilidade de crédito ignorada quando a detentora não oferece o produto

O módulo de token inválido da portabilidade de crédito é ignorado antes do registro dinâmico quando a detentora não tem o endpoint de portabilidade registrado.

**13/07 · Documentação** - Documentação da FVP reformulada

A documentação da FVP foi reorganizada em páginas por plano, em português e inglês, com uma planilha por plano.

**11/06 · Planos** - Módulos de pagamentos v5 na FVP Automática

Onze módulos de pagamentos v5 passaram a compor o plano automático, ao lado dos equivalentes em v4: consentimento negativo, DICT, MANU, QRES, datas de agendamento, limites de pagamento recorrente, assinatura incorreta, cabeçalho de aceite JSON/JWT, validação de finalidade do consentimento e usuário logado incorreto. No mesmo dia, o módulo de usuário logado incorreto de pagamentos automáticos v1 foi retirado do plano.

**18/05 · Planos** - Jornada Otimizada na FVP Automática

Incluído o fvp-optimised-journey_invalid-permissions_test-module-v1, que verifica a recusa de um consentimento de jornada otimizada criado com combinação de permissões incorreta.

**07/04 · Planos** - Remoção de módulos duplicados de pagamentos automáticos

Três módulos de pagamentos automáticos v1 que estavam duplicados no plano foram removidos, mantendo apenas as versões correntes.

**19/02 · Planos** - Pagamentos automáticos atualizados para a versão 2.2

A família de módulos de pagamentos automáticos passou para a versão 2.2, substituindo a anterior: credor inválido em Pix Automático, parâmetros inválidos, consentimento negativo, consentimentos negativos, consentimento rejeitado e credor inválido em sweeping.

**05/02 · Planos** - Enrollments com parâmetros inválidos na versão 2.2

Incluído o fvp-enrollments_api_invalid-parameters_test-module_v2-2, que verifica a recusa de uma inscrição com cabeçalho, assinatura ou campos inválidos.

**14/01 · Planos** - Portabilidade de Crédito na FVP Automática

Incluído o fvp_credit-portability_api_invalid_token_test-module_v3-3, que verifica se o endpoint de portabilidades responde no Diretório e recusa um token de client_credentials.

</details>

<details>
<summary>2025 - 3 alterações</summary>

**22/05 · Planos** - Módulos de enrollments com parâmetros inválidos atualizados

Os módulos de parâmetros inválidos de enrollments v1 e v2 foram atualizados e renomeados, sem mudança no que é verificado.

**27/03 · Planos** - Pagamentos automáticos v2.0.0-rc.1

Seis módulos de pagamentos automáticos v2.0.0-rc.1 entraram no plano, cobrindo credor inválido e parâmetros inválidos em Pix Automático, consentimento negativo e rejeitado, e credor inválido em sweeping.

**26/02 · Planos** - Consentimentos atualizados para a versão 3.2

Os quatro módulos de consentimento passaram para a versão 3.2: consentimentos incompatíveis, extensão com status inválido, cenários negativos e grupos de permissão.

</details>

<details>
<summary>2024 - 13 alterações</summary>

**01/11 · Planos** - Enrollments 2.0.0

Incluído o módulo de parâmetros inválidos de enrollments na versão 2, acompanhando a publicação da API 2.0.0.

**04/10 · Planos** - Módulos de enrollments realocados para a FVP Manual

Três módulos de enrollments que dependem da jornada do usuário saíram do plano automático e passaram a ser executados apenas na FVP Manual: opções de status inválidas, troca de chaves de pagamento e campos de pagamento divergentes.

**23/09 · Planos** - Ampliação do plano automático

O plano quase dobrou de tamanho, de 25 para 46 módulos. Entraram os módulos de consentimento v3, os de pagamentos v4 (DICT, MANU, QRES, agendamento, limites de recorrência, assinatura e cabeçalho de aceite), os de pagamentos automáticos v1, o DCR com tls_client_auth e a verificação de status de certificação.

**24/08 · Planos** - Enrollments na FVP Automática

Os primeiros módulos de enrollments passaram a ser executados na FVP Automática, cobrindo parâmetros inválidos e opções de status inválidas.

**29/07 · Planos** - Cadastro no Diretório atualizado para a versão 2

O módulo de cadastro no Diretório passou para o directory_api_server-registration_test_module_v2, substituindo a versão anterior.

**24/06 · Planos** - Novos cenários de pagamentos v3

Incluídos módulos de teste de pagamentos v3 no plano de execução: fvp-payments_api_dict_test-module_v3, fvp-payments_api_manu-fail_test-module_v3, fvp-payments_api_pixscheduling-dates-unhappy_test-module_v3 e fvp-payments_api_qres-code-enforcement_test-module_v3.

**23/05 · Periodicidade** - Execução diária

A rotina de execução passou a rodar diariamente, com atualização dos chamados de acordo.

**23/05 · Planos** - Cenários felizes de consentimento

Adicionado um cenário feliz para consents v2 e v3, payments v3 e v4 e automatic payments v1; os módulos fazem o fluxo de DCR e um POST para as respectivas APIs: fvp_consents_api_bad-logged_test-module_v2, fvp_consents_api_bad-logged_test-module_v3, fvp_payments_consents_api_bad-logged_test-module_v3, fvp_payments_consents_api_bad-logged_test-module_v4 e fvp_automatic_payments_consents_api_bad-logged_test-module_v1.

**16/04 · Certificados** - Certificado de assinatura atualizado

Atualizado o certificado de assinatura usado pela ferramenta para o método private_key_jwt e para o fluxo da fase 3.

**15/04 · Comportamento** - FAPI Unique e novo cenário de DCR

Todos os servidores passaram a ser testados apenas com o método private_key_jwt na verificação do well-known, independentemente de suportá-lo. Adicionado o dcr_api_fvp-unhappy-tls-client-auth_test_module, que tenta um DCR com tls_client_auth e espera rejeição do servidor.

**25/03 · Comportamento** - DCR com private_key_jwt para todos

Os testes de DCR passaram a usar o método private_key_jwt para todos os servidores, independentemente de suporte, além da execução com tls_client_auth para os que suportam esse método.

**22/01 · Planos** - Cenários negativos de consentimento de pagamentos v3

Adicionado o payments_api_consents_negative_no_redirect_test-module_v3, que executa 5 cenários negativos de consentimento de pagamentos v3 e 1 cenário positivo.

**11/01 · Planos** - Teste de certificado revogado reincluído

O dcr_api_fvp-revoked-certificate_test-module voltou a ser executado e a notificar as instituições.

</details>

<details>
<summary>2023 - 16 alterações</summary>

**13/10 · Planos** - Cenários negativos de consentimento de pagamentos v2

Adicionado o payments_api_consents_negative_no_redirect_test-module_v2, que executa 5 cenários negativos de consentimento de pagamentos e 1 cenário positivo.

**21/09 · Planos** - Verificação de status de certificação

Adicionado o directory_api_certification-status_test-module, que verifica o status de certificação de cada API após a certificação automática semanal.

**08/09 · Planos** - Remoção do teste de certificado revogado

Removido o dcr_api_fvp-revoked-certificate_test-module da execução, a pedido do GT de Segurança.

**31/08 · Comportamento** - Critério de seleção de servidores

A rotina passou a incluir todos os Authorization Servers publicados com well-known corretamente formatado, inclusive well-knowns duplicados; antes, testava-se apenas um servidor por well-known.

**31/08 · Certificados** - Certificado do DCR feliz atualizado (SERPRO)

O teste dcr_api_fvp-fapi1-advanced-final-brazil-dcr-no-authorization-flow_happy-flow_test-module passou a usar um BRCAC emitido pela AC SERPRO SSLv1, garantindo que as organizações aceitem esse novo tipo de certificado.

**17/08 · Certificados** - Certificado revogado e atualização SERASA

Adicionado o dcr_api_fvp-revoked-certificate_test-module, que faz o fluxo de DCR apresentando um certificado revogado e espera rejeição do servidor. Os testes dcm-subject-dn-test-fvp e dcr-brcac2022-support-fvp passaram a usar um BRCAC emitido pela AC SERASA SSL EV V4.

**13/07 · Planos** - Teste de cadastro no Diretório e novo chamado

Adicionado o directory_api_server-registration_test-module, que verifica se as instituições cadastraram corretamente seus servidores conforme o Guia de Operação do Diretório (certificação de segurança e funcional presentes e metadados válidos). Passou a existir um chamado próprio para falhas nesse teste, totalizando dois chamados possíveis por servidor: um para os testes de DCR e outro para o cadastro no Diretório.

**06/07 · Planos** - Certificado do endpoint do servidor

Adicionado o fvp-payments-consents-server-certificate-v2, que confirma se o certificado usado nos endpoints do servidor está alinhado aos padrões de certificado brasileiros.

**29/06 · Certificados** - Atualização de certificado (SOLUTI G4)

Os testes de FAPI-DCR passaram a usar um BRCAC emitido pela AC SOLUTI SSL EV G4, garantindo que as organizações aceitem esse novo tipo de certificado.

**15/06 · Comportamento** - Cabeçalho x-fapi-interaction-id em consents

Adicionado o cabeçalho x-fapi-interaction-id à requisição de POST payments-consents.

**01/06 · Plataforma** - Download do log em zip na página de resultado

Foi adicionado um botão na página enviada às instituições quando falham nos testes, permitindo baixar os logs como na Conformance Suite.

**10/03 · Mensagens** - Detalhes de erro no chamado do Service Desk

A notificação do Service Desk passou a incluir, além dos testes que falharam, a hipótese de falha identificada no teste.

**09/03 · Comportamento** - Critério de seleção de servidores

A rotina passou a incluir todos os Authorization Servers publicados com well-known corretamente formatado; antes, testava-se apenas servidores com endpoints de consents ou de payments-consents publicados.

**02/02 · Certificados** - Atualização de certificado (SOLUTI G3)

Os testes dcm-subject-dn-test-fvp e dcr-brcac2022-support-fvp passaram a usar um BRCAC emitido pela AC SOLUTI SSL EV G3.

**13/01 · Certificados** - Atualização de certificado (SERASA V3)

Os testes dcm-subject-dn-test-fvp e dcr-brcac2022-support-fvp passaram a usar um BRCAC emitido pela AC SERASA SSL EV V3.

**12/01 · Planos** - Três novos cenários de DCR

Adicionados os módulos dcr-subjectdn-fvp (verifica o parsing do tls_subject_dn em diferentes formatos), dcr-brcac2022-support-fvp (aceitação do formato novo e antigo do certificado de transporte brasileiro) e dcm-subject-dn-test-fvp (aceitação de um PUT que troca o tls_subject_dn para o de um novo certificado).

</details>

<details>
<summary>2022 - 8 alterações</summary>

**22/12 · Comportamento** - Teste de múltiplos clientes

O módulo dcr-multiple-clients passou a retornar falha, em vez de aviso, quando o servidor aceita um DCR com um client_id já criado para o mesmo Software Statement.

**30/11 · Comportamento** - Comportamento do teste de exclusão de DCR

O teste fapi1-advanced-final-brazildcr-client-delete-no-authorization-flow passou a aguardar 1 minuto entre a exclusão do cliente e a emissão de um token.

**15/11 · Plataforma** - Suporte a múltiplos servidores e correção de mtls.ca

Corrigido o problema, introduzido na versão de 2022-11-08, em que o certificado folha era enviado na cadeia de CA intermediária. Implementada a capacidade de testar múltiplos servidores de uma mesma organização cadastrada no Diretório.

**08/11 · Certificados** - Cadeia de certificados mtls.ca ajustada

A cadeia de certificados intermediários passou a enviar apenas o certificado intermediário e a raiz, removendo os intermediários não relacionados ao certificado em uso, conforme a RFC 5246.

**25/10 · Plataforma** - Suporte a CAs adicionais

Implementada a capacidade de usar múltiplos certificados no mesmo plano de teste, viabilizando testes que exigem mais de um certificado emitido.

**16/08 · Plataforma** - Novo teste opcional e página de resultados

Adicionado o dcr-test-multiple-clients (retorna aviso se o servidor suporta mais de um cliente por servidor, durante o período de adaptação). Implementada a página de resultados, com link único por instituição para acessar os resultados após a execução semanal.

**04/08 · Planos** - Suporte a testes da fase 3 e remoções

O consents-bad-logged passou a chamar tanto o endpoint de payments-consents (fase 3) quanto o de consents (fase 2). Removidos o dcr-subjectdn e o dcr-test-attempt-client-takeover, a pedido do GT de Segurança. A rotina passou a obter o endpoint de payments-consents além do de consents da fase 2.

**01/07 · Plataforma** - Lançamento da plataforma

Plataforma criada com 23 planos de teste, incluindo os 18 testes originais de FAPI-DCR e 5 testes funcionais específicos (consents-bad-logged, dcr-test-sandbox-credentials, dcr_no_subject_type, dcr-subjectdn e dcr-test-attempt-client-takeover). A comunicação com as instituições passou a ser feita pelo Service Desk (SysAid), com os resultados entregues em arquivo .zip.

</details>

---

[↑ FVP](FVP/PT) · [◀ FVP](FVP/PT) · [Testes de DCR ▶](FVP/PT/Automatica/DCR)


---

*Conteúdo baixado em 16/09/2026, 15:37:50*
