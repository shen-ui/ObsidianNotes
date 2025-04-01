
When a new entity is necessary and relational to another table, a new database table can be created using the `CREATE TABlE` statement.

---
```SQL
-- CREATE TABLE statement with optional table constraints and default values
CREATE TABLE IF NOT EXISTS another_table (
	c_1 DataType TableConstraint DEFAULT def_value,
	c_2 DataType TableConstraint DEFAULT def_value,
	...
);
```
