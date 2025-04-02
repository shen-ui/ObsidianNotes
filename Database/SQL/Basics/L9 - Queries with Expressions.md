---
tags:
  - AS
  - Math
  - Expressions
  - String
  - Manipulation
---
***Expressions*** can be used to write complex logic when querying for columns in a row. They can be used to mathematically or with string functions along with arithmetic's to transform values.

```SQL
--Example query with expressions

SELECT particle_speed / 2.0 AS half_particle_speed
FROM physics_data
WHERE ABS(particle_position) * 10.0 > 500;
```

Each database framework has its own supported set of expressions including mathematics, string and date functions that can be used in a query. expressions can optimize a query resulting in faster time complexity and with post processing results of a query.

When querying, you may assign an ***Alias*** to part of a query using the `AS` keyword.

```SQL 
--Query with Alias/AS

SELECT column AS column_alias
FROM Table;
```


Regular columns and tables can be expressed as an alias to make quick and easy references to parts of queries. It's best practice to use alias as a way to tame complex queries.

```SQL
--Example query with JOIN, AS and Expressions

SELECT column AS better_column_name, … 
FROM a_long_widgets_table_name AS mywidgets
INNER JOIN widget_sales
ON mywidgets.id = widget_sales.widget_id;
```


