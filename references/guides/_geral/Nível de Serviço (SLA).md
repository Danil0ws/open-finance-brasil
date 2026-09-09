# Nível de Serviço (SLA)

O suporte eficaz da disponibilidade do Open Finance Brasil mantém níveis consistentes de serviços do sistema.

As APIs “Produtos e Serviços”, “Canais de Atendimento”, “Consentimento”, “Dados Cadastrais”, “Cartão de Crédito”, “Contas” e “Operações de Crédito” deverão satisfazer requisitos mínimos de disponibilidade.

Cada um de seus endpoints deverá estar disponível:

-   I - 85% do tempo a cada 24 horas; e
    
-   II - 95% do tempo a cada 1 mês; e
    
-   III - 99,5% do tempo a cada 3 meses.
    

## **Checagem de disponibilidade:**

A disponibilidade é checada no _endpoint_ `GET /discovery/status`, conforme documentada no item [API de Status](https://openbankingbrasil.atlassian.net/wiki/spaces/DraftOF/pages/1671948/APIs+Comuns+Discovery).

A cada 30 segundos, a API de status é requisitada com _timeout_ de 1s.

-   Será considerado _uptime_, se o retorno for:
    
    -   OK.
        
-   Será considerado _downtime_, se o retorno for:
    
    -   _PARTIAL\_FAILURE_;  
        
    -   _SCHEDULED\_OUTAGE_:
        
        -   Se a requisição for realizada entre o período de 01h e 07h, o contador de SCHEDULED\_OUTAGE é iniciado com 30 segundos acrescidos;  
            
        -   Cada nova requisição vai adicionando 30 segundos mais ao contador de SCHEDULED\_OUTAGE, até que uma requisição volte outro valor ou a requisição for feita depois das 07h.  
            
    -   _UNAVAILABLE_:
        
        -   Se a requisição for realizada entre o período de 07h e 01h;  
            
        -   Se serviço não responder a requisição;  
            
        -   O contador de _downtime_ é iniciado com 30 segundos acrescidos;  
            
        -   Cada nova requisição adicionará 30 segundos a mais ao contador de _downtime_, até que uma requisição retorne OK.  
            

O _downtime_ deve ser calculado como o número total de segundos simultâneos por requisição da API, por período de 24 horas, começando e terminando à meia-noite, que qualquer _endpoint_ da API não esteja disponível, dividido por 86.400 (total de segundos em 24 horas) e expresso como uma porcentagem.

**A disponibilidade é calculada sendo 100% menos a quantidade em percentual da indisponibilidade.**

-   De modo geral, consideram-se os erros 5XX HTTP _status codes_ como erros do servidor, e portanto, atribuíveis ao servidor das APIs;
    
-   Erros baseados em 4XX HTTP _status code_ são, em grande parte, atribuídos à ações ou falhas dos receptores, e dessa forma, não devem ser incluídos no cálculo.
    

Não será considerado como _downtime_:

-   Uma indisponibilidade por mês, por 3h entre 01h e 07h, desde que reportado com uma semana de antecedência ao diretório;
    
-   Por tempo não definido, a qualquer momento e sem notificação em caso de resolução de problemas de segurança, desde que aprovado pelo Diretório. Neste caso, as instituições devem garantir o emprego dos melhores esforços para a resolução do problema
