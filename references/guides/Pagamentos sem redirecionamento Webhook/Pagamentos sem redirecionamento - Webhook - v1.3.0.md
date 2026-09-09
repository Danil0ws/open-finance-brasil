# Pagamentos sem redirecionamento - Webhook - v1.3.0

## Jornada sem redirecionamento

### Notificação sobre a edição de um vínculo de conta

-   Alguns parâmetros podem ser alterados/editados exclusivamente em ambiente do PSP Pagador (Detentor) e devem gerar notificação ao ITP, permitindo a sincronia entre os dados do ITP e do PSP.
    
-   Os parâmetros editáveis exclusivamente em ambiente do PSP Pagador são:
    
    -   expirationDateTime
        
    -   transactionLimit
        
    -   dailyLimit
        

### Tipos de evento

-   A API Webhook, em seu payload de notificação, apresenta um campo do tipo ENUM chamado “eventType” e com domínio DATA\_CHANGED e STATE\_CHANGED. Este campo serve de auxilio para o ITP identificar qual a ação realizada pelo pagador ou PSP Pagador dentro do vínculo e direcionar a comparação para os campos que podem ser afetados com cada tipo.
    
-   Os valores do ENUM representam o seguinte:
    
    -   DATA\_CHANGED: Indica que dados do consentimento ou do vínculo de dispositivo foram alterados.
        
    -   STATUS\_CHANGED: Indica que o estado do consentimento, do pagamento ou do vínculo de dispositivo foi alterado.
        

### Notificação sobre a vinculação da conta

-   Os eventos que acionarão notificações na máquina de estados do vínculo de conta da jornada sem redirecionamento serão os status REJECTED e REVOKED;
    

![webhook-maq-estados-vinculacao.png](images/webhook-maq-estados-vinculacao.png)

-   No diagrama de exemplo abaixo, é possível identificar como será o comportamento para a consulta do vínculo da conta entre a iniciadora de pagamentos e a detentora de contas;
    

![image-20230817-175443.png](images/image-20230817-175443.png)
