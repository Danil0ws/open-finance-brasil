# Fluxo de tickets

## **Abertura de tickets**

Após a execução da FVP Automática, caso a instituição falhe em algum dos testes, a rotina abrirá um ticket.

-   **"Teste Automático DCR - CustomerFriendlyName":** aberto se o servidor falhar em pelo menos um teste relacionado ao DCR ou testes funcionais.
    
-   **"Teste Automático Cadastro Diretório - CustomerFriendlyName":** aberto se o servidor falhar em pelo menos um teste de validação de cadastro no diretório.
    
-   API’s do Open Finance (Produtos): aberto se o servidor falhar em pelo menos um teste funcional
    

Se o servidor falhar em ambos os tipos, ambos os tickets serão abertos. Dentro do ticket devem constar:

-   Descrição do ticket com módulos que ocasionaram a abertura deste ticket
    
-   Well-Known do servidor testado
    
-   ID do Authorisation Server encontrado no Diretório
    
-   Evidências apontando onde a instituição falhou, com URI para a página de resultados (acesso autenticado via credenciais do Diretório).
    

![att\_0\_for\_2064973922.png](images/att_0_for_2064973922.png)

## **Manutenção de tickets**

Caso a instituição continue com falha, as novas falhas serão anexadas ao ticket existente com o link da nova evidência em forma de nota. Se a instituição obtiver sucesso em todos os módulos, o ticket é fechado automaticamente com uma nota de sucesso.

![att\_1\_for\_2064973922.png](images/att_1_for_2064973922.png)

Os testes DCR de produção estão acessíveis no Motor de Conformidade regular, permitindo execução no ambiente de Sandbox para correção de problemas identificados em produção, [Web Conformance Sandbox](https://web.conformance.directory.openbankingbrasil.org.br/). Em caso de dúvidas, a instituição deve abrir um novo ticket no Service Desk de conformidade.

## **Página de resultados**

Após cada execução da FVP Automática são geradas páginas de resultados com os logs das execuções e o detalhamento dos pontos de falha, semelhante ao motor de conformidade.

A URL base é https://results.sandbox.directory.openbankingbrasil.org.br/TestID/index.html, onde TestID é uma sequência aleatória fornecida à instituição após a abertura de um ticket no Service Desk.

Para acessar os resultados é necessário autenticar-se com credenciais do Diretório Open Finance e estar vinculado a uma organização ativa. Não há indexação dos resultados existentes, portanto a instituição deve salvar o URI do teste para consultas futuras.

![att\_2\_for\_2064973922.png](images/att_2_for_2064973922.png)

## **Suporte e Dúvidas Adicionais**

Caso a instituição tenha dúvidas ou apontamentos de irregularidades, aconselhamos que realizem a abertura de um ticket de Solicitação de Informações via Service Desk: Solicitação de Serviço → Solicitação de Informações → Conformidade → Ferramenta de Validação em Produção (FVP).

![att\_0\_for\_2064581488.png](images/att_0_for_2064581488.png)
