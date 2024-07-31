<div align="center">
  <div>
    <img height = "150" width = "150" src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/mysql/mysql-original-wordmark.svg" />
  </div>
</div>

<p style="text-align: justify;">Criar um sistema simples de registro de estoque com uma tabela para produtos e outra para histórico de alterações de estoque. Sempre que a quantidade de um produto for atualizada, um registro deve ser inserido na tabela de histórico.</p>

<p style="text-align: justify;">Estrutura das Tabelas</p>

<ul>

  <p style="text-align: justify;">Produto</p>

  <li style="text-align: justify;">ID (INT, PK, Auto Increment)</li>
  <li style="text-align: justify;">Nome (VARCHAR(100), NOT NULL)</li>
  <li style="text-align: justify;">Quantidade (INT, NOT NULL)</li>

</ul>

<ul>

  <p style="text-align: justify;">HistoricoEstoque</p>

  <li style="text-align: justify;">ID (INT, PK, Auto Increment)</li>
  <li style="text-align: justify;">ID_Produto (INT, FK para Produto)</li>
  <li style="text-align: justify;">DataAlteracao (DATETIME, NOT NULL)</li>
  <li style="text-align: justify;">QuantidadeAntiga (INT, NOT NULL)</li>
  <li style="text-align: justify;">QuantidadeNova (INT, NOT NULL)</li>

</ul>

<p style="text-align: justify;">Tarefa</p>

<p style="text-align: justify;">Criar um trigger chamado trg_AtualizaEstoque na tabela Produto que insira um registro na tabela HistoricoEstoque sempre que a quantidade de um produto for atualizada.</p>

```sql
CREATE DATABASE ESTOQUE;

USE ESTOQUE;

CREATE TABLE PRODUTO(

	ID INT PRIMARY KEY AUTO_INCREMENT,
    NOME VARCHAR(100) NOT NULL,
    QUANTIDADE INT NOT NULL

);

CREATE TABLE HISTORICOESTOQUE(

	ID INT PRIMARY KEY AUTO_INCREMENT,
    DATAALTERACAO DATETIME NOT NULL,
    QUANTIDADEANTIGA INT NOT NULL,
    QUANTIDADENOVA INT NOT NULL,
    ID_PRODUTO INT NOT NULL,
    FOREIGN KEY (ID_PRODUTO)
    REFERENCES PRODUTO(ID)

);

INSERT INTO PRODUTO(NOME, QUANTIDADE)
VALUES 
('CELULAR', 10),
('PC', 5),
('TECLADO', 20),
('MOUSE', 20);

SELECT * FROM PRODUTO;

DELIMITER $

CREATE TRIGGER TRG_ATUALIZAESTOQUE
BEFORE UPDATE ON PRODUTO
FOR EACH ROW
BEGIN
	INSERT INTO HISTORICOESTOQUE(DATAALTERACAO, QUANTIDADEANTIGA, QUANTIDADENOVA, ID_PRODUTO)
    VALUES (SYSDATE(), OLD.QUANTIDADE, NEW.QUANTIDADE, OLD.ID);
END$

SELECT * FROM PRODUTO;
SELECT * FROM HISTORICOESTOQUE;

UPDATE PRODUTO SET QUANTIDADE = QUANTIDADE + 60
WHERE
ID = 4;

SELECT PRODUTO.NOME AS 'PRODUTO',
HISTORICOESTOQUE.QUANTIDADENOVA AS 'QUANTIDADE ATUAL',
HISTORICOESTOQUE.QUANTIDADEANTIGA AS 'QUANTIDADE ANTERIOR',
HISTORICOESTOQUE.DATAALTERACAO AS 'DATA DA ULTIMA ALTERACAO'
FROM HISTORICOESTOQUE
INNER JOIN PRODUTO
ON
PRODUTO.ID = HISTORICOESTOQUE.ID_PRODUTO;
```