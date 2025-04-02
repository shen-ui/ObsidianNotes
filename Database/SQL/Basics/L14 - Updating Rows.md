A common task is to update existing rows of data which can be done using the `UPDATE` statement. Like `INSERT`, a table must be specified to update columns and rows. Data to be updated must also match the table's schema.

```SQL
-- UPDATE statement with values
UPDATE table
SET c_1 = value_or_expression,
	c_2 = value_or_expression,
	...
WHERE condition;
```

This statement works by comparing column name to value pairs and applying those changes to each and all rows that satisfies the condition in the `WHERE` clause.

>[!WARNING] 
>It's inevitable to make mistakes updating data by affecting the wrong data in production databases or leaving out a clause which may affect more data that anticipated. Be cautious in the construction of UPDATE statements.
>A good tip is to always write the constraint first and test with a `SELECT` query to make sure the rows being updated are the correct rows. Only then, should a column/value pair should be updated.



