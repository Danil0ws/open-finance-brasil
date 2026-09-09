# Informações Gerais - API Admin - v2.0.1

### Contexto

APIs de Status, de _Outages_ e Métricas são comuns e obrigatórias a todas as instituições participantes do Open Finance Brasil, independentemente da fase de adesão.

Relatórios e Métricas

Situação do Ambiente

Deve dar acesso a dados sobre a disponibilidade atual das implementações, bem como dados sobre indisponibilidades programada.

Métricas

Deve dar acesso a dados de performance de todas as APIs disponibilizadas.

Sendo assim:

1.  Todas as instituições devem publicar essas APIs que monitoram a situação do ambiente;
    
2.  API de métricas deve reportar os dados de performance de **todas as APIs** que a instituição oferece;
    
3.  API de métricas deve ser atualizada conforme lançamento de novas APIs pela instituição ou atualização das APIs já existentes.
    

**Métricas**: (GET /admin/v2/metrics)

### Visão geral

Os dados das APIs Administrativas são consumidos apenas pela Estrutura de Governança do Open Finance para avaliação e controle da qualidade dos serviços fornecidos pelas instituições participantes.

-   Para o entendimento a respeito do cálculo do upTime e DownTime sugere o link de Disponibilidade;
    
-   Para preenchimento do objeto invocativos sugere o link de Referência.
    

### Listas de IPs liberados para acesso a API Admin​

Para garantir a segurança cibernética e evitar a potencial exposição de dados, as instituições que desejarem restringir o acesso à API Admin devem liberar o acesso apenas aos endereços de IP especificados na tabela abaixo:

**Diretório**

**Conformance Suite**

**Monitoramento Sintético**

54.184.72.46

52.42.104.2

18.229.115.248

44.236.37.249

18.229.193.105

44.225.153.192

18.229.12.101

18.229.190.79

52.67.100.177

52.67.104.190

52.67.173.76

54.233.174.43

Essa medida visa proteger contra possíveis ataques e também evitar o uso indevido de recursos e a transmissão de dados. As instituições que optarem por não implementar essas restrições de acesso devem estar cientes das implicações associadas.

### Visão de alto nível das estruturas de dados

![image-20231214-132200.png](images/image-20231214-132200.png)

### Dicionário de Dados

[Fazer download do dicionário de dados](data/references/openapi/dictionary-getMetrics_v2.md)
