# 💡 Tip: Extracting the relationships

In order to create the proper relationships between your database tables in Whaly workbench, you can use the above SQL queries to extract them.

```
SELECT 
    tc.table_schema, 
    tc.constraint_name, 
    tc.constraint_type, 
    tc.table_name, 
    kcu.column_name, 
    ccu.table_schema AS foreign_table_schema, 
    ccu.table_name AS foreign_table_name, 
    ccu.column_name AS foreign_column_name
FROM information_schema.table_constraints AS tc 
JOIN information_schema.key_column_usage AS kcu 
ON 
    tc.constraint_name = kcu.constraint_name 
    AND 
    tc.table_schema = kcu.table_schema 
JOIN information_schema.constraint_column_usage AS ccu 
ON 
    ccu.constraint_name = tc.constraint_name 
    AND 
    ccu.table_schema = tc.table_schema;
```

&#x20;If you want to export those into a CSV file, you can run directly in Postgres:

```
\copy (SELECT tc.table_schema, tc.constraint_name, tc.constraint_type, tc.table_name, kcu.column_name, ccu.table_schema AS foreign_table_schema, ccu.table_name AS foreign_table_name, ccu.column_name AS foreign_column_name FROM information_schema.table_constraints AS tc JOIN information_schema.key_column_usage AS kcu ON tc.constraint_name = kcu.constraint_name AND tc.table_schema = kcu.table_schema JOIN information_schema.constraint_column_usage AS ccu ON ccu.constraint_name = tc.constraint_name AND ccu.table_schema = tc.table_schema;) to 'whaly.csv' csv header
```

This will write on your Postgres server a whaly.csv file with all the relationships between the tables.
