# List all foreign keys referencing table \(MSSQL\)

This gives you:

* The FK itself itself
* Schema that the FK belongs to
* The "_referencing table_" or the table that has the FK
* The "_referencing column_" or the column inside referencing table that points to the FK
* The "_referenced table_" or the table that has the key column that your FK is pointing to
* The "_referenced column_" or the column that is the key that your FK is pointing to

Code below:

```sql
SELECT  obj.name AS FK_NAME,
    sch.name AS [schema_name],
    tab1.name AS [table],
    col1.name AS [column],
    tab2.name AS [referenced_table],
    col2.name AS [referenced_column]
FROM sys.foreign_key_columns fkc
INNER JOIN sys.objects obj
    ON obj.object_id = fkc.constraint_object_id
INNER JOIN sys.tables tab1
    ON tab1.object_id = fkc.parent_object_id
INNER JOIN sys.schemas sch
    ON tab1.schema_id = sch.schema_id
INNER JOIN sys.columns col1
    ON col1.column_id = parent_column_id AND col1.object_id = tab1.object_id
INNER JOIN sys.tables tab2
    ON tab2.object_id = fkc.referenced_object_id
INNER JOIN sys.columns col2
    ON col2.column_id = referenced_column_id AND col2.object_id = tab2.object_id
```

Reference: [https://stackoverflow.com/questions/483193/how-can-i-list-all-foreign-keys-referencing-a-given-table-in-sql-server](https://stackoverflow.com/questions/483193/how-can-i-list-all-foreign-keys-referencing-a-given-table-in-sql-server)

