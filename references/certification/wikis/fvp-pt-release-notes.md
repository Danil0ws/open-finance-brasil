# Release Notes

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/PT/Release-Notes](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/PT/Release-Notes)
**Slug:** `FVP/PT/Release-Notes`

---

---
title: Notas de versão
---

[← FVP](FVP/PT)

# FVP - Notas de versão da ferramenta

Esta página reúne as notas de versão da FVP, registrando as mudanças relevantes na ferramenta e nos planos de teste. As entradas estão agrupadas por ano, da mais recente para a mais antiga; cada ano fica recolhido e abre ao ser clicado.

<details>
<summary>2026 - 16 alterações</summary>

**21/08 · Planos** - Plano de ponta a ponta de pagamentos Aberta v4 retirado

O plano de ponta a ponta de pagamentos na modalidade Aberta deixou de ser oferecido na versão 4. Com a Restrita retirada em agosto, a versão 4 não é mais oferecida em nenhuma modalidade; a versão 5 segue disponível nas duas.

**21/08 · Planos** - Agendamento sem redirecionamento passou a validar Pagamentos v5

No plano de agendamento de pagamentos da jornada sem redirecionamento (Enrollments v2.2.0, Restrita), os dois módulos passaram a conferir o consentimento e o pagamento contra a versão 5 da API de Pagamentos, e seus nomes terminam em v5.

**13/08 · Comportamento** - Falha ao obter as raízes do Diretório é reportada como problema do Diretório

Na validação da cadeia de certificados, quando as raízes do Diretório não podem ser obtidas o teste falha apontando o Diretório. As raízes são lidas uma vez e reaproveitadas ao longo da execução.

**04/08 · Planos** - Plano de ponta a ponta de pagamentos Restrita v4 retirado

O plano de ponta a ponta de pagamentos na modalidade Restrita deixou de ser oferecido na versão 4. A versão 5 segue disponível nas duas modalidades, e a versão 4 continua disponível na modalidade Aberta.

**29/07 · Logs** - Bloco de Service Desk no log do teste

Cada execução passou a trazer um bloco próprio de Service Desk no log do teste. Ele mostra a busca por chamados, com quantos candidatos ela retornou, quais são do mesmo Authorization Server e quais sobraram depois dos filtros de módulo executado, segmento e status; cada chamada feita ao Service Desk, com método, endereço, corpo, código de retorno e tempo de resposta; e o resultado da ação, com o número do chamado aberto, atualizado ou encerrado. A última linha resume a execução em Authorization Server, marca, módulo, segmento, horário e ação tomada. Quando a execução não movimenta chamado, a linha diz o motivo, e o bloco só aparece quando houve contato com o Service Desk.

**15/07 · Mensagens** - Leitura das raízes do Diretório mais tolerante

A validação da cadeia de certificados passou a aceitar a resposta das raízes do Diretório em formato de lista e a encerrar o módulo com mensagem clara quando a resposta não pode ser interpretada.

**13/07 · Documentação** - Documentação da FVP reformulada

A documentação da FVP foi reorganizada em páginas por plano, em português e inglês, com uma planilha por plano.

**09/07 · Formulário** - Formulário de configuração simplificado

O formulário de configuração dos planos deixou de exibir os campos que a FVP não usa ou preenche sozinha (identificação do usuário logado e da pessoa jurídica, discovery e base do Diretório, keystore, publish e alias), ficando restrito aos campos que o participante de fato preenche. Os textos de ajuda de CPF e CNPJ também foram revisados.

**03/07 · Planos** - Planos E2E de pagamentos v5

Os planos de ponta a ponta de pagamentos passaram a contar com a versão 5, nas modalidades Open (Imediato) e Restricted (Agendado), com os módulos correspondentes.

**26/06 · Formulário** - Novos campos de execução no formulário

O formulário de configuração dos planos manuais passou a incluir os campos de execução Tipo, Ciclo e Ticket de Service Desk, usados para identificar execuções de teste e reteste.

**25/06 · Interface** - Encerramento manual de um teste como falho

A ferramenta passou a oferecer um controle para encerrar manualmente um teste como falho, útil quando o ambiente da detentora apresenta um problema que não retorna erro à FVP.

**18/06 · Comportamento** - Execução dos módulos agendados restrita ao agendamento

Os módulos assíncronos da FVP Manual Restrita passaram a ser executados apenas de forma agendada; a execução manual foi bloqueada, evitando disparos fora do fluxo de múltiplos dias.

**18/06 · Planos** - Nomes de exibição dos planos padronizados

Os nomes de exibição dos planos da FVP Manual foram padronizados nas modalidades Open (Imediato) e Restricted (Agendado), tornando a lista mais clara.

**20/04 · Planos** - Jornada Otimizada

A Jornada Otimizada foi adicionada à FVP, com os planos correspondentes de pagamentos e de enrollments.

**03/03 · Planos** - Plano de exclusão de cliente

A FVP Manual passou a oferecer o plano de exclusão de cliente, na modalidade Agendada, cobrindo o encerramento do cadastro do cliente junto à detentora.

**29/01 · Planos** - Planos de jornada sem redirecionamento

Entraram quatro planos da API de Enrollments v2.2.0, que cobrem a jornada sem redirecionamento: pagamentos e pagamentos automáticos, cada um nas modalidades Aberta (Imediato) e Restrita (Agendado).

</details>

---

[↑ FVP](FVP/PT) · [◀ Gerenciamento de Cliente](FVP/PT/Manual/Scheduled/Gerenciamento-de-Cliente) · [Perguntas frequentes ▶](FVP/PT/FAQ)


---

*Conteúdo baixado em 16/09/2026, 15:38:05*
