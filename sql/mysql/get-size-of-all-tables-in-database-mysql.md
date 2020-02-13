# Get size of all tables in database \(MYSQL\)



```sql
SELECT 
table_name, 
table_rows, 
(data_length+index_length)/power(1024,1) tablesize_kb
FROM INFORMATION_SCHEMA.TABLES
WHERE TABLE_SCHEMA = '<DB name>';
```

