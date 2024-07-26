<div align="center">
  <div>
    <img height = "150" width = "150" src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/mysql/mysql-original-wordmark.svg" />
  </div>
</div>

<p style="text-align: justify;">Você está gerenciando um banco de dados para uma pequena loja que deseja acompanhar seus produtos, categorias e pedidos. Você terá três tabelas principais</p>

<ul>
  <li style="text-align: justify;">Categorias - Armazena as categorias dos produtos.r</li>
  <li style="text-align: justify;">Produtos - Armazena os produtos da empresa.</li>
  <li style="text-align: justify;">Pedidos - Armazena os pedidos feitos pelos clientes.</li>
</ul>

```sql
CREATE DATABASE LOJA;
```

```sql
CREATE TABLE CATEGORIA(

	ID INT PRIMARY KEY AUTO_INCREMENT,
    TIPO VARCHAR(255) NOT NULL UNIQUE

);
```

```sql
CREATE TABLE PRODUTO(

	ID INT PRIMARY KEY AUTO_INCREMENT,
    NOME VARCHAR(255) NOT NULL,
    PRECO FLOAT(10,2) NOT NULL,
    ID_CATEGORIA INT NOT NULL,
    FOREIGN KEY (ID_CATEGORIA)
    REFERENCES CATEGORIA(ID)

);
```

```sql
CREATE TABLE PEDIDO(

	ID INT PRIMARY KEY AUTO_INCREMENT,
    DATAPEDIDO DATE NOT NULL,
    ID_PRODUTO INT NOT NULL,
    FOREIGN KEY (ID_PRODUTO)
    REFERENCES PRODUTO(ID)

);
```

```sql
INSERT INTO CATEGORIA(TIPO)
VALUES
('Eletrônicos'),
('Mobília'),
('Roupas');
```

```sql
INSERT INTO PRODUTO(NOME, PRECO, ID_CATEGORIA)
VALUES
('Laptop', 999.99, 1),
('Pc', 150.00, 2),
('Camiseta', 20.00, 3);
```

```sql
ALTER TABLE PEDIDO 
ADD COLUMN QUANTIDADE INT NOT NULL;
```

```sql
INSERT INTO PEDIDO(DATAPEDIDO, ID_PRODUTO, QUANTIDADE)
VALUES
('2024-07-01', 1, 2),
('2024-07-02', 2, 1),
('2024-07-03', 3, 5);
```

<ul>
  <li style="text-align: justify;">Executar a consulta INNER JOIN: Execute a consulta com INNER JOIN para visualizar os pedidos com detalhes dos produtos e categorias.</li>
  <li style="text-align: justify;">Criar e consultar a View: Crie a view OrderDetails e faça uma consulta para verificar os dados.</li>
  <li style="text-align: justify;">Criar e usar a Stored Procedure: Crie a stored procedure AddOrder e insira um novo pedido usando a procedure.</li>
</ul>

```sql
SELECT PRD.NOME AS 'PRODUTO', PRD.PRECO,
C.TIPO AS 'CATEGORIA', 
PDD.DATAPEDIDO AS 'DATA', PDD.QUANTIDADE
FROM
PRODUTO PRD
INNER JOIN CATEGORIA C
ON
PRD.ID_CATEGORIA = C.ID
INNER JOIN PEDIDO PDD
ON
PDD.ID_PRODUTO = PRD.ID;
```

```sql
CREATE VIEW VW_DETALHE_PEDIDO AS
	SELECT PRD.NOME AS 'PRODUTO', PRD.PRECO,
    PDD.DATAPEDIDO AS 'DATA', PDD.QUANTIDADE
    FROM PEDIDO PDD
    INNER JOIN PRODUTO PRD
    ON
    PRD.ID = PDD.ID_PRODUTO;
```

```sql
DELIMITER $

CREATE PROCEDURE ADDPEDIDO(DTPEDIDO DATE, IDPRODUTO INT, QTDPRODUTO INT)
	BEGIN
		INSERT INTO PEDIDO(DATAPEDIDO, ID_PRODUTO, QUANTIDADE)
		VALUES
		(DTPEDIDO, IDPRODUTO, QTDPRODUTO);
	END$
```