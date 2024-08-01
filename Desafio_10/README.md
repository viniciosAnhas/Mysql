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

```