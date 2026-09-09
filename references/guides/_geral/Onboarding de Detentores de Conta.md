# Onboarding de Detentores de Conta

**Obrigatoriedade de participação:**

A participação na fase de iniciação de pagamentos na modalidade de detentora de conta é obrigatória para instituições obrigatórias no arranjo Pix. A participação é voluntária para as demais instituições.

**Requisitos de atuação na modalidade:**

-   Homologação no arranjo Pix: Instituição deve ter obtido sucesso nos testes de Open Finance no ambiente Pix tester, conforme[https://mailchi.mp/1a06af40e3d4/open-banking-informa-10141804](https://mailchi.mp/1a06af40e3d4/open-banking-informa-10141804);
    
-   Habilitação do papel regulatório: Habilitar papel “CONTA” no Diretório de Participantes;
    
-   Publicação das APIs:
    
    -   Instituições obrigatórias no arranjo Pix: Necessário a publicação das APIs de Pagamentos e Pagamentos automáticos
        
        -   A publicação da API Vínculo de dispositivo será obrigatória a partir de fev/2026
            
    -   Instituições voluntárias: Necessário publicação das APIs de Pagamentos e Pagamentos automáticos
        

**Restrição de funcionalidades para testes:**

Nova marca detentora de conta: Indicação de _flag_ “Homologacao” no servidor de autorização para caso de nova marca detentora de conta

Novo produto (instituições voluntárias): Indicação de metadado “Homologacao” na Família da API.

**Indicadores monitorados:**

**Item**

**Pagamentos (Imediato e agendados)**

**Pagamentos automáticos (Transf. Inteligentes e Pix automático)**

**Vínculo de Dispositivo (Jornada sem redirecionamento)**

Comportamento funcional

Sucesso em todos os módulos dos planos de testes relativos à cada API, para todos os servidores de autorização, PF e PJ (quando aplicável)

fvp-payments-e2e\_open\_test-plan-v4

fvp-automatic-payments\_open\_test-plan-v1

fvp-no\_redirect\_payments\_open\_test-plan-v2

Integração com ferramentas do perímetro central

Pareamento de 95% das chamadas com a Plataforma de Coleta de Métricas (PCM) e envio de todos additionalInfos

Testes bilaterais

Realização de pagamentos liquidados com 10 ITPs

200 pagamentos, sendo:

-   100 imediatos
    
-   100 agendados
    

200 pagamentos, sendo:

-   100 transferências inteligentes
    
-   100 pix automáticos
    
    -   30 _first payments_
        
    -   70 _recurring payments_
        

100 pagamentos

Incidentes bilaterais

Resolução de todos os chamados em aberto até a conclusão do processo

**Links úteis:**

[Clique para acessar o Painel Integrado - Pagamentos](https://sa-east-1.quicksight.aws.amazon.com/sn/account/openfinance-brasil/dashboards/5a1cb1ad-921c-4548-95b7-2c8355af1233)

[Clique para acessar o Painel Integrado - Pagamentos automáticos](https://sa-east-1.quicksight.aws.amazon.com/sn/account/openfinance-brasil/dashboards/bd53b4da-289e-465f-b9fa-c2954928b45f)

[Clique para acessar o Painel Integrado - Jornada sem redirecionamento (Vínculo de Dispositivo)](https://sa-east-1.quicksight.aws.amazon.com/sn/account/openfinance-brasil/dashboards/1338e60a-c4d6-4a67-a861-7c5046ad7ac2)
