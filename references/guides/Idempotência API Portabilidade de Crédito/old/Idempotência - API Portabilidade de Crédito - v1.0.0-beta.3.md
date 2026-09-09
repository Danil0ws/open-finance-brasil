# Idempotência - API Portabilidade de Crédito - v1.0.0-beta.3

-   APIs que implementam o conceito de idempotência oferecem maior confiabilidade ao processo e mitigam problemas de inconsistência de informações ou duplicidade de registros. No entanto, aumentam a complexidade da implementação, tornando essencial sua consideração desde a etapa de arquitetura e design do sistema até a codificação.
    
-   Na portabilidade de crédito, existem dois fluxos distintos: a solicitação via Open Finance Brasil (OFB) e via Registradora. Conforme especificado no PRD, o processo de portabilidade ocorre por meio de fluxos assíncronos, com espaçamentos de dias úteis. Isso permite que a Instituição Credora identifique solicitações duplicadas e mantenha o registro mais antigo, alinhado ao escopo regulatório e à gestão de simultaneidade.
