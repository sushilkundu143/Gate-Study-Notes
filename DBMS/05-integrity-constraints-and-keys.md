# 5. Integrity Constraints and Keys

Integrity constraints are rules the DBMS enforces so data always stays valid.

## 5.1 Types of Constraints

| Constraint | Rule | SQL |
| --- | --- | --- |
| Domain | Value must belong to the attribute's domain/type | `INT`, `CHECK (age >= 18)` |
| Not-null | Attribute cannot be NULL | `NOT NULL` |
| Key (uniqueness) | No two tuples share the same key value | `UNIQUE`, `PRIMARY KEY` |
| Entity integrity | Primary key attributes can never be NULL | `PRIMARY KEY` |
| Referential integrity | FK value must exist in referenced key, or be NULL | `FOREIGN KEY ... REFERENCES` |
| General / semantic | Any business rule | `CHECK`, `ASSERTION`, triggers |

## 5.2 Referential Integrity in Detail

`Emp.dept_id` references `Dept.dept_id`. `Emp` is the **referencing (child)** table; `Dept` is the **referenced (parent)** table.

| Operation | Can it violate referential integrity? |
| --- | --- |
| Insert into child | **Yes** (FK value may not exist in parent) |
| Delete from child | No |
| Update child FK | **Yes** |
| Insert into parent | No |
| Delete from parent | **Yes** (children left dangling) |
| Update parent key | **Yes** |

Actions when a parent row is deleted/updated:

| Action | Effect on child rows |
| --- | --- |
| `NO ACTION` / `RESTRICT` (default) | Reject the delete |
| `CASCADE` | Delete (or update) matching child rows too, recursively |
| `SET NULL` | Set child FK to NULL |
| `SET DEFAULT` | Set child FK to its default value |

### ON DELETE CASCADE chain example

Table `T(A primary key, C references T(A) ON DELETE CASCADE)`:

| A | C |
| --- | --- |
| 2 | 4 |
| 3 | 4 |
| 4 | 3 |
| 5 | 2 |
| 7 | 2 |
| 9 | 5 |
| 6 | 4 |

Delete `(2,4)` → rows with `C = 2` are deleted: `(5,2)`, `(7,2)` → then rows with `C = 5`: `(9,5)` → then `C = 7` or `C = 9`: none.
Additionally deleted: **(5,2), (7,2), (9,5)**.

## 5.3 Assertions and Triggers

```sql
CREATE ASSERTION salary_cap CHECK (
  NOT EXISTS (SELECT * FROM Emp WHERE salary > 1000000)
);

CREATE TRIGGER audit_salary AFTER UPDATE OF salary ON Emp
FOR EACH ROW INSERT INTO SalaryLog VALUES (NEW.emp_id, OLD.salary, NEW.salary);
```

- **CHECK**: checked on the row being inserted/updated (one table).
- **ASSERTION**: database-wide condition; any table.
- **Trigger**: event → condition → action (ECA rule).

## 5.4 Keys Recap

- Super key ⊇ candidate key; primary key is one candidate key.
- A foreign key must refer to the **whole** primary/candidate key of the referenced table.
- A foreign key may be NULL (unless declared `NOT NULL`) and may repeat.
- A table can reference itself (self-referencing FK, e.g. `manager_id`).

## 5.5 Common Traps

1. Deleting from the **child** table never violates referential integrity.
2. Cascades are **recursive** — follow the chain until nothing more is deleted.
3. If the FK in the referencing table is part of a composite key, it must match the full referenced key.
4. Entity integrity concerns the **primary key** only; other candidate keys declared `UNIQUE` may allow NULLs.
