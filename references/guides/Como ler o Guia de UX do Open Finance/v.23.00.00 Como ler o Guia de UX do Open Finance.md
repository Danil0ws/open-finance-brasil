# v.23.00.00 Como ler o Guia de UX do Open Finance

# Navegação orientada por produtos e jornadas

O Guia de UX vem sendo aprimorado para tornar a consulta mais intuitiva e apoiar o desenho, a implementação e a validação das jornadas.

A estrutura atual organiza o conteúdo por **Família de Produtos**, **Produtos**, **Jornadas** e **Variações de Jornada**, refletindo a forma como as experiências são construídas e consultadas no ecossistema.

Com essa estruturação, as jornadas podem ser percorridas de forma contínua, reduzindo a necessidade de navegar entre diferentes páginas para compreender o fluxo completo. Isso proporciona uma visão mais integrada da experiência e facilita a localização dos requisitos, recomendações e cenários associados a cada etapa.

* * *

# Notação do identificador único de requisitos e recomendações

A partir da versão 22.00.02, cada requisito e recomendação passa a possuir um identificador único e permanente. Os identificadores são mantidos entre as versões do Guia, permitindo rastrear alterações, referenciar itens específicos e acompanhar sua evolução ao longo do tempo.

A notação é composta por três elementos:

-   **Prefixo do tipo de item**: indica se o item é um requisito ou uma recomendação.
    
-   **Sigla da família de produto**: identifica a família à qual o item pertence.
    
-   **Número sequencial único**: identifica o requisito ou recomendação dentro da família de produto.
    

Exemplo:

`REQ.DC-0001`

Onde:

-   **REQ**: requisito
    
-   **DC**: família de produto Dados do Cliente
    
-   **0001**: identificador sequencial único do item.
    

Os identificadores são utilizados como referência permanente no Guia de UX e não são renumerados em novas publicações. Dessa forma, instituições e implementadores podem manter referências consistentes aos requisitos e recomendações, independentemente da evolução do conteúdo ao longo do tempo.

## Sobre a numeração dos indicadores

**Atenção!**

Os identificadores são permanentes e existem para fins de rastreabilidade. Para consulta e implementação, siga a sequência apresentada na jornada.

Os identificadores foram criados para garantir rastreabilidade e referência permanente dos requisitos e recomendações. Por esse motivo, a numeração não deve ser interpretada como uma indicação da ordem de apresentação dos itens em uma jornada.

Como um mesmo requisito ou recomendação pode ser reutilizado em diferentes jornadas, etapas ou cenários, a sequência numérica dos identificadores nem sempre acompanha a ordem em que os itens são apresentados no Guia.

Assim, é possível encontrar um requisito com identificador posterior sendo apresentado antes de outro com identificador anterior. Essa situação é esperada e não representa um erro de edição ou ordenação, mas uma consequência da reutilização de conteúdo e da manutenção de identificadores permanentes.

Durante a consulta ao Guia, deve-se considerar a sequência lógica da jornada e a ordem de apresentação dos requisitos e recomendações, e não a ordem numérica dos identificadores.

* * *

# Organização da página das jornadas

Em cada página, os conteúdos estão organizados por instituição, reunindo em blocos específicos todos os cenários aplicáveis a cada participante. Essa estrutura aprimora trechos em que conteúdos de diferentes instituições apareciam em uma única lista, dificultando a consulta e a identificação das informações relevantes.

Dessa forma, é possível localizar com mais facilidade os conteúdos de cada etapa, compreender rapidamente o que se aplica a cada instituição e navegar de forma mais direta pelos tópicos relacionados. Torna-se mais fácil a comparação entre instituições e a identificação de requisitos e recomendações em jornadas mais extensas.

A estrutura aparece da seguinte maneira:

## Etapa 1: Nome da etapa (Jornada)

#F4F5F7

### **Requisitos - Abreviação da instituição (Ex.: ITP)**

**Cenário: Momento específico da etapa**

-   `REQ.XX-00000` Requisito a ser seguido pela ITP.
    
    Ex.:  
    `REQ.DC-06300` Se apresentar Termos e Condições, informar que, ao continuar, o usuário está concordando com esses termos.
    
-   `REQ.XX-00000` Requisito que representa a proibição de algo e deve ser seguido pela ITP.
    
    Ex.:  
    `REQ.DC-06400` Se apresentar Termos e Condições, não utilizar _opt-in_.
    

#F4F5F7

### **Recomendações - Abreviação da instituição (Ex.: ITP)**

**Cenário: Momento específico da etapa**

-   `REC.XX-0000` Recomendação sugerida para a ITP.
    
    Ex.:  
    `REC.DC-01900` Quando aplicável, informar sobre a gratuidade da operação de forma clara e sem fricções que atrapalhem a jornada.
    

* * *

# Caixas de aviso

Por fim, as caixas de **Nota** e **Atenção** são utilizadas para complementar o conteúdo principal, destacando detalhes adicionais e pontos críticos que auxiliam na interpretação correta e na aplicação das orientações apresentadas.

**Nota**

As notas possuem caráter informativo.

**Atenção!**

As informações possuem caráter de alerta e, se não observadas, podem comprometer o entendimento do conteúdo do Guia.
