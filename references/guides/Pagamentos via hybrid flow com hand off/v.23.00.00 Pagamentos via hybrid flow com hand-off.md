# v.23.00.00 Pagamentos via hybrid flow com hand-off

# Visão geral

A Jornada de Iniciação de Pagamento via Hybrid flow com Hand-off é usada quando há mudança de dispositivo (aplicativo móvel ou desktop) nas etapas de Direcionamento ITP > ID e Redirecionamento ID > ITP.

Por exemplo, o usuário inicia a jornada no aplicativo móvel da ITP, é direcionado para o ambiente desktop da ID e volta para o aplicativo móvel da ITP.

Nesses casos, ambas instituições precisam garantir que as transições sejam seguras, claras e com o mínimo de fricção possível para o usuário.

![image-20260112-175014.png](images/image-20260112-175014.png)

wide760

**Nota**  
Nas interfaces ilustrativas, a Instituição Iniciadora de Transação de Pagamento (ITP) está sendo representada pela marca **Cloud Finance** e a Instituição Detentora de Conta (ID) é a marca **Bratech**.

* * *

# Requisitos e recomendações

Esta seção reúne os requisitos e recomendações aplicáveis às **jornadas de Pagamento** via Open Finance com uso de Hybrid Flow com Hand-off.

## Etapas da jornada

2.  Direcionamento
    

4.  Redirecionamento
    

wide760

Além dos requisitos e recomendações previstos nesta página, aplicam-se a esta jornada aqueles descritos nas etapas de **Direcionamento** em:

-   Pix via Hybrid Flow;
    
-   Pix com vencimento através de QR Code dinâmico via Hybrid Flow;
    
-   Pix Agendado via Hybrid Flow;
    
-   Pix Automático via Hybrid Flow;
    
-   Transferências Inteligentes via Hybrid Flow;
    
-   Regulamentação e documentos do arranjo de pagamento vigentes.
    

* * *

# Etapa 2: Direcionamento

Após o usuário iniciar a solicitação de pagamento, a Instituição Iniciadora de Transação de Pagamento (ITP) deve direcionar o usuário para o ambiente - app ou browser (desktop) _-_ da Instituição Detentora de Conta (ID) para que o usuário revise e confirme (ou cancele) a solicitação.

REQ.PG-03200 a 03400true

REQ.PG-03402

-   `REQ.PG-03402` Na tela do direcionamento, informar o tempo que o usuário possui para confirmar a solicitação de autorização de pagamento na ID conforme definido pelo tipo de transação.  
    Ex.: Você tem até xx minutos para confirmar a transação
    

![image-20251123-170315.png](images/image-20251123-170315.png)REQ.PG-03403#F4F5F7

## Requisitos - ID

**Cenário: Recepção do usuário**

-   `REQ.PG-03403` Para direcionamento do ambiente desktop da ITP para aplicativo da ID, receber o usuário com mensagem com instruções para continuidade da jornada.  
    

![image-20251123-170436.png](images/image-20251123-170436.png)wide760#F4F5F7

## Recomendações - ITP

**Cenário: Tela de transição**

REC.PG-01200true

REC.PG-01201 a 01202

-   `REC.PG-01201` Utilizar o menor número de interações possível para reduzir a fricção na jornada.
    
-   `REC.PG-01202` Apresentar uma mensagem amigável e contextualizada na tela de transição, destacando as vantagens do direcionamento.
    

REC.PG-01500true

REC.PG-01501

-   `REC.PG-01501` No ambiente desktop, seguir o padrão visual do aplicativo da instituição para garantir segurança e familiaridade ao usuário.
    

REC.PG-01502 a 01503

-   `REC.PG-01502` Para facilitar o direcionamento do usuário do ambiente desktop da ITP para o aplicativo da ID, utilizar mecanismos como QR code dinâmico, código de ativação, entre outros.
    
-   `REC.PG-01503` Utilizar DeepLink nas jornadas iniciadas em dispositivos móveis.
    

![image-20251123-170806.png](images/image-20251123-170806.png)REC.PG-01504#F4F5F7

## Recomendações - ID

**Cenário: Recepção do usuário**

-   `REC.PG-01504` Caso a ID possua mais de um canal disponível - aplicativo ou ambiente desktop _-_, disponibilizar a opção de acesso que julgar mais apropriada para a experiência do seu usuário.
    

* * *

# Etapa 4: Redirecionamento

Após o usuário confirmar, cancelar ou o tempo da solicitação expirar, a Instituição Detentora de Conta (ID) deve redirecionar o usuário para o ambiente - app ou browser (desktop) _-_ da Instituição Iniciadora de Transação de Pagamento (ITP) para que ele possa visualizar o resultado da solicitação.

wide760#F4F5F7

## Requisitos - ID

**Cenário: Tela de transição**

REQ.PG-06299

-   `REQ.PG-06299` Exibir mensagem informando que a próxima etapa será o retorno para a ITP.
    

REQ.PG-06300 a 06600true

![image-20251123-171103.png](images/image-20251123-171103.png)REQ.PG-01505#F4F5F7

## Recomendações - ID

**Cenário: Tela de transição**

-   `REC.PG-01505` No ambiente desktop, ao identificar que o usuário confirmou, cancelou ou que o tempo expirou, exibir a página de redirecionamento para a ITP.
    

![image-20251123-171345.png](images/image-20251123-171345.png)

* * *

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Agendado, Pix Automático, Pix Saque e Pix Troco e Transferências Inteligentes

**Jornada**

Hybrid Flow com Hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 637

**ID**

`REQ.PG-03402`

**Texto**

Na tela do direcionamento, informar o tempo que o usuário possui para confirmar a solicitação de autorização de pagamento na ID conforme definido pelo tipo de transação.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Agendado, Pix Automático, Pix Saque e Pix Troco e Transferências Inteligentes

**Jornada**

Hybrid Flow com Hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.PG-03403`

**Texto**

Para direcionamento do ambiente desktop da ITP para aplicativo da ID, receber o usuário com mensagem com instruções para continuidade da jornada.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Agendado, Pix Automático, Pix Saque e Pix Troco e Transferências Inteligentes

**Jornada**

Hybrid Flow com Hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.PG-06299`

**Texto**

Exibir mensagem informando que a próxima etapa será o retorno para a ITP.
