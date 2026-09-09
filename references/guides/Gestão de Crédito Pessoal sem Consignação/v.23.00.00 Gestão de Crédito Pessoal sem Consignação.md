# v.23.00.00 Gestão de Crédito Pessoal sem Consignação

GT.PC - intr

As instituições participantes da jornada de Portabilidade de Crédito (Instituição Proponente (IP) e Instituição Credora (IC)) devem disponibilizar ao usuário, por meio de uma Área de Gestão, a listagem de todos os pedidos realizados, com o tipo de produto, seus respectivos status e informações detalhadas, respeitando o contexto da jornada (síncrona ou assíncrona) e os prazos de exibição definidos para cada situação. 

As instituições também devem permitir que o usuário cancele uma portabilidade que esteja em andamento a qualquer momento antes da fase de liquidação e devem comunicar o cancelamento à outra instituição.

wide760#F4F5F7

## **Requisitos - IP**

**Cenário: Consulta aos pedidos**

REQ.PC-04000

-   `REQ.PC-04000` Exibir os pedidos de Portabilidade de Crédito em estrutura que permita localizar um pedido específico e acessar seus detalhes.  
    Ex.: lista
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-04000`

**Texto**

Exibir os pedidos de Portabilidade de Crédito em estrutura que permita localizar um pedido específico e acessar seus detalhes.

REQ.PC-04100

-   `REQ.PC-04100` No item de exibição, indicar um dos seguintes status individuais para cada pedido: **Pedido em análise, Sem proposta disponível, Proposta disponível, Portabilidade em andamento, Portabilidade cancelada** e **Portabilidade concluída.**
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-04100`

**Texto**

No item de exibição, indicar um dos seguintes status individuais para cada pedido: **Pedido em análise, Sem proposta disponível, Proposta disponível, Portabilidade em andamento, Portabilidade cancelada** e **Portabilidade concluída.**

REQ.PC-04200

-   `REQ.PC-04200` No item de exibição, indicar o tipo de contrato associado a cada pedido: **Consignado Federal** ou **Crédito Pessoal sem Consignação**.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-04200`

**Texto**

No item de exibição, indicar o tipo de contrato associado a cada pedido: **Consignado Federal** ou **Crédito Pessoal sem Consignação**.

![image-20260824-182242.png](images/image-20260824-182242.png)

**Cenário: Pedido em análise**

REQ.PC-04300

-   `REQ.PC-04300` No item de exibição, mostrar o status **Pedido em análise** em jornadas assíncronas, enquanto a IP não finaliza a análise do pedido.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-04300`

**Texto**

No item de exibição, mostrar o status **Pedido em análise** em jornadas assíncronas, enquanto a IP não finaliza a análise do pedido.

REQ.PC-04400

-   `REQ.PC-04400` Manter o item de exibição com o status **Pedido em análise** até a análise ser concluída, conforme prazo determinado pela IP.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-04400`

**Texto**

Manter o item de exibição com o status **Pedido em análise** até a análise ser concluída, conforme prazo determinado pela IP.

REQ.PC-04500

-   `REQ.PC-04500` Na tela de detalhes do status **Pedido em análise**, exibir o motivo do status.  
      
    Ex.: Ainda estamos analisando seu pedido de portabilidade.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-04500`

**Texto**

Na tela de detalhes do status **Pedido em análise**, exibir o motivo do status.

EQ.PC-04600

-   `REQ.PC-04600` Na tela de detalhes do status **Pedido em análise**, exibir os seguintes dados do contrato original:
    
    -   Taxa de juros
        
    -   Valor da parcela
        
    -   Número de parcelas
        
    -   Saldo devedor
        
    -   Número do contrato
        

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-04600`

**Texto**

Na tela de detalhes do status **Pedido em análise**, exibir os seguintes dados do contrato original :

-   Taxa de juros
    
-   Valor da parcela
    
-   Número de parcelas
    
-   Saldo devedor
    
-   Número do contrato
    

RQ.PC-04601

-   `REQ.PC-04601` Na tela de detalhes do status **Pedido em análise**, informar ao usuário que eventuais garantias vinculadas ao contrato original não são transferidas na portabilidade.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação

**Jornada**

Gestão

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-04601`

**Texto**

Na tela de detalhes do status **Pedido em análise**, informar ao usuário que eventuais garantias vinculadas ao contrato original não são transferidas na portabilidade.

REQ.PC-04700

-   `REQ.PC-04700` No caso de jornada assíncrona, na tela de detalhes do status **Pedido em análise**, informar prazo estimado para finalização da análise do pedido.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-04700`

**Texto**

No caso de jornada assíncrona, na tela de detalhes do status **Pedido em análise**, informar prazo estimado para finalização da análise do pedido.

![image-20260826-133431.png](images/image-20260826-133431.png)

**Cenário: Sem proposta disponível**

REQ.PC-04800

-   `REQ.PC-04800` No item de exibição, mostrar o status **Sem proposta disponível** em jornadas assíncronas quando, após o vencimento do prazo de análise, a IP não disponibilizar proposta de portabilidade.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-04800`

**Texto**

No item de exibição, mostrar o status **Sem proposta disponível** em jornadas assíncronas quando, após o vencimento do prazo de análise, a IP não disponibilizar proposta de portabilidade.

REQ.PC-04900

-   `REQ.PC-04900` Manter o item de exibição com o status **Sem proposta disponível** por período definido pela própria Instituição Proponente.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-04900`

**Texto**

Manter o item de exibição com o status **Sem proposta disponível** por período definido pela própria Instituição Proponente.

REQ.PC-05000

-   `REQ.PC-05000` Na tela de detalhes do status **Sem Proposta Disponível**, exibir o motivo do status.  
    Ex.: Não encontramos uma oferta para o seu perfil.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-05000`

**Texto**

Na tela de detalhes do status **Sem Proposta Disponível**, exibir o motivo do status.

![image-20260824-182507.png](images/image-20260824-182507.png)

**Cenário: Proposta disponível**

REQ.PC-05100

-   `REQ.PC-05100` No item de exibição, mostrar o status **Proposta disponível** quando houver uma proposta, mas o usuário ainda não a tiver aceitado ou recusado.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-05100`

**Texto**

No item de exibição, mostrar o status **Proposta disponível** quando houver uma proposta, mas o usuário ainda não a tiver aceitado ou recusado.

REQ.PC-05200

-   `REQ.PC-05200` Manter o item de exibição com o status **Proposta disponível**, por, no mínimo, dois dias, conforme legislação e regulação vigente.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-05200`

**Texto**

Manter o item de exibição com o status **Proposta disponível**, por, no mínimo, dois dias, conforme legislação e regulação vigente.

REQ.PC-05300

-   `REQ.PC-05300` Na tela de detalhes do status **Proposta disponível**, exibir o comparativo entre a proposta e o contrato original com os seguintes itens:
    
    -   Saldo devedor
        
    -   Para (indicando a instituição de destino)
        
    -   De (indicando a instituição de origem)
        
    -   Diferença mensal (indicando o valor de redução/aumento mensal em relação ao contrato de origem)
        
    -   Diferença total (indicando o valor de redução/aumento total em relação ao contrato de origem)
        
    -   Novo prazo (indicando a quantidade de parcelas até o fim do novo contrato)
        
    -   Prazo remanescente (indicando a quantidade de parcelas remanescentes até o fim do contrato de origem)
        
    -   Nova parcela (indicando o valor da parcela do novo contrato)
        
    -   Parcela atual (indicando o valor da parcela do contrato de origem)
        
    -   Nova taxa de juros (indicando a taxa de juros do novo contrato)
        
    -   Taxa de juros atual (indicando a taxa de juros do contrato de origem)
        
    -   Novo CET (indicando o Custo Efetivo Total do novo contrato)
        
    -   CET atual (indicando o Custo Efetivo Total do contrato de origem)
        
    -   Data da primeira parcela do novo contrato
        
    -   Data da última parcela do novo contrato
        

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-05300`

**Texto**

Na tela de detalhes do status **Proposta disponível**, exibir o comparativo entre a proposta e o contrato original com os seguintes itens:

-   Saldo devedor
    
-   Para (indicando a instituição de destino)
    
-   De (indicando a instituição de origem)
    
-   Diferença mensal (indicando o valor de redução/aumento mensal em relação ao contrato de origem)
    
-   Diferença total (indicando o valor de redução/aumento total em relação ao contrato de origem)
    
-   Novo prazo (indicando a quantidade de parcelas até o fim do novo contrato)
    
-   Prazo remanescente (indicando a quantidade de parcelas remanescentes até o fim do contrato de origem)
    
-   Nova parcela (indicando o valor da parcela do novo contrato)
    
-   Parcela atual (indicando o valor da parcela do contrato de origem)
    
-   Nova taxa de juros (indicando a taxa de juros do novo contrato)
    
-   Taxa de juros atual (indicando a taxa de juros do contrato de origem)
    
-   Novo CET (indicando o Custo Efetivo Total do novo contrato)
    
-   CET atual (indicando o Custo Efetivo Total do contrato de origem)
    
-   Data da primeira parcela do novo contrato
    
-   Data da última parcela do novo contrato
    

REQ.PC-05301

-   `REQ.PC-05301` Na tela de detalhes do status **Proposta disponível**, informar ao usuário que eventuais garantias vinculadas ao contrato original não são transferidas na portabilidade.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação

**Jornada**

Gestão

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-05301`

**Texto**

Na tela de detalhes do status **Proposta disponível**, informar ao usuário que eventuais garantias vinculadas ao contrato original não são transferidas na portabilidade.

![image-20260826-133529.png](images/image-20260826-133529.png)

**Cenário: Portabilidade em andamento**

REQ.PC-05400

-   `REQ.PC-05400` No item de exibição, mostrar o status **Portabilidade em andamento** após o usuário aceitar a proposta.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-05400`

**Texto**

No item de exibição, mostrar o status **Portabilidade em andamento** após o usuário aceitar a proposta.

REQ.PC-05500

-   `REQ.PC-05500` Manter o item de exibição com o status **Portabilidade em andamento** até que a portabilidade seja concluída ou cancelada.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-05500`

**Texto**

Manter o item de exibição com o status **Portabilidade em andamento** até que a portabilidade seja concluída ou cancelada.

REQ.PC-05600

-   `REQ.PC-05600` Na tela de detalhes do status **Portabilidade em andamento**, exibir o comparativo entre a proposta aceita e o contrato original com os seguintes itens:
    
    -   Saldo devedor
        
    -   Para (indicando a instituição de destino)
        
    -   De (indicando a instituição de origem)
        
    -   Diferença mensal (indicando o valor de redução/aumento mensal em relação ao contrato de origem)
        
    -   Diferença total (indicando o valor de redução/aumento total em relação ao contrato de origem)
        
    -   Novo prazo (indicando a quantidade de parcelas até o fim do novo contrato)
        
    -   Prazo remanescente (indicando a quantidade de parcelas remanescentes até o fim do contrato de origem)
        
    -   Nova parcela (indicando o valor da parcela do novo contrato)
        
    -   Parcela atual (indicando o valor da parcela do contrato de origem)
        
    -   Nova taxa de juros (indicando a taxa de juros do novo contrato)
        
    -   Taxa de juros atual (indicando a taxa de juros do contrato de origem)
        
    -   Novo CET (indicando o Custo Efetivo Total do novo contrato)
        
    -   CET atual (indicando o Custo Efetivo Total do contrato de origem)
        
    -   Data da primeira parcela do novo contrato
        
    -   Data da última parcela do novo contrato
        

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-05600`

**Texto**

Na tela de detalhes do status **Portabilidade em andamento**, exibir o comparativo entre a proposta aceita e o contrato original com os seguintes itens:

-   Saldo devedor
    
-   Para (indicando a instituição de destino)
    
-   De (indicando a instituição de origem)
    
-   Diferença mensal (indicando o valor de redução/aumento mensal em relação ao contrato de origem)
    
-   Diferença total (indicando o valor de redução/aumento total em relação ao contrato de origem)
    
-   Novo prazo (indicando a quantidade de parcelas até o fim do novo contrato)
    
-   Prazo remanescente (indicando a quantidade de parcelas remanescentes até o fim do contrato de origem)
    
-   Nova parcela (indicando o valor da parcela do novo contrato)
    
-   Parcela atual (indicando o valor da parcela do contrato de origem)
    
-   Nova taxa de juros (indicando a taxa de juros do novo contrato)
    
-   Taxa de juros atual (indicando a taxa de juros do contrato de origem)
    
-   Novo CET (indicando o Custo Efetivo Total do novo contrato)
    
-   CET atual (indicando o Custo Efetivo Total do contrato de origem)
    
-   Data da primeira parcela do novo contrato
    
-   Data da última parcela do novo contrato
    

REQ.PC-05601

-   `REQ.PC-05601` Na tela de detalhes do status **Portabilidade em andamento**, informar ao usuário que eventuais garantias vinculadas ao contrato original não são transferidas na portabilidade.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação

**Jornada**

Gestão

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-05601`

**Texto**

Na tela de detalhes do status **Portabilidade em andamento**, informar ao usuário que eventuais garantias vinculadas ao contrato original não são transferidas na portabilidade.

REQ.PC-05700

-   `REQ.PC-05700` No status **Portabilidade em andamento**, possibilitar que o usuário baixe o contrato assinado da proposta.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-05700`

**Texto**

No status **Portabilidade em andamento**, possibilitar que o usuário baixe o contrato assinado da proposta.

REQ.PC-05800

-   `REQ.PC-05800` Permitir desistência da Portabilidade de Crédito antes da liquidação.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-05800`

**Texto**

Permitir desistência da Portabilidade de Crédito antes da liquidação.

REQ.PC-05900

-   `REQ.PC-05900` Informar que o usuário pode desistir da portabilidade antes da fase da liquidação.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-05900`

**Texto**

Informar que o usuário pode desistir da portabilidade antes da fase da liquidação.

REQ.PC-06000

-   `REQ.PC-06000` Caso a portabilidade entre em fase de liquidação, desabilitar a opção de cancelamento do pedido.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-06000`

**Texto**

Caso a portabilidade entre em fase de liquidação, desabilitar a opção de cancelamento do pedido.

![image-20260826-133639.png](images/image-20260826-133639.png)

**Cenário: Portabilidade cancelada**

REQ.PC-06100

-   `REQ.PC-06100` No item de exibição, mostrar o status **Portabilidade cancelada** quando houver o cancelamento, qualquer que seja o motivo.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-06100`

**Texto**

No item de exibição, mostrar o status **Portabilidade cancelada** quando houver o cancelamento, qualquer que seja o motivo.

REQ.PC-06200

-   `REQ.PC-06200` Manter o item de exibição com o status **Portabilidade cancelada** por 14 dias corridos após o cancelamento.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-06200`

**Texto**

Manter o item de exibição com o status **Portabilidade cancelada** por 14 dias corridos após o cancelamento.

REQ.PC-06300

-   `REQ.PC-06300` Na tela de detalhes do status **Portabilidade cancelada**, exibir um dos motivos do cancelamento:
    
    -   Proposta recusada
        
    -   Proposta expirada
        
    -   Usuário cancelou a portabilidade
        
    -   Proponente cancelou a portabilidade
        
    -   Contraproposta aceita
        

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-06300`

**Texto**

Na tela de detalhes do status **Portabilidade cancelada**, exibir um dos motivos do cancelamento:

-   Proposta recusada
    
-   Proposta expirada
    
-   Usuário cancelou a portabilidade
    
-   Proponente cancelou a portabilidade
    
-   Contraproposta aceita
    

REQ.PC-06400

-   `REQ.PC-06400` Na tela de detalhes do status **Portabilidade cancelada**, exibir o comparativo entre a proposta e o contrato original com os seguintes itens:
    
    -   Saldo devedor
        
    -   Para (indicando a instituição de destino)
        
    -   De (indicando a instituição de origem)
        
    -   Diferença mensal (indicando o valor de redução/aumento mensal em relação ao contrato de origem)
        
    -   Diferença total (indicando o valor de redução/aumento total em relação ao contrato de origem)
        
    -   Novo prazo (indicando a quantidade de parcelas até o fim do novo contrato)
        
    -   Prazo remanescente (indicando a quantidade de parcelas remanescentes até o fim do contrato de origem)
        
    -   Nova parcela (indicando o valor da parcela do novo contrato)
        
    -   Parcela atual (indicando o valor da parcela do contrato de origem)
        
    -   Nova taxa de juros (indicando a taxa de juros do novo contrato)
        
    -   Taxa de juros atual (indicando a taxa de juros do contrato de origem)
        
    -   Novo CET (indicando o Custo Efetivo Total do novo contrato)
        
    -   CET atual (indicando o Custo Efetivo Total do contrato de origem)
        
    -   Data da primeira parcela do novo contrato
        
    -   Data da última parcela do novo contrato
        

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-06400`

**Texto**

Na tela de detalhes do status **Portabilidade cancelada**, exibir o comparativo entre a proposta e o contrato original com os seguintes itens:

-   Saldo devedor
    
-   Para (indicando a instituição de destino)
    
-   De (indicando a instituição de origem)
    
-   Diferença mensal (indicando o valor de redução/aumento mensal em relação ao contrato de origem)
    
-   Diferença total (indicando o valor de redução/aumento total em relação ao contrato de origem)
    
-   Novo prazo (indicando a quantidade de parcelas até o fim do novo contrato)
    
-   Prazo remanescente (indicando a quantidade de parcelas remanescentes até o fim do contrato de origem)
    
-   Nova parcela (indicando o valor da parcela do novo contrato)
    
-   Parcela atual (indicando o valor da parcela do contrato de origem)
    
-   Nova taxa de juros (indicando a taxa de juros do novo contrato)
    
-   Taxa de juros atual (indicando a taxa de juros do contrato de origem)
    
-   Novo CET (indicando o Custo Efetivo Total do novo contrato)
    
-   CET atual (indicando o Custo Efetivo Total do contrato de origem)
    
-   Data da primeira parcela do novo contrato
    
-   Data da última parcela do novo contrato
    

![image-20260824-182920.png](images/image-20260824-182920.png)

**Cenário: Portabilidade concluída**

REQ.PC-06500

-   `REQ.PC-06500` No item de exibição, mostrar o status **Portabilidade concluída** após a portabilidade ter sido finalizada com sucesso.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-06500`

**Texto**

No item de exibição, mostrar o status **Portabilidade concluída** após a portabilidade ter sido finalizada com sucesso.

REQ.PC-06600

-   `REQ.PC-06600` Manter o item de exibição com o status **Portabilidade concluída** por 14 dias corridos após a conclusão.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-06600`

**Texto**

Manter o item de exibição com o status **Portabilidade concluída** por 14 dias corridos após a conclusão.

REQ.PC-06700

-   `REQ.PC-06700` Na tela de detalhes do status **Portabilidade concluída**, exibir o comparativo entre a proposta aceita e o contrato original com os seguintes itens:
    
    -   Saldo devedor
        
    -   Para (indicando a instituição de destino)
        
    -   De (indicando a instituição de origem)
        
    -   Diferença mensal (indicando o valor de redução/aumento mensal em relação ao contrato de origem)
        
    -   Diferença total (indicando o valor de redução/aumento total em relação ao contrato de origem)
        
    -   Novo prazo (indicando a quantidade de parcelas até o fim do novo contrato)
        
    -   Prazo remanescente (indicando a quantidade de parcelas remanescentes até o fim do contrato de origem)
        
    -   Nova parcela (indicando o valor da parcela do novo contrato)
        
    -   Parcela atual (indicando o valor da parcela do contrato de origem)
        
    -   Nova taxa de juros (indicando a taxa de juros do novo contrato)
        
    -   Taxa de juros atual (indicando a taxa de juros do contrato de origem)
        
    -   Novo CET (indicando o Custo Efetivo Total do novo contrato)
        
    -   CET atual (indicando o Custo Efetivo Total do contrato de origem)
        
    -   Data da primeira parcela do novo contrato
        
    -   Data da última parcela do novo contrato
        

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-06700`

**Texto**

Na tela de detalhes do status **Portabilidade concluída**, exibir o comparativo entre a proposta aceita e o contrato original com os seguintes itens:

-   Saldo devedor
    
-   Para (indicando a instituição de destino)
    
-   De (indicando a instituição de origem)
    
-   Diferença mensal (indicando o valor de redução/aumento mensal em relação ao contrato de origem)
    
-   Diferença total (indicando o valor de redução/aumento total em relação ao contrato de origem)
    
-   Novo prazo (indicando a quantidade de parcelas até o fim do novo contrato)
    
-   Prazo remanescente (indicando a quantidade de parcelas remanescentes até o fim do contrato de origem)
    
-   Nova parcela (indicando o valor da parcela do novo contrato)
    
-   Parcela atual (indicando o valor da parcela do contrato de origem)
    
-   Nova taxa de juros (indicando a taxa de juros do novo contrato)
    
-   Taxa de juros atual (indicando a taxa de juros do contrato de origem)
    
-   Novo CET (indicando o Custo Efetivo Total do novo contrato)
    
-   CET atual (indicando o Custo Efetivo Total do contrato de origem)
    
-   Data da primeira parcela do novo contrato
    
-   Data da última parcela do novo contrato
    

REQ.PC-06701

-   `REQ.PC-06701` Na tela de detalhes do status **Portabilidade concluída**, informar ao usuário que eventuais garantias vinculadas ao contrato original não foram transferidas na portabilidade.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação

**Jornada**

Gestão

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-06701`

**Texto**

Na tela de detalhes do status **Portabilidade concluída**, informar ao usuário que eventuais garantias vinculadas ao contrato original não foram transferidas na portabilidade.

REQ.PC-06800

-   `REQ.PC-06800` No status **Portabilidade concluída**, possibilitar que o usuário baixe o contrato assinado da proposta.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-06800`

**Texto**

No status **Portabilidade concluída**, possibilitar que o usuário baixe o contrato assinado da proposta.

![image-20260826-133727.png](images/image-20260826-133727.png)

wide760#F4F5F7

## **Requisitos - IC**

**Cenário: Consulta aos pedidos**

REQ.PC-06900

-   `REQ.PC-06900` Exibir os pedidos de Portabilidade de Crédito em estrutura que permita localizar um pedido específico e acessar seus detalhes.  
    Ex.: lista
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IC

**Proposta**

**Justificativa**

**ID**

`REQ.PC-06900`

**Texto**

Exibir os pedidos de Portabilidade de Crédito em estrutura que permita localizar um pedido específico e acessar seus detalhes.

REQ.PC-07000

-   `REQ.PC-07000` No item de exibição, indicar um dos seguintes status individuais para cada pedido: **Portabilidade em andamento, Portabilidade cancelada** e **Portabilidade concluída.**
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IC

**Proposta**

**Justificativa**

**ID**

`REQ.PC-07000`

**Texto**

No item de exibição, indicar um dos seguintes status individuais para cada pedido: **Portabilidade em andamento, Portabilidade cancelada** e **Portabilidade concluída.**

REQ.PC-07100

-   `REQ.PC-07100` No item de exibição, indicar o tipo de contrato associado a cada pedido: **Consignado Federal** ou **Crédito Pessoal sem Consignação**.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IC

**Proposta**

**Justificativa**

**ID**

`REQ.PC-07100`

**Texto**

No item de exibição, indicar o tipo de contrato associado a cada pedido: **Consignado Federal** ou **Crédito Pessoal sem Consignação**.

![image-20260824-183500.png](images/image-20260824-183500.png)

**Cenário: Portabilidade em andamento**

REQ.PC-07200

-   `REQ.PC-07200` No item de exibição, mostrar o status **Portabilidade em andamento** após o usuário aceitar a proposta da IP.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IC

**Proposta**

**Justificativa**

**ID**

`REQ.PC-07200`

**Texto**

No item de exibição, mostrar o status **Portabilidade em andamento** após o usuário aceitar a proposta da IP.

REQ.PC-07300

-   `REQ.PC-07300` Manter o item de exibição com a informação do status **Portabilidade em andamento** até que a portabilidade seja concluída ou cancelada.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IC

**Proposta**

**Justificativa**

**ID**

`REQ.PC-07300`

**Texto**

Manter o item de exibição com a informação do status **Portabilidade em andamento** até que a portabilidade seja concluída ou cancelada.

REQ.PC-07400

-   `REQ.PC-07400` Na tela de detalhes do status **Portabilidade em andamento**, quando a proposta for aceita pelo usuário, exibir os seguintes dados do contrato original:
    
    -   Taxa de juros
        
    -   Valor da parcela
        
    -   Número de parcelas
        
    -   Saldo devedor
        
    -   Número do contrato
        

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IC

**Proposta**

**Justificativa**

**ID**

`REQ.PC-07400`

**Texto**

Na tela de detalhes do status **Portabilidade em andamento**, quando a proposta for aceita pelo usuário, exibir os seguintes dados do contrato original:

-   Taxa de juros
    
-   Valor da parcela
    
-   Número de parcelas
    
-   Saldo devedor
    
-   Número do contrato
    

REQ.PC-07500

-   `REQ.PC-07500` Na tela de detalhes do status **Portabilidade em andamento**, quando a contraproposta for recusada ou a contraproposta expirar por prazo, exibir comparativo entre a contraproposta e proposta da IP com os seguintes itens:
    
    -   Saldo devedor
        
    -   Para (indicando a instituição que está oferecendo a contraproposta)
        
    -   De (indicando a instituição que fez a proposta)
        
    -   Diferença mensal (indicando o valor de redução/aumento mensal em relação à proposta)
        
    -   Diferença total (indicando o valor de redução/aumento total em relação à proposta)
        
    -   Novo prazo (indicando a quantidade de parcelas até o fim do novo contrato)
        
    -   Prazo remanescente (indicando a quantidade de parcelas remanescentes até o fim do contrato da proposta)
        
    -   Nova parcela (indicando o valor da parcela do novo contrato)
        
    -   Parcela da proposta (indicando o valor da parcela da proposta)
        
    -   Nova taxa de juros (indicando a taxa de juros do novo contrato)
        
    -   Taxa de juros da proposta (indicando a taxa de juros da proposta)
        
    -   Novo CET (indicando o Custo Efetivo Total do novo contrato)
        
    -   CET da proposta (indicando o Custo Efetivo Total da proposta)
        
    -   Data da primeira parcela do novo contrato
        
    -   Data da última parcela do novo contrato
        

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IC

**Proposta**

**Justificativa**

**ID**

`REQ.PC-07500`

**Texto**

Na tela de detalhes do status **Portabilidade em andamento**, quando a contraproposta for recusada ou a contraproposta expirar por prazo, exibir comparativo entre a contraproposta e proposta da IP com os seguintes itens:

-   Saldo devedor
    
-   Para (indicando a instituição que está oferecendo a contraproposta)
    
-   De (indicando a instituição que fez a proposta)
    
-   Diferença mensal (indicando o valor de redução/aumento mensal em relação à proposta)
    
-   Diferença total (indicando o valor de redução/aumento total em relação à proposta)
    
-   Novo prazo (indicando a quantidade de parcelas até o fim do novo contrato)
    
-   Prazo remanescente (indicando a quantidade de parcelas remanescentes até o fim do contrato da proposta)
    
-   Nova parcela (indicando o valor da parcela do novo contrato)
    
-   Parcela da proposta (indicando o valor da parcela da proposta)
    
-   Nova taxa de juros (indicando a taxa de juros do novo contrato)
    
-   Taxa de juros da proposta (indicando a taxa de juros da proposta)
    
-   Novo CET (indicando o Custo Efetivo Total do novo contrato)
    
-   CET da proposta (indicando o Custo Efetivo Total da proposta)
    
-   Data da primeira parcela do novo contrato
    
-   Data da última parcela do novo contrato
    

REQ.PC-07501

-   `REQ.PC-07501` Na tela de detalhes do status **Portabilidade em andamento**, informar ao usuário que eventuais garantias vinculadas ao contrato original não são transferidas na portabilidade.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação

**Jornada**

Gestão

**Instituição**

IC

**Proposta**

**Justificativa**

**ID**

`REQ.PC-07501`

**Texto**

Na tela de detalhes do status **Portabilidade em andamento**, informar ao usuário que eventuais garantias vinculadas ao contrato original não são transferidas na portabilidade.

REQ.PC-07600

-   `REQ.PC-07600` Permitir desistência da Portabilidade de Crédito antes da liquidação.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IC

**Proposta**

**Justificativa**

**ID**

`REQ.PC-07600`

**Texto**

Permitir desistência da Portabilidade de Crédito antes da liquidação.

REQ.PC-07700

-   `REQ.PC-07700` Informar que o usuário pode desistir da portabilidade antes da fase da liquidação.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IC

**Proposta**

**Justificativa**

**ID**

`REQ.PC-07700`

**Texto**

Informar que o usuário pode desistir da portabilidade antes da fase da liquidação.

REQ.PC-07800

-   `REQ.PC-07800` Caso a portabilidade entre em fase de liquidação, desabilitar a opção de cancelamento do pedido.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IC

**Proposta**

**Justificativa**

**ID**

`REQ.PC-07800`

**Texto**

Caso a portabilidade entre em fase de liquidação, desabilitar a opção de cancelamento do pedido.

![image-20260826-133839.png](images/image-20260826-133839.png)

**Cenário: Portabilidade cancelada**

REQ.PC-07900

-   `REQ.PC-07900` No item de exibição, mostrar o status **Portabilidade cancelada** quando houver cancelamento, qualquer que seja o motivo.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IC

**Proposta**

**Justificativa**

**ID**

`REQ.PC-07900`

**Texto**

No item de exibição, mostrar o status **Portabilidade cancelada** quando houver cancelamento, qualquer que seja o motivo.

REQ.PC-08000

-   `REQ.PC-08000` Manter o item de exibição com o status **Portabilidade cancelada** por 14 dias corridos após o cancelamento.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IC

**Proposta**

**Justificativa**

**ID**

`REQ.PC-08000`

**Texto**

Manter o item de exibição com o status **Portabilidade cancelada** por 14 dias corridos após o cancelamento.

REQ.PC-08100

-   `REQ.PC-08100` Na tela de detalhes do status **Portabilidade cancelada**, exibir um dos motivos do cancelamento:
    
    -   Usuário cancelou a portabilidade
        
    -   Proponente cancelou a portabilidade
        
    -   Contraproposta aceita
        

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IC

**Proposta**

**Justificativa**

**ID**

`REQ.PC-08100`

**Texto**

Na tela de detalhes do status **Portabilidade cancelada**, exibir um dos motivos do cancelamento:

-   Usuário cancelou a portabilidade
    
-   Proponente cancelou a portabilidade
    
-   Contraproposta aceita
    

REQ.PC-08200

-   `REQ.PC-08200` Na tela de detalhes do status **Portabilidade cancelada**, quando o cancelamento aconteceu por decisão do usuário ou por iniciativa da IP, exibir os seguintes dados do contrato original:
    
    -   Taxa de juros
        
    -   Valor da parcela
        
    -   Número de parcelas
        
    -   Saldo devedor
        
    -   Número do contrato
        

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IC

**Proposta**

**Justificativa**

**ID**

`REQ.PC-08200`

**Texto**

Na tela de detalhes do status **Portabilidade cancelada**, quando o cancelamento aconteceu por decisão do usuário ou por iniciativa da IP, exibir os seguintes dados do contrato original:

-   Taxa de juros
    
-   Valor da parcela
    
-   Número de parcelas
    
-   Saldo devedor
    
-   Número do contrato
    

![image-20260824-183640.png](images/image-20260824-183640.png)

REQ.PC-08300

-   `REQ.PC-08300` Na tela de detalhes do status **Portabilidade cancelada**, quando o motivo do cancelamento for o aceite da contraproposta, exibir o comparativo entre a contraproposta aceita e proposta da IP com os seguintes itens:
    
    -   Saldo devedor
        
    -   Para (indicando a instituição que está oferecendo a contraproposta)
        
    -   De (indicando a instituição que fez a proposta)
        
    -   Diferença mensal (indicando o valor de redução/aumento mensal em relação à proposta)
        
    -   Diferença total (indicando o valor de redução/aumento total em relação à proposta)
        
    -   Novo prazo (indicando a quantidade de parcelas até o fim do novo contrato)
        
    -   Prazo remanescente (indicando a quantidade de parcelas remanescentes até o fim do contrato da proposta)
        
    -   Nova parcela (indicando o valor da parcela do novo contrato)
        
    -   Parcela da proposta (indicando o valor da parcela da proposta)
        
    -   Nova taxa de juros (indicando a taxa de juros do novo contrato)
        
    -   Taxa de juros da proposta (indicando a taxa de juros da proposta)
        
    -   Novo CET (indicando o Custo Efetivo Total do novo contrato)
        
    -   CET da proposta (indicando o Custo Efetivo Total da proposta)
        
    -   Data da primeira parcela do novo contrato
        
    -   Data da última parcela do novo contrato
        

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IC

**Proposta**

**Justificativa**

**ID**

`REQ.PC-08300`

**Texto**

Na tela de detalhes do status **Portabilidade cancelada**, quando o motivo do cancelamento for o aceite da contraproposta, exibir o comparativo entre a contraproposta aceita e proposta da IP com os seguintes itens:

-   Saldo devedor
    
-   Para (indicando a instituição que está oferecendo a contraproposta)
    
-   De (indicando a instituição que fez a proposta)
    
-   Diferença mensal (indicando o valor de redução/aumento mensal em relação à proposta)
    
-   Diferença total (indicando o valor de redução/aumento total em relação à proposta)
    
-   Novo prazo (indicando a quantidade de parcelas até o fim do novo contrato)
    
-   Prazo remanescente (indicando a quantidade de parcelas remanescentes até o fim do contrato da proposta)
    
-   Nova parcela (indicando o valor da parcela do novo contrato)
    
-   Parcela da proposta (indicando o valor da parcela da proposta)
    
-   Nova taxa de juros (indicando a taxa de juros do novo contrato)
    
-   Taxa de juros da proposta (indicando a taxa de juros da proposta)
    
-   Novo CET (indicando o Custo Efetivo Total do novo contrato)
    
-   CET da proposta (indicando o Custo Efetivo Total da proposta)
    
-   Data da primeira parcela do novo contrato
    
-   Data da última parcela do novo contrato
    

**Cenário: Portabilidade concluída**

REQ.PC-08400

-   `REQ.PC-08400` No item de exibição, mostrar o status **Portabilidade concluída** após a portabilidade ter sido finalizada com sucesso.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IC

**Proposta**

**Justificativa**

**ID**

`REQ.PC-08400`

**Texto**

No item de exibição, mostrar o status **Portabilidade concluída** após a portabilidade ter sido finalizada com sucesso.

REQ.PC-08500

-   `REQ.PC-08500` Manter o item de exibição com o status **Portabilidade concluída** por 14 dias corridos após a conclusão.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IC

**Proposta**

**Justificativa**

**ID**

`REQ.PC-08500`

**Texto**

Manter o item de exibição com o status **Portabilidade concluída** por 14 dias corridos após a conclusão.

REQ.PC-08600

-   `REQ.PC-08600` Na tela de detalhes do status **Portabilidade concluída**, exibir os seguintes dados do contrato original:
    
    -   Taxa de juros
        
    -   Valor da parcela
        
    -   Número de parcelas
        
    -   Saldo devedor
        
    -   Número do contrato
        

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Gestão

**Instituição**

IC

**Proposta**

**Justificativa**

**ID**

`REQ.PC-08600`

**Texto**

Na tela de detalhes do status **Portabilidade concluída**, exibir os seguintes dados do contrato original:

-   Taxa de juros
    
-   Valor da parcela
    
-   Número de parcelas
    
-   Saldo devedor
    
-   Número do contrato
    

REQ.PC-08601

-   `REQ.PC-08601` Na tela de detalhes do status **Portabilidade concluída**, informar ao usuário que eventuais garantias vinculadas ao contrato original não foram transferidas na portabilidade.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação

**Jornada**

Gestão

**Instituição**

IC

**Proposta**

**Justificativa**

**ID**

`REQ.PC-08600`

**Texto**

Na tela de detalhes do status **Portabilidade concluída**, informar ao usuário que eventuais garantias vinculadas ao contrato original não foram transferidas na portabilidade.

![image-20260826-133936.png](images/image-20260826-133936.png)

Recomendações IP GT#F4F5F7

## Recomendações - IP

**Cenário: Pedido em análise**

-   `REC.PC-01700` Exibir representação gráfica do andamento do pedido, com indicadores visuais simples e sequenciais (ex.: linha de progresso ou etapas conectadas), para indicar de forma clara a etapa atual e as próximas fases.
    

![image-20260622-194056.png](images/image-20260622-194056.png)

**Cenário: Portabilidade em andamento**

-   `REC.PC-01800` Exibir representação gráfica do andamento da portabilidade, com indicadores visuais simples e sequenciais (ex.: linha de progresso ou etapas conectadas), para indicar de forma clara as etapas concluídas, a etapa atual e as próximas fases.
    

![image-20260824-183823.png](images/image-20260824-183823.png)

**Cenário: Portabilidade concluída**

-   `REC.PC-01900` Exibir representação gráfica do andamento da portabilidade, com indicadores visuais simples e sequenciais (ex.: linha de progresso ou etapas conectadas), para indicar de forma clara as etapas concluídas.
    

![image-20260824-183941.png](images/image-20260824-183941.png)

**Cenário: Sem proposta disponível**

-   `REC.PC-02000` Exibir representação gráfica do andamento do pedido, com indicadores visuais simples e sequenciais (ex.: linha de progresso ou etapas conectadas), para indicar de forma clara a etapa concluída e a situação atual de que não há oferta disponível.
    
-   `REC.PC-02100` Na tela de detalhes do status **Sem proposta disponível**, exibir os seguintes dados do contrato original:
    
    -   Taxa de juros
        
    -   Valor da parcela
        
    -   Número de parcelas
        
    -   Saldo devedor
        
    -   Número do contrato
        
-   `REC.PC-02200` Possibilitar que o usuário faça um novo pedido de Portabilidade de Crédito.
    

![image-20260824-184154.png](images/image-20260824-184154.png)

**Cenário: Portabilidade cancelada**

-   `REC.PC-02300` Para pedidos de portabilidade que tenham sido cancelados pelo usuário ou pela Proponente, exibir representação gráfica do andamento do pedido, com indicadores visuais simples e sequenciais (ex.: linha de progresso ou etapas conectadas), para indicar de forma clara as etapas concluídas e a situação atual de que a portabilidade foi cancelada.
    
-   `REC.PC-02400` Para pedidos de portabilidade que tenham sido cancelados pelo usuário ou pela Proponente, possibilitar que o usuário faça um novo pedido de Portabilidade de Crédito.
    

![da18ef22-e8b9-4d12-b7f2-92fcde56f408.png](images/da18ef22-e8b9-4d12-b7f2-92fcde56f408.png)
