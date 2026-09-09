# FluxoRetentativasPixAutomatico-20250115-011248

![FluxoRetentativasPixAutomatico-20250115-011248](FluxoRetentativasPixAutomatico-20250115-011248.png)

## Texto Extraído

Empresa Recebedora

Iniciador

PSP Pagador (Detentor)

Usuario Pagador

1. Identifica a
falha no
recebimento do

_ pagamento
Inicio

Deve informar a ID do
pagamento que falhou

4. Prepara
payload de
nova tentativa
de
agendamento

7. Recebe pedido
de pagamento

8. Valida as
informagées
recebidas

2. Notifica o
Iniciador para
nova tentativa

3. Recebe pedido
de nova tentativa
de liquidagao

6. Envia
soliciatagao de

agamento
5. Cria nova pag

solicitagao de
pagamento
agendado

18. Recebe o
sucesso na
criagao do novo
pagamento

17. Envia
resposta de
sucesso na
criagao do
pagamento
10. Data do
pagamento é a
mesma data de
liquidagao do
originalRecurrin
gPaymentld
informado?
9. Processa o
pedido de
agendamento
de pagamento

19. Processa o
retorno da
solicitagao

11. Valida
regras de
novas
tentativas
intradia

12. Valida
regras de
novas
tentativas
extradia

Loop até que o
pagamento
esteja em
SCHD ou RJCT

Pagamento em
20. Consulta SCHD?
estado da
pagamento

13. Registra o
novo
pagamento
agendado

22. Recebe
notificagao de
confirmagao do
agendamento

21. Envia
notificagao de
sucesso

14. Notifica o
pagador de um
novo débito
agendado

24. Recebe
notificagao de
falha do
agendamento

----»®&

23. Envia
notificagao de
falha

15. Envia
notificagao de
novo débito
agendado

16. Recebe
notificagao de
novo débito
agendado

---
**Arquivo original:** `FluxoRetentativasPixAutomatico-20250115-011248.png`
**Tamanho:** 1073.25 KB