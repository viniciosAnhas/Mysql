<div align="center">
  <div>
    <img height = "150" width = "150" src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/mysql/mysql-original-wordmark.svg" />
  </div>
</div>

<p style="text-align: justify;">Traga os funcionarios que trabalhem no departamento de filmes ou no departamento de roupas.</p>

<p style="text-align: justify;">O gestor de marketing pediu a lista das funcionarias que trabalhem no departamento de filmes ou no departamento lar. Ele necessita enviar um email para as colaboradoras desses dois setores.</p>

<p style="text-align: justify;">Traga os funcionarios do sexo masculino ou os funcionarios que trabalhem no setor jardim.</p>

```sql
SELECT NOME
FROM funcionarios
WHERE (DEPARTAMENTO = 'filmes')
OR
(DEPARTAMENTO = 'ROUPAS');
```

```sql
SELECT NOME,
EMAIL
FROM funcionarios
WHERE (SEXO = 'FEMININO')
AND
((DEPARTAMENTO = 'FILMES') 
OR
(DEPARTAMENTO = 'LAR'));
```

```sql
SELECT NOME
FROM funcionarios
WHERE (SEXO = 'MASCULINO')
OR
(DEPARTAMENTO = 'JARDIM');
```