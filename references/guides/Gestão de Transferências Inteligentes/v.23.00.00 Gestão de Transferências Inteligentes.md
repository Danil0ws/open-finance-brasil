# v.23.00.00 Gestão de Transferências Inteligentes

Esta página reúne os requisitos e recomendações para gestão de autorizações e transações de pagamentos com **Transferências Inteligentes via Open Finance com ou sem autorização de compartilhamento de saldo e limite via** **Jornada Otimizada** **(JO)**.

Nota.Regulamentação e Arranjotrue

* * *

# Gestão na ITP

Esta seção reúne os requisitos e recomendações para gestão de Transferências Inteligentes na Instituição Iniciadora de Transação de Pagamento (ITP).

* * *

## Gestão das autorizações na ITP

![image-20260624-140328.png](images/image-20260624-140328.png)

REQ.PG-08200true

![image-20260615-200221.png](images/image-20260615-200221.png)

REQ.PG-08300 a 08500true

![image-20260615-200442.png](images/image-20260615-200442.png)

REQ.PG-08601true

![image-20260623-185917.png](images/image-20260623-185917.png)

REQ.PG-08701 a 08702true

REQ.PG-08703true

![image-20260623-185938.png](images/image-20260623-185938.png)

REQ.PG-08603true

![image-20260623-175734.png](images/image-20260623-175734.png)

REQ.PG-08605true

REQ.PG-06901true

REQ.PG-06904true

REQ.PG-07203true

REQ.PG-07300 true

REQ.PG-07400true

wide760

**Nota**

Como as Transferências Inteligentes ocorrem exclusivamente entre contas de mesma titularidade, a ITP pode, se desejar, exibir as informações de identificação do pagador e do recebedor de forma consolidada no comprovante.

Ex.:  
Titular  
Maria da Silva

\*\*\*.222.333-\*\*.

REQ.PG-07600true

REQ.PG-07601true

REQ.PG-07602true

REQ.PG-07603true

REQ.PG-07604true

REQ.PG-07700true

REQ.PG-07803true

![image-20260623-180237.png](images/image-20260623-180237.png)REQ.PG-07806 a 07807

**Cenário: Alteração da autorização de pagamento**

-   `REQ.PG-07806` Quando a ITP não for a instituição detentora da conta recebedora, permitir que o usuário inclua, altere ou exclua contas recebedoras de mesma titularidade nas autorizações ativas.
    
-   `REQ.PG-07807` Se a ITP disponibilizar mais de uma opção de gatilho/objetivo de transferência, permitir que o usuário possa alterá-las.
    

![image-20260623-184417.png](images/image-20260623-184417.png)

REQ.PG-08900true

![image-20260624-130553.png](images/image-20260624-130553.png)

**Cenário: Experiência de alteração**

Na área de gestão de pagamento da ITP, para evitar o reinício do processo de criação de uma autorização de pagamento, o usuário pode ter a experiência de alteração de parâmetros como ID pagadora, o prazo da autorização, o valor ou limites transacionais, embora, no backend, esteja cancelando a autorização vigente e criando uma nova autorização de pagamento.  
Nesses casos, o usuário deverá passar pelo fluxo completo, envolvendo o direcionamento para a ID, confirmação e redirecionamento para ITP para efetivação da solicitação.

REQ.PG-08907true  
Ex.: **Tudo certo!** A autorização anterior foi cancelada e uma nova foi criada com a sua nova instituição.

![image-20260623-184609.png](images/image-20260623-184609.png)

REQ.PG-08908true

REQ.PG-08909true

REQ.PG-08910true

![image-20260623-184831.png](images/image-20260623-184831.png)

REC.PG-02200 a 02300true

![image-20260616-190415.png](images/image-20260616-190415.png)

REC.PG-02301true

![image-20260624-215716.png](images/image-20260624-215716.png)

REC.PG-02400true

![image-20260615-202302.png](images/image-20260615-202302.png)

REC.PG-02401true

![image-20260623-185015.png](images/image-20260623-185015.png)

REC.PG-02402true

![image-20260623-185054.png](images/image-20260623-185054.png)REC.PG-02405

-   `REC.PG-02405` Permitir que o usuário crie um apelido para cada uma de suas contas recebedoras.     
    Exs.: Investimentos, Poupança para Viagem etc
    

![image-20260623-185140.png](images/image-20260623-185140.png)

REC.PG-02406true

REC.PG-02900true  
Ex.: Tem certeza que quer cancelar a autorização? Essa ação não pode ser desfeita e resultará no cancelamento de todas as transferências futuras vinculadas.

![image-20260623-185326.png](images/image-20260623-185326.png)

* * *

## Gestão do compartilhamento de saldo e limite via Jornada Otimizada na ITP

Esta seção reúne os requisitos e recomendações para gestão de compartilhamento de saldo e limite da conta pagadora concedido via Jornada Otimizada na jornada de Transferências Inteligentes na Instituição Iniciadora de Transação de Pagamento (ITP).

wide760

**Nota**

Consulte a página **Gestão de Compartilhamento de Dados** para mais informações sobre o comprovante do compartilhamento de dados de saldo e limite.

wide760#F4F5F7

## Requisitos - ITP

REQ.PG-08602

**Cenário: Histórico das autorizações de pagamento com compartilhamento de saldo e limite via Jornada Otimizada**

-   `REQ.PG-08602` Sinalizar, de forma clara, no histórico das autorizações de pagamento, aquelas para os quais o usuário optou por compartilhar o saldo e limite.  
    Ex.: tag “Saldo e limite compartilhados”
    

![image-20260623-185631.png](images/image-20260623-185631.png)

**Cenário: Comprovante das autorizações de pagamento com compartilhamento de saldo e limite via Jornada Otimizada**

REQ.PG-07804true

REQ.PG-07808

-   `REQ.PG-07808` Exibir o escopo dos dados compartilhados.
    

![image-20260623-190206.png](images/image-20260623-190206.png)REQ.PG-08911

**Cenário: Cancelamento da autorização de pagamento com compartilhamento de saldo e limite via Jornada Otimizada**

-   `REQ.PG-08911` Ao optar pelo cancelamento da autorização do pagamento, informar ao usuário que o compartilhamento de saldo e limite da conta pagadora também será cancelado.​
    

![image-20260623-190340.png](images/image-20260623-190340.png)REQ.PG-11300 a 11400

**Cenário: Cancelamento do compartilhamento de saldo e limite da conta via Jornada Otimizada**

-   `REQ.PG-11300` Permitir o cancelamento, a qualquer momento, do compartilhamento de saldo e limite da conta pagadora concedido via Jornada Otimizada.
    
-   `REQ.PG-11400` Ao optar pelo cancelamento do compartilhamento de saldo e limite da conta pagadora concedido via Jornada Otimizada, informar ao usuário que a autorização de pagamento se mantém ativa.
    

![image-20260623-190543.png](images/image-20260623-190543.png)wide760#F4F5F7

## Recomendações - ITP

REC.PG-03700 a 03800

**Cenário: Cancelamento do compartilhamento de saldo e limite da conta via Jornada Otimizada**

-   `REC.PG-03700` Ao optar pelo cancelamento do compartilhamento de saldo e limite da conta pagadora concedido via Jornada Otimizada, exibir mensagem informando sobre os benefícios de manter a funcionalidade.
    
-   `REC.PG-03800` Incluir informação adicional sobre o compartilhamento de saldo e limite da conta pagadora através da Jornada Otimizada por meio de link, botão, imagem, texto etc.
    

![image-20260623-190641.png](images/image-20260623-190641.png)

* * *

## Gestão dos pagamentos na ITP

wide760#F4F5F7

## Requisitos - ITP

REQ.PG-08700true

REQ.PG-08701 a 08702true

REQ.PG-08703true

![image-20260624-125050.png](images/image-20260624-125050.png)

REQ.PG-08800true

REQ.PG-07000true

REQ.PG-07100true

REQ.PG-07200true

REQ.PG-07203true

REQ.PG-07300 true

REQ.PG-07400true

REQ.PG-07600true

REQ.PG-07601

-   `REQ.PG-07601` Exibir o gatilho/objetivo que originou a transferência, quando aplicável.
    

REQ.PG-07700true

![image-20260624-125943.png](images/image-20260624-125943.png)

REQ.PG-08900true

![image-20260624-130314.png](images/image-20260624-130314.png)

REC.PG-02500true

![image-20260422-142340.png](images/image-20260422-142340.png)

* * *

# Gestão na ID

Esta seção reúne os requisitos e recomendações para gestão de Transferências Inteligentes na Instituição Detentora de Conta (ID).

* * *

## Gestão das autorizações na ID

![image-20260624-133712.png](images/image-20260624-133712.png)wide760#F4F5F7

## Requisitos - ID

REQ.PG-08200true

![image-20260615-202641.png](images/image-20260615-202641.png)

REQ.PG-08201 a 08202true

![image-20260615-202836.png](images/image-20260615-202836.png)

REQ.PG-08601true

![image-20260624-131008.png](images/image-20260624-131008.png)

REQ.PG-08701 a 08702true

REQ.PG-08703true

REQ.PG-08704true

![image-20260624-131131.png](images/image-20260624-131131.png)

REQ.PG-08604true

![image-20260624-131405.png](images/image-20260624-131405.png)

REQ.PG-08605true

REQ.PG-06901true

REQ.PG-06904true

REQ.PG-07203true

REQ.PG-07300 true

REQ.PG-07600true

REQ.PG-07604true

REQ.PG-07700true

REQ.PG-07800true

REQ.PG-07801true

![image-20260624-131836.png](images/image-20260624-131836.png)

REQ.PG-08908true

REQ.PG-08909true

REQ.PG-08910true

![image-20260624-132201.png](images/image-20260624-132201.png)

REC.PG-02200 a 02300true

![image-20260615-204630.png](images/image-20260615-204630.png)

REC.PG-02301true

![image-20260624-215939.png](images/image-20260624-215939.png)

REC.PG-02400true

![image-20260615-204746.png](images/image-20260615-204746.png)

REC.PG-02401true

![image-20260624-132716.png](images/image-20260624-132716.png)wide760#F4F5F7

## Recomendações - ID

REC.PG-02402true

![image-20260624-133352.png](images/image-20260624-133352.png)

REC.PG-02404true

![image-20260624-133434.png](images/image-20260624-133434.png)

REC.PG-02406true

REC.PG-02900true  
Ex.: Tem certeza que quer cancelar a autorização? Essa ação não pode ser desfeita e resultará no cancelamento de todas as transferências futuras vinculadas.

![image-20260624-133603.png](images/image-20260624-133603.png)

* * *

## Gestão do compartilhamento de saldo e limite via Jornada Otimizada na ID

Esta seção reúne os requisitos e recomendações para gestão de compartilhamento de saldo e limite da conta pagadora concedido via Jornada Otimizada na jornada de Transferências Inteligentes na Instituição Detentora de Conta (ID).

wide760#F4F5F7

## Requisitos - ID

REQ.PG-08602true

![image-20260624-133744.png](images/image-20260624-133744.png)

**Cenário: Comprovante das autorizações de pagamento com compartilhamento de saldo e limite via Jornada Otimizada**

REQ.PG-07804true

REQ.PG-07808true

![image-20260624-134036.png](images/image-20260624-134036.png)

REQ.PG-08911true

![image-20260624-134206.png](images/image-20260624-134206.png)

REQ.PG-11300 a 11400true

![image-20260624-134340.png](images/image-20260624-134340.png)

wide760#F4F5F7

## Recomendações - ID

REC.PG-03700 a 03800true

![image-20260624-134610.png](images/image-20260624-134610.png)

* * *

## Gestão dos pagamentos na ID

wide760#F4F5F7

## Requisitos - ID

REQ.PG-08700true

![image-20260624-135013.png](images/image-20260624-135013.png)

REQ.PG-08701 a 08702true

REQ.PG-08703true

REQ.PG-08704true

![image-20260624-135102.png](images/image-20260624-135102.png)

REQ.PG-08800true

REQ.PG-07000true

REQ.PG-07100true

REQ.PG-07200true

REQ.PG-07203true

REQ.PG-07400true

REQ.PG-07600true

REQ.PG-07700true

REQ.PG-07800true

![image-20260624-140218.png](images/image-20260624-140218.png)

REQ.PG-08900true

![image-20260624-140152.png](images/image-20260624-140152.png)

REC.PG-02500true

![image-20260624-135955.png](images/image-20260624-135955.png)

* * *

Matriz de status de pagamentostrue

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Transferências Inteligentes

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Transparência e clareza, Conveniência e controle, Segurança e privacidade - IN BCB 760

**ID**

`REQ.PG-07806`

**Texto**

Quando a ITP não for a instituição detentora da conta recebedora, permitir que o usuário inclua, altere ou exclua contas recebedoras de mesma titularidade nas autorizações ativas.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Transferências Inteligentes

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Transparência e clareza, Conveniência e controle, Segurança e privacidade - IN BCB 760

**ID**

`REQ.PG-07807`

**Texto**

Se a ITP disponibilizar mais de uma opção de gatilho/objetivo de transferência, permitir que o usuário possa alterá-las.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Transferências Inteligentes

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

Experiência do usuário, Transparência e clareza, Conveniência e controle, Segurança e privacidade - IN BCB 760

**ID**

`REQ.PG-07808`

**Texto**

Exibir o escopo dos dados compartilhados.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Transferências Inteligentes

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

Experiência do usuário, Transparência e clareza, Conveniência e controle, Segurança e privacidade - IN BCB 760

**ID**

`REQ.PG-08602`

**Texto**

Sinalizar, de forma clara, no histórico das autorizações de pagamento, aquelas para os quais o usuário optou por compartilhar o saldo e limite.  
Ex.: tag “Saldo e limite compartilhados”

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Transferências Inteligentes

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

Experiência do usuário, Transparência e clareza, Conveniência e controle, Segurança e privacidade - IN BCB 760

**ID**

`REQ.PG-08911`

**Texto**

Ao optar pelo cancelamento da autorização do pagamento, informar ao usuário que o compartilhamento de saldo e limite da conta pagadora também será cancelado.​

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Transferências Inteligentes

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

Experiência do usuário, Transparência e clareza, Conveniência e controle, Segurança e privacidade - IN BCB 760

**ID**

`REQ.PG-11300`

**Texto**

Permitir o cancelamento, a qualquer momento, do compartilhamento de saldo e limite da conta pagadora concedido via Jornada Otimizada.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Transferências Inteligentes

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

Experiência do usuário, Transparência e clareza, Conveniência e controle, Segurança e privacidade - IN BCB 760

**ID**

`REQ.PG-11400`

**Texto**

Ao optar pelo cancelamento do compartilhamento de saldo e limite da conta pagadora concedido via Jornada Otimizada, informar ao usuário que a autorização de pagamento se mantém ativa.
