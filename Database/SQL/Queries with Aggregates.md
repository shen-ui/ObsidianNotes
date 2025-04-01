---
tags:
  - Aggregate
  - AGG_FUNC
  - COUNT
  - MIN
  - MAX
  - AVG
  - SUM
  - GROUP_BY
---
In addition to expressions, SQL supports functions, or colloquially known as *Aggregates*. These allow you to summarize information about a group of rows of data. 

```SQL
--Query with Aggregate Functions over All Rows

SELECT AGG_FUNC( column / expression ) AS aggregate_descriptor, ...
FROM Table
WHERE constraints_expression
```

Aggregate functions without specified grouping will run over a whole set of result rows and return a ==**SINGLE VALUE**==.

| FUNCTION                    | Description                                                                                                                                                                                     |
| --------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `COUNT( * ), COUNT(column)` | A common function used to counts the number of rows in the group if no column name is specified. Otherwise, count the number of rows in the group with non-NULL values in the specified column. |
| `MIN(column)`               | Finds the smallest numerical value in the specified column for all rows in the group.                                                                                                           |
| `MAX(column)`               | Finds the largest numerical value in the specified column for all rows in the group.                                                                                                            |
| `AVG(column)`               | Finds the average numerical value in the specified column for all rows in the group.                                                                                                            |
| `SUM(column)`               | Finds the sum of all numerical values in the specified column for the rows in the group.                                                                                                        |
Across rows, you may apply aggregate functions to individual groups of data. This would then create as many results as there are unique groups defined by the `GROUP BY` clause.

```SQL
--Aggregate Functions over Groups

SELECT AGG_FUNC( column or expression ) AS aggregate_description, ...
FROM Table
WHERE constraint_expression
GROUP BY column;
```

One may notice that if the `GROUP BY` clause is executed after the WHERE clause, how does one filter grouped rows? To answer this need, SQL provides the `HAVING` clause which is used specifically with `GROUP BY` to allow filtering grouped rows from a resulting set.

```SQL
-- Query with HAVING constraing

SELECT grouped_columns, AGG_FUNC(column_expression) AS aggregate_result_alias, ...
FROM Table
WHERE condition
GROUP BY column
HAVING group_condition;

```

The `HAVING` clause is written the same way as the `WHERE` clause and are applied to group rows. If you imagine data with millions of rows and properties, being able to apply additional constraints is often necessary to make sense of data.