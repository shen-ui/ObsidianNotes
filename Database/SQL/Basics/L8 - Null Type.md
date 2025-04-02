---
tags:
  - "NULL"
  - IS_NULL
  - IS_NOT_NULL
  - WHERE
---
==`NULL`== is a datatype that, in good practice, should generally be avoid and reduced as much as possible, due to the value requiring special attention when constructing queries. A good way to avoid `NULL` type is to replace the value with a type-driven value such as `0`, or  `""`.

If it is necessary to store incomplete data, `NULL` can be appropriate if type-driven values will skew analysis. 

In some scenarios, joining tables can cause asymmetric data, and in these cases, it's important to test a column for `NULL` in a `WHERE` clause to see if a row has `NULL` using the `IS NULL` or `IS NOT NULL` constraint.


> [!Example] Select query with NULL values
> `SELECT column_one, column_two, … `
> `FROM mytable `
> `WHERE column IS/IS NOT NULL` 
> `AND/OR another_condition AND/OR …;`
> 
