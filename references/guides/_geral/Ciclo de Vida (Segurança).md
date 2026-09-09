# Ciclo de Vida (Segurança)

## Etapas do Ciclo de vida dos Documentos de Segurança

-   _**Design**_ \- Etapa em que um dos GTs de Segurança estão construindo uma nova versão da Documentação. Nesta etapa a parte das especificações já desenvolvidas e aprovadas pelo GT serão disponibilizadas no ambiente de **Draft na Área do Desenvolvedor** no Portal do Open Finance.
    
    -   O início das discussões sobre a evolução da Documentação pelo GT de Segurança marca o início desta etapa;
        
-   _**Implementing**_ \- Etapa em que a nova versão da Documentação (unstable) estará disponível.
    
    -   O evento de publicação da nova versão da Documentação na **Área do Desenvolvedor** marcará o início desta etapa;
        
    -   Poderá ser usada para reportar possíveis bugs nas especificações;
        
-   _**Certifying**_ \- etapa em que a versão unstable da Documentação estará disponível para implementação.
    
    -   Poderá ser usada para reportar possíveis bugs nas especificações;
        
-   _**Current**_ \- etapa que indica a versão oficial da Documentação que deve estar em produção. Quando uma nova versão da Documentação (x+1) entrar em produção a versão antiga (versão x) sairá da etapa current para deprecated durante o período de convivência e a nova versão (versão x+1) sairá da etapa certifying para current.
    
    -   O evento de entrada em produção marcará o início desta etapa.
        
-   _**Deprecated**_ \- etapa em que a versão atual (versão x) da Documentação está sendo substituída pela próxima versão (x+1) em ambiente produtivo pelos participantes dando início ao período de convivência destas versões.
    
    -   O evento de entrada em produção da próxima versão da Documentaçao marcará o início desta etapa.
        
-   _**Retired**_ \- etapa em que a versão da Documentação se torna indisponível em ambiente produtivo.
    
    -   O evento de remoção desta versão da Documentação do ambiente produtivo marcará o início desta etapa.
        

## **Período de Convivência**

-   Quando temos a versão x em deprecated, significa que a versão x+1 está em current;
    
-   Este período é utilizado para que tenhamos uma transição mais suave entre a versão que está sendo aposentada (retired) e a versão que está se tornando oficial (current);
    
-   O período de convivência terá no máximo duas versões da mesma Documentação convivendo;
    
-   A duração do período de convivência será definido no GT Segurança, de acordo com a alteração que foi realizada na documentação. Só se aplica em casos de versões Major e Minor.
    

![image-20231128-153142.png](images/image-20231128-153142.png)
