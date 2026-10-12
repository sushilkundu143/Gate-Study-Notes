# 4. SQL

SQL is the practical query language. GATE mostly asks you to **predict the output** of a query or
pick the query that matches an English statement.

## 4.1 Query Skeleton and Logical Execution Order

```sql
SELECT   DISTINCT column_list        -- 5. pick columns (6. remove duplicates)
FROM     tables / joins               -- 1. build the rows
WHERE    row_condition                -- 2. filter rows
GROUP BY grouping_columns             -- 3. form groups
HAVING   group_condition              -- 4. filter groups
ORDER BY columns                      -- 7. sort
```

> `WHERE` filters **rows** before grouping; `HAVING` filters **groups** after grouping.
> Aggregates (`COUNT`, `SUM`, `AVG`, `MIN`, `MAX`) cannot appear in `WHERE`.

## 4.2 DDL and DML

```sql
CREATE TABLE Dept (
  dept_id   INT PRIMARY KEY,
  name      VARCHAR(50) NOT NULL UNIQUE
);

CREATE TABLE Emp (
  emp_id    INT PRIMARY KEY,
  name      VARCHAR(50),
  salary    INT CHECK (salary > 0),
  dept_id   INT REFERENCES Dept(dept_id) ON DELETE SET NULL
);

INSERT INTO Emp VALUES (1, 'Asha', 50000, 10);
UPDATE Emp SET salary = salary * 1.1 WHERE dept_id = 10;
DELETE FROM Emp WHERE salary < 1000;
ALTER TABLE Emp ADD COLUMN email VARCHAR(100);
DROP TABLE Emp;         -- removes table and data
```

| Command | Category |
| --- | --- |
| `CREATE`, `ALTER`, `DROP`, `TRUNCATE` | DDL |
| `INSERT`, `UPDATE`, `DELETE`, `SELECT` | DML |
| `GRANT`, `REVOKE` | DCL |
| `COMMIT`, `ROLLBACK`, `SAVEPOINT` | TCL |

## 4.3 NULL and Three-Valued Logic (Common Trap)

Any comparison with `NULL` gives **UNKNOWN**, not TRUE/FALSE. `WHERE` keeps only TRUE rows.

| AND | T | U | F |
| --- | --- | --- | --- |
| **T** | T | U | F |
| **U** | U | U | F |
| **F** | F | F | F |

| OR | T | U | F |
| --- | --- | --- | --- |
| **T** | T | T | T |
| **U** | T | U | U |
| **F** | T | U | F |

`NOT U = U`.

Rules to remember:

1. `x = NULL` is never true → use `x IS NULL`.
2. Aggregates **ignore NULLs**, except `COUNT(*)` which counts rows.
3. `AVG(col)` = `SUM(col) / COUNT(col)` (NULLs excluded from both).
4. `x NOT IN (1, 2, NULL)` is never TRUE → returns **no rows**.
5. `GROUP BY` puts all NULLs in **one** group.
6. `DISTINCT` and `UNION` treat NULLs as equal to each other.

## 4.4 Joins

```sql
SELECT * FROM A INNER JOIN B ON A.id = B.id;      -- matched rows only
SELECT * FROM A LEFT  JOIN B ON A.id = B.id;      -- all A, NULL-padded B
SELECT * FROM A RIGHT JOIN B ON A.id = B.id;      -- all B
SELECT * FROM A FULL  JOIN B ON A.id = B.id;      -- all rows from both
SELECT * FROM A CROSS JOIN B;                     -- Cartesian product
SELECT * FROM A NATURAL JOIN B;                   -- join on all same-named columns
```

## 4.5 Aggregation and Grouping

```sql
-- Departments whose average salary is above 50,000
SELECT dept_id, AVG(salary)
FROM   Emp
GROUP  BY dept_id
HAVING AVG(salary) > 50000;
```

Rule: every non-aggregated column in `SELECT` must appear in `GROUP BY`.

## 4.6 Subqueries

| Form | Meaning |
| --- | --- |
| `x IN (subquery)` | x equals some value |
| `x NOT IN (subquery)` | x equals none (beware NULLs) |
| `x > ALL (subquery)` | x greater than every value (TRUE if subquery is empty) |
| `x > ANY / SOME (subquery)` | x greater than at least one value (FALSE if empty) |
| `EXISTS (subquery)` | subquery returns at least one row |
| `NOT EXISTS (subquery)` | subquery returns no rows |

**Correlated subquery**: the inner query uses a column from the outer query, so it is re-evaluated per outer row.

```sql
-- Employees earning more than their department's average
SELECT e.name
FROM   Emp e
WHERE  e.salary > (SELECT AVG(salary) FROM Emp x WHERE x.dept_id = e.dept_id);
```

**Highest salary without MAX**

```sql
SELECT salary FROM Emp WHERE salary >= ALL (SELECT salary FROM Emp);
```

**Second highest salary**

```sql
SELECT MAX(salary) FROM Emp WHERE salary < (SELECT MAX(salary) FROM Emp);
```

**"For all" (division) with double NOT EXISTS**

```sql
-- Students who took every course
SELECT s.sid FROM Student s
WHERE NOT EXISTS (
  SELECT c.cid FROM Course c
  WHERE NOT EXISTS (
    SELECT * FROM Enroll e WHERE e.sid = s.sid AND e.cid = c.cid));
```

## 4.7 Set Operations

| SQL | Duplicates |
| --- | --- |
| `UNION` / `INTERSECT` / `EXCEPT` | Removed |
| `UNION ALL` / `INTERSECT ALL` / `EXCEPT ALL` | Kept (bag semantics) |

With bags, if a row appears `m` times in A and `n` times in B:

- `UNION ALL` → `m + n`
- `INTERSECT ALL` → `min(m, n)`
- `EXCEPT ALL` → `max(0, m − n)`

## 4.8 Views

- A **view** is a stored query (virtual table).
- Updatable only if simple: one base table, no aggregates, no `DISTINCT`, no `GROUP BY`.
- A **materialized view** stores its result and must be refreshed.

## 4.9 Output-Prediction Method

1. Build `FROM` rows (draw the join/product).
2. Apply `WHERE` (watch NULLs).
3. Group, then compute aggregates.
4. Apply `HAVING`.
5. Project columns; apply `DISTINCT` only if written.
6. For correlated subqueries, evaluate per outer row in a small table.

## 4.10 Common Traps

1. `COUNT(col)` vs `COUNT(*)` vs `COUNT(DISTINCT col)` give different answers when NULLs/duplicates exist.
2. `SELECT` keeps duplicates; RA projection does not.
3. `> ALL (empty)` is TRUE; `> ANY (empty)` is FALSE.
4. `NOT IN` with a NULL in the subquery returns nothing.
5. `HAVING` without `GROUP BY` treats the whole table as one group.
