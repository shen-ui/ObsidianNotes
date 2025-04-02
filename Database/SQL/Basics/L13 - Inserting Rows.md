---
tags:
  - INSERT
  - SCHEMA
aliases:
  - INSERT INTO
---
Now that we've spent time learning how to query for data, its time to start learning about `SCHEMA`  and `INSERT` to add new data.

### SCHEMA
---
A table is a two dimensional set of rows and columns with columns being properties and rows being data entries. A <mark style="background: #CACFD9A6;">database schema</mark> is used to describe these properties within a row and provides a structure to each table with properties like:
	- Data Type
	- Uniqueness
	- Constraints

```SQL
-- Creating a Schema Example
CREATE SCHEMA schemaname;
GO

-- To deploy a table with schema
CREATE TABLE schemaname.tablename( values ... );
```

```SQL
-- Contents of schema file
CREATE TABLE schemaname.tableName(
		Id INT PRIMARY KEY,
		Name VARCHAR(256),
		Date DATETIME NOT NULL
);
```

### INSERT INTO
---
The `INSERT` keyword can be used to insert rows of data into a table.
within the statement, we must declare what is written into the table with corresponding data aligned with the column. You may also insert multiple rows at a time sequentially.

```SQL
-- Insert Statment with values
INSERT INTO table
	VALUES (v_1, v_2, ...),
		   (v_1, v_2, ...),
		   ...;
```

If there is incomplete data and the table with columns that are signed for `default` values, a row insert can be specified with them explicitly.

> [!NOTE]
> It is important to match the number of columns with values, otherwise it may result in an error.

```SQL
-- Insert Statment with specific columns
INSERT INTO table
	(c_1, c2, ...) --contains 4 specific columns
	VALUES (v_1, v_2, ...),----|
		   (v_1, v_2, ...),-----must explicitly contain 4 values
		   ...;
```

Despite these queries are more verbose to write, inserting this way has the added benefit of being forward compatible. For example, if you were to need to add a new column to the table with a default value, no hard coded `INSERT` statements will have to change as a result to accommodate the change.

```SQL
-- INSERT statement with expressions
INSERT INTO books
(book_id, rating, sales_in_thousands)
VALUES(1, 9, (SELECT sales FROM bookSales WHERE bookSales.id = books.id)/1000);
```