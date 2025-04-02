
Now that the idea of creating queries is established, its now time to put it all together in the context of a complete query.

```SQL
-- Full Select Query
SELECT DISTINCT column, AGG_FUNC(column / expression), ...
FROM Table
	JOIN Another_table
	ON Table.column = another_table.column
	WHERE constraint / expression
	HAVING constraint / expression
	ORDER BY column ASC / DESC
	LIMIT count OFFSET COUNT;
```

Queries begin with finding data on a table, then filtering that data that can be processed. 

### FROM & JOINS
---
The `FROM` clause and `JOIN` classes are the first to be executed to determine the total set of data that will be queried. This includes sub-queries in clauses and can create temp tables to be created under the hood that contains all rows and columns of the table that is being joined.

### WHERE
---
Once the working set of data is established, the first pass `WHERE` constraints are applied to the individual rows. Each of the constraints can only access columns directly from the tables  requested in the `FROM` clause. Aliases in the `SELECT` portion are not accessible in most databases since they may include expressions dependent on parts of the query that have not yet executed.

### GROUP BY
---
The remaining rows after the `WHERE` constraints are applied are then grouped by common values in the column specified in the `GROUP BY` clause. This will return as many rows that are unique in that column. This means that this clause should only need to use then when an aggregate function is used within the query.

### HAVING
---
If a query contains the `GROUP BY` clause, then `HAVING` may be applied to the grouped rows and discards grouped rows that don't satisfy the constraint after the declaration of the clause. 

## SELECT
---
Any expressions in the `SELECT` part of the query are finally computed.

### DISTINCT
---
Of the remaining rows, duplicates will be removed.

## ORDER BY
---
If an order is specified with `ORDER BY`, the rows are sorted by ascending or descending order.  

### LIMIT / OFFSET
---
The rows that fall outside the range of `LIMIT` and `OFFSET` are discarded, leaving the remaining final data set to be returned from a query.

#### Conclusion
---
Not all the parts above are required for a query, but that is part of how SQL shows it's strengths. SQL is flexible and allows for quick manipulation of data while only using a few set of rules.