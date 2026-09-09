# Tentativas Intradia e Extradia para Pix automático - v2.0.0 - [SV] Pagamentos Automáticos

-   Conceito geral do fluxo de tentativas Intradia e Extradia para o produto Pix automático
    
    -   Fluxo Intradia - A transação ocorre no dia em que foi solicitada a sua programação
        
        -   Primeira Tentativa: A liquidação da transação é tentada entre 0h e 8h no dia programado
            
            -   Na situação de falha onde o e2eid não pode ser mais utilizado a iniciadora deve enviar um novo pagamento contendo um novo e2eid
                
            -   Situações de erro que exigem a realização de novas tentativas de liquidação pelo iniciador, com e sem reenvio de e2eID para o agendamento do pagamento, conforme Tabela 1
                
            -   O horário de envio que o Iniciador deve enviar o novo e2eid para ser persistido na segunda tentativa deve ser no máximo ao meio-dia (12h00) do mesmo dia para para tentativas de liquidação intradia
                
        -   Segunda Tentativa: Se a ordem de pagamento não for liquidada até às 8h, o PSP (prestador de serviços de pagamento) do pagador deve realizar uma nova tentativa entre 18h e 21h do mesmo dia
            
    -   Fluxo Extradia - A transação é programada para ocorrer em uma data futura, com processamento e liquidação automática nessa data
        
        -   O iniciador a pedido do recebedor pode realizar as novas tentativas
            
        -   Quando um pagamento não é liquidado na data programada (Intradia), a iniciadora pode realizar novas tentativas dentro de uma janela de 7 dias corridos após a data original de liquidação (exceto para a periodicidade semanal, onde o prazo é de 5 dias), por meio de acionamento do iniciador para detentora, até às 23:59h do dia imediatamente anterior à liquidação. Caso não seja possível realizar a nova tentativa cobrança no prazo estipulado, o recebedor pode optar por enviar o valor total dos meses em atraso na cobrança do ciclo novo, sempre sujeito aos limites estipulados pelo pagador.
            
        -   Durante esse período de sete dias o iniciador pode fazer até três tentativas de liquidação em datas diferentes, seguindo as mesmas regras de prazos da intradia
            

  
**Tabela 1: Situações de erro que exigem a realização de novas tentativas de liquidação pelo iniciador, com e sem reenvio de e2eID para o agendamento do pagamento**

**Código de erro**

**Contabiliza tentativa?**

**Permite nova tentativa intradia ³**

**Exige reevio de e2eID**

NAO\_INFORMADO

SIM

SIM

SIM

PAGAMENTO\_RECUSADO\_SPI

SIM

SIM

SIM

FALHA\_INFRAESTRUTURA\_SPI

SIM

SIM

SIM

FALHA\_INFRAESTRUTURA\_ICP

SIM

SIM

SIM

FALHA\_INFRAESTRUTURA\_PSP\_RECEBEDOR

SIM

SIM

SIM

SALDO\_INSUFICIENTE

SIM

SIM

NÃO

VALOR\_ACIMA\_LIMITE

SIM

SIM

NÃO

PAGAMENTO\_RECUSADO\_DETENTORA

SIM

SIM

NÃO

FALHA\_INFRAESTRUTURA\_DETENTORA

SIM

NÃO

NÃO

LIMITE\_VALOR\_TRANSACAO\_CONSENTIMENTO\_EXCEDIDO²

SIM

NÃO

NÃO

DETALHE\_TENTATIVA\_INVALIDO

NÃO

SIM

NÃO

VALOR\_INVALIDO

NÃO

NÃO

NÃO

PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO

NÃO

NÃO

NÃO

CONSENTIMENTO\_INVALIDO

N/A

NÃO

NÃO

TITULARIDADE\_INCONSISTENTE

N/A

NÃO

NÃO

LIMITE\_PERIODO\_VALOR\_EXCEDIDO¹

N/A

NÃO

NÃO

LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO¹

N/A

NÃO

NÃO

LIMITE\_VALOR\_TOTAL\_CONSENTIMENTO\_EXCEDIDO¹

N/A

NÃO

NÃO

LIMITE\_TENTATIVAS\_EXCEDIDO²

N/A

NÃO

NÃO

CONSENTIMENTO\_REVOGADO²

N/A

NÃO

NÃO

FORA\_PRAZO\_PERMITIDO

N/A

NÃO

NÃO

PERMISSAO\_INSUFICIENTE

N/A

NÃO

NÃO

¹ - Erro exclusivo para o produto Transferências inteligentes  
² - Erro não ocorre no momento da liquidação, apenas no momento do agendamento  
³ - Conforme previsto no Art. 7, parágrafo 1 da IN BCB 513 - "Caso a ordem de pagamento não seja enviada para liquidação no horário previsto, por ausência de recursos suficientes ou de limite transacional disponível, o prestador de serviços de pagamento do usuário pagador deve enviar notificação para seu cliente informando-o sobre a não liquidação do Pix Automático (...)"

-   **Exemplo de aplicabilidade**
    

![TentativaDeLiquidacaoSucesso.png](images/TentativaDeLiquidacaoSucesso.png)

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
                

![TentativaLiquidacaoExtradiaFalhas.png](images/TentativaLiquidacaoExtradiaFalhas.png)

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
