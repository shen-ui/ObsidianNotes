As databases change over time a way to update corresponding tables and database schemas is by using the `ALTER TABLE` statement to add, remove or modify columns and table constraints.

---
#### Adding Columns
---
To add new columns, the syntax is similar to `CREATE TABLE`.You need to specify the data type and any potential table constraints and default values to be applied to existing and new rows. In MySQL, you can even specify where to insert the new columns using the `FIRST` or `AFTER` clause, though its not a standard feature of SQL.

```SQL
-- ALTER talbe to add new columns
ALTER TABLE table
ADD c_1 DataType OptionalTableConstraint
	DEFAULT default_value;
```

#### Removing Columns
---
Dropping columns is pretty simple, just add `DROP` and specify the column.

```SQL
-- DROP a column
Alter TABLE table
DROP column_to_drop;
```

#### Renaming a Table
---
Like before, renaming a table will be necessary sometimes. Just add `RENAME TO` and specify the name.
```SQL
-- Altering table name
ALTER TABLE table
RENAME TO new_name;
```

>[!NOTE]
>Any database will support different methods of altering so its best to look at the documentation of a database to get a look at capabilities.

