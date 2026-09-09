# API Consents: fluxo básico do consentimento

Fluxo detalhado do GT Segurança disponível em: **https://openbanking-brasil.github.io/specs-seguranca/tpp-user-guide-ptbr.html#AcessoClientes**










## **8. Status do consentimento 7. Consulta do** **consentimento**


## **6. Geração do Access Token 5. Autenticação e** **Confirmação**



**Transmissora** respondendo
com o status do consentimento
como “autorizado”



**Receptora** consulta o status do
consentimento através do
**GET/consents/v1/consents/**
**{consentId}**



**Transmissora** utiliza do
_authorization-code_ para gerar

- _Access Token_ para possibilitar

- acesso aos dados pela
receptora



**Usuário** se autentica, seleciona
as origens e confirma as
informações do consentimento
na transmissora


