# 2. Relational Model & Relational Algebra

## 2.1 Relational Model Vocabulary

| Term | Meaning | Table analogy |
| --- | --- | --- |
| Relation | Set of tuples | Table |
| Tuple | One record | Row |
| Attribute | Named column | Column |
| Domain | Set of allowed values for an attribute | Data type |
| Degree (arity) | Number of attributes | Number of columns |
| Cardinality | Number of tuples | Number of rows |
| Schema | Relation name + attributes, e.g. `R(A, B, C)` | Table definition |
| Instance | Data present at a moment | Table contents |

Key facts:

- A relation is a **set** → no duplicate tuples, order of rows doesn't matter (SQL tables are **bags** and allow duplicates).
- Attribute values are **atomic** (1NF).
- `NULL` means unknown / not applicable.

## 2.2 Keys

| Key | Definition |
| --- | --- |
| Super key | Any set of attributes that uniquely identifies a tuple |
| Candidate key | Minimal super key (no proper subset is a super key) |
| Primary key | One chosen candidate key; cannot be NULL |
| Alternate key | Candidate keys not chosen as primary |
| Foreign key | Attributes referring to the primary (or candidate) key of another / same relation |
| Prime attribute | Belongs to **some** candidate key |

**Counting super keys**: if a relation has `n` attributes and a single candidate key of `k` attributes,
number of super keys = `2^(n−k)`.
For two candidate keys `K1`, `K2`: `|SK| = |SK(K1)| + |SK(K2)| − |SK(K1 ∪ K2)|` (inclusion–exclusion).

Example: `R(A,B,C,D)`, candidate keys `A` and `B` → `2^3 + 2^3 − 2^2 = 12` super keys.

## 2.3 Relational Algebra (RA) Operators

RA is **procedural**: you say *how* to get the result. Inputs and outputs are relations (sets).

### Basic (fundamental) operators

| Operator | Symbol | Result |
| --- | --- | --- |
| Selection | `σ_condition(R)` | Rows of R satisfying condition |
| Projection | `π_attrs(R)` | Only listed columns, **duplicates removed** |
| Union | `R ∪ S` | Rows in R or S (union-compatible) |
| Set difference | `R − S` | Rows in R but not in S |
| Cartesian product | `R × S` | Every row of R paired with every row of S |
| Rename | `ρ_newName(R)` | Renames relation/attributes |

`{σ, π, ∪, −, ×, ρ}` is a **complete set**: every other RA operator can be written with these.

### Derived operators

| Operator | Definition using basic operators |
| --- | --- |
| Intersection `R ∩ S` | `R − (R − S)` |
| Theta join `R ⋈_θ S` | `σ_θ(R × S)` |
| Equi join | Theta join with only `=` |
| Natural join `R ⋈ S` | Equi join on all common attributes, then keep one copy of each common column |
| Division `R ÷ S` | See 2.5 |
| Left/right/full outer join | Join + unmatched rows padded with NULL |

**Union compatibility**: same number of attributes and matching domains, in order.

## 2.4 Tuple Count Bounds (Very Frequently Asked)

Let `|R| = m`, `|S| = n`.

| Expression | Minimum rows | Maximum rows |
| --- | --- | --- |
| `σ_c(R)` | 0 | m |
| `π_A(R)` | 1 (if m > 0) | m |
| `R ∪ S` | max(m, n) | m + n |
| `R ∩ S` | 0 | min(m, n) |
| `R − S` | 0 | m |
| `R × S` | m·n | m·n |
| `R ⋈ S` (natural) | 0 | m·n |
| `R ⋈ S`, common attribute is the key of S | 0 | m |
| `R ⋈ S`, common attribute is FK in R referring to key of S (no NULL FK) | m | m |
| `R ⟕ S` (left outer) | m | max(m, m·n) |
| `R ⟗ S` (full outer) | max(m, n) | max(m·n, m + n) |

> If R and S have **no common attribute**, natural join = Cartesian product.

## 2.5 Division

`R(A, B) ÷ S(B)` returns all `A` values that are paired in R with **every** `B` value in S.
Use it for "**for all**" queries, e.g. "students who took **all** courses".

```text
R ÷ S = π_A(R) − π_A( (π_A(R) × S) − R )
```

Example:

| R: sid | cid |
| --- | --- |
| 1 | C1 |
| 1 | C2 |
| 2 | C1 |

`S = {C1, C2}` → `R ÷ S = {1}`.

## 2.6 Outer Joins

| Join | Keeps unmatched rows from |
| --- | --- |
| Left outer `⟕` | Left relation |
| Right outer `⟖` | Right relation |
| Full outer `⟗` | Both |

Example: `R1(A,B) = {(1,5), (3,7)}`, `R2(A,C) = {(1,7), (4,9)}`.

`R1 ⟗ R2` (natural, on A) = `{(1,5,7), (3,7,NULL), (4,NULL,9)}`.

## 2.7 Useful Equivalences

1. `σ_{c1 ∧ c2}(R) = σ_{c1}(σ_{c2}(R))` — selections cascade and commute.
2. `π_A(π_{A,B}(R)) = π_A(R)` — only the last projection matters.
3. `σ_c(R ⋈ S) = σ_c(R) ⋈ S` if c uses only R's attributes (**push selection down**).
4. Joins and Cartesian products are commutative and associative.
5. `σ_c(R ∪ S) = σ_c(R) ∪ σ_c(S)`; same for `−` and `∩`.
6. `π` distributes over `∪` but **not** over `−` or `∩` in general.

## 2.8 Common Traps

1. Projection removes duplicates in RA; SQL `SELECT` does **not** (use `DISTINCT`).
2. `σ` in RA ≈ `WHERE` in SQL; `π` in RA ≈ `SELECT` column list in SQL.
3. Referential integrity (`r.B` FK → `s.C`) means `π_B(r) − π_C(s) = ∅` (ignoring NULL FKs).
4. A selection that filters the right side **before** a left outer join is not the same as filtering after it.
5. Division answers "all"; difference answers "not / none".
