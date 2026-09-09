# Testes de longa duração

Presentes exclusivamente na FVP Manual - Testes Restritos, podendo ser solicitado em ciclos, têm como objetivo validar comportamentos e etapas que ocorrem em dias posteriores à execução inicial (liquidação de pagamentos futuros, tentativas de retry etc.). Como exigem validações em dias subsequentes, o sucesso na etapa inicial não significa que o teste foi concluído;

Os tickets só serão encerrados após a conclusão bem-sucedida de todas as etapas. O detalhamento do tratamento de falhas nos testes de longa duração pode ser encontrado na página: Fluxo de ticket – Testes de longa duração.

## **Como funcionam os testes agendados – longa duração**

-   **Execução assíncrona:** execuções de acompanhamento em datas futuras ocorrem automaticamente, sem intervenção do usuário.
    
-   **Persistência:** client\_id, consent\_id, payment\_id e refresh tokens são armazenados de forma segura entre execuções para garantir a continuidade do fluxo.
    
-   **Temporização de negócio:** alinhada às linhas do tempo reais dos pagamentos (ex.: D+2, D+3), com possíveis janelas específicas (ex.: 21:00–23:59 BRT).
    
-   **Salvaguardas automáticas:** acompanhamentos só são agendados se o fluxo inicial for concluído com sucesso.
    
-   **Visibilidade:** a estrutura pode visualizar as execuções agendadas, sua origem e status (agendado, executado, cancelado).
    

## **Software Statements utilizados nos testes agendados**

Os clients criados a partir dos Software Statements abaixo devem ser mantidos no Servidor de Autorização da instituição e NÃO devem ser deletados nem modificados, pois o mesmo ClientId será utilizado em novos testes:

-   44ffd907-2318-496b-ad91-07bbb0a836da
    
-   25402dd0-7553-477b-b635-b9ce79da18f2
    

_Caso a instituição realize a deleção acidental dos Clients atrelados aos Software Statements mencionados, será necessária a exclusão desse mesmo Client também do lado da ferramenta FVP. Mais informações podem ser encontradas na página:_ _Fluxo de deleção de Client._

Para identificação dos testes Agendados - Longa duração, seguem abaixo os módulos de produtos executados, contendo de 2 a 3 etapas por teste:

-   Testes de validação da liquidação de Pix Automático:
    
    -   Teste 1 de 2: automatic-payments\_api\_automatic-pix-scheduling\_1-2\_test-module\_v2-2
        
    -   Teste 2 de 2: automatic-payments\_api\_automatic-pix-scheduling\_2-2\_test-module\_v2-2
        
-   Testes de validação de retrys de Pix Automático:
    
    -   Teste 1 de 3: automatic-payments\_api\_automatic-pix-scheduling-retry\_1-3\_test-module\_v2-2
        
    -   Teste 2 de 3: automatic-payments\_api\_automatic-pix-scheduling-retry\_2-3\_test-module\_v2-2
        
    -   Teste 3 de 3: automatic-payments\_api\_automatic-pix-scheduling-retry\_3-3\_test-module\_v2-2
        
-   Testes de validação de Pagamentos Agendados:
    
    -   Teste 1 de 2: payments\_api\_scheduled-pix-verification\_1-2\_test-module\_v4
        
    -   Teste 2 de 2: payments\_api\_scheduled-pix-verification\_2-2\_test-module\_v4
        
-   Testes de validação de JSR - Jornada Sem Redirecionamento - Pagamentos Agendados:
    
    -   Teste 1 de 2: enrollments\_api\_payments\_scheduled-pix-verification\_1-2\_test-module\_v4
        
    -   Teste 2 de 2: enrollments\_api\_payments\_scheduled-pix-verification\_2-2\_test-module\_v4
        
-   Testes de validação de JSR - Jornada Sem Redirecionamento - Pagamentos Automáticos:
    
    -   Teste 1 de 2: enrollments\_api\_automatic-payments\_automatic-pix-scheduling\_1-2\_test-module\_v2-2
        
    -   Teste 2 de 2: enrollments\_api\_automatic-payments\_automatic-pix-scheduling\_2-2\_test-module\_v2-2
        
-   Testes de validação de Portabilidade de Crédito:
    
    -   Teste 1 de 3: credit-portability\_api\_accepted\_settlement\_1-3\_test-module\_v1
        
    -   Teste 2 de 3: credit-portability\_api\_accepted\_settlement\_2-3\_test-module\_v1
        
    -   Teste 3 de 3: credit-portability\_api\_accepted\_settlement\_3-3\_test-module\_v1
        

Os detalhes e o funcionamento de cada teste solicitado, incluindo os critérios de execução e validação de cada módulo, podem ser encontrados na página: Planos e suas configurações

## Suporte e Dúvidas Adicionais

Caso a instituição tenha dúvidas ou apontamentos de irregularidades, aconselhamos que realizem a abertura de um ticket de Solicitação de Informações via Service Desk: Solicitação de Serviço → Solicitação de Informações → Conformidade → Ferramenta de Validação em Produção (FVP).
