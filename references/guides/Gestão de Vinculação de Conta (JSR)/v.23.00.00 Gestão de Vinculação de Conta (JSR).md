# v.23.00.00 Gestão de Vinculação de Conta (JSR)

Esta página reúne os requisitos e recomendações para gestão de **vínculos de conta utilizados nas Jornadas de pagamento Sem Redirecionamento (JSR) com ou sem autorização de compartilhamento de saldo e limite via Jornada Otimizada (JO).**

* * *

# Gestão na ITP

Esta seção reúne os requisitos e recomendações para gestão de vínculos de conta na Instituição Iniciadora de Transação de Pagamento (ITP).

* * *

## Gestão dos vínculos de conta na ITP

![image-20260423-180255.png](images/image-20260423-180255.png)#F4F5F7

## Requisitos - ITP

REQ.VC-07500

**Cenário: Acesso ao Open Finance**

-   `REQ.VC-07500` Disponibilizar acesso ao ambiente Open Finance nos seus canais, incluindo-o no primeiro nível do menu principal, para garantir acesso rápido e fácil ao usuário.
    

![image-20260611-174146.png](images/image-20260611-174146.png)

REQ.VC-07600

**Cenário: Geral**

-   `REQ.VC-07600` Conforme regulação vigente, comunicar o resultado de todas as ações ao usuário, inclusive em caso de falha.
    

![image-20260611-174247.png](images/image-20260611-174247.png)REQ.VC-07700

**Cenário: Gestão dos vínculos de conta ativos**

-   `REQ.VC-07700` Disponibilizar funcionalidade de consulta e cancelamento dos vínculos de conta ativos.
    

![image-20260611-175644.png](images/image-20260611-175644.png)

REQ.VC-07800

**Cenário**: **Comprovante dos vínculos de conta ativos**

-   `REQ.VC-07800` Exibir comprovante de cada vínculo de conta ativo.
    

REQ.VC-07900

-   `REQ.VC-07900` No comprovante, exibir nome da ID, número da agência e conta da conta vinculada.
    

![image-20260615-144545.png](images/image-20260615-144545.png)

REQ.VC-08200

**Cenário**: **Comprovante dos vínculos de conta inativos**

-   `REQ.VC-08200` Nos casos de vinculações de conta com status como Não concluído, Cancelado, Expirado, Rejeitado, Em análise, exibir o status com clareza e os campos aplicáveis, de acordo com a disponibilidade de informações no momento.
    

![image-20260611-175559.png](images/image-20260611-175559.png)

REQ.VC-08300

**Cenário: Histórico dos vínculos de conta**

-   `REQ.VC-08300` Disponibilizar funcionalidade de consulta ao histórico de todos os vínculos de conta e seus respectivos status.  
    Ex.: Ativo, Não concluído, Cancelado, Expirado, Rejeitado.
    

![image-20260611-175809.png](images/image-20260611-175809.png)wide760#F4F5F7

## Requisitos - ITP

REQ.VC-08500 a 08900

**Cenário: Cancelamento dos vínculos de conta ativos**

-   `REQ.VC-08500` Permitir que o usuário cancele vínculos de conta ativos a qualquer momento.
    
-   `REQ.VC-08600` Informar sobre a irreversibilidade do cancelamento do vínculo de conta e outras possíveis consequências.
    
-   `REQ.VC-08700` Ao optar pelo cancelamento do vínculo de conta, informar que a autorização de Pix Automático atrelada ao vínculo de conta também será cancelada.
    
-   `REQ.VC-08800` Ao optar pelo cancelamento do vínculo de conta que possua uma autorização de Pix Automático atrelada, informar que novos agendamentos não poderão ser criados após o cancelamento.
    
-   `REQ.VC-08900` Ao optar pelo cancelamento do vínculo de conta que possua uma autorização de Pix Automático atrelada, informar que pagamentos já enviados serão mantidos.
    

![image-20260615-145013.png](images/image-20260615-145013.png)

wide760#F4F5F7

## Recomendações - ITP

REC.VC-01800

**Cenário: Acesso à gestão de vínculos de conta**

-   `REC.VC-01800` Disponibilizar acesso aos vínculos de conta através:   
    \- Da área “Open Finance”; e/ou   
    \- Do caminho “Open Finance” > “Minhas contas salvas/vinculadas”; e/ou   
    \- De áreas dedicadas aos produtos, no canal da instituição.
    

![image-20260611-183040.png](images/image-20260611-183040.png)

REC.VC-01900

**Cenário: Comprovante dos vínculo de conta ativos**

-   `REC.VC-01900` Exibir a data de validade do vínculo de conta
    

![image-20260611-183131.png](images/image-20260611-183131.png)

REC.VC-02000 a 02100

**Cenário: Histórico dos vínculos de conta**

-   `REC.VC-02000` Disponibilizar funcionalidades de ordenação (por data, recebedor, status) e de filtro pelo status na consulta ao histórico de vínculos de conta.
    
-   `REC.VC-02100` No histórico, exibir primeiramente os que estiverem próximos de expirar.
    

![image-20260615-145221.png](images/image-20260615-145221.png)

REC.VC-02200 a 02400

**Cenário: Cancelamento dos vínculos de conta ativos**

-   `REC.VC-02200` Possibilitar que o usuário cancele todos os vínculos de conta ativo em uma única jornada.
    
-   `REC.VC-02300` Em caso de cancelamento do vínculo de conta – com ou sem compartilhamento de saldo e limite via Jornada Otimizada – por parte do usuário, exibir uma mensagem de confirmação da ação.   
    Ex.: Tem certeza que quer cancelar o vínculo de conta? \[O compartilhamento de saldo e limite também será cancelado.\]
    
-   `REC.VC-02400` Combinar a mensagem de confirmação com a informação obrigatória sobre a irreversibilidade do cancelamento.
    
    Ex.: Tem certeza que deseja cancelar o vínculo? Essa ação é irreversível \[e encerra o compartilhamento do saldo e limite e a autorização de Pix Automático atrelada. Os pagamentos agendados serão mantidos, mas novos agendamentos não poderão ser feitos\].
    

![image-20260611-183505.png](images/image-20260611-183505.png)

* * *

## Gestão do compartilhamento de saldo e limite via Jornada Otimizada na ITP

Esta seção reúne os requisitos e recomendações para gestão do compartilhamento de saldo e limite da conta pagadora concedido via Jornada Otimizada na jornada de Vinculação de Conta na Instituição Iniciadora de Transação de Pagamento (ITP).

wide760

**Nota**

Consulte a página **Gestão de Compartilhamento de Dados** para mais informações sobre o comprovante do compartilhamento de dados de saldo e limite.

wide760#F4F5F7

## Requisitos - ITP

REQ.VC-08400

**Cenário: Histórico dos vínculos de conta com compartilhamento de saldo e limite via Jornada Otimizada**

-   `REQ.VC-08400` Sinalizar, de forma clara, no histórico dos vínculos de conta, aqueles para os quais o usuário optou por compartilhar o saldo e limite.  
    Ex.: tag “Saldo e limite compartilhados”
    

![image-20260611-175909.png](images/image-20260611-175909.png)REQ.VC-08000 a 08100

**Cenário: Comprovante dos vínculos de conta com compartilhamento de saldo e limite via Jornada Otimizada**

-   `REQ.VC-08000` Indicar que o saldo e o limite da conta pagadora estão sendo compartilhados.
    
-   `REQ.VC-08100` Exibir o escopo dos dados compartilhados.
    

REQ.VC-09000

**Cenário: Cancelamento da vinculação de conta com compartilhamento de saldo e limite via Jornada Otimizada**

-   `REQ.VC-09000` Ao optar pelo cancelamento da vinculação de conta, informar o usuário que o compartilhamento de saldo e limite da conta pagadora também será cancelado.​
    

![image-20260611-180651.png](images/image-20260611-180651.png)REQ.VC-09100 a 09200

**Cenário: Cancelamento do compartilhamento de saldo e limite da conta via Jornada Otimizada**

-   `REQ.VC-09100` Permitir o cancelamento, a qualquer momento, do compartilhamento de saldo e limite da conta pagadora concedido via Jornada Otimizada.
    
-   `REQ.VC-09200` Ao optar pelo cancelamento do compartilhamento de saldo e limite da conta pagadora concedido via Jornada Otimizada, informar o usuário de que o vínculo de conta se mantém ativo.
    

![image-20260611-183643.png](images/image-20260611-183643.png)

wide760#F4F5F7

## Recomendações - ITP

REC.VC-02499

**Cenário: Ambiente Open Finance**

-   `REC.VC-02499` Na tela inicial da área de gestão do Open Finance, exibir opções como “O que é o Open Finance?” e “Ler Termos de Uso” facilitando o acesso a informações essenciais sobre o funcionamento e os direitos do usuário no Open Finance.
    

![image-20260624-215716.png](images/image-20260624-215716.png)REC.VC-02500 a 02600

**Cenário: Cancelamento do compartilhamento de saldo e limite da conta via Jornada Otimizada**

-   `REC.VC-02500` Ao optar pelo cancelamento do compartilhamento de saldo e limite da conta pagadora concedido via Jornada Otimizada, exibir mensagem informando sobre os benefícios de manter a funcionalidade.
    
-   `REC.VC-02600` Incluir informação adicional sobre o compartilhamento de saldo e limite da conta pagadora através da Jornada Otimizada por meio de link, botão, imagem, texto etc.
    

![image-20260611-185227.png](images/image-20260611-185227.png)

* * *

# Gestão na ID

Esta seção reúne os requisitos e recomendações para gestão dos vínculos de conta na Instituição Detentora de Conta (ID).

* * *

## Gestão dos vínculos de conta na ID

![image-20260611-194952.png](images/image-20260611-194952.png)

wide760#F4F5F7

## Requisitos - ID

REQ.VC-07500true

![image-20260612-201018.png](images/image-20260612-201018.png)REQ.VC-07501

-   `REQ.VC-07501` Se apresentar Termos e Condições, exibi-los somente na área de gestão Open Finance.
    

![image-20260624-221924.png](images/image-20260624-221924.png)

REQ.VC-07600true

![image-20260612-201154.png](images/image-20260612-201154.png)

**Cenário: Gestão dos vínculos de conta ativos**

REQ.VC-07601

-   `REQ.VC-07601` Disponibilizar funcionalidade de consulta, alteração e cancelamento dos vínculos de conta ativos.
    

![image-20260612-201358.png](images/image-20260612-201358.png)

REQ.VC-07800true

REQ.VC-07801 a 07803

-   `REQ.VC-07801` No comprovante, exibir o nome da ITP envolvida no vínculo.
    
-   `REQ.VC-07802` No comprovante, exibir número da agência e conta da conta vinculada.
    
-   `REQ.VC-07803` No comprovante, exibir o prazo de validade do vínculo de conta.
    

![image-20260612-201653.png](images/image-20260612-201653.png)

REQ.VC-08200true

![image-20260612-202956.png](images/image-20260612-202956.png)

REQ.VC-08300true

![image-20260713-180257.png](images/image-20260713-180257.png)

REQ.VC-08401 a 08402

**Cenário: Alteração dos vínculos de conta ativos**

-   `REQ.VC-08401` Permitir a alteração do prazo de validade do vínculo da conta.
    
-   `REQ.VC-08402` Informar o usuário, no momento da confirmação da alteração, que as alterações do prazo vínculo de conta podem afetar os pagamentos automáticos.
    
    Ex.: **Prazo alterado com sucesso**. Pagamentos automáticos programados para data posterior ao novo prazo serão cancelados.
    

![image-20260615-140947.png](images/image-20260615-140947.png)

REQ.VC-08403 a 08408

-   `REQ.VC-08403` Permitir que o usuário altere os limites diário e/ou por transação do vínculo de conta.
    
-   `REQ.VC-08404` Observar a mesmas regras aplicáveis à etapa de **Confirmação** da jornada de vinculação de conta.
    
-   `REQ.VC-08405` Impedir a alteração do limite por transação com valor superior a R$ 500,00, salvo quando houver previsão diversa em contrato bilateral entre ITP e ID.
    
-   `REQ.VC-08406` Informar o usuário de que os limites do Pix serão considerados.
    
-   `REQ.VC-08407` Informar o usuário, antes da confirmação, de que as alterações do limite podem afetar os pagamentos agendados.     
    Ex.: Existem pagamentos agendados com valores superiores ao limite estabelecido. A redução do limite poderá impedir a realização desses pagamentos na data programada. Tem certeza que deseja confirmar a redução?
    
-   `REQ.VC-08408` Seguir a regulação vigente para efetivação da alteração.
    

![image-20260615-142536.png](images/image-20260615-142536.png)wide760#F4F5F7

## Requisitos - ID

REQ.VC-08500 a 08900true

![image-20260615-143647.png](images/image-20260615-143647.png)

wide760#F4F5F7

## Recomendações - ID

REC.VC-01800true

![image-20260615-143941.png](images/image-20260615-143941.png)

REC.VC-01801

**Cenário: Comprovante do vínculo de conta**

-   `REC.VC-01801` Exibir o nome/apelido do dispositivo autorizado, se definido pelo usuário.
    

![image-20260615-144106.png](images/image-20260615-144106.png)

REC.VC-02101 a 02102

**Cenário: Alteração dos vínculos de conta ativos**

-   `REC.VC-02101` Nas jornadas de alteração, usar o termo “alterar” em suas diferentes conjugações, de acordo com o contexto.
    
-   `REC.VC-02102` Pré-preencher dados do vínculo de conta para facilitar a alteração.  
    Ex.: Se o parâmetro alterado for de limites, os demais campos podem vir pré-preenchidos.
    

![image-20260624-172844.png](images/image-20260624-172844.png)

REC.VC-02200 a 02400true

![image-20260320-181119.png](images/image-20260320-181119.png)

* * *

## Gestão do compartilhamento de saldo e limite via Jornada Otimizada na ID

Esta seção reúne os requisitos e recomendações para gestão do compartilhamento de saldo e limite da conta pagadora concedido via Jornada Otimizada na jornada de Vinculação de Conta na Instituição Detentora de Conta (ID).

wide760#F4F5F7

## Requisitos - ID

wide760

**Nota**

Consulte a página **Gestão de compartilhamento de dados** para mais informações sobre o comprovante do compartilhamento de dados de saldo e limite.

REQ.VC-08400true

![image-20260624-174000.png](images/image-20260624-174000.png)

REQ.VC-08000 a 08100true

![image-20260612-202625.png](images/image-20260612-202625.png)REQ.VC-08409

**Cenário: Alteração dos vínculos de conta ativos com compartilhamento de saldo e limite via Jornada Otimizada**

-   `REQ.VC-08409` Ao alterar o prazo do vínculo de conta, informar que o prazo do compartilhamento de saldo e limite concedido via Jornada Otimizada será automaticamente atualizado conforme o novo prazo do vínculo de conta.
    

![image-20260615-142842.png](images/image-20260615-142842.png)

REQ.VC-09000true

![image-20260616-143119.png](images/image-20260616-143119.png)

REQ.VC-09100 a 09200true

![image-20260615-145415.png](images/image-20260615-145415.png)

wide760#F4F5F7

## Recomendações - ID

REC.VC-02499true

![image-20260624-215939.png](images/image-20260624-215939.png)

REC.VC-02500 a 02600true

![image-20260615-145513.png](images/image-20260615-145513.png)true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

IN BCB 760

**ID**

`REQ.VC-07500`

**Texto**

Disponibilizar acesso ao ambiente Open Finance nos seus canais, incluindo-o no primeiro nível do menu principal, para garantir acesso rápido e fácil ao usuário.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

IN BCB 760

**ID**

`REQ.VC-07501`

**Texto**

Se apresentar Termos e Condições, exibi-los somente na área de gestão Open Finance.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

IN BCB 760

**ID**

`REQ.VC-07600`

**Texto**

Conforme regulação vigente, comunicar o resultado de todas as ações ao usuário, inclusive em caso de falha.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP

**Justificativa**

IN BCB 760

**ID**

`REQ.VC-07700`

**Texto**

Disponibilizar funcionalidade de consulta e cancelamento dos vínculos de conta ativos.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP

**Justificativa**

IN BCB 760

**ID**

`REQ.VC-07800`

**Texto**

Exibir comprovante de cada vínculo de conta ativo.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP

**Justificativa**

IN BCB 760

**ID**

`REQ.VC-07900`

**Texto**

No comprovante, exibir nome da ID, número da agência e conta da conta vinculada.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

IN BCB 760

**ID**

`REQ.VC-08000`

**Texto**

Indicar que o saldo e o limite da conta pagadora estão sendo compartilhados.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

IN BCB 760

**ID**

`REQ.VC-08100`

**Texto**

Exibir o escopo dos dados compartilhados.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

IN BCB 760

**ID**

`REQ.VC-08200`

**Texto**

Nos casos de vinculações de conta com status como Não concluído, Cancelado, Expirado, Rejeitado, Em análise, exibir o status com clareza e os campos aplicáveis, de acordo com a disponibilidade de informações no momento.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

IN BCB 760

**ID**

`REQ.VC-08300`

**Texto**

Disponibilizar funcionalidade de consulta ao histórico de todos os vínculos de conta e seus respectivos status.  
Ex.: Ativo, Não concluído, Cancelado, Expirado, Rejeitado.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

IN BCB 760

**ID**

`REQ.VC-08400`

**Texto**

Se o usuário tiver compartilhado o saldo e limite da conta pagadora através da Jornada Otimizada, sinalizar, de forma clara, na lista do histórico dos vínculos de conta, aqueles para os quais o usuário optou por compartilhar o saldo e limite.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

**ID**

`REQ.VC-08500`

**Texto**

Permitir que o usuário cancele vínculos de conta ativos a qualquer momento.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

**ID**

`REQ.VC-08600`

**Texto**

Informar sobre a irreversibilidade do cancelamento do vínculo de conta e outras possíveis consequências.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

IN BCB 760

**ID**

`REQ.VC-08700`

**Texto**

Ao optar pelo cancelamento do vínculo de conta, informar que a autorização de Pix Automático atrelada ao vínculo de conta também será cancelada.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

**ID**

`REQ.VC-08800`

**Texto**

Ao optar pelo cancelamento do vínculo de conta que possua uma autorização de Pix Automático atrelada, informar que novos agendamentos não poderão ser criados após o cancelamento.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

**ID**

`REQ.VC-08900`

**Texto**

Ao optar pelo cancelamento do vínculo de conta que possua uma autorização de Pix Automático atrelada, informar que pagamentos já enviados serão mantidos.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

IN BCB 760

**ID**

`REQ.VC-09000`

**Texto**

Ao optar pelo cancelamento do vínculo de conta, informar que o compartilhamento de saldo e limite também será cancelado.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

IN BCB 760

**ID**

`REQ.VC-09100`

**Texto**

Permitir que o usuário cancele o compartilhamento de saldo e limite de um vínculo de conta a qualquer momento.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

IN BCB 760

**ID**

`REQ.VC-09200`

**Texto**

Ao optar pelo cancelamento do compartilhamento de saldo e limite do compartilhamento de saldo e limite, informar o usuário de que o vínculo de conta se mantém ativo.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

IN BCB 760

**ID**

`REQ.VC-07601`

**Texto**

Disponibilizar funcionalidade de consulta, alteração e cancelamento dos vínculos de conta ativos.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Gestão

**Proposta**

**Instituição**

ID

**Justificativa**

IN BCB 760

**ID**

`REQ.VC-07801`

**Texto**

No comprovante, exibir o nome da ITP envolvida no vínculo.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Gestão

**Proposta**

**Instituição**

ID

**Justificativa**

IN BCB 760

**ID**

`REQ.VC-07802`

**Texto**

No comprovante, exibir número da agência e conta da conta vinculada.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Gestão

**Proposta**

**Instituição**

ID

**Justificativa**

IN BCB 760

**ID**

`REQ.VC-07803`

**Texto**

No comprovante, exibir o prazo de validade do vínculo de conta.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Gestão

**Proposta**

**Instituição**

ID

**Justificativa**

IN BCB 760

**ID**

`REQ.VC-08401`

**Texto**

Permitir a alteração do prazo de validade do vínculo da conta.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Gestão

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-08402`

**Texto**

Informar o usuário, no momento da confirmação da alteração, que as alterações do prazo vínculo de conta podem afetar os pagamentos automáticos.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Gestão

**Proposta**

**Instituição**

ID

**Justificativa**

IN BCB 760

**ID**

`REQ.VC-08403`

**Texto**

Permitir que o usuário altere os limites diário e/ou por transação do vínculo de conta.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Gestão

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-08404`

**Texto**

Observar a mesmas regras aplicáveis à etapa de **Confirmação** da jornada de vinculação de conta.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Gestão

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-08405`

**Texto**

Impedir a alteração do limite por transação com valor superior a R$ 500,00, salvo quando houver previsão diversa em contrato bilateral entre ITP e ID.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Gestão

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-08406`

**Texto**

Informar o usuário de que os limites do Pix serão considerados.

trueListe as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Gestão

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-08407`

**Texto**

Informar o usuário, antes da confirmação, de que as alterações do limite podem afetar os pagamentos agendados.   true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Gestão

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-08408`

**Texto**

Seguir a regulação vigente para efetivação da alteração.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Gestão

**Proposta**

**Instituição**

ID

**Justificativa**

IN BCB 760

**ID**

`REQ.VC-08409`

**Texto**

Se o usuário tiver compartilhado o saldo e limite da conta através da Jornada Otimizada, informar que a data de validade do compartilhamento será automaticamente atualizada conforme a nova data de validade do vínculo de conta.
