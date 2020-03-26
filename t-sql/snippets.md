# Snippets

Check row count twice with pause in between checks to see if row count increases in any tables

```sql
SELECT GETDATE() CurrentTime

SELECT T.name TableName, I.rows Records
FROM sysobjects T, sysindexes I
WHERE T.xtype = 'U' and I.id = T.id and I.indid IN (0,1)
ORDER BY TableName

WAITFOR DELAY '00:00:15'

SELECT GETDATE() CurrentTime

SELECT T.name TableName, I.rows Records
FROM sysobjects T, sysindexes I
WHERE T.xtype = 'U' and I.id = T.id and I.indid IN (0,1)
ORDER BY TableName
```

