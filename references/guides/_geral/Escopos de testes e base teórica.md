# Escopos de testes e base teórica

## **Escopo de testes**

Executada automaticamente todos os dias às 04:00, a FVP Automática realiza testes de conformidade nos servidores de autorização selecionados e comunica eventuais falhas à instituição por meio de tickets no Service Desk.

São executados testes que não exigem interação do usuário, como validações de DCR, FAPI, testes funcionais e verificações de cadastros no Diretório. Esses testes também podem ser executados na FVP Manual. No entanto, algumas validações disponíveis na FVP Automática não estão disponíveis na FVP Manual.

## **Acompanhamento e comunicação de falhas**

A instituição pode acompanhar, por meio do Service Desk, os tickets abertos em decorrência das falhas identificadas durante a execução da FVP Automática.

Caso seja identificada pelo menos uma falha, será aberto um ticket contendo os resultados dos testes executados, as respectivas evidências e os módulos que ocasionaram a abertura do ticket. O ticket também poderá apresentar os módulos que estejam em manutenção e que, por esse motivo, não devem ser considerados na análise da execução.

O conteúdo do ticket seguirá o modelo abaixo:

_Foram identificadas uma ou mais falhas nos testes de **{tipo}** da FVP Automática, executados em **{started}**, no servidor de autorização da instituição._

_**Evidências:** {link}_

_**Módulos que ocasionaram a abertura deste ticket:**_

-   _{módulo 1}_
    
-   _{módulo 2}_
    

_**Módulos em manutenção, que não influenciam este ticket:**_

-   _{módulo 1}_
    
-   _{módulo 2}_
    

_Os módulos listados em manutenção devem ser desconsiderados na análise dos resultados da execução realizada em **{started}**._

Após avaliar as falhas identificadas, caso seja necessário repetir os testes antes da próxima execução da FVP Automática, a instituição poderá executar o plano **“Automatic FVP Mirror - Open FVP”**, disponível na **FVP Manual**.

Caso não sejam identificadas falhas na execução, nenhum ticket será aberto no Service Desk.

## **Descoberta no Diretório e geração dos planos**

Para iniciar a execução dos testes automatizados, a FVP consulta o Diretório e monta os planos de teste em três etapas:

1.  Consulta à API pública do Diretório
    

A FVP lê a resposta JSON e extrai, para cada organização registrada:

-   ID da Organização
    
-   Nome da Organização
    
-   Lista de servidores de autorização
    
-   URL do Well-Known
    
-   Customer Friendly Name
    
-   ID do Authorisation Server
    
-   URI de Consents
    
-   Processamento dos Well-Known
    

2.  Em seguida, consulta o endpoint Well-Known de cada servidor de autorização e atualiza as informações obtidas:
    

-   Métodos de autorização suportados (chave privada ou mTLS)
    
-   Se o PAR é suportado e se é obrigatório.
    
-   Geração dos planos de teste
    

3.  Com essas informações, cria um plano de teste para cada cenário válido. O número de planos por servidor é:
    

-   software statements × variantes de autorização suportadas
    

Exemplo: um Authorisation Server com 2 variantes, testado com 2 software statements, gera 4 planos válidos.

## **Clients de testes**

Cada execução da FVP registra um client (DCR) no início e o excluí ao final. Quando um client remanescente de uma execução anterior não é removido, o próximo DCR falha ("Client already present for this Software Statement"). Por isso, é responsabilidade da instituição checar e excluir diariamente os clients remanescentes — exceto os de testes de longa duração. (ver 3.2 – Erros comuns)

### **Software Statements cujos clients DEVEM ser deletados**

-   bcc3ba64-faf5-456c-a162-8fef7ee67170
    
-   bc97b8f0-cae0-4f2f-9978-d93f0e56a833
    
-   70ee2970-038b-44d6-9300-d3af3a890154
    
-   21ef921f-7d9f-4fa5-afae-d24545d6c880
    
-   f61e3065-ca7b-4982-8ff5-86dff43ece63
    
-   d52c9049-a67b-432f-bdde-fe613099f83b
    

_Reforçamos que, para os software statements cujos clients devem ser deletados, a exclusão deve ser feita preferencialmente entre 13h e 02h, a fim de evitar interferências na execução dos testes conduzidos pela Associação Open Finance._

### **Software Statements cujos clients NÃO devem ser deletados**

Usados em testes de longa duração, o mesmo ClientId é reaproveitado. Não delete nem altere. Se caso apague por engano, siga o Fluxo de deleção de clients.

-   44ffd907-2318-496b-ad91-07bbb0a836da - Testes de Pagamentos
    
-   25402dd0-7553-477b-b635-b9ce79da18f2 – Teste de Portabilidade de Crédito
    

Para mais detalhes sobre os testes e suas validações, visite a página Testes e Validações.
