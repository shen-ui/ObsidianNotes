---
tags:
  - JOIN
  - INNER
  - normalization
  - primary
  - LEFT_JOIN
  - RIGHT_JOIN
  - FULL_JOIN
---
Entity data in the real world is often broken down into pieces and stored across multiple orthogonal tables using a process called *normalization*.

---

*Normalization* is useful in reducing duplicate data in a table, allows data to grow independent and allows databases to add functionality in security, complexity or added services. As a trade-off queries become more complex since they need to find additional data from different parts of a database. There are also performance issues that may arise. 

Tables that share information about a single entity need to have a *primary key* that uniquely identities other entities across a database. A common way of implementation is the use of auto-incrementing integers, but may also include strings or hash values.

`JOIN` is a keyword used in a query to combine row data across separate tables within a database.
There are multiple forms of ==`JOIN`==.

```SQL
--Query using JOIN

SELECT column_one, column_two, …
FROM table
INNER JOIN another_table
ON table.id = another_table.id
WHERE conditon_one, condition_two, ... 
ORDER BY column, … ASC/DESC 
LIMIT num_limit OFFSET num_offset;
```

`INNER JOIN` matches rows from one table to another given they have a primary key that binds access a row from another table. 

>[!NOTE]
>`INNER JOIN` and `JOIN` are equivalent. Differentiating them does help with readability.

If two tables have asymmetric data, we may also use ==`LEFT JOIN`==, ==`RIGHT JOIN`==, and ==`FULL_JOIN`== to ensure that data is not left out of results.

![[0e377725-1e0a-400c-bab7-0099dbf1efb8_1280x1664.png]]

>[!NOTE]
>#PRACTICE
