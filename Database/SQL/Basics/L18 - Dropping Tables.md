In some cases, a table may need to be dropped entirely including metadata and all rows. `DROP TABLE` differs from `DELETE` in that it removes table schema from database entirely.

---
```SQL
-- DROP Table
DROP TABLE IF EXISTS table;
```

If there is another table that is reliant on a `PRIMARY KEY` in the table you are dropping, you will have to `ALTER` the dependent table first to remove the reliant rows.