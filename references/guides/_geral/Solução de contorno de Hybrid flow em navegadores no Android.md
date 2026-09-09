# Solução de contorno de Hybrid flow em navegadores no Android

Algumas instituições receptoras/iniciadoras reportaram um problema que ocorre especificamente na utilização do fluxo _web-to-app_ quando a parte web se inicia via Google Chrome, ou navegadores semelhantes, em dispositivos Android. ​

Este problema acontece porque o Google Chrome, no momento de redirecionamento para o aplicativo da instituição detentora/transmissora, realiza uma pré validação do link de redirecionamento, e essa pré validação acaba "queimando" a URL de _request\_uri_. Essa "queima" acontece porque segundo a RFC 9126, sessão 4, é recomendado que a URL _request\_uri_ seja de uso único, portanto uma segunda chamada a ela deveria ser invalidada. Esta recomendação combinada com o comportamento do Google Chrome em dispositivos Android causa um problema na experiência do usuário, pois o mesmo fica impossibilitado de completar a aprovação do consentimento. ​

Para contornar este problema, foi encontrada uma solução que pode ser aplicada diretamente pelos receptores/iniciadores e este contorno está documentado no video abaixo. Essa solução se baseia na criação de um _intent_ com base no _package_ da aplicação da instituição transmissora/detentora para que o redirecionamento ocorra diretamente para o aplicativo sem requisição “_pre flight_” realizadas pelo próprio navegador Chrome.

**Demonstração da implementação da solução**
