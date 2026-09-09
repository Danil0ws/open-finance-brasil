**REQUISITOS MÍNIMOS**

para a experiência do usuário

versão 7.3


[Acesse aqui a versão 7.4, com vigência a partir de 01/03/2027.](https://www.bcb.gov.br/content/estabilidadefinanceira/pix/Regulamento_Pix/versoes_futuras/IV_RequisitosMinimosparaExperienciadoUsuario-versao7-4.pdf)




Versão: 7.3

Dezembro de 2025


##### **REQUISITOS MÍNIMOS**

para a experiência do usuário


Elaboração, distribuição e informações

Banco Central do Brasil

Setor Bancário Sul (SBS) Quadra 3 Bloco B - Ed. Sede

Brasília – DF, CEP: 70074-900

Site: https://www.bcb.gov.br


Todos os direitos reservados. É permitida a reprodução

parcial ou total desta obra, desde que citada a fonte e

que não seja para venda ou qualquer fim comercial.

Venda proibida. Distribuição gratuita. A responsabilidade

pelos direitos autorais de textos e imagens desta obra é

da área técnica.




9:30








































|Col1|Col2|01<br>Introdução<br>04|02<br>Obrigações e<br>Recomendações<br>Gerais<br>05 - 10|03<br>Pix com chave Pix<br>11 - 17|04<br>Pix com inserção<br>manual dos dados de<br>conta transacional<br>18 - 21|Col7|
|---|---|---|---|---|---|---|
|||01<br>Introdução<br>04|05<br>Geração de QR Code<br>estático<br>22 - 25|06<br>Pagamento através de<br>QR Code estático<br>26 - 31|07<br>32 - 38<br>Pagamento imediato<br>ou com vencimento<br>através de QR Code<br>dinâmico|08<br>39 - 40<br>Extrato|
|09<br>41 - 45<br>Devolução|10<br>46 - 52<br>Minhas Chaves|11<br>53 - 62<br>Meus Limites Pix<br>|12<br>Pix Agendado<br>63 - 69|13<br>Pix Copia e Cola<br>70 - 73<br>|14<br>Pix Saque e Pix Troco<br>74 - 81<br>||
|09<br>41 - 45<br>Devolução|10<br>46 - 52<br>Minhas Chaves|82 - 103<br>15<br>Pix Automático|16<br>104 - 114<br>Autoatendimento MED|17<br>Serviços de iniciação<br>de transação de<br>pagamento no Pix<br>115 - 119|18<br>Integração com Lista<br>de Contatos<br>120 - 121|19<br>Pix em Internet Banking<br>122 - 127|
|20<br>Acessibilidade no Pix<br>128 - 129|Anexo I<br>130 - 137<br>21|Histórico de revisão<br>138 - 163<br>22|||||




Obrigações e Recomendações Gerais

Nesse item são abordadas as obrigações e as recomendações gerais a todos
os casos de uso.

#### Recomendações e OBRIGAÇÕES


Versão: 7.3
Dezembro de 2025
# 02




Obrigatório







































funcionalidade de pagamento ou de transferência.


ambiente Pix nessa tela.


seguintes ações:


após o login;


pagamento.


principais:

 - Velocidade (transação realizada em poucos segundos);

 - Disponibilidade (a qualquer dia e a qualquer hora);

 - Conveniência (experiência simples e prática);


 - Formas de iniciação (chave, QR code).


 - Inserção de chave Pix;

 - Leitura de QR Code;


 - Inserção do Pix Copia e Cola.








































Obrigatório

















podem ser acrescentadas, a critério do participante.


Saque”, “Pix Troco”, “Pix Agendado” e “Pix Automático”.







aquelas que a instituição participante exige para outras formas de pagamento.


transação.





















de análise para ser autorizada e dar a opção de cancelamento da transação.

Exemplos:


Pix?


cancelar a transação?


































Obrigatório

















passar por etapas intermediárias.


no site do Banco Central caso a ocorrência não seja resolvida pelo PSP.






















































































Obrigatório

















informações:


regulamentação vigente;

 - O campo “Descrição” refere-se a “informacoesEntreUsuarios” da pacs.008;


qualquer conteúdo dinâmico.


detalhada quando o usuário clicar na notificação;


período diurno.


PSP. A notificação deve conter, no mínimo, as seguintes informações:


termos da regulamentação vigente;

 - O campo “Identificador” refere-se ao “TxId” da pacs.008;


detalhada quando o usuário clicar na notificação;


Code e, preferencialmente, ser enviada em período diurno.








Obrigatório













ou disponibilizar a opção de salvamento, quando o txId estiver preenchido.











comprovante de agendamento.


compartilhamento (arquivo pdf ou imagem).






























**Pix com Chave Pix**


Trata-se de Pix entre usuários por meio da utilização de chave Pix.


#### Recomendações e OBRIGAÇÕES

Versão: 7.3

Dezembro de 2025
# 03



Versão: 7.3



Dezembro de 2025




Obrigatório






    - CPF/CNPJ, número de telefone celular, e-mail.

























identificação do usuário recebedor.


preenchimento.


“informacoesEntreUsuarios”.


qualquer conteúdo dinâmico.
























Obrigatório



















































comunicado sobre o erro de formato.


problema no formato da chave.

Exemplos:

 - Transação não concluída. Formato da chave inválido;

 - Ocorreu um problema no formato da chave. Tente novamente;

 - Ocorreu um erro. Confira o formato dessa chave;

 - Seu Pix não foi concluído. Verifique o formato da chave informada.


indisponibilidade dessa chave.


inexistente ou está indisponível.

Exemplos:

 - Transação não concluída. Chave indisponível.

 - Chave não localizada. Tente novamente.

 - Ocorreu um erro. Não foi possível encontrar essa chave.

 - Erro. Veja se informou a chave certa.

 - Pix não concluído. Verifique se a chave está correta.


motivo.


concluir a transação.

Exemplos:


possível realizar o Pix.


fundada suspeita de fraude.


















Obrigatório















evidenciar o efetivo motivo do não processamento da transação.


extrapolado.


do próprio PSP.

Exemplos:

 - Tente outro valor, saldo insuficiente.

 - Pix não realizado, o saldo que você possui não foi suficiente.

 - Você está sem saldo para finalizar esse Pix;

 - Transação não concluída. Conta do destinatário indisponível.


 - Erro. Conta do recebedor indisponível;

 - Transação não concluída. Conta do destinatário inexistente.

 - Pix não concluído. A conta da pessoa que você quer transferir não existe.

 - Erro. Conta do recebedor inexistente;


Pix. Tente novamente.

 - Desculpe, tivemos uma falha técnica. Tente de novo.











Recomendado


conta transacional.


























Obrigatório























do PSP. A notificação deve conter, no mínimo, as seguintes informações:

 - Nome do recebedor e valor da transação.


- período estabelecido na regulação em vigor, contendo, no mínimo:

 - Nome, CPF (mascarado ou não)/CNPJ e nome do PSP do usuário pagador;

 - Nome, CPF (mascarado ou não)/CNPJ e nome do PSP do usuário recebedor;

 - Campo “Descrição” (sempre que estiver preenchido);

 - Valor e ID da transação;

 - Data e hora/minuto/segundo (horário de Brasília) da liquidação.


representados na tela ao lado.

 - O ID/transação refere-se ao "EndtoEndID" presente na pacs.008;

 - O campo “Descrição” refere-se a “informacoesEntreUsuarios” da pacs.008;


qualquer conteúdo dinâmico.


















Recomendado


Para as chaves aleatórias, é recomendado:







usada no QR Code;


tentar receber Pix por meio desse “apelido”;


facilitar o seu compartilhamento;


chave.








**Pix com inserção manual dos dados de conta transacional**


Trata-se de Pix entre usuários por meio da inserção manual pelo usuário
pagador dos dados da conta transacional do usuário recebedor.


#### Recomendações e OBRIGAÇÕES

Versão: 7.3

Dezembro de 2025
# 04



Versão: 7.3



Dezembro de 2025




Obrigatório




































 - Campos referentes à conta transacional, CPF/CNPJ, campo “Descrição”.


participantes.


confirmação da transação.

 - Nome, campos referentes à conta transacional, CPF/CNPJ.


pagamento.


equivocadas.


“informacoesEntreUsuarios”.


qualquer conteúdo dinâmico.


deverá ser informado disso antes de confirmar o pagamento.


Exemplos:


crédito [nome da linha de crédito].












Obrigatório















evidenciar o efetivo motivo do não processamento da transação.


extrapolado.


do próprio PSP.

Exemplos:

 - Tente outro valor, saldo insuficiente.

 - Pix não realizado, o saldo que você possui não foi suficiente.

 - Você está sem saldo para finalizar esse Pix.

 - Transação não concluída. Conta do destinatário indisponível.


 - Erro. Conta do recebedor indisponível.

 - Transação não concluída. Conta do destinatário inexistente.

 - Pix não concluído. A conta da pessoa que você quer transferir não existe.

 - Erro. Conta do recebedor inexistente.


Pix. Tente novamente.

 - Desculpe, tivemos uma falha técnica. Tente de novo.





















Recomendado


conta transacional.






































Obrigatório























do PSP. A notificação deve conter, no mínimo, as seguintes informações:

 - Nome do recebedor e valor da transação.


- período estabelecido na regulação em vigor, contendo, no mínimo:

 - Nome, CPF (mascarado ou não)/CNPJ e nome do PSP do usuário pagador;

 - Nome, CPF (mascarado ou não)/CNPJ e nome do PSP do usuário recebedor;

 - Campo “Descrição” (sempre que estiver preenchido),

 - Valor e ID da transação;

 - Data e hora/minuto/segundo (horário de Brasília) da liquidação.


representados na tela ao lado.

 - O ID/transação refere-se ao "EndtoEndID" presente na pacs.008;

 - O campo “Descrição” refere-se a “informacoesEntreUsuarios” da pacs.008;


qualquer conteúdo dinâmico.


















**Geração de QR Code estático**


Trata-se da geração de QR Code estático e do recebimento pelo usuário
recebedor de transação iniciada com esse QR Code.


#### Recomendações e OBRIGAÇÕES

Versão: 7.3

Dezembro de 2025
# 05



Versão: 7.3



Dezembro de 2025




Obrigatório















das quatro chaves:

 - Número de telefone celular, e-mail, CPF/CNPJ ou chave aleatória.
















































Obrigatório

















usuário a condição de não serem de preenchimento obrigatório.

 - Identificador e valor;


recebedor, para fazer a conciliação de seus recebimentos.





Recomendado

















registro de chave Pix.






































|9:30 9:30<br>Receber Receber<br>Saldo: R$ 1.000,00 Saldo: R$ 1.000,00<br>Selecione o tipo de chave ? Selecione o tipo de chave ?<br>Celular CPF E-mail aC leh aa tv óe ri a Celular CPF E-mail aC leh aa tv óe ri a<br>Chave: +55 61 98888-8888 Chave: +55 61 98888-8888<br>Valor (opcional) ? Valor (opcional) ?<br>03<br>R$ 0,00 R$ 0,00<br>Identificador (opcional) ? Identificador (opcional) ?<br>Pequena descrição da transação 03 Pequena descrição da transação<br>0 de 25 caracteres 0 de 25 caracteres<br>Selecione ou cadastre uma chave antes de<br>realizar essa ação.<br>Avançado Continuar<br>Avançado Continuar Entendi<br>Ao tentar continuar sem<br>a seleção de uma<br>9:30 chave, o usuário será 9:30<br>alertado quanto a sua<br>Receber obrigatoriedade. Receber<br>Saldo: R$ 1.000,00 Saldo: R$ 1.000,00<br>Selecione o tipo de chave ? 04 Selecione o tipo de chave ?<br>Celular CPF E-mail aC leh aa tv óe ri a Celular CPF E-mail aC leh aa tv óe ri a<br>Chave: +55 61 98888-8888 Chave: +55 61 98888-8888<br>Valor (opcional) ? Valor (opcional) ?<br>R$ 0,00 R$ 0,00<br>Identificador (opcional) ? Identificador (opcional) ?<br>Pequena descrição da transação Pequena descrição da transação<br>0 de 25 caracteres 0 de 25 caracteres<br>Dúvida: Os campos Identificador e Valor são<br>o pp rc ei eo nvn coa hcis iê m p n ea ã nr oa to ec dsri p oa e ç ccã aio f mi qd puo oe Q so eR v r áC a lo fo ed r i,e t oo. C pa es loo 03 pO r eu ss su iá or nio a rs oe r íá c on no eti f dic ea ad jo ud a ao . 04 reD ceú bv eid ra u: mA Pch ixa dve e é fo n rmec ae pss ráá tr ii ca a p . a Sr aa i bp ao mde ar i s.<br>pagador.<br>Avançado Entendi Continuar Avançado Entendi Continuar|Col2|Col3|
|---|---|---|
|Receber<br>Saldo: R$ 1.000,00<br>Continuar<br>Avançado<br>Chave<br>aleatória<br>E-mail<br>CPF<br>Celular<br>Selecione o tipo de chave<br>?<br>?<br>?<br>0 de 25 caracteres<br>Pequena descrição da transação<br>Identificador (opcional)<br>Valor (opcional)<br>R$ 0,00<br>Chave:+5561 98888-8888<br>Entendi<br>Dúvida: Os campos Identificador e Valor são<br>opcionais para criação do QR Code. Caso<br>você não especifique o valor, o<br>preenchimento do campo será feito pelo<br>pagador.|Receber<br>Saldo: R$ 1.000,00<br>Continuar<br>Avançado<br>Chave<br>aleatória<br>E-mail<br>CPF<br>Celular<br>Selecione o tipo de chave<br>?<br>?<br>?<br>0 de 25 caracteres<br>Pequena descrição da transação<br>Identificador (opcional)<br>Valor (opcional)<br>R$ 0,00<br>Chave:+5561 98888-8888<br>Entendi<br>Dúvida: A chave é necessária para poder<br>receber um Pix de forma prática.Saiba mais.|Receber<br>Saldo: R$ 1.000,00<br>Continuar<br>Avançado<br>Chave<br>aleatória<br>E-mail<br>CPF<br>Celular<br>Selecione o tipo de chave<br>?<br>?<br>?<br>0 de 25 caracteres<br>Pequena descrição da transação<br>Identificador (opcional)<br>Valor (opcional)<br>R$ 0,00<br>Chave:+5561 98888-8888<br>Entendi<br>Dúvida: A chave é necessária para poder<br>receber um Pix de forma prática.Saiba mais.|
||||








Obrigatório







pelo usuário que ler esse QR Code.







Recomendado






















































**Pagamento através de QR Code estático**


Trata-se de pagamento iniciado pelo usuário pagador por meio da leitura de
QR Code estático.


#### Recomendações e OBRIGAÇÕES

Versão: 7.3

Dezembro de 2025
# 06



Versão: 7.3



Dezembro de 2025




Obrigatório













do DICT sobre usuário recebedor:


para o usuário pagador.


Empresarial/Razão Social;


equivocadas.


Code.









Code.






















































Obrigatório





pagador.





confirmação do pagamento.













deverá ser informado disso antes de confirmar o pagamento.


Exemplos:


crédito [nome da linha de crédito].


















Obrigatório

























sobre essa situação.


problema técnico ou de comunicação.

Exemplos:

 - Transação não concluída. Falha de comunicação. Tente novamente;

 - Seu Pix não foi finalizado. Tivemos problema técnico. Tente novamente;

 - Desculpe, tivemos um problema de comunicação. Tente novamente.


chave inexistente ou bloqueada.


inexistente ou está indisponível.

Exemplos:

 - Transação não concluída. Chave indisponível;

 - Chave não localizada. Tente novamente;

 - Ocorreu um erro. Não foi possível encontrar essa chave.


motivo.


concluir a transação.

Exemplos:


possível realizar o Pix.


pode ser realizado.






















Obrigatório











evidenciar o efetivo motivo do não processamento da transação.


extrapolado.


do próprio PSP.

Exemplos:

 - Tente outro valor, saldo insuficiente;

 - Pix não realizado, o saldo que você possui não foi suficiente;

 - Você está sem saldo para finalizar esse Pix;

 - Transação não concluída. Conta do destinatário indisponível;


 - Erro. Conta do recebedor indisponível;

 - Transação não concluída. Conta do destinatário inexistente;

 - Pix não concluído. A conta da pessoa que você quer transferir não existe;

 - Erro. Conta do recebedor inexistente;


Pix. Tente novamente;

 - Desculpe, tivemos uma falha técnica. Tente de novo.













Recomendado


conta transacional.




|9:30|Col2|
|---|---|
|Confirmação de transferência<br>Saldo:R$ 1.000,00<br>Finalizar<br>Cancelar<br>R$ 10,00<br>Valor final<br>PSP:PSP ABCD<br>CPF/CNPJ:***.777.888 - **<br>Nome:Fernanda Costa<br>INFORMAÇÕES DO DESTINATÁRIO<br>Entendi<br>Transação não concluída. Tempo de<br>processamento extrapolado. Tente novamente.|Confirmação de transferência<br>Saldo:R$ 1.000,00<br>Finalizar<br>Cancelar<br>R$ 10,00<br>Valor final<br>PSP:PSP ABCD<br>CPF/CNPJ:***.777.888 - **<br>Nome:Fernanda Costa<br>INFORMAÇÕES DO DESTINATÁRIO<br>Entendi<br>Transação não concluída. Tempo de<br>processamento extrapolado. Tente novamente.|
|||
















Obrigatório





















mínimo, as seguintes informações:

 - Nome do recebedor e valor da transação.


- período estabelecido na regulação em vigor, contendo, no mínimo:

 - Nome, CPF (mascarado ou não)/CNPJ e nome do PSP do usuário pagador;

 - Nome, CPF (mascarado ou não)/CNPJ e nome do PSP do usuário recebedor;

 - Mensagem do campo “Identificador” (TxId), sempre que estiver preenchido;

 - Valor e ID da transação;

 - Data e hora/minuto/segundo (horário de Brasília) da liquidação.


“Identificador” (TxId) estiver preenchido.


representados na tela ao lado.

 - O ID/transação refere-se ao "EndtoEndID" presente na pacs.008.
























**Pagamento imediato ou com vencimento através de QR Code dinâmico**


Trata-se de pagamento iniciado pelo usuário pagador por meio da leitura de
QR Code dinâmico.


#### Recomendações e OBRIGAÇÕES

Versão: 7.3

Dezembro de 2025
# 07



Versão: 7.3



Dezembro de 2025




Obrigatório



































































aplicáveis:


participante;

 - Os dados do devedor (CPF/CNPJ e Nome), caso informados;


outros);


preenchimento do usuário pagador;


contrário, o valor não poderá ser editável).


informações ao pagador (se houver).




































Obrigatório













campos aplicáveis.

 - Campo de data de vencimento;


de vencimento ou para data a agendar;


participante;

 - Os dados do devedor (CPF/CNPJ e Nome);


recebedor queira transmitir ao usuário pagador;


preenchimento do usuário pagador;


nas transações iniciadas por QR Code.












Obrigatório

















específica sobre essa situação.


problema técnico ou de comunicação. Exemplos:

 - Transação não concluída. Falha de comunicação. Tente novamente.

 - Seu Pix não foi finalizado. Tivemos um problema técnico.

 - Desculpe, tivemos um problema de comunicação. Tente novamente.


de crédito que será utilizada.

Exemplos:


crédito [nome da linha de crédito].









Recomendado


conta transacional.






























Obrigatório



Versão 7.3 Pagamento imediato ou com vencimento através de QR Code dinâmico



















O pagador deverá ser informado acerca de erro decorrente da leitura de QR Code com

chave inexistente ou bloqueada.

Mensagem obrigatória: Deve evidenciar que a transação não foi realizada e que houve um

problema técnico ou de comunicação.

Exemplos:

 - Transação não concluída. Falha de comunicação. Tente novamente;

 - Seu Pix não foi finalizado. Tivemos problema técnico. Tente novamente;

 - Desculpe, tivemos um problema de comunicação. Tente novamente.


Caso o prazo de expiração do QR Code tenha sido ultrapassado, o usuário pagador deve

ser comunicado sobre isso. A mensagem deve evidenciar que a transação não foi

concluída e especificar o erro.

Exemplos:

 - Transação não concluída. QR Code inválido;

 - Erro ao realizar o Pix. QR Code inválido.


O pagador deverá ser informado acerca de erro decorrente da leitura de QR Code com

chave vinculada a uma conta ou usuário com restrição para recebimento de transação

Pix por envolvimento em fraude e da impossibilidade de concluir a transação por esse

motivo.

Mensagem obrigatória: Deve evidenciar que a conta de destino ou o usuário recebedor

esteve envolvido em transação com fundada suspeita de fraude e que não é possível

concluir a transação.

Exemplos:

 - Conta ou recebedor envolvido em transação com fundada suspeita de fraude. Não é

possível realizar o Pix.

 - Conta de destino envolvida em transação com fundada suspeita de fraude. O Pix não

pode ser realizado.













**DESTINATÁRIO** : PSP do usuário pagador



36




Obrigatório



















erro.

Exemplos:


  - vencimento. Pix não realizado. QR Code vencido.


evidenciar o efetivo motivo do não processamento da transação.


extrapolado.


do próprio PSP.

Exemplos:

 - Tente outro valor, saldo insuficiente;

 - Pix não realizado, o saldo que você possui não foi suficiente;

 - Você está sem saldo para finalizar esse Pix;

 - Transação não concluída. Conta do destinatário indisponível;


 - Erro. Conta do recebedor indisponível;

 - Transação não concluída. Conta do destinatário inexistente;

 - Pix não concluído. A conta da pessoa que você quer transferir não existe;

 - Erro. Conta do recebedor inexistente;


Pix. Tente novamente;

 - Desculpe, tivemos uma falha técnica. Tente de novo.


















Obrigatório


























 - Nome do recebedor e valor da transação.


 - período estabelecido na regulação em vigor, contendo, no mínimo:

 - Nome, CPF (mascarado ou não)/CNPJ e nome do PSP do usuário pagador;

 - Nome, CPF (mascarado ou não)/CNPJ e nome do PSP do usuário recebedor;

 - Mensagem do campo “Identificador” (TxId);

 - Valor e ID da transação,

 - Data e hora/minuto/segundo (horário de Brasília) da liquidação.


nome do PSI deve constar no comprovante.


(agência e conta) do recebedor no comprovante de pagamento.


meio de QR Code dinâmico.

 - O ID/transação refere-se ao "EndtoEndID" presente na pacs.008.







Pix vinculada ao pagamento do QR Code Dinâmico.


Recomendado









recebedor.








**Extrato**


Demonstrativo de pagamentos, recebimentos e devoluções realizados no
Pix, em que os usuários obtêm acesso a informações ligadas a cada transação
realizada.


#### Recomendações e OBRIGAÇÕES

Versão: 7.3

Dezembro de 2025
# 08



Versão: 7.3



Dezembro de 2025




Obrigatório























diferenciadas de transações que não são do Pix.


e do troco separadamente.


um menu de consulta específico para agendamentos.











transação Pix.



















devolução correspondente, quando existir.





da transação raiz, o nome do remetente não deve ser exibido no extrato.


Recomendado


na funcionalidade de extrato.













PSP com referência ao participante que prestou o serviço de iniciação.








**Devolução**


Funcionalidade que permite aos usuários do Pix a devolução, parcial ou total,
do valor de uma transação recebida.


#### Recomendações e OBRIGAÇÕES

Versão: 7.3

Dezembro de 2025
# 09



Versão: 7.3



Dezembro de 2025




Obrigatório





últimos 90 dias.









devolução.



Recomendado


ou na consulta ao extrato Pix, se este for disponibilizado.






































Obrigatório





recebidos.















preenchimento.


“informacoesEntreUsuarios”.


usuário estão representados na tela ao lado.

 - O ID/transação refere-se ao "EndtoEndID" presente na pacs.008 original;


renderizar links ou qualquer conteúdo dinâmico.







Recomendado


ser de fácil consulta pelo usuário.









conta transacional.
















Obrigatório













































evidenciar o efetivo motivo do não processamento da transação de devolução.


dias e valor superior ao da transação.

Exemplos:

 - Devolução não concluída. Dados incompatíveis com a transação original;

 - Erro ao fazer a devolução, confira se informou os dados corretamente;

 - Erro ao devolver o Pix, verifique se os dados estão corretos;


90 dias;

 - Erro ao devolver o Pix pois já passou o prazo de 90 dias;


original;

 - Erro ao devolver o Pix. Verifique o valor informado;

 - Tente outro valor, saldo insuficiente;

 - Devolução não concluída. O saldo que você possui não é suficiente;

 - Você está sem saldo para finalizar esse Pix.


nesse caso.


informações:

 - Motivo do bloqueio;

 - Valor bloqueado;

 - Nome do usuário pagador;

 - Data/hora/minuto/segundo (horário de Brasília) da transação original;

 - Prazo máximo do bloqueio (72 horas).
















Obrigatório





























mínimo, as seguintes informações:

 - Valor disponibilizado;

 - Data/hora/minuto/segundo (horário de Brasília) do bloqueio;

 - Nome do usuário pagador;

 - Data/hora/minuto/segundo (horário de Brasília) da transação original;

 - Valor da transação original.


deve conter, no mínimo, as seguintes informações:

 - Valor devolvido;

 - Data/hora/minuto/segundo (horário de Brasília) do bloqueio;

 - Nome do destinatário da devolução;

 - Data/hora/minuto/segundo (horário de Brasília) da transação original;

 - Valor da transação original.


as seguintes informações:

 - Valor creditado;

 - Nome do remetente da devolução;

 - Data/hora/minuto/segundo (horário de Brasília) da transação original;

 - Valor da transação original.


















**Minhas Chaves**


Funcionalidade que permite aos usuários do Pix o registro, a exclusão e a
portabilidade de chaves no Pix.


#### Recomendações e OBRIGAÇÕES

Versão: 7.3

Dezembro de 2025
# 10



Versão: 7.3



Dezembro de 2025




Obrigatório



Versão 7.3 Minhas Chaves

















É obrigatório que, quando do primeiro acesso ao Minhas chaves, o usuário seja informado

sobre a chave, abordando, no mínimo:

 - Que a chave identifica de forma prática o recebedor e facilita a experiência de

pagamento ou transferência;

 - Tipos (número de celular, e-mail, CPF/CNPJ, chave aleatória);

 - Restrição de que cada chave só poderá ser vinculada a uma única conta;

 - Que pode ser cadastrado até 5 chaves para a mesma conta.


Apresentar obrigatoriamente, sempre que houver registro de chave, mensagem de

consentimento que informe, no mínimo, que usuários pagadores que tenham

conhecimento da chave visualizarão os seguintes dados do usuário recebedor ao lhe

enviar pagamentos:

 - Nome completo;

 - CPF com máscara (ex: **.777.888-**).

O nome do prestador de serviços de pagamento ao qual a chave está vinculada poderá

ser exibido, a critério do PSP do pagador. Além disso, a mensagem de consentimento deve

informar que todos os demais usuários do Pix que tenham a informação do e-mail ou do

número de telefone celular do usuário poderão saber que ele cadastrou esse email e/ou

esse número de telefone celular como chave Pix.





















**DESTINATÁRIO** : PSP do usuário pagador e PSP do usuário recebedor



47




Obrigatório





gerenciamento pelo usuário.





telefone celular, e-mail, CPF/CNPJ e chave aleatória).















ao usuário.



Recomendado


exclusão, portabilidade e reivindicação), para diferentes tipos de chave.




















































Obrigatório













operação foi realizada e que foi bem sucedida.


realizada e o motivo do insucesso. Exemplos:

 - Chave cadastrada/ alterada/ editada/ excluída/ deletada com sucesso!

 - Pronto, sua chave já está registrada!


informar sua chave [chave].


 - Pronto! Portabilidade efetuada. Já pode usar a chave [chave].


chave confirmou que ainda a usa.


pois não identificamos a confirmação na instituição de origem.


























**Meus Limites Pix**


Funcionalidade que permite aos usuários do Pix consultar e gerenciar os
limites do Pix, inclusive para Pix Saque/Pix Troco, Pix Agendado e Pix
Automático, e cadastrar contas ou beneficiários com limites diferenciados.


#### Recomendações e OBRIGAÇÕES

Versão: 7.3

Dezembro de 2025
# 11



Versão: 7.3



Dezembro de 2025




Obrigatório



























disponibilizada.


abordando, no mínimo, os seguintes pontos:

- Pix para pessoas


(contas associadas a CPF), por período (diurno e noturno).

- Pix para empresas


(contas associadas a CNPJ).

- Pix Saque e Pix Troco


transações Pix Saque e Pix Troco;


definidos de forma independente dos demais limites;


dinheiro;


3.000,00 (período diurno) e R$ 1.000,00 (período noturno).

- Pix Agendado


forma independente dos demais limites.

- Pix Automático


empresas (contas associadas a CNPJ);


forma independente dos demais limites.

- Cadastro de contas (caso essa funcionalidade seja disponibilizada)


gerir os valores de cada um desses limites;


diferenciado e gerir o valor desse limite.

- Cadastro de beneficiários (caso essa funcionalidade seja disponibilizada)


valores de cada um desses limites;


gerir o valor desse limite.




































Obrigatório

















Automático.


Central), ficando a critério do PSP pagador atender a essas solicitações.




























Obrigatório















aumento está sujeito à aprovação do PSP pagador.






























Obrigatório





redução foi concluída com sucesso.












































Obrigatório









noturno.
































Obrigatório

















a todas as contas cadastradas.





cadastrados e exclusão das contas.


de cadastro será concluído no prazo de 24 a 48 horas.




























Obrigatório





















cadastrados e exclusão das beneficiários.


processo de cadastro será concluído no prazo de 24 a 48 horas.






























Obrigatório











incompatibilidade com limites pré-cadastrados.

Exemplos:


cadastrado para esse beneficiário”.
































Recomendado





noturno para 20:00 ou 22:00.







Obrigatório


alteração será concluída no prazo de 24 a 48 horas.


















**Pix Agendado**


Funcionalidade que permite o agendamento único e agendamentos
recorrentes de transações Pix.


#### Recomendações e OBRIGAÇÕES

Versão: 7.3

Dezembro de 2025
# 12



Versão: 7.3



Dezembro de 2025




Obrigatório





inclusive para dias não úteis.

































































deve ser apresentada também a data agendada para o pagamento.


(sempre que estiver preenchido).

 - O campo “Descrição” refere-se a “informacoesEntreUsuarios” da pacs.008;


qualquer conteúdo dinâmico;


do payload do QR Code dinâmico.





Recomendado













para o pagamento.








Obrigatório



















transações Pix, permitindo, no mínimo, a recorrência semanal e mensal.

















































transações.


informada) e a data do último Pix (caso existente).


“Descrição” (sempre que estiver preenchido).

 - O campo “Descrição” refere-se a “informacoesEntreUsuarios” da pacs.008;


qualquer conteúdo dinâmico;


do horário limite para o cancelamento.





Recomendado













prazo indeterminado.








Obrigatório





















os seguintes dados:

 - Frequência da recorrência;

 - Quantidade de pagamentos (caso selecionada);

 - Data do último Pix (caso existente).


de conta transacional”.



















Recomendado















agendamentos.


meses em que for aplicável, o dia da liquidação do agendamento recorrente.






























Obrigatório

















agendamento ou mudar a data prevista para a liquidação da transação.


comunicando o motivo do insucesso do agendamento.
















































Obrigatório















cancelamento individual do agendamento programado mais próximo.


agendamentos vinculados a uma recorrência de uma só vez.


pagador.



Recomendado















agendamentos recorrentes por um período determinado.


agendamento deve ser informado ao usuário pagador.


pagamentos ou a data de término do agendamento.


deve ser informado ao usuário pagador.


















































Obrigatório















































permitir que o usuário efetue a recomposição do saldo até esse horário


sido possível efetivar a transação Pix.


motivo.


por falha operacional e que ele deve realizar um novo Pix.


conter, no mínimo, as seguintes informações:

 - Nome do recebedor;

 - Valor da transação


clicar na notificação.



Recomendado
















**Pix Copia e Cola**


Disponibilização de opção ao usuário pagador, na interface de mobile
banking, de colar código.


#### Recomendações e OBRIGAÇÕES

Versão: 7.3

Dezembro de 2025
# 13



Versão: 7.3



Dezembro de 2025




Obrigatório













espécie, por meio da opção de colar código (Pix Copia e Cola).




















|Col1|9:30|
|---|---|
||Pix<br>Saldo:R$ 1.000,00<br>Insira o código no campo abaixo:|
|0,00|0,00|






























Obrigatório








































































Obrigatório











código (Pix Copia e Cola).
























**Pix Saque e Pix Troco**


Permite aos usuários do Pix realizar o saque de recursos em espécie em
agentes de saque ou participantes e a consultar os locais que disponibilizam

- serviço.


#### Recomendações e OBRIGAÇÕES

Versão: 7.3

Dezembro de 2025
# 14



Versão: 7.3



Dezembro de 2025




Obrigatório











no mínimo:

 - O que é o serviço;


disponibilizar o Pix Saque e o Pix Troco;


diretamente por meio de caixas eletrônicos;


definidas na regulamentação;


correspondentes bancários.





Recomendado


informacional do Pix.


























Obrigatório































disponíveis aos usuários no momento da consulta:


(Unicad);


ou pelo participante (Pix Saque);

 - Disponibilidade (dias e horários) do serviço de saque.


sejam prestadas, devem ser disponibilizadas pelos participantes aos usuários:

 - Valor máximo disponível por transação;

















quaisquer alterações ocorridas.


Recomendado


atendimento que disponibilizarão o serviço de saque.
































Obrigatório













retornados ao usuário sacador os seguintes dados:


não exista, o nome informado deve ser o Nome Empresarial/Razão Social;


critério do participante;


outros);


preenchimento do usuário sacador;


usuário sacador. Caso contrário, o valor não poderá ser editável).






















































Obrigatório







retornados ao usuário sacador os seguintes dados:


ser o Nome Empresarial/Razão Social;


critério do participante;













outros);


preenchimento do usuário sacador;

- O valor da compra;


contrário, o valor não poderá ser editável);

- O valor final da transação.




















































Obrigatório



























Exemplos:


crédito [nome da linha de crédito].


mínimo, as seguintes informações:

 - Nome do recebedor e valor final da transação.


ao usuário estão representados nas telas ao lado.

 - O ID/transação refere-se ao "EndtoEndID" presente na pacs.008.


comprovante deve informar o valor da tarifa passível de cobrança.










**Pix Automático**


Funcionalidade que permite aos usuários do Pix realizar transações
recorrentes de forma automática, mediante prévia autorização.


#### Recomendações e OBRIGAÇÕES

Versão: 7.3

Dezembro de 2025
# 15



Versão: 7.3



Dezembro de 2025




Obrigatório



















dias posteriores.
Exemplos:

 - O que é o Pix Automático:

É o Pix trazendo ainda mais comodidade para você!

 - Vantagens do Pix Automático

   - É gratuito;

pré-aprovada (ex. cheque especial);

que você deseja pagar oferece essa opção.

 - Funcionamento do Pix Automático

conta;

“Pagamentos agendados” no menu Pix Automático;

como data de pagamento, valor e nome do recebedor;

  - Pagamentos podem ocorrer em qualquer dia (úteis e não úteis);

feita pelo menos mais uma tentativa no próprio dia;

dia anterior à data de pagamento;

autorização, você poderá contestar a transação.




















Obrigatório





























































autorização, mediante autenticação prévia no app da conta).

A notificação deve conter, no mínimo:

 - Nome do recebedor;

 - Nome do devedor, quando ele for diferente do pagador;

 - Objeto do pagamento;

 - Data de expiração da autorização pendente.


pagador.


seguintes informações:

 - Alerta de vencimento da solicitação de autorização;

 - Nome do recebedor;

 - Nome do devedor, quando ele for diferente do pagador;

 - Objeto do pagamento.


da autorização, mediante autenticação prévia no app da conta.


jornada 1 sempre deve ser efetivada no ambiente Pix logado da conta.


opções de ordenação.


- nome informado deve ser o Nome Empresarial/Razão Social.



(continuidade da jornada de autorização no item 16).












Obrigatório







Automático para aquele pagamento.







Recomendado













Automático dispostas no item 4.














































Obrigatório



























continue para confirmar a autorização.


autorização (continuidade da jornada de autorização no item 16).


para a etapa da oferta do Pix Automático para os próximos pagamentos.


















































Obrigatório































autorização), o PSP pagador deve possibilitar:


autorização.


de pagamento por QR Code.

 - a inserção do código por meio da opção Pix Copia e Cola.


autorização no item 16).




























































Obrigatório












































 - Nome do recebedor;

 - CNPJ do recebedor;

 - Nome do devedor;

 - CPF (mascarado)/CNPJ do devedor;

 - Objeto do pagamento (caso seja informado);


 - Data prevista do primeiro pagamento;

 - Periodicidade dos pagamentos futuros;

 - Prazo da autorização ou quantidade de parcelas;

 - Valor previsto dos pagamentos (caso seja fixo);


existentes).


não exista, o nome informado deve ser o Nome Empresarial/Razão Social.


participante.


preenchido, deve ser exibido ao usuário pagador.


O prazo da autorização pode ser por tempo indeterminado.


estabelecido.


 - Notificações serão enviadas quando os pagamentos forem agendados;


pagamentos por meio do Pix Automático podem ser desabilitados;

 - O cancelamento da autorização pode ser feito a qualquer momento;


Automático.

Deve ser disponibilizada a informação do ID da autorização.














Obrigatório



















bem como pelo uso do Pix Copia e Cola.






































Obrigatório























seguintes informações:

 - Nome do recebedor;

 - CNPJ do recebedor;

 - Nome do devedor;

 - CPF (mascarado)/CNPJ do devedor;

 - Objeto do pagamento (caso seja informado);


 - Data prevista do primeiro pagamento recorrente;

 - Periodicidade dos pagamentos futuros;

 - Prazo da autorização ou quantidade de parcelas;

 - Valor previsto dos pagamentos (caso seja fixo);


outros);


preenchimento do usuário pagador.


Caso contrário, o valor não poderá ser editável.


não exista, o nome informado deve ser o Nome Empresarial/Razão Social.


opcional e fica a critério do participante.

O prazo da autorização pode ser por tempo indeterminado.


sujeito ao valor máximo estabelecido pelo usuário.


configuração do valor a partir do mínimo estabelecido.


























Obrigatório























































para o processo de autorização.


meio do Pix Automático.


jornada 3, o usuário deve ser imediatamente informado que:

 - O pagamento imediato foi efetivado;


Automático forem agendados;


para pagamentos por meio do Pix Automático podem ser desabilitados;

 - O cancelamento da autorização pode ser feito a qualquer momento;


Automático.

Deve ser disponibilizada a informação do ID da autorização.


autorização não foi concluído.


ser apresentados ao usuário estão representados na tela ao lado;


autorização.

O ID/transação refere-se ao "EndtoEndID" presente na pacs.008.


posteriormente.












Obrigatório





autorizações ativas.
















 - Nome do recebedor;

 - CNPJ do recebedor;

 - Nome do devedor;

 - CPF (mascarado)/CNPJ do devedor;

 - ID da autorização;

 - Objeto do pagamento (caso seja informado);


 - Data prevista do primeiro pagamento recorrente;

 - Periodicidade dos pagamentos futuros;

 - Prazo da autorização ou quantidade de parcelas;

 - Valor previsto dos pagamentos (caso seja fixo);

 - Valor máximo do pagamento (caso definido pelo pagador).


não exista, o nome informado deve ser o Nome Empresarial/Razão Social.

O prazo da autorização pode ser por tempo indeterminado.


pagamento ocorrer após o vencimento.
































Obrigatório







agendados para o mesmo dia.




































Obrigatório





























permitir a configuração do valor a partir do mínimo estabelecido.


agendamentos futuros, não se aplicando aos agendamentos já realizados.


eventual edição feita pelo usuário:

-Valor máximo: desabilitado

-Recebimento de notificações de agendamento: habilitado

-Uso de linha de crédito (caso seja ofertada pelo PSP): habilitado


imediatamente informado que a alteração foi concluída com sucesso.



Recomendado













possibilidade de cancelamento do pagamento agendado.






















Obrigatório





cancelamento dos pagamentos agendados.














 - Nome do recebedor;

 - CNPJ do recebedor;

 - Nome do devedor;

 - CPF (mascarado)/CNPJ do devedor;

 - Objeto do pagamento (caso seja informado);


 - Data prevista do pagamento;

 - Valor do pagamento;


preenchido).


não exista, o nome informado deve ser o Nome Empresarial/Razão Social.


e multa acrescidos ao pagamento).


qualquer conteúdo dinâmico.









anterior à data agendada para o pagamento.
























Obrigatório













todas as autorizações, com, no mínimo, as seguintes informações:

 - Nome do recebedor;

 - Status: pendente, ativa, expirada, cancelada e em processamento;

 - Data da autorização, exceto nos casos de autorizações pendentes;


 - Nas expiradas: data do fim da vigência;


deve estar disponível de forma clara e acessível ao usuário pagador.


e que ainda estejam em processo de conclusão.


experiência unificada para o usuário pagador.


autorizações e consentimentos.















Recomendado


filtro pelo status na consulta ao histórico das autorizações.








Recomendado































recebimento de notificações de agendamento.


autorizações numa única jornada (única tela).


máximo definido, o pagamento não será agendado e o usuário será notificado.


configuração do valor a partir do mínimo estabelecido.


agendamentos futuros, não se aplicando aos agendamentos já realizados.


possibilidade de cancelamento do pagamento agendado.






























Obrigatório
























 - Identificação de que a transação é um Pix Automático;

 - Nome e CNPJ do recebedor;

 - Nome do PSP do recebedor;

 - Nome e CPF (mascarado ou não)/CNPJ do pagador;

 - Objeto do pagamento (caso seja informado);


 - ID da transação ("EndtoEndID" presente na pacs.008);

 - Data e hora/minuto/segundo (horário de Brasília) da liquidação;

 - Valor.


representados na tela ao lado.


cobrança vinculada ao QR Code.





Recomendado












Obrigatório













pagamento imediato:

Exemplos:

 - Falha ao confirmar sua autorização do Pix Automático. Tente novamente.


autorização do Pix Automático. Tente de novo.


pagamentos.


















Obrigatório









































agendamento com as seguintes informações:

 - Transação agendada do Pix Automático;

 - Nome do recebedor;

 - Valor;

 - Data de pagamento.


a recomposição do saldo até esse horário.


próximos dias.


vencimento.
















Obrigatório











































meios.


meios.


preferencialmente, após esse horário.


agendados”, no menu “Pix Automático”, ou em “Lançamentos futuros”.


do recebedor.


 - Cancelamento do Pix Automático a pedido do recebedor;

 - Nome do recebedor;

 - Objeto do pagamento (caso seja informado);


notificação não serão cancelados;

 - Suspensão de novos agendamentos.
















Obrigatório































ultrapassar o valor máximo estabelecido pelo usuário na autorização.


conclusão do processo de autorização pelo PSP do recebedor.


confirmação referente à jornada 1, contendo, no mínimo, os seguintes dados:

 - Nome do recebedor e informação de que a exclusão foi a seu pedido;

 - Motivação da exclusão:

  - erro nos dados da recorrência;

  - usuário pagador confirmou a recorrência utilizando outro meio.


Social.


clicar na notificação.







Recomendado







pagamento no mesmo ciclo.
















**Autoatendimento MED**


Funcionalidade que permite aos usuários pagadores registrar, pelo próprio
aplicativo, a contestação de transações Pix decorrentes de golpe, fraude ou
crime, bem como de irregularidades em transações Pix Automático, e
consultar os pedidos já efetuados, no âmbito do Mecanismo Especial de
Devolução (MED).


#### Recomendações e OBRIGAÇÕES

Versão: 7.3

Dezembro de 2025
# 16



Versão: 7.3



Dezembro de 2025




Obrigatório











deve disponibilizar consulta a contestações registradas.


funcionalidade de contestação.




























































































Obrigatório































PSP, e cancelamento de pedidos registrados.


solicitar a devolução.

Exemplos:


Acione o MED o quanto antes!


Veja como funciona a contestação nos casos de golpe, fraude ou crime:

1. Sua solicitação deve ser feita em até 80 dias da realização da transação;

2. O envio de documentação complementar auxilia a comprovação da fraude;


de volta.


1. Sua solicitação pode ser feita em até 80 dias da realização da transação;


em até 24 horas;


das demais contestações devidas a golpe, fraude ou crime.












Obrigatório





















primeiro acesso, as regras do mecanismo.



âmbito do MED devido ao prazo limite excedido.































meu conhecimento; (SituationType: account_takeover)


transação; (SituationType: coercion)


autorização; (SituationType: fraudulent_access)

 - Outro tipo de golpe. (SituationType: other)


resposta sobre o tipo de golpe, fraude ou crime de que o usuário foi vítima.


valores no DICT.


informações:


registro;


contestação;


total do valor;




















Recomendado











MED. Deve haver também uma opção de resposta para outros tipos de fraude


de transações que não sejam passíveis de devolução via MED.

Exemplos:

 - Desentendimento comercial entre comprador e vendedor;

 - Transferência realizada para pessoa ou empresa erradas;

 - Arrependimento em efetuar o Pix.









Obrigatório




























Obrigatório











































ser questionado sobre o motivo.


as situações elegíveis à devolução previstas no regulamento do Pix.


recuperação de valores.


disponíveis:


golpista; (SituationType: scam);

 - Não autorizei o Pix Automático para essa cobrança;

 - Já cancelei a autorização para essa cobrança;


de pagamento);

 - Outra situação envolvendo cobrança indevida no Pix Automático.


abordando, no mínimo, as seguintes informações:


registro;


de no máximo 24h;



Recomendado







caracteres.














Obrigatório



























informações:


registro;


contestação;


total do valor;


imediatamente informado sobre essa situação.


um problema técnico ou de comunicação. Exemplos:

 - Falha no registro da contestação do Pix. Tente novamente mais tarde;

 - Desculpe, tivemos um problema de comunicação. Tente novamente.


envolvendo o Pix.













Recomendado











diretamente o recebedor para resolver o problema.







Pix Automático ao mesmo tempo (registro em lote).


















Obrigatório







































permitir que o usuário:


canal de atendimento do PSP e o prazo para conclusão da análise;


contestação pelo PSP;

 - Cancele pedidos registrados.


com, no mínimo, as seguintes informações:

 - Número do protocolo do pedido;

 - Nome do recebedor da transação raiz;

 - Valor da transação contestada;

 - Valor efetivamente devolvido, no caso de contestação aprovada;


exemplo: em análise/aprovada/rejeitada/cancelada).


mínimo, as seguintes informações:

 - Número, data e hora do protocolo do registro;

 - Situação da solicitação;


se encontra em avaliação;

 - Nome do recebedor da transação contestada;

 - Valor da transação contestada;

 - ID da transação contestada;

 - Valor efetivamente devolvido, no caso de contestação aprovada.


transação raiz ou em outras contas envolvidas na fraude.


poderá solicitar o cancelamento do pedido.













questionado se tem certeza de que deseja efetuar o cancelamento.












Obrigatório





















deve conter, no mínimo, as seguintes informações:

 - Nome do usuário pagador da transação vinculada à notificação de infração;


de infração;

 - Valor da transação vinculada à notificação de infração;

 - Motivo do bloqueio;

 - Valor bloqueado;

 - Prazo máximo do bloqueio (11 dias).


mínimo, as seguintes informações:

 - Nome do usuário pagador da transação vinculada à notificação de infração;


de infração;

 - Valor da transação vinculada à notificação de infração;

 - Valor disponibilizado;

 - Data/hora/minuto/segundo (horário de Brasília) do bloqueio.


parte do valor previamente bloqueado.


usuário recebedor deve conter, no mínimo, as seguintes informações:

 - Valor da transação vinculada à notificação de infração;



















de infração;




 - Valor devolvido;


conta que recebeu os recursos da transação raiz.


na mensagem.
















Obrigatório















em sua conta decorrente de uma devolução de transação Pix contestada.


no mínimo, as seguintes informações:

 - Valor creditado;

 - Nome do remetente da devolução;

 - Data/hora/minuto/segundo (horário de Brasília) da transação raiz;

 - Valor da transação raiz.


notificação deve conter no mínimo:

 - Valor creditado;


registros no âmbito do MED.


transação raiz, não deve ser exibido ao usuário pagador.









qualquer canal de atendimento.


Recomendado


do registro de contestação via MED.








**Serviço de iniciação de transação de pagamento no Pix**


Trata-se da disponibilização ao usuário de serviço de iniciação de transação
de pagamento no Pix.


#### Recomendações e OBRIGAÇÕES

Versão: 7.3

Dezembro de 2025
# 17



Versão: 7.3



Dezembro de 2025




Obrigatório













Agendado” e “Pix Automático”.


casos.


de análise para ser autorizada e dar a opção de cancelamento da transação.

Exemplos:


Pix?


cancelar a transação?


comunicado sobre o erro de formato pelo PSI.


problema no formato da chave.

Exemplos:

 - Transação não concluída. Formato da chave inválido;

 - Ocorreu um problema no formato da chave. Tente novamente;

 - Ocorreu um erro. Confira o formato dessa chave;

 - Seu Pix não foi concluído. Verifique o formato da chave informada.


inexistência dessa chave pelo PSI.


chave é inexistente.

Exemplos:

 - Transação não concluída. Chave inexistente.

 - Chave não localizada. Tente novamente.

 - Ocorreu um erro. Não foi possível encontrar essa chave.

 - Erro. Veja se informou a chave certa.

 - Pix não concluído. Verifique se a chave está correta.








**Obrigatório**













sobre essa situação pelo PSI.


problema técnico ou de comunicação.

Exemplos:

 - Transação não concluída. Falha de comunicação. Tente novamente.

 - Seu Pix não foi finalizado. Tivemos um problema técnico. Tente novamente.

 - Desculpe, tivemos um problema de comunicação. Tente novamente.


problema técnico ou de comunicação.

Exemplos:

 - Transação não concluída. Falha de comunicação. Tente novamente.

 - Seu Pix não foi finalizado. Tivemos um problema técnico.

 - Desculpe, tivemos um problema de comunicação. Tente novamente.


concluída e especificar o erro.

Exemplos:

 - Transação não concluída. QR Code inválido.

 - Erro ao realizar o Pix. QR Code inválido.


concluída e especificar o erro.

Exemplos:


  - vencimento.

 - Pix não realizado. QR Code vencido.








Obrigatório

















preenchido.


conta transacional quando o txId estiver preenchido.


(ex: ***.777.888-**).


ser informados ao usuário pagador, no mínimo, os seguintes dados:


participante;

 - Valor da transação.


conta transacional, no momento da confirmação do pagamento.


previstas no capítulo “Pix Agendado”.








Obrigatório







referentes à disponibilização:


funcionamento, em local a critério do PSI;


correspondentes à etapa de consentimento na jornada oferecida pelo PSI;


 - Do comprovante de pagamento;

 - Das mensagens de erro;


pagamentos.



Recomendado







pagamento.


transação de pagamento.



histórico de todas as autorizações, correspondentes à etapa de consentimento.





dos nomes que possuem chave Pix.








**Integração com Lista de Contatos**


Funcionalidade que permite ao usuário identificar facilmente as pessoas na
lista de contatos do seu smartphone que possuem chaves Pix.


#### Recomendações e OBRIGAÇÕES

Versão: 7.3

Dezembro de 2025
# 18



Versão: 7.3



Dezembro de 2025




Recomendado







aplicativo do PSP requer prévio consentimento do usuário.





consentimento do usuário.


usuário.










































**Pix em Internet Banking**


Disponibilização de opção ao usuário pagador, na interface de internet
banking, de colar código.


#### Recomendações e OBRIGAÇÕES

Versão: 7.3

Dezembro de 2025
# 19



Versão: 7.3



Dezembro de 2025




Recomendado



Versão 7.3 Pix em Internet Banking





No internet banking do PSP, pode haver opção de rápido e fácil acesso ao usuário para

realizar pagamentos de transações a partir de websites, por meio da opção de colar

código Pix obtido nos websites.

























**DESTINATÁRIO** : PSP do usuário pagador e PSP do usuário recebedor



123




Recomendado



Versão 7.3 Pix em Internet Banking





No internet banking do PSP, pode haver opção de rápido e fácil acesso ao usuário para

realizar pagamentos de transações a partir de websites, por meio da opção de colar

código Pix obtido nos websites.





































**DESTINATÁRIO** : PSP do usuário pagador e PSP do usuário recebedor



124




Recomendado



Versão 7.3 Pix em Internet Banking





No internet banking do PSP, pode haver opção de rápido e fácil acesso ao usuário para

realizar pagamentos de transações a partir de websites, por meio da opção de colar

código Pix obtido nos websites.



























































**DESTINATÁRIO** : PSP do usuário pagador e PSP do usuário recebedor



125




Recomendado



Versão 7.3 Pix em Internet Banking





No internet banking do PSP, pode haver opção de rápido e fácil acesso ao usuário para

realizar pagamentos de transações a partir de websites, por meio da opção de colar

código Pix obtido nos websites.



























































**DESTINATÁRIO** : PSP do usuário pagador e PSP do usuário recebedor



126




Recomendado



Versão 7.3 Pix em Internet Banking







Antes da confirmação do pagamento com vencimento, devem ser retornados ao usuário

pagador os dados abaixo, utilizando os dados do DICT sobre usuário recebedor nos

campos aplicáveis:

 - Campo de data de vencimento;

 - Opção para o pagador, se desejar, informar a Data de Pagamento Pretendida (DPP),

definida no Manual de Padrões para Iniciação do Pix, para o mesmo dia ou para a data

de vencimento ou para data a agendar;

 - Valores: original, abatimento, desconto, juros, multa (caso informados) e valor final;

 - Nome e CPF (com máscara) / CNPJ (sem máscara) do recebedor. No caso de CNPJ, o

nome informado deve ser o Nome Fantasia da empresa, caso exista. Caso não exista, o

nome informado deve ser o Nome Empresarial/Razão Social. O número da agência e o

número da conta do recebedor não devem retornar para o usuário pagador. O retorno

da informação do nome do PSP do recebedor é opcional e fica a critério do

participante;

 - Os dados do devedor (CPF/CNPJ e Nome);

 - O campo "InfoAdicionais", caso informado, conforme definido no Manual de Padrões

para Iniciação do Pix;

 - O campo “infoAdicionais” deve conter apenas caracteres ou HTML sem qualquer

conteúdo dinâmico, como por exemplo scripts (javascript, php, cgi, dentre outros);

 - O campo "Solicitação ao Pagador", caso informado: descrição e caixa de texto para

preenchimento do usuário pagador;

 - Campos de endereço do recebedor: UF; Cidade; Logradouro e CEP (essas informações

podem estar disponíveis ao usuário por meio de outro objeto como, por exemplo, um

ícone ou botão).

















**DESTINATÁRIO** : PSP do usuário pagador e PSP do usuário recebedor



127




**Acessibilidade no Pix**


Disponibilização ao usuário de acesso às ferramentas de acessibilidade,
integradas ao ambiente Pix.


#### Recomendações e OBRIGAÇÕES

Versão: 7.3

Dezembro de 2025
# 20



Versão: 7.3



Dezembro de 2025




Recomendado



























de acessibilidade, sendo exemplo não exaustivo:


Perguntas Frequentes (FAQ);

 - Possibilidade de uso de intérprete de Libras.


smartphones, sendo exemplos não exaustivos:

 - Aumento do tamanho das áreas de toque dos botões ou ícones ("touch");

 - Descrição ativa nos elementos da tela e funcionalidades;

 - Seleção de prioridades de informações a serem lidas;


ambiente Pix.




































|Pix|Col2|Col3|Col4|
|---|---|---|---|
|Saldo:R$ 1.000,00<br>Nadir da Silva|Saldo:R$ 1.000,00<br>Nadir da Silva|Saldo:R$ 1.000,00<br>Nadir da Silva||
|om<br>  Manual<br>Pix Copia<br>e Cola<br>Pix com<br>QR Code<br>Receber Pix<br>Meus<br>limites<br>Pix<br>Automático<br>Extrato /<br>Devolução<br>as<br>es<br>10,00<br>r<br>Pagamento<br>via Chave<br>Roberto da Silva<br>R$3<br>Valor<br>J<br>AS TRANSAÇÕES<br>Celular<br>CPF<br>Chave<br>Aleatória<br>E-mail<br> escuro<br> explicativo em Libras sobre o Pix<br>tar a fonte<br>Vídeo|om<br>  Manual<br>Pix Copia<br>e Cola<br>Pix com<br>QR Code<br>Receber Pix<br>Meus<br>limites<br>Pix<br>Automático<br>Extrato /<br>Devolução<br>as<br>es<br>10,00<br>r<br>Pagamento<br>via Chave<br>Roberto da Silva<br>R$3<br>Valor<br>J<br>AS TRANSAÇÕES<br>Celular<br>CPF<br>Chave<br>Aleatória<br>E-mail<br> escuro<br> explicativo em Libras sobre o Pix<br>tar a fonte<br>Vídeo|om<br>  Manual<br>Pix Copia<br>e Cola<br>Pix com<br>QR Code<br>Receber Pix<br>Meus<br>limites<br>Pix<br>Automático<br>Extrato /<br>Devolução<br>as<br>es<br>10,00<br>r<br>Pagamento<br>via Chave<br>Roberto da Silva<br>R$3<br>Valor<br>J<br>AS TRANSAÇÕES<br>Celular<br>CPF<br>Chave<br>Aleatória<br>E-mail<br> escuro<br> explicativo em Libras sobre o Pix<br>tar a fonte<br>Vídeo|om<br>  Manual<br>Pix Copia<br>e Cola<br>Pix com<br>QR Code<br>Receber Pix<br>Meus<br>limites<br>Pix<br>Automático<br>Extrato /<br>Devolução<br>as<br>es<br>10,00<br>r<br>Pagamento<br>via Chave<br>Roberto da Silva<br>R$3<br>Valor<br>J<br>AS TRANSAÇÕES<br>Celular<br>CPF<br>Chave<br>Aleatória<br>E-mail<br> escuro<br> explicativo em Libras sobre o Pix<br>tar a fonte<br>Vídeo|
|||||
|om<br>  Manual<br>tar a fon|Pix Copia<br>e Cola<br>  te|Pix com<br>QR Code|Pix com<br>QR Code|






**Anexo I**


Itens a serem avaliados no processo de verificação de aderência das soluções
aos usuários finais.


**Observações:**

        - Os itens constantes no processo de verificação de
aderência das soluções aos usuários finais, bem como as
respectivas telas do projeto de aplicativo, devem ser
identificados e dispostos de acordo com ordem
apresentada na tabela constante neste anexo.


        - O cumprimento quanto aos demais itens constantes do
documento “Requisitos Mínimos para a Experiência do
Usuário” é obrigatório, não havendo tão somente a
necessidade de apresentação das telas no âmbito do
projeto de solução aos usuários finais.


#### Recomendações e OBRIGAÇÕES

Versão: 7.3

Dezembro de 2025
# 21



Versão: 7.3



Dezembro de 2025




-Inserção da obrigação 9.

                                     - Capítulos 3 (item 13), 4 (item 9), 6 (item 13) e 11 (item 14):

-Exclusão da obrigação de mencionar o canal de atendimento no comprovante de pagamento.

                                      - Capítulo 13:

-Substituição de referências a "link" por "código", com correspondente alteração nas ilustrações.

                                - Pequenos ajustes de forma ao longo do texto.


10/2020 2.0 - Inclusão do Capítulo 13 -"Pix Copia e Cola" e ajuste da numeração dos capítulos subsequentes.

                                    - Capítulos 3 e 4 (item 3):

-Inclusão de informação referente ao campo livre

-Formação da pacs.008.

                                     - Capítulo 3 (item 13):

-Inclusão de informação referente ao ID da Transação – EndtoEndID da pacs.008.

                                   - Capítulo 4 (item 09):

-Inclusão de informação referente ao ID da Transação – EndtoEndID da pacs.008.

                                    - Capítulo 6 (item 13):

-Inclusão de informação referente ao ID da Transação – EndtoEndID da pacs.008.

                                    - Capítulo 7 (item 4 e 6):

-Inclusão de informação referente ao ID da Transação – EndtoEndID da pacs.008.

                                      - Capítulo 11 (item 14):

-Inclusão de informação referente ao ID da Transação – EndtoEndID da pacs.008.

                                   - Novo Capítulo 13:

-Pix Copia e Cola: Disponibilização de opção ao usuário pagador, na interface de mobile banking, de colar atalho.

                                     - Capítulo 14:

-Pix em Internet Banking: Alteração do título do capítulo e numeração.



138




Data Versão Descrição das Alterações

11/2020 2.1 - Índice: -Correção do título do capítulo de “Recebimento” por “Pagamento” através de QR Code Dinâmico;

-Inserção do Anexo I - Itens a serem avaliados no processo de verificação de aderência das soluções aos usuários finais.

                                  - Obrigações Gerais (Página 6, item 01):

-Alteração da redação do item para “O ambiente Pix deve estar acessível, a qualquer tempo, no aplicativo principal de cada participante. Seu acesso deve

estar na tela de login ou na tela imediatamente após o login, com não menos destaque que qualquer outra funcionalidade de pagamento ou de

transferência”.

.• Capítulo 5 (item 02):

-Exclusão na tela de aplicativo da menção da quantidade de caracteres no campo “Descrição”.

                                   - Capítulo 5 (item 03):

-Inclusão de informação referente ao campo “Identificador”;

-Inclusão de informação referente ao campo “Descrição”; Exclusão nas telas de aplicativo da menção da quantidade de caracteres no campo “Descrição”.

                                   - Capítulo 05 (página 21):

-Alteração da expressão “copiar link” para “copiar código”.

                                    - Capítulo 13 (página 52, 53, 54 e 55):

-Alteração da palavra “atalho” pela palavra “código”.

                                   - Capítulo 13 (página 54):

-Alteração da expressão “copiar link” para “copiar código”.

                                   - Capítulo 14 (página 56, 58 e 59):

-Alteração da palavra “atalho” pela palavra “código”.

                                   - Capítulo 14 (página 58):

-Alteração da expressão “copie o link” para “copie o código”.

                                 - Anexo I: Itens a serem avaliados no processo de verificação de aderência das soluções aos usuários finais.

                                 - Histórico de Revisão: Inserção de tabela com histórico de versões e revisões do conteúdo.


12/2020 3.0 - Índice: -Inclusão do capítulo 10 – “Meus Limites Pix” e ajuste da numeração dos capítulos subsequentes;

-Alteração do título do Capítulo 11 para Pagamento imediato ou com vencimento através de QR Code dinâmico.

                                 - Obrigações Gerais:

-Página 7: item 09 – Alteração do texto; Exclusão do termo “Campo livre” presente na figura ilustrativa; Alteração da quantidade de caracteres do campo

Descrição (0 a 140 caracteres);

-Criação dos itens 10, 11 e 12, obrigatórios.

                                      - Capítulos 2, 6, 10, 11 e 13 (tela inicial do ambiente Pix)

-Inclusão do ícone “Meus Limites Pix”.

                                   - Capítulo 02: (item 07):

-Inclusão da nomenclatura obrigatória “Meus Limites Pix”.



139




Data Versão Descrição das Alterações


                                   - Capítulo 03:
12/2020 3.0

-Páginas 10, 11 e 12 - Exclusão do “Campo livre” presente nas figuras ilustrativas. Alteração dos termos “campo livre” para os termos “campo Descrição”.

-Página 10 – alteração do texto do item 03;

-Página 12 - alteração do texto do item 06; exclusão do campo “Instituição”;

-Página 14 – novo item 12 com nova redação; inclusão do item 14 recomendado, referente às Chaves Aleatórias.

                                    - Capítulo 04:

-Página 16 - itens 01 e 03: alteração dos termos “campo livre” para os termos “campo Descrição”;

-Página 18 - alteração do texto do item 07; exclusão do texto do item 08, original. Renumeração do item 09 para 08, acompanhado de novo texto;

                                   - Capítulo 05:

-Página 20 - inclusão na tela do aplicativo da menção da quantidade de caracteres no campo “Identificador” (0 a 25 caracteres);

-Páginas 20, 21 e 22 - exclusão do campo “Descrição”;

-Página 20 - Inclusão na tela do aplicativo da menção da quantidade de caracteres no campo “Identificador” (0 a 25 caracteres);

-Página 22 - item 07 torna-se obrigatório. Inserção de item 08, recomendado; Ajuste da figura, com a alteração do termo “Copiar Código” para “Copiar

Código QR”; exclusão do campo “Descrição”. Alteração do texto do item 03.

                                   - Capítulo 06:

-Páginas 24, 25 e 27 - exclusão do campo “Descrição”;

-Página 24 – ajuste do texto do item 01;

-Página 25 - alteração da palavra “Instituição” por “PSP” nas duas figuras da página;

-Página 28 – exclusão do item 12 original e remuneração do item 13 (anterior) para item 12.

                                   - Capítulo 08:

-Página 32 - alteração do texto de “Campo Livre” para “Descrição”;

-Página 33 – criação de novo item 06;

-Página 33: alteração do texto do agora item 07.

                                - Exclusão do capítulo 10 – Geração de QR Code Dinâmico.

                                   - Novo Capítulo 10:

-Meus Limites - Funcionalidade que permite aos usuários do Pix consultar, reduzir, bem como solicitar aumento do valor dos limites transacionais

disponibilizados.

Capítulo 11:

-Página 46 - Alteração do título e do conteúdo para Pagamento imediato ou com vencimento através de QR Code dinâmico - Trata-se de pagamento

iniciado pelo usuário pagador por meio da leitura de QR Code dinâmico;

-Páginas 47, 48, 49, 50 e 51 – alteração de itens e telas de forma a representar a experiência de pagamentos de QR Code dinâmico imediato e com

vencimento.

                                - Pequenos ajustes de forma.



140




Data Versão Descrição das Alterações


-Páginas 8, 10, 14, 16, 18 e 33: inclusão de obrigação referente ao campo “Descrição” - “O campo “Descrição” deve ser sanitizado de modo a neutralizar tags
01/2021 3.1

HTML inseguras.”

-Ajustes nas referências das páginas dos itens a serem avaliados no processo de verificação de aderência das soluções aos usuários finais.

-Ajuste no texto do histórico de revisão referente à versão 3.0 de 24.12.2020.

                                - Pequenos ajustes de forma.



141




Data Versão Descrição das Alterações


                                        - Índice:
03/2021 4.0 -Inclusão do capítulo 14 - “Integração com Lista de Contatos” e ajuste da numeração dos capítulos subsequentes.

                                  - Introdução:

-Página 04 - nova redação no segundo parágrafo da Introdução com o objetivo de informar que deve ser respeitado o Manual de Uso da Marca Pix no que

se refere às aplicações de marca Pix.

                                    - Capítulo 2:

-Página 06 - alterações no texto do item 01.

-Página 08 - alterações no texto dos itens 10 e 11.

                                    - Capítulo 4:

-Página 18 - alteração nas telas exemplificativas.

                                    - Capítulo 5:

-Página 22 - alteração nas telas exemplificativas.

                                    - Capítulo 6:

-Páginas 24, 25, 26, 27 e 28 - alteração nas telas exemplificativas.

-Página 28 - inclusão de novo item de número 13 – “O PSP não pode salvar a chave Pix nem deve disponibilizar opção de salvamento da chave Pix vinculada

ao pagamento do QR Code estático quando o TxId estiver preenchido.”

                                    - Capítulo 7:

-Página 30 - alteração na tela exemplificativa.

                                    - Capítulo 8:

-Página 32 - alterações no texto do item 02.

-Página 32 - alterações nas telas exemplificativas.

                                    - Capítulo 9:

-Página 37 - alterações no texto do item 02.

                                      - Capítulo 11:

-Página 47 - alteração nas telas exemplificativas com a inclusão do campo “InfoAdicionais”.

-Página 47 - alterações no texto dos itens 02 e 03.

-Página 49 – renumeração dos itens presentes no capítulo em conjunto com a exclusão do item 08 presente na versão 3.1.

-Páginas 49 e 50 - alteração nas telas exemplificativas com a inclusão do campo “InfoAdicionais”.

-Página 51 – inclusão de novo item de número 14 – “O PSP não pode salvar a chave Pix nem deve disponibilizar opção de salvamento da chave Pix vinculada

ao pagamento do QR Code dinâmico.”

-Página 51 - alteração nas telas exemplificativas.

                                     - Capítulo 12:

-Páginas 53 - alteração nas telas exemplificativas

                                     - Capítulo 13:

-Página 57 - alteração nas telas exemplificativas com a inclusão do campo “InfoAdicionais”.

                                - Novo Capítulo 14: Integração com Lista de Contatos - Funcionalidade que permite ao usuário identificar facilmente as pessoas na lista de contatos do seu

smartphone que possuem chaves Pix.

                                     - Anexo 1:

-Página 66: alteração no texto presente no item 1 (Pix com Chave Pix).

-Página 69: alteração no texto presente no item 2 (Devolução).

                                - Pequenos ajustes de forma.



142




Data Versão Descrição das Alterações


                                      - Capítulo 11:
03/2021 4.1 -Página 47: alteração no texto do item 01 - O valor (Caso o usuário recebedor informe que o valor pode ser alterado utilizando o campo “Modalidade de

alteração de valor”, conforme definido no Manual de Padrões para Iniciação do Pix, deve-se permitir a edição do valor pelo usuário pagador. Caso contrário,

                                  - valor não poderá ser editável).

-Página 47: alteração no texto do item 02 - Usuário pagador pode cancelar o pagamento, mas não pode editar os dados do QR Code, à exceção do valor

(caso permitido pelo usuário recebedor) e do campo de solicitação de informações ao pagador (se houver).

                                  - Pequenos ajustes de forma.



143




Data Versão Descrição das Alterações


                                     - Capítulo 2:
04/2021 4.2 -Página 8 – Inserção do novo item 10 referente à obrigação do participante em disponibilizar, no ambiente Pix, atalho (ícone, botão ou texto com hiperlink)

em que o usuário possa, ao clicar, ser direcionado para o canal de atendimento disponibilizado pelo PSP para o tratamento de reclamação envolvendo o Pix;

-Página 8 - Inserção do novo item 11 referente à obrigação do participante em disponibilizar, no ambiente Pix, atalho (ícone, botão ou texto com hiperlink) em

que o usuário possa, ao clicar, ser direcionado à página do Banco Central do Brasil na Internet para registro da reclamação (https://www.bcb.gov.br/

acessoinformacao/registrar_reclamacao);

-Página 8 – Inserção do novo item 12 referente à recomendação ao participante em deixar claro para o usuário que, antes de fazer uma reclamação no

Banco Central do Brasil, tente resolver o problema junto ao próprio PSP;

-Página 8 – Inclusão de figuras representativas de tela de celular em que constam a inserção de ícone que, ao ser acionado, direciona o usuário para

registro de reclamação;

-Página 9 – Item 13 (item 10 na versão 4.1) – inserção da obrigatoriedade de inclusão, na notificação de conclusão da transação, de informação referente à

tarifa cobrada, caso permitida nos termos da regulação vigente;

-Página 9 – Item 14 (item 11 na versão 4.1) – inserção da obrigatoriedade de inclusão, na notificação de conclusão da transação, de informação referente à

tarifa cobrada, caso permitida nos termos da regulação vigente.

                                      - Capítulo 11:

-Página 52 – item 15 – obrigatório – inserção de obrigação de que quando o usuário pagador agendar o pagamento do QR Dinâmico com vencimento, o PSP

deve disponibilizar a ele o comprovante de agendamento bem como consulta às transações agendadas;

-Página 52 – item 16 – obrigatório – inserção de obrigação de que deve ser ofertada ao usuário a funcionalidade de cancelamento da transação agendada;

-Página 52 – item 17 – obrigatório – inserção de obrigação de que caso a transação agendada seja cancelada por insuficiência de saldo na conta do

usuário, o usuário deve receber notificação do cancelamento. A forma de envio da notificação é de livre escolha do PSP. Caso a notificação seja via push,

parte das informações, à escolha do PSP, pode estar detalhada quando o usuário clicar na notificação.

                                     - Capítulo 12:

-Página 54 – Item 02 – recomendado – recomendação ao PSP para que encaminhe notificação um dia antes da data do débito do Pix Agendado

informando ao usuário quanto à necessidade de existência de saldo em conta;

-Página 54 – item 05 – obrigatório – inserção de obrigação de que caso a transação agendada seja cancelada por insuficiência de saldo na conta do

usuário, o usuário deve receber notificação do cancelamento. A forma de envio da notificação é de livre escolha do PSP. Caso a notificação seja via push,

parte das informações, à escolha do PSP, pode estar detalhada quando o usuário clicar na notificação;

-Página 54 – item 06 – obrigatório – inserção de obrigação de que deve ser ofertada ao usuário a funcionalidade de cancelamento da transação agendada.

                                     - Anexo I:

-Página 67 – Anexo I – Inserção dos itens 05 e 06, referentes aos itens a serem avaliados no processo de verificação de aderência das soluções aos usuários

finais.

                                - Pequenos ajustes de forma e de referência aos itens constantes no Manual.



144




Data Versão Descrição das Alterações


                                   - Capítulo 02:
05/2021 4.3 -Página 08 – consolidação dos itens 11 e 12 em um novo item 11 obrigatório, o qual dispõe que “Deve ser disponibilizada, no ambiente Pix, junto ao atalho para

                               - canal de atendimento do participante, mensagem informativa ao usuário para que este possa registrar reclamação no site do Banco Central do Brasil

(https://www.bcb.gov.br/acessoinformacao/registrar_reclamacao) caso a ocorrência não seja resolvida pelo PSP.

-Página 08 – Alteração das telas representativas da experiência do usuário quando do encaminhamento para registro de uma reclamação.

                                      - Capítulo 12:

-Página 54 – Alteração das telas representativas da experiência do usuário quando do agendamento de um Pix.

-Página 54 – inserção de novo item 02: “Pode ser disponibilizado ao usuário pagador a opção de agendamento de pagamentos recorrentes”.

                                     - Anexo I:

-Página 67 - Alteração do Anexo I (item 06) em função das alterações promovidas no capítulo 02 - Obrigações e Recomendações Gerais

                                - Pequenos ajustes de forma e de referência aos itens constantes no Manual.



145




Data Versão Descrição das Alterações


                                     - Capítulo 2:
07/2021 4.4 -Página 09 – item 12: inserção de informação referente à notificação de liquidação de transação agendada. “Nas transações de Pix Agendado, o usuário

recebedor deve receber notificação da liquidação da transação, sendo a forma de envio da notificação de livre escolha do PSP. A notificação deve conter as

mesmas informações discriminadas para as transações Pix com chave ou inserção manual de dados e, preferencialmente, ser enviada em período diurno.”

-Página 09 – item 13: inserção de informação referente à notificação de liquidação de transação agendada. “Nas transações de Pix Cobrança para

pagamento com vencimento em que houver agendamento, o usuário recebedor deve receber notificação da liquidação da transação, sendo a forma de

envio da notificação de livre escolha do PSP. A notificação deve conter as mesmas informações discriminadas para as transações Pix com QR Code e,

preferencialmente, ser enviada em período diurno.”

                                     - Capítulo 3:

-Página 16 – item 11: inserção de informação referente à notificação de liquidação de transação agendada. “Nas transações de Pix Agendado, o usuário

pagador deve receber notificação da liquidação da transação, sendo a forma de envio da notificação de livre escolha do PSP. A notificação deve conter as

mesmas informações discriminadas acima e, preferencialmente, ser enviada em período diurno.”

                                     - Capítulo 4:

-Página 21 – item 07: inserção de informação referente ao horário de notificação de liquidação de transação agendada. “Nas transações de Pix Agendado, o

usuário pagador deve receber notificação da liquidação da transação, sendo a forma de envio da notificação de livre escolha do PSP. A notificação deve

conter as mesmas informações discriminadas acima e, preferencialmente, ser enviada em período diurno.”

                                       - Capítulo 11:

-Página 54 – item 12: inserção de informação referente à notificação de liquidação de transação agendada. “Nas transações de Pix Cobrança para

pagamento com vencimento em que houver agendamento, o usuário pagador deve receber notificação da liquidação da transação, sendo a forma de

envio da notificação de livre escolha do PSP. A notificação deve conter as mesmas informações discriminadas acima e, preferencialmente, ser enviada em

período diurno.”

                                 - Pequenos ajustes de forma.



146




Data Versão Descrição das Alterações


                                      - Índice:
08/2021 5.0 - Inclusão do capítulo 15 – “Serviços de iniciação de transação de pagamento no Pix” e ajustes de numeração dos capítulos subsequentes;

                                 - Inclusão do capítulo 17 – “Acessibilidade no Pix” e ajustes de numeração dos capítulos subsequentes;

                                 - Inclusão do Anexo II – “Prazos de implementação vigentes relativos às funcionalidades obrigatórias dos Requisitos Mínimos para a Experiência do Usuário.”;

                                      - Capítulo 1:

-Página 04: novo parágrafo quarto destinado aos prestadores de serviço de iniciação de transação de pagamento (PSIs) e novo parágrafo quinto referente

ao tratamento não discriminatório aos usuários no que se refere à acessibilidade;

                                    - Capítulo 2:

-Página 07 – item 07: correção das indicações nas telas exemplificativas;

-Página 10 – item 14: nova redação (inserção de PSI como participante);

                                     - Capítulo 3:

                                  - Página 16 – item 12: exclusão da indicação do item na tela exemplificativa;

                                     - Capítulo 7:

-Página 32 - item 05: novo item recomendado(transações iniciadas pelo PSI);

                                    - Capítulo 9:

-Página 40 - item 05: exclusão das indicações do item na tela exemplificativa;

                                     - Capítulo 12:

-Página 55 – item 01: novo item obrigatório (opção de agendamento);

-Página 55 – item 03: nova redação para o item (consulta a agendamentos);

                                  - Página 55 – itens 02, 04 e 05: renumeração de itens obrigatórios;

-Página 55 – itens 06 e 07: renumeração dos itens recomendados;

                                  - Inclusão do Capítulo 15

                                - Páginas 62 a 65 – “Serviço de iniciação de transação de pagamento no Pix” e ajuste da numeração dos capítulos subsequentes;

                                   - Inclusão do capítulo 17

                                 - Páginas 71 e 72 - “Acessibilidade no Pix” e ajustes de numeração dos capítulos subsequentes;

                                     - Anexo I:

                                 - Página 77 – novo item obrigatório (Pix Agendado);

                                  - Alterações nas interfaces das telas exemplificativas.

                                - Pequenos ajustes de forma.



147




Data Versão Descrição das Alterações


                                      - Índice:
09/2021 6.0 -Inclusão do novo capítulo 14 - “Pix Saque e Pix Troco” e ajustes de numeração dos capítulos subsequentes;

-Reposicionamento do capítulo “Integração com Lista de Contatos”, que agora passa a se situar após o capítulo 15 - “Serviços de iniciação de transação de

pagamento no Pix”;

                                   - Capítulo 02:

-Página 07 - item 07: inclusão das nomenclaturas “Pix Saque” e “Pix Troco”;

-Página 08 - item 11: exclusão da URL e do link da página do Banco Central na tela exemplificativa, e reposicionamento da mensagem informativa sobre o

registro de reclamações no site do Banco Central, após o atalho para o canal de atendimento do participante;

                                   - Capítulo 03:

-Página 12 - item 02: inclusão do código DDI +55 como padrão para a chave de número de telefone celular;

                                   - Capítulo 07:

-Página 32 - item 01: inclusão dos saques no rol de transações Pix;

                                     - Capítulo 13:

-Página 57 - item 02: inclusão de saques de recursos em espécie como opção de rápido e fácil acesso ao usuário no aplicativo de mobile banking do PSP;

                                  - Inclusão do novo Capítulo 14:

-Páginas 60 a 67: ajuste da numeração dos capítulos e páginas subsequentes;

-Ajuste da numeração dos capítulos e páginas subsequentes;

-Página 85: alteração no texto do item 01 (capítulo Extrato), incluindo os saques entre as transações Pix;

                                  - Alterações nas interfaces das telas exemplificativas.

                                - Pequenos ajustes de forma.



148




Data Versão Descrição das Alterações

                                      - Índice:
10/2021 6.1 -Renumeração das páginas a partir do Capítulo 10 - Meus Limites, em função de alterações e inserção de novos conteúdos.

                                     - Capítulo 10:

-Páginas 45 a 53- inclusão de novas funcionalidades que permitam ao usuário consultar e gerenciar os limites do Pix por período e por transação, inclusive

para Pix Saque e Pix Troco, e cadastrar contas com limites diferenciados.

                                     - Anexo I:

-Página 91 - inclusão do item 01, página 46, do Capítulo 10 - Meus Limites.

                                  - Alterações nas interfaces das telas exemplificativas.

                                - Pequenos ajustes de forma.


                                   - Capítulo 07:
12/2021 6.2 -Página 32 - inclusão de novo item 02: obrigatoriedade referente à forma de lançamento de transações Pix Troco nos extratos e renumeração dos itens

subsequentes.

-Página 32 - alteração da tela exemplificativa associada ao item 01, que também passa a ser associada ao novo item 02.

                                     - Capítulo 10:

-Página 46 - item 01 e 02: inclusão do gerenciamento de limites por tipo de beneficiário.

-Página 46 - item 02: mudança do início do período noturno que pode ser alterado pelo usuário.

-Página 51 - item 08: mudança do início do período noturno que pode ser alterado pelo usuário.

-Página 51 - Alteração da tela exemplificativa associada ao item 8.

                                     - Capítulo 14:

-Página 66 - alteração do termo “ofertar” por “disponibilizar”;

-Página 67 - item 01: ajustes na redação (inclusão de correspondentes bancários);

-Página 67 - alteração das telas exemplificativas associadas ao item 01;

-Página 68 - item 03: ajustes na redação (informações referentes aos locais em que o Pix Saque e o Pix Troco são disponibilizados);

-Página 68 - item 04: ajustes na redação (substituição de “serviço” por “Pix Saque e/ou Pix Troco);

-Página 69 - item 05: ajustes na redação (substituição de “serviço” por “Pix Saque e/ou Pix Troco);

-Página 69 - ajuste da tela associada ao item 05;

-Página 70 - item 11: ajustes na redação (substituição de “serviço” por “Pix Saque e/ou Pix Troco) e exclusão do “valor final da transação”;

-Página 71 - item 14: ajustes na redação (substituição de “serviço” por “Pix Saque e/ou Pix Troco), inclusão do termo “nome” como informação associada ao

PSP do recebedor e exclusão do “valor final da transação”; e

-Página 72 - item 16: ajustes na redação (inclusão do termo “nome” como informação associada ao PSP do recebedor).

                                     - Anexo I:

-Página 91 - alteração do item 01 do Capítulo “Meus Limites Pix”

                                  - Alterações nas interfaces das telas exemplificativas.

                                - Pequenos ajustes de forma.



149




Data Versão Descrição das Alterações

                                      - Índice:
10/2022 6.3 -Renumeração das páginas a partir do Capítulo 3 - Pix com Chave Pix, em função de alterações e inserção de novos conteúdos.

                                - Exclusão do Anexo II (Capítulo 20), dado que os prazos de implementação das funcionalidades obrigatórias serão disciplinados em Instrução Normativa,

publicada a cada atualização dos requisitos mínimos para a Experiência do usuário.

                                   - Capítulo 02:

-Página 8 - item 10: inclusão de referência ao Mecanismo Especial de Devolução, que deve ser acionado por meio do canal de atendimento disponibilizado

pelo PSP;

-Página 9 - item 12: exclusão da informação do nome do PSP do pagador como informação mínima nas notificações ao recebedor das transações Pix

iniciadas com chave ou inserção manual de dados;

-Página 9 - item 12: alterações referentes à sanitização do campo “Descrição”;

-Página 9 - item 13: exclusão da informação do nome do PSP do pagador como informação mínima nas notificações ao recebedor das transações Pix

iniciadas com chave ou inserção manual de dados;

-Página 10 - item 15 (novo): vedação à exibição da chave Pix entre os dados retornados do DICT, nem salvar ou disponibilizar a opção de salvamento, quando

                                   - txId estiver preenchido.

                                   - Capítulo 03:

-Página 12 - item 03: alterações referentes à sanitização do campo “Descrição”;

-Página 14 - item 06: retorno da informação do nome do PSP do recebedor passa ser opcional nas transações iniciadas por chave;

-Página 14 - item 06: retorno da informação da chave Pix passa a ser obrigatória nas transações iniciadas por chave;

-Página 15 - item 09: ajuste no texto para que, nas mensagens de erro na liquidação, seja evidenciado o efetivo motivo do não processamento da transação;

-Página 16 - item 11: nome do PSP do recebedor deixa de ser informação mínima nas notificações; e

-Página 16 - item 12: inclusão das informações do CPF (mascarado ou não) / CNPJ do recebedor e das informações (nome, CPF (mascarado ou não) / CNPJ

e nome do PSP) da ponta pagadora no comprovante, que deve ser disponibilizado para os usuários pagador e recebedor.

                                 - Capítulo 04

-Página 19 - item 01: vedação à exibição dos nomes dos participantes liquidantes especiais na lista de instituições participantes e esclarecimentos sobre o

número associado a cada PSP;

-Página 19 - tela exemplificativa do item 01: inclusão do tipo de conta “conta de pagamento”;

-Página 19 - item 03: alterações referentes à sanitização do campo “Descrição”;

-Página 20 - item 05: ajuste no texto para que, nas mensagens de erro na liquidação, seja evidenciado o efetivo motivo do não processamento da transação;

-Página 21 - item 07: obrigatoriedade de fornecer o CPF (mascarado)/CNPJ do recebedor, nas notificações de transações iniciadas por inserção manual;

-Página 21 - item 07: nome do PSP do recebedor deixa de ser informação mínima nas notificações;

-Página 21 - item 08: inclusão das informações do CPF (mascarado ou não) / CNPJ do recebedor e das informações (nome, CPF (mascarado ou não) / CNPJ

e nome do PSP) da ponta pagadora no comprovante, que deve ser disponibilizado para os usuários pagador e recebedor; e

-Página 21 - item 08: alterações referentes à sanitização do campo “Descrição”.



150




Data Versão Descrição das Alterações

                                   - Capítulo 05:
10/2022 6.3 -Página 25 - item 07 (item 08 da versão anterior): fornecimento da opção de Copiar Código QR para viabilizar a funcionalidade Pix Copia e Cola deixa de ser

uma recomendação e passa a ser uma obrigatoriedade.

                                   - Capítulo 06:

-Página 27 - item 01: retorno da informação do nome do PSP do recebedor passa ser opcional e fica a critério do participante;

-Página 27 - item 01: inclusão da obrigatoriedade da opção “Cancelar”, antes da confirmação da transação (já consta na tela exemplificativa associada ao

item);

-Página 27 - item 01: vedação à disponibilização do campo “Descrição” (“informacoesEntreUsuarios” da pacs.008) para preenchimento do usuário pagador

nas transações iniciadas por QR Code estático;

-Página 29 - item 07: ajustes no texto referente a erros de chave não existente no QR Code estático;

-Página 30 - item 09: ajuste no texto para que, nas mensagens de erro na liquidação, seja evidenciado o efetivo motivo do não processamento da transação;

-Página 31 - item 12: nome do PSP do recebedor deixa de ser informação mínima nas notificações; e

-Página 31 - item 12: inclusão das informações do CPF (mascarado ou não) / CNPJ do recebedor e das informações (nome, CPF (mascarado ou não) / CNPJ e

nome do PSP) da ponta pagadora, e do campo “Identificador” (TxId), sempre que estiver preenchido, como informações mínimas do comprovante, que deve

ser disponibilizado para os usuários pagador e recebedor.

                                   - Capítulo 07:

-Página 33 - item 05: ajustes no texto referente à recuperação dos comprovantes, excluindo as informações mínimas, que são especificadas nos itens sobre

comprovantes para cada forma de iniciação.

                                   - Capítulo 08:

-Página 35 - item 02: inclusão do valor da transação entre as informações mínimas que o usuário deve visualizar para poder selecionar a opção de

devolução;

-Página 35 - item 03: item deixa de ser recomendado e passa a ser obrigatório;

-Página 36 - item 07: ajustes no texto para inclusão das informações do CPF (mascarado ou não) /CNPJ do destinatário e ID da transação de devolução no

comprovante, em aderência à tela exemplificativa do item;

-Página 36 - item 07: alterações referentes à sanitização do campo “Descrição”;

-Página 37 - item 09: ajustes no texto, incorporando parte do conteúdo antigo item 11 da versão anterior, consolidando todas as orientações referentes a

mensagens de erro de liquidação em transações de devolução;

-Página 38 - item 11 (novo): obrigatoriedade de, no caso de bloqueio cautelar, o PSP do recebedor disponibilizar a possibilidade de devolução total dos

recursos pelo usuário recebedor;

-Página 38 - item 12 (novo): obrigatoriedade de o usuário recebedor da transação original ser imediatamente notificado sobre o bloqueio cautelar, e

informações mínimas da notificação;

-Página 38 - item 13 (novo): obrigatoriedade de o usuário recebedor da transação original ser imediatamente notificado sobre o bloqueio decorrente de

abertura de uma notificação de infração associada a uma solicitação de devolução, e informações mínimas da notificação;

-Página 38 - item 14 (novo): obrigatoriedade de o usuário recebedor da transação original ser imediatamente notificado sobre a liberação de recursos na

sua conta após a realização de um bloqueio, e informações mínimas da notificação;

-Página 38 - item 15 (novo): obrigatoriedade de o usuário recebedor da transação original ser imediatamente notificado, caso os recursos bloqueados

tenham sido efetivamente devolvidos, e informações mínimas da notificação; e



151




Data Versão Descrição das Alterações

-Página 38 - item 16 (novo): obrigatoriedade de o usuário pagador da transação original ser imediatamente notificado sobre o crédito em sua conta
10/2022 6.3 decorrente de uma devolução, e informações mínimas da notificação;

                                   - Capítulo 09:

-Página 40 - item 02: a informação do nome do PSP ao qual a chave está vinculada deixa de ser uma informação mínima visualizada pelo usuário pagador

que tem conhecimento da chave, e ajustes no texto;

-Página 42 - item 08: alteração da informação do prazo de finalização do processo de reivindicação de posse de 14 para 30 dias;

-Página 43 - item 10: ajustes referentes à comunicação do início do processo de portabilidade e na tela exemplificativa; e

-Página 45 - item 12: ajustes no texto referentes às mensagens em caso de falha de comunicação com o DICT para registro, exclusão, alteração, solicitação

de portabilidade ou reivindicação de chave.

                                      - Capítulo 11:

-Página 56 - item 01: vedação ao retorno das informações do número da agência e do número da conta do recebedor ao usuário pagador, assim como já

ocorre para as transações de pagamento por meio de QR code estático;

                                - Página 56 - item 01: retorno da informação do nome do PSP do recebedor antes da confirmação do pagamento imediato passa ser opcional e fica a critério

do participante;

                                - Página 56 - item 01: vedação à disponibilização do campo “Descrição” (“informacoesEntreUsuarios” da pacs.008) para preenchimento do usuário pagador,

nas transações de pagamento imediato iniciadas por QR Code dinâmico;

-Página 57 - item 03: inserção do campo “data de vencimento” na tela retornada após a leitura de um Pix Cobrança para pagamento com vencimento e

alterações referente à indicação da data de pagamento pretendida;

-Página 57 - item 03: vedação ao retorno das informações do número da agência e do número da conta do recebedor ao usuário pagador, assim como já

ocorre para as transações de pagamento por meio de QR code estático;

-Página 57 - item 03: retorno da informação do nome do PSP do recebedor antes da confirmação do pagamento com vencimento passa ser opcional e fica

a critério do participante;

-Página 57 - item 03: ajustes no texto referente ao campo “infoAdicionais”;

-Página 57 - item 03: vedação à disponibilização do campo “Descrição” (“informacoesEntreUsuarios” da pacs.008) para preenchimento do usuário pagador,

nas transações de pagamento com vencimento iniciadas por QR Code dinâmico;

-Página 58 - item 06: item deixa de ser recomendado e passa a ser obrigatório;

-Página 59 - item 09: ajuste no texto de mensagem em caso de expiração do QR Code dinâmico;

-Página 60 - item 11: ajuste no texto para que, nas mensagens de erro na liquidação, seja evidenciado o efetivo motivo do não processamento da transação;

-Página 61 - item 12: nome do PSP do recebedor deixa de ser informação mínima nas notificações;

-Página 61 - item 13: inclusão das informações do CPF (mascarado ou não) / CNPJ do recebedor e das informações (nome, CPF (mascarado ou não) / CNPJ e

nome do PSP) da ponta pagadora, e do campo “Identificador” (TxId), sempre que estiver preenchido no comprovante, que deve ser disponibilizado para os

usuários pagador e recebedor; e

-Página 61 - item 17: ajustes no texto referente à não efetivação de transação agendada, em função de insuficiência de saldo na conta do usuário.



152




Data Versão Descrição das Alterações

10/2022 6.3 Capítulo 12:-Página 63 - item 01: ajuste no texto, esclarecendo que os pagamentos podem ser agendados para dias não úteis;

-Página 63 - item 02: ajustes no texto e tela exemplificativa, para que o comprovante destaque expressamente que é referente a um agendamento de

transação Pix.

-Página 63 - item 05: ajustes no texto referente à não efetivação de transação agendada, em função de insuficiência de saldo na conta do usuário.

-Página 63 - item 05: ajustes no texto referente à não efetivação de transação agendada, em função de insuficiência de saldo na conta do usuário.

                                     - Capítulo 14:

                                 - Página 71 - item 06: alterações referentes à sanitização do campo “Condições de disponibilização do serviço de saque”;

-Página 72 - item 11: alterações referentes à sanitização do campo “infoAdicionais”;

-Página 73 - item 14: alterações referentes à sanitização do campo “infoAdicionais”;

-Página 74 - item 16: alterações referentes à sanitização do campo “infoAdicionais”; e

-Página 75 - item 19: alterações nas informações mínimas dos comprovantes das transações Pix Saque e Pix Troco.

                                     - Capítulo 15:

-Página 81 - item 15 (novo): obrigatoriedade de o prestador do serviço de iniciação de transação de pagamento cumprir os requisitos referentes ao conjunto

de dados que deve ser informado ao usuário pagador antes da confirmação do pagamento, para cada forma de iniciação;

-Página 82 - item 16 (novo): padronização do conjunto de dados que deve ser informado ao usuário pagador pelo prestador do serviço de iniciação de

transação de pagamento e pelo participante detentor da conta transacional, nos casos em que o prestador do serviço de iniciação de transação de

pagamento possui todas as informações do usuário recebedor.

                                     - Capítulo 17:

-Página 87: ajustes das informações do payload da tela exemplificativa; e

-Página 88 - item 02 (novo): obrigatoriedade de exibição das informações do payload do QR dinâmico, para pagamentos com vencimento no Internet

Banking.

                                   - Anexo I

-Página 8: ajustes no item 10 - inclusão de referência ao Mecanismo Especial de Devolução;

-Página 12: alteração do item 3 - sanitização do campo “Descrição;

-Página 14: alteração do item 6 - retorno da informação do nome do PSP do recebedor passa ser opcional nas transações iniciadas por chave;

-Página 16: alteração do item 12 - obrigatoriedade das informações do CPF (mascarado ou não) / CNPJ do recebedor e das informações (nome, CPF

(mascarado ou não) / CNPJ e nome do PSP) da ponta pagadora no comprovante, que deve ser disponibilizado para os usuários pagador e recebedor, e

alterações referentes à sanitização do campo “Descrição”;

-Página 19: alteração do item 1 - vedação à exibição dos nomes dos participantes liquidantes especiais na lista de instituições participantes e

esclarecimentos sobre o número associado a cada PSP;

-Página 21: alteração do item 8 - obrigatoriedade das informações do CPF (mascarado) / CNPJ do recebedor e das informações (nome, CPF (mascarado ou

não) / CNPJ e nome do PSP) da ponta pagadora no comprovante, que deve ser disponibilizado para os usuários pagador e recebedor, e alterações

referentes à sanitização do campo “Descrição”;



153




Data Versão Descrição das Alterações

10/2022 6.3 -Página 25: alteração do item 7 (item 08 da versão anterior) - fornecimento da opção de Copiar Código QR para viabilizar a funcionalidade Pix Copia e Cola

deixa de ser uma recomendação e passa a ser uma obrigatoriedade;

-Página 31 - item 12: inclusão das informações do CPF (mascarado ou não) / CNPJ do recebedor e das informações (nome, CPF (mascarado ou não) / CNPJ e

nome do PSP) da ponta pagadora no comprovante, que deve ser disponibilizado para os usuários pagador e recebedor;

-Página 31 - item 12: inclusão da informação da mensagem do campo “Identificador” (TxId) no comprovante, que deve ser disponibilizado para os usuários

pagador e recebedor;

-Página 35: alteração do item 2 - inclusão do valor da transação entre as informações mínimas que o usuário deve visualizar para selecionar a opção de

devolução;

-Página 40: alteração do item 2 - a informação do nome do PSP ao qual a chave está vinculada deixa de ser uma informação mínima visualizada pelo

usuário pagador que tem conhecimento da chave; e

-Página 63: ajuste no item 1 - agendamento deve ser disponibilizado também para pagamentos nos dias não úteis.

                                  - Alterações nas interfaces das telas exemplificativas.

                                - Pequenos ajustes de forma.


07/2023 6.4 - Capítulo 9:

                                 - Página 45: alterações no item 14 - obrigatoriedade de informar ao usuário, nas tentativas de registro, exclusão, alteração, portabilidade ou reivindicação de

chaves em horário no qual o participante não disponibilize essas funcionalidades, sobre o prazo previsto para efetivação ou o horário em que a

funcionalidade

estará disponível.

                                     - Capítulo 10:

-Página 47: ajustes no item 1 - fim dos limites por transação e nova funcionalidade de cadastro de beneficiários com limites diferenciados; obrigatoriedade

de disponibilização do menu “Meus Limites Pix” no ambiente Pix e de pelo menos uma das funcionalidades de cadastro de limites específicos (contas e

beneficiários);

                                - Página 47: ajustes no item 2 - menu “Meus Limites Pix” deve conter informações sobre limites por período em transações para pessoas e empresas, e sobre

cadastro de beneficiários, caso essa funcionalidade seja disponibilizada pelo PSP; obrigatoriedade de disponibilização de pelo menos uma das

funcionalidades de cadastro de limites específicos (contas e beneficiários)

                                 - Página 47: alterações no item 2 - limites de Pix Saque e Pix Troco foram alterados de R$ 500,00 para R$ 3.000,00 no período diurno e de R$ 100,00 para R$

1.000,00 no período noturno;

                                 - Página 47: alteração no item 2 - a funcionalidade de gestão de horários deixa de ser obrigatória;

                                  - Página 48: item 3 - ajuste na tela exemplificativa; exclusão da consulta e da edição de limites por transação;

                                - Página 48: ajustes no item 4 - maior clareza sobre a necessidade de aprovação do PSP nas solicitações de limites maiores do que os disponibilizados para

alterações;

                                - Página 49: ajustes no item 5 - maior clareza sobre a informação do prazo de processamento para qualquer solicitação de aumento de limite e de eventual

necessidade de aprovação do PSP, nos casos em que o limite solicitado for maior do que o valor do parâmetro regulamentado pelo BCB, conforme período

(diurno ou noturno) e usuário recebedor (pessoa física ou jurídica);



154




Data Versão Descrição das Alterações

07/2023 6.4 - Página 51: alterações no item 7 - maior clareza sobre a impossibilidade de o usuário solicitar aumento de limites Pix Saque Pix Troco para valores

superiores aos regulamentados pelo BCB; limites  de Pix Saque e Pix Troco foram alterados de R$ 500,00 para R$ 3.000,00 no  período diurno e de R$ 100,00

para R$ 1.000,00 no período noturno;

-Página 52: alteração no item 8 (antigo  item 9) - a funcionalidade de cadastro de contas não permite mais o limite  diferenciado por transação;

-Página 52: ajustes no item 8 (antigo item  9) - maior clareza sobre a faculdade de disponibilizar a funcionalidade de  cadastro de contas com limites

diferenciados e possibilidade de utilização de  um limite aplicável a todas as contas cadastradas; e alteração na tela  exemplificativa, considerando um

único limite diário para cada conta  cadastrada.

-Página 52: ajustes no item 10 (antigo item  11) - a funcionalidade de cadastro de contas deve permitir a fácil alteração  dos limites cadastrados;

-Página 53: inclusão dos itens 11, 12 e 13  - requisitos para a funcionalidade de cadastro de beneficiários, caso seja  disponibilizada pelo PSP;

-Página 54: novo item 14: obrigatoriedade  de informar ao usuário sobre eventuais impossibilidades de cadastro de  limites específicos para contas e

beneficiários, se houver incompatibilidade  com limites pré-cadastrados, caso o PSP disponibilize ambas as funcionalidades  de cadastramento de limites

(contas e beneficiários)

-Página 55: Novo item 15 (antigo item 8)

-Página 55: Novo item 16 - obrigatoriedade  de informar ao usuário sobre o prazo de alteração do início do horário  noturno, caso o PSP disponibilize essa

funcionalidade.

                                     - Anexo I:

-Página 47: ajustes no item 1 – fim dos  limites por transação e nova funcionalidade de cadastro de beneficiários com  limites diferenciados; obrigatoriedade

de disponibilização do menu “Meus  Limites Pix” no ambiente Pix e de pelo menos uma das funcionalidades de  cadastro de limites específicos (contas e

beneficiários);

                                   - Alterações nas interfaces das telas exemplificativas.

                                - Pequenos ajustes de forma.



155




Data Versão Descrição das Alterações

08/2024 7.0 - Índice:

                              - Reposicionamento do capítulo “Pagamento imediato ou com vencimento através de QR Code dinâmico” do capítulo 11 para o capítulo 07 e ajustes da

numeração dos capítulos subsequentes;

                                - Inclusão do novo capítulo 15 – “Pix Automático” e ajustes da numeração dos capítulos subsequentes.

                                     - Capítulo 01:

                               - Página 04 - Introdução: alteração na menção ao número do capítulo que trata do serviço de iniciação de transação de pagamento (de capítulo 15 para

capítulo 16).

                                    - Capítulo 02:

                                - Página 07 – item 07: inclusão do Pix Agendado e do Pix Automático nas nomenclaturas obrigatórias;

                                 - Página 08 – item 10: ajustes na redação de forma a evidenciar a obrigatoriedade de acesso fácil e direto ao canal de atendimento para fins de registro de

reclamações no âmbito do Pix;

                                 - Página 09 – itens 12 e 13: alteração do destinatário dos requisitos (de PSP do usuário pagador para PSP do usuário recebedor);

                                - Página 10 – item 16 (novo): inclusão de obrigatoriedade de apresentação de ícone do tipo “check” nos comprovantes de pagamento;

                                - Página 10 – item 17 (novo): inclusão de obrigatoriedade de apresentação das informações e ícones (“check” ou “calendar clock”) constantes das telas de

conclusão das jornadas de pagamento e agendamento nos respectivos comprovantes.

                                   - Capítulo 03:

                                - Página 16 – item 11: ajustes na redação (apresentação das informações de forma mais resumida, com migração de parte do texto para o capítulo 12 – “Pix

Agendado”,  com alterações).

                                    - Capítulo 04:

                                 - Página 19 – item 02: ajustes na redação (exclusão de “caso o PSP possua essa informação (por exemplo, se o usuário recebedor for seu cliente”);

                                - Página 21 – item 07: ajustes na redação (apresentação das informações de forma mais resumida, com migração de parte do texto para o capítulo 12 – “Pix

Agendado”, com alterações, e substituição do CPF/CNPJ pelo nome do recebedor).

                                   - Capítulo 07:

                                - Página 38 – item 12: ajustes na redação (apresentação das informações de forma mais resumida, com migração de parte do texto para o capítulo 12 – “Pix

Agendado”, com alterações);

                                 - Página 38 – item 13: ajustes na redação (referências ao payload do QR Code dinâmico e à tela com exemplo ilustrativo);

                                  - Migração dos itens 15, 16 e 17 para o capítulo 12 –“ Pix Agendado” (com alterações).

                                   - Capítulo 08:

                                 - Página 40 – item 03 (novo): inclusão de obrigatoriedade de identificação do Pix Agendado no extrato da conta e, caso disponibilizado, no extrato Pix;

                                 - Página 40 – item 04 (novo): inclusão de obrigatoriedade de identificação do Pix Automático no extrato da conta e, caso disponibilizado, no extrato Pix, e

ajustes da numeração dos itens subsequentes;

                               - Página 40 – item 07: inclusão de recomendação de recuperação dos comprovantes de agendamento na funcionalidade de extrato;

                                 - Página 40: inclusão de exemplos de transações Pix Agendado, Pix Agendado recorrente e Pix Automático nas telas ilustrativas.

                                      - Capítulo 11:

                                - Página 53 – exclusão de “por período” e inclusão de menção ao Pix Agendado e ao Pix Automático no subtítulo do capítulo;

                                - Página 54 – item 01: exclusão de “por período” e inclusão de menção ao Pix Agendado e ao Pix Automático;

                                - Página 54 – Item 02: exclusão de “por período (diurno e noturno)” no tópico “Pix para empresas” e inclusão de informações relativas ao Pix Agendado e ao

Pix Automático. Acréscimo do termo “diários” aos limites e inclusão de frase para fazer referência a opção de limite global diário diferenciado nas

informações sobre cadastro de beneficiários e cadastro de contas;

                                 - Página 55 – Item 03: inclusão do Pix Agendado e Pix Automático na consulta e alteração de limites;

                                - Página 55 – Item 04: inclusão do Pix Agendado e Pix Automático na permissão de solicitação de aumento de limite;

                                - Página 56 – Item 05: inclusão de exceção no prazo de 24 a 48 horas para processamento de solicitação de aumento de limite no caso do Pix Automático.



156




Data Versão Descrição das Alterações

08/2024 7.0 - Capítulo 11:

                                - Página 56 - Item 06 (novo): inclusão de obrigatoriedade de comunicação ao usuário pagador sobre o prazo de 8 horas para processamento da solicitação

de aumento de limite para o Pix Automático, sujeito à aprovação do PSP, e ajustes da numeração dos itens subsequentes;

                               - Página 57 – item 08 (novo): inclusão de obrigatoriedade de comunicação ao usuário pagador caso solicitações de redução de limite do Pix Agendado

resultem na inviabilização da liquidação de agendamentos já programados, inclusão de tela exemplificativa e ajustes da numeração dos itens

subsequentes;

                                 - Página 59 – item 10: inserido o termo “diário” na menção ao limite diferenciado aplicável a todas as contas cadastradas;

                                 - Página 60 – item 13: inserido o termo “diário” na menção ao limite diferenciado aplicável a todos os beneficiários cadastrados;

                                  - Páginas 54, 55, 59, 60 e 62: ajustes nas telas para inclusão do Pix Agendado e do Pix Automático.

                                     - Capítulo 12:

                               - Páginas 64 a 69: reformulação geral do capítulo, com ajustes de redação e inclusão de novos itens para tratar do Pix Agendado recorrente, do limite

específico para transações agendadas e de aprimoramentos realizados nos comprovantes de agendamento, assim como para considerar informações

sobre o envio de notificação após a liquidação da transação agendada antes existentes no capítulo 03 – “Pix com Chave Pix”, no capítulo 04 – “Pix com

inserção manual dos dados de conta transacional” e no capítulo 07 – “Pagamento imediato ou com vencimento através de QR Code dinâmico”.

                                   - Capítulo 15 (novo):

                                - Inclusão do novo capítulo “Pix Automático” e ajustes da numeração dos capítulos e páginas subsequentes.

                                    - Capítulo 16:

                                - Padronização do termo “prestador de serviço de iniciação de transação de pagamento (PSI)” em todo o capítulo;

                                     - Exclusão dos itens 11, 13, 17 e 18 da versão 6.4;

                                    - Renumeração dos itens 12, 14, 15, 16, da versão 6.4, para 14, 11, 12, 13, na versão 7.0, respectivamente;

                                 - Página 105 – item 01: inclusão do Pix Agendado e do Pix Automático nas nomenclaturas obrigatórias dos PSIs;

                               - Página 107 – item 14: ajustes na redação (necessidade de cumprimento das obrigatoriedades previstas no capítulo “Pix Agendado”, caso o PSI oferte

agendamento único e/ou recorrente);

                                 - Página 108 – item 15 (novo): inclusão de obrigatoriedade de disponibilização de funcionalidades do Pix Automático, caso o PSI oferte o produto;

                                 - Página 108 – item 16 (novo): inclusão de recomendação referente à oferta do Pix Agendado pelo PSI;

                                 - Página 108 – item 17 (novo): inclusão de recomendação referente à oferta do Pix Automático pelo PSI;

                                - Página 108 – item 18 (novo): inclusão de recomendação referente à disponibilização da funcionalidade de consulta ao histórico de autorizações do Pix

Automático.

                                   - Capítulo 20 (Anexo I):

                                - Ajustes de numeração de páginas e itens citados;

                                - Página 120: Alterações no item 10 do cap. “Obrigações e recomendações gerais” – ajustes na redação de forma a evidenciar a obrigatoriedade de acesso

fácil e direto ao canal de atendimento para fins de registro de reclamações no âmbito do Pix;

                                 - Página 124: Alterações no item 01 do cap. “Meus limites Pix” – exclusão de “por período” e inclusão de menção ao Pix Agendado e ao Pix Automático;

                                 - Página 124: Alteração no item 01 do cap. “Pix Agendado” – substituição da palavra “pagamentos” por “transações Pix”;

                                 - Páginas 124 e 125: Inclusão dos itens a serem avaliados no processo de verificação de aderência referentes ao cap. “Pix Automático”.

                                  - Alterações nas interfaces das telas exemplificativas.

                                - Pequenos ajustes de forma.



157




Data Versão Descrição das Alterações

02/2025 7.1 - Índice:

                                - Inclusão do novo capítulo 16 – “Autoatendimento MED” e ajustes da numeração dos capítulos subsequentes.

                                     - Capítulo 01:

                                - Página 04 – Introdução: alteração da aplicabilidade das obrigações contidas neste documento de aplicativos destinados a pessoas físicas para pessoas

naturais;

                               - Página 04 – Introdução: alteração na menção ao número do capítulo que trata do serviço de iniciação de transação de pagamento (de capítulo 16 para

capítulo 17).

                                   - Capítulo 02:

                                 - Página 06 – item 04: alteração do termo pessoa física para pessoa natural na menção ao custo do Pix.

                                   - Capítulo 03:

                              - Página 13 – item 05: inclusão do retorno de chave bloqueada quando houver consulta de chave no DICT e do termo indisponibilidade de chave como

mensagem a ser informada ao usuário;

                               - Página 14 – item 06: exclusão da palavra “oculto” na menção ao “CPF mascarado” como dado do usuário recebedor a ser apresentado para conferência.

Inserção de frase para deixar claro que não poderá haver qualquer mascaramento de chave Pix no retorno de consulta ao DICT, de forma a permitir a

conferência dos dados da chave pelo usuário pagador antes de confirmar o pagamento;

                               - Página 16 – item 12: ajuste de forma do texto sobre dados mínimos a serem apresentados no comprovante de pagamento que passou a ser apresentado

em tópicos. Inclusão da data da liquidação como informação mínima a ser apresentada.

                                   - Capítulo 04:

                               - Página 21 – item 08: ajuste de forma do texto sobre dados mínimos a serem apresentados no comprovante de pagamento que passou a ser apresentado

em tópicos. Inclusão da data da liquidação como informação mínima a ser apresentada.

                                   - Capítulo 06:

                               - Página 29 – item 07: ajuste de texto e inclusão do erro de leitura de QR Code pelo motivo de chave bloqueada e do termo chave indisponível como

mensagem a ser informada ao usuário;

                               - Página 31 – item 12: ajuste de forma do texto sobre dados mínimos a serem apresentados no comprovante de pagamento que passou a ser apresentado

em tópicos. Inclusão da data da liquidação como informação mínima a ser apresentada. Inclusão de frase sobre vedação à exibição da chave Pix vinculada

ao QR Code estático e dos dados bancários (agência e conta) do recebedor no comprovante de pagamento, quando o campo “Identificador” (TxId) estiver

preenchido.

                                   - Capítulo 07:

                                 - Página 36 – exclusão de uma das telas exemplificativas;

                                - Página 36 – item 08: inclusão do erro de leitura de QR Code pelo motivo de chave bloqueada;

                               - Página 38 – item 13: ajuste de forma do texto sobre dados mínimos a serem apresentados no comprovante de pagamento que passou a ser apresentado

em tópicos. Inclusão da data da liquidação como informação mínima a ser apresentada. Exclusão do trecho “sempre que estiver preenchido” associado à

mensagem do campo “Identificador” (TxId). Inclusão de frase sobre vedação à exibição da chave Pix vinculada ao QR Code dinâmico e dos dados bancários

(agência e conta) do recebedor no comprovante de pagamento.

                                   - Capítulo 08:

                                - Página 40 – item 03: inclusão da especificação “lançamentos futuros” no extrato da conta ou extrato Pix, onde serão disponibilizadas as transações Pix

Agendado. Inserção da possibilidade de identificar o Pix Agendado em um menu de consulta específico para agendamentos.

                                     - Capítulo 10:

                                 - Página 47 – item 02: exclusão do trecho “em caso de Pix iniciados por QR Code” em frase que possibilita, a critério do PSP pagador, a exibição do nome do

prestador de serviços de pagamento ao qual a chave está vinculada.



158




Data Versão Descrição das Alterações

02/2025 7.1 - Capítulo 12:

                              - Página 64 – item 04: inclusão da especificação “com vencimento” na frase “para agendamentos únicos realizados por meio do QR code dinâmico”.

Exclusão dos trechos “sempre que estiver preenchido” e “conforme o tipo de pagamento”;

                                - Página 64 – item 05: inclusão do “Pix Agendado” na citação ao limite diário. Substituição de data agendada por data prevista para o pagamento;

                                - Página 65 – item 07: substituição da quantidade de repetições por quantidade de pagamentos;

                                - Página 65 – item 08: substituição da quantidade de repetições por quantidade de pagamentos;

                                - Página 65 – item 09: substituição da quantidade de repetições por quantidade de pagamentos;

                                - Página 65 – item 10: exclusão do trecho “a qualquer momento” e inclusão da informação “horário limite para o cancelamento” de agendamento;

                                - Página 66 – item 12: substituição da quantidade de repetições por quantidade de pagamentos;

                                - Página 67 – item 16: ajustes de redação e inclusão da frase “para agendamentos recorrentes, a verificação do limite disponível deve ser feita pelo menos

para a data agendada mais próxima”;

                                - Página 68 – item 20: substituição da quantidade de repetições por quantidade de pagamentos;

                                 - Página 69 – item 23: inclusão de “Agendado” para especificar o tipo de transações Pix.

                                      - Capítulo 15:

                                 - Página 85 – item 08: alteração de item 15 para item 16 na referência à continuidade da jornada de autorização;

                                  - Página 86 – item 10: alteração de itens 15 e 18 para itens 16 e 19 na referência às telas com informações da autorização;

                                 - Página 87 – item 12: alteração de item 15 para item 16 na referência à continuidade da jornada de autorização;

                                - Página 87 – item 13 (novo): inclusão de obrigatoriedade para permitir ao usuário concluir a jornada de pagamento, sem avançar para a etapa da oferta do

Pix Automático para os próximos pagamentos, caso ocorra erro na leitura apenas da parte do QR Code relativa à recorrência;

                                  - Página 88 – item 15: alteração de item 15 para item 16 na referência à continuidade da jornada de autorização;

                               - Página 91 – item 19: inclusão de informação para esclarecer que “o valor do pagamento imediato não está sujeito ao valor máximo estabelecido pelo

usuário”. Exclusão de um parágrafo que foi transferido para o novo item 20, da página 92;

                               - Página 92 – item 20 (novo): reposicionamento de parágrafo do item 19 que cita a necessidade de constar a informação de que o primeiro pagamento é

imediato e inclusão de obrigatoriedade de campo check box para que o usuário ateste conhecimento de que está autorizando pagamentos recorrentes

futuros;

                                - Página 95 – item 31: adequação em redação para substituir “do” por “de um”;

                               - Página 98 – item 39: inclusão de informação para recomendar que “caso o valor máximo seja alterado para um valor inferior ao de um pagamento já

agendado, o PSP pagador poderá informar o fato ao usuário pagador e oferecer a possibilidade de cancelamento do pagamento agendado”;

                                - Página 99 – item 40: inclusão da data da liquidação como informação mínima a ser apresentada;

                                - Página 102 – item 48: inclusão de informação para estabelecer que “quando a liquidação ocorrer entre zero hora e seis horas da manhã, a notificação deve

ser enviada, preferencialmente, após esse horário”;

                               - Página 103 – item 53: inclusão da obrigatoriedade de envio de notificação sobre resultado do processamento da autorização na situação em que tenha

sido ultrapassado o limite máximo de tempo que o PSP do pagador deve aguardar para a conclusão do processo de autorização pelo PSP do recebedor;

                                - Página 103 – item 57 (novo): inclusão de recomendação de envio de notificação sobre a possibilidade de alteração do valor máximo até dois dias antes da

data prevista de liquidação e da necessidade de entrar em contato com o recebedor, de forma a viabilizar o pagamento no mesmo ciclo, nos casos em que

um agendamento não foi realizado por ultrapassar o valor máximo estabelecido para a autorização.

                                   - Capítulo 16 (novo):

                               - Inclusão do novo capítulo “Autoatendimento MED” e ajustes da numeração dos capítulos e páginas subsequentes.

                                    - Capítulo 21 (Anexo I):

                                - Ajustes de numeração de páginas e itens citados;

                                - Página 136: Inclusão dos itens a serem avaliados no processo de verificação de aderência referentes ao cap. “Autoatendimento MED”.

                                  - Alterações nas interfaces das telas exemplificativas.

                                - Pequenos ajustes de forma.



159




Data Versão Descrição das Alterações

10/2025 7.2 - Capítulo 03:

                                - Página 13 – item 06 (novo): inclusão de obrigatoriedade de envio de mensagem de erro nos casos em que o retorno do envio de chave ao DICT for de conta

ou usuário com restrição para recebimento de transação Pix por envolvimento em fraude.

                                - Ajustes de numeração de itens devido à inclusão de novo item no capítulo.

                                   - Capítulo 06:

                                - Página 29 – item 08 (novo): inclusão de obrigatoriedade de informar ao usuário acerca de erro decorrente da leitura de QR Code com chave vinculada a

conta ou usuário com restrição para recebimento de transação Pix por envolvimento em fraude.

                                - Ajustes de numeração de itens devido à inclusão de novo item no capítulo.

                                   - Capítulo 07:

                                - Página 36 – item 10 (novo): inclusão de obrigatoriedade de informar ao usuário acerca de erro decorrente da leitura de QR Code com chave vinculada a

conta ou usuário com restrição para recebimento de transação Pix por envolvimento em fraude.

                              - Página 38 – item 16 (novo): inclusão de recomendação de exibição dos dados do devedor no comprovante de pagamento para os usuários pagador e

recebedor, se forem informados.

                                 - Ajustes de numeração de itens devido à inclusão de novos itens no capítulo.

                                   - Capítulo 08:

                             - Página 40 – item 03: exclusão de permissão de complementação ao nome Pix Agendado para informar ao usuário que se trata de um agendamento

recorrente;

                               - Página 40 – item 04: inclusão do trecho “o pagamento imediato das jornadas 3 e 4 de autorização constitui uma exceção a essa regra, não devendo ser

identificado com a nomenclatura Pix Automático no extrato da conta ou no extrato Pix, mas sim como uma transação Pix”;

                                - Página 40 – item 05 (novo): inclusão de obrigatoriedade de identificação das devoluções de transações Pix contestadas no âmbito do MED no extrato da

conta e, caso disponibilizado, no extrato Pix. Inclusão de vedação à exibição do nome do remetente caso os recursos devolvidos sejam provenientes de conta

diferente da conta recebedora da transação raiz.

                                - Ajustes de numeração de itens devido à inclusão de novo item no capítulo.

                                     - Capítulo 10:

                                - Página 48 – item 07: substituição de “devem” por “podem”.

                                     - Capítulo 12:

                                  - Páginas 66 e 68 – itens 13 e 18: substituição de “Pix Agendado recorrente” por “Pix Agendado” nas telas exemplificativas.

                                     - Capítulo 15:

                              - Página 85 – item 05: inclusão da numeração da jornada de autorização à qual o item se aplica e de texto explicativo sobre o campo “objeto do

pagamento”;

                                - Página 85 – item 06: inclusão da numeração da jornada de autorização à qual o item se aplica;

                                - Página 85 – item 07: inclusão da numeração da jornada de autorização à qual o item se aplica;

                             - Página 85 – item 08: inclusão de menção ao menu “Autorizações pendentes” e da numeração da jornada de autorização à qual o item se aplica.

Substituição de “dessa jornada” por “da jornada”;

                               - Página 86 – item 09: inclusão da numeração da jornada de autorização à qual o item se aplica, do trecho “de confirmação” e realização de ajustes de

redação;

                                 - Página 87 – item 11: inclusão da numeração da jornada de autorização à qual o item se aplica;

                                 - Página 87 – item 12: inclusão da numeração da jornada de autorização à qual o item se aplica. Substituição de “dessa jornada” por “da jornada”;

                                 - Página 87 – item 13: inclusão da numeração da jornada de autorização à qual o item se aplica;

                                 - Página 88 – item 14: inclusão da numeração da jornada de autorização à qual o item se aplica;

                                 - Página 88 – item 15: inclusão da numeração da jornada de autorização à qual o item se aplica. Substituição de “dessa jornada” por “da jornada”;

                                - Página 89 – item 16: inclusão da numeração das jornadas de autorização às quais o item se aplica. Inclusão de “(caso seja informado)” após “objeto do

pagamento” e substituição de “identificador da cobrança” por “identificador do objeto da cobrança”. Inclusão de texto explicativo sobre os campos “objeto

do pagamento” e “identificador do objeto da cobrança”;

                                 - Página 89 – item 17: inclusão da numeração das jornadas de autorização às quais o item se aplica;



160




Data Versão Descrição das Alterações

10/2025 7.2 - Capítulo 15:

                                - Página 90 – item 18: exclusão de “primeiro” antes de “pagamento imediato”. Inclusão da numeração da jornada de autorização à qual o item se aplica;

                               - Página 91 – item 19: exclusão de “primeiro” antes de “pagamento imediato”. Inclusão da numeração da jornada de autorização à qual o item se aplica.

Inclusão de “(caso seja informado)” após “objeto do pagamento” e substituição de “identificador da cobrança” por “identificador do objeto da cobrança”;

                                - Página 92 – item 20: inclusão da numeração da jornada de autorização à qual o item se aplica. Substituição de “destaque de que o primeiro pagamento é

imediato” por “destaque de que haverá um pagamento imediato”;

                                - Página 92 – item 21: exclusão de “primeiro” antes de “pagamento imediato”. Inclusão da numeração da jornada de autorização à qual o item se aplica;

                                - Página 92 – item 22: inclusão da numeração da jornada de autorização à qual o item se aplica;

                                - Página 92 – item 23: substituição de “primeiro pagamento” por “pagamento imediato referente à jornada 3”;

                               - Página 92 – item 24: inclusão da numeração das jornadas de autorização às quais o item se aplica. Substituição de “prazo exigido em regulamentação

para permitir a conclusão do processo” por “tempo estabelecido para a experiência do usuário pagador na concessão da autorização Pix Automático”.

Inclusão de “pagador” após “mensagem ao usuário”;

                                - Página 93 – item 26: inclusão de “(caso seja informado)” após “objeto do pagamento” e substituição de “identificador da cobrança” por “identificador do

objeto da cobrança”;

                               - Página 95 – item 28: inclusão de “(caso seja ofertada pelo PSP)” após “uso de linha de crédito”. Inclusão de botão para opção de recebimento de

notificações de agendamento na tela do canto superior direito;

                                  - Página 95 – item 29: inclusão de “(caso seja ofertada pelo PSP)” após “uso de linha de crédito”;

                                - Página 96 – item 33: inclusão de “(caso seja informado)” após “objeto do pagamento” e substituição de “identificador da cobrança” por “identificador do

objeto da cobrança”;

                                - Página 97 – item 35: inclusão de obrigatoriedade de contemplar na consulta ao histórico tanto as autorizações concedidas diretamente ao PSP quanto os

consentimentos efetivados por meio de um PSI, com padronização da nomenclatura utilizada para indicar o status das autorizações;

                               - Página 99 – item 40: Inclusão de “recorrente” após “comprovante de pagamento” e de “(caso seja informado)” após “objeto do pagamento”. Inclusão das

informações do pagador na primeira tela exemplificativa;

                             - Página 99 – item 41 (novo): Inclusão de vedação à identificação do comprovante de pagamento imediato das jornadas 3 e 4 ou da cobrança com

vencimento da jornada 4 como Pix Automático e inclusão de obrigatoriedade de seguir os requisitos dispostos nos capítulos “Pagamento através de QR Code

estático” e “Pagamento imediato ou com vencimento através de QR Code dinâmico”;

                               - Página 99 – item 42 (novo): Inclusão de recomendação para incluir os dados do devedor no comprovante de pagamento recorrente.

                                - Página 101 – item 44: substituição de “notificações de pagamentos agendados” por “notificações de agendamento”;

                                - Página 102 – item 52 (nova numeração): Inclusão de “(caso seja informado)” após “objeto do pagamento”;

                                - Página 102 – item 52: excluído, tendo em vista a revogação por meio da Instrução Normativa BCB nº 625, de 29/05/2025;

                                 - Página 103 – item 55: inclusão da numeração da jornada de autorização à qual o item se aplica. Substituição de “suspensão” por “exclusão”;

                                - Página 103 – item 58: exclusão de “até dois dias antes da data prevista de liquidação” e inclusão de “tentar” antes de “viabilizar o pagamento no mesmo

ciclo”;

                                 - Página 103 – exclusão da menção à data limite para alteração do valor máximo da tela exemplificativa referente aos itens 53 e 58;

                                 - Ajustes de numeração de itens devido à inclusão de novos itens no capítulo.

                                    - Capítulo 16:

                                - Página 106 – item 03: substituição de “deve-se fornecer” por “devem ser fornecidas” e “prazo limite para resolução das contestações de transações” por

“prazo máximo para o PSP concluir a análise da contestação de transação”;

                                - Página 106 – item 04: ajuste decorrente do MED 2.0 – complementação de texto para informar que a devolução pode ocorrer a partir de contas diferentes

da conta recebedora da transação raiz (original) que estejam envolvidas na fraude. Exclusão de trecho que menciona o período de monitoramento de 90

dias para devoluções complementares;

                                 - Página 107 – item 07: ajuste decorrente do MED 2.0 – substituição do termo “notificação de infração” por “recuperação de valores”;

                                - Página 107 – item 08: ajustes decorrentes do MED 2.0 – substituição do termo “notificação de infração” por “recuperação de valores” e complementação de

texto para informar sobre a necessidade de existência de saldo na conta recebedora da transação raiz ou em outras contas envolvidas na suspeita de

fraude para viabilizar a devolução parcial ou total;



161




Data Versão Descrição das Alterações

10/2025 7.2 - Capítulo 16:

                                - Página 108 – item 09: ajustes decorrentes do MED 2.0 – substituição do termo “notificação de infração” por “recuperação de valores” e complementação de

texto para informar sobre a necessidade de existência de saldo na conta recebedora da transação raiz ou em outras contas envolvidas na suspeita de

fraude para viabilizar a devolução parcial ou total;

                                 - Página 108 – item 10: ajuste decorrentes do MED 2.0 – substituição do termo “notificação de infração” por “recuperação de valores”. Inclusão de informação

para estabelecer que “a solicitação do relato da fraude deve ocorrer preferencialmente antes da finalização da jornada de autoatendimento, logo após o

registro da recuperação de valores, de forma a garantir a tempestividade da coleta das informações”;

                                 - Página 108 – item 11: ajuste decorrentes do MED 2.0 – substituição do termo “notificação de infração” por “recuperação de valores”;

                                 - Página 110 – item 14: ajuste decorrentes do MED 2.0 – substituição do termo “notificação de infração” por “recuperação de valores”;

                                - Página 111 – item 17: ajustes decorrentes do MED 2.0 – substituição do termo “notificação de infração” por “recuperação de valores” e complementação de

texto para informar sobre a necessidade de existência de saldo na conta recebedora da transação raiz ou em outras contas envolvidas na suspeita de

fraude para viabilizar a devolução parcial ou total;

                                - Página 112 – item 23: ajuste decorrentes do MED 2.0 – substituição de “nome do recebedor” por “nome do recebedor da transação raiz”. Inclusão do valor

efetivamente devolvido no conjunto de informações mínimas a serem apresentadas para contestações aprovadas. Substituição de “valor” por “valor

contestado” nas telas exemplificativas e inclusão de “valor devolvido” no exemplo de contestação aprovada;

                              - Página 112 – item 24: substituição do “nome do recebedor” por “nome do recebedor da transação contestada”. Substituição de “valor efetivamente

devolvido referente às contestações aprovadas” por “valor efetivamente devolvido, no caso de contestação aprovada”. Ajuste decorrente do MED 2.0 –

reescrita da frase que trata do prazo de 90 dias para realização de devoluções, com inclusão de menção a outras contas envolvidas na fraude além da

conta recebedora da transação raiz;

                                - Página 113 – item 26: ajustes decorrentes do MED 2.0 – substituição do termo “transação original” por “transação raiz”, inclusão de menção aos demais

recebedores envolvidos na suspeita de fraude e substituição de “notificação de infração associada a uma solicitação de devolução” por “recuperação de

valores”;

                                - Página 113 – item 27: ajustes decorrentes do MED 2.0 – substituição do termo “transação original” por “transação raiz” e inclusão de menção aos demais

recebedores envolvidos na suspeita de fraude;

                                - Página 113 – item 28: ajustes decorrentes do MED 2.0 – substituição do termo “transação original” por “transação raiz” e inclusão de menção aos demais

recebedores envolvidos na suspeita de fraude.

                                - Página 113 – exclusão do termo “PSP do usuário pagador” do destinatário no rodapé da página.

                                - Página 114 – item 29: ajustes decorrentes do MED 2.0 – inclusão de informações mínimas da notificação de crédito proveniente da conta do recebedor da

transação raiz e da notificação no caso de crédito de conta diferente da que recebeu a transação raiz. Proibição de exibição do nome do remetente do

crédito quando se tratar de uma conta diferente da que recebeu a transação raiz;

                                 - Página 114 – Inclusão de segunda tela exemplificativa para o item 29 e exclusão do termo “PSP do usuário recebedor” do destinatário do rodapé da página.

                                     - Capítulo 21 (Anexo I):

                                - Ajustes de numeração de páginas e itens citados.



162




Data Versão Descrição das Alterações

12/2025 7.3 - Capítulo 16:

                                - Página 113 – item 26: ajustes no texto de forma a deixar claro que, no contexto do MED 2.0, a mensagem enviada para o usuário recebedor envolvido na

suspeita de fraude comunicando o bloqueio de recursos em sua conta deve fazer menção às informações da transação vinculada à notificação de infração

recebida, que pode ser a transação raiz ou uma transação a partir da segunda camada. Na tela exemplificativa correspondente, inclusão do valor da

transação vinculada à notificação de infração, diferente do valor bloqueado, e alteração do horário de recebimento da notificação para alinhamento à

informação sobre o horário do bloqueio do exemplo mostrado na tela do item 27.

                                - Página 113 – item 27: ajustes no texto de forma a deixar claro que, no contexto do MED 2.0, a mensagem enviada para o usuário recebedor envolvido na

suspeita de fraude comunicando a liberação de recursos bloqueados em sua conta deve fazer menção às informações da transação vinculada à

notificação de infração recebida, que pode ser a transação raiz ou uma transação a partir da segunda camada. Complementação de texto para informar

sobre a necessidade de envio da mensagem inclusive nos casos em que tenha ocorrido devolução de parte do valor previamente bloqueado. Na tela

exemplificativa correspondente, substituição de “bloqueado” por “associado ao bloqueio realizado” e de “referente à transação Pix” por “vinculado à

transação Pix”.

                                - Página 113 – item 28: complementação de texto para esclarecer que a devolução tem como destinatário o usuário pagador da transação raiz. Ajustes no

texto de forma a deixar claro que, no contexto do MED 2.0, a mensagem enviada para o usuário recebedor envolvido na suspeita de fraude comunicando a

devolução dos recursos bloqueados em sua conta deve fazer menção às informações da transação vinculada à notificação de infração recebida, que pode

ser a transação raiz ou uma transação a partir da segunda camada. Exclusão da “Data/hora/minuto/segundo (horário de Brasília) do bloqueio” do rol de

informações mínimas obrigatórias na mensagem. Proibição de exibição do nome do destinatário da devolução quando se tratar de devolução proveniente

de conta diferente da que recebeu a transação raiz. Na tela exemplificativa correspondente, exclusão do nome do destinatário da devolução e da data/hora/

minuto/segundo do bloqueio, e inclusão de “via MED”.

                                  - Página 114 – item 29: substituição do termo “transação original” por “transação raiz”. Substituição de “não deve ser exibido na notificação” por “não deve ser

exibido ao usuário pagador”.

                                 - Página 114 – item 30 (novo): inclusão de obrigatoriedade da aplicação do disposto nos itens 26 a 29 do Cap. 16 às contestações no âmbito do MED abertas

por qualquer canal de atendimento.

                                 - Página 114 – item 31: ajuste de numeração do item.



163


