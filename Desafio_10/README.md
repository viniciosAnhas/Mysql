<div align="center">
  <div>
    <img height = "150" width = "150" src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/mysql/mysql-original-wordmark.svg" />
  </div>
</div>

<p style="text-align: justify;">Vamos criar um banco de dados focado em um sistema de hospital.</p>

<p style="text-align: justify;">Estrutura das Tabelas</p>

<ul>

  <p style="text-align: justify;">PACIENTE</p>

  <li style="text-align: justify;">ID (INT, Primary Key, Auto Increment)</li>
  <li style="text-align: justify;">NOME (VARCHAR(100), Not Null)</li>
  <li style="text-align: justify;">CPF (CHAR(11), Not Null, Unique)</li>
  <li style="text-align: justify;">DATA_NASCIMENTO (DATE, Not Null)
</li>

</ul>

<ul>

  <p style="text-align: justify;">MEDICO</p>

  <li style="text-align: justify;">ID (INT, Primary Key, Auto Increment)</li>
  <li style="text-align: justify;">NOME (VARCHAR(100), Not Null)</li>
  <li style="text-align: justify;">ESPECIALIDADE (VARCHAR(100), Not Null)</li>

</ul>

<ul>

  <p style="text-align: justify;">CONSULTA</p>

  <li style="text-align: justify;">ID (INT, Primary Key, Auto Increment)</li>
  <li style="text-align: justify;">ID_PACIENTE (INT, Not Null, Foreign Key referencing PACIENTE(ID))</li>
  <li style="text-align: justify;">ID_MEDICO (INT, Not Null, Foreign Key referencing MEDICO(ID))</li>
  <li style="text-align: justify;">DATA_CONSULTA (DATE, Not Null)</li>
  <li style="text-align: justify;">DIAGNOSTICO (TEXT, Null)</li>

</ul>

<ul>

  <p style="text-align: justify;">HISTORICO_CONSULTAS</p>

  <li style="text-align: justify;">ID (INT, Primary Key, Auto Increment)</li>
  <li style="text-align: justify;">DATA_ALTERACAO (DATETIME, Not Null)</li>
  <li style="text-align: justify;">ID_CONSULTA (INT, Not Null, Foreign Key referencing CONSULTA(ID))</li>
  <li style="text-align: justify;">DIAGNOSTICO_ANTIGO (TEXT, Null)</li>
  <li style="text-align: justify;">DIAGNOSTICO_NOVO (TEXT, Null)</li>

</ul>

<p style="text-align: justify;">Tarefas</p>

<ul>
  <li style="text-align: justify;">Criar as tabelas conforme a descrição.</li>
  <li style="text-align: justify;">Inserir dados fictícios nas tabelas de pacientes, médicos e consultas.</li>
  <li style="text-align: justify;">Criar uma trigger que insere registros na tabela HISTORICO_CONSULTAS sempre que o diagnóstico de uma consulta for atualizado.</li>

  <li style="text-align: justify;">Fazer consultas utilizando JOINs para:</li>

  <ul>
    <li style="text-align: justify;">Obter todas as consultas de um determinado paciente.</li>
    <li style="text-align: justify;">Obter todas as consultas realizadas por um determinado médico.</li>
    <li style="text-align: justify;">Obter o histórico de alterações dos diagnósticos de consultas.</li>
  </ul>

</ul>

```sql
CREATE DATABASE HOSPITAL;

USE HOSPITAL;

CREATE TABLE PACIENTE(

	ID INT PRIMARY KEY AUTO_INCREMENT,
    NOME VARCHAR(100) NOT NULL,
    CPF CHAR(11) NOT NULL UNIQUE,
    DATANASCIMENTO DATE NOT NULL

);

CREATE TABLE MEDICO(

	ID INT PRIMARY KEY AUTO_INCREMENT,
    NOME VARCHAR(100) NOT NULL,
    ESPECIALIDADE VARCHAR(100) NOT NULL

);

CREATE TABLE CONSULTA(

	ID INT PRIMARY KEY AUTO_INCREMENT,
    ID_PACIENTE INT NOT NULL,
    ID_MEDICO INT NOT NULL,
    DATACONSULTA DATE NOT NULL,
    DIAGNOSTICO TEXT NULL,
    FOREIGN KEY (ID_PACIENTE)
    REFERENCES PACIENTE (ID),
    FOREIGN KEY (ID_MEDICO)
    REFERENCES MEDICO (ID)

);

DROP TABLE CONSULTA;

CREATE TABLE HISTORICOCONSULTA(

	ID INT PRIMARY KEY AUTO_INCREMENT,
    DATAAULTERACAO DATE NOT NULL,
    ID_CONSULTA INT NOT NULL,
    DIAGNOSTICOANTIGO TEXT NULL,
    DIAGNOSTICONOVO TEXT NULL

);

INSERT INTO PACIENTE(NOME, CPF, DATANASCIMENTO)
VALUES
('João da Silva', '12345678901', '1980-01-15'),
('Maria dos Santos', '23456789012', '1985-02-20'),
('Carlos Pereira', '34567890123', '1990-03-25'),
('Ana Oliveira', '45678901234', '1975-04-30'),
('Pedro Souza', '56789012345', '2000-05-05'),
('Fernanda Lima', '67890123456', '1995-06-10'),
('Rafael Alves', '78901234567', '1988-07-15'),
('Beatriz Gomes', '89012345678', '1993-08-20'),
('Rodrigo Rocha', '90123456789', '1979-09-25'),
('Juliana Costa', '01234567890', '1982-10-30');

SELECT * FROM PACIENTE;

INSERT INTO MEDICO(NOME, ESPECIALIDADE)
VALUES
('Dr. João Almeida', 'Cardiologista'),
('Dra. Maria Souza', 'Dermatologista'),
('Dr. Carlos Pereira', 'Pediatra'),
('Dra. Ana Oliveira', 'Ginecologista'),
('Dr. Pedro Lima', 'Ortopedista'),
('Dra. Fernanda Alves', 'Oftalmologista'),
('Dr. Rafael Gomes', 'Neurologista'),
('Dra. Beatriz Silva', 'Psiquiatra'),
('Dr. Rodrigo Rocha', 'Urologista'),
('Dra. Juliana Costa', 'Endocrinologista'),
('Dr. Marcelo Santos', 'Gastroenterologista'),
('Dra. Carolina Ribeiro', 'Hematologista'),
('Dr. Eduardo Martins', 'Infectologista'),
('Dra. Camila Fernandes', 'Nefrologista'),
('Dr. Bruno Carvalho', 'Pneumologista'),
('Dra. Renata Azevedo', 'Reumatologista'),
('Dr. Alexandre Barros', 'Otorrinolaringologista'),
('Dra. Patrícia Dias', 'Mastologista'),
('Dr. Felipe Vieira', 'Oncologista'),
('Dra. Daniela Moreira', 'Alergologista'),
('Dr. Gustavo Lopes', 'Anestesiologista'),
('Dra. Sabrina Pinto', 'Angiologista'),
('Dr. Lucas Correia', 'Cirurgião Plástico'),
('Dra. Marina Mendes', 'Radiologista'),
('Dr. André Nunes', 'Imunologista');

SELECT * FROM MEDICO;

INSERT INTO CONSULTA(ID_PACIENTE, ID_MEDICO, DATACONSULTA, DIAGNOSTICO)
VALUES
(1, 3, '2023-11-15', 'Diagnóstico: Gripe'),
(5, 7, '2021-05-16', 'Diagnóstico: Dor nas costas'),
(2, 15, '2022-03-17', 'Diagnóstico: Enxaqueca'),
(9, 23, '2020-12-18', 'Diagnóstico: Infecção urinária'),
(3, 5, '2024-04-19', 'Diagnóstico: Bronquite'),
(8, 13, '2021-08-20', 'Diagnóstico: Anemia'),
(4, 8, '2023-07-21', 'Diagnóstico: Sinusite'),
(7, 21, '2022-09-22', 'Diagnóstico: Hipertensão'),
(10, 19, '2021-01-23', 'Diagnóstico: Asma'),
(6, 6, '2023-10-24', 'Diagnóstico: Artrite'),
(1, 9, '2022-11-25', 'Diagnóstico: Diabetes'),
(5, 25, '2020-02-26', 'Diagnóstico: Alergia alimentar'),
(2, 2, '2024-06-27', 'Diagnóstico: Dermatite'),
(9, 18, '2023-05-28', 'Diagnóstico: Infecção de ouvido'),
(3, 4, '2021-03-29', 'Diagnóstico: Cálculo renal'),
(8, 11, '2022-08-30', NULL),
(4, 12, '2021-07-31', 'Diagnóstico: Depressão'),
(7, 20, '2024-04-01', 'Diagnóstico: Hipotireoidismo'),
(10, 14, '2022-12-02', 'Diagnóstico: Hepatite'),
(6, 10, '2023-09-03', 'Diagnóstico: Fibromialgia'),
(1, 23, '2021-04-04', NULL),
(5, 17, '2020-11-05', 'Diagnóstico: Câncer de pele'),
(2, 22, '2023-02-06', 'Diagnóstico: Conjuntivite'),
(9, 19, '2022-05-07', 'Diagnóstico: Pneumonia'),
(3, 24, '2020-01-08', 'Diagnóstico: Insuficiência renal'),
(8, 5, '2021-10-09', 'Diagnóstico: Osteoporose'),
(4, 7, '2023-06-10', 'Diagnóstico: Apendicite'),
(7, 13, '2022-03-11', 'Diagnóstico: Colesterol alto'),
(10, 3, '2024-01-12', 'Diagnóstico: Problemas de visão'),
(6, 4, '2021-12-13', 'Diagnóstico: Tuberculose'),
(1, 9, '2023-11-14', 'Diagnóstico: Sinusite crônica'),
(5, 11, '2022-07-15', 'Diagnóstico: Faringite'),
(2, 14, '2024-08-16', 'Diagnóstico: Otite média'),
(9, 20, '2021-09-17', NULL),
(3, 16, '2020-04-18', 'Diagnóstico: Bronquite crônica'),
(8, 1, '2023-10-19', 'Diagnóstico: Alergia a pólen'),
(4, 23, '2022-02-20', 'Diagnóstico: Inflamação intestinal'),
(7, 25, '2021-06-21', 'Diagnóstico: Hepatite B'),
(10, 22, '2024-04-22', 'Diagnóstico: Úlcera gástrica'),
(6, 3, '2023-03-23', 'Diagnóstico: Problemas de audição'),
(1, 5, '2020-07-24', NULL),
(5, 7, '2024-09-25', 'Diagnóstico: Infecção fúngica'),
(2, 9, '2021-08-26', 'Diagnóstico: Síndrome do intestino irritável'),
(9, 11, '2022-05-27', 'Diagnóstico: Insônia'),
(3, 13, '2020-06-28', 'Diagnóstico: Cistite'),
(8, 15, '2023-12-29', 'Diagnóstico: Pressão alta'),
(4, 18, '2022-11-30', 'Diagnóstico: Lombalgia'),
(7, 2, '2021-01-31', 'Diagnóstico: Epilepsia'),
(10, 4, '2024-10-01', 'Diagnóstico: Gota'),
(6, 6, '2023-07-02', 'Diagnóstico: Conjuntivite alérgica'),
(1, 8, '2022-09-03', 'Diagnóstico: Cirrose'),
(5, 10, '2020-02-04', 'Diagnóstico: Dermatite seborreica'),
(2, 12, '2021-03-05', 'Diagnóstico: Varicela'),
(9, 14, '2024-06-06', 'Diagnóstico: Herpes zoster'),
(3, 16, '2023-04-07', 'Diagnóstico: Espondilite'),
(8, 20, '2022-12-08', 'Diagnóstico: Hipoglicemia'),
(4, 1, '2021-08-09', 'Diagnóstico: Trombose'),
(7, 3, '2020-05-10', 'Diagnóstico: Deficiência de vitamina D'),
(10, 5, '2023-10-11', 'Diagnóstico: Artrite reumatoide'),
(6, 7, '2022-03-12', 'Diagnóstico: Lupus eritematoso'),
(1, 9, '2021-01-13', 'Diagnóstico: Doença de Crohn'),
(5, 11, '2023-02-14', 'Diagnóstico: Catarata'),
(2, 14, '2021-11-15', NULL),
(9, 23, '2022-04-16', 'Diagnóstico: Embolia pulmonar'),
(3, 4, '2024-03-17', 'Diagnóstico: Hemorroida'),
(8, 6, '2023-05-18', 'Diagnóstico: Influenza'),
(4, 15, '2020-07-19', 'Diagnóstico: Hipertensão arterial'),
(7, 17, '2021-12-20', 'Diagnóstico: Varizes'),
(10, 19, '2022-01-21', 'Diagnóstico: Esquizofrenia'),
(6, 21, '2024-06-22', 'Diagnóstico: Doença de Parkinson'),
(1, 20, '2023-07-23', NULL),
(5, 25, '2021-08-24', 'Diagnóstico: Poliomielite'),
(2, 10, '2022-09-25', 'Diagnóstico: Zika vírus'),
(9, 12, '2020-10-26', 'Diagnóstico: Doença celíaca'),
(3, 14, '2023-11-27', 'Diagnóstico: Sífilis'),
(8, 2, '2021-02-28', 'Diagnóstico: Obesidade mórbida'),
(4, 16, '2024-03-29', 'Diagnóstico: Apendicite aguda'),
(7, 18, '2023-04-30', 'Diagnóstico: Insuficiência cardíaca'),
(10, 22, '2022-05-01', 'Diagnóstico: Malária'),
(6, 23, '2020-06-02', 'Diagnóstico: Sarampo'),
(1, 24, '2021-07-03', 'Diagnóstico: Câncer de mama'),
(5, 1, '2024-08-04', NULL),
(2, 3, '2023-09-05', 'Diagnóstico: Deficiência de cálcio'),
(9, 5, '2022-10-06', 'Diagnóstico: Hipertireoidismo'),
(3, 7, '2021-11-07', 'Diagnóstico: Peste bubônica'),
(8, 9, '2020-12-08', 'Diagnóstico: Miopia'),
(4, 11, '2024-01-09', 'Diagnóstico: Alzheimer'),
(7, 13, '2023-02-10', 'Diagnóstico: Câncer de próstata'),
(10, 15, '2022-03-11', 'Diagnóstico: Tuberculose'),
(6, 17, '2021-04-12', NULL),
(1, 19, '2020-05-13', 'Diagnóstico: Esclerodermia'),
(5, 21, '2023-06-14', 'Diagnóstico: Gengivite'),
(2, 23, '2022-07-15', 'Diagnóstico: Hérnia de disco'),
(9, 25, '2021-08-16', 'Diagnóstico: Colite ulcerativa');

SELECT * FROM CONSULTA;

DELIMITER $

CREATE TRIGGER TRG_HISTORICO
BEFORE UPDATE ON CONSULTA
FOR EACH ROW
BEGIN
	INSERT INTO HISTORICOCONSULTA(DATAAULTERACAO, ID_CONSULTA, DIAGNOSTICOANTIGO, DIAGNOSTICONOVO)
    VALUES (SYSDATE(), OLD.ID, OLD.DIAGNOSTICO, NEW.DIAGNOSTICO);
END$

DELIMITER ;

UPDATE CONSULTA SET DIAGNOSTICO = 'DOR DE CABECA'
WHERE 
ID = 21;

SELECT * FROM CONSULTA WHERE ID = 10;

SELECT * FROM HISTORICOCONSULTA;

UPDATE CONSULTA SET DIAGNOSTICO = 'DOR NO PE'
WHERE 
ID = 10;

SELECT P.NOME AS 'PACIENTE', P.CPF,
M.NOME AS 'MEDICO',
C.DATACONSULTA AS 'DATA DA CONSULTA', C.DIAGNOSTICO
FROM CONSULTA C
INNER JOIN PACIENTE P
ON
P.ID = C.ID_PACIENTE
INNER JOIN MEDICO M
ON
M.ID = C.ID_PACIENTE
WHERE
P.CPF = '45678901234';

SELECT M.NOME AS 'MEDICO',
C.DATACONSULTA AS 'DATA DA CONSULTA',
P.NOME AS 'PACIENTE',
C.DIAGNOSTICO
FROM CONSULTA C
INNER JOIN MEDICO M
ON
M.ID = C.ID_MEDICO
INNER JOIN PACIENTE P
ON
P.ID = C.ID_PACIENTE
WHERE
M.ID = 15;

SELECT P.NOME AS 'PACIENTE', P.CPF,
M.NOME AS 'MEDICO', M.ESPECIALIDADE,
H.DATAAULTERACAO AS 'DATA DA ATUALIZACAO', H.DIAGNOSTICONOVO AS 'DIAGNOSTICO NOVO', H.DIAGNOSTICOANTIGO AS 'DIAGNOSTICO ANTIGO'
FROM HISTORICOCONSULTA H
INNER JOIN CONSULTA C
ON
C.ID = H.ID_CONSULTA
INNER JOIN MEDICO M
ON
M.ID = C.ID_MEDICO
INNER JOIN PACIENTE P
ON
P.ID = C.ID_PACIENTE;
```