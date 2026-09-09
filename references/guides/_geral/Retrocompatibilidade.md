# Retrocompatibilidade

As informações contidas nessa sessão visam garantir que os participantes (Iniciadora / Detentora / Transmissora / Receptora) do ecossistema consigam compreender como funciona a retrocompatibilidade no contexto do Open Finance Brasil e quais são os aspectos que uma API pode sofrer visando impactos e tratativas.

Nos itens abaixo, é possível identificar quais são os cenários de compatibilidade e tipos de mudança que podem ocorrer no ecossistema:

-   **Análise de cenários:** Identificar quem realizou a chamada no processo de consumo da API (Iniciadora / Detetora / Transmissora / Receptora)
    
    -   _Backward Compatibility_ - Compatibilidade com versões anteriores;
        
    -   _Forward Compatibility_ - Compatibilidade com versões posteriores;
        
    -   _Business Compatibility_ \- Compatibilidade com regras de negócio em versões posteriores;
        
-   **Tipos de mudança:** Identificar qual o tipo de mudança na API (Categoria)
    
    -   _Non Breaking Change_ (NBC): Alterações que não realizaram a “quebra” de contrato, ou seja, mudanças que são compatíveis com versões anteriores e não exigem ajustes na implementação para que funcionalidades existentes continuem funcionando;
        
    -   _Technical Breaking Change_ (TBC): Alterações que possuem o potencial de “quebrar” o contrato, ou seja, mudanças que são incompatíveis com versões anteriores e exigem ajustes na implementação para que as funcionalidades existentes continuem funcionando;
        
    -   _Business Breaking Change_ (BBC): Alterações que não necessariamente estão quebrando o contrato do ponto de vista técnico. Mudanças de negócios que são incompatíveis com versões anteriores.
