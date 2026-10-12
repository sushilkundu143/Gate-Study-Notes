# 9. Solved GATE PYQs — DBMS (Topic-wise)

How to use this file:

1. Cover the solution, attempt the question, then check.
2. Questions are **rewritten in our own words**; numbers and logic match the original exam question.
3. `[GATE YYYY]` = previous year question. `[GATE-pattern]` = practice question built on a repeatedly asked pattern.
4. Computed answers (keys, closures, serializability, index arithmetic, SQL output) were re-checked with scripts.

## Contents

- [A. ER Model](#a-er-model)
- [B. Relational Algebra](#b-relational-algebra)
- [C. Tuple Relational Calculus](#c-tuple-relational-calculus)
- [D. SQL](#d-sql)
- [E. Integrity Constraints and Keys](#e-integrity-constraints-and-keys)
- [F. Functional Dependencies and Normal Forms](#f-functional-dependencies-and-normal-forms)
- [G. File Organization and Indexing](#g-file-organization-and-indexing)
- [H. Transactions and Concurrency Control](#h-transactions-and-concurrency-control)

---

## A. ER Model

### A1. [GATE 2005] Minimum tables for two relationships

Entities E1 and E2 have only simple single-valued attributes. Relationship R1 (between E1 and E2) is one-to-many,
and R2 (also between E1 and E2) is many-to-many. Neither relationship has attributes.
What is the minimum number of relational tables needed?

**Answer: 3**

- E1 → 1 table, E2 → 1 table.
- R1 is one-to-many → store as a foreign key on the "many" side; no extra table.
- R2 is many-to-many → needs its own table.
- Total = 2 + 1 = **3**.

### A2. [GATE 2017] When can the relationship table merge with an entity table?

Entity types A and B are connected by relationship R (no attributes). When can R's table be merged with A's table?

**Answer: When R is many-to-one from A to B and A's participation in R is total.**

- Many-to-one from A to B → each A row relates to **at most one** B, so B's key fits as one column in A.
- Total participation of A → every A row has a value, so no NULL padding is needed.

### A3. [GATE 2018] Many-to-one with total participation on both sides

R is many-to-one from E1 to E2. Both E1 and E2 participate totally, and |E1| > |E2|. Which statement is always true?

**Answer: Every entity in E1 is associated with exactly one entity in E2.**

- Many-to-one from E1 → each E1 relates to **at most one** E2.
- Total participation of E1 → each E1 relates to **at least one** E2.
- Together → **exactly one**.
- E2 entities relate to at least one E1 (total) and possibly many; "exactly one" or "at most one" for E2 is not guaranteed.

### A4. [GATE-pattern] Tables for weak entity + multivalued attribute

`Employee(eid, name, {phone})` (phone multivalued) owns weak entity `Dependent(dname, age)` through identifying relationship `Has`.
`Employee` M:N `Project(pid)` through `WorksOn(hours)`. Minimum tables?

**Answer: 5** — Employee, EmployeePhone(eid, phone), Dependent(eid, dname, age), Project, WorksOn(eid, pid, hours).
The identifying relationship `Has` needs no table (it is the FK `eid` inside Dependent).

### A5. [GATE-pattern] 1:1 relationship, total participation on both sides

`Person` 1:1 `Passport` with total participation on both sides, no other relationships. Minimum tables?

**Answer: 1** — every person has exactly one passport and vice versa, so both can be stored in one table.

---

## B. Relational Algebra

### B1. [GATE 2012] Referential integrity in RA

`R1(A, B)`, `R2(C, D)`; `B` is a foreign key referring to `C`. If instances satisfy referential integrity, which is always true?

**Answer: `π_B(r1) − π_C(r2) = ∅`**

Every B value in r1 must exist among the C values of r2, so removing all C values leaves nothing.
The reverse (`π_C(r2) − π_B(r1) = ∅`) is not required: a parent row may have no children.

### B2. [GATE 2004] Which expression is necessarily empty?

`R1(A, B, C)` with key A, `R2(D, E)` with key D, and `C` is a foreign key referring to `D`. No violations.

**Answer: `π_C(r1) − π_D(r2)`** is necessarily empty (same reasoning as B1).

### B3. [GATE 2015] Full natural outer join

`R1(A,B) = {(1,5), (3,7)}`, `R2(A,C) = {(1,7), (4,9)}`. `R = R1 ⟗ R2`. Which tuples are in R?

**Answer: `(1,5,7)`, `(3,7,NULL)`, `(4,NULL,9)`**

- A = 1 matches → `(1,5,7)`.
- A = 3 only in R1 → `(3,7,NULL)`.
- A = 4 only in R2 → `(4,NULL,9)`.

### B4. [GATE 2018] Which expression is NOT equivalent to `r ⋈ σ_{B<5}(s)`?

`r(A,B)`, `s(B,C)`; `s.B` is the primary key and `r.B` is a foreign key referring to `s.B`. `⟕` = natural left outer join.

**Answer: `r ⟕ σ_{B<5}(s)` is NOT equivalent.**

- It keeps **every** r tuple; tuples with `B ≥ 5` appear padded with NULL, but Q drops them.
- `σ_{B<5}(r ⋈ s)`, `σ_{B<5}(r ⟕ s)` and `σ_{B<5}(r) ⟕ s` all equal Q (FK guarantees each r tuple has a match).

### B5. [GATE 2014] Simplifying nested selections and projections

Optimize `π_A1( π_A2( σ_F1( σ_F2(r) ) ) )`, where A1 ⊆ A2.

**Answer: `π_A1( σ_{F1 ∧ F2}(r) )`**

Cascaded selections combine with ∧; only the outermost projection matters.

### B6. [GATE 2010] Maximum size of a natural join

`R(A,B,C)` and `S(B,D,E)` with FDs `B → A`, `A → C`. `|R| = 200`, `|S| = 100`. Maximum tuples in `R ⋈ S`?

**Answer: 100**

The join is on `B`. Since `B → A` and `A → C`, `B` is a key of R, so each S tuple matches **at most one** R tuple.
Maximum = |S| = **100**.

### B7. [GATE 2007] What does this expression return?

`studInfo(studId, name, sex)`, `enroll(studId, courseId)`:

```text
π_courseId( ( π_studId(σ_sex='female'(studInfo)) × π_courseId(enroll) ) − enroll )
```

**Answer: courses in which at least one female student is not enrolled** (i.e. not all female students take the course).

- The product pairs every female student with every course.
- Subtracting `enroll` keeps pairs (female, course) where that female is **not** enrolled.
- Project the course ids.

### B8. [GATE-pattern] Division

`Takes(sid, cid) = {(1,C1),(1,C2),(2,C1),(3,C1),(3,C2),(3,C3)}`, `Course(cid) = {C1, C2}`.
`Takes ÷ Course` = ?

**Answer: `{1, 3}`** — the students paired with **both** C1 and C2.

### B9. [GATE-pattern] Tuple bounds

`|R| = 10`, `|S| = 20`, no common attributes. Rows in `R ⋈ S`?

**Answer: 200** — natural join without common attributes is a Cartesian product.

---

## C. Tuple Relational Calculus

### C1. [GATE 2008] Equivalent form of a universal quantifier

Which TRC expression is equivalent to `∀ t ∈ r (P(t))`?

I. `¬∃ t ∈ r (P(t))`  II. `∃ t ∉ r (P(t))`  III. `¬∃ t ∈ r (¬P(t))`  IV. `∃ t ∉ r (¬P(t))`

**Answer: III only.** "Every t satisfies P" = "no t fails P".

### C2. [GATE-classic] Expressive power

Which have the same expressive power: (I) relational algebra, (II) safe TRC, (III) safe DRC?

**Answer: All three (Codd's theorem).**

### C3. [GATE-pattern] Translate TRC to English

`Emp(eid, dept, sal)`

```text
{ t | t ∈ Emp ∧ ¬∃ s ∈ Emp ( s.dept = t.dept ∧ s.sal > t.sal ) }
```

**Answer: employees who have the highest salary in their department** (ties included).

### C4. [GATE-pattern] Is this expression safe?

`{ t | ¬(t ∈ Emp) }`

**Answer: Unsafe** — the result is every possible tuple not in Emp, which is infinite.

---

## D. SQL

### D1. [GATE 2015] SQL SELECT vs relational algebra

The SQL `SELECT` clause is equivalent to which RA operation?

**Answer: Projection, except that SQL `SELECT` may return duplicates.**

### D2. [GATE 2012] HAVING and GROUP BY

Which statements are true?

- P: A query can contain `HAVING` even without `GROUP BY`.
- Q: A query can contain `HAVING` only if it has `GROUP BY`.
- R: All `GROUP BY` attributes must appear in `SELECT`.
- S: Not all `GROUP BY` attributes need to appear in `SELECT`.

**Answer: P and S.** Without `GROUP BY`, `HAVING` treats the whole table as one group.

### D3. [GATE 2004] Interpreting a grouped query

`Employee(name, sex, salary, deptName)`

```sql
SELECT deptName FROM Employee
WHERE  sex = 'M'
GROUP  BY deptName
HAVING AVG(salary) > (SELECT AVG(salary) FROM Employee);
```

**Answer: departments where the average salary of male employees is greater than the average salary of all employees in the company.**

`WHERE` keeps only male rows **before** grouping; the subquery averages over everyone.

### D4. [GATE 2011] Generated table values

Table `T(X, Y)` starts with `(1, 1)`. 128 times, a row `(MX + 1, 2·MY + 1)` is inserted, where MX and MY are the current maximums.
What does `SELECT Y FROM T WHERE X = 7;` return?

**Answer: 127**

Y sequence: 1, 3, 7, 15, 31, 63, 127 → `Y = 2^X − 1` → X = 7 gives **127**. (Verified in SQLite.)

### D5. [GATE-pattern] Aggregates and NULL

`Emp(id, dept, salary) = (1,10,100), (2,10,NULL), (3,20,300), (4,20,300), (5,NULL,200)`

Find `COUNT(*)`, `COUNT(salary)`, `COUNT(DISTINCT salary)`, `AVG(salary)`.

**Answer: 5, 4, 3, 225**

- `COUNT(*)` counts rows (5).
- `COUNT(salary)` ignores NULL (4).
- Distinct non-NULL values {100, 200, 300} (3).
- `AVG = (100 + 300 + 300 + 200) / 4 = 225` (NULL excluded from numerator and denominator).

### D6. [GATE-pattern] NOT IN with NULL

Same `Emp`; `Ban(dept) = {20, NULL}`.

```sql
SELECT id FROM Emp WHERE dept NOT IN (SELECT dept FROM Ban);
```

**Answer: empty result.**
For dept 10: `10 <> 20` is TRUE but `10 <> NULL` is UNKNOWN → overall UNKNOWN → row dropped. Every row is dropped.
(`IN` instead of `NOT IN` returns ids 3 and 4.)

### D7. [GATE-pattern] GROUP BY with NULL

Same `Emp`. Number of groups from `SELECT dept, COUNT(*) FROM Emp GROUP BY dept`?

**Answer: 3 groups** — NULL, 10 and 20 (all NULLs form one group).

### D8. [GATE-pattern] Correlated subquery

Same `Emp`.

```sql
SELECT COUNT(*) FROM Emp e
WHERE e.salary >= (SELECT MAX(salary) FROM Emp x WHERE x.dept = e.dept);
```

**Answer: 3**

- id 1: max in dept 10 is 100 → TRUE.
- id 2: NULL salary → UNKNOWN.
- ids 3, 4: 300 ≥ 300 → TRUE.
- id 5: dept is NULL → `x.dept = NULL` matches nothing → subquery NULL → UNKNOWN.

### D9. [GATE-pattern] ALL on an empty subquery

`SELECT COUNT(*) FROM Emp WHERE salary > ALL (SELECT salary FROM Emp WHERE dept = 99);` (no dept 99)

**Answer: 5 (all rows), in standard SQL.**

`x > ALL (empty set)` is TRUE for every row — even a NULL salary — because there is no value it could fail against.
(The opposite: `x > ANY (empty set)` is FALSE for every row, giving 0.)

> Rule: `ALL` over an empty set is TRUE; `ANY`/`SOME` over an empty set is FALSE.

### D10. [GATE-pattern] Bag semantics

`A(x) = {1, 1, 2, 3}`, `B(x) = {1, 2, 2, 4}`.

| Query | Result rows |
| --- | --- |
| `A UNION B` | 4 (`{1,2,3,4}`) |
| `A UNION ALL B` | 8 |
| `A JOIN B ON A.x = B.x` | 4 (two 1s × one 1 = 2, one 2 × two 2s = 2) |
| `A LEFT JOIN B ON A.x = B.x` | 5 (above 4 + unmatched 3) |

---

## E. Integrity Constraints and Keys

### E1. [GATE 2005] ON DELETE CASCADE chain

`T(A, C)`: A is the primary key; C is a foreign key referring to A with `ON DELETE CASCADE`.
Rows: `(2,4), (3,4), (4,3), (5,2), (7,2), (9,5), (6,4)`. Delete `(2,4)`. Which rows must also be deleted?

**Answer: `(5,2), (7,2), (9,5)`**

Delete A=2 → rows with C=2: (5,2), (7,2) → rows with C=5: (9,5) → rows with C=7 or C=9: none.

### E2. [GATE 2014] Foreign keys and assertions

- S1: A foreign key declaration can always be replaced by an equivalent check assertion.
- S2: If `R(a, b, c)` has primary key `(a, b)`, then `CREATE TABLE S (a INT, d INT, e INT, PRIMARY KEY (d), FOREIGN KEY (a) REFERENCES R)` is valid.

**Answer: Both false.**

- S1: an assertion cannot reproduce referential actions like `ON DELETE CASCADE`.
- S2: `a` alone cannot reference R because R's primary key is `(a, b)`.

### E3. [GATE 2016] Which is NOT a super key?

Schema `(V, W, X, Y, Z)` with primary key `VY`.

**Answer: `VWXZ`** — it does not contain Y, so it does not contain the key `VY`. Any set containing both V and Y is a super key.

### E4. [GATE-pattern] Count super keys

`R(A, B, C, D, E)` with candidate keys `A` and `BC`. How many super keys?

**Answer: 20**

- Contain A: `2^4 = 16`.
- Contain B and C: `2^3 = 8`.
- Contain A, B and C: `2^2 = 4`.
- Total = 16 + 8 − 4 = **20**.

### E5. [GATE-pattern] Which operation can violate referential integrity?

`Emp.dept` references `Dept.id`.

**Answer: inserting into Emp, updating Emp.dept, deleting from Dept, updating Dept.id.** Deleting from Emp or inserting into Dept never violates it.

---

## F. Functional Dependencies and Normal Forms

### F1. [GATE 2013] Count candidate keys

`R(A,B,C,D,E,F,G,H)`, `F = {CH→G, A→BC, B→CFH, E→A, F→EG}`. How many candidate keys?

**Answer: 4 — `AD, BD, ED, FD`**

- D never appears on a right side → D is in every key.
- `(AD)+`: A→BC, B→CFH, F→EG, CH→G → all ✓.
- Similarly B, E, F each with D reach everything; C, G, H with D do not.

### F2. [GATE 2013] Normal form of the same relation

Same R and F as F1. Highest normal form?

**Answer: 1NF but not 2NF.**
Key `AD` is composite and `A → BC` makes the non-prime attribute C depend on part of a key (partial dependency).

### F3. [GATE 2005] Candidate keys

`R(A,B,C,D,E,H)`, `F = {A→B, BC→D, E→C, D→A}`.

**Answer: `AEH, BEH, DEH`** (full working in [file 06, §6.3](./06-functional-dependencies-and-normalization.md#63-finding-all-candidate-keys-exam-method)).

### F4. [GATE 2014] Key of R

`R(E,F,G,H,I,J,K,L,M,N)`, `F = {EF→G, F→IJ, EH→KL, K→M, L→N}`.

**Answer: `EFH`**

E, F, H never appear on a right side. `(EFH)+ = EFH → G (EF) → IJ (F) → KL (EH) → M → N` = all 10 attributes.

### F5. [GATE 2016] Weakest normal form gained by redesign

`Article(Volume, Number, StartPage, EndPage, Title, Year, Price)`, key `(V, N, S, E)`.
FDs: `VNSE → Title`, `VN → Year`, `VNSE → Price`. Redesign: `(V, N, S, E, Title, Price)` and `(V, N, Year)`.

**Answer: 2NF**

`VN → Year` is a partial dependency (VN is part of the key), so the old schema is not in 2NF. After the split both parts are in 2NF (in fact BCNF).

### F6. [GATE 2017] Minimal cover

`R(V,W,X,Y,Z)`, `F = {V→W, VW→X, Y→VX, Y→Z}`.

**Answer: `{V→W, V→X, Y→V, Y→Z}`** (working in [file 06, §6.4](./06-functional-dependencies-and-normalization.md#64-equivalence-and-minimal-canonical-cover)).

### F7. [GATE 2019] BCNF and dependency preservation of a decomposition

`X(P,Q,R,S)`, `F = {QR→S, R→P, S→Q}`. Decompose into `Y(P,R)` and `Z(Q,R,S)`.
I: Y and Z are both in BCNF. II: The decomposition is dependency preserving.

**Answer: Only II is true.**

- Y(P,R) with R→P → BCNF.
- Z(Q,R,S): keys QR and RS. `S → Q` holds but S is not a super key → **not BCNF**.
- `R→P` lives in Y; `QR→S`, `S→Q` live in Z → all preserved.

### F8. [GATE 2001] Lossless or dependency preserving?

`R(A,B,C,D)`, `F = {A→B, C→D}`, decomposed into `R1(A,B)`, `R2(C,D)`.

**Answer: dependency preserving but not lossless.**
`R1 ∩ R2 = ∅`, which determines nothing → lossy (the join is a Cartesian product).

### F9. [GATE 2005] Lossy join result

`r(A,B,C,D)`, `r1 = π_ABC(r)`, `r2 = π_AD(r)`, `s = r1 ⋈ r2`. The decomposition is lossy. Which is true?

**Answer: `r ⊂ s`** — a lossy join always produces extra (spurious) tuples, never fewer.

### F10. [GATE-concept] 3NF but not BCNF

R is in 3NF but not BCNF. Which must be true?

**Answer: R has a non-trivial FD `X → A` where X is not a super key and A is a prime attribute.**

### F11. [GATE-pattern] Highest normal form

`R(A,B,C,D)`, `F = {AB→C, C→D, D→A}`.

**Answer: 3NF (not BCNF)**

- Keys: `AB, BC, BD` → every attribute is prime.
- `C→D` and `D→A`: left sides are not super keys → BCNF violated.
- Right sides D and A are prime → 3NF satisfied.

### F12. [GATE-pattern] Cyclic FDs

`R(A,B,C,D,E)`, `F = {A→B, B→C, C→D, D→A}`. Candidate keys and highest NF?

**Answer: keys `AE, BE, CE, DE`; highest NF = 3NF.**
All attributes are prime (3NF), but `A → B` has a non-super-key left side (not BCNF).

### F13. [GATE-pattern] Instance can disprove FDs

| A | B | C |
| --- | --- | --- |
| 1 | x | p |
| 1 | y | p |
| 2 | x | q |

Which FDs are **definitely violated**?

**Answer: `A → B` (rows 1, 2) and `B → C` (rows 1, 3).** `A → C` and `C → A` are not violated by this instance, but the instance cannot prove they hold.

### F14. [GATE-pattern] Lossless test

`R(A,B,C,D,E)`, `F = {A→BC, CD→E}`. Is decomposing into `R1(A,B,C)` and `R2(A,D,E)` lossless?

**Answer: Yes** — `R1 ∩ R2 = A`, and `A → ABC = R1`.
Dependency preserving? **No** — `CD → E` cannot be checked in either part.

---

## G. File Organization and Indexing

### G1. [GATE 2004] Order of a B+ tree internal node

Child pointer = 6 B, key = 14 B, block = 512 B. Order (max children)?

**Answer: 26** — `6p + 14(p − 1) ≤ 512` → `20p ≤ 526` → `p = 26`.

### G2. [GATE 2007] Order of a B+ tree leaf

Block = 1 KB, record pointer = 7 B, key = 9 B, block pointer = 6 B. Max (key, record pointer) pairs in a leaf?

**Answer: 63** — `n(9 + 7) + 6 ≤ 1024` → `16n ≤ 1018` → `n = 63`.

### G3. [GATE 2015] Keys in a non-leaf node

Key = 12 B, block = 1024 B, record pointer = 10 B, block pointer = 8 B. Max keys in a non-leaf node?

**Answer: 50** — `8n + 12(n − 1) ≤ 1024` → `n = 51` children → **50 keys**.

### G4. [GATE 2017] Maximum order

Key = 8 B, block = 512 B, block pointer = 2 B.

**Answer: 52** — `2p + 8(p − 1) ≤ 512` → `10p ≤ 520` → `p = 52`.

### G5. [GATE 2020] Disk accesses for a million records

Block = 4 KB, key = 12 B, pointer = 8 B, 1,000,000 records, each record in its own block, nothing cached.
Minimum disk accesses to retrieve a record?

**Answer: 4**

- Internal order 205, leaf capacity 204 → 4902 leaves.
- Internal levels: 4902 → 24 → 1 → **2** internal levels.
- 2 internal + 1 leaf + 1 data block = **4**.

### G6. [GATE 2008] Multilevel secondary index

16,384 records of 32 B, key 6 B, block 1024 B, block pointer 10 B, file ordered on a non-key field, unspanned.
Secondary index on the key field, multilevel. First- and second-level index blocks?

**Answer: 256 and 4**

- Entry = 16 B → 64 entries per block.
- Dense: 16,384 / 64 = **256** first-level blocks.
- 256 / 64 = **4** second-level blocks.

### G7. [GATE 2008] Clustering index field type

A clustering index is defined on fields of which type?

**Answer: non-key and ordering** (ordering key → primary index; non-ordering → secondary index).

### G8. [GATE 2013] Definition of a clustered index

**Answer: An index is clustered if the data records are stored in the same order as the index entries (search key order).**

### G9. [GATE-pattern] Primary index cost

30,000 records, record 100 B, block 1024 B (unspanned), primary key 9 B, block pointer 6 B.
Block accesses with a single-level primary index vs. binary search on the data file?

**Answer: 7 with the index; 12 without.**

- `bfr = ⌊1024/100⌋ = 10` → data blocks `b = 3000`.
- Binary search on data: `⌈log₂ 3000⌉ = 12`.
- Index entries = 3000 (sparse, one per block); entry = 15 B → `⌊1024/15⌋ = 68` per block → `⌈3000/68⌉ = 45` index blocks.
- Cost = `⌈log₂ 45⌉ + 1 = 6 + 1 = 7`.

### G10. [GATE-pattern] Minimum keys in a B tree

B tree of order 5 (max 5 children) with 3 levels. Minimum number of keys?

**Answer: 17** — `2⌈5/2⌉^(3−1) − 1 = 2·9 − 1 = 17`.

### G11. [GATE-pattern] B+ tree insertion split

B+ tree with leaf capacity 3 keys. A leaf holds `[10, 20, 30]`; insert 25. What is copied to the parent?

**Answer: 25**
Leaf becomes `[10, 20, 25, 30]` → split into `[10, 20]` and `[25, 30]` → **copy** 25 up (the right half's first key).

---

## H. Transactions and Concurrency Control

### H1. [GATE 2015] Which ACID property?

Transfer: `read(x); x := x − 50; write(x); read(y); y := y + 50; write(y)`. The rule "x + y stays constant" is which property?

**Answer: Consistency.**

### H2. [GATE 2014] Which schedule is conflict serializable?

1. `r1(x) r2(x) w1(x) r3(x) w2(x)`
2. `r2(x) r1(x) w2(x) r3(x) w1(x)`
3. `r3(x) r2(x) r1(x) w2(x) w1(x)`
4. `r2(x) w2(x) r3(x) r1(x) w1(x)`

**Answer: Schedule 4.**

- 1: `r1 … w2` gives T1→T2 and `r2 … w1` gives T2→T1 → cycle.
- 2 and 3: same T1 ↔ T2 cycle.
- 4: edges `T2→T3, T2→T1, T3→T1` → acyclic, serial order **T2, T3, T1**.

### H3. [GATE 2012] Interleaving two dependent transactions

P = Q = 0 initially.

```text
T1: read(P); read(Q); if P = 0 then Q := Q + 1; write(Q)
T2: read(Q); read(P); if Q = 0 then P := P + 1; write(P)
```

Any non-serial interleaving leads to which kind of schedule?

**Answer: a schedule that is not conflict serializable.**

In any interleaving, T1 reads P before T2 writes P (T1→T2) and T2 reads Q before T1 writes Q (T2→T1) → cycle.

### H4. [GATE 2016] Ordered exclusive locking

T acquires exclusive locks on all objects it needs in increasing address order, performs its operations, then releases all locks.

**Answer: guarantees serializability and freedom from deadlock.**
All locks are held before any release (2PL → serializable); a global lock order prevents circular wait (no deadlock).

### H5. [GATE 2010] Serializability and deadlock freedom

Which protocols guarantee both conflict serializability and deadlock freedom? I. 2PL  II. Timestamp ordering

**Answer: II only.** 2PL can deadlock; timestamp ordering never makes a transaction wait.

### H6. [GATE 2019] Strict 2PL and Thomas write rule

- I: Strict 2PL generates conflict-serializable schedules that are also recoverable.
- II: Timestamp ordering with Thomas write rule can generate view-serializable schedules that are not conflict serializable.

**Answer: Both true.**

### H7. [GATE 2003] Irrecoverable scenario

Which situation can make a schedule irrecoverable?

**Answer: A transaction reads a data item written by an uncommitted transaction (and commits before that writer).**

### H8. [GATE 2006] Log-based recovery

Account B starts at 12,000. Log:

```text
1. <T1 start>
2. <T1, B, 12000, 10000>
3. <T1, M, 0, 2000>
4. <T1 commit>
5. <T2 start>
6. <T2, B, 10000, 10500>
7. <T2 commit>     ← crash happens before this is written
```

**Answer: Undo record 6 (set B back to 10,000) and redo records 2 and 3.** T1 committed → redo; T2 did not → undo.

### H9. [GATE-pattern] Conflict serializability with 3 transactions

`r1(X) r2(Z) r1(Z) r3(X) r3(Y) w1(X) w3(Y) r2(Y) w2(Z) w2(Y)`

**Answer: Conflict serializable, order T3 → T1 → T2.**

- `r3(X) … w1(X)` → T3→T1.
- `r1(Z) … w2(Z)` → T1→T2.
- `w3(Y) … r2(Y)`, `w3(Y) … w2(Y)`, `r3(Y) … w2(Y)` → T3→T2.
- Acyclic → topological order T3, T1, T2.

### H10. [GATE-pattern] View serializable but not conflict serializable

`r1(X) w2(X) w1(X) w3(X)`

**Answer: View serializable (≡ T1, T2, T3), not conflict serializable.**

- Conflict edges: `r1 → w2` (T1→T2), `w2 → w1` (T2→T1) → cycle.
- View: T1 reads initial X; final write by T3 in both; no other reads → same as serial T1 T2 T3.
- Blind writes `w2(X)` and `w3(X)` make this possible.

### H11. [GATE-pattern] Count schedules

T1 has 2 operations and T2 has 3 operations. How many schedules? How many serial?

**Answer: 10 schedules, 2 serial** — `5! / (2! · 3!) = 10`; serial = `2! = 2`.

### H12. [GATE-pattern] Recoverable vs cascadeless

`w1(X) r2(X) c1 c2` — classify.

**Answer: Recoverable but not cascadeless.**
T2 reads uncommitted X from T1 (not cascadeless), but T1 commits before T2 (recoverable).
If the order were `w1(X) r2(X) c2 c1`, it would be **irrecoverable**.

### H13. [GATE-pattern] Wait-die vs wound-wait

TS(T1) = 5 (older), TS(T2) = 10 (younger).

| Situation | Wait-die | Wound-wait |
| --- | --- | --- |
| T1 requests item held by T2 | T1 **waits** | T2 is **wounded** (rolled back) |
| T2 requests item held by T1 | T2 **dies** (rolled back) | T2 **waits** |

### H14. [GATE-pattern] Timestamp ordering decision

TS(T1) = 10, TS(T2) = 20. Schedule `r1(X) w2(X) w1(X)`. With basic TO, what happens at `w1(X)`?
With Thomas write rule?

**Answer: Basic TO aborts T1; Thomas write rule ignores `w1(X)` and continues.**
At `w1(X)`: `WTS(X) = 20 > TS(T1) = 10` and `RTS(X) = 10` is not greater than TS(T1), so the write is obsolete.

### H15. [GATE-pattern] 2PL classification

```text
T1: lock-X(A) read(A) lock-X(B) unlock(A) write(B) unlock(B)
```

**Answer: Follows basic 2PL (all locks before the first unlock), but not strict 2PL** (X lock on A released before commit).

### H16. [GATE-pattern] Deadlock under 2PL

```text
T1: lock-X(A) …           lock-X(B)
T2:          lock-X(B) …           lock-X(A)
```

**Answer: Deadlock** — T1 waits for T2 on B and T2 waits for T1 on A (cycle in wait-for graph). 2PL does not prevent this.
