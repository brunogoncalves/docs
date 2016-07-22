# Outros comandos úteis do MySQL

Exibir o tamanho de cada database:

```sql
SELECT TABLE_SCHEMA BANCO, ROUND(SUM(DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024, 2) SIZE_MB
FROM information_schema.TABLES
GROUP BY TABLE_SCHEMA
ORDER BY SIZE_MB DESC, TABLE_SCHEMA
```