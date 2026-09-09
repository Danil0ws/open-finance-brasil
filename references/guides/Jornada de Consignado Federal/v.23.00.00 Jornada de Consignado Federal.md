# v.23.00.00 Jornada de Consignado Federal

Do ponto de vista da experiência do usuário, a principal diferença entre a Jornada de Crédito Pessoal sem Consignação e a Jornada do Consignado Federal está na etapa de **Consulta**. No Consignado Federal, é necessária uma autorização no site `SouGov`, colhida pela Instituição Proponente (IP). Essa autorização deve especificar o contrato a ser portado.

* * *

# Protótipo navegável do Consignado Federal

100%middle600

* * *

# Fluxo de telas do Consignado Federal

![image-20260308-150357.png](images/image-20260308-150357.png)

* * *

# Etapa 1: Descoberta

E1. PC -intrtrue

wide760#F4F5F7

## Requisitos - IP

**Cenário: Acesso à Portabilidade de Crédito**

REQ.PC-00100true

REQ.PC-00200true

REQ.PC - img 100true

* * *

# Etapa 2: Consulta

E2. PC -intrtrue

wide760#F4F5F7

## Requisitos - IP

**Cenário: Seleção do contrato**

REQ.PC-00300true

REQ.PC-00400true

REQ.PC-00500true

REQ.PC-00600true

REQ.PC-00700true

REQ.PC-00800true

![image-20260615-182515.png](images/image-20260615-182515.png)

**Cenário: Autorização no SouGov (usuário sem autorização)**

REQ.PC-00810

-   `REQ.PC-00810` Depois da escolha do contrato, quando somente o usuário puder dar a autorização**,** exibir uma tela direcionando o usuário para o SouGov.
    

truecatálogo de requisitos pc

**Produto**

CF

**Jornada**

Jornada de Consignado Federal

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-00810`

**Texto**

Depois da escolha do contrato, quando somente o usuário puder dar a autorização**,** exibir uma tela direcionando o usuário para o SouGov.

REQ.PC-00820

-   `REQ.PC-00820` Quando somente o usuário puder dar a autorização, na tela de direcionamento, informar ao usuário que, no SouGov, ele deve autorizar a consulta aos dados dos contratos que deseja portar.
    

truecatálogo de requisitos pc

**Produto**

CF

**Jornada**

Jornada de Consignado Federal

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-00820`

**Texto**

Quando somente o usuário puder dar a autorização, na tela de direcionamento, informar ao usuário que, no SouGov, ele deve autorizar a consulta aos dados dos contratos que deseja portar.

REQ.PC-00830

-   `REQ.PC-00830` Quando somente o usuário puder dar a autorização, na tela de direcionamento, orientar o usuário a retornar à IP depois da autorização no SouGov para seguir com a portabilidade.
    

truecatálogo de requisitos pc

**Produto**

CF

**Jornada**

Jornada de Consignado Federal

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-00830`

**Texto**

Quando somente o usuário puder dar a autorização, na tela de direcionamento, orientar o usuário a retornar à IP depois da autorização no SouGov para seguir com a portabilidade.

REQ.PC-00840

-   `REQ.PC-00840` Depois da escolha do contrato, quando a instituição coleta a autorização pelo usuário, exibir uma tela informando sobre a importância da autorização no SouGov.
    

truecatálogo de requisitos pc

**Produto**

CF

**Jornada**

Jornada de Consignado Federal

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-00840`

**Texto**

Depois da escolha do contrato, quando a instituição coleta a autorização pelo usuário, exibir uma tela informando sobre a importância da autorização no SouGov.

REQ.PC-00850

-   `REQ.PC-00850` Quando a instituição coleta a autorização pelo usuário, na tela informativa, exibir opção de continuidade da jornada.
    

truecatálogo de requisitos pc

**Produto**

CF

**Jornada**

Jornada de Consignado Federal

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-00850`

**Texto**

Quando a instituição coleta a autorização pelo usuário, na tela informativa, exibir opção de continuidade da jornada.

![image-20260622-193312.png](images/image-20260622-193312.png)

Recomendações IP E2true

**Cenário: Autorização no SouGov**

REC.PC-02500 a 02600

-   `REC.PC-02500` Exibir opção de continuidade da jornada para o usuário que já realizou a autorização no SouGov, informando que essa autorização permanece válida por 45 dias.
    
-   `REC.PC-02600` Incluir mensagens curtas de contextualização, explicando o “porquê” da etapa de autorização, de modo a reduzir incertezas e aumentar a percepção de segurança.
    

![image-20260622-193540.png](images/image-20260622-193540.png)

* * *

# Etapa 3: Solicitação

E3. PC -intrtrue

wide760#F4F5F7

## Requisitos - IP

**Cenário: Solicitação da Portabilidade de Crédito**

REQ.PC-00900true

REQ.PC-01000true

REQ.PC-01100true

![image-20260615-182747.png](images/image-20260615-182747.png)

REQ.PC-01200trueREQ.PC-01300true

![image-20260615-183016.png](images/image-20260615-183016.png)

Recomendações IP E3true

* * *

# Etapa 4: Oferta

E4. PC -intrtrue

wide760#F4F5F7

## Requisitos - IP

**Cenário: Apresentação da proposta**

REQ.PC-01400trueREQ.PC-01500trueREQ.PC-01600trueREQ.PC-01700trueREQ.PC-01800true

![image-20260714-130528.png](images/image-20260714-130528.png)

**Cenário: Proposta desvantajosa**

REQ.PC-01900trueREQ.PC-02000true

![image-20260714-130634.png](images/image-20260714-130634.png)

**Cenário: Aceite ou recusa da proposta**

REQ.PC-02100trueREQ.PC-02200true

**Cenário: Aceite da proposta**

REQ.PC-02300trueREQ.PC-02400trueREQ.PC-02500true

REQ.PC-02600trueREQ.PC-02700trueREQ.PC-02800trueREQ.PC-02900true

**Cenário: Recusa da proposta**

REQ.PC-03000trueREQ.PC - img 600true

wide760#F4F5F7

## Requisitos - IC

**Cenário: Apresentação da contraproposta**

wide760

**Nota**

A oferta da contraproposta não é requisito, mas caso deseje ofertá-la, a IC deve seguir os requisitos abaixo.

REQ.PC-03100trueREQ.PC-03200true

![image-20260223-203128.png](images/image-20260223-203128.png)

REQ.PC-03300trueREQ.PC-03400trueREQ.PC-03500trueREQ.PC-03600true

![image-20260615-183627.png](images/image-20260615-183627.png)

**Cenário: Aceite ou recusa da contraproposta**

REQ.PC-03700trueRecomendações IP E4true

* * *

# Etapa 5: Efetivação

E5. PC -intrtrue
