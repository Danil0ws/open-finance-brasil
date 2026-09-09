# Responsabilidades de execuções — Ciclos Abertos e Restritos

A **FVP Manual (Ferramenta de Validação em Produção)** possui duas modalidades de execução: **Testes Abertos** e **Testes Restritos**. A principal diferença entre elas está na **responsabilidade pela execução dos testes**, que é definida de acordo com a existência de uma conta aberta pelo fornecedor contratado pela estrutura na marca da instituição.

**Como funciona**

-   **Testes Abertos** são executados pela própria instituição.
    
-   **Testes Restritos** são executados exclusivamente pela estrutura do Open Finance Brasil, por meio do fornecedor responsável.
    

A relação das contas abertas pelo fornecedor, bem como a responsabilidade de execução dos testes em cada ciclo, pode ser consultada no [Dashboard FVP Manual – Relação de Contas Abertas](https://sa-east-1.quicksight.aws.amazon.com/sn/account/openfinance-brasil/dashboards/68dbb82b-76df-425f-a07f-7865067dd735)

**Comparativo entre as modalidades**

**Modalidade**

**Quando se aplica**

**Responsável pela execução**

**FVP Manual – Testes Abertos**

O fornecedor contratado **não possui** conta aberta na marca da instituição.

A própria instituição.

**FVP Manual – Testes Restritos**

O fornecedor contratado **possui** conta aberta na marca da instituição.

Estrutura do Open Finance Brasil (fornecedor responsável).

## **FVP Manual – Ciclo Aberto**

Nessa modalidade, o acesso aos planos de teste é disponibilizado aos usuários da própria organização, garantindo que as execuções ocorram sem interferência do fornecedor de testes.

Sempre que o fornecedor responsável pela execução **não possuir conta aberta** na marca da instituição, a execução dos testes passa a ser de responsabilidade da própria instituição.

Para informações sobre acesso, configuração e execução dos planos de teste, consulte a FVP Manual - Ciclo Aberto

## **FVP Manual – Ciclo Restrito**

Os Testes Restritos são planos de teste de execução exclusiva do fornecedor responsável pela operação da FVP Manual.

Essa modalidade é aplicada quando o fornecedor contratado **possui conta aberta** na instituição, assumindo a responsabilidade pela execução dos testes durante os ciclos mensais da FVP Manual.

Caso seja identificada alguma falha durante a execução dos testes, será aberto um **ticket no Service Desk**, contendo todas as evidências da execução realizada.

Para que esse ticket seja encerrado, é necessária a obtenção de uma execução bem-sucedida do mesmo módulo de teste, realizada novamente pelo fornecedor responsável.

Diferentemente dos Testes Abertos, nos quais a instituição deve executar todos os planos de teste disponibilizados para os produtos dos quais participa, os Testes Restritos possuem seu ciclo de execução definido pela AOF. Em cada ciclo, são selecionados os módulos de teste que serão executados pelo fornecedor responsável.

A instituição consegue realizar o acompanhamento dos resultados de testes através do [Quicksight de monitoramento](https://sa-east-1.quicksight.aws.amazon.com/sn/account/openfinance-brasil/dashboards/68dbb82b-76df-425f-a07f-7865067dd735).

Para informações sobre acesso, configuração e execução dos planos de teste, consulte a FVP Manual - Ciclo Restrito

Quando houver necessidade de uma nova execução, a instituição deverá abrir um chamado no Service Desk na categoria:

**Requisição → Reexecução → FVP Manual – Testes Restritos**

**Resumo**

**Característica**

**Testes Abertos**

**Testes Restritos**

Quem executa os testes

Instituição

Fornecedor

Acesso aos planos de teste

Instituição

Fornecedor

Critério de aplicação

Fornecedor sem conta aberta

Fornecedor com conta aberta

Frequência das execuções

Ciclos mensais

Ciclos mensais

Testes executados por ciclo

A execução de todos os planos de teste disponibilizados é obrigatória para as instituições que possuam o respectivo produto. Para que a instituição obtenha sucesso na avaliação do ciclo, é necessário que todos os testes aplicáveis sejam executados e aprovados.

Serão executados os módulos de teste selecionados para o ciclo. Caso todos sejam aprovados, a instituição será considerada aprovada no ciclo, obtendo sucesso na avaliação.

Em caso de falha

A instituição realiza nova execução conforme orientação da FVP

A estrutura realiza a reexecução mediante solicitação da instituição via Service Desk

## Suporte e Dúvidas Adicionais

Caso a instituição tenha dúvidas ou apontamentos de irregularidades, aconselhamos que realizem a abertura de um ticket de Solicitação de Informações via Service Desk: Solicitação de Serviço → Solicitação de Informações → Conformidade → Ferramenta de Validação em Produção (FVP).
