# Formação e Estabilidade do ID

Os IDs de recursos devem atender as seguintes regras:​

-   O ID de um recurso deve ser especificado no _endpoint_ de uma API apenas para obter detalhes do recurso ou para realizar alterações no mesmo.
    
-   Se o ID for especificado nos padrões do Open Finance, então ele é obrigatório e deverá ser fornecido pela entidade implementadora da API de acordo com o padrão definido.
    
-   Se um ID for especificado, o mesmo deverá ser totalmente desconectado de significados com outras entidades. Por exemplo, um ID não deve ser uma combinação de outros campos ou uma _string_ que possa ter conteúdo sensível que possa ser extraído.
    
-   Os IDs devem ser únicos, porém sua unicidade pode estar dentro de um contexto. Por exemplo, um ID de conta corrente deve ser único, porém apenas dentro do contexto de conta corrente.​
    
-   Nos _payloads_ o nome de campo "id" nunca deverá ser utilizado. Cada campo ID deverá ter um nome significativo, dessa forma independentemente de onde o ID for utilizado entre múltiplos _endpoints_, ele sempre irá se referir ao seu objeto principal. Por exemplo, IDs para conta deverão ser representados no JSON como "accountId".
    
-   O identificador único deve se manter estável e imutável independente da data de consulta e do consentimento. Podem existir casos de exceção e estes estarão bem documentados no _Swagger_ das APIs.
    

### Princípios para a formação de IDs (identificadores) de recursos nas APIs

-   O ID DEVE ser uma string com limitação de 100 caracteres - limite que poderá ser revisitado em caso de necessidade apresentada por quaisquer dos participantes do Open Finance Brasil e - aderente aos padrões apresentados na seção 2.1 da RFC 2141;
    
-   Uma vez que será trafegado nas chamadas de interface, o ID NÃO DEVE conter dados classificados como PII - Personally identifiable information (Informação Pessoalmente Identificável) ou Informação de Identificação Pessoal;
    
-   DEVE ser garantida a unicidade do ID dentro do contexto da API assim como a estabilidade do mesmo, sendo a estabilidade condicionada à manutenção das características de identificação natural do recurso em questão (por exemplo, as informações de banco, agência e conta na API de Contas). A alteração das características de identificação natural implica na geração de um novo identificador associado ao recurso;
    
-   A utilização de meios técnicos razoáveis e disponíveis para a formação do ID é de livre implementação por parte da instituição transmissora dos dados, de forma que apenas a aderência aos princípios elencados nesta documentação é mandatória.
