<div align="center">
  <div>
    <img height = "150" width = "150" src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/mysql/mysql-original-wordmark.svg" />
  </div>
</div>

<p style="text-align: justify;">Você está gerenciando um banco de dados para uma biblioteca que deseja acompanhar seus livros, autores e empréstimos. Você terá três tabelas principais:</p>

<ul>
  <li style="text-align: justify;">Autores - Armazena informações sobre os autores</li>
  <li style="text-align: justify;">Livros - Armazena informações sobre os livros.</li>
  <li style="text-align: justify;">Empréstimos - Armazena informações sobre os empréstimos de livros.</li>
</ul>

<p style="text-align: justify;">Estrutura das tabelas</p>

<ul>

  <p style="text-align: justify;">Autores</p>

  <li style="text-align: justify;">ID_AUTOR: INT, chave primária, auto-incremento</li>
  <li style="text-align: justify;">NOME: VARCHAR(100), não nulo</li>

</ul>

<ul>

  <p style="text-align: justify;">Livros</p>

  <li style="text-align: justify;">ID_LIVRO: INT, chave primária, auto-incremento</li>
  <li style="text-align: justify;">TÍTULO: VARCHAR(100), não nulo</li>
  <li style="text-align: justify;">ID_AUTOR: INT, chave estrangeira referenciando ID_AUTOR em Autores</li>
  <li style="text-align: justify;">GÊNERO: VARCHAR(50), não nulo</li>

</ul>

<ul>

  <p style="text-align: justify;">Empréstimos</p>

  <li style="text-align: justify;">ID_EMPRÉSTIMO: INT, chave primária, auto-incremento</li>
  <li style="text-align: justify;">ID_LIVRO: INT, chave estrangeira referenciando ID_LIVRO em Livros</li>
  <li style="text-align: justify;">DATA_EMPRÉSTIMO: DATE, não nulo</li>
  <li style="text-align: justify;">DATA_DEVOLUÇÃO: DATE, pode ser nulo</li>
  <li style="text-align: justify;">NOME_CLIENTE: VARCHAR(100), não nulo</li>

</ul>

<p style="text-align: justify;">Inserção de Dados
</p>

<ul>

  <p style="text-align: justify;">Autores</p>

  <li style="text-align: justify;">João Silva
</li>
  <li style="text-align: justify;">Maria Oliveira
</li>
  <li style="text-align: justify;">Pedro Santos
</li>

</ul>

<ul>

  <p style="text-align: justify;">Livros</p>

  <li style="text-align: justify;">Título: "Aprendendo MySQL", Autor: João Silva, Gênero: Tecnologia</li>
  <li style="text-align: justify;">Título: "Introdução à Programação", Autor: Maria Oliveira, Gênero: Educação</li>
  <li style="text-align: justify;">Título: "História do Brasil", Autor: Pedro Santos, Gênero: História</li>

</ul>

<ul>

  <p style="text-align: justify;">Empréstimos</p>

  <li style="text-align: justify;">Data Empréstimo: 2024-07-10, Livro: "Aprendendo MySQL", Cliente: Ana Souza
</li>
  <li style="text-align: justify;">Data Empréstimo: 2024-07-12, Livro: "Introdução à Programação", Cliente: Bruno Lima
</li>
  <li style="text-align: justify;">Data Empréstimo: 2024-07-15, Livro: "História do Brasil", Cliente: Carla Mendes
</li>

</ul>

<p style="text-align: justify;">Tarefas</p>

<ul>
  <li style="text-align: justify;">Criar as tabelas: Crie as tabelas Autores, Livros e Empréstimos conforme a descrição fornecida.</li>
  <li style="text-align: justify;">Inserir os dados: Insira os dados nas tabelas conforme a descrição fornecida.
</li>
  <li style="text-align: justify;">Executar uma consulta com INNER JOIN: Crie uma consulta que mostre os empréstimos com detalhes dos livros e autores.
</li>
</li>
  <li style="text-align: justify;">Criar uma view: Crie uma view que exiba os detalhes dos empréstimos.
</li>
  <li style="text-align: justify;">Criar uma stored procedure: Crie uma stored procedure para inserir um novo empréstimo.

</li>
</ul>

```sql
CREATE DATABASE BIBLIOTECA;

USE BIBLIOTECA;

CREATE TABLE AUTOR(

	ID INT PRIMARY KEY AUTO_INCREMENT,
    NOME VARCHAR(100) NOT NULL

);

CREATE TABLE LIVRO(

	ID INT PRIMARY KEY AUTO_INCREMENT,
    TITULO VARCHAR(100) NOT NULL,
    GENERO VARCHAR(50) NOT NULL,
    ID_AUTOR INT NOT NULL,
    FOREIGN KEY (ID_AUTOR)
    REFERENCES AUTOR(ID)

);

CREATE TABLE EMPRESTIMO(

	ID INT PRIMARY KEY AUTO_INCREMENT,
    DTEMPRESTIMO DATE NOT NULL,
    DTDEVOLUCAO DATE,
    CLIENTE VARCHAR(100) NOT NULL,
    ID_LIVRO INT NOT NULL,
    FOREIGN KEY (ID_LIVRO)
    REFERENCES LIVRO(ID)

);

INSERT INTO AUTOR(NOME)
VALUES
('João Silva'),
('Maria Oliveira'),
('Pedro Santos');

SELECT * FROM AUTOR;

INSERT INTO LIVRO(TITULO, ID_AUTOR, GENERO)
VALUES
('Aprendendo MySQL', 1, 'Tecnologia'),
('Introdução à Programação', 2, 'Educação'),
('História do Brasil', 3, 'Historia');

SELECT * FROM LIVRO;

INSERT INTO EMPRESTIMO(DTEMPRESTIMO, ID_LIVRO, CLIENTE)
VALUES
('2024-07-10', 1, 'Ana Souza'),
('2024-07-12', 2, 'Bruno Lima'),
('2024-07-15', 3, 'Carla Mendes');

SELECT * FROM EMPRESTIMO;

SELECT L.TITULO, L.GENERO,
A.NOME AS 'AUTOR',
E.DTEMPRESTIMO AS 'DATA DE EMPRESTIMO', E.CLIENTE
FROM
AUTOR A
INNER JOIN LIVRO L
ON
L.ID_AUTOR = A.ID
INNER JOIN EMPRESTIMO E
ON
E.ID_LIVRO = L.ID;

CREATE VIEW VW_EMPRESTIMO AS
	SELECT E.DTEMPRESTIMO AS 'DATA DE EMPRESTIMO', E.CLIENTE,
    L.TITULO, L.GENERO
    FROM EMPRESTIMO E
    INNER JOIN LIVRO L
    ON
    E.ID_LIVRO = L.ID;
    
SELECT * FROM VW_EMPRESTIMO;

DELIMITER #

CREATE PROCEDURE ADDEMPRESTIMO(DATAEMPRESTIMO DATE, DATADEVOLUCAO DATE, USUARIO VARCHAR(100), IDLIVRO INT)
	BEGIN
		INSERT INTO EMPRESTIMO(DTEMPRESTIMO, DTDEVOLUCAO, CLIENTE, ID_LIVRO)
        VALUES
        (DATAEMPRESTIMO, DATADEVOLUCAO, USUARIO, IDLIVRO);
	END#

DELIMITER ;
    
CALL ADDEMPRESTIMO('2024-07-26', '2024-08-02', 'VINICIOS ANHAS', 1);

SELECT * FROM EMPRESTIMO;
```