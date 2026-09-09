# Informações Gerais - [DA] Contas - v1.0.0

17

## **Contexto sobre a API**

A API Contas foi derivada da API Produtos e Serviços, esta especificação inclui todos os artefatos relevantes para a Especificação de API sobre contas de depósito à vista, poupança e de pagamento pré-paga pessoa natural e pessoa jurídica de dados abertos.

### **Conta de Depósito à Vista (Current Account)**

Conhecida popularmente pelo nome de conta corrente. É a maneira mais comum de manter dinheiro em uma instituição financeira. Funciona como um cofre, em que o cliente deposita seu dinheiro e pode ter acesso a serviços como pagamento de contas, saques, transferências, emissão de cheques e realização de compras com cartão de débito, entre outros. Para guardar o dinheiro e oferecer serviços como os citados, a instituição financeira pode cobrar tarifas, mas o cliente é quem escolhe se prefere pagar uma tarifa individualizada por serviço que utilizar ou uma tarifa única que dá direito a um pacote de serviços.

### **Conta de Poupança (Savings Account)**

A conta de depósitos de poupança, popularmente conhecida como conta poupança, conta de poupança ou ainda caderneta de poupança, é um tipo de investimento criado com o objetivo de estimular a economia popular. Assim, para abrir e manter uma conta de poupança, o cliente não paga tarifas, não paga imposto de renda sobre o dinheiro aplicado e ainda pode depositar pequenos valores, que passam a gerar rendimentos mensalmente. Se um valor depositado na conta de poupança não for mantido aplicado por pelo menos um mês, isto é, se for resgatado antes, não ocorrerá remuneração desse dinheiro.

### **Conta de Pagamento Pré-paga (Prepaid Payment Account)**

Destinada à execução de transações de pagamento em moeda eletrônica realizadas com base em fundos denominados em reais previamente aportados.

## Prefixo

\- Prefixo dos endpoints: /opendata-accounts/v1

## **Lista de Endpoints**

\- Contas pessoa Jurídica: GET /business-accounts

\- Contas Pessoa Natural: GET /personal-accounts

## **Visão de alto nível**

![accounts-DA.png](images/accounts-DA.png)

## **Dicionário de dados**

[Fazer download do dicionário de dados pessoa natural](data/references/openapi/dictionary-getPersonalAccounts_v1.md)

[Fazer download do dicionário de dados pessoa jurídica](data/references/openapi/dictionary-getBusinessAccounts_v1.md)
