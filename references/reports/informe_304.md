# [Open Finance] Informa #304

Atualização sobre instabilidade da autoridade certificadora Serasa    Como complemento ao Informa #299 ("Importante: Instabilidade da autoridade certificadora Serasa", enviado em 12/01/2023), a Serasa informa que o problema de instabilidade está resolvido. |

 Esclarecimento sobre o valor do identificador de transação (txid) para o QRCode dinâmico    Esclarecemos que **o valor do identificador de transação (txid) deve ser obtido através do JSON**, ou seja, através da URL contida no QRCode Dinâmico, e não pelo QRCode Dinâmico.     Este direcionamento está de acordo com a especificação do Open Finance para a API de Pagamentos v2.0.0 e com o Manual de Padrões do Pix, que em seu item 1.6.2 cita que *“os campos Valor e Identificador da Transação (txid) não devem ser preenchidos no QR Code Dinâmico. Se preenchidos, seu conteúdo deve ser ignorado, prevalecendo sempre os campos obtidos através da URL (payload JSON)”.* |

 Fase 3 – Atualização da lista de problemas conhecidos  O Grupo Técnico de Especificações Serviços comunica que foi adicionado um item à lista de problemas conhecidos da fase 3, conforme segue:   - **BCLOG-F03-V02-004**   - **API/Sessão:** API Payments   - **Endpoint:** PATCH/pix/payments/{paymentId}   - **Campos:** code, title e detail   - **Qual o problema:** O *Swagger* orienta a utilização dos códigos de erro para o *endpoint* de criação de iniciação de pagamento quando deveria ser orientada a utilização de código de erro relativo ao *endpoint* de cancelamento   - **Como deveria ser:**     - **code**: PAGAMENTO\_NAO\_PERMITE\_CANCELAMENTO     - **title**: Pagamento não permite cancelamento     - **detail**: Pagamento não permite cancelamento   - **Orientação:** Utilizar os campos conforme abaixo:     - **code**: PAGAMENTO\_NAO\_PERMITE\_CANCELAMENTO     - **title**: Pagamento não permite cancelamento     - **detail**: Pagamento não permite cancelamento |

 Nova Categoria da Plataforma de Coleta de Métricas (PCM)    Informamos que, no dia 24/01/2023, serão disponibilizadas as novas categorias referentes à **Plataforma de Coleta de Métricas (PCM)** no ambiente de Produção do Service Desk.    As categorias deverão ser utilizadas para a abertura de tickets relacionados à dúvidas, solicitações de melhorias e incidentes pertinentes à PCM. São elas: |

 Estrutura no catálogo de serviços: |

 Os esclarecimentos de dúvidas referentes às novas categorias serão realizados através da abertura de chamados na plataforma do Service Desk. |

 Service Desk - Remoção da categoria “Plataforma de Ressarcimento” Com objetivo de simplificar o processo de abertura de tickets, as categorias referentes à **Plataforma de Ressarcimento** serão removidas do catálogo de serviços para abertura de novos tickets. |

 Estrutura a ser removida no catálogo de serviços: |

 Informamos que o histórico de tickets dessa categoria será mantido.     Os esclarecimentos de dúvidas referentes a esta remoção serão realizados através da abertura de chamados na plataforma do Service Desk. |
