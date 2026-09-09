# FAPI-BR v2.2.1 - Open Finance Brasil Financial-grade API Security Profile

true

## Change log

## **Versão 2.2.1**

**#**

**Sessão do Documento**

**Alteração**

**Tipo**

**Motivador**

1

8.1. Servidor de autorização — Nota de clarificação

Nota para esclarecer o comportamento esperado em renovações por `grant_type=refresh_token` com subconjunto de escopos, quando associadas a consentimento(s) válido(s).

Patch

Padronizar a interpretação entre Authorization Servers e garantir interoperabilidade em cenários de renovação de tokens com escopos parciais.

## **Versão 2.2.0**

**#**

**Sessão do Documento**

**Alteração**

**Tipo**

**Motivador**

1

5.1. Servidor de Autorização — Item 23

Definição do ponto de consumo do request\_uri e revisão do tempo mínimo de validade.

Minor

Evitar invalidação indevida do request\_uri por pré‑carregamento ou chamadas duplicadas.

2

5.1. Servidor de Autorização — Nota 1

Esclarecimento do âmbito de APIs de recursos protegidos.

Patch

Melhorar precisão da documentação.

3

5.2. Cliente confidencial — Item 9

Revisão de redação para clarificar o significado.

Patch

Aumentar clareza e evitar ambiguidade.

## **Versão 2.1.0**

**#**

**Sessão do Documento**

**Alteração**

**Tipo**

**Motivador**

1

Todo o documento

Reestruturação, reescrita e correções de typos do documento para maior clareza, sem alterações de requisitos existentes.

Patch

Melhoria das documentações de segurança

2

8.1. Servidor de autorização

Inclusão de clarificações referentes ao gerenciamento de tokens para o caso de consentimentos criados em Jornadas Otimizadas

Minor

Nova funcionalidade de Jornada Otimizada
