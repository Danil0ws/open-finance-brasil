# Orientacoes_Execucao_FVP

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Orientacoes_Execucao_FVP](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Orientacoes_Execucao_FVP)
**Slug:** `Orientacoes_Execucao_FVP`

---

---
title: Orientações para o Time de Execução da FVP
---
## Introdução - Testes Agendados e Imediatos

O recurso **Testes Agendados** da FVP amplia a capacidade da plataforma para validar implementações em produção do Open Finance Brasil em **cenários de múltiplos dias**. Diferente das execuções tradicionais, que se encerram em uma única rodada, os testes agendados permitem iniciar um fluxo em um dia e continuar automaticamente nos dias subsequentes.

Essa funcionalidade é especialmente importante para validações que dependem de **datas, horários e comportamentos do sistema** que só podem ser observados de forma assíncrona.

Este documento concentra orientações para os testes agendados, mas também detalhes para a execução de testes imediatos.

1. [Automatic PIX Scheduling – Retry Tests](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Scheduled-Tests-%5BPT%5D#gear-pix-autom%C3%A1tico--agendamento-e-retry-m%C3%B3dulos-1-a-3)
2. [Payments API — Scheduled PIX Verification](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Scheduled-Tests-%5BPT%5D#gear-api-pagamentos--verifica%C3%A7%C3%A3o-de-pix-agendado-m%C3%B3dulos-1-e-2)
3. [Credit Portability — CPC](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Scheduled-Tests-%5BPT%5D#gear-portabilidade-de-cr%C3%A9dito--cpc-m%C3%B3dulos-1-a-3)
4. [Non-Redirect Journey — NJR (Enrollments)](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Scheduled-Tests-%5BPT%5D#gear-jornada-sem-redirecionamento--jsr)
5. [Jornada Otimizada — JO](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Orientacoes_Execucao_FVP#gear-jornada-otimizada--jo)

## Como funcionam os Testes Agendados

* **Execução assíncrona**: ao executar um fluxo de teste, podem ser programadas execuções de acompanhamento em datas futuras. Essas execuções ocorrem automaticamente, sem intervenção do usuário.
* **Persistência**: informações críticas como _client_id_, _consent_id_, _payment_id_ e _refresh tokens_ são armazenadas com segurança entre as rodadas para garantir a continuidade.
* **Temporização de negócios**: os testes são alinhados às linhas do tempo reais de pagamentos (por exemplo, D+2, D+3) e alguns são restritos a janelas específicas de execução (por exemplo, entre **21:00 e 23:59 BRT**).
* **Salvaguardas automáticas**: testes de acompanhamento só são agendados se o fluxo inicial for concluído com sucesso; caso ocorra erro no início do processo, nenhuma execução adicional é disparada.
* **Visibilidade**: a Estrutura da Associação Open Finance pode visualizar as execuções agendadas, sua origem e seu status (agendado, executado, cancelado).

## Fluxos de Teste Agendados Disponíveis

### Fluxo de Agendamento de Pix Automático

Valida que um **pagamento Pix recorrente pode ser agendado** e posteriormente executado conforme o esperado.

* A execução inicial cria e autoriza um consentimento recorrente, agenda um pagamento Pix Automático e armazena as informações relevantes.
* Um teste de acompanhamento confirma que o pagamento agendado é executado com sucesso na data futura definida.

### Fluxo de Tentativa (Retry) de Pix Automático

Valida os **mecanismos de nova tentativa** para pagamentos Pix agendados.

* A execução inicial cria um consentimento recorrente com _retry_ habilitado, agenda um pagamento Pix Automático e prepara o tratamento de falhas.
* Na execução de acompanhamento, o sistema valida que o pagamento original falhou e que uma nova tentativa foi corretamente iniciada com as referências apropriadas.
* Uma verificação final confirma que o pagamento de _retry_ foi removido da agenda, aceitando tanto o status **ACSC** quanto **RJCT**.

Em conjunto, esses fluxos asseguram que as instituições estão em conformidade com os padrões do Open Finance Brasil para **pagamentos Pix agendados e recorrentes**, cobrindo tanto o agendamento bem-sucedido quanto os cenários de nova tentativa.

### Fluxo de Portabilidade de crédito - CPC

Valida a progressão agendada de uma solicitação de portabilidade de crédito até que ela atinja o estado "**DISPONIVEL"**.

* A execução inicial envia a solicitação de portabilidade (com os dados de identificação necessários) e armazena os identificadores relevantes.
* O teste subsequente valida que a solicitação foi **aceita** pelas instituições envolvidas dentro da janela de negócio esperada.
* Um teste final confirma que a solicitação alcançou um **estado terminal de liquidação ou contratação** na janela seguinte.

Essas etapas garantem que as instituições cumpram os requisitos de **prazo e transição de estado** definidos pelo Open Finance Brasil para a portabilidade de crédito.

## Políticas de Execução

* Os testes agendados só podem ser executados por **pessoal autorizado**.
* Os testes agendados executam automaticamente nos horários designados após a execução do fluxo inicial.
* Identificadores e credenciais são **persistidos com segurança** entre as execuções.
* Alguns testes exigem execução em **janelas de tempo estritas** para refletir o comportamento real de produção.
* Logs e resultados ficam disponíveis pela interface da FVP.

## Lista de Planos de Teste

A lista completa de planos de teste disponíveis, seus módulos correspondentes e detalhes de execução está disponível abaixo. Ela complementa as descrições de alto nível com detalhes técnicos (endpoints, respostas esperadas, identificadores):

* **Planilha**: `fvp-async_tests.xlsx` (anexo na página original)

---

## Documentação de Execução de Testes

### :gear: PIX Automático — Agendamento e _Retry_ (Módulos 1 a 3)

**Módulos de Teste:**

* `automatic-payments_api_automatic-pix-scheduling-retry_1-3_test-module_v2`
* `automatic-payments_api_automatic-pix-scheduling-successful-retry_1-3_test-module_v2`

Este documento explica como validar pagamentos Pix recorrentes, incluindo o fluxo de **retry** quando o pagamento original falha.

#### 1) Campos obrigatórios para execução

Os campos variam conforme a execução: **Pessoa Física (PF)** ou **Pessoa Jurídica (PJ)**.

**Para debtor PF**

* `loggedUserIdentification`
* `brazilCpf` (11 dígitos, apenas números)

**Para debtor PJ**

* `loggedUserIdentification`
* `businessEntityIdentification`
* `brazilCnpj` (14 dígitos, apenas números)

**Para PF e PJ**

* `Authorisation Server ID`
* `contractDebtorName`
* `contractDebtorIdentification`
* `Payment consent – Creditor Account ISPB: `Pagamento/Consentimento – ISPB da conta credora primeiros 5 dígitos da instituição que detém a conta do recebedor
* `Payment consent – Creditor Account Issuer:` Emissor da conta credora / agência da instituição credora
* `Payment consent – Creditor Account Number:` Número da conta credora
* `Payment consent – Creditor Account Type: `Tipo da conta credora
* `Payment consent – Creditor Account Name: `Nome do titular da conta credora (recebedor)
* `Payment consent – Creditor Account CPF/CNPJ:` CPF/CNPJ do titular da conta credora (recebedor). Para **Pix Automático**, o identificador **deve ser um CNPJ**.

#### 2) Requisitos adicionais de execução

**Saldo em conta (debtor):**

* **D+0 (dia da execução):** R$ 0,00
* **D+1 (dia seguinte):** R$ 0,00
* **D+2 (dois dias após):** R$ 0,00
* **D+3 (três dias após):** **mínimo de R$ 1,00**

> **Nota**: “D+N” refere-se a N dias corridos após a execução do **Módulo 1**.

**Disponibilidade do servidor:**

* **Módulos 2 e 3** são agendados automaticamente pela Conformance Suite (não manuais).
* Manter o servidor do participante **online e responsivo entre 21:00 e 23:59 (BRT)** nos dias agendados.

#### 3) Visão geral dos módulos de teste

**Módulo 1 — Agendar pagamento recorrente (manual)**

* Criar manualmente um pagamento Pix recorrente.
* O primeiro pagamento deve ser **agendado para D+2**.
* Fluxo de status esperado: **Aguardando Autorização → Autorizado → Agendado**.
* Dados de consentimento e pagamento são **persistidos** para uso nos Módulos 2 e 3.

**Módulo 2 — _Retry_ após falha (automático; executa 2 dias após o Módulo 1)**

* A Conformance Suite inicia este módulo no horário programado.
* Verifica que o **primeiro pagamento agendado falhou**.
* Confirma que o sistema **agendou um _retry_ para D+1**.
* Janela de execução: **21:00 a 23:59 (BRT)**; o servidor do participante deve permanecer online.

**Módulo 3 — Confirmação de _retry_ bem-sucedido (automático; executa 1 dia após o Módulo 2)**

* A Conformance Suite inicia este módulo no horário programado.
* Verifica que o **pagamento de retry foi concluído com sucesso**.
* Status final do pagamento: **`ACSC`**.
* Janela de execução: **21:00 a 23:59 (BRT)**; o servidor do participante deve permanecer online.

---

### :gear: API Pagamentos — Verificação de PIX Agendado (Módulos 1 e 2)

Este documento explica como validar testes da **API Pagamentos** para **verificação de PIX agendado**.

#### 1) Campos obrigatórios para execução

Os campos variam conforme a execução: PF ou PJ.

**Para debtor PF**

* `loggedUserIdentification`
* `brazilCpf` (11 dígitos, apenas números)

**Para debtor PJ**

* `loggedUserIdentification`
* `businessEntityIdentification`
* `brazilCnpj` (14 dígitos, apenas números)

**PF e PJ**

* `Authorization Server ID`
* `Payment consent – Creditor Account ISPB`: ISPB da conta credora primeiros 5 dígitos da instituição que detém a conta do recebedor
* `Payment consent – Creditor Account Issuer:` Emissor da conta credora: agência da instituição credora
* `Payment consent – Creditor Account Number:` Número da conta credora
* `Payment consent – Creditor Account Type:` Tipo da conta credora
* `Payment consent – Creditor Account Name:` Nome do titular da conta credora (recebedor)
* `Payment consent – Creditor Account CPF/CNPJ:` CPF/CNPJ do titular da conta credora (recebedor\*\*)\*\* (_pode ser CPF ou CNPJ_)
* `Payment consent – Creditor Account Proxy (Pix key):` Proxy (chave Pix) do recebedor

#### 2) Requisitos adicionais de execução

**Saldo em conta (devedor):**

* **D+0 (dia da execução):** **R$ 2,00**
* **D+1 (dia seguinte):** **R$ 2,00**
* **D+2 (dois dias após):** **R$ 1,00**

**Disponibilidade do servidor:**

* **Módulo 2** é agendado automaticamente pela Conformance Suite (não manual).
* Manter o servidor do participante **online e responsivo entre 05:00 e 06:59 (BRT)** nos dias agendados.

#### 3) Visão geral dos módulos de teste

**Módulo 1 — Agendar dois pagamentos (manual)**

* Criar manualmente **dois** pagamentos Pix agendados:
  * Primeiro pagamento agendado para **D+1**
  * Segundo pagamento agendado para **D+2**
* Fluxo de status esperado: **Aguardando Autorização → Autorizado → Agendado**.
* Consentimento e dados de pagamento são **persistidos** para o Módulo 2.

**Módulo 2 — Verificar execução de ambos os pagamentos (automático)**

* A Conformance Suite inicia este módulo no horário programado.
* Verifica que **ambos os pagamentos agendados** foram concluídos com sucesso.
* Status final de cada pagamento: **`ACSC`**.

---

## :gear: **Portabilidade de crédito — CPC (Módulos 1 a 3)**

Planos e módulos de teste (**imediatos e agendados**) relacionados às instruções desta seção:

* **Imediatos**: Production Functional Tests for Credit Portability - API Version 1:
  * `fvp-credit-portability_api_invalid-contract-terms_test-module_v1`
  * `fvp-credit-portability_api_received-portability_test-module_v1`
  * `fvp-credit-portability_api_invalid_grant_type_invalid_x-fapi_invalid_idempodency_test-module_v1`
* **Agendados**: Production Functional Tests for Credit Portability Scheduling - API Version 1:
  * `fvp-credit-portability_api_accepted_settlement_1-3_test-module_v1` - manualmente executado
  * `fvp-credit-portability_api_accepted_settlement_2-3_test-module_v1` - automaticamente agendado
  * `fvp-credit-portability_api_accepted_settlement_3-3_test-module_v1` - automaticamente agendado

### **1) Campos para execução**

Os nomes espelham o formulário da FVP:

* `alias` — **Opcional.** Automaticamente preenchido/substituído pela informação coletada através do authorizationServerId.
* `description` **— Opcional**, a criterio do usuário.
* `publish` **—** Define a visibilidade dos resultados para outros usuários. “**Everything**” expõe detalhes de configuração (incluindo segredos). Use “**summary**” se quiser manter esses detalhes privados, publicando só o resultado geral. Na dúvida, escolha “**No**” (é possível tornar público depois).
* `discoveryUrl `**— Opcional.** Automaticamente preenchido/substituído pela informação coletada através do authorizationServerId.
* `authorizationServerId `**— Obrigatório.** ID do _Authorization Server_ da instituição no Diretório.
* **PF / PJ (obrigatório, escolha 1):**
  * **PF:** brazilCpf (11 dígitos, apenas números)
  * **PJ:** brazilCnpj (14 dígitos, apenas números)

    Preencha **apenas um**. Se ambos forem enviados, a execução pode ser rejeitada.
* `discoveryEndpoint` — **Opcional**. Automaticamente preenchido/substituído pela informação coletada através do authorizationServerId.

### **2) Requisitos adicionais de execução**

**Saldo em conta:** não é necessário para os testes de Portabilidade de crédito, mas sim um empréstimo do tipo pessoal clean (CPC).

**Disponibilidade do servidor:**

* Os Módulos **2** e **3** são agendados **automaticamente** pelo Conformance Suite (não são manuais).
* Garanta que o servidor do participante está **online e responsivo** nos dias agendados.

  Se estiver **off-line** na janela, os Módulos 2 e 3 poderão falhar.

### **3) Visão geral dos módulos e janelas**

* **Módulo 1 (M1 - manual):**
  * Submete uma solicitação de Portabilidade de Crédito que deve atingir o status RECEIVED e armazena os identificadores necessários para a validação de acompanhamento.
  * O teste exige que o usuário possua ao menos um contrato CREDITO_PESSOAL_CLEAN com concurrentManagement = DISPONIVEL e isEligible = TRUE.
  * Executa a sequência completa de pré-verificações (_consent_; recuperação de contratos; elegibilidade; POST /portabilities) e agenda o **Módulo 2** para o **próximo dia útil (D+1) às 10:10 (GMT-3)**.
* **Módulo 2 (M2 - automático, próxima janela/dia):**
  * Valida que a mesma solicitação de portabilidade evolui para ACCEPTED_SETTLEMENT_IN_PROGRESS dentro do prazo de negócio esperado.
  * Se o status ainda estiver PENDING, a suíte **reagenda automaticamente** este módulo.
  * Quando a solicitação é aceita, o teste aciona um **cancelamento pelo cliente** com PATCH /portabilities/{id}/cancel e reasonType = CANCELADO_PELO_CLIENTE, confirmando o término correto com status = CANCELLED.
  * Ao concluir, agenda para o dia seguinte o módulo de verificação de _concurrent management_ do contrato (às 00:01, GMT-3).
* **Módulo 3 (M3 - automático, próxima janela/dia):**
  * Confirma que o contrato original retorna a DISPONIVEL e permanece elegível para futuras portabilidades.
  * Valida data.portability.status = DISPONIVEL e isEligible = TRUE, e então **exclui o consentimento** associado, concluindo o ciclo.

### **4) Cronograma e duração máxima**

* **Janelas por plano:** o M1 pode ser executado em qualquer horário. Os horários exatos de execução M2 e M3 são **pré-configurados** na FVP.
* **Duração máxima:** espera-se concluir em tempo **≤ 5 dias úteis**, excluindo fins de semana e feriados nacionais.

  Se esse limite for atingido sem estado terminal, o teste é reportado como **Not Completed / Expired** e será necessária reexecução completa.

---

## :gear: **Jornada sem Redirecionamento — JSR**

Planos de teste (**imediatos** e **agendados**) relacionados às instruções desta seção:

* **Production Functional Tests for No Redirect Payments - API Version 2.2**
* **Production Functional Tests for No Redirect Payments Scheduling - API Version 2.2**
* **Production Functional Tests for No Redirect Automatic Pix Payments - API Version 2.2**
* **Production Functional Tests for No Redirect Automatic Pix Payments Scheduling - API Version 2.2**

### **1) Campos para execução**

Os nomes espelham o formulário da FVP:

**Para debtor PF:**

* `brazilCpf` - 11 dígitos, apenas números

**Para debtor PJ:**

* `businessEntityIdentification` - Sempre CNPJ, 14 dígitos, apenas números
* `brazilCnpj` - 14 dígitos, apenas números

**PF e PJ:**

* `alias` — **Opcional.** Automaticamente preenchido/substituído pela informação coletada através do authorizationServerId.
* `description` **— Opcional**, a criterio do usuário.
* `publish` **—** Define a visibilidade dos resultados para outros usuários. “**Everything**” expõe detalhes de configuração (incluindo segredos). Use “**summary**” se quiser manter esses detalhes privados, publicando só o resultado geral. Na dúvida, escolha “**No**” (é possível tornar público depois).
* `loggedUserIdentification` - **Obrigatório.** Sempre CPF, 11 dígitos, apenas números.
* `authorizationServerId` **- Obrigatório.** ID do _Authorization Server_ da instituição no Diretório.
* `Payment consent – Creditor Account ISPB`- **Obrigatório.** ISPB da conta credora primeiros 5 dígitos da instituição que detém a conta do recebedor.
* `Payment consent – Creditor Account Issuer` - **Obrigatório.** Emissor da conta credora: agência da instituição credora.
* `Payment consent – Creditor Account Number` - **Obrigatório.** Número da conta credora.
* `Payment consent – Creditor Account Type` - **Obrigatório.** Tipo da conta credora.
* `Payment consent – Creditor Account Name` - **Obrigatório.** Nome do titular da conta credora (recebedor).
* `Payment consent – Creditor Account CPF/CNPJ` - **Obrigatório.** CPF/CNPJ do titular da conta credora (recebedor).
* `Payment consent – Creditor Account Proxy (Pix key)` - **Obrigatório.** Proxy (chave Pix) do recebedor.

**Obrigatórios exclusivamente para plano de Enrollments + Automatic Payments:**

* `contractDebtorName` - Nome do cliente devedor do contrato.
* `contractDebtorIdentification` - CPF/CNPJ do cliente devedor do contrato.

### **2) Requisitos adicionais de execução de testes de longa duração:**

**Saldo em conta (debtor):**

* Production Functional Tests for No Redirect Payments Scheduling - API Version 2.2:
  * **D+0 (dia da execução):** indiferente - Sugere-se ter um saldo mínimo de R$2,00 para início do teste.
  * **D+1 (dia seguinte):** mínimo de R$ 1,00 \<\<\<\<
  * **D+2 (dois dias após):** mínimo de R$ 1,00 \<\<\<\<
  * **D+3 (três dias após):** indiferente
* Production Functional Tests for No Redirect Automatic Pix Payments Scheduling - API Version 2.2:
  * **D+0 (dia da execução):** indiferente - Sugere-se ter um saldo mínimo de R$1,00 para início do teste.
  * **D+1 (dia seguinte):** indiferente
  * **D+2 (dois dias após):** mínimo de R$ 1,00 \<\<\<\<
  * **D+3 (três dias após):** indiferente

> **Nota**: “D+N” refere-se a N dias corridos após a execução do **Módulo 1**.

**Disponibilidade do servidor:**

* O Módulo **2** é agendado **automaticamente** pelo Conformance Suite (não é manual).
* Executar o módulo 2 diretamente acarretará abertura indesejada de ticket contra a instituição, contendo link incorreto ("quebrado") do test manager.
* Garanta que o servidor do participante está **online e responsivo** nos dias agendados. Se estiver **off-line** na janela, o Módulo 2 falhará.

### **3) Visão geral dos módulos e janelas de longa duração**

* Production Functional Tests for No Redirect Payments Scheduling - API Version 2.2:
  * **Agenda dois pagamentos** de 1,00 cada, via JSR
    * Pagamento 1 para D+1
    * Pagamento 2 para D+2
    * Em D+3 o teste confere o sucesso desses pagamentos
  * Módulo 1 pode ser executado a qualquer horário
  * Módulo 2 ocorrerá às **5am BRT de D+3**
* Production Functional Tests for No Redirect Automatic Pix Payments Scheduling - API Version 2.2:
  * **Agenda um pagamento automático** de 1,00, via JSR
    * Pagamento em D+2.
    * Em D+3 o teste confere o sucesso desse pagamento
  * Módulo 1 pode ser executado a qualquer horário
  * Módulo 2 ocorrerá às **9pm BRT de D+3**

### **4) Cronograma e duração máxima**

* **Janelas por plano:** o Módulo 1 pode ser executado em qualquer horário. Os horários exatos de execução dos Módulos 2 de cada plano são **pré-configurados** na FVP.
* **Duração máxima:** 3 dias corridos (inclui dias não úteis).

### **5) Comportamento dos testes imediatos em relação a pagamentos e outras observações**

* **Production Functional Tests for No Redirect Payments - API Version 2.2**

| Módulo | Valor do pagamento | Resultado esperado |
|--------|--------------------|--------------------|
| **fvp-enrollments-api-pre-flight-test-v2** | \- | Sem pagamentos. |
| **fvp-enrollments_api_payments-core_open_test-module_v2-2** | 0.5 BRL  | :white_check_mark: Pagamento com sucesso de R$0,50. |
| **fvp-enrollments_api_invalid-challenge_open_test-module_v2-2** | \- | Sem pagamentos. |
| **fvp-enrollments_api_invalid-origin_open_test-module_v2-2** | \- | Sem pagamentos. |
| **fvp-enrollments_api_invalid-public-key_open_test-module_v2-2** | \- | Sem pagamentos. |
| **fvp-enrollments_api_invalid-rpid_open_test-module_v2-2** | \- | Sem pagamentos. |
| **fvp-enrollments_api_invalid-status-sign-options_open_test-module_v2-2** | \- | Sem pagamentos. |
| **fvp-enrollments_api_payments-pre-enrollment_open_test-module_v2-2** | **-** | :warning: Há uma tentativa de pagamento com R$0,50 centavos, mas não deve ter sucesso. |
| **fvp-enrollments_api_payments-unmatching-fields_open_test-module_v2-2** | **-** | :warning: Há duas tentativas de pagamento com R$0,50 centavos cada, mas não deve ter sucesso em nenhuma. |
| **fvp-enrollments_api_payments-keys-swap_open_test-module_v2-2** | **-** | Sem pagamentos. |

* **Production Functional Tests for No Redirect Automatic Pix Payments - API Version 2.2**

<table>
<tr>
<th>Módulo</th>
<th>Valor do pagamento</th>
<th>Resultado esperado</th>
</tr>
<tr>
<td>

**fvp-enrollments_automatic-payments_authorised-executed-scheduled-successfully_v2-2**
</td>
<td>R$1,50</td>
<td>

:white_check_mark: Duas tentativas de pagamento, ambas esperam sucesso:

* Primeiro: R$1,00
* Segundo: R$0,50

:warning: **_É mandatório, durante a etapa de redirecionamento, selecionar tempo indeterminado para que o teste tenha sucesso_**
</td>
</tr>
<tr>
<td>

**fvp-enrollments_api_automatic-payment_enrollment-limits_negative_test-module_v2-2**
</td>
<td>

\-
</td>
<td>

:warning: Consentimento criado, há tentativa de pagamento com R$2,00, mas **não deve ter sucesso.**
</td>
</tr>
<tr>
<td>

**fvp-enrollments_api_automatic-payments_enrollment-limits_v2-2**
</td>
<td>R$1,00</td>
<td>

:white_check_mark: Duas tentativas de pagamento, apenas a primeira espera sucesso:

* Primeiro: R$1,00
* Segundo: R$0,50 (agendado, não deve descontar)
</td>
</tr>
<tr>
<td>

**fvp-enrollments_automatic-payments_sweeping-consent-not-authorised_v2-2**
</td>
<td>

\-
</td>
<td>Sem pagamentos.</td>
</tr>
</table>

---

## :gear: Jornada Otimizada — JO

Planos de teste (todos imediatos, sem testes agendados) relacionados às instruções desta seção:

* Production Functional Tests for Optimised Journey Core - API Version 1
* Production Functional Tests for Optimised Journey Automatic Payments - API Version 1
* Production Functional Tests for Optimised Journey No Redirect Payments - API Version 1

### 1) Planos e módulos

Production Functional Tests for Optimised Journey Core - API Version 1 (3 módulos):

* fvp-optimised-journey_automatic-pix_test-module-v1
* fvp-optimised-journey_invalid-permissions_test-module-v1
* fvp-optimised-journey_payments_test-module-v1

Production Functional Tests for Optimised Journey Automatic Payments - API Version 1 (5 módulos):

* fvp-optimised-journey_sweeping_payments-balances_test-module-v1
* fvp-optimised-journey_sweeping_revoked-consent_payments_test-module-v1
* fvp-optimised-journey_sweeping_revoked-recurring-consent_test-module-v1
* fvp-optimised-journey_sweeping_invalid-par_test-module-v1
* fvp-optimised-journey_sweeping_invalid-request_test-module-v1

Production Functional Tests for Optimised Journey No Redirect Payments - API Version 1 (5 módulos):

* fvp-optimised-journey_enrollments-balances_test-module-v1
* fvp-optimised-journey_enrollments_revoked-consent_payments_test-module-v1
* fvp-optimised-journey_enrollments_revoked-enrollment_test-module-v1
* fvp-optimised-journey_enrollments-invalid-request_test-module-v1
* fvp-optimised-journey_enrollments-invalid_par_test-module-v1

### 2) Campos para execução

Os nomes abaixo espelham os labels do formulário da FVP. O mesmo conjunto de campos vale para todos os módulos de um mesmo plano.

Detalhamento:

* `alias` — Opcional. Automaticamente preenchido/substituído pela informação coletada através do Authorisation Server ID.
* `description` — Opcional, a critério do usuário.
* `publish` — Define a visibilidade dos resultados para outros usuários. "Everything" expõe detalhes de configuração (incluindo segredos). Use "summary" se quiser manter esses detalhes privados, publicando só o resultado geral. Na dúvida, escolha "No" (é possível tornar público depois).
* `Authorisation Server ID` — Obrigatório. ID do Authorization Server da instituição no Diretório.
* `Payment consent - Logged User CPF` — Obrigatório. CPF do usuário logado, 11 dígitos, apenas números.
* `Payment consent - Business Entity CNPJ` — Obrigatório para PJ. CNPJ, 14 dígitos, apenas números.
* `Payment consent - Creditor Account ISPB` — Obrigatório. ISPB da conta credora (primeiros 8 dígitos da instituição que detém a conta do recebedor).
  * **Para os testes de sweeping (Automatic Payments) devem ser utilizados sempre os dados de mesma titularidade de quem executa o teste.**
* `Payment consent - Creditor Account Issuer` — Obrigatório. Agência da conta credora.
  * **Para os testes de sweeping (Automatic Payments) devem ser utilizados sempre os dados de mesma titularidade de quem executa o teste.**
* `Payment consent - Creditor Account Number`— Obrigatório. Número da conta credora.
  * **Para os testes de sweeping (Automatic Payments) devem ser utilizados sempre os dados de mesma titularidade de quem executa o teste.**
* `Payment consent - Creditor Account Type` — Obrigatório. Tipo da conta credora (ex.: SVGS, CACC).
  * **Para os testes de sweeping (Automatic Payments) devem ser utilizados sempre os dados de mesma titularidade de quem executa o teste.**
* `Payment consent - Creditor Account Name` — Obrigatório. Nome do titular da conta credora (recebedor).
  * **Para os testes de sweeping (Automatic Payments) devem ser utilizados sempre os dados de mesma titularidade de quem executa o teste.**
* `Payment consent - Creditor Account CPF / CNPJ` — Obrigatório, **conforme tabela abaixo**.
  * **Para os testes de sweeping (Automatic Payments) devem ser utilizados sempre os dados de mesma titularidade de quem executa o teste.**
* `Recurring Payment consent - Contract Debtor Name` — Obrigatório, **conforme tabela abaixo**.
  * Informações sobre o cliente devedor do contrato. Pode possuir titularidade diferente do usuário pagador descrito nos objetos "/data/loggedUser" e "/data/businessEntity".
* `Recurring Payment consent - Contract Debtor Identification` — Obrigatório, **conforme tabela abaixo.**
  * Número do documento de identificação oficial do cliente devedor do contrato (CPF ou CNPJ).
* `brazilCpf` — Obrigatório para PF. CPF, 11 dígitos, apenas números.
* `brazilCnpj` — Obrigatório para PJ. CNPJ, 14 dígitos, apenas números.

| Campo | Core | Automatic Payments | No Redirect Payments |
|-------|:----:|:------------------:|:--------------------:|
| alias | X | X | X |
| description | X | X | X |
| publish | X | X | X |
| Authorisation Server ID | X | X | X |
| Payment consent - Logged User CPF | X | X | X |
| Payment consent - Business Entity CNPJ | X | X | X |
| Payment consent - Creditor Account ISPB | X | X | X |
| Payment consent - Creditor Account Issuer | X | X | X |
| Payment consent - Creditor Account Number | X | X | X |
| Payment consent - Creditor Account Type | X | X | X |
| Payment consent - Creditor Account Name | X | X | X |
| Payment consent - Creditor Account CPF / CNPJ | X |  | X |
| Recurring Payment consent - Contract Debtor Name | X |  |  |
| Recurring Payment consent - Contract Debtor Identification | X |  |  |
| brazilCpf | X | X | X |
| brazilCnpj | X | X | X |

### 3) Requisitos adicionais de execução

Saldo em conta (debtor):

* Production Functional Tests for Optimised Journey Core - API Version 1
  * Nenhum pagamento é executado neste plano.
  * Os 3 módulos são fluxos de rejeição — o consent é rejeitado antes de qualquer tentativa de débito.
  * Saldo em conta é indiferente; basta que a conta debtor exista, esteja ativa e seja elegível para a autorização do consent.
  * **Configure este plano com um creditor PJ**
* Production Functional Tests for Optimised Journey Automatic Payments - API Version 1
  * Dois pagamentos de R$ 1,00 são executados pelos seguintes módulos:
    * fvp-optimised-journey_sweeping_payments-balances_test-module-v1
    * fvp-optimised-journey_sweeping_revoked-consent_payments_test-module-v1
    * Os demais módulos do plano não executam pagamento.
  * Saldo mínimo recomendado na conta debtor no início da execução do plano: R$ 2,00.
  * **Configure este plano com um creditor PF (mesma titularidade)**
* Production Functional Tests for Optimised Journey No Redirect Payments - API Version 1
  * Dois pagamentos de R$ 1,00 são executados em sequência pelos seguintes módulos:
    * fvp-optimised-journey_enrollments-balances_test-module-v1
    * fvp-optimised-journey_enrollments_revoked-consent_payments_test-module-v1
    * Os demais módulos do plano não executam pagamento.
  * Saldo mínimo recomendado na conta debtor no início da execução do plano: R$ 2,00.
  * **Configure este plano com um creditor PF ou PJ**

Nota sobre o valor do pagamento: todos os pagamentos da Jornada Otimizada são fixos em R$ 1,00 BRL pela FVP, mesmo que seja enviado paymentAmount na configuração JSON.

Disponibilidade do servidor:

* Todos os 13 módulos da Jornada Otimizada são imediatos — não há agendamento nem execuções assíncronas. Não há janela de tempo específica para executar os testes; basta que o servidor do participante esteja online e responsivo durante a execução manual do plano. Se o servidor ficar indisponível no meio da execução, os módulos subsequentes falharão e o plano precisará ser reexecutado do início.

### 4) Comportamento dos testes em relação a pagamentos e outras observações

Production Functional Tests for Optimised Journey Core - API Version 1

| Módulo | Cenário | Valor do pagamento | Resultado esperado |
|--------|---------|--------------------|--------------------|
| fvp-optimised-journey_automatic-pix_test-module-v1 | Garantia de erro | — | Consent de recurring-payments (Automatic Pix) criado, mas rejeitado após redirect — Automatic Pix não é permitido na JO. Sem pagamento. |
| fvp-optimised-journey_invalid-permissions_test-module-v1 | Garantia de erro | — | POST /consents retorna 422 por combinação de permissões incorreta (COMBINACAO_PERMISSOES_INCORRETA). Sem pagamento. |
| fvp-optimised-journey_payments_test-module-v1 | Garantia de erro | — | Consent de pagamento criado, mas rejeitado após redirect — Payments API não é permitida na JO. Sem pagamento. |

Production Functional Tests for Optimised Journey Automatic Payments - API Version 1

| Módulo | Cenário | Valor do pagamento | Resultado esperado |
|--------|---------|--------------------|--------------------|
| fvp-optimised-journey_sweeping_payments-balances_test-module-v1 | Interoperabilidade | R$ 1,00 | Pagamento executado com sucesso via POST /recurring-payments, saldo reduzido, PATCH revoga o recurring-consent ao final. |
| fvp-optimised-journey_sweeping_revoked-consent_payments_test-module-v1 | Garantia de jornada | R$ 1,00 | Após DELETE /consents, o pagamento via recurring-consent ainda é executado com sucesso (status final ACSC). |
| fvp-optimised-journey_sweeping_revoked-recurring-consent_test-module-v1 | Garantia de jornada | — | PATCH revoga o recurring-consent após autorização. Sem pagamento. |
| fvp-optimised-journey_sweeping_invalid-par_test-module-v1 | Garantia de erro | — | PAR sem recurringConsentId → consent rejeitado (FLUXO_NAO_SUPORTADO_PRODUTO). Sem pagamento. |
| fvp-optimised-journey_sweeping_invalid-request_test-module-v1 | Garantia de erro | — | POST /recurring-consents sem o objeto journey → consent rejeitado (FLUXO_NAO_SUPORTADO_PRODUTO). Sem pagamento. |

Production Functional Tests for Optimised Journey No Redirect Payments - API Version 1

| Módulo | Cenário | Valor do pagamento | Resultado esperado |
|--------|---------|--------------------|--------------------|
| fvp-optimised-journey_enrollments-balances_test-module-v1 | Interoperabilidade | R$ 1,00 | Pagamento executado com sucesso via FIDO_FLOW (POST /pix/payments), saldo reduzido, PATCH revoga o enrollment ao final. |
| fvp-optimised-journey_enrollments_revoked-consent_payments_test-module-v1 | Garantia de jornada | R$ 1,00 | Após DELETE /consents, o pagamento via enrollment ainda é executado com sucesso via FIDO_FLOW (status final ACSC). |
| fvp-optimised-journey_enrollments_revoked-enrollment_test-module-v1 | Garantia de jornada | — | PATCH revoga o enrollment após autorização. Sem pagamento. |
| fvp-optimised-journey_enrollments-invalid-request_test-module-v1 | Garantia de erro | — | POST /enrollments sem o objeto journey → enrollment rejeitado (REJEITADO_SEGURANCA_INTERNA). Sem pagamento. |
| fvp-optimised-journey_enrollments-invalid_par_test-module-v1 | Garantia de erro | — | PAR sem enrollmentId → consent rejeitado (INTERNAL_SECURITY_REASON). Sem pagamento. |



---

*Conteúdo baixado em 16/09/2026, 15:38:14*
