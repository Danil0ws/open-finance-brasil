# v.23.00.00 Vinculação de Conta (JSR) via hybrid flow com hand-off

# Visão geral

A Jornada de Iniciação de Pagamento via hybrid flow com hand-off é usada quando há mudança de dispositivo (aplicativo móvel ou desktop) nas etapas de Direcionamento ITP > ID e Redirecionamento ID > ITP.

Por exemplo, o usuário inicia a jornada no aplicativo móvel da ITP, é direcionado para o ambiente desktop da ID e volta para o aplicativo móvel da ITP.

Nesses casos, ambas instituições precisam garantir que as transições sejam seguras, claras e com o mínimo de fricção possível para o usuário.

![image-20260112-175014.png](images/image-20260112-175014.png)

wide760

**Nota**  
Nas interfaces ilustrativas, a Instituição Iniciadora de Transação de Pagamento (ITP) está sendo representada pela marca **Cloud Finance** e a Instituição Detentora de Conta (ID) é a marca **Bratech**.

* * *

# Requisitos e recomendações

Esta seção reúne os requisitos e recomendações aplicáveis à **jornada de Vinculação de Conta (JSR) via hybrid flow com hand-off**.

## Etapas da jornada

2.  Direcionamento
    

4.  Redirecionamento
    

## Cenário de referência

-   Vinculação de Conta imediata entre ITP, dispositivo e ID.
    
-   Alçada simples.
    
-   Redirecionamento entre instituições em dispositivos diferentes.
    

> Jornadas que envolvam o compartilhamento de saldo e limite via Jornada Otimizada devem observar as regras específicas previstas nas páginas correspondentes.

* * *

# Etapa 2: Direcionamento

760Resumo

Após o usuário iniciar a solicitação de vinculação de conta, a Instituição Iniciadora de Transação de Pagamento (ITP) deve direcionar o usuário para o ambiente - aplicativo móvel ou desktop _-_ da Instituição Detentora de Conta (ID) para que o usuário revise e confirme (ou cancele) a solicitação.

REQ.VC-02400 a 02700true

![image-20260611-170904.png](images/image-20260611-170904.png)REQ.VC-02701#F4F5F7

## Requisitos - ID

**Cenário: Recepção do usuário**

-   `REQ.VC-02701` Para direcionamento da ITP em desktop para o aplicativo da ID, receber o usuário com mensagem contendo instruções para continuidade da jornada.
    

![image-20260611-170945.png](images/image-20260611-170945.png)

REC.VC-01200 a 01300true

REC.VC-01301 a 01306

-   `REC.VC-01301` Utilizar o menor número de interações possível para reduzir a fricção na jornada.
    
-   `REC.VC-01302` Exibir mensagem amigável e contextualizada na tela de transição, destacando as vantagens do direcionamento.
    
-   `REC.VC-01303` No desktop, seguir o padrão visual do aplicativo da instituição para garantir segurança e familiaridade ao usuário.
    
-   `REC.VC-01304` Para facilitar o direcionamento do usuário do desktop da ITP para o aplicativo da ID, utilizar mecanismos como QR code dinâmico, código de ativação, entre outros.
    
-   `REC.VC-01305` Utilizar DeepLink nas jornadas iniciadas em dispositivos móveis.
    
-   `REC.VC-01306` Alertar sobre a possibilidade de falha na jornada em dispositivos com o recurso de ocultação de aplicativos ativado, orientando o usuário a desativar esse recurso se necessário.
    

![image-20260415-135610.png](images/image-20260415-135610.png)

REC.VC-01307#F4F5F7

## Recomendações - ID

**Cenário: Recepção do usuário**

-   `REC.VC-01307` Se a ID possuir mais de um canal disponível - aplicativo ou ambiente desktop _-_, disponibilizar a opção de acesso que julgar mais apropriada para a experiência do seu usuário.
    

* * *

# Etapa 4: Redirecionamento

760Resumo

Após o usuário confirmar, cancelar ou o tempo da solicitação expirar, a Instituição Detentora de Conta (ID) deve redirecionar o usuário para o ambiente - aplicativo móvel ou desktop _-_ da Instituição Iniciadora de Transação de Pagamento (ITP) para que ele possa visualizar o resultado da solicitação.

#F4F5F7

## Requisitos - ID

**Cenário: Tela de transição**

-   `REQ.VC-06199` Informar que a próxima etapa será o retorno para a ITP.
    

REQ.VC-06200 a 06500true

![image-20260611-171800.png](images/image-20260611-171800.png)

REC.VC-01700true

![image-20260611-172042.png](images/image-20260611-172042.png)

trueListe as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow com hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-02701`

**Texto**

Para direcionamento de ambiente desktop da ITP para aplicativo da ID, receber o usuário com mensagem com instruções para continuidade da jornada.  true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.VC-06199`

**Texto**

Informar que a próxima etapa será o retorno para a ITP.
