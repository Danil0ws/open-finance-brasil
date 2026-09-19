# Visão geral do Mock TPP

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Visão-geral-do-Mock-TPP](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Visão-geral-do-Mock-TPP)
**Slug:** `Visão-geral-do-Mock-TPP`

---

[[_TOC_]]

# Objetivo do Mock TPP

O Mock TPP foi projetado e criado pela equipe do Motor de Conformidade para ser tanto uma ferramenta de apoio à execução de testes de Servidores de Autorização (FAPI OP) quanto uma ferramenta de apoio aos TPPs na construção de sua própria solução totalmente funcional. O Mock TPP é fornecido com um código fonte totalmente aberto que pode ser facilmente executado em uma máquina local.

Nesta página, apontamos tanto onde se pode encontrar o código fonte do Mock TPP como também como executá-lo rapidamente localmente a fim de executar testes contra um Servidor de Autorização existente registrado no Sandbox Directory.

# Código-fonte do Mock TPP

O código-fonte para o Mock TPP está hospedado no [Open Banking Applications Example Repo](https://github.com/OpenBanking-Brasil/applications-exemplo/tree/main/tpp-payments-client).

No Diretório do Sandbox do Open Banking, você consegue acessar o Software Statement do Mock TPP [neste link](https://web.sandbox.directory.openbankingbrasil.org.br/organisations/74e929d9-33b6-4d85-8ba7-c146c867a817/softwareStatements/7218e1af-195f-42b5-a44b-8c7828470f5a/softwareStatementView).

O Mock TPP está sendo melhorado pela equipe do Motor de Conformidade, entretanto, se você quiser contribuir para o desenvolvimento desta ferramenta, sinta-se à vontade para levantar qualquer P.R contra o repositório. Da mesma forma, se você tiver qualquer sugestão de melhoria ou se tiver qualquer problema na execução da solução, por favor, levante um problema na [Conformance Suite Issues Page](https://gitlab.com/obb1/certification/-/issues)

# Quick Start - Rodando o Mock TPP

## O que é necessário para rodar:

Docker

MongoDB

Vue

NPM (node package manager)

Node v16 (preferencialmente)

Para ajudar com o início, também gravamos um [Quick Start 6 Minutes video](https://youtu.be/bq3GfShkO_A) mostrando o processo de ponta a ponta da execução do Mock TPP

## Rodando pela primeira vez

**(1) Adicione uma entrada de DNS local no seu arquivo hosts:**

**Para poder executar com sucesso o Mock TPP localmente, você precisa adicionar uma entrada DNS ao seu host local.**

**Para o MacOS:**

1. Abra o terminal
2. Digite: sudo nano /private/etc/hosts
3. Insira a sua senha

**Para o Windows 8/10:**

1. Pressione a tecla Windows.
2. Digite Notepad no campo de busca.
3. Nos resultados da busca, clique com o botão direito do mouse no Bloco de Notas e selecione Executar como administrador.
4. No Bloco de Notas, abra o seguinte arquivo: c:\\Windows\\System32\\Drivers\\etc\\hosts

**Após abrir o arquivo de hosts:**

4. Você deve ver a configuração atual de seus hosts. Desça com a tecla 'baixo' até chegar à parte 127.0.0.1 e vá logo após o "localhost".
5. Você deverá adicionar as entradas abaixo no seu arquivo.

```
127.0.0.1   tpp.localhost
127.0.0.1   mongo1
127.0.0.1   mongo2
127.0.0.1   mongo3
```

6. Salvar o arquivo: Pressione "Ctrl + O" para escrever e "Ctrl + X" para sair no MacOS ou simplesmente salvar normalmente no Windows

No final, deverá ficar como a imagem abaixo (exemplo para um Mac):

![image](uploads/dd6fccbec47afd20ec94333d3b1b08e1/image.png)

**(2) Instale os pacotes necessários:**

Dentro do folder tpp-payments-client, abra uma janela do terminal e execute

```
npm install
```

Isto instalará todos os pacotes necessários para rodar o projeto

**(3) Execute o Mock TPP:**

Rode o Docker na sua máquina e depois disso, abra uma janela do terminal e digite:

```
docker-compose up
```

Agora, dentro da pasta applications-exemplo/tpp-payments-client, digite:

```
npm run start
```

_Isto executará um script que executará tanto o front-end quanto o backend juntos_

Se você quiser executá-las separadamente, abra duas janelas de terminal e corra:

Backend:

```
DEBUG=tpp* node index.js
```

Frontend:

```
npm run serve
```

**(4) Permitindo que seu navegador execute o código:**

- Depois de compilá-lo com sucesso, abra uma janela do navegador para https://tpp.localhost e seu navegador lhe pedirá para perguntar se você confia neste site - pressione sim.

**(5) Abertura da tela inicial do Mock TPP:**

- Abra uma janela para https://tpp.localhost:8080/ e você poderá selecionar se deseja Dados do Cliente ou Pagamentos

## Executando o Mock TPP:

Se você já passou pela configuração anterior, você só precisa executar o seguinte comando dentro da pasta tpp-payments-client:

```
npm run start
```

Isto executará o Mock TPP

# Configuração do Mock TPP

O Mock TPP vem povoado com um conjunto existente de credenciais para um S.S. que está registrado no ambiente Sandbox. O usuário pode optar por atualizar estas credenciais junto com algumas variáveis operacionais antes de executar o Mock TPP para ter certeza de que ele vai usar credenciais que foram definidas para funcionar contra uma determinada implementação.

A visão de configuração está dividida em:

- Authorization and Message Settings
- Software Statement Settings
- Mock TPP Settings

### Atualizando os certificados

Você pode adicionar seus próprios certificados pressionando o botão "Configurações" na visualização inicial e depois indo para "Configurações de Declaração de Software".

![image](uploads/9c1df2b244dec555eb9e697fe65d0363/image.png)

O Mock TPP espera as chaves privadas e públicas dos certificados de Assinatura (BRSEAL) e de Transporte (BRCAC) e também o arquivo da Autoridade Certificadora

- ca.pem
- signing.key
- signing.pem
- transport.key
- transport.pem

Ao atualizar os certificados no arquivo de configuração, certifique-se de usar os mesmos nomes ao carregá-los.

![image](uploads/8c2b4a071d34abbde199ca758a447bc0/image.png)

![image](uploads/c3fd4bedf90cfcb58ca0a17e90f7d6d0/image.png)

### Configuração de outros parâmetros

Todas as configurações podem ser alteradas no menu Configurações. O Mock TPP foi criado para poder ser executado e executado por qualquer instituição registrada no Diretório.

É possível alterar os detalhes do cliente e os detalhes do aplicativo para o que se deseja testar

![image](uploads/8d98f081f72e9a82ef8ecef5008f1e1a/image.png)

---

*Conteúdo baixado em 16/09/2026, 15:38:45*
