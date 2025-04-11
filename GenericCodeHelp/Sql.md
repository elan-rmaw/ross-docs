# Fast query to retrieve rough count on number of rows
```
SELECT SUM(p.rows) FROM sys.partitions AS p
  INNER JOIN sys.tables AS t
  ON p.[object_id] = t.[object_id]
  INNER JOIN sys.schemas AS s
  ON s.[schema_id] = t.[schema_id]
  WHERE t.name = N'Event'
  AND s.name = N'dbo'
  AND p.index_id IN (0,1);
  ```