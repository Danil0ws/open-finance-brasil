# AdesaoPixAutomatico-20231016-211347

![AdesaoPixAutomatico-20231016-211347](AdesaoPixAutomatico-20231016-211347.png)

## Texto Extraído

Usuario Pagador

Iniciador

PSP Pagador (Detentor)

PSP Recebedor

| Ambiente cliente
PSP Recebedor

2. Seleciona o
pix automatico
como método

de pagamento
1. Acessa Pee

ambiente do
Recebedor

6. Valida os
dados inseridos

5. Recebe os
dados inseridos
pelo Pagador

7. Solicita
access_token
para Detentor

8. Recebe
solicitagao de
token

9. Processa
solicitagao de
access_token

inseridos sao
enviados ao
Iniciador
3. Informa os
dados de
pagamento

12. Criao
consentimento
(POST
/recurring-
consents)

—
* Ambiente do PSP
| Pagador

20. Realiza a
autenticagao

19. Redireciona o
Pagador para
autententicacao
no Detentor

18. Processa
retorno da
criagao do

consentimento

21. Autoriza o
consentimento

Aprovacao em
multiplas
alcadas ?

24. Redireciona o
usuario para
aplicacao do

25. Recebe
informagdes do
redirecionamento

26. Valida
informagées
recebidas

17. Recebe

11. Recebe o
token enviado
pelo Detentor

10. Envia token
para o Iniciador

13. Envia
solicitagao de
consentimento

para o Detentor

14. Recebe a
solicitagao de
consentimento

resposta da
criagao e URL de
redirecionamento

16. Retorna ao
Iniciador sucesso
na criagao do
consentimento

15. Processa
solicitagao de
consentimento

recorrente

recorrente

Loop até que o
consentimento
esteja em

AUTHORISED

27. Consulta
status
consentimento

31. Recebe a
notificagao de
sucesso

22. Muda
consentimento para
status AUTHORISED

23. Notifica os demais
aprovadores solicitando a
aprovacgao

30. Notifica o
Pagador do
sucesso na

Adesao

28. Notifica o
Recebedor do
sucesso na
adesao

29. Recebe
notificagao do
sucesso da
Adesao

---
**Arquivo original:** `AdesaoPixAutomatico-20231016-211347.png`
**Tamanho:** 1274.42 KB