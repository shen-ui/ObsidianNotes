
To delete rows from a database, `DELETE` may be used.

---
```SQL
-- DELETE with condition
DELETE FROM Table
WHERE condition;
```

>[!WARNING]
>If `WHERE` statement is omitted, *all* rows will be deleted. Though it's a quick way to clear out a table, be careful  in it's use. 

