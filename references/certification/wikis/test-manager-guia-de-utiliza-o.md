# Test Manager   Guia de Utilização

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Test-Manager---Guia-de-Utilização](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Test-Manager---Guia-de-Utilização)
**Slug:** `Test-Manager---Guia-de-Utilização`

---

---
title: Test Manager - Guia de Utilização
---
## **Objetivo**

* Explicar, objetivamente, como o Test Manager **abre**, **alimenta** e **fecha** tickets no Service Desk quando testes agendados são executados a partir da FVP Manual de longa duração.

---

## **Visão geral**

* O Test Manager é o sistema que permite a execução de testes agendados da FVP Manual Restrita e a integração das respectivas execuções com o Service Desk. Quando um plano de testes agendados é executado, o sistema pode:
  * **Abrir** um ticket (primeira falha do plano).
  * **Atualizar** um ticket existente (falhas seguintes do mesmo plano, via nota).
  * **Fechar** um ticket automaticamente (quando todos os testes do plano passarem).

  > Importante: isso acontece somente para testes que pertencem a planos de longa duração. Testes avulsos (fora desses planos) não geram tickets automáticos.
* O acompanhamento é sempre dado por uma **combinação**, que passa a ser acompanhada de forma automática apenas a partir do segundo módulo de teste de longa duração (o módulo inicial é controlado manualmente pela AOPF):
  * **Authorisation Server Id (ASId) + Nome padronizado do plano de testes + tipo (PF ou PJ)**
* A decisão “existe ticket aberto?” vem sempre de uma nova consulta ao Service Desk ao final do teste com falha ou ao final do último teste agendado, e não de um banco interno.
  * Utilizar um banco de dados interno para atrelar atualizações apenas a um ticket original era um comportamento antigo da ferramenta, atualizado em 19/02/2026.
  * Pode haver mais de um ticket por combinação. Nesse caso, todos são atualizados/encerrados pela automação.
* Como acessar o Test Manager: [https://scheduler.fvp.directory.openbankingbrasil.org.br/](https://scheduler.fvp.directory.openbankingbrasil.org.br/#)

---

## **Como funciona (fluxo em 4 etapas)**

#### **1) Preparação (quando o teste é criado/agendado)**

* **O que o sistema faz:** identifica que o teste pertence a um plano de longa duração e guarda internamente os dados da combinação (ASId, nome do plano de teste, tipo).
* **O que você vê:** nada muda no Service Desk (nenhum ticket é criado/alterado nessa etapa).

#### **2) Abertura de ticket (falhou e não há ticket aberto para a combinação)**

* Quando o teste termina com falha, o sistema checa se já existe ticket aberto para a mesma **combinação**:
  * ASId
  * Plano de testes
  * Tipo (PF ou PJ)
* Se não existir, ele abre um ticket novo com título/descrição padrão e link do teste que falhou.
* **O que você pode esperar:**
  * Na próxima execução do módulo que falhou, o Test Manager vai realizar nova consulta ao Service Desk e passar a alimentar todos os tickets abertos contendo a mesma combinação.

#### **3) Alimentação do ticket (falhou e já existe ticket aberto para a combinação)**

* Se o teste falhar e já existir um ou mais tickets abertos para aquela combinação, o sistema não abre outro. Ele atualiza os tickets existentes, adicionando uma nota com texto padrão e o link do teste que acabou de falhar.
* **O que você pode esperar:**
  * Falhas seguintes do mesmo plano viram notas no mesmo ticket, mantendo histórico e evidências atualizadas em todos os tickets que contêm a mesma combinação.

#### **4) Fechamento automático (quando todos os testes do plano passam)**

* Quando um teste passa e o sistema identifica que ele é o último do plano (isto é, todos os testes do plano já rodaram e passaram), ele:
  * Faz nova consulta ao Service Desk
  * Fecha todos os tickets da mesma combinação com status diferente de encerrado, ou seja, ainda abertos no Service Desk
  * Encerra o acompanhamento daquela combinação (na próxima rodada do plano, o ciclo recomeça)
* **O que você pode esperar:**
  * Se o teste passou, mas ainda não é o último do plano, os tickets relativos ao primeiro módulo, caso existam, permanecem abertos.

---

## **Cenários possíveis/comuns**

* **Várias falhas seguidas no mesmo plano de teste**
  * A primeira falha abre o ticket, caso não haja um ticket com a mesma combinação anteriormente aberto. As demais entram como notas em todos os tickets abertos para aquela combinação.
* **Um teste passou, mas ainda faltam outros do plano**
  * Os tickets daquela combinação não serão fechados até o último teste do plano passar.
* **Ticket original fechado manualmente antes da conclusão do plano**
  * Na próxima falha, o sistema consultará novamente o Service Desk, coletando todos os tickets abertos com o critério da mesma combinação.
    * Se houver algum aberto, atualizará todos com a evidência de falha.
    * Se não houver nenhum aberto, abrirá um novo ticket com a evidência de falha.
  * No próximo sucesso, o sistema consultará novamente o Service Desk, coletando todos os tickets abertos com o critério da mesma combinação:
    * Se houver algum aberto, encerrará todos com evidência de sucesso e removerá a combinação do registro interno (instituição + plano + tipo)
    * Se não houver nenhum aberto, apenas removerá a combinação do registro interno (instituição + plano + tipo).
* **Service Desk/integração fora do ar na falha**
  * O sistema não reprocessa sozinho (sem retry). Em uma próxima falha/sucesso do teste, o sistema tentará novamente alimentar/encerrar o ticket.
* **Exceções (blacklist)**
  * Alguns planos podem estar em lista de exceção; nesses casos, o sistema **não abre nem atualiza** tickets, mesmo com falha.

---

## **Logs dos módulos de teste**

**Feature adicionada em 19/02/2026:**

Depois de cada interação com o Service Desk (ao terminar um teste de plano de longa duração), o scheduler passa a escrever no log do próprio teste da FVP um bloco "ServiceDesk integration" com:

**1) Sucessos (INFO)**

* Mensagens que indicam o que foi feito e incluem o(s) ID(s) do SR quando houver:
  * **Abertura:** Servicedesk: Opened new SR: \<id\>
  * **Atualização (nota):** Servicedesk: Updated SRs: \<id1\>, \<id2\>, ...
  * **Fechamento:** Servicedesk: Closed SRs: \<id1\>, \<id2\>, ...

**2) Falhas (WARNING)**

* Quando houver erro ao acessar o Service Desk (abrir, atualizar ou fechar), o log do teste registra WARNING com a ação e o motivo:
  * Ex. 1: Servicedesk: Failed to open SR: HTTP 500 - \<corpo da resposta\>
  * Ex. 2: Servicedesk: Failed to update SR 12345: \<mensagem da exceção\>
  * Ex. 3: Servicedesk: Failed to close SR 12345: ...
* Em falhas de HTTP usa-se status e corpo. Nos demais casos, a mensagem da exceção.

**Onde aparece:**

* No event log do teste, abaixo do sumário, dentro do bloco "ServiceDesk integration".
* Assim, ao abrir o log daquele teste, será possível ver:
  * Se houve sucesso e qual o número de ticket foi aberto, quais foram atualizados ou quais foram fechados (com ID)
  * Ou se houve falha e qual ação falhou (e, quando aplicável, em qual SR e com qual HTTP/erro).

---

Caso deseje enviar sugestões/dúvidas, reportar inconsistências ou discutir qualquer ponto deste documento, por gentileza utilize a página de Issues no GitLab: https://gitlab.com/groups/raidiam-conformance/open-finance/-/issues.

---

*Conteúdo baixado em 16/09/2026, 15:38:38*
