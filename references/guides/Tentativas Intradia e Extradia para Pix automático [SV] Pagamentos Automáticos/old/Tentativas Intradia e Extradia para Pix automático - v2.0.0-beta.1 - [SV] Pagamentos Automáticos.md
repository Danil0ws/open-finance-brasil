# Tentativas Intradia e Extradia para Pix automático - v2.0.0-beta.1 - [SV] Pagamentos Automáticos

-   Conceito geral do fluxo de tentativas Intradia e Extradia para o produto Pix automático
    
    -   Fluxo Intradia - A transação ocorre no dia em que foi solicitada a sua programação
        
        -   Primeira Tentativa: A liquidação da transação é tentada entre 0h e 8h no dia programado
            
        -   Segunda Tentativa: Se a ordem de pagamento não for liquidada até às 8h, o PSP (prestador de serviços de pagamento) do pagador deve realizar uma nova tentativa entre 18h e 21h do mesmo dia
            
        -   Na situação de falha onde o e2eid não pode ser mais utilizado a iniciadora deve enviar um novo pagamento contendo um novo e2eid (Falha de infra SPI e/ou PSP recebedor)
            
    -   Fluxo Extradia - A transação é programada para ocorrer em uma data futura, com processamento e liquidação automática nessa data
        
        -   O iniciador a pedido do recebedor pode realizar as novas tentativas
            
        -   Quando um pagamento não é liquidado na data programada (Intradia), a detentora pode realizar novas tentativas dentro de uma janela de 7 dias corridos após a data original de liquidação, por meio de acionamento do iniciador para detentora, até às 23:59h do dia imediatamente anterior à liquidação
            
        -   Durante esse período de sete dias o iniciador pode fazer até três tentativas de liquidação em datas diferentes, seguindo as mesmas regras de prazos da intradia
            
-   **Exemplo de aplicabilidade**
    

![8ba930ad-9f94-4480-9b3a-a7c0f13b784d.png](images/8ba930ad-9f94-4480-9b3a-a7c0f13b784d.png)

-   Data envio: 14/09/24 – (02 a 10 dias de antecedência da liquidação)
    
    -   Data liquidação: 16 de setembro de 2024.
        
-   A primeira tentativa (Intradia):
    
    -   Data liquidação: 16 de setembro de 2024
        
        -   Primeira Tentativa: A liquidação é tentada entre 0h e 8h.
            
            -   Se houver saldo suficiente e os limites forem respeitados, a transação é concluída.
                
            -   Caso falhe (por exemplo, por saldo insuficiente), segue-se para as novas tentativas.
                
        -   Segunda Tentativa: Uma nova tentativa é feita entre 18h e 21h.
            
            -   Se houver saldo suficiente e os limites forem respeitados, a transação é concluída
                
            -   Em caso de falha considerar o cenário de tentativas (Extradias)
                

![2.png](images/2.png)

-   Novas tentativas nos 7 dias seguintes (Extradias):
    
    -   Se a liquidação não for concluída no dia 16 de setembro, o detentor pode tentar realizar novas liquidações durante os próximos 7 dias corridos, através do acionamento do iniciador em até 3 tentativas em dias diferentes.
        
    -   Primeira Tentativa Extradias: 18 de setembro de 2024
        
        -   A primeira tentativa após a falha no dia 16 pode ser feita.
            
            -   A liquidação é tentada novamente dentro das janelas de liquidação.
                
        -   Segunda Tentativa Extradias: 20 de setembro de 2024
            
            -   Se a tentativa do dia 18 falhar, o iniciador pode realizar uma nova tentativa
                
        -   Terceira Tentativa Extradias: 22 de setembro de 2024, é feita no dentro do período de 7 dias corridos.
            
            -   Se houver saldo suficiente e os limites forem respeitados, a transação é concluída
                
            -   Em caso de falha notificar o motivo
