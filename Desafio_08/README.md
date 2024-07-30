<div align="center">
  <div>
    <img height = "150" width = "150" src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/mysql/mysql-original-wordmark.svg" />
  </div>
</div>

<p style="text-align: justify;">Você está gerenciando um banco de dados para uma loja online. O banco de dados deve acompanhar informações sobre clientes, produtos, categorias de produtos, pedidos e detalhes dos pedidos. O exercício envolve as seguintes tabelas:</p>

<ul>
  <li style="text-align: justify;">Clientes - Armazena informações sobre os clientes.</li>
  <li style="text-align: justify;">Produtos - Armazena informações sobre os produtos.</li>
  <li style="text-align: justify;">Categorias - Armazena informações sobre as categorias dos produtos.</li>
  <li style="text-align: justify;">Pedidos - Armazena informações sobre os pedidos realizados.</li>
  <li style="text-align: justify;">Detalhes_Pedidos - Armazena informações detalhadas sobre os itens em cada pedido.</li>
</ul>

<p style="text-align: justify;">Estrutura das Tabelas</p>

<ul>

  <p style="text-align: justify;">Clientes</p>

  <li style="text-align: justify;">ID_CLIENTE: INT, chave primária, auto-incremento</li>
  <li style="text-align: justify;">NOME: VARCHAR(100), não nulo</li>
  <li style="text-align: justify;">EMAIL: VARCHAR(100), não nulo</li>

</ul>

<ul>

  <p style="text-align: justify;">Categorias</p>

  <li style="text-align: justify;">ID_CATEGORIA: INT, chave primária, auto-incremento</li>
  <li style="text-align: justify;">NOME: VARCHAR(100), não nulo</li>

</ul>

<ul>

  <p style="text-align: justify;">Produtos</p>

  <li style="text-align: justify;">ID_PRODUTO: INT, chave primária, auto-incremento</li>
  <li style="text-align: justify;">NOME: VARCHAR(100), não nulo</li>
  <li style="text-align: justify;">PRECO: DECIMAL(10, 2), não nulo</li>
  <li style="text-align: justify;">ID_CATEGORIA: INT, chave estrangeira referenciando ID_CATEGORIA em Categorias</li>

</ul>

<ul>

  <p style="text-align: justify;">Pedidos</p>

  <li style="text-align: justify;">ID_PEDIDO: INT, chave primária, auto-incremento</li>
  <li style="text-align: justify;">ID_CLIENTE: INT, chave estrangeira referenciando ID_CLIENTE em Clientes</li>
  <li style="text-align: justify;">DATA_PEDIDO: DATE, não nulo</li>

</ul>

<ul>

  <p style="text-align: justify;">Detalhes_Pedidos</p>

  <li style="text-align: justify;">ID_DETALHE: INT, chave primária, auto-incremento</li>
  <li style="text-align: justify;">ID_PEDIDO: INT, chave estrangeira referenciando ID_PEDIDO em Pedidos</li>
  <li style="text-align: justify;">ID_PRODUTO: INT, chave estrangeira referenciando ID_PRODUTO em Produtos</li>
  <li style="text-align: justify;">QUANTIDADE: INT, não nulo</li>
  <li style="text-align: justify;">PRECO_UNITARIO: DECIMAL(10, 2), não nulo</li>

</ul>

<p style="text-align: justify;">Inserção de Dados</p>

<ul>

  <p style="text-align: justify;">Clientes</p>

  <li style="text-align: justify;">João Silva, joao.silva@example.com</li>
  <li style="text-align: justify;">Maria Oliveira, maria.oliveira@example.com</li>
  <li style="text-align: justify;">Pedro Santos, pedro.santos@example.com</li>
  <li style="text-align: justify;">Ana Clara, ana.clara@example.com</li>
  <li style="text-align: justify;">Carlos Eduardo, carlos.eduardo@example.com</li>
  <li style="text-align: justify;">Fernanda Lima, fernanda.lima@example.com</li>

</ul>

<ul>

  <p style="text-align: justify;">Categorias</p>

  <li style="text-align: justify;">Eletrônicos</li>
  <li style="text-align: justify;">Móveis</li>
  <li style="text-align: justify;">Livros</li>
  <li style="text-align: justify;">Roupas</li>
  <li style="text-align: justify;">Brinquedos</li>

</ul>

<ul>

  <p style="text-align: justify;">Produtos</p>

  <li style="text-align: justify;">Smartphone, 1200.00, Eletrônicos</li>
  <li style="text-align: justify;">Notebook, 3000.00, Eletrônicos</li>
  <li style="text-align: justify;">Cadeira, 250.00, Móveis</li>
  <li style="text-align: justify;">Mesa, 450.00, Móveis</li>
  <li style="text-align: justify;">Livro de MySQL, 80.00, Livros</li>
  <li style="text-align: justify;">Camisa, 50.00, Roupas</li>
  <li style="text-align: justify;">Boneca, 120.00, Brinquedos</li>
  <li style="text-align: justify;">Tablet, 800.00, Eletrônicos</li>
  <li style="text-align: justify;">Sofá, 1500.00, Móveis</li>
  <li style="text-align: justify;">Livro de Java, 100.00, Livros</li>

</ul>

<ul>

  <p style="text-align: justify;">Pedidos</p>

  <li style="text-align: justify;">2024-07-10, João Silva</li>
  <li style="text-align: justify;">2024-07-12, Maria Oliveira</li>
  <li style="text-align: justify;">2024-07-15, Pedro Santos</li>
  <li style="text-align: justify;">2024-07-20, Ana Clara</li>
  <li style="text-align: justify;">2024-07-22, Carlos Eduardo</li>
  <li style="text-align: justify;">2024-07-25, Fernanda Lima</li>

</ul>

<ul>

  <p style="text-align: justify;">Detalhes_Pedidos</p>

  <li style="text-align: justify;">Pedido 1, Smartphone, 1, 1200.00</li>
  <li style="text-align: justify;">Pedido 1, Livro de MySQL, 2, 80.00</li>
  <li style="text-align: justify;">Pedido 2, Notebook, 1, 3000.00</li>
  <li style="text-align: justify;">Pedido 3, Cadeira, 4, 250.00</li>
  <li style="text-align: justify;">Pedido 3, Mesa, 1, 450.00</li>
  <li style="text-align: justify;">Pedido 4, Camisa, 3, 50.00</li>
  <li style="text-align: justify;">Pedido 4, Boneca, 2, 120.00</li>
  <li style="text-align: justify;">Pedido 5, Tablet, 1, 800.00</li>
  <li style="text-align: justify;">Pedido 5, Sofá, 1, 1500.00</li>
  <li style="text-align: justify;">Pedido 6, Livro de Java, 1, 100.00</li>
  <li style="text-align: justify;">Pedido 6, Livro de MySQL, 1, 80.00</li>

</ul>

<p style="text-align: justify;">Requisitos do Exercício</p>

<ul>
  <li style="text-align: justify;">Criação das Tabelas: Crie as tabelas mencionadas acima.</li>
  <li style="text-align: justify;">Inserção dos Dados: Insira os registros mencionados acima.</li>
  <li style="text-align: justify;">Consultas com Filtros:</li>

  <ul>
    <li style="text-align: justify;">Selecione todos os pedidos realizados no mês de julho de 2024.</li>
    <li style="text-align: justify;">Selecione todos os pedidos realizados por um cliente específico.</li>
    <li style="text-align: justify;">Selecione todos os produtos da categoria "Eletrônicos" que foram vendidos.</li>
    <li style="text-align: justify;">Selecione todos os clientes que compraram produtos da categoria "Livros".</li>
  </ul>

  <li style="text-align: justify;">Criação da View: Crie uma view que exiba o relatório de vendas.</li>
  <li style="text-align: justify;">Stored Procedure: Crie uma stored procedure que permita registrar um novo pedido e atualizar a quantidade de um produto no estoque.
</li>

</ul>

```sql
CREATE DATABASE ECOMMERCE;

USE ECOMMERCE;

CREATE TABLE CLIENTE(

	ID INT PRIMARY KEY AUTO_INCREMENT,
    NOME VARCHAR(100) NOT NULL,
    EMAIL VARCHAR(100) NOT NULL,
    SEXO ENUM('F', 'M') NOT NULL,
    CPF CHAR(11) NOT NULL UNIQUE

);

CREATE TABLE TIPOTELEFONE(

	ID INT PRIMARY KEY AUTO_INCREMENT,
    TIPO CHAR(3) NOT NULL UNIQUE

);

CREATE TABLE TELEFONE(

	ID INT PRIMARY KEY AUTO_INCREMENT,
    NUMERO CHAR(11) NOT NULL,
    ID_TIPOTELEFONE INT NOT NULL,
    FOREIGN KEY (ID_TIPOTELEFONE)
    REFERENCES TIPOTELEFONE (ID),
    ID_CLIENTE INT NOT NULL,
    FOREIGN KEY (ID_CLIENTE)
    REFERENCES CLIENTE(ID)

);

CREATE TABLE ESTADO(

	ID INT PRIMARY KEY AUTO_INCREMENT,
    NOME CHAR(2) NOT NULL UNIQUE

);

CREATE TABLE ENDERECO(

	ID INT PRIMARY KEY AUTO_INCREMENT,
    RUA VARCHAR(100) NOT NULL,
    NUMERO CHAR(100) NOT NULL,
    BAIRRO VARCHAR(100) NOT NULL,
    CIDADE VARCHAR(100) NOT NULL,
    ID_ESTADO INT NOT NULL,
    FOREIGN KEY (ID_ESTADO)
    REFERENCES ESTADO(ID),
    ID_CLIENTE INT NULL UNIQUE,
    FOREIGN KEY (ID_CLIENTE)
    REFERENCES CLIENTE (ID)

);

CREATE TABLE CATEGORIA(

	ID INT PRIMARY KEY AUTO_INCREMENT,
    NOME VARCHAR(100) NOT NULL UNIQUE

);

CREATE TABLE PRODUTO(

	ID INT PRIMARY KEY AUTO_INCREMENT,
    NOME VARCHAR(100) NOT NULL,
    PRECO FLOAT(10,2) NOT NULL,
    ID_CATEGORIA INT NOT NULL,
    FOREIGN KEY (ID_CATEGORIA)
    REFERENCES CATEGORIA(ID)

);

CREATE TABLE PEDIDO(

	ID INT PRIMARY KEY AUTO_INCREMENT,
    DATAPEDIDO DATE NOT NULL,
    ID_CLIENTE INT NOT NULL,
    FOREIGN KEY (ID_CLIENTE)
    REFERENCES CLIENTE(ID)

);

CREATE TABLE DETALHEPEDIDO(

	ID INT PRIMARY KEY AUTO_INCREMENT,
    ID_PEDIDO INT NOT NULL,
    ID_PRODUTO INT NOT NULL,
    QUANTIDADE INT NOT NULL,
    PRECOUNITARIO FLOAT(10,2) NOT NULL,
    FOREIGN KEY (ID_PEDIDO)
    REFERENCES PEDIDO(ID),
    FOREIGN KEY (ID_PRODUTO)
    REFERENCES PRODUTO (ID)

);

INSERT INTO ESTADO(NOME)
VALUES
('AC'),
('AL'),
('AP'),
('AM'),
('BA'),
('CE'),
('DF'),
('ES'),
('GO'),
('MA'),
('MT'),
('MS'),
('MG'),
('PA'),
('PB'),
('PR'),
('PE'),
('PI'),
('RJ'),
('RN'),
('RS'),
('RO'),
('RR'),
('SC'),
('SP'),
('SE'),
('TO');

SELECT * FROM ESTADO;

INSERT INTO CLIENTE(NOME, EMAIL, SEXO, CPF)
VALUES
('João Silva', 'joao.silva@example.com', 'M', '78654462094'),
('Maria Oliveira', 'maria.oliveira@example.com', 'F', '36815562026'),
('Pedro Santos', 'pedro.santos@example.com', 'M', '13570742040'),
('Ana Clara', 'ana.clara@example.com', 'F', '32151423093'),
('Carlos Eduardo', 'carlos.eduardo@example.com', 'M', '43579073060'),
('Fernanda Lima', 'fernanda.lima@example.com', 'F', '87524189010');

SELECT * FROM CLIENTE;

INSERT INTO TIPOTELEFONE(TIPO)
VALUES
('COM'),
('RES'),
('CEL');

SELECT * FROM TIPOTELEFONE;

DROP TABLE TELEFONE;

INSERT INTO TELEFONE(NUMERO, ID_TIPOTELEFONE, ID_CLIENTE)
VALUES
('89330677010', 2, 5),
('30137282052', 3, 6),
('40247090034', 1, 2),
('63907136063', 3, 4),
('21519781091', 3, 3),
('94120002004', 2, 1),
('87434245034', 1, 3),
('34162047006', 3, 1),
('65986185099', 2, 4),
('19050699014', 3, 2);

SELECT * FROM TELEFONE;

INSERT INTO ENDERECO(RUA, NUMERO, BAIRRO, CIDADE, ID_ESTADO, ID_CLIENTE)
VALUES
('Avenida Alameda Marechal Rondon', '142', 'Setor Granjeiro', 'Jataí', 9, 4),
('Rua Major Celso da Câmara Lima', '372', 'Cajueiro Seco', 'Jaboatão dos Guararapes', 17, 6),
('Rua Floriano Peixoto', '941', 'Nossa Senhora da Abadia', 'Uberaba', 13, 3),
('Avenida Santana', '153', 'Central', 'Santana', 3, 5),
('Rua Toledo', '596', 'Água Verde', 'Laranjeiras do Sul', 16, 1),
('11ª Travessa Nossa Senhora da Conceição', '815', 'Clima Bom', 'Maceió', 2, 2);

SELECT * FROM ENDERECO;

INSERT INTO CATEGORIA(NOME)
VALUES
('Eletrônicos'),
('Móveis'),
('Livros'),
('Roupas'),
('Brinquedos');

SELECT * FROM CATEGORIA;

INSERT INTO PRODUTO(NOME, PRECO, ID_CATEGORIA)
VALUES
('Smartphone', 1200.00, 1),
('Notebook', 3000.00, 1),
('Cadeira', 250.00, 2),
('Mesa', 450.00, 2),
('Livro de MySQL', 80.00, 3),
('Camisa', 50.00, 4),
('Boneca', 120.00, 5),
('Tablet', 800.00, 1),
('Sofá', 1500.00, 2),
('Livro de Java', 100.00, 3);

SELECT * FROM PRODUTO;

INSERT INTO PEDIDO(DATAPEDIDO, ID_CLIENTE)
VALUES
('2024-07-10', 1),
('2024-07-12', 2),
('2024-07-15', 3),
('2024-07-20', 4),
('2024-07-22', 5),
('2024-07-25', 6);

SELECT * FROM PEDIDO;

INSERT INTO DETALHEPEDIDO(ID_PEDIDO, ID_PRODUTO, QUANTIDADE, PRECOUNITARIO)
VALUES
(1, 1, 1, 1200.00),
(1, 5, 2, 80.00),
(2, 2, 1, 3000.00),
(3, 3, 4, 250.00),
(3, 4, 1, 450.00),
(4, 6, 3, 50.00),
(4, 7, 2, 120.00),
(5, 8, 1, 800.00),
(5, 9, 1, 1500.00),
(6, 10, 1, 100.00),
(6, 5, 1, 80.00);

SELECT * FROM DETALHEPEDIDO;

SELECT T.NUMERO AS 'TELEFONE',
TT.TIPO
FROM TELEFONE T
INNER JOIN TIPOTELEFONE TT
ON
TT.ID = T.ID_TIPOTELEFONE;

SELECT E.RUA, E.NUMERO, E.BAIRRO, E.CIDADE,
ES.NOME AS 'ESTADO'
FROM ENDERECO E
INNER JOIN ESTADO ES
ON
ES.ID = E.ID_ESTADO;

SELECT C.NOME AS 'CLIENTE', C.EMAIL, C.SEXO, C.CPF,
T.NUMERO AS 'TELEFONE', 
TT.TIPO
FROM CLIENTE C
INNER JOIN TELEFONE T
ON
C.ID = T.ID_CLIENTE
INNER JOIN TIPOTELEFONE TT
ON
TT.ID = T.ID_TIPOTELEFONE;

SELECT C.NOME AS 'CLIENTE', C.EMAIL, C.SEXO, C.CPF,
E.RUA, E.NUMERO, E.BAIRRO, E.CIDADE,
ES.NOME AS 'ESTADO'
FROM CLIENTE C
INNER JOIN ENDERECO E
ON
C.ID = E.ID_CLIENTE
INNER JOIN ESTADO ES
ON
ES.ID = E.ID_ESTADO;

SELECT * FROM PEDIDO;

SELECT PEDIDO.DATAPEDIDO AS 'DATA DO PEDIDO',
CLIENTE.NOME AS 'CLIENTE',
PRODUTO.NOME AS 'PRODUTO'
FROM DETALHEPEDIDO
INNER JOIN PEDIDO
ON
PEDIDO.ID = DETALHEPEDIDO.ID_PEDIDO
INNER JOIN PRODUTO
ON
PRODUTO.ID = DETALHEPEDIDO.ID_PRODUTO
INNER JOIN CLIENTE
ON
CLIENTE.ID = PEDIDO.ID_CLIENTE
WHERE
PEDIDO.DATAPEDIDO BETWEEN '2024-07-01' AND '2024-07-31';

SELECT PEDIDO.DATAPEDIDO AS 'DATA DO PEDIDO',
CLIENTE.NOME AS 'CLIENTE',
PRODUTO.NOME AS 'PRODUTO',
PRODUTO.PRECO AS 'PRECO DO PRODUTO'
FROM DETALHEPEDIDO
INNER JOIN PEDIDO
ON
PEDIDO.ID = DETALHEPEDIDO.ID_PEDIDO
INNER JOIN PRODUTO
ON
PRODUTO.ID = DETALHEPEDIDO.ID_PRODUTO
INNER JOIN CLIENTE
ON
CLIENTE.ID = PEDIDO.ID_CLIENTE
WHERE
CLIENTE.CPF = '13570742040';

SELECT PRODUTO.NOME AS 'PRODUTO',
CATEGORIA.NOME AS 'CATEGORIA'
FROM DETALHEPEDIDO
INNER JOIN PRODUTO
ON
PRODUTO.ID = DETALHEPEDIDO.ID_PRODUTO
INNER JOIN CATEGORIA
ON
CATEGORIA.ID = PRODUTO.ID_CATEGORIA
WHERE
CATEGORIA.NOME = 'Eletrônicos';

SELECT CLIENTE.NOME AS 'CLIENTE',
PRODUTO.NOME AS 'PRODUTO',
CATEGORIA.NOME AS 'CATEGORIA'
FROM DETALHEPEDIDO
INNER JOIN PRODUTO
ON
PRODUTO.ID = DETALHEPEDIDO.ID_PRODUTO
INNER JOIN CATEGORIA
ON
CATEGORIA.ID = PRODUTO.ID_CATEGORIA
INNER JOIN PEDIDO
ON
PEDIDO.ID = DETALHEPEDIDO.ID_PEDIDO
INNER JOIN CLIENTE
ON
CLIENTE.ID = PEDIDO.ID_CLIENTE
WHERE
CATEGORIA.NOME = 'Livros';

CREATE VIEW VW_RELATORIO_VENDAS AS
	SELECT PEDIDO.DATAPEDIDO AS 'DATA DO PEDIDO',
	CLIENTE.NOME AS 'CLIENTE', CLIENTE.EMAIL, CLIENTE.CPF,
	PRODUTO.NOME AS 'PRODUTO',
	ENDERECO.RUA, ENDERECO.NUMERO, ENDERECO.BAIRRO, ENDERECO.CIDADE,
	ESTADO.NOME AS 'ESTADO',
	PRODUTO.PRECO AS 'PRECO DO PRODUTO',
	CATEGORIA.NOME AS 'CATEGORIA DO PRODUTO',
	DETALHEPEDIDO.QUANTIDADE, DETALHEPEDIDO.PRECOUNITARIO AS 'PRECO UNITARIO'
	FROM DETALHEPEDIDO
	INNER JOIN PEDIDO
	ON
	PEDIDO.ID = DETALHEPEDIDO.ID_PEDIDO
	INNER JOIN PRODUTO
	ON
	PRODUTO.ID = DETALHEPEDIDO.ID_PRODUTO
	INNER JOIN CATEGORIA
	ON
	CATEGORIA.ID = PRODUTO.ID_CATEGORIA
	INNER JOIN CLIENTE
	ON
	CLIENTE.ID = PEDIDO.ID_CLIENTE
	INNER JOIN ENDERECO
	ON
	CLIENTE.ID = ENDERECO.ID_CLIENTE
	INNER JOIN ESTADO
	ON
	ESTADO.ID = ENDERECO.ID_ESTADO;
    
SELECT * FROM VW_RELATORIO_VENDAS;

DELIMITER $

CREATE PROCEDURE NOVO_PEDIDO(
    IN CLIENTE_ID INT, 
    IN DATA_PED DATE, 
    IN PRODUTO_ID INT, 
    IN QTD INT, 
    IN PRECO_UNIT DECIMAL(10, 2))
BEGIN
    DECLARE PEDIDO_ID INT;
    
    -- Inserir o novo pedido
    INSERT INTO PEDIDO (ID_CLIENTE, DATAPEDIDO)
    VALUES (CLIENTE_ID, DATA_PED);
    
    -- Obter o ID do pedido recém-criado
    SET PEDIDO_ID = LAST_INSERT_ID();
    
    -- Inserir os detalhes do pedido
    INSERT INTO DETALHEPEDIDO (ID_PEDIDO, ID_PRODUTO, QUANTIDADE, PRECOUNITARIO)
    VALUES (PEDIDO_ID, PRODUTO_ID, QTD, PRECO_UNIT);
    
    -- Atualizar a quantidade do produto
    UPDATE PRODUTO
    SET QUANTIDADE = QUANTIDADE - QTD
    WHERE ID = PRODUTO_ID;
END $

DROP PROCEDURE NOVO_PEDIDO;

DELIMITER ;

CALL NOVO_PEDIDO(1, '2024-07-29', 1, 2, 1200.00);
```