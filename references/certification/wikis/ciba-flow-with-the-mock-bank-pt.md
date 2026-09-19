# CIBA Flow with the Mock Bank (PT)

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/CIBA-Flow-with-the-Mock-Bank-(PT)](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/CIBA-Flow-with-the-Mock-Bank-(PT))
**Slug:** `CIBA-Flow-with-the-Mock-Bank-(PT)`

---

---
title: Fluxo CIBA com o Mock Bank
---
CIBA (Client Initiated Backchannel Authentication) é um fluxo de autorização desacoplado: em vez de mandar o usuário por um redirect no navegador, o pedido de autenticação é entregue por fora e aprovado em um canal separado. Neste guia, a **suíte de conformidade da Raidiam** faz o papel do cliente (o receptor) e o **Mock Bank** faz o papel do OpenID Provider e detentor de dados. A entrega do token é por **ping**.

Esta página traz orientações para o **happy path** do CIBA: o fluxo assíncrono limpo, sem fallback. A suíte registra um cliente CIBA para você a cada execução (DCR dinâmico) a partir da sua software statement, e o apaga no final, então você nunca registra um cliente na mão. Como a suíte não dirige um navegador, o consentimento é aprovado **na mão, na tela do Mock Bank**: o plano pausa e espera uma pessoa aprovar o pedido.

## 1. O que adicionar na sua software statement

Este guia assume que você já tem uma organização no diretório sandbox e uma software statement que você usa em outros planos. Você só adiciona o que o CIBA precisa. Você não cria uma statement nova, e não faz o DCR você mesmo.

- **Roles**: a statement precisa ter `CONTA` e `DADOS`.
- **Redirect URI**: adicione o callback da suíte `https://web.conformance.directory.openbankingbrasil.org.br/test/a/<alias>/callback`. O registro exige um `redirect_uris` não vazio mesmo para um cliente CIBA. O `<alias>` é o valor que você coloca no campo `alias` da configuração do teste.
- **Webhook** (`software_api_webhook_uris`): adicione `https://web.conformance.directory.openbankingbrasil.org.br/test-mtls/a/<alias>`, sem barra no final. A suíte compara esse valor exatamente contra a própria base mTLS antes de rodar. Esse campo guarda um único valor, então uma statement aponta para um ambiente por vez.
- **Certificado de transporte**: use um certificado **BRCAC**. Uma organização com o papel `DADOS` não pode usar um certificado `TRANSPORT` (rtstransport) simples. Gere o BRCAC no diretório e guarde a chave privada: ela vira o seu `mtls.key`, e o certificado emitido vira o seu `mtls.cert`.
- **Backchannel Client Notification Endpoint** (o campo do diretório): deixe **vazio**. A suíte monta o notification endpoint sozinha como `<base mTLS>/cb`, e o Mock Bank aceita esse valor dentro do corpo do DCR.

## 2. Selecione o plano

Entre na suíte de conformidade em `https://web.conformance.directory.openbankingbrasil.org.br/`, selecione o plano de CIBA Customer Data para o happy path (perfil "Phase 2 - Customer Data - API Version 3") e preencha a configuração que ele pedir na UI.

- **Não escolha nenhuma variante.** O plano já fixa as quatro: `openbanking_brazil`, `plain_response`, `private_key_jwt` e `pushed` (PAR). Escolher qualquer uma delas retorna HTTP 400 ("already sets this variant").
- **O DCR é dinâmico.** A suíte registra um cliente CIBA novo a partir da sua software statement a cada execução, adicionando o grant type de CIBA, o modo de entrega ping e o notification endpoint, e apaga esse cliente no final, mesmo quando o teste falha. Você não pré-registra um cliente.

## 3. Rode o teste

Inicie o teste na suíte e aprove na tela do Mock Bank quando o plano pausar (seção 4).

## 4. Aprove na tela do Mock Bank

O plano chega em `WAITING` e pede que você complete a autenticação CIBA. Para aprovar:

1. Espere o status do teste virar `WAITING`.
2. Abra o bloco **Call the backchannel authentication endpoint** no log e copie o `auth_req_id` da resposta do `/bc-authorize`.

   ![image.png](uploads/b3ead387044ef82ef31f61dc653e22c4/image.png){width=526 height=172}
3. Em uma nova aba do navegador, abra:

   ```
   https://auth.mockbank.openbankingbrasil.org.br/ciba/authorize/<auth_req_id>
   ```
4. Faça login como `ralph.bragg@gmail.com` / `P@ssword01`, marque **I consent** e clique em **Confirm Consent**.

> **Timing**
>
> Aprove quando a linha de pendência aparecer no log, não por relógio. Aprovar cedo demais consome o grant durante os polls de pendência e aparece como `invalid_grant`. A janela de aprovação é fixa em 600s (o `requested_expiry` é ignorado).

Depois que você aprova, o Mock Bank manda o ping para a suíte em `POST /cb`, a suíte troca o `auth_req_id` por tokens, confirma que o consentimento está `AUTHORISED` e fica consultando a API de Resources até um recurso voltar. O cliente registrado é então apagado.


---

*Conteúdo baixado em 16/09/2026, 15:37:12*
