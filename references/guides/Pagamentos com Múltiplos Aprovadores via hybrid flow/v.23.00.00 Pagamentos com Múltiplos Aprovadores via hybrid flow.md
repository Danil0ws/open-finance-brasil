# v.23.00.00 Pagamentos com Múltiplos Aprovadores via hybrid flow

Esta página reúne os requisitos e recomendações aplicáveis à jornada de pagamento com Pix via Open Finance com múltiplos aprovadores (múltipla alçada) via hybrid flow.

## Etapas da jornada

3.  Confirmação
    

5.  Efetivação
    

wide760

**Nota**

Além dos requisitos e recomendações previstos nesta página, aplicam-se a esta jornada aqueles descritos em:

-   Pix via hybrid flow;
    
-   Pix com vencimento através de QR Code dinâmico via hybrid flow;
    
-   Pix Agendado via hybrid flow;
    
-   Pix Automático via hybrid flow;
    
-   Transferências Inteligentes via hybrid flow;
    

-   Regulamentação e documentos do arranjo de pagamento vigentes.
    

wide760

**Atenção**

A jornada de **Pix Saque e Pix Troco** não suporta pagamentos com múltiplos aprovadores.

Consulte a página **Casos de erro de Pix Saque e Pix Troco** para mais informações sobre os possíveis erros e como comunicá-los ao usuário durante a jornada.

* * *

# Etapa 3: Confirmação

Nesta etapa, A ID deve:

-   Comunicar o usuário solicitante sobre a necessidade de múltiplas aprovações da transação.
    
-   Comunicar os demais aprovadores sobre a pendência de aprovação.
    
-   Comunicar a ITP sobre a necessidade de múltiplas aprovações da transação.
    

#F4F5F7

## Requisitos - ID

**Cenário: Dinâmica de aprovação**

REQ.PG-13700 a 13800

-   `REQ.PG-13700` Seguir os poderes vigentes para movimentação de conta, conforme as políticas internas da instituição (Ex.: Estatutos e contratos sociais), assegurando que as jornadas de iniciação de pagamento adotem a mesma dinâmica de alçadas e filas de aprovação já aplicáveis a pagamentos fora do Open Finance, sem a criação de regras específicas.
    
-   `REQ.PG-13800` Estender para o âmbito do Open Finance os mecanismos já disponibilizados nos canais da instituição que permitam a representantes legais devidamente constituídos autorizar ou delegar poderes a outras pessoas.
    

REQ.PG-13900 a 14100

**Cenário: Confirmação da solicitação para o usuário solicitante**

-   `REQ.PG-13900` Informar o usuário solicitante sobre a necessidade de aprovações adicionais, conforme a política de poderes da instituição.
    
-   `REQ.PG-14000` Informar o usuário solicitante sobre o prazo para atuação conforme o tipo de transação.
    
-   `REQ.PG-14100` Informar sobre a necessidade de reinício do processo se o prazo expirar.
    

![image-20260624-162649.png](images/image-20260624-162649.png)

REQ.PG-14200

-   `REQ.PG-14200` Quando aplicável, exibir mensagem informando o solicitante que o pagamento ultrapassa o limite da conta selecionada e que só será efetuado após a última aprovação necessária, desde que o limite seja ajustado em tempo hábil e de acordo com os critérios da instituição para a conta.
    

![image-20260624-162742.png](images/image-20260624-162742.png)REQ.PG-14300

-   `REQ.PG-14300` Redirecionar o usuário solicitante para a ITP após a confirmação da transação.
    

![image-20260304-184823.png](images/image-20260304-184823.png)REQ.PG-14400 a 14900

**Cenário: Confirmação do usuário aprovador**

-   `REQ.PG-14400` Permitir a atuação do usuário aprovador de forma assíncrona após a confirmação do usuário solicitante.
    
-   `REQ.PG-14500` Exibir, no mínimo, as mesmas informações da transação apresentadas ao usuário solicitante na etapa de confirmação da transação.
    
-   `REQ.PG-14600` Exibir identificação do usuário solicitante.
    
-   `REQ.PG-14700` Quando aplicável, informar sobre demais pendências de aprovação.
    
-   `REQ.PG-14800` Informar o usuário aprovador sobre o prazo para atuação conforme o tipo de transação.
    
-   `REQ.PG-14900` Informar sobre a necessidade de reinício do processo se o prazo para aprovação expirar.
    

![image-20260624-163022.png](images/image-20260624-163022.png)REQ.PG-15000

-   `REQ.PG-15000` Após atuação do usuário aprovador, exibir mensagem informando sobre o resultado da solicitação.
    

![image-20251123-172809.png](images/image-20251123-172809.png)REC.PG-04500 a 04600#F4F5F7

## Recomendações - ID

**Cenário: Confirmação do usuário aprovador**

-   `REC.PG-04500` Permitir a atuação dos usuários aprovadores através do acesso ao ambiente Open Finance ou de outro fluxo já existente na instituição.
    
-   `REC.PG-04600` Identificar o usuário solicitante através de seu nome e CPF (mascarado).
    

![image-20260624-163136.png](images/image-20260624-163136.png)

* * *

# Etapa 5: Efetivação

Nesta etapa, A ITP deve:

-   Exibir o resultado da solicitação com a pendência de aprovação.
    

REQ.PG-15100 a 15200#F4F5F7

## Requisitos - ITP

**Cenário: Pendência de aprovação**

-   `REQ.PG-15100` Informar que a solicitação está pendente e será confirmada após aprovação dos demais aprovadores.  
    Ex.: A transação só será concluída após confirmação de todos os aprovadores.
    
-   `REQ.PG-15200` Informar o usuário solicitante sobre o prazo para atuação dos demais representantes e da necessidade de reinício do processo se o prazo expirar.   
    Ex.: Os aprovadores têm até DD/MM/AAAA às HH:MM para confirmar a transação. Após essa data, uma nova ordem de pagamento deverá ser criada.
    

![image-20260624-163247.png](images/image-20260624-163247.png)

* * *

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Agendado, Pix Automático e Transferências Inteligentes

**Jornada**

Múltiplos Aprovadores (hybrid flow e JSR)

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.PG-13700`

**Texto**

Seguir os poderes vigentes para movimentação de conta, conforme as políticas internas da instituição (Ex.: Estatutos e contratos sociais), assegurando que as jornadas de iniciação de pagamento adotem a mesma dinâmica de alçadas e filas de aprovação já aplicáveis a pagamentos fora do Open Finance, sem a criação de regras específicas.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Agendado, Pix Automático e Transferências Inteligentes

**Jornada**

Múltiplos Aprovadores (hybrid flow e JSR)

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.PG-13800`

**Texto**

Estender para o âmbito do Open Finance os mecanismos já disponibilizados nos canais da instituição que permitam a representantes legais devidamente constituídos autorizar ou delegar poderes a outras pessoas.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Agendado, Pix Automático e Transferências Inteligentes

**Jornada**

Múltiplos Aprovadores via hybrid flow

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.PG-13900`

**Texto**

Informar o usuário solicitante sobre a necessidade de aprovações adicionais, conforme a política de poderes da instituição.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Agendado, Pix Automático e Transferências Inteligentes

**Jornada**

Múltiplos Aprovadores via hybrid flow

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.PG-14000`

**Texto**

Informar o usuário solicitante sobre o prazo para atuação conforme o tipo de transação.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Agendado, Pix Automático e Transferências Inteligentes

**Jornada**

Múltiplos Aprovadores via hybrid flow

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.PG-14100`

**Texto**

Informar sobre a necessidade de reinício do processo se o prazo expirar.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Agendado, Pix Automático e Transferências Inteligentes

**Jornada**

Múltiplos Aprovadores via hybrid flow

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.PG-14200`

**Texto**

Quando aplicável, exibir mensagem informando o solicitante que o pagamento ultrapassa o limite da conta selecionada e que só será efetuado após a última aprovação necessária, desde que o limite seja ajustado em tempo hábil e de acordo com os critérios da instituição para a conta.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Agendado, Pix Automático e Transferências Inteligentes

**Jornada**

Múltiplos Aprovadores via hybrid flow

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.PG-14300`

**Texto**

Redirecionar o usuário solicitante para a ITP após a confirmação da transação.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Agendado, Pix Automático e Transferências Inteligentes

**Jornada**

Múltiplos Aprovadores (hybrid flow e JSR)

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.PG-14400`

**Texto**

Permitir a atuação do usuário aprovador de forma assíncrona após a confirmação do usuário solicitante.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Agendado, Pix Automático e Transferências Inteligentes

**Jornada**

Múltiplos Aprovadores (hybrid flow e JSR)

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.PG-14500`

**Texto**

Exibir, no mínimo, as mesmas informações da transação apresentadas ao usuário solicitante na etapa de confirmação da transação.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Agendado, Pix Automático e Transferências Inteligentes

**Jornada**

Múltiplos Aprovadores (hybrid flow e JSR)

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.PG-14600`

**Texto**

Exibir identificação do usuário solicitante.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Agendado, Pix Automático e Transferências Inteligentes

**Jornada**

Múltiplos Aprovadores (hybrid flow e JSR)

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.PG-14700`

**Texto**

Quando aplicável, informar sobre demais pendências de aprovação.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Agendado, Pix Automático e Transferências Inteligentes

**Jornada**

Múltiplos Aprovadores (hybrid flow e JSR)

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.PG-14800`

**Texto**

Informar o usuário aprovador sobre o prazo para atuação conforme o tipo de transação.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Agendado, Pix Automático e Transferências Inteligentes

**Jornada**

Múltiplos Aprovadores (hybrid flow e JSR)

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.PG-14900`

**Texto**

Informar sobre a necessidade de reinício do processo se o prazo para aprovação expirar.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Agendado, Pix Automático e Transferências Inteligentes

**Jornada**

Múltiplos Aprovadores via hybrid flow

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.PG-15000`

**Texto**

Após atuação do usuário aprovador, exibir mensagem informando sobre o resultado da solicitação.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Agendado, Pix Automático e Transferências Inteligentes

**Jornada**

Múltiplos Aprovadores (hybrid flow e JSR)

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.PG-15100`

**Texto**

Informar que a solicitação está pendente e será confirmada após aprovação dos demais aprovadores.

trueListe as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Agendado, Pix Automático e Transferências Inteligentes

**Jornada**

Múltiplos Aprovadores (hybrid flow e JSR)

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.PG-15200`

**Texto**

Informar o usuário solicitante sobre o prazo para atuação dos demais representantes e da necessidade de reinício do processo se o prazo expirar.
