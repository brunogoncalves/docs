# Outros comandos úteis do MySQL

### Exibir o tamanho de cada database

```sql
SELECT TABLE_SCHEMA BANCO, ROUND(SUM(DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024, 2) SIZE_MB, ROUND(SUM(DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024 / 1024, 2) SIZE_GB
FROM information_schema.TABLES
GROUP BY TABLE_SCHEMA
ORDER BY SIZE_MB DESC, TABLE_SCHEMA
```

### Exibir o tamanho das tabelas de um database:

```sql
SELECT TABLE_NAME TABELA, ROUND(SUM(DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024, 2) SIZE_MB, ROUND(SUM(DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024 / 1024, 2) SIZE_GB
FROM information_schema.TABLES
WHERE TABLE_SCHEMA = 'mysql'
GROUP BY TABLE_NAME
ORDER BY SIZE_MB DESC, TABLE_NAME
```

### Diminuindo o tamanho do banco de dados

m problema que enfrentava sempre que colocava um aplicativo utilizando o MySQL é o tamanho sempre crescente do arquivo
`/var/lib/mysql/ibdata1.` Este arquivo armazena as tableas do tipo InnoDB e, mesmo que os dados sejam removidos ou elimine
tabelas e, até mesmo, banco de dados, o tamanho do ibdata1 não diminui,
o que pode ocasionar problemas de espaço em disco mais para frente.

```sql
OPTIMIZE TABLE tabela;
```