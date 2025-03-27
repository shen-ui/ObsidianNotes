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

