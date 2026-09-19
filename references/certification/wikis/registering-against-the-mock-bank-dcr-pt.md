# Registering against the Mock Bank (DCR) (PT)

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Registering-against-the-Mock-Bank-(DCR)-(PT)](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Registering-against-the-Mock-Bank-(DCR)-(PT))
**Slug:** `Registering-against-the-Mock-Bank-(DCR)-(PT)`

---

## Fazendo o registro da aplicação criada com o Mock Bank

[Versão em inglês disponível aqui](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Registering-against-the-Mock-Bank-%28DCR%29)

Assumindo que todos os passos apresentados na [página anterior](https://gitlab.com/obb1/certification/-/wikis/Discovery-of-the-Mock-Bank) foram feitos corretamente, o cliente consegue agora executar um DCR contra o Mock Bank. As etapas feitas na página anterior estão anotadas abaixo:

1. Criou uma Declaração de Software (S.S.) no ambiente Sandbox
2. Atribuiu os papéis regulatórios necessários a esta S.S.
3. Obteve as chaves relacionadas aos certificados BRCAC e BRSEAL emitidos pela PKI do ambiente Sandbox do Diretório
4. Obteve os detalhes do Mock Bank no Diretório de Participantes

A especificação de Segurança existente fornece um guia completo relacionado ao processo de DCR que pode ser encontrado no [Capítulo 3 do Guia TPP - Registering the application with a provider](https://github.com/OpenBanking-Brasil/specs-seguranca/blob/main/tpp-user-guide.md#30-registering-the-application-with-a-provider). Este guia foi construído com base nas [Especificações de DCR do Open Banking Brasil](https://github.com/OpenBanking-Brasil/specs-seguranca/blob/main/open-banking-brasil-dynamic-client-registration-1_ID2.md#regulatory-roles-to-openid-and-oauth-20-mappings) e deve ser seguido pelo usuário para permitir que o cliente realize um DCR contra o Mock Bank

O Mock Bank está configurado, [e também foi certificado](https://openid.net/certification/#FAPI_OPs), para suportar todas as 4 variações FAPI Brasil (private_key/mtls) e (by_value/par). Isto significa que qualquer TPP que suporte uma das variações da FAPI Brasil não deve ter nenhum problema de conexão com o Mock Bank.

A execução de um DCR contra o Mock Bank também pode ser vista no vídeo [Mock Bank - Execute a DCR](https://www.youtube.com/watch?v=9e0CVxsAVwA&t=2s&ab_channel=OpenBankingBrasil)

## Exemplo de um DCR feita contra o Mock Bank

Para garantir que todos os Servidores de Autorização no Escopo do Open Banking estejam seguindo corretamente as especificações de segurança e DCR, a estrutura inicial encomendou, juntamente com a Open ID Foundation, [planos de teste para as normas brasileiras](https://openid.net/fapi-op-conformance-testing-certification-submission-overview-for-open-banking-brazil/). Estes testes não só permitem que as Instituições testem suas implementações, certificando-se de que estão em conformidade com as especificações, mas também servem como uma forma de a autoridade central garantir que nenhuma Instituição será capaz de compartilhar dados sem estar em conformidade.


A execução destes testes cria logs públicos que podem ser revisados por qualquer pessoa interessada nas etapas que neles existam. 

Podemos então aproveitar esta ferramenta para executar corretamente um DCR contra o Mock Bank. Na execução do teste [fapi1-final-final-brazildcr-happy-flow contra o Mock Bank](https://www.certification.openid.net/log-detail.html?log=l7dSstpmBVFxGbW&public=true), é possível verificar todas as etapas envolvidas na execução correta de um DCR contra o Mock Bank.

No site da Open ID Foundation, também é possível consultar todos os testes executados contra todas as instituições que estão atualmente no Open Banking. Esta informação é exibida na [Página de Certificação FAPI OP Certification](https://openid.net/certification/#FAPI_OPs) e também inclui todos os testes FAPI realizados contra o Mock Bank



---

*Conteúdo baixado em 16/09/2026, 15:38:27*
