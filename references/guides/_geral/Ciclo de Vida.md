# Ciclo de Vida

## **Etapas do ciclo de vida da API**

-   _**Design**_**:** etapa em que um dos GTs de Especificações de Dados Abertos, Dados do Cliente e/ou Serviços estão construindo uma nova versão da API. Nesta etapa a parte das especificações já desenvolvidas e aprovadas pelo GT serão disponibilizadas no ambiente de _Draft_ na Área do Desenvolvedor no Portal do Open Finance.
    
    -   O início das discussões sobre a evolução da API pelos GTs de Especificações marca o início desta etapa.
        
-   _**Implementing**_**:** etapa em que a nova versão da API (_**unstable**_) estará disponível para implementação.
    
    -   O evento de publicação da nova versão da API na Área do Desenvolvedor marcará o início desta etapa;
        
    -   Poderá ser usada para reportar possíveis _bugs_ nas especificações;
        
    -   As detentoras/transmissoras devem iniciar as implementações a partir da publicação da nova versão da API.
        
-   _**Certifying**_**:** etapa em que a versão _**unstable**_ da API estará disponível para implementação e certificação.
    
    -   O evento de liberação do uso dos motores de certificação marcará o início desta etapa;
        
    -   Poderá ser usada para reportar possíveis _bugs_ nas especificações ou nos motores de teste.
        
-   _**Current**_**:** etapa que indica a versão oficial da API que deve estar em produção. Quando uma nova versão da API (x+1) entrar em produção a versão antiga (versão x) sairá da etapa _current_ para _deprecated_ durante o período de convivência e a nova versão (versão x+1) sairá da etapa _certifying_ para _current_.
    
    -   O evento de entrada em produção marcará o início desta etapa.
        
-   _**Deprecated**_**:** etapa em que a versão atual (versão x) da API está sendo substituída pela próxima versão (x+1) em ambiente produtivo pelos participantes dando início ao período de convivência destas versões.
    
    -   O evento de entrada em produção da próxima versão da API marcará o início desta etapa.
        
-   _**Retired**_**:** Etapa em que a versão da API se torna indisponível em ambiente produtivo. A retirada de versões “retired” das APIs é monitorada pela IN 441.
    
    -   Essa etapa consiste na remoção da API retired do ambiente produtivo.
        
    -   Responsabilidades e ações para a remoção do ambiente produtivo:
        
        1.  Detentora/Transmissor: Descadastrar a API "retired" do Diretório;
            
        2.  Detentora/Transmissor: Remover a API "retired" de seu API gateway;
            
        3.  Iniciadora/Receptor: Garantir que não haverá mais acionamentos da API "retired", invalidando eventuais caches internos e acionando apenas o novo endpoint.
            

## **Período de convivência**

-   Quando temos a versão x em _deprecated_, significa que a versão x+1 está em _current_;
    
-   Este período é utilizado para que tenhamos uma transição mais suave entre a versão que está sendo aposentada (_retired_) e a versão que está se tornando oficial (_current_);
    
-   Neste período, teremos obrigatoriamente os participantes detentores de conta e transmissores de dados com as duas versões em produção, desde o primeiro dia do período de convivência, enquanto que os iniciadores de pagamento e os receptores de dados estarão lançando em produção suas implementações da versão x+1, sendo obrigatório o lançamento completo até o final do período de convivência;
    
-   O período de convivência terá no máximo duas versões da mesma API convivendo;
    
-   Após o fim do período de convivência, a versão _deprecated_ deverá ser desligada entre 00:00 e 23:59 em d+1, onde d é o último dia do período de convivência;​
    
    -   Em d+1 , ou seja, no dia do desligamento da API, não deve ocorrer chamadas para a versão _deprecated_.
        

![PB14.png](images/PB14.png)
