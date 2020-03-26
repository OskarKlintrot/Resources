# Snippets

Check row count twice with pause in between checks to see if row count increases in any tables

```sql
DECLARE @RowCounts TABLE(
  TableName sysname NOT NULL,
  RecordsPre INT NOT NULL,
  TimestampPre DateTimeOffset NOT NULL,
  RecordsPost INT NULL,
  TimestampPost DateTimeOffset NULL
);

INSERT INTO @RowCounts (TableName, RecordsPre, TimestampPre)
SELECT T.name TableName, I.rows Records, GETDATE() CurrentTime
FROM sysobjects T, sysindexes I
WHERE T.xtype = 'U' and I.id = T.id and I.indid IN (0,1)

WAITFOR DELAY '00:00:15'

UPDATE A
SET RecordsPost = B.Records,
    TimestampPost = B.CurrentTime
FROM (
  SELECT T.name TableName, I.rows Records, GETDATE() CurrentTime
  FROM sysobjects T, sysindexes I
  WHERE T.xtype = 'U' and I.id = T.id and I.indid IN (0,1)
) B
INNER JOIN @RowCounts A
ON A.TableName = B.TableName

SELECT *
FROM @RowCounts
ORDER BY TableName
```

