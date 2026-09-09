# Ciclos - Calendário de execução

## **Definição dos ciclos**

Os testes da FVP devem ser executados em **ciclos mensais estruturados**, contemplando a validação das APIs expostas pelas instituições. Cada ciclo deve considerar:

-   Os segmentos de **Pessoa Física (PF)** e **Pessoa Jurídica (PJ)** suportados pela instituição (flags "Suporta contas PF" e "Suporta contas PJ" no diretório);
    
-   As APIs publicadas em cada servidor;
    
-   Os cenários de teste definidos pela governança da Associação Open Finance.
    

As instituições deverão obter êxito em **todos os testes previstos para seus servidores a cada ciclo**, como condição de conformidade contínua em produção. Os critérios de exigência por servidor são: servidor (marca sem conta do fornecedor → responsabilidade da instituição), segmento suportado (PF e/ou PJ) e APIs publicadas.

O **Ciclo Aberto** segue o calendário mensal, com execução de responsabilidade da instituição participante (quando os fornecedores não possuem conta aberta no servidor). A execução é realizada pelos usuários da própria instituição, com perfil PFVPC no Diretório.

O **Ciclo Restrito** segue o mesmo calendário mensal, com execução de responsabilidade dos fornecedores contratados pela Associação (quando possuem conta aberta no servidor da instituição). Nessa modalidade, os testes são executados pelos fornecedores credenciados, com acesso exclusivo aos membros da Associação e aos próprios fornecedores.

Os detalhes sobre os testes previstos em cada ciclo são apresentados nas páginas específicas:

-   **Ciclo Aberto** – lista completa de planos de teste e módulos exigidos para o ciclo aberto.
    
-   **Ciclo Restrito** – lista completa de planos de teste e módulos exigidos para o ciclo restrito.
    

## **Cronograma de execução**

Os ciclos de execução da FVP Manual obedecem a um ciclo mensal estruturado, aplicável tanto para o Ciclo Aberto quanto para o Ciclo Restrito. A governança apresenta ao BCB, os testes que serão realizados durante cada ciclo, incluindo aqueles que serão cobrados das instituições e dos fornecedores contratados. A partir dessa definição, são estabelecidos os testes que devem ser executados nos servidores sob responsabilidade de cada instituição e fornecedor ao longo do ciclo.

A seguir, é apresentado o calendário de execução correspondente aos ciclos previstos para 2026.

![att\_0\_for\_2064580860.png](images/att_0_for_2064580860.png)

## **Monitoramento via Quicksight**

Tanto para a FVP Aberta quanto para a FVP Restrita, as instituições podem acompanhar o andamento dos testes e resultados em tempo real através do dashboard Quick - Monitoramento da FVP - Instituições.

**Acesso ao dashboard:** [Quick - Monitoramento da FVP - Instituições](https://sa-east-1.quicksight.aws.amazon.com/sn/account/openfinance-brasil/dashboards/68dbb82b-76df-425f-a07f-7865067dd735)

**O que é possível monitorar no Quick:**

-   Status de execução dos ciclos de testes (abertos e restritos);
    
-   Resultados por servidor e API;
    
-   Histórico de execuções por ciclo;
    
-   Indicadores de conformidade contínua;
    
-   Evidências de sucesso/falha por cenário de teste.
    

**Importante:** O dashboard Quick serve para **ambas as modalidades** (FVP Aberta e FVP Restrita), permitindo que instituições acompanhem todos os testes sob sua responsabilidade, independentemente de quem executa (instituição ou fornecedor).

## **Suporte e Dúvidas Adicionais**

Caso a instituição tenha dúvidas ou apontamentos de irregularidades, aconselhamos que realizem a abertura de um ticket de Solicitação de Informações via Service Desk: Solicitação de Serviço → Solicitação de Informações → Conformidade → Ferramenta de Validação em Produção (FVP).
