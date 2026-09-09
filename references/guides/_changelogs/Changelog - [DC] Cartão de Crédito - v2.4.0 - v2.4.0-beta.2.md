# Changelog - [DC] Cartão de Crédito - v2.4.0 - v2.4.0-beta.2

## GET /accounts/{creditCardAccountId}/limits

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data

Alterado - "description"

Alteração

\[Restrição\] O envio dos dados de limites deve seguir as seguintes orientações:

-   A lista vazia deve ser interpretada como a ausência da informação;
    
-   Cenário de limite com valor zerado, deve ter um registro explícito informando o valor como zero;
    
-   Cenário de "cartão sem limite", isto é, cartões em que o uso do limite é flexível, deve ser informado em um registro explícito com isLimitFlexible como true;
    
-   Os limites globais devem ser compartilhados na lista de limites, definidos pelo enum CONSOLIDADO, no campo consolidationType. Limites já incluídos no global não devem ser compartilhados, para não ocorrer redundância de informações;
    
-   Limites segregados, que não fazem parte do global, devem ser compartilhados pelo enum INDIVIDUAL, no campo consolidationType.
    
-   Cartões virtuais, só devem ter seu limite listado caso o limite do mesmo for segregado do global, assim, devem ser compartilhados pelo enum INDIVIDUAL, no campo consolidationType.
    
-   Só devem ser compartilhados limites de cartões ativos.  
    

  

\[Restrição\] O envio dos dados de limites deve seguir as seguintes orientações:

-   A lista vazia deve ser interpretada como a ausência da informação;
    
-   Cenário de limite com valor zerado, deve ter um registro explícito informando o valor como zero;
    
-   Cenário de "cartão sem limite", isto é, cartões em que o uso do limite é flexível, deve ser informado em um registro explícito com isLimitFlexible como true;
    
-   Os limites globais devem ser compartilhados na lista de limites, definidos pelo enum CONSOLIDADO, no campo consolidationType. Limites já incluídos no global não devem ser compartilhados, para não ocorrer redundância de informações;
    
-   Limites segregados, que não fazem parte do global, devem ser compartilhados pelo enum INDIVIDUAL, no campo consolidationType.
    
-   Cartões virtuais, só devem ter seu limite listado caso o limite do mesmo for segregado do global, assim, devem ser compartilhados pelo enum INDIVIDUAL, no campo consolidationType.
    
-   Só devem ser compartilhados limites de cartões ativos. Exclusivamente no caso de contas cartões canceladas, enviar lista vazia.
