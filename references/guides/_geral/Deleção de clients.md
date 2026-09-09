# Deleção de clients

A deleção de client deverá ser tratada como solicitação específica, com controle de impacto, rastreabilidade e vínculo explícito ao ticket originador do teste afetado.

Caso a instituição tenha excluído acidentalmente os clients atrelados aos Software Statements de longa duração, será necessário excluir o mesmo client também na ferramenta FVP, sob pena de o teste não poder ser concluído com sucesso.

Os clients utilizados nesse contexto são criados a partir dos seguintes Software Statements:

-   **44ffd907-2318-496b-ad91-07bbb0a836da.**
    
-   **25402dd0-7553-477b-b635-b9ce79da18f2.**
    

Para tratamento, a instituição deverá abrir ticket no Service Desk na categoria:  
**Requisição > Reexecução > Deleção de Client**

O ticket deverá informar obrigatoriamente o ticket vinculado ao teste afetado. O ticket original permanecerá com o SLA pausado e com o status “AGUARDANDO REEXECUÇÃO/CONTESTAÇÃO” até a conclusão da análise.

  
Formulário Deleção de Client.

![att\_0\_for\_2065171244.png](images/att_0_for_2065171244.png)

Caso a deleção seja considerada procedente, a exclusão será concluída em até 5 dias úteis.

Após a conclusão da deleção procedente, poderá ser solicitado internamente um novo ticket de reexecução, com direcionamento ao fornecedor em nome da instituição.

![att\_1\_for\_2065171244.png](images/att_1_for_2065171244.png)

Qualquer cenário que não corresponda à exclusão de client deverá ser tratado pela equipe técnica, com avaliação do caso e eventual deliberação de abertura de ticket de reexecução ao fornecedor.

Antes da abertura do chamado, a instituição deverá validar previamente se o client está efetivamente sem uso, avaliar impacto em testes em andamento e registrar a justificativa da solicitação.

## **Cuidados obrigatórios**

-   **Validar previamente se o client está sem uso:** confirme que não há execuções, integrações ou testes ativos utilizando o client antes de prosseguir com a solicitação.
    
-   **Avaliar o impacto em testes em andamento:** análise possíveis impactos em cenários de teste ativos para evitar interrupções ou resultados inconsistentes.
    
-   **Registrar a justificativa da solicitação:** documente claramente o motivo da ação, garantindo transparência e rastreabilidade do processo.
    
-   **Referenciar corretamente o ticket associado:** utilize o número do ticket correspondente para preservar o histórico e facilitar futuras consultas.
    
-   **Garantir a comunicação com as partes envolvidas:** informe as equipes impactadas sobre a solicitação e possíveis efeitos da alteração, evitando conflitos operacionais e retrabalho.
    

## **Suporte e Dúvidas Adicionais**

Caso a instituição tenha dúvidas ou apontamentos de irregularidades, aconselhamos que realizem a abertura de um ticket de Solicitação de Informações via Service Desk: Solicitação de Serviço → Solicitação de Informações → Conformidade → Ferramenta de Validação em Produção (FVP).
