# Erros comuns nos testes

## **Erros de acesso e sessão**

-   **Access Denied:** usuário cadastrado no diretório de produção, mas sem associação aos perfis necessários (PFVPC e Certification Manager).
    

Solução: solicitar ao suporte da Raidiam a validação do cadastro e a inclusão do e-mail no perfil Certification Manager.

![att\_0\_for\_2064974092.png](images/att_0_for_2064974092.png)

-   **Failed to fetch:** timeout de sessão após inatividade prolongada ou troca de abas. Solução: acionar "Close" e recarregar a página para restabelecer a sessão.
    

![att\_1\_for\_2064974092.png](images/att_1_for_2064974092.png)

-   **Error:** um ou mais campos obrigatórios não preenchidos na configuração do plano.
    

Solução: verificar e completar todos os campos obrigatórios.

![att\_2\_for\_2064974092.png](images/att_2_for_2064974092.png)

-   **HTTP Error 403:** pode ocorrer durante o redirecionamento, sem impacto funcional.
    

Solução: clicar em "Close" e prosseguir; se não retomar, recarregar a página.

## **Mensagens de erro nos logs**

Mensagens frequentes nos logs, com o motivo e a solução recomendada.

**40x no DCR — "Client already present for this Software Statement on Server"**

Problema: o servidor não aceita novo DCR porque já existe um client\_id para esse Software Statement. O client foi criado em um módulo anterior e a solicitação de exclusão foi recusada pelo servidor.

Solução: verifique o plano e confirme se a solicitação DELETE falhou em algum módulo. Se sim, corrija a causa e exclua manualmente o client usando o SoftwareStatementID. Se não, o problema ocorreu em teste anterior; exclua manualmente o client e aguarde a próxima execução.

**"Test was unable to call the Consents API on test"**

Problema: no teste consents-bad-logged, não foi possível chamar a API POST Consents porque o URI da API de Consentimento não foi fornecido no plano.

Solução: verifique no diretório se o Authorisation Server está registrado com uma API de Consentimentos válida para a Fase 3 e/ou Fase 2. Consulte o Guia Operacional do Diretório para registrar a API de Consentimentos no servidor.

**"DCR is not being accepted because of missing optional fields on the request"**

Problema: o servidor recusa o DCR porque um campo opcional não foi incluído no corpo da solicitação.

Solução: o servidor deve aplicar um padrão suportado para todos os campos opcionais, garantindo o processamento da solicitação.

**"Routine was unable to confirm within the well-known endpoint the supported token authentication methods"**

Causas potenciais: Well-Known com certificados SSL inválidos; response\_body sem private\_key\_jwt ou tls\_client\_auth em token\_endpoint\_auth\_methods\_supported; servidor negou acesso da FVP ao verificar o Well-Known.

Solução: use certificado SSL EV válido de CA ou ICP-Brasil; garanta conformidade com o RFC8414; verifique se o payload JSON contém os métodos de autenticação de token esperados.

**"Server claims the authorization token is invalid or expired"**

Problema: o servidor não está aceitando tokens de acesso válidos (problema de sincronização no cache de tokens entre instâncias do authorisation server).

Solução: implementar estratégia de fallback para consultar o token no banco de dados quando não encontrado no cache.

**"Failure when calling the directory endpoints - Token or Assertion"**

Problema: o diretório retornou erro 50x devido ao alto uso da plataforma durante o teste.

Solução: nenhuma mudança é necessária; ignore os resultados e aguarde nova execução.

**"Server returned that the client presented invalid certificates"**

Problema: em todas as solicitações de DCR, o servidor retorna as credenciais do client como inválidas.

Solução: certifique-se de que o API Gateway confia no certificado e na CA emissora.

**"State was passed in request, but is missing from response"**

Problema: ocorre no redirecionamento de volta à FVP quando o usuário não está logado no navegador padrão do dispositivo móvel — as informações da URL de redirecionamento se perdem, pois o link é único.

Solução: em execuções via QR Code, autentique-se previamente no navegador móvel que será utilizado, antes de iniciar o teste, para garantir a transmissão correta dos parâmetros.

## **Suporte e Dúvidas Adicionais**

Caso a instituição tenha dúvidas ou apontamentos de irregularidades, aconselhamos que realizem a abertura de um ticket de Solicitação de Informações via Service Desk: Solicitação de Serviço → Solicitação de Informações → Conformidade → Ferramenta de Validação em Produção (FVP).
