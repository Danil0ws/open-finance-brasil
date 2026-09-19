# FAQ

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/PT/FAQ](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/PT/FAQ)
**Slug:** `FVP/PT/FAQ`

---

---
title: Perguntas frequentes
---

[← FVP](FVP/PT)

# FVP - Perguntas frequentes

Esta página reúne as dúvidas mais comuns sobre a FVP, organizadas por tema. As respostas valem tanto para a FVP Manual quanto para a Automática, salvo indicação em contrário.

## Sobre a ferramenta

**O que é a FVP Manual Restrita e qual a diferença dela para a FVP Manual Aberta e a FVP Automática?**

A FVP Automática é executada diariamente, de forma automática, e cobre os testes de DCR, DCM e as verificações de todas as fases até a etapa de autorização do consentimento. A FVP Manual, por incluir a jornada completa de compartilhamento de dados e de iniciação de pagamentos, exige a interação do usuário para autorizar o consentimento e concluir as iniciações. A diferença entre a Manual Aberta e a Manual Restrita está em alguns módulos disponíveis apenas para a estrutura do Open Finance Brasil, como a validação dos limites do usuário.

**Recebi a mensagem "Failed to fetch" na ferramenta. O que isso significa?**

A mensagem "Failed to fetch" está relacionada ao timeout da sessão da FVP, esperado em sessões longas ou após a troca de abas no navegador. O erro não impede a execução do módulo: basta recarregar a página para continuar acompanhando a execução normalmente.

## Notificações e encerramento de tickets

**Recebi um ticket de notificação da FVP Manual Restrita, mas não consigo comentar nem encerrá-lo. O que devo fazer?**

Os tickets de notificação da FVP Manual Restrita não podem ser comentados ou encerrados pela instituição. O encerramento depende de uma reexecução bem-sucedida do módulo, feita exclusivamente pelo fornecedor responsável pelos testes. Para pedir uma reexecução, abra um chamado em Requisição > Reexecução > FVP Manual - Testes restritos. Para dúvidas sobre a FVP, abra em Requisições > Solicitação de Informações > Conformidade > Ferramenta de Validação em Produção.

**Solicitei uma reexecução. Como não tenho nenhuma ação até o retorno do resultado, o SLA do meu ticket será impactado?**

Não. Ao abrir um pedido de reexecução, o ticket passa ao status "Aguardando Requisitante - Essencial". Como a instituição não tem nenhuma ação a realizar enquanto aguarda, a cada 24h o ticket ganha 24h adicionais de SLA. Após o encerramento do pedido, o status volta para "Encaminhado N2 Atendimento" e o SLA volta a ser contado normalmente.

**Em vez dos logs, recebi como evidência um JSON com a mensagem "DCR Error – Failure on generating a client". O que isso quer dizer?**

Em cada execução, a FVP registra um cliente no início (DCR, Dynamic Client Registration) e o exclui ao final, pois não pode reter as informações do cliente e as especificações do Open Finance permitem apenas um cliente por software statement. Quando o registro falha no início, o módulo não chega a ser executado e retorna "DCR Error – Failure on generating a client", acompanhado de um log com o motivo da falha e de um botão para baixá-lo. Enquanto o DCR falhar, o módulo não poderá ser criado.

## Comportamento dos testes

**O teste não chegou ao fim: o status está como "INTERRUPTED" e os logs mostram "Test was interrupted before it could complete". O que significa?**

Essa mensagem tem duas causas. Falha bloqueante: a FVP identificou uma falha que impede as etapas seguintes de validação, por exemplo uma falha no fluxo de autorização, cujo código é essencial para obter o token de acesso. Interrupção espontânea: o responsável pelo teste acionou o botão "stop", em geral ao identificar no ambiente da detentora uma falha que não retorna erro à FVP. Nesse caso, use o xfapi-interaction-id presente nos logs para identificar o erro diretamente no ambiente da detentora.

**O motor fez chamadas de "Delete" de consentimentos ou pagamentos em um momento indevido do teste. Por quê?**

As chamadas de "Delete" fazem parte da etapa de Cleanup. Ao final do módulo, com sucesso ou falha, a FVP exclui os recursos criados durante o teste para não deixar dados armazenados na detentora. Diante de uma falha crítica, o Cleanup pode ser acionado de forma preventiva, antes da conclusão. Se o teste falhou antes de criar o consentimento ou pagamento, o Cleanup pode gerar um erro por não haver recurso a excluir; nesse caso, considere a primeira falha, que interrompeu o teste. O Cleanup costuma incluir "Unregister dynamically registered client", "Deleting consent" e "Patch consents endpoint".

**Após a execução, baixei os logs e eles vieram vazios. Por quê?**

Por segurança, a FVP não armazena as informações usadas no teste: cinco minutos após o término da execução, os logs são apagados automaticamente. Faça o download em até cinco minutos após a finalização do teste; depois disso, o arquivo virá vazio.

## Mensagens de erro comuns

Para apoiar a identificação e a correção das falhas, abaixo estão as mensagens de erro mais frequentes nos logs, com a causa provável e como resolver.

**40x na requisição do DCR - Client already present for this Software Statement on Server**

Problema: o servidor não aceita um novo DCR porque já existe um client_id para esse software statement. O cliente foi criado em um módulo de DCR anterior e a solicitação de exclusão foi recusada, deixando o registro ativo. Solução: verifique se a solicitação DELETE falhou em algum módulo. Se sim, corrija a causa e exclua manualmente o cliente pela chave SoftwareStatementID. Se não, o problema ocorreu em uma execução anterior; exclua o cliente manualmente e aguarde a próxima execução para avaliar a causa.

**Test was unable to call the Consents API on test**

Problema: no módulo consents-bad-logged, a API POST Consents não pôde ser chamada porque o URI da API de Consentimento não foi fornecido no plano de teste. Solução: confirme no Diretório que o Authorisation Server está registrado com uma API de Consentimentos válida para a fase em que a instituição participa. Consulte o Guia Operacional do Diretório.

**DCR is not being accepted because of missing optional fields on the request**

Problema: o servidor recusa o DCR pela ausência de um campo opcional no corpo da solicitação. Solução: o servidor deve aplicar um padrão suportado para os campos opcionais, garantindo o processamento da solicitação.

**Routine was unable to confirm within the well-known endpoint the supported token authentication methods**

Problema: as causas possíveis incluem certificado SSL inválido no Well-Known, ausência de private_key_jwt ou tls_client_auth em token_endpoint_auth_methods_supported, ou negação de acesso da FVP ao Well-Known. Solução: use um certificado SSL EV válido, de CA ou ICP-Brasil; garanta conformidade com o RFC 8414; e confirme que o JSON retornado traz os métodos de autenticação de token esperados.

**Server claims the authorization token is invalid or expired**

Problema: o servidor não aceita tokens de acesso válidos, em geral por dessincronização do cache de tokens entre instâncias do Authorisation Server. Solução: implemente um fallback que consulte o token no banco de dados quando ele não for encontrado no cache.

**Failure when calling the directory endpoints - Token or Assertion**

Problema: o Diretório retornou um erro 50x ao ser chamado, por alto uso da plataforma durante o teste. Solução: nenhuma mudança é necessária; ignore o resultado e aguarde uma nova execução.

**Server returned that the client presented invalid certificates**

Problema: o servidor considera inválidas as credenciais emitidas para o cliente, fazendo todos os testes falharem. Solução: garanta que o API Gateway confia no certificado e na CA que o emitiu.

**State was passed in request, but is missing from response**

Problema: a falha ocorre no redirecionamento de volta à FVP. Se o usuário do teste não estiver logado no navegador padrão do dispositivo móvel, os parâmetros da URL de redirecionamento se perdem quando o navegador pede autenticação, pois o link de redirecionamento é de uso único. Solução: em execuções por QR Code, autentique-se antes no navegador do dispositivo móvel que será usado, garantindo que o redirecionamento preserve os parâmetros.

**Authorization response fragment is empty**

Problema: a resposta do authorization server volta para a FVP no fragmento da URL, a parte depois do #, que existe apenas no navegador e nunca é enviada ao servidor. A FVP fica atrás de um login de infraestrutura, então, se o navegador que conclui a jornada de consentimento não tiver sessão válida na FVP no momento do retorno, o gateway força o login e o fragmento se perde nesse desvio. Sem os parâmetros, o módulo não tem o que validar. A mensagem "State was passed in request, but is missing from response" tem a mesma origem. Solução: a mensagem continua com o diagnóstico daquela execução, e é ele que diz de que lado está a correção. Os itens seguintes explicam cada variação, que aparece somente em inglês na ferramenta. Na maioria dos casos basta fazer login na FVP no próprio navegador que conclui a jornada, imediatamente antes de escanear o QR Code: o login dura 10 minutos a partir do momento em que você loga naquele navegador.

**Authorization response fragment is empty: the browser that returned from the authorization server had no previous FVP session**

Problema: o navegador que voltou do authorization server nunca havia acessado a FVP, ou seja, não estava logado. É o caso típico de quem está logado no desktop e escaneia o QR Code com o celular sem ter logado na FVP no celular. O gateway não reconhece o navegador, força o login e o fragmento se perde nesse desvio. Solução: a correção é do lado de quem testa e é imediata. Faça login na FVP no navegador que conclui a jornada de consentimento, no celular antes de escanear o QR Code, e rode o teste novamente.

**Authorization response fragment is empty even though the browser's FVP login was still valid when it returned**

Problema: o navegador voltou com a mesma sessão que já tinha, sem nenhuma autenticação nova. Não houve desvio de login, portanto nada foi descartado do lado da FVP: o fragmento chegou vazio porque veio vazio. Solução: é a única variação que aponta para fora da FVP. Verifique o redirecionamento do authorization server da detentora, que provavelmente devolveu a resposta sem os parâmetros esperados no fragmento da URL.

**Authorization response fragment is empty: the browser's FVP login most likely expired during the consent journey**

Problema: o navegador já tinha sessão na FVP, mas voltou com um login novo, isto é, o login venceu no meio da jornada de consentimento e o gateway pediu autenticação outra vez. O fragmento se perde no mesmo desvio de login. Solução: também é do lado de quem testa, mas por tempo, não por esquecimento, e a correção é de sequência, não de configuração. O login dura 10 minutos a partir do momento em que você loga naquele navegador: faça login imediatamente antes de escanear o QR Code e conclua a jornada dentro dessa janela.

**Authorization response fragment is empty, although the returning browser was already logged in to the FVP**

Problema: sabe-se que o navegador já havia acessado a FVP, mas não é possível afirmar se o login foi renovado no retorno. Acontece quando o registro de referência não está disponível, por exemplo depois de um reinício do serviço, ou quando aquele navegador não fez nenhuma requisição além do próprio retorno desde então. Solução: a mensagem apresenta duas hipóteses e é deliberadamente sem veredito, para não gerar acusação sem base. Trate primeiro a expiração do login, que é a mais provável e está sob controle de quem testa: refaça o teste logando na FVP imediatamente antes de escanear o QR Code e conclua a jornada dentro dos 10 minutos. Se a falha persistir com essa janela respeitada, investigue o redirecionamento do authorization server.

**Authorization response fragment is empty. Ensure the mobile browser is authenticated to FVP before starting the test.**

Problema: é a forma genérica da mensagem, emitida quando não há informação alguma sobre o login do navegador porque a requisição não passou pelo gateway da FVP. Aparece majoritariamente no Motor de Conformidade, e não na FVP, e vale como aviso, não como diagnóstico. Solução: garanta que o navegador do celular esteja autenticado na FVP antes de iniciar o teste. Se o problema persistir, feche todas as abas da FVP, reinicie o navegador, faça login novamente e escaneie o QR Code outra vez, ou use uma aba privada ou anônima.

---

[↑ FVP](FVP/PT) · [◀ Notas de versão](FVP/PT/Release-Notes)


---

*Conteúdo baixado em 16/09/2026, 15:37:54*
