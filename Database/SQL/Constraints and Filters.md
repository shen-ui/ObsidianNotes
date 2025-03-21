*Tables naturally will populate and become very expensive to query. Reading rows will become near impossible if not horribly inefficient.* 

---
## *Constraints*

A good way to add constraints to filter rows is the ==`WHERE`== clause. It applies to rows and checks for columns values to determine if the row shall be included within the query.

`SELECT column, another_column, …`
`FROM Table` 
`WHERE condition` 
`AND/OR anothercondition`
`AND/OR …;`

> [!TLDR]
> Complex clauses can be constructed by joining `WHERE` with numerous `AND` or `OR` keywords.

|       **Operation**       |                                               **Condition**                                               |                **Example**                 |
| :-----------------------: | :-------------------------------------------------------------------------------------------------------: | :----------------------------------------: |
|   `=, !=, <, <=, >, >=`   |                                       Standard numerical operation                                        |               col_name != 4                |
|     `BETWEEN … AND …`     |                             Number is within range of two values (inclusive)                              |   col_name `BETWEEEN` *1.5* `AND` *10.5*   |
| `NOT BETWEEN ... AND ...` |                           Number is not within range of two values (inclusive)                            | col_name `NOT BETWEEEN` *1.5* `AND` *10.5* |
|        `IN (...)`         |                                          Number exists in a list                                          |          col_name `IN`* (2,4,6)*           |
|      `NOT IN (...)`       |                                        Number don't exist in list                                         |        col_name `NOT IN` *(2,4,6)*         |
|          `LIKE`           |                                  Case insenstive exact string comparison                                  |          col_name `LIKE` *"ABC"*           |
|        `NOT LIKE`         |                            Case insensitive exact string inequality comparison                            |        col_name `NOT LIKE` *"ABC"*         |
|            `%`            | Used anywhere in a string to match a sequence of zero or more characters (only with `LIKE` or` NOT LIKE`) |        col_name `NOT LIKE` *"$%AT"*        |
|         `IN(...)`         |                                          String exists in a list                                          |      col_name `IN` *("A", "B", "C")*       |
|       `NOT IN(...)`       |                                     String does not exists in a list                                      |    col_name `NOT IN` *("A", "B", "C")*     |

> [!NOTE] 
> full-text search is best left to dedicated libraries like [Apache Lucene](https://lucene.apache.org/) or [Sphinx](https://sphinxsearch.com/), libraries that are designed to do full text search. As a result, they are more efficient and can support wider text search features such as multi-language and advanced queries.
> 


---
## *Filters*

Data in a database may be unique, but results of a query may not be. For example, a table of Pokémon cards may have multiple copies of [Pikachu's](https://www.tcgplayer.com/search/pokemon/product?productLineName=pokemon&q=pikachu&view=grid&ProductTypeName=Cards&page=1&CardType=Pokemon) varying across multiple sets of Pokémon cards. In such cases, SQL provides the keyword `DISTINCT` which provides a convenient way to discard rows

`SELECT` ==DISTINCT== `column, another_column, … 
`FROM mytable 
`WHERE condition_one, condition_two, ...`

> [!NOTE]
> `DISTINCT` will blindly remove duplicate rows and will not promise data that is explicitly singleton

---

## *Ordering*

Most data that returns from a query generally are not sorted in a particular order. As a result, it's not particularly easy to read through queries especially when there may be thousands if not millions of rows. Because of this, SQL provides the keywords `ORDER BY` as a solution.

`SELECT column_one, column_ two, ... `
`FROM Table`
`WHERE condition_one, condition_two, ... `
==ORDER BY== `column` ==ASC/DESC==`;`

| Keyword | Description                | Example                                                     |
| ------- | -------------------------- | ----------------------------------------------------------- |
| `ASC`   | Order by ascending values  | `SELECT` *column* `FROM` *Table* `ORDER BY` *column* `ASC`  |
| `DESC`  | Order by descending values | `SELECT` *column* `FROM` *Table* `ORDER BY` *column* `DESC` |

There are also multiple other clauses to not only order, but also `LIMIT` and `OFFSET` which are used to optimize queries even further.

`SELECT column_one, column_ two, ... `
`FROM Table`
`WHERE condition_one, condition_two, ... `
`ORDER BY column` ==ASC/DESC==`;`

| Keyword  | Description                                          | Example                                                |
| -------- | ---------------------------------------------------- | ------------------------------------------------------ |
| `LIMIT`  | reduce the number of rows returned                   | `SELECT` *column* `FROM` *Table* `LIMIT` *num_limit*   |
| `OFFSET` | Specify where to begin counting the number rows from | `SELECT` *column* `FROM` *Table* `OFFSET` *num_offset* |
Using these keywords are essential for API's. Think of [infinite scroll](https://htmx.org/examples/infinite-scroll/) technique that is used by [Reddit](www.reddit.com) or any content driven website. Because of this, it's essential to be comfortable with these keywords.

