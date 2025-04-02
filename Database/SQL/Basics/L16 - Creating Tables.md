
When a new entity is necessary and relational to another table, a new database table can be created using the `CREATE TABlE` statement.

### Create Tables
---
```SQL
-- CREATE TABLE statement with optional table constraints and default values
CREATE TABLE IF NOT EXISTS another_table (
	c_1 DataType TableConstraint DEFAULT def_value,
	c_2 DataType TableConstraint DEFAULT def_value,
	...
);
```

The structure of the new table is defined by a schema. If a table exists with the same name, a error will be thrown, to suppress this, the `IF NOT EXISTS` clause will only create a table if a database does not contain a table with a name that already exists.

### Primative Data Types
---

Generally, most databases will contain type support for numeric, string, Boolean and possibly dates and binary data.

| **Data Type**                                        | **Description**                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| ---------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `INTEGER`, `BOOLEAN`                                 | The integer datatypes can store whole integer values like the count of a number or an age. In some implementations, the boolean value is just represented as an integer value of just 0 or 1.                                                                                                                                                                                                                                                         |
| `FLOAT`, `DOUBLE`, `REAL`                            | The floating point datatypes can store more precise numerical data like measurements or fractional values. Different types can be used depending on the floating point precision required for that value.                                                                                                                                                                                                                                             |
| `CHARACTER(num_chars)`, `VARCHAR(num_chars)`, `TEXT` | The text based datatypes can store strings and text in all sorts of locales. The distinction between the various types generally amount to underlaying efficiency of the database when working with these columns.<br><br>Both the CHARACTER and VARCHAR (variable character) types are specified with the max number of characters that they can store (longer values may be truncated), so can be more efficient to store and query with big tables |
| `DATE`, `DATETIME`                                   | SQL can also store date and time stamps to keep track of time series and event data. They can be tricky to work with especially when manipulating data across timezones.                                                                                                                                                                                                                                                                              |
| `BLOB`                                               | Finally, SQL can store binary data in blobs right in the database. These values are often opaque to the database, so you usually have to store them with the right metadata to requery them.                                                                                                                                                                                                                                                          |

### Table Constraints
---

Each column can also have additional table constraints that offer automation or limit values.


| Constraint          | Description                                                                                                                                                                                                                                                                                                                                                                                        |
| ------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `PRIMARY KEY`       | This means that the values in this column are unique, and each value can be used to identify a single row in this table.                                                                                                                                                                                                                                                                           |
| `AUTOINCREMENT`     | For integer values, this means that the value is automatically filled in and incremented with each row insertion. Not supported in all databases.                                                                                                                                                                                                                                                  |
| `UNIQUE`            | This means that the values in this column have to be unique, so you can't insert another row with the same value in this column as another row in the table. Differs from the `PRIMARY KEY` in that it doesn't have to be a key for a row in the table.                                                                                                                                            |
| `NOT NULL`          | This means that the inserted value can not be `NULL`.                                                                                                                                                                                                                                                                                                                                              |
| `CHECK(expression)` | This allows you to run a more complex expression to test whether the values inserted are valid. For example, you can check that values are positive, or greater than a specific size, or start with a certain prefix, etc.                                                                                                                                                                         |
| `FOREIGN KEY`       | This is a consistency check which ensures that each value in this column corresponds to another value in a column in another table.  <br>  <br>For example, if there are two tables, one listing all Employees by ID, and another listing their payroll information, the `FOREIGN KEY` can ensure that every row in the payroll table corresponds to a valid employee in the master Employee list. |

```SQL
-- Example table schema
CREATE TABLE games (
	id INTEGER PRIMARY KEY,
	title TEXT,
	director VARCHAR(40),
	year INTEGER,
	length_minutes INTEGER
);
```
