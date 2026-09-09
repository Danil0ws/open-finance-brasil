# Dúvidas comuns

Esta seção reúne as dúvidas mais frequentes sobre a utilização da FVP, abordando o funcionamento da ferramenta, notificações, tickets e comportamentos observados durante a execução dos testes.

## **Dúvidas comuns sobre a ferramenta**

**O que é a FVP Manual Restrita e qual a diferença dela para a FVP Manual Aberta e a FVP Automática?**

-   A FVP Automática executa testes diariamente, de forma automatizada, contemplando validações de DCR, DCM e testes das fases que antecedem a autorização do consentimento.
    
-   A FVP Manual, por sua vez, contempla a jornada completa de compartilhamento de dados e iniciação de pagamentos, exigindo a interação do usuário para autorizar o consentimento e concluir os fluxos.
    
-   A diferença entre a **FVP Manual Aberta** e a **FVP Manual Restrita** está na responsabilidade pela execução dos testes e na disponibilidade de alguns módulos exclusivos da estrutura do Open Finance Brasil, como determinados testes de validação.
    

**Recebi a mensagem "Failed to fetch" na ferramenta. O que isso significa?**

-   A mensagem **"Failed to fetch"** normalmente está relacionada ao tempo de expiração da sessão da FVP (timeout), situação comum após longos períodos de inatividade ou troca de abas no navegador.
    
-   Essa ocorrência não significa, necessariamente, que o teste falhou. Basta atualizar a página para continuar acompanhando a execução.
    

![att\_0\_for\_2065170632.png](images/att_0_for_2065170632.png)

## **Dúvidas comuns sobre notificações e encerramento dos tickets**

**Recebi um ticket de notificação da** FVP Manual Restrita**, porém não consigo comentar ou encerrá-lo. O que devo fazer?**

-   Os tickets de notificação da **FVP Manual Restrita** não podem ser comentados ou encerrados pela instituição.
    
-   O encerramento ocorre somente após uma nova execução bem-sucedida do módulo de teste, realizada pelo fornecedor responsável.
    
-   Para solicitar uma reexecução, abra um chamado no Service Desk na categoria: **Requisição → Reexecução → FVP Manual – Testes Restritos**
    
-   Caso a solicitação seja apenas para esclarecimento de dúvidas, utilize a categoria: **Requisição → Solicitação de Informações → Conformidade → Ferramenta de Validação em Produção**
    

**Solicitei uma reexecução. Meu SLA será impactado enquanto aguardo o retorno?**

-   Não. Após a abertura da solicitação de reexecução, o ticket passa para o status **"Aguardando Requisitante - Essencial"**. Durante esse período, a instituição não possui nenhuma ação pendente e o SLA é ajustado automaticamente.
    
-   Após a conclusão da reexecução, o ticket retorna ao status **"Encaminhado N2 Atendimento"**, retomando a contagem normal do SLA.
    

## **Dúvidas comuns sobre o comportamento dos testes**

**O teste foi interrompido (status "INTERRUPTED"). O que isso significa?**

-   Esse comportamento pode ocorrer por dois motivos:
    
    -   A FVP identificou uma falha crítica que impediu a continuidade da execução;
        
    -   A execução foi interrompida manualmente por meio do botão **"Stop"**.
        
-   Para identificar a causa da interrupção, recomenda-se analisar o primeiro erro apresentado nos logs da execução.
    

![att\_1\_for\_2065170632.png](images/att_1_for_2065170632.png)

**O motor realizou chamadas de DELETE para consentimentos ou pagamentos em um momento inesperado. Por quê?**

-   As chamadas **DELETE** fazem parte do processo de limpeza (**Cleanup**) executado pela FVP.
    
    -   Esse processo pode ocorrer:
        
        -   Ao final da execução, para remover os recursos criados durante o teste;
            
        -   Durante a execução, caso uma falha crítica impeça a continuidade do fluxo.
            
-   Se o consentimento ou pagamento não chegou a ser criado, é esperado que a operação de limpeza também apresente erro. Nesses casos, deve ser considerada a primeira falha identificada durante a execução do teste.
    

**Após a execução, baixei os logs e eles vieram vazios. Por quê?**

-   Por questões de segurança, a FVP mantém as informações das execuções disponíveis apenas por um período limitado.
    
-   Após esse prazo, os dados são removidos automaticamente da ferramenta. Caso o download seja realizado após a exclusão das informações, o arquivo será disponibilizado sem conteúdo.
    

## **Múltipla Alçada**

A Jornada de Iniciação de Pagamento com Múltiplos Aprovadores é utilizada quando um pagamento necessita da autorização de mais de um usuário da mesma conta.

Nesse fluxo, o solicitante inicia o pagamento na ITP e é informado pela ID de que são necessárias aprovações adicionais. A solicitação permanece com o status Pendente de aprovação até que os demais aprovadores autorizem ou rejeitem a transação. Após a conclusão do processo, o solicitante é informado sobre o resultado.

É importante que a ITP e a ID forneçam informações claras e precisas a todos os usuários envolvidos durante todo o processo.

Atualmente, a FVP não suporta à execução de testes para jornadas com múltiplos aprovadores (múltipla alçada).
