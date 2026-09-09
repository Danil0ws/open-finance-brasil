# FVP Manual - Ciclo Aberto

A FVP Manual - Testes Abertos permite que as instituições executem testes em produção em seus próprios servidores. Dentro de cada ciclo, é esperado que as instituições obtenham sucesso nos testes solicitados. Para mais informações sobre as responsabilidades de execuções, visitar a página _Responsabilidades de execuções — Restritos e Aberta_.

As instituições podem acompanhar os resultados e as responsabilidades de cada ciclo visitando a página: [Dashboard do ciclo FVP Manual Aberta no QuickSight](https://sa-east-1.quicksight.aws.amazon.com/sn/account/openfinance-brasil/dashboards/68dbb82b-76df-425f-a07f-7865067dd735/sheets/68dbb82b-76df-425f-a07f-7865067dd735_7585736a-24f7-4a87-be83-1a47937e3901).

![att\_0\_for\_2065039718.png](images/att_0_for_2065039718.png)

Nos ciclos da FVP Manual Aberta, se identificada ausência de sucesso na execução dos testes solicitados por parte da instituição, um ticket de notificação é direcionado à instituição via Service Desk. Para encerrá-lo, a instituição deve anexar uma evidência de sucesso no teste. O detalhamento do tratamento de falhas pode ser encontrado na página Fluxo de ticket - Ciclo Aberto.

Os servidores, segmentos e testes que devem obter sucesso em cada ciclo, dependem dos seguintes critérios:

-   **Servidor:** Marcas (Servidor de Autorização) em que o fornecedor contratado não possua conta aberta, a responsabilidade de obtenção de sucesso é da própria instituição.
    
-   **Segmento suportado (PF ou PJ):** Para cada segmento suportado pelo servidor, a instituição deverá obter sucesso nos testes, executando como usuário PF ou PJ, conforme aplicável.
    
-   **APIs Publicadas:** De acordo com as APIs publicadas em cada servidor, serão exigidos sucessos nos testes relativos a essas APIs.
    

A lista de planos e módulos de testes da FVP em que os servidores das instituições deverão obter sucesso completo a cada ciclo, de acordo com as APIs publicadas em cada servidor:

Os detalhes e o funcionamento de cada teste solicitado, incluindo os critérios de execução e validação de cada módulo, podem ser encontrados na página: Planos e suas configurações

**API / Produto**

**Plano de teste**

**Módulo de teste**

Pagamentos Automáticos v2.2.0 — Pix Automático

Automatic Payments API – v2.2.0 - Automatic Pix – Open FVP

fvp\_automatic-payments\_api\_automatic-pix-semanal-core\_open\_test-module\_v2-2

Pagamentos Automáticos v2.2.0 — Transferências Inteligentes

Automatic Payments API – v2.2.0 - Sweeping – Open FVP

fvp\_automatic-payments\_api\_sweeping-accounts-core\_test-module\_v2-2

Dados do Cliente

Customer Data APIs – v2/v3 - Happy Path – Open FVP

fvp-customer\_data\_unique\_happy\_path\_test-module

Pagamentos v5.0.0

Payments API – v5.0.0 - Open FVP

fvp-payments\_api\_**recurring**\-payments-custom-not-cancelled\_open\_test-module\_v5

Vínculo de Dispositivo v2.2.0 (JSR)

Enrollments API – v2.2.0 - Payments – Open FVP

enrollments\_api\_payments-core\_test-module\_v2-2

Para mais informações sobre o a estrutura temporal dos ciclos, prazos e regras, você pode acessar na página: Ciclos - Calendário de execução
