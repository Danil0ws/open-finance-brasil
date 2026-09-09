# Escopo da API de Pagamentos - v5.0.0 - [SV] Pagamentos

> Os serviços de pagamento suportados pela API de Pagamentos compreendem as formas de iniciação de pagamentos, conforme detalhado abaixo:

## 1\. Pagamentos Pix por tipo de execução

-   Pagamentos Pix imediatos
    
-   Pagamentos Pix agendados
    
-   Pagamentos Pix agendados recorrentes
    

## 2\. Pagamentos Pix por meio de QR Code

Válido independentemente da forma de captura pelo usuário (ex.: leitura por câmera, código “copia e cola”, por aproximação/NFC ou tecnologias equivalentes).

### 2.a QR Code Estático

-   Pix Saque
    
-   QR Code sem valor predefinido
    
-   QR Code com valor fixo
    
-   QR Code reutilizável
    
-   QR Code com identificador de transação (TxID)
    
-   QR Code pessoal, comercial ou institucional
    

### 2.b QR Code Dinâmico

1.  Pix Saque e Troco
    
2.  -   COB com valor fixo
        
    -   COB com valor variável
        
3.  -   COBV com valor e vencimento
        
    -   COBV com expiração após o vencimento
        
    -   COBV com quaisquer combinações de abatimento, desconto, multa e juros
        
    -   COBV de uso único ou reutilizável (url de cobrança é reutilizável)
        

### 2.c Pix Composto

1.  Contemplando todos os serviços inclusos nos itens 2.a e 2.b
    
2.  Não é aplicável ao Open Finance a criação de recorrências de Pix Automático a partir deste tipo de QR Code
