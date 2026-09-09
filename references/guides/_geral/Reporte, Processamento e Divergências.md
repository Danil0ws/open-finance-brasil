# Reporte, Processamento e Divergências

# Reporte

A Plataforma de Coleta de Métricas tem por objetivo coletar informações sobre as solicitações que foram feitas entre as instituições. Quando uma chamada é feita entre duas instituições, ambas precisam enviar para a Plataforma de Coleta de Métricas o dado sobre essa solicitação. Esse dado que é enviado pelas instituições é chamado de **Reporte**.

# Processamento

Quando um _Reporte_ é recebido, a plataforma busca a contraparte, ou seja, o _reporte_ enviado pela instituição que fez par com a solicitação original. Caso a encontre, os dois registros já são marcados com o status que os define como conciliados. Esse processo é feito em tempo real conforme os registros são adicionados à plataforma. O módulo de **Processamento** é responsável por fazer a conciliação em tempo real descrita acima, a conciliação no momento do fechamento e o ajuste de divergências.

# Fechamento

O Fechamento é procedimento de contabilização das chamadas enviadas pelos participantes com o objetivo de encontrar inconsistências. Ela contabiliza um período pré especificado. Ao encontrar inconsistências, esse procedimento abre _Divergências_ a serem ajustadas pelas instituições.

# Divergência

Uma divergência é aberta quando um determinado _reporte_ não encontra uma correspondência entre os reportes enviados pela instituição com quem a chamada foi feita. Considere hipotéticas instituições A e B. Quando A faz uma solicitação para B, ambas precisam enviar para a Plataforma de Coleta de Métricas os dados sobre essa solicitação. Caso uma delas não envie, ou envie com dados errados, é gerada uma **Divergência**.

Divergências também podem ser geradas por inconsistências absolutas ou lógicas entre os reportes, tais como dados que deveriam ser iguais e diferem no momento da conciliação (absolutas) ou parâmetros que carecem de sentido quanto combinados (lógicos).

note

**Exemplos de inconsistências**

-   **Inconsistência absoluta**: instituição "A" reporta que obteve um código HTTP 200, enquanto a instituição "B" reporta um código HTTP 201.
    
-   **Inconsistência lógica**: Instituição "B" no pepel de server reporta um timestamp de requisição com timestamp inferior ao timestamp reportado pela instituição "A" no papel de client (um response não pode ser acontecido antes de um request).
    

**Exemplos de inconsistências**

-   **Inconsistência absoluta**: instituição "A" reporta que obteve um código HTTP 200, enquanto a instituição "B" reporta um código HTTP 201.
    
-   **Inconsistência lógica**: Instituição "B" no pepel de server reporta um timestamp de requisição com timestamp inferior ao timestamp reportado pela instituição "A" no papel de client (um response não pode ser acontecido antes de um request).
    

As próximas seções descrevem em detalhe cada um desses componentes.

* * *

Próximo: Reporte
