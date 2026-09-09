# v.23.00.00 Jornada de Crédito Pessoal sem Consignação

A Jornada de Portabilidade do Crédito Pessoal sem Consignação inicia-se quando o usuário acessa o Open Finance e identifica a disponibilidade da funcionalidade. Em seguida, o usuário consulta os contratos de empréstimos elegíveis e seleciona aqueles que deseja portar.

Após a seleção, o usuário solicita a portabilidade dos contratos escolhidos. Na sequência, recebe uma proposta da Instituição Proponente e, caso a aceite, pode também receber uma contraproposta da Instituição Credora.

Por fim, o usuário é notificado da conclusão da Portabilidade de Crédito, momento em que a operação é efetivada e liquidada.

![Jornada de Portabilidade do Crédito Pessoal sem Consignação](images/Jornada%20de%20Portabilidade%20de%20Cre%CC%81dito-20251020-150705.png)

* * *

# Protótipo navegável

wide760

**Nota**

Nas interfaces ilustrativas, a Instituição Proponente está sendo representada pela marca **Wiscredi** na cor azul escuro e a Instituição Credora é a marca **Bratech** na cor amarelo escuro.

100%middle600

# **Fluxo de telas (Jornada de Crédito Pessoal sem consignação)**

* * *

# Etapa 1: Descoberta

E1. PC -intr

Nesta etapa inicial da jornada, o usuário acessa o canal digital da Instituição Proponente (IP) e encontra a opção de iniciar a Portabilidade de Crédito.

A Instituição Proponente (IP) deve garantir que esse acesso ocorra de forma adequada, segura e em conformidade com os critérios regulatórios definidos para o Open Finance.

wide760#F4F5F7

## Requisitos - IP

**Cenário: Acesso à Portabilidade de Crédito**

REQ.PC-00100

-   `REQ.PC-00100` Disponibilizar o produto apenas para Pessoa Física.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Crédito Pessoal sem Consignação, Jornada de Consignado Federal

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-00100`

**Texto**

Disponibilizar o produto apenas para Pessoa Física.

REQ.PC-00200

-   `REQ.PC-00200` Se não houver consentimento, ou se ele expirar em até 15 dias úteis a partir da data de solicitação, direcionar o usuário para a Jornada de Compartilhamento de Dados quando ele selecionar a opção Portabilidade de Crédito via Open Finance.  
      
    Ex.: Renove seu consentimento de compartilhamento de dados antes de seguir com a solicitação de portabilidade.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Jornada de Crédito Pessoal sem Consignação, Jornada de Consignado Federal

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-00200`

**Texto**

Se não houver consentimento, ou se ele expirar em até 15 dias úteis a partir da data de solicitação, direcionar o usuário para a Jornada de Compartilhamento de Dados quando ele selecionar a opção Portabilidade de Crédito via Open Finance.

![image-20260615-182342.png](images/image-20260615-182342.png)Recomendações IP E1#F4F5F7

## Recomendações - IP

**Cenário: Acesso à Portabilidade de Crédito**

-   `REC.PC-00010` Implementar a opção de Portabilidade de Crédito na seção de Crédito/Empréstimos do canal digital.  
    
-   `REC.PC-00020` Pelo menos na primeira utilização do produto, exibir uma tela introdutória com breve explicação sobre Portabilidade de Crédito.  
    
-   `REC.PC-00021` Permitir que o usuário avance após confirmar que compreendeu as informações.  
    
-   `REC.PC-00022` Incluir a chamada para o fluxo de consentimento, se necessário.  
    
-   `REC.PC-00023` Disponibilizar canais adicionais para esclarecimento de dúvidas.  
    
-   `REC.PC-00024` Exibir mensagem informando os produtos disponíveis para Portabilidade de Crédito via Open Finance.  
    
-   `REC.PC-00025` Exibir mensagem sempre que um novo produto estiver disponível para Portabilidade de Crédito via Open Finance.  
    
-   `REC.PC-00026` Garantir coerência entre rótulos, ícones e mensagens apresentadas, adotando nomenclatura simples e alinhada ao modelo mental do usuário, de modo a facilitar a identificação de onde acessar a Portabilidade de Crédito e evitar ambiguidades. 
    

![image-20260824-184855.png](images/image-20260824-184855.png)

**Cenário: Jornada de Consentimento**

-   `REC.PC-00030` Permitir ao usuário baixar o comprovante de compartilhamento de dados, reforçando a percepção de segurança e confiança ao garantir a guarda do registro das informações compartilhadas.
    

![image-20260824-184959.png](images/image-20260824-184959.png)

* * *

# Etapa 2: Consulta

E2. PC -intr

Nesta etapa, o usuário consulta os contratos de crédito elegíveis para portabilidade pertencentes às Instituições Credoras (IC) para as quais ele já consentiu o compartilhamento de dados de Operações de Crédito.  

A Instituição Proponente (IP), por sua vez, deve garantir a exibição desses contratos de forma clara, estruturada e completa, possibilitando que o usuário visualize os detalhes e selecione aqueles que deseja portar.

wide760#F4F5F7

## Requisitos - IP

**Cenário: Seleção do contrato**

REQ.PC-00300

-   `REQ.PC-00300` Exibir todos os contratos ativos de crédito para os quais o usuário tenha consentido seus dados de Operação de Crédito.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Jornada de Crédito Pessoal sem Consignação, Jornada de Consignado Federal

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-00300`

**Texto**

Exibir todos os contratos ativos de crédito para os quais o usuário tenha consentido seus dados de Operação de Crédito.

REQ.PC-00400

-   `REQ.PC-00400` No campo de cada contrato ativo de crédito, exibir:
    
    -   Nome da Credora
        
    -   Taxa
        
    -   Valor da parcela
        
    -   Número de parcelas  
        
    -   Saldo devedor
        
    -   Número do contrato
        

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Jornada de Crédito Pessoal sem Consignação, Jornada de Consignado Federal

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-00400`

**Texto**

No campo de cada contrato ativo de crédito, exibir: Nome da Credora, Taxa, Valor da parcela, Número de parcelas, Saldo devedor e Número do contrato.

REQ.PC-00500

-   `REQ.PC-00500` Exibir contratos com pedido de portabilidade em andamento desabilitados para seleção, sejam feitos via Open Finance ou via registradora.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Jornada de Crédito Pessoal sem Consignação, Jornada de Consignado Federal

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-00500`

**Texto**

Exibir contratos com pedido de portabilidade em andamento desabilitados para seleção, sejam feitos via Open Finance ou via registradora.

REQ.PC-00600-   `REQ.PC-00600` Indicar visualmente que há uma portabilidade em andamento para o contrato exibido.  truecatálogo de requisitos pc**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Jornada de Crédito Pessoal sem Consignação, Jornada de Consignado Federal

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-00600`

**Texto**

Indicar visualmente que há uma portabilidade em andamento para o contrato exibido.  REQ.PC-00700

-   `REQ.PC-00700` Indicar visualmente o tipo de contrato na lista.  
      
    Ex. Consignado Federal ou Crédito Pessoal sem Consignação.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Jornada de Crédito Pessoal sem Consignação, Jornada de Consignado Federal

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-00700`

**Texto**

Indicar visualmente o tipo de contrato na lista.

REQ.PC-00800-   `REQ.PC-00800` Permitir que o usuário selecione o contrato desejado.  truecatálogo de requisitos pc**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Jornada de Crédito Pessoal sem Consignação, Jornada de Consignado Federal

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-00800`

**Texto**

Permitir que o usuário selecione o contrato desejado.  ![image-20260824-165400.png](images/image-20260824-165400.png)Recomendações IP E2#F4F5F7

## Recomendações - IP

**Cenário: Seleção do contrato**

-   `REC.PC-00100` Exibir todas as Instituições Credoras para os quais o usuário tenha consentido seus dados de Operação de Crédito.  
    
-   `REC.PC-00200` Permitir que o usuário busque pela Credora desejada. 
    
-   `REC.PC-00300` Permitir que o usuário selecione a Credora cujos contratos ativos de crédito deseja visualizar.
    

![image-20260824-185228.png](images/image-20260824-185228.png)

-   `REC.PC-00350` Permitir seleção múltipla de contratos, desde que cada um receba proposta individual clara.
    

![image-20260824-185258.png](images/image-20260824-185258.png)

* * *

# Etapa 3: Solicitação

E3. PC -intrNesta etapa, o usuário seleciona o contrato elegível que deseja portar e envia o pedido de Portabilidade de Crédito.

A Instituição Proponente (IP) deve possibilitar esse envio e informar o usuário sobre o andamento da análise e a eventual disponibilização de uma proposta.  
Além disso, caso deseje, a Proponente pode acionar proativamente o usuário com uma oferta de portabilidade, iniciando a jornada a partir do momento que considerar mais adequado. wide760#F4F5F7

## Requisitos - IP

**Cenário: Solicitação da Portabilidade de Crédito**

REQ.PC-00900

-   `REQ.PC-00900` Permitir o envio do pedido de Portabilidade de Crédito.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Jornada de Crédito Pessoal sem Consignação, Jornada de Consignado Federal

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-00900`

**Texto**

Permitir o envio do pedido de Portabilidade de Crédito.

REQ.PC-01000

-   `REQ.PC-01000` Em caso de jornada assíncrona, exibir uma tela confirmando o envio do pedido.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Jornada de Crédito Pessoal sem Consignação, Jornada de Consignado Federal

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-01000`

**Texto**

Em caso de jornada assíncrona, exibir uma tela confirmando o envio do pedido.

REQ.PC-01100

-   `REQ.PC-01100` Em caso de jornada assíncrona, informar o prazo estimado para conclusão da análise e disponibilização da proposta.  
      
    Ex.: Em até XX horas, vamos analisar se há uma oferta compatível com o seu perfil.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Jornada de Crédito Pessoal sem Consignação, Jornada de Consignado Federal

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-01100`

**Texto**

Em caso de jornada assíncrona, informar o prazo estimado para conclusão da análise e disponibilização da proposta.

![image-20260824-180231.png](images/image-20260824-180231.png)

REQ.PC-01200

-   `REQ.PC-01200` Caso a proponente acione o usuário para oferecer a Portabilidade de Crédito, informá-lo sobre a oferta. Ex.: _push_, SMS, email etc.  
      
    Ex.: Traga seu empréstimo 885320 para cá.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Jornada de Crédito Pessoal sem Consignação, Jornada de Consignado Federal

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-01200`

**Texto**

Caso a proponente acione o usuário para oferecer a Portabilidade de Crédito, informá-lo sobre a oferta. Ex.: _push_, SMS, email etc.

REQ.PC-01201

-   `REQ.PC-01201` Informar ao usuário, durante a etapa de solicitação, que eventuais garantias vinculadas ao contrato original não são transferidas na portabilidade.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Jornada de Crédito Pessoal sem Consignação, Jornada de Consignado Federal

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-01201`

**Texto**

Informar ao usuário, durante a etapa de solicitação, que eventuais garantias vinculadas ao contrato original não são transferidas na portabilidade.

REQ.PC-01300

-   `REQ.PC-01300` Na comunicação sobre a oferta, encaminhar o usuário diretamente para a etapa correspondente na jornada.  
      
    Ex.: seleção do contrato, exibição da proposta, análise do pedido etc., conforme o modelo adotado (síncrono ou assíncrono).
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Jornada de Crédito Pessoal sem Consignação, Jornada de Consignado Federal

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-01300`

**Texto**

Na comunicação sobre a oferta, encaminhar o usuário diretamente para a etapa correspondente na jornada.

![image-20260826-133246.png](images/image-20260826-133246.png)Recomendações IP E3#F4F5F7

## Recomendações -IP

**Cenário: Solicitação da Portabilidade de Crédito**

-   `REC.PC-00400` Em caso de jornada assíncrona, ao sair do fluxo, direcionar o usuário para a Área de Gestão de Pedidos para que ele possa visualizar o status do pedido (Ex.: Pedido em análise).
    

![image-20260824-185400.png](images/image-20260824-185400.png)

* * *

# Etapa 4: Oferta

E4. PC -intr

Nesta etapa, o usuário é informado sobre a disponibilidade ou ausência de uma proposta (pela Proponente) ou de uma contraproposta (pela Credora), e pode acessá-la para análise.

A Instituição Proponente e/ou a Instituição Credora deve garantir que essa comunicação ocorra de forma clara, apresentando todos os detalhes relevantes da proposta ou contraproposta, para que o usuário possa tomar uma decisão consciente.

wide760#F4F5F7

## Requisitos - IP

**Cenário: Apresentação da proposta**

REQ.PC-01400

-   `REQ.PC-01400` Exibir de forma comparativa os novos valores da proposta feita pela Proponente versus os valores da Credora.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Jornada de Crédito Pessoal sem Consignação, Jornada de Consignado Federal

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-01400`

**Texto**

Exibir de forma comparativa os novos valores da proposta feita pela Proponente versus os valores da Credora.

REQ.PC-01500

-   `REQ.PC-01500` O comparativo dos novos valores da proposta feita pela Proponente versus os valores da Credora deve conter:
    
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

Jornada de Crédito Pessoal sem Consignação, Jornada de Consignado Federal

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-01500`

**Texto**

O comparativo dos novos valores da proposta feita pela Proponente versus os valores da Credora deve conter:

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
    

REQ.PC-01600-   `REQ.PC-01600` Exibir, com destaque, a diferença de valor mensal e valor total que o novo contrato oferece em relação ao contrato de origem, seja para mais, para menos ou com nenhuma diferença. truecatálogo de requisitos pc**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Jornada de Crédito Pessoal sem Consignação, Jornada de Consignado Federal

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-01600`

**Texto**

Exibir, com destaque, a diferença de valor mensal e valor total que o novo contrato oferece em relação ao contrato de origem, seja para mais, para menos ou com nenhuma diferença. REQ.PC-01700-   `REQ.PC-01700` Sinalizar na exibição da proposta, conforme estratégia da instituição, que o valor da parcela pode sofrer alterações.  truecatálogo de requisitos pc**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Jornada de Crédito Pessoal sem Consignação, Jornada de Consignado Federal

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-01700`

**Texto**

Sinalizar na exibição da proposta, conforme estratégia da instituição, que o valor da parcela pode sofrer alterações.  REQ.PC-01800-   `REQ.PC-01800` Exibir prazo para que o usuário aceite ou recuse a proposta até seu cancelamento automático de acordo com a legislação e regulação vigentes.
    
    -   Ex.: Você tem 2 dias para aceitar a proposta ou ela será cancelada automaticamente. ![image-20260824-180540.png](images/image-20260824-180540.png)

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Jornada de Crédito Pessoal sem Consignação, Jornada de Consignado Federal

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-01800`

**Texto**

Exibir prazo para que o usuário aceite ou recuse a proposta até seu cancelamento automático de acordo com a legislação e regulação vigentes.

**Cenário: Proposta desvantajosa**

REQ.PC-01900

-   `REQ.PC-01900` Informar com clareza ao usuário caso a proposta resulte em aumento dos custos do empréstimo em comparação ao contrato original.
    
    -   Ex.: Valor adicional mensal e Valor adicional total.
        

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Jornada de Crédito Pessoal sem Consignação, Jornada de Consignado Federal

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-01900`

**Texto**

Informar com clareza ao usuário caso a proposta resulte em aumento dos custos do empréstimo em comparação ao contrato original.

REQ.PC-02000

-   `REQ.PC-02000` Exibir uma confirmação adicional perguntando explicitamente ao usuário se ele deseja prosseguir com o aceite, antes da formalização.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Jornada de Crédito Pessoal sem Consignação, Jornada de Consignado Federal

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-02000`

**Texto**

Exibir uma confirmação adicional perguntando explicitamente ao usuário se ele deseja prosseguir com o aceite, antes da formalização.

![image-20260824-180633.png](images/image-20260824-180633.png)

**Cenário: Aceite ou recusa da proposta**

REQ.PC-02100

-   `REQ.PC-02100` Possibilitar que o usuário aceite ou recuse a proposta de Portabilidade de Crédito.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Jornada de Crédito Pessoal sem Consignação, Jornada de Consignado Federal

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-02100`

**Texto**

Possibilitar que o usuário aceite ou recuse a proposta de Portabilidade de Crédito.

REQ.PC-02200-   `REQ.PC-02200` Desobrigar o usuário de aceitar ou recusar a proposta no momento da exibição.  
      
    Ex.: Botão **Voltar**. truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Jornada de Crédito Pessoal sem Consignação, Jornada de Consignado Federal

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-02200`

**Texto**

Desobrigar o usuário de aceitar ou recusar a proposta no momento da exibição.

**Cenário: Aceite da proposta**

REQ.PC-02300

-   `REQ.PC-02300` Direcionar o usuário para a tela de assinatura do contrato.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Jornada de Crédito Pessoal sem Consignação, Jornada de Consignado Federal

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-02300`

**Texto**

Direcionar o usuário para a tela de assinatura do contrato.

REQ.PC-02400

-   `REQ.PC-02400` Disponibilizar em tela, conforme estratégia da instituição, as condições operacionais do contrato conforme descrito no cenário de Apresentação da proposta.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Jornada de Crédito Pessoal sem Consignação, Jornada de Consignado Federal

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-02400`

**Texto**

Disponibilizar em tela, conforme estratégia da instituição, as condições operacionais do contrato conforme descrito no cenário de Apresentação da proposta.

REQ.PC-02500-   `REQ.PC-02500` Possibilitar que o usuário baixe o contrato completo.  truecatálogo de requisitos pc**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Jornada de Crédito Pessoal sem Consignação, Jornada de Consignado Federal

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-02500`

**Texto**

Possibilitar que o usuário baixe o contrato completo.  

REQ.PC-02600

-   `REQ.PC-02600` Possibilitar que o usuário assine o contrato exclusivamente por meio digital com autenticação, exceto nos casos ou estados que exijam obrigatoriamente a assinatura física.  
      
    Ex.: senha, token por SMS, token por email etc. truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Jornada de Crédito Pessoal sem Consignação, Jornada de Consignado Federal

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-02600`

**Texto**

Possibilitar que o usuário assine o contrato exclusivamente por meio digital com autenticação, exceto nos casos ou estados que exijam obrigatoriamente a assinatura física.

REQ.PC-02700

-   `REQ.PC-02700` Exibir mensagem em tela informando que o pedido de Portabilidade de Crédito foi realizado e que a efetivação poderá levar até 5 dias úteis.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Jornada de Crédito Pessoal sem Consignação, Jornada de Consignado Federal

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-02700`

**Texto**

Exibir mensagem em tela informando que o pedido de Portabilidade de Crédito foi realizado e que a efetivação poderá levar até 5 dias úteis.

REQ.PC-02800-   `REQ.PC-02800` Disponibilizar imediatamente o contrato assinado, inclusive para download.  truecatálogo de requisitos pc**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Jornada de Crédito Pessoal sem Consignação, Jornada de Consignado Federal

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-02800`

**Texto**

Disponibilizar imediatamente o contrato assinado, inclusive para download.  REQ.PC-02900

-   `REQ.PC-02900` Informar, quando aplicável, o prazo para desistência da Portabilidade de Crédito antes da liquidação.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Jornada de Crédito Pessoal sem Consignação, Jornada de Consignado Federal

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-02900`

**Texto**

Informar, quando aplicável, o prazo para desistência da Portabilidade de Crédito antes da liquidação.

**Cenário: Recusa da proposta**

REQ.PC-03000

-   `REQ.PC-03000` Exibir mensagem em tela confirmando que a Portabilidade de Crédito foi cancelada porque a proposta foi recusada.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Jornada de Crédito Pessoal sem Consignação, Jornada de Consignado Federal

**Instituição**

IP

**Proposta**

**Justificativa**

**ID**

`REQ.PC-03000`

**Texto**

Exibir mensagem em tela confirmando que a Portabilidade de Crédito foi cancelada porque a proposta foi recusada.

REQ.PC - img 600

**Nota**

A assinatura do contrato não conclui a Portabilidade de Crédito. A efetivação da portabilidade acontecerá apenas após a liquidação do contrato pela Proponente junto à Instituição Credora e sua confirmação de recebimento no final da jornada.

![image-20260824-180713.png](images/image-20260824-180713.png)

wide760#F4F5F7

## Requisitos - IC

**Cenário: Apresentação da contraproposta**

wide760

**Nota**

A oferta da contraproposta não é requisito, mas caso deseje ofertá-la, a IC deve seguir os requisitos abaixo.

REQ.PC-03100

-   `REQ.PC-03100` Disponibilizar a oferta da contraproposta em seu canal digital.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Jornada de Crédito Pessoal sem Consignação, Jornada de Consignado Federal

**Instituição**

IC

**Proposta**

**Justificativa**

**ID**

`REQ.PC-03100`

**Texto**

Disponibilizar a oferta da contraproposta em seu canal digital.

REQ.PC-03200

-   `REQ.PC-03200` Garantir que o aceite ou recusa da contraproposta ocorra exclusivamente através de seu canal digital, exceto nos casos ou estados que exijam assinatura física.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Jornada de Crédito Pessoal sem Consignação, Jornada de Consignado Federal

**Instituição**

IC

**Proposta**

**Justificativa**

**ID**

`REQ.PC-03200`

**Texto**

Garantir que o aceite ou recusa da contraproposta ocorra exclusivamente através de seu canal digital, exceto nos casos ou estados que exijam assinatura física.

![image-20260824-180759.png](images/image-20260824-180759.png)

REQ.PC-03300

-   `REQ.PC-03300` Informar com clareza o prazo para aceite ou recusa da contraproposta, respeitando o limite das 9h do 3º dia útil após a disponibilização da contraproposta.  
    

truecatálogo de requisitos pc**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Jornada de Crédito Pessoal sem Consignação, Jornada de Consignado Federal

**Instituição**

IC

**Proposta**

**Justificativa**

**ID**

`REQ.PC-03300`

**Texto**

Informar com clareza o prazo para aceite ou recusa da contraproposta, respeitando o limite das 9h do 3º dia útil após a disponibilização da contraproposta.  REQ.PC-03400

-   `REQ.PC-03400` Desobrigar o usuário de aceitar ou recusar a contraproposta.  
      
    Ex.: Botão **Voltar**.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Jornada de Crédito Pessoal sem Consignação, Jornada de Consignado Federal

**Instituição**

IC

**Proposta**

**Justificativa**

**ID**

`REQ.PC-03400`

**Texto**

Desobrigar o usuário de aceitar ou recusar a contraproposta.

REQ.PC-03500-   `REQ.PC-03500` Informar que a ausência de resposta do usuário implica no sequenciamento da operação com a Proponente.  truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Jornada de Crédito Pessoal sem Consignação, Jornada de Consignado Federal

**Instituição**

IC

**Proposta**

**Justificativa**

**ID**

`REQ.PC-03500`

**Texto**

Informar que a ausência de resposta do usuário implica no sequenciamento da operação com a Proponente.

REQ.PC-03600

-   `REQ.PC-03600` Seguir os requisitos complementares descritos no cenário de Apresentação da Proposta.
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Jornada de Crédito Pessoal sem Consignação, Jornada de Consignado Federal

**Instituição**

IC

**Proposta**

**Justificativa**

**ID**

`REQ.PC-03600`

**Texto**

Seguir os requisitos complementares descritos no cenário de Apresentação da Proposta.

![image-20260824-180851.png](images/image-20260824-180851.png)

**Cenário: Aceite ou recusa da contraproposta**

REQ.PC-03700

-   `REQ.PC-03700` Nos casos em que a credora oferece a contraproposta, seguir os requisitos descritos no cenário de Aceite ou Recusa da Proposta.  
    
    ![image-20260824-180927.png](images/image-20260824-180927.png)
    

truecatálogo de requisitos pc

**Produto**

Crédito Pessoal sem Consignação, CF

**Jornada**

Jornada de Crédito Pessoal sem Consignação, Jornada de Consignado Federal

**Instituição**

IC

**Proposta**

**Justificativa**

**ID**

`REQ.PC-03700`

**Texto**

Nos casos em que a credora oferece a contraproposta, seguir os requisitos descritos no cenário de Aceite ou Recusa da Proposta.

Recomendações IP E4#F4F5F7

## Recomendações - IP

**Cenário: Apresentação da proposta**

-   `REC.PC-00500` Disponibilizar ajuda contextual na tela de detalhes da proposta, acionada por ícone de ajuda, para explicar, por exemplo, o significado de termos financeiros, como o CET (Custo Efetivo Total), ou para ressaltar que na portabilidade de crédito não há liberação de troco.
    
-   `REC.PC-00600` Além da visibilidade prevista na fase de solicitação, apresentar os prazos e as próximas etapas até a conclusão da jornada.
    

![image-20260824-185543.png](images/image-20260824-185543.png)

**Cenário: Aceite/recusa da proposta**

-   `REC.PC-00700` Habilitar a assinatura do contrato somente quando o usuário tiver feito a rolagem de todo o contrato.
    
-   `REC.PC-00800` Na tela de assinatura do contrato, informar ao usuário que a assinatura não conclui a Portabilidade de Crédito, que só será finalizada após confirmação da Proponente.
    
-   `REC.PC-00900` Possibilitar que o usuário faça um novo pedido de Portabilidade de Crédito após assinatura do contrato.
    

![image-20260824-185636.png](images/image-20260824-185636.png)

**Cenário: Abandono e retomada de jornada**

-   `REC.PC-01000` Se a proposta ainda estiver disponível, exibir, por exemplo, um modal para reengajar o usuário na jornada de Portabilidade de Crédito, em momento definido conforme estratégia da instituição.  
      
    Ex.: Ao acessar o aplicativo, a área de Crédito/Empréstimos ou a seção do Open Finance.
    
-   `REC.PC-01100` Se a proposta ainda estiver disponível, levar o usuário para a tela de exibição da proposta.
    
-   `REC.PC-01200` Se a proposta ainda estiver disponível, efetivar o pedido de Portabilidade de Crédito apenas após assinatura do contrato.
    

![image-20260824-185712.png](images/image-20260824-185712.png)

-   `REC.PC-01250` Se a proposta não estiver mais disponível, informar o usuário que a proposta não está mais disponível.
    
-   `REC.PC-01300` Se a proposta não estiver mais disponível, possibilitar que o usuário faça um novo pedido de Portabilidade de Crédito para o mesmo contrato.
    
-   `REC.PC-01400` Se a proposta não estiver mais disponível, possibilitar que o usuário faça um novo pedido de Portabilidade de Crédito.
    

![image-20260824-185741.png](images/image-20260824-185741.png)

* * *

* * *

# Etapa 5: Efetivação

E5. PC -intrApós o aceite da proposta ou o sequenciamento do pedido pela Instituição Proponente (IP), a Portabilidade de Crédito entra na etapa de efetivação. Nesse momento, a Proponente é responsável por liquidar o contrato junto à Credora. A Portabilidade de Crédito é efetivada quando a Credora confirma a liquidação do contrato.  

### Efetivação da Portabilidade

Esta etapa ocorre no _backend_ da jornada, sem ações diretas do usuário. Por esse motivo, os requisitos e recomendações relacionados à experiência do usuário estão organizados em outras seções do guia, conforme descrito a seguir:  

-   **Notificações**: reúne os requisitos referentes à informação ativa ao usuário sobre a efetivação da portabilidade, incluindo orientações para acesso ao status atualizado do pedido.
    
-   **Gestão de Portabilidade de Crédito**: concentra os requisitos sobre a atualização do status do pedido para “Portabilidade concluída” e a exibição dos dados da operação concluída.  
    

![image-20251125-130522.png](images/image-20251125-130522.png)
