# List all foreign keys referencing table \(MYSQL\)

## MSSQL version

{% page-ref page="../mssql/list-all-foreign-keys-referencing-table.md" %}

## 

```sql
select
kcu.table_schema as 'Table Schema',
fks.constraint_name as FK_NAME,
kcu.table_name as 'referencing table',
kcu.column_name as 'referencing column',
kcu.referenced_table_name as 'referenced table',
kcu.referenced_column_name as 'referenced column'
from information_schema.referential_constraints fks
join information_schema.key_column_usage kcu
on fks.constraint_schema = kcu.table_schema
and fks.table_name = kcu.table_name
and fks.constraint_name = kcu.constraint_name
where kcu.referenced_table_name is not null;
```



{% embed url="https://dataedo.com/kb/query/mysql/list-foreign-keys" %}

{% embed url="https://www.binarytides.com/list-foreign-keys-in-mysql/" %}



