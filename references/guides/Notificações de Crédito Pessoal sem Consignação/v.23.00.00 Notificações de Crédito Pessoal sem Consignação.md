# v.23.00.00 Notificações de Crédito Pessoal sem Consignação

NT.PC - intr

Esta seção reúne requisitos e recomendações relacionados à comunicação e ao envio de notificações ao usuário durante a jornada de Portabilidade de Crédito.

Cada instituição é responsável por notificar o usuário sobre as mudanças de status que ocorrerem em seu respectivo ambiente.

As notificações ativas garantem que o usuário seja informado sobre mudanças relevantes do seu pedido. Esses mesmos eventos devem estar refletidos na Área de Gestão por meio de status e descrições acessíveis ao usuário. 

Mudanças de estado que não exigem notificação ativa ainda podem ser apresentadas como status na Área de Gestão, de forma clara e contextualizada.

* * *

wide760#F4F5F7

## **Requisitos - IP**

**Cenário: Geral**

REQ.PC-03800

-   `REQ.PC-03800` Notificar ativamente o usuário (ex. _push_, e-mail, SMS) sobre, no mínimo, as seguintes mudanças de status dos pedidos de Portabilidade de Crédito: **Proposta disponível**, **Proposta indisponível** (jornada assíncrona), **Cancelamento** e **Efetivação de Portabilidade**.  
      
    Ex.:
    
    -   **Proposta disponível**: Temos uma proposta disponível para o seu pedido de portabilidade de crédito. Confira agora mesmo!
        
    -   **Proposta indisponível**: Não encontramos uma proposta de portabilidade de crédito adequada ao seu perfil agora.
        
    -   **Cancelamento**: Sua solicitação de portabilidade de crédito para o empréstimo 885320 foi cancelada. Visualize os detalhes na Área de Gestão.
        
    -   **Efetivação de Portabilidade**: Tudo certo! A portabilidade do seu empréstimo 885320 foi concluída. Acesse a Área de Gestão para mais informações.
        

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Notificações

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-03800`

**Texto**

Notificar ativamente o usuário (ex. _push_, e-mail, SMS) sobre, no mínimo, as seguintes mudanças de status dos pedidos de Portabilidade de Crédito: Proposta disponível, Proposta indisponível (jornada assíncrona), Cancelamento e Efetivação de Portabilidade.

![image-20251127-174951.png](images/image-20251127-174951.png)wide760#F4F5F7

## **Requisitos - IC**

**Cenário: Geral**

REQ.PC-03900

-   `REQ.PC-03900`Nos casos em que há contraproposta, notificar ativamente o usuário (ex. _push_, e-mail, SMS) sobre a disponibilidade de contraproposta para os pedidos de Portabilidade de Crédito.  
      
    Ex.: Temos uma contraproposta para você. Recebemos o seu pedido de portabilidade de crédito para o empréstimo 885320 e temos uma contraproposta para você. Confira!
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Notificações

**Instituição**

IC

**Proposta**

**Justificativa**

**ID**

`REQ.PC-03900`

**Texto**

Nos casos em que há contraproposta, notificar ativamente o usuário (ex. _push_, e-mail, SMS) sobre a disponibilidade de contraproposta para os pedidos de Portabilidade de Crédito.

![image-20251127-175051.png](images/image-20251127-175051.png)Recomendações IP NT#F4F5F7

## Recomendações - IP

**Cenário: Geral**

-   `REC.PC-01500` Para aprimorar a experiência, em caso de jornadas assíncronas, notificar ativamente o usuário (ex. _push_, e-mail, SMS) sobre as demais mudanças de status dos pedidos de Portabilidade de Crédito.
    
    -   **Proposta prestes a expirar**  
        Ex.: Aceite sua proposta de portabilidade do empréstimo 885320 até amanhã às 23h59. Após esse prazo, ela será cancelada.  
        
    -   **Portabilidade em andamento**  
        Ex.:  A portabilidade do seu empréstimo 885320 está em fase final e será concluída em até 2 dias. Te avisaremos quando estiver tudo certo!
        

![image-20251127-175153.png](images/image-20251127-175153.png)Recomendações IC NT#F4F5F7

## Recomendações - IC

**Cenário: Geral**

-   `REC.PC-01600` Para aprimorar a experiência, quando aplicável, notificar ativamente o usuário (ex. _push_, e-mail, SMS) quando a contraproposta estiver próxima de expirar.  
      
    Ex.: Contraproposta prestes a expirar. Você tem até amanhã às 9h para aceitar a nossa contraproposta para o empréstimo 885320. Após esse prazo, ela será cancelada e a portabilidade será sequenciada com a Wiscredi.
    

![image-20251127-175256.png](images/image-20251127-175256.png)
