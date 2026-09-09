# Escopo da API Pagamentos - v5.0.0-rc.1 - [SV] Pagamentos

Os serviços de pagamento suportados pela API de Pagamentos compreendem as formas de iniciação de pagamentos¹, conforme detalhado abaixo:

### 1\. Pagamentos Pix por tipo de execução

a) Pagamentos Pix imediatos;  
b) Pagamentos Pix agendados;  
c) Pagamentos Pix agendados recorrentes.

### 2\. Pagamentos Pix por meio de QR Code, independentemente da forma de captura pelo usuário (ex.: leitura por câmera, código “copia e cola”, por aproximação/NFC ou tecnologias equivalentes).

#### a) QR Code Estático

i. Pix Saque;  
ii. QR Code sem valor predefinido;  
iii. QR Code com valor fixo;  
iv. QR Code reutilizável;  
v. QR Code com identificador de transação (TxID);  
vi. QR Code pessoal, comercial ou institucional.

#### b) QR Code Dinâmico

i. Pix Saque e Troco;  
ii. Cobrança Pix sem vencimento (COB)²

• COB com valor fixo;  
• COB com valor variável;

iii. Cobrança Pix com vencimento (COBV)

• COBV com valor e vencimento;  
• COBV com expiração após o vencimento;  
• COBV com quaisquer combinações de abatimento, desconto, multa e juros;  
• COBV de uso único ou reutilizável (url de cobrança é reutilizável).

#### c) Pix Composto

i. Contempla um QRCode com mais de um serviço na mesma jornada do usuário;  
ii. Esse tipo de QRCode deve ser passível de uso no Open Finance com todos os serviços inclusos nos itens a) e b).

\- Pagamentos imediatos e agendados presentes no QRCode poderão ser pagos via Open Finance

iii. Não é aplicável ao Open Finance a criação de autorização de recorrências via Pix Automático.

##### Observações:

¹ Os produtos indicados nesta lista observam as formas de iniciação já estabelecidas no Manual de Iniciação de Pagamentos do Pix.  
²O COB pode conter informações adicionais ou não (i.e.: mensagem ao pagador) e podem ser configurado como de uso único ou de url reutilizável.
