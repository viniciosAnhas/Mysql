<div align="center">
  <div>
    <img height = "150" width = "150" src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/mysql/mysql-original-wordmark.svg" />
  </div>
</div>

<p style="text-align: justify;">O cliente <b>Tera Comércio de Produtos S.A</b>, solicitou a modelagem de um banco de dados para cadastro dos seus clientes.</p>

<p style="text-align: justify;">A função da Unidados é a análise dos requisitos junto aos usuários para a correta construção do produto. O cliente deseja que inicialmente os scripts sejam construídos para o <b>Banco de Dados MySQL</b>, porém, posteriormente pode haver mudança no ambiente e consequentemente adaptação dos scripts para outros produtos de SGBD.</p>

<p style="text-align: justify;">O cliente não quer nenhuma informação relativa à vendas ou estoque, desejando somente as informações primárias de Clientes.</p>

<p style="text-align: justify;">O nosso cliente solicitou uma tabela para armazenar os livros que são comercializados pela empresa. A solicitação é somente para livros e não há a necessidade de realizar busca em outras tabelas. Hoje há um funcionário de vendas que tem uma tabela do Excel para guardar esses registros, mas as buscas estão ficando complexas. Decidiu-se então criar um banco de dados separado para esse funcionário.</p>

<p style="text-align: justify;">Após a criação da tabela, deveremos entregar algumas queries prontas para que sejam enviadas para o programador. As queries são as seguintes:.</p>

<ul>
  <li style="text-align: justify;">Trazer todos os dados.</li>
  <li style="text-align: justify;">Trazer o nome do livro e o nome da editora.</li>
  <li style="text-align: justify;">Trazer o nome do livro e a UF dos livros publicados por autores do sexo masculino.</li>
  <li style="text-align: justify;">Trazer o nome do livro e o número de páginas dos livros publicados por autores do sexo feminino.</li>
  <li style="text-align: justify;">Trazer os valores dos livros das editoras de São Paulo.</li>
  <li style="text-align: justify;">Trazer os dados dos autores do sexo masculino que tiveram livros publicados por São Paulo ou Rio de Janeiro (Questão Desafio).</li>
</ul>

<p style="text-align: justify;">Utilize a planilha contendo os dados de exemplo.</p>


```sql
CREATE DATABASE LIVRARIA;
```

```sql
CREATE TABLE LIVROS(

	ID INT(11) PRIMARY KEY AUTO_INCREMENT,
    NM_LIVRO VARCHAR(255) NOT NULL UNIQUE,
    NM_AUTOR VARCHAR(255) NOT NULL,
    SX_AUTOR ENUM('M','F') NOT NULL,
    TOT_PAGINAS INT(11) NOT NULL,
    NM_EDITORA VARCHAR(255) NOT NULL,
    VLR_LIVRO DOUBLE NOT NULL,
    UF CHAR(2) NOT NULL,
    A_PUBLICADO INT(4) NOT NULL
);
```

```sql
SELECT * 
FROM LIVROS;
```

```sql
SELECT NM_LIVRO AS 'LIVRO', 
NM_EDITORA AS 'EDITORA' 
FROM LIVROS;
```

```sql
SELECT NM_LIVRO AS 'LIVRO', 
UF AS 'ESTADO'
FROM LIVROS
WHERE SX_AUTOR = 'M';
```

```sql
SELECT NM_LIVRO AS 'LIVRO', 
TOT_PAGINAS AS 'TOTAL DE PAGINAS'
FROM LIVROS
WHERE SX_AUTOR = 'F';
```

```sql
SELECT VLR_LIVRO AS 'VALOR'
FROM LIVROS
WHERE UF = 'SP';
```

```sql
SELECT NM_AUTOR AS 'NOME DO AUTOR',
SX_AUTOR AS 'SEXO DO AUTOR'
FROM LIVROS
WHERE (SX_AUTOR = 'M')
AND
((UF = 'SP')
OR
(UF = 'RJ'));
```