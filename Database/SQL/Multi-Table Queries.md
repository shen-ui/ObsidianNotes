
Entity data in the real world is often broken down into pieces and stored across multiple orthogonal tables using a process called *normalization*.

---

*Normalization* is useful in reducing duplicate data in a table, allows data to grow independent and allows databases to add functionality in security, complexity or added services. As a trade-off queries become more complex since they need to find additional data from different parts of a database. There are also performance issues that may arise. 

Tables that share information about a single entity need to have a *primary key* that uniquely identities other entities across a database. A common way of implementation is the use of auto-incrementing integers, but may also include strings or hash values.

`JOIN` is a keyword used in a query to combine row data across seperate tables within a database.
There are multiple forms of `JOIN`.


