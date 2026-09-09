# Fluxo de ticket - Testes de longa duração

Como os testes de longa duração exigem validações em dias subsequentes à primeira execução bem-sucedida, como a confirmação da liquidação, o sucesso na etapa inicial não significa que o teste tenha sido concluído com sucesso. Os tickets de notificação relacionados a esses testes somente serão encerrados após a conclusão bem-sucedida de todas as etapas subsequentes do fluxo.

Dessa forma, mesmo nos casos de reexecução em que a primeira etapa do teste seja concluída com sucesso, será necessário aguardar o resultado da última etapa do teste de longa duração antes de considerar a pendência resolvida. Até que haja resultado da execução subsequente, o SLA do ticket permanecerá pausado. Em caso de sucesso, o ticket será encerrado; em caso de falha, novas evidências serão adicionadas ao ticket e o SLA será retomado.

Nos ciclos da FVP Manual - Testes Restritos, testes de longa duração pode ser solicitados. Se identificada falha na execução durante o ciclo vigente, um ticket com as evidências é direcionado à instituição via Service Desk. Para encerrá-lo, uma reexecução com sucesso deve ser obtida exclusivamente pelo fornecedor. O detalhamento do tratamento de falhas dos tickets pode ser encontrado na página Reexecução e contestação.  
  
Há dois cenários onde a Instituição poderá receber uma notificação via Service Desk nos testes de longa duração.

**Cenário 1:**

A instituição falhou no primeiro módulo de um teste de longa duração, o fornecedor realizará o armazenamento das evidências em formato de zip e a associação realizará a criação de um ticket encaminhando para a instituição analisar e realizar a correção do cenário de erro apontado, como mostra a imagem a seguir.

![att\_0\_for\_2065040259.png](images/att_0_for_2065040259.png)

**Cenário 2:**

A instituição falhou na etapa subsequente do teste, ou seja, o erro ocorreu no modulo 2 ou 3 do teste de longa duração, a criação de um novo ticket é realizada automaticamente pela própria ferramenta de testes, a evidência é disponibilizada através de um link na descrição do ticket, como mostra a imagem a seguir.

![att\_1\_for\_2065040259.png](images/att_1_for_2065040259.png)

Os resultados das reexecuções realizadas nas etapas agendadas aparecem em nota no ticket principal, junto ao link com a evidência do resultado do teste.

-   Em caso de falha: a automação encaminha o ticket para a instituição corrigir o cenário.
    
-   Em caso de sucesso: o ticket é encerrado automaticamente pela ferramenta.  
    

![att\_2\_for\_2065040259.png](images/att_2_for_2065040259.png)

## **Plataforma de agendamento (Scheduler)**

É possivel encontrar as informações sobre as etapas subsequentes dos testes de longa duração na **Plataforma de Agendamento**. Para acessá-la, utilize o link disponibilizado ao final dos logs — que aparece quando as etapas anteriores ao módulo final são concluídas com sucesso.

![att\_3\_for\_2065040259.png](images/att_3_for_2065040259.png)

Na ferramenta é possível encontrar informações de agendamentos dos testes e seus resultados.

![att\_4\_for\_2065040259.png](images/att_4_for_2065040259.png)

Para informações sobre as etapas subsequentes dos testes de longa duração, consulte a documentação da **Plataforma de Agendamento (Scheduler)** disponível no Planos de execução agendada - Longa Duração.

Se houve a exclusão inadvertida de **clients vinculados aos Software Statements**, o client correspondente também deverá ser excluído na ferramenta FVP. Para mais informações, consulte a página Deleção de Client.
