# v.23.00.00 Gestão de Pix

Esta página reúne os requisitos e recomendações para **gestão de transações de pagamentos imediatos com Pix** **com ou sem redirecionamento (JSR)**, via Open Finance.

* * *

# Gestão na ITP

Esta seção reúne os requisitos e recomendações para gestão de Pix na Instituição Iniciadora de Transação de Pagamento (ITP).

* * *

## Gestão dos pagamentos na ITP

![image-20260616-191143.png](images/image-20260616-191143.png)

wide760#F4F5F7

## Requisitos - ITP

REQ.PG-08200

**Cenário: Acesso ao Open Finance**

-   `REQ.PG-08200` Disponibilizar acesso ao ambiente Open Finance nos seus canais, incluindo-o no primeiro nível do menu principal, para garantir acesso rápido e fácil ao usuário.
    

![image-20260615-200221.png](images/image-20260615-200221.png)

REQ.PG-08300 a 08500

**Cenário: Acesso à gestão de pagamentos**

-   `REQ.PG-08300` Disponibilizar, dentro do ambiente Open Finance, ambiente para gestão de autorizações de pagamentos e pagamentos quando oferecer serviços de Pix Saque e Pix Troco, Pix Agendado, Pix Automático e/ou Transferências Inteligentes.
    
-   `REQ.PG-08400` Disponibilizar, dentro do Open Finance, ambiente para gestão de contas vinculadas, autorizações e pagamentos quando atuar também no escopo de compartilhamento de dados.
    
-   `REQ.PG-08500` Quando atuar no escopo de compartilhamento de dados, diferenciar, com clareza, a área para gestão de compartilhamento de dados da área para gestão de pagamentos.
    

![image-20260615-200442.png](images/image-20260615-200442.png)

REQ.PG-08600

-   `REQ.PG-08600` Quando a área de gestão de pagamentos não for obrigatória, diferenciar, com clareza, no histórico, os pagamentos realizados via Open Finance daqueles realizados diretamente na instituição.    
    Ex.: filtros ou iconografia.
    

REQ.PG-08700

**Cenário: Histórico dos pagamentos**

-   `REQ.PG-08700` Permitir a consulta ao histórico de pagamentos e seus respectivos status.
    

REQ.PG-08701 a 08702

**Cenário: Exibição dos status das solicitações**

-   `REQ.PG-08701` Se a instituição disponibilizar o status (pagamento/agendamento/solicitação) “Em processamento”, exibir ao usuário seguindo a matriz de status.
    
-   `REQ.PG-08702` Sempre exibir os status (pagamento/agendamento/solicitação) “Não concluído/a” e (pagamento/agendamento/solicitação) “Concluído/a ou Ativo/a”.
    

REQ.PG-08703

-   `REQ.PG-08703` Se a instituição disponibilizar o cenário de múltiplos aprovadores, exibir o status “Aguardando aprovação” (do pagamento/agendamento/solicitação) para todos os usuários necessários e envolvidos nessa operação.
    

![image-20260615-203226.png](images/image-20260615-203226.png)

REQ.PG-08800

**Cenário: Comprovante dos pagamentos**

-   `REQ.PG-08800` Para o comprovante de cada pagamento, além das informações descritas neste cenário, exibir quaisquer outras informações exigidas pelo arranjo de pagamento para comprovante de pagamento.
    

REQ.PG-07000true

REQ.PG-07100true

REQ.PG-07200true

REQ.PG-07300 true

REQ.PG-07400true

REQ.PG-07500true

REQ.PG-07600true

REQ.PG-07700true

![image-20260616-190257.png](images/image-20260616-190257.png)

REQ.PG-08900

-   `REQ.PG-08900` Para solicitações com status como Agendado, Não concluído, Cancelado, Expirado, Rejeitado, Em análise ou Pendente de aprovação, exibir o status e os campos aplicáveis, conforme definido pelo arranjo de pagamento.
    

![image-20260616-190327.png](images/image-20260616-190327.png)

wide760#F4F5F7

## Recomendações - ITP

REC.PG-02200 a 02300

**Cenário: Onboarding Open Finance**

-   `REC.PG-02200` Na primeira utilização do usuário, realizar onboarding objetivo, exibindo as funcionalidades oferecidas pela instituição no ambiente Open Finance.
    
-   `REC.PG-02300`Exibir link de acesso à **Área do Cidadão** para consulta de informações relacionadas ao Open Finance.
    

![image-20260616-190415.png](images/image-20260616-190415.png)REC.PG-02301

**Cenário: Ambiente Open Finance**

-   `REC.PG-02301` Na tela inicial da área de gestão do Open Finance, exibir opções como “O que é o Open Finance?” e “Ler Termos de Uso” facilitando o acesso a informações essenciais sobre o funcionamento e os direitos do usuário no Open Finance.
    

![image-20260624-215716.png](images/image-20260624-215716.png)

REC.PG-02400

**Cenário: Acesso à gestão de pagamentos**

-   `REC.PG-02400` Permitir que a gestão de transações de pagamento via Open Finance também seja feita na área Pix da instituição. 
    

![image-20260615-202302.png](images/image-20260615-202302.png)

REC.PG-02500

**Cenário: Histórico dos pagamentos**

-   `REC.PG-02500` Permitir a ordenação (por data, recebedor, status) e o filtro de status na consulta ao histórico dos pagamentos.
    

![image-20260615-203307.png](images/image-20260615-203307.png)

* * *

# Gestão na ID

Esta seção reúne os requisitos e recomendações para gestão de Pix na Instituição Detentora de Conta (ID).

* * *

## Gestão dos pagamentos na ID

![image-20260616-190811.png](images/image-20260616-190811.png)

wide760#F4F5F7

## Requisitos - ID

REQ.PG-08200true

![image-20260615-202641.png](images/image-20260615-202641.png)

REQ.PG-08201 a 08202

**Cenário: Acesso à gestão de pagamentos**

-   `REQ.PG-08201` Disponibilizar, dentro do ambiente Open Finance, áreas para gestão de contas vinculadas, autorizações de pagamentos e pagamentos.
    
-   `REQ.PG-08202` Se apresentar Termos e Condições, exibi-los somente na área de gestão Open Finance.
    

![image-20260615-202836.png](images/image-20260615-202836.png)

REQ.PG-08700true

REQ.PG-08701 a 08702true

REQ.PG-08703true

REQ.PG-08704

-   `REQ.PG-08704` Não exibir o status (pagamento/solicitação) “Solicitado/a” ao usuário.
    

![image-20260615-203634.png](images/image-20260615-203634.png)

REQ.PG-08800true

REQ.PG-07200true

REQ.PG-07300 true

REQ.PG-07400true

REQ.PG-07500true

REQ.PG-07600true

REQ.PG-07700true

REQ.PG-07800true

REQ.PG-07900true

REQ.PG-08000true

![image-20260616-190914.png](images/image-20260616-190914.png)

REQ.PG-08900true

![image-20260616-190945.png](images/image-20260616-190945.png)

wide760#F4F5F7

## Recomendações - ID

REC.PG-02200 a 02300true

![image-20260615-204630.png](images/image-20260615-204630.png)

REC.PG-02400true

![image-20260624-215939.png](images/image-20260624-215939.png)

REC.PG-02500true

![image-20260615-204746.png](images/image-20260615-204746.png)

REC.PG-02500true

![image-20260615-204903.png](images/image-20260615-204903.png)

* * *

Matriz de status de pagamentos

## Status da iniciação de pagamentos

Para padronizar e facilitar o entendimento do usuário nas Jornadas de Iniciação de Pagamento, mostramos a seguir os status que devem ser apresentados ao usuário.

A tabela tem como objetivo deixar claro o De-Para entre o status apresentado para o usuário e os status técnicos das APIs.

Para exibir o status final ao usuário, deve-se seguir esta matriz de status do “Consentimento” vs Status “Payments”:

**STATUS PARA O USUÁRIO FINAL**

**STATUS DE CONSENTIMENTO**

**STATUS DO** `GET/PIX/PAYMENTS/{PAYMENTID}`

**(Pagamento) Solicitado**

CONSUMED (Etapa de Efetivação)

`RCVD` (Received)

**(Pagamento) Agendado**

CONSUMED

`SCHD` (Processo de agendamento realizado)

**(Consentimento) Aguardando aprovação de multiplas alçadas**

PARTIALLY ACCEPTED

N/A

**(Pagamento) Pendente**

CONSUMED

`PDNG` (Pendente)

**(Pagamento) Em Processamento**

CONSUMED

`ACCP` (Pagamento pronto para ser enviado para liquidação)   `ACPD` (Pagamento enviado para liquidação)

**(Pagamento) Rejeitado pelo usuário ou detentor**

CONSUMED

`RJCT` (Rejeitado)

**(Pagamento) Concluído**

CONSUMED

`ACSC` (Pagamento liquidado)

**(Pagamento) Cancelado**

REJECTED   
CONSUMED

N/A  
`CANC` (Transação cancelada a pedido do usuário)

**Agendamento cancelado**

CONSUMED

`CANC` (Transação cancelada a pedido do usuário)

**(Pagamento) Solicitado**

AUTHORISED (Etapa de Efetivação)

`RCVD` (Received)

**(Pagamento) Pendente**

AUTHORISED

`PDNG` (Pendente)

**(Pagamento) Em Processamento**

AUTHORISED

`ACCP` (Pagamento pronto para ser enviado para liquidação)   `ACPD` (Pagamento enviado para liquidação)

**(Pagamento) Rejeitado pelo usuário ou detentor**

AUTHORISED

`RJCT` (Rejeitado)

**(Pagamento) Concluído**

AUTHORISED

`ACSC` (Pagamento liquidado)

**(Pagamento) Cancelado**

AUTHORISED

`CANC` (Transação cancelada a pedido do usuário)

**(Consentimento) Rejeitado pelo usuário ou detentor**

REJECTED

N/A

**(Consentimento) Revogado pelo usuário, pelo detentor ou pelo iniciador**

REVOKED

Qualquer status de pagamento que seja diferente de `RCVD` ou `SCHD`

**(Consentimento) Aguardando aprovação de multiplas alçadas**

PARTIALLY ACCEPTED

N/A

**(Consentimento) Aguardando aprovação**

AWAITING AUTHORISATION

N/A

**(Consentimento) atingiu o seu limite (Prazo ou valor)**

CONSUMED

`RJCT` (Rejeitado)    
`ACSC` (Pagamento liquidado)   `CANC` (Transação cancelada a pedido do usuário)

* * *

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

IN BCB 760

**ID**

`REQ.PG-08200`

**Texto**

Permitir acesso ao ambiente Open Finance nos seus canais, incluindo-o no primeiro nível do menu principal, para garantir acesso rápido e fácil ao usuário.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

IN BCB 760

**ID**

`REQ.PG-08300`

**Texto**

Disponibilizar, dentro do ambiente Open Finance, áreas para gestão de autorizações de pagamentos e pagamentos quando oferecer serviços de Pix Saque e Pix Troco, Pix Agendado, Pix Automático e/ou Transferências Inteligentes.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Agilidade, Transparência e clareza, Conveniência e controle - IN BCB 760

**ID**

`REQ.PG-08400`

**Texto**

Disponibilizar, dentro do Open Finance, ambiente para gestão de contas vinculadas, autorizações e pagamentos quando atuar também no escopo de compartilhamento de dados.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Agilidade, Transparência e clareza, Conveniência e controle - IN BCB 760

**ID**

`REQ.PG-08500`

**Texto**

Quando atuar no escopo de compartilhamento de dados, diferenciar, com clareza, a área para gestão de compartilhamento de dados da área para gestão de pagamentos.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Agilidade, Transparência e clareza, Conveniência e controle - IN BCB 760

**ID**

`REQ.PG-08600`

**Texto**

Quando a área de gestão de pagamentos não for obrigatória, diferenciar, com clareza, no histórico, os pagamentos realizados via Open Finance daqueles realizados diretamente na instituição.    
Ex.: filtros ou iconografia.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-08700`

**Texto**

Permitir a consulta ao histórico de pagamentos e seus respectivos status.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

**ID**

`REQ.PG-08701`

**Texto**

Se a instituição disponibilizar o status (pagamento/agendamento/solicitação) “Em processamento”, exibir ao usuário seguindo a matriz de status.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

**ID**

`REQ.PG-08702`

**Texto**

Sempre exibir os status (pagamento/agendamento/solicitação) “Não concluído/a” e (pagamento/agendamento/solicitação) “Concluído/a”.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Transferências Inteligentes

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

**ID**

`REQ.PG-08703`

**Texto**

Se a instituição disponibilizar o cenário de múltiplos aprovadores, exibir o status “Aguardando aprovação” (do pagamento/agendamento/solicitação) para todos os usuários necessários e envolvidos nessa operação.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Gestão

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.PG-08704`

**Texto**

Não exibir o status “(pagamento/agendamento/solicitação) solicitado” ao usuário.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-08800`

**Texto**

Para o comprovante de cada pagamento, além das informações descritas neste cenário, exibir quaisquer outras informações exigidas pelo arranjo de pagamento para comprovante de pagamento.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-08900`

**Texto**

Para solicitações com status como Agendado, Não concluído, Cancelado, Expirado, Rejeitado, Em análise ou Pendente de aprovação, exibir o status com clareza e os campos aplicáveis, conforme definido pelo arranjo de pagamento.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Gestão

**Proposta**

**Instituição**

ID

**Justificativa**

IN BCB 760

**ID**

`REQ.PG-08201`

**Texto**

Disponibilizar, dentro do ambiente Open Finance, áreas para gestão de contas vinculadas, autorizações de pagamentos e pagamentos.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

IN BCB 760

**ID**

`REQ.PG-08202`

**Texto**

Se apresentar Termos e Condições, exibi-los somente na área de gestão Open Finance.
