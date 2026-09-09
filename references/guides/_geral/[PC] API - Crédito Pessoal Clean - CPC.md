# [PC] API - Crédito Pessoal Clean - CPC

none

## 1\. Contexto

A portabilidade de crédito no Open Finance permite que os usuários transfiram suas operações de crédito e arrendamento mercantil entre instituições financeiras em busca de melhores condições.

**Crédito Pessoal Clean** (CPC) é a forma mais simples de um empréstimo para pessoas físicas, onde a contratação é rápida, sem burocracia e sem a necessidade de apresentar um bem como garantia, também conhecido como "empréstimo pessoal sem garantia" ou "crédito sem garantias".

Atualmente, a solicitação de portabilidade pode ser feita via registradora, mas esse processo pode ser demorado e complexo, desestimulando os clientes a utilizarem o serviço.

## 2\. Cronograma

![image-20250829-131630.png](https://openfinancebrasil.atlassian.net/wiki/rest/api/content/905740587/child/attachment/att1326579757/download)

## **3\. Obrigatoriedade de Participação**

De acordo com o regulador, a obrigatoriedade é vinculada à participação no Compartilhamento de Dados: Com as instituições que ofertam ou possuem clientes na modalidade de empréstimo para o produto CPC, no papel de Instituição Credora Original e/ou Instituição Proponente.

-   Participação obrigatória para instituições do S1, S2 com mais de 5M de clientes.
    
-   Regras de reciprocidade para S3–S5, se atuar como Proponente, deverá atuar como Instituição Credora Original.
    
-   A participação como Instituição Credora Original é obrigatória, enquanto o papel de Instituição Proponente é voluntário.
    
-   Instituição financeira que participar do compartilhamento de dados no Open Finance deve participar da portabilidade como Instituição Credora Original, e vice-versa.
    
-   Conforme atualizações recentes na regulamentação do Open Finance, a participação voluntária no compartilhamento de dados e, consequentemente na portabilidade, implica a participação de todas as instituições do conglomerado
    

## 4\. Documentação Negocial

As documentações de negócio no contexto do Open Finance e da Portabilidade de Crédito são fundamentais para padronizar regras, jornadas e requisitos, garantindo clareza, alinhamento regulatório e interoperabilidade entre as instituições participantes.

true0true0

## 5\. Mapeamento Visual da Jornada

O mapeamento visual da jornada do produto Portabilidade de Crédito é um recurso essencial para garantir o entendimento, a padronização e a eficiência no ecossistema do Open Finance Brasil. Ele permite que todos os participantes, instituições financeiras, desenvolvedores e áreas de negócio compreendam de forma rápida e assertiva como o processo funciona de ponta a ponta.

Este material reúne todos os diagramas da jornada de portabilidade de crédito para o produto **Crédito Pessoal Clean (CPC)**, com o objetivo de apresentar, de forma clara, o fluxo principal e os cenários alternativos.

Os conteúdos estão organizados para representar toda jornada, desde a solicitação de portabilidade até os possíveis desfechos, como efetivação, contraproposta ou cancelamento pelo cliente, entre outros.

true0true0

## 6\. Documentação Técnica

Esta página reúne as especificações técnicas para a implementação do serviço de Portabilidade de Crédito no âmbito do Open Finance Brasil, com foco no produto **Crédito Pessoal Clean**. O objetivo é fornecer às instituições participantes as informações necessárias para garantir a integração correta com as APIs, assegurando conformidade regulatória, interoperabilidade e consistência nos fluxos operacionais.

Nesta documentação, você encontrará orientações detalhadas sobre:

2true0

O conteúdo aqui apresentado é fundamental para garantir que as implementações sejam realizadas de forma padronizada, segura e eficiente, proporcionando uma jornada fluida para os consumidores no ecossistema do Open Finance.

## 7\. Histórico das especificações

O produto **Crédito Pessoal Clean (CPC)** está sendo desenvolvido de forma incremental, em colaboração com as Instituições Financeiras por meio do Grupo de Trabalho (GT), seguindo o escopo definido pela DTO e adotando um modelo de implementações faseadas. 

O histórico referente às implementações das especificações do produto **Crédito Pessoal Clean (CPC)** está detalhado nos itens abaixo.

1true0

## 8\. FAQ

Para uma melhor organização, as perguntas e respostas a seguir foram organizadas por categorias:

Obrigatoriedade de Participação 1800

1.  **O comitê Gestor do Sistema de Autorregulação da Portabilidade de Operações de Crédito será mantido?**  
    Sim, será mantido.
    
2.  **Os novos entrantes na fase de compartilhamento estão dispensados dos marcos?**  
    _Sim. Os novos entrantes estão dispensados dos marcos intermediários de certificação, mas serão cobrados pelo ticket de certificação e pela publicação das APIs nas datas definidas no cronograma vigente._
    
3.  **Quais são exatamente as datas que os novos entrantes na fase de compartilhamento de dados devem seguir?**  
    _Devem seguir os prazos de certificação e publicação definidos no cronograma oficial._
    
4.  **Se uma instituição passar a ser obrigatória para o compartilhamento de dados apenas em outubro de 2025, quais marcos de portabilidade essa instituição deverá cumprir?**  
    _Os novos entrantes estão dispensados dos marcos intermediários de certificação, mas devem realizar a certificação e a publicação das APIs nas datas definidas no cronograma vigente._
    
5.  **A participação de instituições classificadas como S3 a S5 na portabilidade de crédito é obrigatória?**  
    Para instituições classificadas como S3 a S5, a participação no serviço de portabilidade de crédito é opcional, mas condicionada à reciprocidade. Isso significa que se uma instituição S3, S4 ou S5 quiser atuar como proponente, ela também deverá atuar como credora original.
    
6.  **Instituições S3, S4 e S5 que participam do compartilhamento de dados são obrigadas a ofertar portabilidade de crédito?**  
    Sim. Os requisitos se complementam. Mesmo que a instituição seja classificada como S3, S4 ou S5, se ela participa da fase de compartilhamento de dados, estará obrigada a implementar a API Portabilidade de Crédito. Além disso, a obrigatoriedade se estende às demais instituições pertencentes ao mesmo conglomerado financeiro.
    
7.  **Instituições com mais de 5 milhões de clientes precisam participar?**  
    Sim. A obrigatoriedade é definida de forma complementar, com base em dois critérios:
    
    -   A classificação prudencial (ex.: S3, S4);
        
    -   A participação no compartilhamento de dados, especialmente no caso de instituições com mais de 5 milhões de clientes.
        
8.  **Se uma instituição S4 não participa do compartilhamento de dados e possui menos de 5 milhões de clientes, ela é obrigada a ofertar portabilidade de crédito?**  
    Não. Nesse caso, a participação é considerada voluntária. Caso decida oferecer o serviço, a instituição deverá cumprir todos os requisitos técnicos e operacionais definidos.
    
9.  **Em caso de cessão de contrato para um FIDC, a instituição deixa de ter responsabilidade sobre a portabilidade?**  
    Esse ponto ainda não possui definição formal. Casos assim devem ser submetidos à Associação para análise e eventual posicionamento do Banco Central.
    

Referências/Dúvidas Técnicas1800

10.  **Há previsão de custo para chamada de API?**  
     Não haverá custo.
     
11.  **A API de empréstimo poderá ser aproveitada?**  
     Sim, com as devidas adaptações. Uma API específica de Portabilidade de Crédito também será criada.
     
12.  **O RCO deverá ser considerado nas especificações para a cobrança?**  
     Sim, mas a discussão do tema não é foco do grupo de trabalho.
     
13.  **Como será feito o aviso à proponente sobre a não retenção?**  
     A comunicação ocorrerá por meio da consulta ao pedido de portabilidade de crédito. A instituição credora deve atualizar o estado da máquina de estados desse pedido, enquanto a instituição proponente acompanhará a evolução do processo por meio de consultas periódicas ao endpoint correspondente.
     
14.  **A máquina de estados deve ser atualizada para qual valor? REJECTED ou CANCELLED?**  
     Deve ser atualizada para **Cancelled**, estado utilizado quando o cliente cancela o pedido de portabilidade de crédito antes de a instituição credora sinalizar a não retenção ou de a instituição proponente realizar a liquidação da operação.
     
15.  **Após os 3 dias, se o cliente não aceitar a contraproposta, o status muda para ACCEPTED\_SETTLEMENT\_IN\_PROGRESS. Se a instituição proponente não consultar os dados de pagamento nem efetuar o pagamento, o que deve acontecer? Será considerado decurso de prazo? A portabilidade será cancelada?**  
     Sim. Conforme previsto na documentação técnica (descrição do endpoint `GET /portabilities/{portabilityId}`), as instituições devem consultar periodicamente o estado do pedido. Caso a instituição proponente não realize a liquidação, a instituição credora poderá atualizar o status para "Portabilidade cancelada por falta de liquidação", conforme previsto nos motivos de recusa mencionados no documento de requisitos do produto (PRD).
     
16.  **É possível incluir o campo portabilityId na API GET /account-data, de modo que a credora possa utilizar mais de uma conta, a depender do tipo de produto?**  
     Foi solicitada uma alteração no endpoint `account-data`, uma vez que se identificou que as contas podem variar por tipo de produto, e não por pedido de portabilidade. A especificação será atualizada para refletir essa possibilidade de múltiplas contas por produto.
     
17.  **Quando é mencionado “tipo do produto”, isso inclui os campos productType e productSubTypeCategory?**  
     Sim. Com a diferenciação de contas baseada na localidade e no produto, será possível ter uma conta específica para cada pagamento, identificada pelo portabilityId. Caberá à credora identificar o produto e a localidade, quando aplicável, para exibir corretamente os dados bancários.
     
18.  **Existe um prazo para que o productType e productSubTypeCategory seja incluído na API?**  
     O tema foi pautado no GT Portabilidade e será rediscutido na versão Beta 1 do produto Consignado Federal. Entendeu-se que, em um primeiro momento, a identificação do produto será feita pela API Empréstimos. Quando o segundo produto (Consignado Federal) estiver disponível, uma nova análise será realizada para avaliar a necessidade de inclusão de um campo específico na API Portabilidade de Crédito.
     
19.  **Se já houver um pedido de portabilidade em andamento, a chamada à API POST /portabilities deve retornar um erro ou criar uma portabilidade com status REJECTED?**  
     Deve retornar o erro **422** com a mensagem **"EM\_ANDAMENTO"**.
     
20.  **Existe algum SLA regulamentado para a notificação da instituição credora sobre a liquidação do contrato?**  
     _Sim. O prazo é de 2 dias úteis, conforme descrito no PRD._
     
21.  **A instituição precisa obrigatoriamente implementar os dois fluxos (síncrono e assíncrono)?**  
     _Não. A instituição é obrigada a implementar apenas os requisitos do fluxo que adotar. Caso opte pelos dois, deve implementar ambos._
     
22.  **Os motivos de rejeição são padronizados ou o campo rejectionReason é livre?**  
     A justificativa é feita pelo campo `type` dentro de `rejectionReason`. Caso não esteja mapeada, informar `type = "Outros"` e preencher `typeAdditionalInfo`.
     
23.  **Como é validada a retenção de cliente durante o processo de portabilidade de crédito? A instituição precisa registrar formalmente a ação?**  
     Sim. É necessário registro formal e evidência do aceite do cliente, além da atualização de status e assinatura digital.
     
24.  **A instituição credora aciona ativamente a proponente após o período de retenção do cliente?**  
     Não. A comunicação ocorre via atualização de status no pedido de portabilidade, e a proponente deve consultar a API periodicamente.
     
25.  **No fluxo de cancelamento ou retenção, a instituição credora precisa notificar ativamente a proponente via API ou apenas alterar o status do pedido?**  
     Apenas altera o status. A comunicação é feita por mudança de estado e consulta periódica pela proponente.
     
26.  **Existe risco de duplicidade em pedidos de portabilidade...**  
     Não. Há um mecanismo de gestão de simultaneidade que impede pedidos duplicados para o mesmo contrato.
     

Regras do Produto1800

27.  **Haverá limitação da quantidade de pedidos de portabilidade? E existirá alguma carência de um pedido para outro?**  
     Não haverá limite de quantidade ou carência entre pedidos.
     
28.  **Será possível a troca de modalidade?**  
     Não será possível neste primeiro momento. A portabilidade será limitada de CPC para CPC, mas a possibilidade de troca de modalidade será avaliada futuramente.
     
29.  **Como será realizado o cálculo do saldo devedor?**  
     O cálculo seguirá o método utilizado atualmente pelas instituições financeiras.
     
30.  **Como ficará o fluxo de comparação caso o cliente tenha vários contratos do produto CPC na mesma proponente?**  
     A solicitação de portabilidade será feita individualmente para cada operação.
     
31.  **A portabilidade de crédito do produto CPC no OFB será voltada para Pessoa Física (PF) e Pessoa Jurídica (PJ)?**  
     Apenas para Pessoa Física.
     
32.  **O cancelamento da portabilidade pelo cliente no aplicativo da credora é obrigatório?**  
     _Sim, é obrigatório._
     
33.  **Quais modalidades de Crédito Pessoal não estão inclusas nesta primeira entrega?**  
     Empréstimos com antecipação (Ex.: FGTS, 13º salário, Imposto de Renda, etc), empréstimos com qualquer tipo de garantia, empréstimos atrelados a limite de crédito e empréstimos com fluxo de pagamento irregular.
     
34.  **Com a disponibilização do fluxo de PC no OFB, ainda será possível realizar a solicitação de PC via registradora (Núclea)?**  
     Sim, será possível, porém será necessário a instituição credora implementar políticas para impedir simultaneidade.
     
35.  **A oferta de contraproposta diminuirá as chances de a instituição credora ofertar a melhor taxa na adesão do contrato? Existirá limite de contraproposta?**  
     Não, desde que as contrapropostas ocorram dentro de 3 dias úteis.
     
36.  **O que acontecerá se a instituição credora original não responder dentro de 3 dias úteis?**  
     Trata-se de uma inconformidade da credora. O pedido ficará pendente de liquidação até atualização obrigatória de status pela credora original. Além disso, casos de inconformidade serão notificados ao Banco Central.
     
37.  **Para uma operação ser portada, ela precisa estar em dia?**  
     Não há regulamentação específica. A decisão de portar ou não operações em atraso caberá à instituição proponente.
     
38.  **Para operações portadas via OFB, é necessário que a Núclea seja notificada ao término do processo?**  
     Não, exceto em casos de simultaneidade.
     
39.  **Qual o procedimento se o cliente solicitar a portabilidade por diferentes IFs para o mesmo contrato em vias distintas?**  
     A regra de simultaneidade será por ordem de solicitação.
     
40.  **Durante a jornada de portabilidade, se o cliente falecer, como será tratada a contraproposta?**  
     O prazo de 3 dias úteis para a contraproposta será respeitado, a menos que haja manifestação para aceitá-la ou cancelar o pedido original.
     
41.  **Se a proponente faz uma proposta ao cliente com base no saldo devedor em D0, o cliente assina concordando com essa proposta e, em D3, o saldo devedor é atualizado, como ficam os valores pactuados com o cliente e o valor a ser enviado à credora original?**  
     No momento da assinatura do contrato, o cliente deve ser informado sobre a possibilidade de atualização/oscilação no saldo devedor. Dessa forma, ele estará ciente de que poderá haver alterações nos valores pactuados inicialmente, decorrentes da variação do saldo na data da liquidação.
     
42.  **Há algum horário limite para o pagamento da proponente no caso de conquista de um contrato?**  
     Para viabilizar o pagamento no mesmo dia, a instituição credora deve atualizar o status do pedido até às 10h. No exemplo apresentado, como a atualização ocorreu às 23h (fora do horário previsto), o prazo para o pagamento será o dia útil seguinte.
     
43.  **E se o cliente decidir não prosseguir com a portabilidade, mesmo sem receber uma contraproposta? É necessário registrar o aceite do cliente?**  
     Para casos de desistência, a única ação da instituição (credora ou proponente) é registrar o desejo do cliente por meio da mudança de estado para **Cancelled**.
     
44.  **Sobre a simultaneidade: caso o cliente já esteja com um pedido de portabilidade em andamento, a instituição proponente terá acesso ao saldo devedor?**  
     A instituição proponente terá acesso aos dados do contrato, incluindo o saldo devedor. No entanto, não será permitida uma nova solicitação de portabilidade para o mesmo contrato enquanto houver outro pedido em andamento.
     
45.  **Quando o contrato está vinculado a um FIDC, a norma de Portabilidade de Crédito também se aplica?**  
     _Não. A portabilidade no OFB é apenas para CPC (Crédito Pessoal Clean) neste momento._
     
46.  **O cliente precisa cancelar manualmente o pedido de portabilidade após aceitar uma contraproposta da credora?**  
     _Não. A aceitação da contraproposta implica atualização automática do status pelo credor._
     
47.  **A nova proposta deve replicar o número original de parcelas do contrato ou considerar apenas o saldo remanescente?**  
     Deve considerar apenas as parcelas restantes, nunca ultrapassando o contrato original.
     
48.  **A periodicidade da nova proposta pode ser alterada?**  
     Não. Deve ser mantida exatamente como no contrato original.
     
49.  **O que acontece se houver variação no saldo devedor...**  
     Se a variação for superior a 15%, a proponente pode cancelar a portabilidade. A tolerância não se aplica à quantidade de parcelas.
     
50.  **Será possível realizar “troca de modalidade” nos pedidos de portabilidade?**  
     Não. Apenas CPC para CPC.
     
51.  **Haverá cobrança por parte do OFB sobre os pedidos de portabilidade?**  
     A adesão ao OFB é gratuita. Outras taxas estão em análise.
     
52.  **O prazo de 3 dias úteis para a etapa de contraproposta se aplica a todos os produtos...?**  
     Inicialmente apenas para CPC, mas deve ser aplicado ao Consignado Federal.
     
53.  **O fluxo do Open Finance será integrado ao da Núclea?**  
     Não. Os fluxos são independentes. A Núclea será informada apenas para visibilidade institucional.
     
54.  **Está circulando um cronograma do Open Finance 2025–2026 que apresenta datas diferentes para testes e go live. Essas datas estão corretas?**  
     _Sim, refletem as datas do escopo inicial do projeto._
     

Guia de UX1800

55.  **Em relação à área de gestão de contratos, onde o cliente pode consultar status e valores: a credora também precisa disponibilizar essa visualização?**  
     _Sim. A credora deverá exibir comparativo entre contrato original, proposta e contraproposta._
     
56.  **Existe uma jornada de retenção válida mesmo sem oferta de melhores condições para o cliente?**  
     _Sim. Direciona para a jornada de cancelamento por desistência._
     
57.  **As recomendações de cancelamento pelo usuário nos canais da credora, bem como o envio de notificações descritas no guia de UX, são obrigatórias? E como será feita a homologação dessas experiências?**  
     Sim, algumas são obrigatórias conforme escopo regulatório. O cancelamento deve estar disponível nos canais da credora e da proponente. A homologação de UX será comunicada posteriormente.
     
58.  **O guia de UX define como deve ser a tela ou apenas o conteúdo apresentado?**  
     Define apenas as informações obrigatórias, não o design.
     
59.  **Em relação ao guia de UX: a última atualização incluiu como requisito que a instituição proponente e a instituição credora notifiquem o cliente a cada mudança de status do pedido de portabilidade. Isso não pode impactar negativamente a experiência do cliente?**  
     Cada instituição é responsável pelas notificações relativas às suas próprias ofertas.
     
60.  **O cancelamento da portabilidade pelo cliente no aplicativo da credora é obrigatório?**  
     Sim, é obrigatório.
     
61.  **Existe uma jornada de retenção válida mesmo sem oferta de melhores condições...?**  
     Sim. Está previsto no guia como possibilidade válida.
     
62.  **Ainda sobre a jornada de retenção: será considerada válida uma contraproposta com refinanciamento?**  
     Não. O escopo atual contempla apenas portabilidade de crédito.
     
63.  **O cliente precisa cancelar manualmente o pedido após aceitar uma contraproposta...?**  
     Não. A aceitação e o cancelamento são eventos distintos. O sistema atualiza automaticamente.
     
64.  **As recomendações de cancelamento pelo usuário nos canais da credora, bem como o envio de notificações descritas no guia de UX, são obrigatórias...?**  
     Sim. Cancelamento deve estar disponível nos canais digitais da proponente e credora. Algumas notificações são obrigatórias. O formato é flexível, mas conteúdo é obrigatório.
     
65.  **A definição sobre quais informações devem estar visíveis na tela principal ou em detalhes também é livre?**  
     Não. A nova versão do guia trará definição obrigatória para garantir consistência.
