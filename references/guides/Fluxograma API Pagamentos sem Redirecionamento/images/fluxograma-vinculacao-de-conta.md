# fluxograma-vinculacao-de-conta

![fluxograma-vinculacao-de-conta](fluxograma-vinculacao-de-conta.png)

## Texto Extraído

Seleciona a detentora de conta

Solicita criagao do vinculo de conta

Confirma armazenamento
e aguardam autorizagao para ;
vinculo para uso

criagao do vinculo de conta (Enrollmentld<>Usuario<>ITP)
€ ' em estado inicial

AWAITING_AUTHORISATION

Armazena informagées do

Redireciona para ambiente da detentora

Beene ee

prcrcrc rcs tess s sss cece ses n newer cece ns aaa proctor sce s sss sss c ese s enero e cece sens >
Solicita os dados da conta do usuario para autorizagao do vinculo de conta
(Autenticagao no ambiente da detentora e Tela de autorizagao)

Confirma o vinculo de conta

' Armazena a conta
selecionada pelo usuario
mudando para estado
AWAITING_CREDENTIALS

Redireciona para ambiente do ITP

Solicita as opgdes de registro FIDO2

Envia as opcodes de Registro FIDO2
(fidoChallange)

Requisita ao dispositivo a criagao da
credencial FIDO2 1

Requisita gesto do usuario para
aprovacgao

Realiza o gesto de autenticagao
(ex.: biometria, PIN)

Cria Credencial FIDO2

Retorna a chave publica FIDO2

Envia a credencial publica

Valida e armazena

credencial
Retorna mensagem de sucesso da

operagao alterando estado para
AUTHORISED

Informa ao usuario que a criagao do vinculo foi bem-sucedida

---
**Arquivo original:** `fluxograma-vinculacao-de-conta.png`
**Tamanho:** 930.56 KB