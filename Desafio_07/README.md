<div align="center">
  <div>
    <img height = "150" width = "150" src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/mysql/mysql-original-wordmark.svg" />
  </div>
</div>

<p style="text-align: justify;">Você está gerenciando um banco de dados para uma loja de eletrônicos e precisa acompanhar suas vendas, produtos e clientes. Você terá três tabelas principais:</p>

<ul>
  <li style="text-align: justify;">Clientes - Armazena informações sobre os clientes.</li>
  <li style="text-align: justify;">Produtos - Armazena informações sobre os produtos.</li>
  <li style="text-align: justify;">Vendas - Armazena informações sobre as vendas realizadas.</li>
</ul>

<p style="text-align: justify;">Estrutura das Tabelas</p>

<ul>

  <p style="text-align: justify;">Clientes</p>

  <li style="text-align: justify;">ID_CLIENTE: INT, chave primária, auto-incremento</li>
  <li style="text-align: justify;">NOME: VARCHAR(100), não nulo</li>
  <li style="text-align: justify;">EMAIL: VARCHAR(100), não nulo</li>

</ul>

<ul>

  <p style="text-align: justify;">Produtos</p>

  <li style="text-align: justify;">ID_PRODUTO: INT, chave primária, auto-incremento</li>
  <li style="text-align: justify;">NOME: VARCHAR(100), não nulo</li>
  <li style="text-align: justify;">PRECO: DECIMAL(10, 2), não nulo</li>
  <li style="text-align: justify;">CATEGORIA: VARCHAR(50), não nulo</li>

</ul>

<ul>

  <p style="text-align: justify;">Vendas</p>

  <li style="text-align: justify;">ID_VENDA: INT, chave primária, auto-incremento</li>
  <li style="text-align: justify;">ID_CLIENTE: INT, chave estrangeira referenciando ID_CLIENTE em Clientes</li>
  <li style="text-align: justify;">ID_PRODUTO: INT, chave estrangeira referenciando ID_PRODUTO em Produtos</li>
  <li style="text-align: justify;">DATA_VENDA: DATE, não nulo</li>
  <li style="text-align: justify;">QUANTIDADE: INT, não nulo</li>

</ul>

<p style="text-align: justify;">Inserção de Dados</p>

<ul>

  <p style="text-align: justify;">Clientes</p>

  <li style="text-align: justify;">João Silva, joao.silva@example.com</li>
  <li style="text-align: justify;">Maria Oliveira, maria.oliveira@example.com</li>
  <li style="text-align: justify;">Pedro Santos, pedro.santos@example.com</li>

</ul>

<ul>

  <p style="text-align: justify;">Produtos</p>

  <li style="text-align: justify;">Nome: "Smartphone", Preço: 1200.00, Categoria: "Eletrônicos"</li>
  <li style="text-align: justify;">Nome: "Notebook", Preço: 3000.00, Categoria: "Eletrônicos"</li>
  <li style="text-align: justify;">Nome: "Cadeira", Preço: 250.00, Categoria: "Móveis"</li>

</ul>

<ul>

  <p style="text-align: justify;">Vendas</p>

  <li style="text-align: justify;">Data Venda: 2024-07-10, Cliente: João Silva, Produto: Smartphone, Quantidade: 1</li>
  <li style="text-align: justify;">Data Venda: 2024-07-12, Cliente: Maria Oliveira, Produto: Notebook, Quantidade: 1</li>
  <li style="text-align: justify;">Data Venda: 2024-07-15, Cliente: Pedro Santos, Produto: Cadeira, Quantidade: 2</li>

</ul>

<p style="text-align: justify;">Tarefas</p>

<ul>
  <li style="text-align: justify;">Criar as tabelas: Crie as tabelas Clientes, Produtos e Vendas conforme a descrição fornecida.</li>
  <li style="text-align: justify;">Inserir os dados: Insira os dados nas tabelas conforme a descrição fornecida.</li>
  <li style="text-align: justify;">Executar consultas com filtros:</li>

  <ul>
    <li style="text-align: justify;">Liste todas as vendas realizadas em julho de 2024.</li>
    <li style="text-align: justify;">Liste todas as vendas realizadas por um cliente específico (por exemplo, "João Silva").</li>
    <li style="text-align: justify;">Liste todos os produtos que foram vendidos mais de uma vez.</li>
    <li style="text-align: justify;">Liste todos os clientes que compraram produtos da categoria "Eletrônicos".</li>
  </ul>

  <li style="text-align: justify;">Criar uma view: Crie uma view que mostre detalhes das vendas, incluindo o nome do cliente, o nome do produto e a quantidade vendida.</li>
  <li style="text-align: justify;">Criar uma stored procedure: Crie uma stored procedure para registrar uma nova venda.</li>

</ul>

```sql
CREATE DATABASE ELETRONICA;

USE ELETRONICA;

CREATE TABLE CLIENTE(

	ID INT PRIMARY KEY AUTO_INCREMENT,
    NOME VARCHAR(100) NOT NULL,
    EMAIL VARCHAR(100) NOT NULL

);

CREATE TABLE PRODUTO(

	ID INT PRIMARY KEY AUTO_INCREMENT,
    NOME VARCHAR(100) NOT NULL,
    PRECO FLOAT(10,2) NOT NULL,
    CATEGORIA VARCHAR(50) NOT NULL

);

CREATE TABLE VENDA(

	ID INT PRIMARY KEY AUTO_INCREMENT,
    DATAVENDA DATE NOT NULL,
    QUANTIDADE INT NOT NULL,
    ID_CLIENTE INT NOT NULL,
	ID_PRODUTO INT NOT NULL,
    FOREIGN KEY (ID_CLIENTE)
    REFERENCES CLIENTE(ID),
    FOREIGN KEY (ID_PRODUTO)
    REFERENCES PRODUTO(ID)

);

INSERT INTO CLIENTE(NOME, EMAIL)
VALUES
('João Silva', 'joao.silva@example.com'),
('Maria Oliveira', 'maria.oliveira@example.com'),
('Pedro Santos', 'pedro.santos@example.com');

SELECT * FROM CLIENTE;

INSERT INTO PRODUTO(NOME, PRECO, CATEGORIA)
VALUES
('Smartphone', 1200.00, 'Eletrônicos'),
('Notebook', 3000.00, 'Eletrônicos'),
('Cadeira', 250.00, 'Móveis');

SELECT * FROM PRODUTO;

INSERT INTO VENDA(DATAVENDA, ID_CLIENTE, ID_PRODUTO, QUANTIDADE)
VALUES
('2024-07-10', 1, 1, 1),
('2024-07-12', 2, 2, 1),
('2024-07-15', 3, 3, 2);

SELECT * FROM VENDA;

SELECT V.DATAVENDA AS 'DATA DA VENDA', 
C.NOME AS 'CLIENTE',
P.NOME AS 'PRODUTO',
V.QUANTIDADE, 
P.CATEGORIA
FROM VENDA V
INNER JOIN CLIENTE C
ON
C.ID = V.ID_CLIENTE
INNER JOIN PRODUTO P
ON
P.ID = V.ID_PRODUTO
WHERE
V.DATAVENDA BETWEEN '2024-07-10' AND '2024-07-31';

SELECT V.DATAVENDA AS 'DATA DA VENDA', 
C.NOME AS 'CLIENTE',
P.NOME AS 'PRODUTO',
V.QUANTIDADE, 
P.CATEGORIA
FROM VENDA V
INNER JOIN CLIENTE C
ON
C.ID = V.ID_CLIENTE
INNER JOIN PRODUTO P
ON
P.ID = V.ID_PRODUTO
WHERE
C.NOME = 'João Silva';

SELECT P.NOME AS 'PRODUTO',
V.QUANTIDADE
FROM PRODUTO P
INNER JOIN VENDA V
ON
P.ID = V.ID_PRODUTO
WHERE
V.QUANTIDADE > 1;

SELECT C.NOME,
P.NOME AS 'PRODUTO', P.CATEGORIA
FROM CLIENTE C
INNER JOIN VENDA V
ON
C.ID = V.ID_CLIENTE
INNER JOIN PRODUTO P
ON
P.ID = V.ID_PRODUTO
WHERE
P.CATEGORIA = 'Eletrônicos';

CREATE VIEW VW_RELATORIO_VENDA AS
	SELECT V.DATAVENDA AS 'DATA DA VENDA',
    C.NOME AS 'CLIENTE',
    P.NOME AS 'PRODUTO', 
    V.QUANTIDADE
    FROM VENDA V
    INNER JOIN CLIENTE C
    ON
    C.ID = V.ID_CLIENTE
    INNER JOIN PRODUTO P
    ON
    P.ID = V.ID_PRODUTO;
    
SELECT * FROM VW_RELATORIO_VENDA;

DELIMITER $

CREATE PROCEDURE ADDVENDA(DTVENDA DATE, QTD INT, IDCLIENTE INT, IDPRODUTO INT)
	BEGIN
		INSERT INTO VENDA(DATAVENDA, QUANTIDADE, ID_CLIENTE, ID_PRODUTO)
        VALUES
        (DTVENDA, QTD, IDCLIENTE, IDPRODUTO);
	END $
    
CALL ADDVENDA('2024-07-29', 5, 1, 3);

SELECT * FROM VENDA;
```