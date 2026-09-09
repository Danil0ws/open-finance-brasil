# v.23.00.00 Changelog

# Resumo da versão

-   **Propostas deliberadas:** PJR-161, PUX-287, PUX-288, PUX-289, PUX-290 e PUX-291.
    
-   **Produtos atualizados:** Compartilhamento de Dados PF (atualizações de CIBA e da IN-760), Compartilhamento de Dados PJ (atualizações da IN-760), Pix Agendado, Pix Automático, Transferências Inteligentes e Crédito Pessoal sem Consignação (CPC).
    
-   **Jornadas atualizadas ou criadas:** Compartilhamento de Dados PF (hybrid flow, hybrid flow com hand-off, CIBA, Fallback, Gestão), Compartilhamento de Dados PJ (hybrid flow, hybrid flow com hand-off, Múltiplos Aprovadores), Pix Agendado (hybrid flow, JSR), Pix Automático (hybrid flow, JSR), Transferências Inteligentes (hybrid flow) e Crédito Pessoal sem Consignação (Jornada e Gestão).
    
-   **Novas jornadas:** 2
    
-   **Requisitos adicionados:** 69
    
-   **Requisitos atualizados:** 67
    
-   **Recomendações adicionadas:** 33
    
-   **Recomendações atualizadas:** 21
    
-   **Recomendações removidas:** 4
    
-   **Outras atualizações**:
    
    -   Alteração do nome do produto CPC para “Crédito Pessoal sem Consignação”.
        
    -   A Jornada de Compartilhamento de Dados com múltiplos aprovadores passou a ficar restrita ao PJ.
        
    -   Restabelecimento do requisito `REQ.PG-05701` nas jornadas via hybrid flow de Pix, Pix com vencimento via QR Code dinâmico, Pix Agendado, Pix Automático, Pix Saque e Pix Troco e Transferências Inteligentes. O requisito, aprovado anteriormente na PUX-214, deixou de constar no Guia a partir da v22.00.02 devido a uma falha editorial.
        

# Resumo das propostas

-   **PJR-161 (IN-760)**
    
    -   Atualização de requisitos e de recomendações para a ITP na Etapa 3 da Jornada de Pix Agendado via JSR.
        
    -   Atualização de requisitos e de recomendações para a ITP na Etapa 3 da Jornada de Pix Automático via JSR.
        

-   **PUX-287 (Nova Jornada de CIBA)**
    
    -   Atualização nas recomendações para a IR na Etapa 1 da jornada de Compartilhamento de Dados PF via hybrid flow e Compartilhamento de Dados PF via hybrid flow com hand-off.
        
    -   Atualização de requisitos e de recomendações para a IR na jornada de Compartilhamento de Dados PF via CIBA.
        
    -   Atualização de requisitos e de recomendações para a IT na jornada de Compartilhamento de Dados PF via CIBA.
        
    -   Atualização de requisitos e de recomendações para a IR na Gestão de Compartilhamento de Dados PF.
        
    -   Atualização de requisitos e de recomendações para a IT na Gestão de Compartilhamento de Dados PF.
        
-   **PUX-288 (Nova Jornada de Fallback)**
    
    -   Atualização de requisitos e de recomendações para a IR na jornada de Compartilhamento de Dados PF com fallback.
        
    -   Atualização de requisitos e de recomendações para a IT na jornada de Compartilhamento de Dados PF com fallback.
        
-   **PUX-289 (IN-760)**
    
    -   Atualização de requisitos e de recomendações para a ITP na Etapa 5 da Jornada de Pix Agendado via hybrid flow.
        
    -   Atualização de requisitos e de recomendações para a ITP na Etapa 5 da Jornada de Pix Automático via hybrid flow.
        
    -   Atualização de requisitos e de recomendações para a ITP na Etapa 5 da Jornada de Transferências Inteligentes via hybrid flow.
        
-   **PUX-290 (IN-760)**
    
    -   Atualização de requisitos para a IR na Etapa 6 da Jornada de Compartilhamento de Dados PF via hybrid flow e jornadas derivadas (Jornada de Compartilhamento de Dados PF via hybrid flow com hand-off, Jornada de Compartilhamento de Dados PJ via hybrid flow, Jornada de Compartilhamento de Dados PJ via hybrid flow com hand-off, Jornada de Compartilhamento de Dados PJ com múltiplos aprovadores).
        
-   **PUX-291 (IN-759)**
    
    -   Atualização de requisitos para a IP na Etapa 3 da Jornada de Crédito Pessoal sem Consignação.
        
    -   Atualização de requisitos para a IP na Gestão de Crédito Pessoal sem Consignação.
        
    -   Atualização de requisitos para a IC na Gestão de Crédito Pessoal sem Consignação.
        

* * *

# Compartilhamento de Dados PF

## Compartilhamento de Dados PF via Hybrid Flow > Etapa 1

### **Recomendações - IR**

**Cenário: Onboarding**

Tipo

De (v. 22.01.00)

Para (v. 23.00.00)

**Adição de recomendação**

N/A

`REC.DC-01110` No início da jornada de compartilhamento de dados, ao menos no primeiro acesso do usuário, exibir onboarding para informar o usuário sobre o compartilhamento de dados.

**Adição de recomendação**

N/A

`REC.DC-01120` No onboarding, informar o usuário sobre a segurança do processo de compartilhamento de dados.

**Adição de recomendação**

N/A

`REC.DC-01131` No onboarding, informar o usuário sobre a seleção da instituição transmissora.

**Adição de recomendação**

N/A

`REC.DC-01140` No onboarding, informar o usuário sobre a possibilidade de escolha dos dados a serem compartilhados.

**Adição de recomendação**

N/A

`REC.DC-01150` No onboarding, informar o usuário sobre a possibilidade de definição do prazo de compartilhamento dos dados.

**Adição de recomendação**

N/A

`REC.DC-01161` No onboarding, informar o usuário sobre a necessidade de confirmação do compartilhamento de dados na instituição transmissora escolhida.

## Jornada de Compartilhamento de Dados PF via hybrid flow > Etapa 6

### **Requisitos - IR**

**Cenário: Mensagem de sucesso**

Tipo

De (v. 22.01.00)

Para (v. 23.00.00)

**Adição de requisito**

N/A

`REQ.DC-10810` Informar, com destaque, o caminho para acessar a área de gestão de compartilhamento de dados da IR.

**Adição de requisito**

N/A

`REQ.DC-10820` Informar, com destaque, que o compartilhamento de dados pode ser cancelado a qualquer momento tanto na IR quanto na IT.

**Adição de requisito**

N/A

`REQ.DC-10830` Se a IR oferecer alteração do compartilhamento de dados, informar, com destaque, que o compartilhamento de dados pode ser alterado a qualquer momento.

**Adição de requisito**

N/A

`REQ.DC-10840` Se a IR oferecer renovação (padrão ou simplificada) do compartilhamento de dados, no caso de vencimento determinado, informar, com destaque, que o compartilhamento de dados pode ser renovado a qualquer momento.

## Compartilhamento de Dados PF via Hybrid Flow com hand-off > Etapa 1

### **Recomendações - IR**

**Cenário: Onboarding**

-   Reaproveitamento de 6 recomendações: `REC.DC-01110`, `REC.DC-01120`, `REC.DC-01131`, `REC.DC-01140`, `REC.DC-01150`, `REC.DC-01161`.
    

## Jornada de Compartilhamento de Dados PF via hybrid flow com hand-off > Etapa 6

### **Requisitos - IR**

**Cenário: Mensagem de sucesso**

-   Reaproveitamento de 4 requisitos: `REQ.DC-10810`, `REQ.DC-10820`, `REQ.DC-10830`, `REQ.DC-10840`.
    

## Compartilhamento de Dados PF via CIBA > Etapa 1

### **Requisitos - IR**

**Cenário: Início do compartilhamento**

-   Reaproveitamento de 12 requisitos: `REQ.DC-04000`, `REQ.DC-04100`, `REQ.DC-04200`, `REQ.DC-04300`, `REQ.DC-04400`, `REQ.DC-04500`, `REQ.DC-04600`, `REQ.DC-04700`, `REQ.DC-04800`, `REQ.DC-04900`, `REQ.DC-05000`, `REQ.DC-05100`.
    

**Cenário: Seleção da IT**

Tipo

De (v. 22.01.00)

Para (v. 23.00.00)

**Adição de requisito**

N/A

`REQ.DC-05110` Quando a instituição disponibilizar seleção múltipla de instituições transmissoras, permitir que o usuário selecione até cinco instituições para a mesma solicitação de compartilhamento.

**Adição de requisito**

N/A

`REQ.DC-05120` Impedir que o usuário avance sem ter escolhido pelo menos uma instituição transmissora.

**Adição de requisito**

N/A

`REQ.DC-05130` Impedir que o usuário selecione mais de cinco instituições transmissoras.

**Cenário: Seleção de dados**

-   Reaproveitamento de 6 requisitos: `REQ.DC-05200`, `REQ.DC-05300`, `REQ.DC-05400`, `REQ.DC-05500`, `REQ.DC-05600`, `REQ.DC-05700`.
    

Tipo

De (v. 22.01.00)

Para (v. 23.00.00)

**Adição de requisito**

N/A

`REQ.DC-05710` Não permitir que o usuário selecione dados diferentes para cada transmissora na mesma jornada.

**Adição de requisito**

N/A

`REQ.DC-05720` Exibir mensagem informando que todo o conjunto de dados selecionados será solicitado, de forma idêntica, a todas as transmissoras escolhidas.

**Adição de requisito**

N/A

`REQ.DC-05730` Exibir mensagem informando que as instituições transmissoras não compartilharão dados entre si.

**Cenário: Prazo de consentimento**

-   Reaproveitamento de 4 requisitos: `REQ.DC-05800`, `REQ.DC-05900`, `REQ.DC-06000`, `REQ.DC-06100`.
    

Tipo

De (v. 22.01.00)

Para (v. 23.00.00)

**Adição de requisito**

N/A

`REQ.DC-06110` Não permitir que o usuário selecione prazos de validade do compartilhamento diferentes para cada transmissora na mesma jornada.

**Adição de requisito**

N/A

`REQ.DC-06120` Exibir mensagem informando que todas as transmissoras escolhidas compartilharão os dados pelo mesmo período selecionado pelo usuário.

**Cenário: Informações da solicitação**

-   Reaproveitamento de 5 requisitos: `REQ.DC-06200`, `REQ.DC-06300`, `REQ.DC-06400`, `REQ.DC-06500`, `REQ.DC-06600`.
    

**Cenário: Conclusão da solicitação**

Tipo

De (v. 22.01.00)

Para (v. 23.00.00)

**Adição de requisito**

N/A

`REQ.DC-06610` Após a confirmação da solicitação de compartilhamento pelo usuário, exibir tela de Conclusão da solicitação.

**Adição de requisito**

N/A

`REQ.DC-06620` Na tela de Conclusão da solicitação, orientar o usuário a acessar o ambiente da(s) instituição(ões) transmissora(s).

**Adição de requisito**

N/A

`REQ.DC-06630` Na tela de Conclusão da solicitação, orientar o usuário a acessar a área de gestão Open Finance das instituições transmissoras para confirmar a solicitação de compartilhamento.

**Adição de requisito**

N/A

`REQ.DC-06640` Na tela de Conclusão da solicitação, informar a data, contendo dia, mês e ano e o horário limite contendo horas e minutos para a confirmação, que deve ser feita em até 24 horas.

**Adição de requisito**

N/A

`REQ.DC-06650` Na tela de Conclusão da solicitação, exibir o nome de cada instituição transmissora escolhida.

**Adição de requisito**

N/A

`REQ.DC-06660` Na tela de Conclusão da solicitação, exibir o logotipo de cada instituição transmissora escolhida.

**Adição de requisito**

N/A

`REQ.DC-06670` Na tela de Conclusão da solicitação, exibir o status inicial da solicitação de cada instituição transmissora escolhida.

**Adição de requisito**

N/A

`REQ.DC-06680` Na tela de Conclusão da solicitação, antes que o usuário saia dessa tela, exibir alerta informando-o sobre a necessidade de acesso aos ambientes das instituições transmissoras escolhidas para confirmar a solicitação.

### **Recomendações - IR**

**Cenário: Onboarding**

-   Reaproveitamento de 4 recomendações: `REC.DC-01110`, `REC.DC-01120`, `REC.DC-01140`, `REC.DC-01150`.
    

Tipo

De (v. 22.01.00)

Para (v. 23.00.00)

**Adição de recomendação**

N/A

`REC.DC-01130` No onboarding, quando a instituição oferecer a seleção múltipla de instituições transmissoras,  
informar o usuário que ele poderá selecionar até cinco instituições para compartilhamento de  
dados.

**Adição de recomendação**

N/A

`REC.DC-01160` No onboarding, informar o usuário sobre a necessidade de confirmação do compartilhamento  
individualmente em cada uma das instituições transmissoras escolhidas.

**Cenário: Resumo da solicitação**

Tipo

De (v. 22.01.00)

Para (v. 23.00.00)

**Adição de recomendação**

N/A

`REC.DC-02110` Exibir resumo da solicitação.

**Adição de recomendação**

N/A

`REC.DC-02120` No resumo da solicitação, informar todas as instituições transmissoras selecionadas.

**Adição de recomendação**

N/A

`REC.DC-02130` No resumo da solicitação, informar o objetivo do uso dos dados.

**Adição de recomendação**

N/A

`REC.DC-02140` No resumo da solicitação, informar o prazo do compartilhamento.

**Adição de recomendação**

N/A

`REC.DC-02150` No resumo da solicitação, informar os dados compartilhados.

**Cenário: Conclusão da solicitação**

Tipo

De (v. 22.01.00)

Para (v. 23.00.00)

**Adição de recomendação**

N/A

`REC.DC-02160` Na tela de Conclusão da solicitação, exibir indicador visual indicando o status inicial de confirmação de cada instituição transmissora escolhida.

**Adição de recomendação**

N/A

`REC.DC-02170` Permitir que o usuário retorne à tela inicial do ambiente da IR.

**Adição de recomendação**

N/A

`REC.DC-02180` Na tela de Conclusão da solicitação, orientar o usuário sobre a notificação enviada por cada instituição transmissora selecionada para aprovação do compartilhamento.

**Cenário: Informações da solicitação**

-   Reaproveitamento de 10 recomendações: `REC.DC-01200`, `REC.DC-01300`, `REC.DC-01400`, `REC.DC-01500`, `REC.DC-01600`, `REC.DC-01700`, `REC.DC-01800`, `REC.DC-01900`, `REC.DC-02000`, `REC.DC-02100`.
    

## Compartilhamento de Dados PF via CIBA > Etapa 2

### **Requisitos - IT**

**Cenário: Notificação para aprovação**

Tipo

De (v. 22.01.00)

Para (v. 23.00.00)

**Adição de requisito**

N/A

`REQ.DC-06690` Notificar ativamente o usuário, no mínimo uma vez, sobre a existência de pendência de confirmação.

**Adição de requisito**

N/A

`REQ.DC-06695` Não utilizar SMS ou e-mail para notificação de pendência de confirmação.

**Adição de requisito**

N/A

`REQ.DC-06710` Enviar a notificação em até 20 segundos a partir da confirmação da solicitação.

**Adição de requisito**

N/A

`REQ.DC-06720` Na notificação, exibir informações claras sobre a pendência do compartilhamento.

**Adição de requisito**

N/A

`REQ.DC-06730` No ambiente de cada instituição transmissora escolhida, exibir indicador visual sinalizando a existência de pendência de confirmação no Ambiente Open Finance, localizado no primeiro nível de navegação do aplicativo.

**Adição de requisito**

N/A

`REQ.DC-06740` Exibir a pendência de confirmação no Ambiente Open Finance até que o usuário conclua a ação.

**Adição de requisito**

N/A

`REQ.DC-06750` Enquanto a solicitação de confirmação estiver pendente, imediatamente após a autenticação do usuário, exibir, na tela inicial, alerta através de um componente visual de alta prioridade (ex.: bottom sheet ou modal), informando o usuário sobre a pendência de confirmação da solicitação e do prazo para confirmação no Open Finance.

**Adição de requisito**

N/A

`REQ.DC-06760` No alerta, apresentar um botão de ação claro que direcione o usuário diretamente para o fluxo de confirmação do consentimento.

**Adição de requisito**

N/A

`REQ.DC-06770` Permitir que o usuário feche ou ignore o alerta sem cancelar a solicitação.

### **Recomendações - IT**

**Cenário: Notificação para aprovação**

Tipo

De (v. 22.01.00)

Para (v. 23.00.00)

**Adição de recomendação**

N/A

`REC.DC-02210` Disponibilizar, na notificação, deeplink com acesso direto ao fluxo necessário para tratamento da pendência.

**Adição de recomendação**

N/A

`REC.DC-02220` Caso o ambiente operacional tenha essa função, exibir um indicador visual (badge) sobre o ícone do aplicativo da(s) transmissora(s) no dispositivo do usuário sempre que houver notificações ou ações pendentes não lidas.

**Adição de recomendação**

N/A

`REC.DC-02230` Exibir a pendência de confirmação até que o usuário clique no ícone do aplicativo da(s) transmissora(s) no dispositivo.

**Adição de recomendação**

N/A

`REC.DC-02240` Quando disponível, priorizar notificações via push.

### **Requisitos - IR**

**Cenário: Notificação para aprovação**

Tipo

De (v. 22.01.00)

Para (v. 23.00.00)

**Adição de requisito**

N/A

`REQ.DC-06780` No Ambiente Open Finance, localizado no primeiro nível do menu principal de navegação da instituição, exibir indicador visual sinalizando a existência de pendência de confirmação do compartilhamento de dados.

**Adição de requisito**

N/A

`REQ.DC-06790` Exibir a pendência no Ambiente Open Finance até que o usuário conclua a ação.

**Adição de requisito**

N/A

`REQ.DC-06810` Caso a IR notifique o usuário sobre a existência de pendência de confirmação, não utilizar SMS ou e-mail para notificação de pendência de confirmação.

### **Recomendações - IR**

**Cenário: Notificação para aprovação**

Tipo

De (v. 22.01.00)

Para (v. 23.00.00)

**Adição de recomendação**

N/A

`REC.DC-02250` Notificar o usuário sobre a existência de pendência de confirmação.

## Compartilhamento de Dados PF via CIBA > Etapa 3

### **Requisitos - IT**

**Cenário: Login**

-   Reaproveitamento de 4 requisitos: `REQ.DC-07300`, `REQ.DC-07400`, `REQ.DC-07500`, `REQ.DC-07600`.
    

**Cenário: Validação da titularidade**

-   Reaproveitamento de 4 requisitos: `REQ.DC-07700`, `REQ.DC-07800`, `REQ.DC-07900`, `REQ.DC-08000`.
    

## Compartilhamento de Dados PF via CIBA > Etapa 4

### **Requisitos - IT**

**Cenário: Informações de consentimento**

-   Reaproveitamento de 5 requisitos: `REQ.DC-08100`, `REQ.DC-08110`, `REQ.DC-08120`, `REQ.DC-08200`, `REQ.DC-08300`.
    

**Cenário: Seleção de origem**

-   Reaproveitamento de 7 requisitos: `REQ.DC-08400`, `REQ.DC-08500`, `REQ.DC-08600`, `REQ.DC-08700`, `REQ.DC-08800`, `REQ.DC-08900`, `REQ.DC-09000`.
    

**Cenário: Detalhes dos dados compartilhados**

-   Reaproveitamento de 3 requisitos: `REQ.DC-09100`, `REQ.DC-09200`, `REQ.DC-09300`.
    

**Cenário: Detalhes para a confirmação**

-   Reaproveitamento de 5 requisitos: `REQ.DC-09400`, `REQ.DC-09500`, `REQ.DC-09600`, `REQ.DC-09700`, `REQ.DC-09800`.
    

### **Recomendações - IT**

**Cenário: Detalhes dos dados compartilhados**

-   Reaproveitamento de 2 recomendações: `REC.DC-02300`, `REC.DC-02400`.
    

## Compartilhamento de Dados PF via CIBA > Etapa 5

### **Requisitos - IT**

**Cenário: Mensagem de sucesso**

Tipo

De (v. 22.01.00)

Para (v. 23.00.00)

**Adição de requisito**

N/A

`REQ.DC-11410` Na tela de efetivação, informar o usuário sobre o sucesso ou insucesso do compartilhamento de dados.

**Adição de requisito**

N/A

`REQ.DC-11420` Na tela de efetivação, exibir mensagem neutra e sem estímulo ou indicação de cancelamento do compartilhamento de dados.

**Adição de requisito**

N/A

`REQ.DC-11430` Na tela de efetivação, informar o usuário sobre a possibilidade de gerenciamento do compartilhamento de dados na Área de Gestão do Open Finance.

**Cenário: Detalhes do consentimento**

Tipo

De (v. 22.01.00)

Para (v. 23.00.00)

**Adição de requisito**

N/A

`REQ.DC-11440` Em caso de sucesso, exibir um resumo da solicitação.

**Adição de requisito**

N/A

`REQ.DC-11450` No resumo da solicitação, apresentar o prazo e a data final. Em caso de prazo indeterminado, identificar como “Indeterminado” ou termo equivalente.

**Adição de requisito**

N/A

`REQ.DC-11460` No resumo da solicitação, apresentar os tipos de dados compartilhados, como dados cadastrais, contas, cartões de crédito, investimentos e operações de crédito.

**Cenário: Consentimento recém confirmado**

-   Reaproveitamento de 1 requisito: `REQ.DC-11400`.
    

## Compartilhamento de Dados PF via Hybrid Flow com CIBA como fallback > Etapa 1

### **Requisitos - IR**

**Cenário: Início do compartilhamento**

-   Reaproveitamento de 12 requisitos: `REQ.DC-04000`, `REQ.DC-04100`, `REQ.DC-04200`, `REQ.DC-04300`, `REQ.DC-04400`, `REQ.DC-04500`, `REQ.DC-04600`, `REQ.DC-04700`, `REQ.DC-04800`, `REQ.DC-04900`, `REQ.DC-05000`, `REQ.DC-05100`.
    

**Cenário: Seleção de dados**

-   Reaproveitamento de 6 requisitos: `REQ.DC-05200`, `REQ.DC-05300`, `REQ.DC-05400`, `REQ.DC-05500`, `REQ.DC-05600`, `REQ.DC-05700`.
    

**Cenário: Prazo de consentimento**

-   Reaproveitamento de 4 requisitos: `REQ.DC-05800`, `REQ.DC-05900`, `REQ.DC-06000`, `REQ.DC-06100`.
    

**Cenário: Informações da solicitação**

-   Reaproveitamento de 5 requisitos: `REQ.DC-06200`, `REQ.DC-06300`, `REQ.DC-06400`, `REQ.DC-06500`, `REQ.DC-06600`.
    

### **Recomendações - IR**

**Cenário: Onboarding**

-   Reaproveitamento de 6 recomendações: `REC.DC-01110`, `REC.DC-01120`, `REC.DC-01131`, `REC.DC-01140`, `REC.DC-01150`, `REC.DC-01161`.
    

**Cenário: Informações da solicitação**

-   Reaproveitamento de 10 recomendações: `REC.DC-01200`, `REC.DC-01300`, `REC.DC-01400`, `REC.DC-01500`, `REC.DC-01600`, `REC.DC-01700`, `REC.DC-01800`, `REC.DC-01900`, `REC.DC-02000`, `REC.DC-02100`.
    

## Compartilhamento de Dados PF via Hybrid Flow com CIBA como fallback > Etapa 2

### **Requisitos - IR**

**Cenário: Tela de transição**

-   Reaproveitamento de 5 requisitos: `REQ.DC-06800`, `REQ.DC-06900`, `REQ.DC-07000`, `REQ.DC-07100`, `REQ.DC-07200`.
    

### **Requisitos - IT**

**Cenário: Seleção de métodos de direcionamento**

-   Reaproveitamento de 1 requisito: `REQ.DC-06700`.
    

### **Recomendações - IR**

**Cenário: Tela de transição**

-   Reaproveitamento de 1 recomendação: `REC.DC-02200`.
    

## Compartilhamento de Dados PF via Hybrid Flow com CIBA como fallback > Etapa 2.1

### **Requisitos - IR**

**Cenário: Acionamento do fallback**

Tipo

De (v. 22.01.00)

Para (v. 23.00.00)

**Adição de requisito**

N/A

`REQ.DC-07210` Utilizar CIBA como fallback quando expirado o tempo do request\_uri de 10min de aprovação pelo processo OU a receptora identificar abandono de jornada, OU qualquer outra falha identificada pela receptora.

**Adição de requisito**

N/A

`REQ.DC-07220` Caso o usuário tente solicitar um novo compartilhamento de dados idêntico a uma solicitação já pendente de confirmação, exibir alerta informando que já existe uma solicitação pendente de confirmação, direcionando-o para a área de gestão.

**Adição de requisito**

N/A

`REQ.DC-07230` Quando aplicável, informar o usuário sobre o consentimento pendente na área de gestão do Open Finance.

### **Recomendações - IR**

**Cenário: Tela de Conclusão da solicitação**

Tipo

De (v. 22.01.00)

Para (v. 23.00.00)

**Adição de recomendação**

N/A

`REC.DC-02260` Se houver fallback, direcionar o usuário para a tela de Conclusão da solicitação.

**Adição de recomendação**

N/A

`REC.DC-02270` Na tela de Conclusão da solicitação, informar o usuário, quando aplicável, sobre a ocorrência de falha no direcionamento.

**Adição de recomendação**

N/A

`REC.DC-02280` Na tela de Conclusão da solicitação, informar o usuário sobre a possibilidade de continuar a jornada sem a necessidade de reinício do processo.

**Adição de recomendação**

N/A

`REC.DC-02281` Após a confirmação da solicitação de compartilhamento pelo usuário, exibir tela de conclusão da solicitação.

**Adição de recomendação**

N/A

`REC.DC-02282` Na tela de conclusão da solicitação, orientar o usuário a acessar o ambiente da(s) instituição(ões) transmissora(s).

**Adição de recomendação**

N/A

`REC.DC-02283` Na tela de conclusão da solicitação, orientar o usuário a acessar a área de gestão Open Finance das instituições transmissoras para confirmar a solicitação de compartilhamento.

**Adição de recomendação**

N/A

`REC.DC-02284` Na tela de conclusão da solicitação, informar a data, contendo dia, mês e ano e o horário limite contendo horas e minutos para a confirmação, que deve ser feita em até 24 horas.

**Adição de recomendação**

N/A

`REC.DC-02285` Na tela de conclusão da solicitação, exibir o nome de cada instituição transmissora escolhida.

**Adição de recomendação**

N/A

`REC.DC-02286` Na tela de conclusão da solicitação, exibir o logotipo de cada instituição transmissora escolhida.

**Adição de recomendação**

N/A

`REC.DC-02287` Na tela de conclusão da solicitação, exibir o status inicial da solicitação de cada instituição transmissora escolhida.

**Adição de recomendação**

N/A

`REC.DC-02288` Na tela de conclusão da solicitação, antes que o usuário saia dessa tela, exibir alerta informando-o sobre a necessidade de acesso aos ambientes das instituições transmissoras escolhidas para confirmar a solicitação.

## Compartilhamento de Dados PF via Hybrid Flow com CIBA como fallback > Etapa 2.2

### **Requisitos - IT**

**Cenário: Notificação para aprovação**

-   Reaproveitamento de 8 requisitos: `REQ.DC-06690`, `REQ.DC-06695`, `REQ.DC-06720`, `REQ.DC-06730`, `REQ.DC-06740`, `REQ.DC-06750`, `REQ.DC-06760`, `REQ.DC-06770`.
    

Tipo

De (v. 22.01.00)

Para (v. 23.00.00)

**Adição de requisito**

N/A

`REQ.DC-06711` Enviar a notificação em até 20 segundos a partir do acionamento do fallback.

### **Requisitos - IR**

**Cenário: Notificação para aprovação**

-   Reaproveitamento de 3 requisitos: `REQ.DC-06780`, `REQ.DC-06790`, `REQ.DC-06810`.
    

### **Recomendações - IT**

**Cenário: Notificação para aprovação**

-   Reaproveitamento de 4 recomendações: `REC.DC-02210`, `REC.DC-02220`, `REC.DC-02230`, `REC.DC-02240`.
    

### **Recomendações - IR**

**Cenário: Notificação para aprovação**

-   Reaproveitamento de 1 recomendação: `REC.DC-02250`.
    

## Compartilhamento de Dados PF via Hybrid Flow com CIBA como fallback > Etapa 3

### **Requisitos - IT**

**Cenário: Login**

-   Reaproveitamento de 4 requisitos: `REQ.DC-07300`, `REQ.DC-07400`, `REQ.DC-07500`, `REQ.DC-07600`.
    

**Cenário: Validação da titularidade**

-   Reaproveitamento de 4 requisitos: `REQ.DC-07700`, `REQ.DC-07800`, `REQ.DC-07900`, `REQ.DC-08000`.
    

## Compartilhamento de Dados PF via Hybrid Flow com CIBA como fallback > Etapa 4

### **Requisitos - IT**

**Cenário: Informações de consentimento**

-   Reaproveitamento de 5 requisitos: `REQ.DC-08100`, `REQ.DC-08110`, `REQ.DC-08120`, `REQ.DC-08200`, `REQ.DC-08300`.
    

**Cenário: Seleção de origem**

-   Reaproveitamento de 7 requisitos: `REQ.DC-08400`, `REQ.DC-08500`, `REQ.DC-08600`, `REQ.DC-08700`, `REQ.DC-08800`, `REQ.DC-08900`, `REQ.DC-09000`.
    

**Cenário: Detalhes dos dados compartilhados**

-   Reaproveitamento de 3 requisitos: `REQ.DC-09100`, `REQ.DC-09200`, `REQ.DC-09300`.
    

**Cenário: Detalhes para a confirmação**

-   Reaproveitamento de 5 requisitos: `REQ.DC-09400`, `REQ.DC-09500`, `REQ.DC-09600`, `REQ.DC-09700`, `REQ.DC-09800`.
    

### **Recomendações - IT**

**Cenário: Detalhes dos dados compartilhados**

-   Reaproveitamento de 2 recomendações: `REC.DC-02300`, `REC.DC-02400`.
    

## Compartilhamento de Dados PF via Hybrid Flow com CIBA como fallback > Etapa 5

### **Requisitos - IT**

**Cenário: Mensagem de sucesso**

-   Reaproveitamento de 3 requisitos: `REQ.DC-11410`, `REQ.DC-11420`, `REQ.DC-11430`.
    

**Cenário: Detalhes do consentimento**

-   Reaproveitamento de 3 requisitos: `REQ.DC-11440`, `REQ.DC-11450`, `REQ.DC-11460`.
    

**Cenário: Consentimento recém confirmado**

-   Reaproveitamento de 1 requisito: `REQ.DC-11400`.
    

## Gestão de Compartilhamento de Dados PF

### **Requisitos - IR**

**Cenário: Histórico dos consentimentos - Geral**

Tipo

De (v. 22.01.00)

Para (v. 23.00.00)

**Adição de requisito**

N/A

`REQ.DC-00950` No histórico de compartilhamento de dados, quando a solicitação estiver pendente, informar de forma explícita que há uma ação necessária do usuário indicando a instituição onde a ação deve ser realizada.

**Adição de requisito**

N/A

`REQ.DC-00960` No histórico de compartilhamento de dados, exibir o nome da instituição que está transmitindo o compartilhamento.

**Adição de requisito**

N/A

`REQ.DC-00970` No histórico de compartilhamento de dados, informar a data, contendo dia, mês e ano e o horário limite contendo horas e minutos para a confirmação da solicitação do compartilhamento de dados pendente, que deve ser feita em até 24 horas a partir da conclusão da solicitação.

**Adição de requisito**

N/A

`REQ.DC-00980` Nos detalhes do compartilhamento de dados, exibir o nome da instituição que está transmitindo o compartilhamento.

**Cenário: Cancelamento de consentimento pendente - Geral**

Tipo

De (v. 22.01.00)

Para (v. 23.00.00)

**Adição de requisito**

N/A

`REQ.DC-00990` Nos detalhes do compartilhamento de dados, permitir que o usuário cancele a solicitação pendente.

**Adição de requisito**

N/A

`REQ.DC-00995` Ao confirmar o cancelamento de uma solicitação pendente, exibir mensagem de sucesso informando que a solicitação foi cancelada.

**Cenário: Alteração do consentimento - Geral**

Tipo

De (v. 22.01.00)

Para (v. 23.00.00)

**Alteração de requisito**

`REQ.DC-01600` Se oferecer a jornada de alteração, informar claramente ao usuário que será necessária uma nova confirmação na Instituição Transmissora de Dados, e direcioná-lo para essa instituição.

`REQ.DC-01600` Se oferecer a jornada de alteração, informar claramente ao usuário que será necessária uma nova confirmação na Instituição Transmissora de Dados, conforme protocolo escolhido pela Instituição Receptora de Dados.

**Cenário: Renovação padrão do consentimento - Geral**

Tipo

De (v. 22.01.00)

Para (v. 23.00.00)

**Alteração de requisito**

`REQ.DC-01650` Se oferecer jornada de renovação padrão, informar claramente ao usuário que será necessária uma nova confirmação na instituição Transmissora de Dados, e direcioná-lo para essa instituição.

`REQ.DC-01650` Se oferecer jornada de renovação padrão, informar claramente ao usuário que será necessária uma nova confirmação na instituição Transmissora de Dados, conforme protocolo escolhido pela Instituição Receptora de Dados.

**Cenário: Detalhes do consentimento - CIBA PF**

Tipo

De (v. 22.01.00)

Para (v. 23.00.00)

**Adição de requisito**

N/A

`REQ.DC-00996` Nos detalhes do compartilhamento de dados, quando a solicitação estiver pendente, orientar o usuário a acessar o ambiente Open Finance da Instituição Transmissora para confirmar a solicitação.

**Adição de requisito**

N/A

`REQ.DC-00997` Nos detalhes do compartilhamento de dados, informar a data, contendo dia, mês e ano e o horário limite contendo horas e minutos para a confirmação da solicitação de compartilhamento de dados pendente, que deve ser feita em até 24 horas a partir da conclusão da solicitação.

**Adição de requisito**

N/A

`REQ.DC-00998` Nos detalhes do compartilhamento de dados, quando o prazo para confirmação expirar, informar claramente que a solicitação foi encerrada e orientar o usuário sobre como iniciar uma nova solicitação.

### **Recomendações - IR**

**Cenário: Histórico dos consentimentos - Geral**

Tipo

De (v. 22.01.00)

Para (v. 23.00.00)

**Adição de recomendação**

N/A

`REC.DC-00650` No histórico e nos detalhes de compartilhamento de dados, quando a solicitação estiver pendente, exibir contador regressivo do prazo para confirmação da solicitação de compartilhamento de dados.

### **Requisitos - IT**

**Cenário: Histórico de consentimentos - Geral**

Tipo

De (v. 22.01.00)

Para (v. 23.00.00)

**Adição de requisito**

N/A

`REQ.DC-00720` No histórico de compartilhamento de dados, exibir o nome da instituição que está recebendo o compartilhamento.

**Adição de requisito**

N/A

`REQ.DC-00730` Nos detalhes do compartilhamento de dados, exibir o nome da instituição que está recebendo o compartilhamento.

**Cenário: Cancelamento de consentimento pendente - Geral**

-   Reaproveitamento de 2 requisitos: `REQ.DC-00990`; `REQ.DC-00995`
    

**Cenário: Histórico dos consentimentos - CIBA PF**

Tipo

De (v. 22.01.00)

Para (v. 23.00.00)

**Adição de requisito**

N/A

`REQ.DC-00760` No histórico de compartilhamento de dados, quando a solicitação estiver pendente, informar de forma explícita que há uma ação necessária do usuário.

**Adição de requisito**

N/A

`REQ.DC-00770` No histórico de compartilhamento de dados, quando a solicitação estiver pendente, informar a data, contendo dia, mês e ano e o horário limite contendo horas e minutos para a confirmação do compartilhamento, que deve ser feita em até 24 horas a partir da conclusão da solicitação.

**Cenário: Detalhes do consentimento - CIBA PF**

Tipo

De (v. 22.01.00)

Para (v. 23.00.00)

**Adição de requisito**

N/A

`REQ.DC-00780` Nos detalhes do compartilhamento de dados, quando a solicitação estiver pendente, informar a data, contendo dia, mês e ano e o horário limite contendo horas e minutos para a confirmação do compartilhamento, que deve ser feita em até 24 horas a partir da conclusão da solicitação.

**Adição de requisito**

N/A

`REQ.DC-00790` Nos detalhes do compartilhamento de dados, permitir que o usuário confirme a solicitação pendente.

**Adição de requisito**

N/A

`REQ.DC-00795` Nos detalhes do compartilhamento de dados, após a confirmação da solicitação pendente, direcionar o usuário para a etapa de Efetivação do compartilhamento de dados.

### **Recomendações - IT**

**Cenário: Histórico dos consentimentos - Geral**

-   Reaproveitamento de 1 recomendação: `REC.DC-00650`.
    

* * *

# Compartilhamento de Dados PJ

## Jornada de Compartilhamento de Dados PJ via hybrid flow > Etapa 6

### **Requisitos - IR**

**Cenário: Mensagem de sucesso**

-   Reaproveitamento de 4 requisitos: `REQ.DC-10810`, `REQ.DC-10820`, `REQ.DC-10830`, `REQ.DC-10840`.
    

## Jornada de Compartilhamento de Dados PJ via hybrid flow com hand-off > Etapa 6

### **Requisitos - IR**

**Cenário: Mensagem de sucesso**

-   Reaproveitamento de 4 requisitos: `REQ.DC-10810`, `REQ.DC-10820`, `REQ.DC-10830`, `REQ.DC-10840`.
    

## Jornada de Compartilhamento de Dados PJ com múltiplos aprovadores > Etapa 6

### **Requisitos - IR**

**Cenário: Mensagem de sucesso**

-   Reaproveitamento de 4 requisitos: `REQ.DC-10810`, `REQ.DC-10820`, `REQ.DC-10830`, `REQ.DC-10840`.
    

* * *

# Pix Agendado

## Pix Agendado via Hybrid Flow > Etapa 5

### Requisitos - ITP

**Cenário: Efetivação de transação de pagamento**

Tipo

De (22.01.00)

Para (23.00.00)

**Adição de requisito**

N/A

`REQ.PG-07809` Informar, com destaque, o caminho para acessar a autorização de pagamento na ITP.

**Adição de requisito**

N/A

`REQ.PG-07810` Informar, com destaque, que a autorização de pagamento pode ser cancelada tanto na ITP quanto na ID.

**Adição de requisito**

N/A

`REQ.PG-07811` Se a ITP oferecer alteração da autorização de pagamento, informar, com destaque, que a autorização pode ser alterada.

### Recomendações - ITP

**Cenário: Efetivação de transação de pagamento**

Tipo

De (22.01.00)

Para (23.00.00)

**Alteração de reomendação**

`REC.PG-02102` Informar sobre a possibilidade de cancelamento do(s) agendamento(s) e o horário limite conforme definido pelo arranjo de pagamento.

Ex.: Você pode cancelar o pagamento até às 23:59 do dia anterior à data agendada.

`REC.PG-02102` Informar o horário limite para cancelamento conforme definido pelo arranjo de pagamento.

Ex.: Você pode cancelar o pagamento até às 23:59 do dia anterior à data agendada.

## Pix agendado via JSR > Etapa 3

### Requisitos - ITP

**Cenário: Efetivação de transação de pagamento**

-   Reaproveitamento de 3 requisitos: `REQ.PG-07809`, `REQ.PG-07810`, `REQ.PG-07811`.
    

### Recomendações - ITP

**Cenário: Efetivação de transação de pagamento**

-   Reaproveitamento de 1 recomendação: `REC.PG-02102`.
    

* * *

# Pix Automático

## Jornada de Pix Automático via Hybrid Flow > Etapa 5

### Requisitos - ITP

**Cenário: Efetivação de transação de pagamento**

Tipo

De (22.01.00)

Para (23.00.00)

**Adição de requisito**

N/A

`REQ.PG-07812` Informar, com destaque, o caminho para acessar e gerenciar a autorização de pagamento na ITP.

-   Reaproveitamento de 1 requisito: `REQ.PG-07810`.
    

### Recomendações - ITP

**Cenário: Efetivação de transação de pagamento**

-   Reaproveitamento de 1 recomendação: `REC.PG-02102`.
    

## Pix automático via JSR > Etapa 3

### Requisitos - ITP

**Cenário: Efetivação de transação de pagamento**

-   Reaproveitamento de 2 requisitos: `REQ.PG-07812`, `REQ.PG-07810`.
    

### Recomendações - ITP

**Cenário: Efetivação de transação de pagamento**

-   Reaproveitamento de 1 recomendação: `REC.PG-02102`.
    

* * *

# Transferências Inteligentes

## Jornada de Transferências Inteligentes via Hybrid Flow > Etapa 5: Efetivação

### Requisitos - ITP

**Cenário: Efetivação de transação de pagamento**

-   Reaproveitamento de 2 requisitos: `REQ.PG-07812`, `REQ.PG-07810`.
    

### Recomendações - ITP

**Cenário: Efetivação da autorização**

Tipo

De (22.01.00)

Para (23.00.00)

**Remoção de recomendação**

`REC.PG-03300` Informar sobre a possibilidade de cancelamento da autorização e, quando aplicável, o horário limite.

N/A

**Remoção de recomendação**

`REC.PG-03400` Informar sobre a possibilidade de alteração dos limites da autorização.

N/A

**Remoção de recomendação**

`REC.PG-03500` Informar sobre a possibilidade de alteração das contas recebedoras.

N/A

**Remoção de recomendação**

`REC.PG-03600` Informar sobre a possibilidade de alteração do recebimento de notificações, quando disponibilizadas.

N/A

-   Reaproveitamento de 1 recomendação: `REC.PG-02102`.
    

* * *

# Crédito Pessoal sem Consignação (CPC)

## Jornada do CPC > Etapa 3

### Requisitos - IP

**Cenário: Solicitação da Portabilidade de crédito**

Tipo

De (22.01.00)

Para (23.00.00)

**Adição de requisito**

N/A

`REQ.PC-01201` Informar ao usuário, durante a etapa de solicitação, que eventuais garantias vinculadas ao contrato original não são transferidas na portabilidade.

## Gestão de CPC

### Requisitos - IP

**Cenário: Pedido em análise**

Tipo

De (22.01.00)

Para (23.00.00)

**Adição de requisito**

N/A

`REQ.PC-04601` Na tela de detalhes do status Pedido em análise, informar ao usuário que eventuais garantias vinculadas ao contrato original não são transferidas na portabilidade.

**Cenário: Proposta disponível**

Tipo

De (22.01.00)

Para (23.00.00)

**Adição de requisito**

N/A

`REQ.PC-05301` Na tela de detalhes do status Proposta disponível, informar ao usuário que eventuais garantias vinculadas ao contrato original não são transferidas na portabilidade.

**Cenário: Portabilidade em andamento**

Tipo

De (22.01.00)

Para (23.00.00)

**Adição de requisito**

N/A

`REQ.PC-05601` Na tela de detalhes do status Portabilidade em andamento, informar ao usuário que eventuais garantias vinculadas ao contrato original não são transferidas na portabilidade.

**Cenário: Portabilidade concluída**

Tipo

De (22.01.00)

Para (23.00.00)

**Adição de requisito**

N/A

`REQ.PC-05701` Na tela de detalhes do status Portabilidade concluída, informar ao usuário que eventuais garantias vinculadas ao contrato original não foram transferidas na portabilidade.

### Requisitos - IC

**Cenário: Portabilidade em andamento**

Tipo

De (22.01.00)

Para (23.00.00)

**Adição de requisito**

N/A

`REQ.PC-07501` Na tela de detalhes do status Portabilidade em andamento, informar ao usuário que eventuais garantias vinculadas ao contrato original não são transferidas na portabilidade.

**Cenário: Portabilidade concluída**

Tipo

De (22.01.00)

Para (23.00.00)

**Adição de requisito**

N/A

`REQ.PC-08601` Na tela de detalhes do status Portabilidade concluída, informar ao usuário que eventuais garantias vinculadas ao contrato original não foram transferidas na portabilidade.
