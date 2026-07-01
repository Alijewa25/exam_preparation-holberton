##  SQL & Database

**1. Difference between DDL, DML, DCL?**
- **DDL** (Data Definition Language): defines/modifies structure — `CREATE`, `ALTER`, `DROP`.
- **DML** (Data Manipulation Language): manages data — `SELECT`, `INSERT`, `UPDATE`, `DELETE`.
- **DCL** (Data Control Language): manages permissions — `GRANT`, `REVOKE`.
**2. Basic syntax for `SELECT`, `INSERT INTO`, `UPDATE...SET...WHERE`, `DELETE FROM...WHERE`?**
```sql
SELECT column1, column2 FROM table WHERE condition;
INSERT INTO table (col1, col2) VALUES (val1, val2);
UPDATE table SET col1 = val1 WHERE condition;
DELETE FROM table WHERE condition;
```
 
**3. `CREATE TABLE` syntax? Common data types?**
```sql
CREATE TABLE users (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    age INT,
    is_active BOOLEAN
);
```
Common types: `INT`, `VARCHAR(n)`, `TEXT`, `FLOAT`/`DECIMAL`, `DATE`/`DATETIME`, `BOOLEAN`.
 
**4. What do `ORDER BY`, `GROUP BY`, `HAVING`, `LIMIT` do?**
- `ORDER BY` — sorts results (`ASC`/`DESC`).
- `GROUP BY` — groups rows sharing the same value in specified columns, usually used with aggregate functions.
- `HAVING` — filters **grouped** results (like `WHERE`, but applied **after** `GROUP BY`).
- `LIMIT` — restricts the number of rows returned.
**5. Aggregate functions — COUNT, SUM, AVG, MIN, MAX?**
- `COUNT()` — counts rows.
- `SUM()` — adds up numeric values.
- `AVG()` — calculates average.
- `MIN()` / `MAX()` — smallest/largest value.
```sql
SELECT COUNT(*), AVG(age) FROM users;
```
 
**6. JOIN types — INNER, LEFT, RIGHT, FULL OUTER?**
- **INNER JOIN** — returns only rows with matches in **both** tables.
- **LEFT JOIN** — returns all rows from the **left** table, plus matches from the right (NULL if no match).
- **RIGHT JOIN** — returns all rows from the **right** table, plus matches from the left.
- **FULL OUTER JOIN** — returns all rows from **both** tables, matched where possible, NULL where not.
**7. What do `GRANT` and `REVOKE` do?**
`GRANT` gives a user specific **privileges** (e.g. `SELECT`, `INSERT`) on a database/table. `REVOKE` **removes** previously granted privileges.
```sql
GRANT SELECT, INSERT ON users TO 'someuser';
REVOKE INSERT ON users FROM 'someuser';
```
 
**8. MySQL — `SHOW DATABASES`, `USE`, `DESCRIBE`?**
- `SHOW DATABASES;` — lists all databases on the server.
- `USE database_name;` — selects a database to work with.
- `DESCRIBE table_name;` — shows the structure (columns, types) of a table.
