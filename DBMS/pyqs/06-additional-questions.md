# PYQs — Additional Questions (GFG Set pages, not in topic quizzes)

[← All PYQ topics](./README.md) · [DBMS notes](../README.md)

**3 questions** (3 from GATE papers). Try each question before opening its solution.

## Quick Answer Key

| Q | Source | Answer |
| --- | --- | --- |
| [Q1](#q1) | GATE CS 2010 | (A) 100 |
| [Q2](#q2) | GATE CS 2006 | (C) For `x = 5000`, Plan 1 executes faster than Plan 2 for all data… |
| [Q3](#q3) | GATE CS 2006 | (C) and (D) are both false; the question has two false options. |

---

## Questions and Solutions

<a id="q1"></a>

### Q1. [GATE CS 2010] Maximum size of a natural join
Consider relations `R(A, B, C)` and `S(B, D, E)` with functional dependencies `B → A` and `A → C`. Relation `R` contains 200 tuples and relation `S` contains 100 tuples. What is the maximum number of tuples possible in the natural join `R ⋈ S`?

- (A) 100
- (B) 200
- (D) 300
- (D) 2000

**Answer: (A) 100**

**Solution:** In `R`, `B → A` and `A → C`, so `B → A C`; therefore each `B` value occurs at most once in `R`. The natural join matches tuples on `B`. Each of the 100 tuples of `S` can match at most one `R` tuple, so the join has at most 100 tuples. This maximum is attainable by making every `S.B` value match a value in `R`. Hence 200, 300, and 2000 are impossible. (The two `(D)` labels are reproduced as shown in the input.)

<a id="q2"></a>

### Q2. [GATE CS 2006] Query plans for enrolled and paid relations
Let `enrolled(student, course)` have primary key `(student, course)`, and let `paid(student, amount)` have primary key `student`. Assume no nulls, foreign keys, or other integrity constraints. Each of the amounts 6000, 7000, 8000, 9000, and 10000 was paid by 20% of the students. Consider these query plans for listing all courses taken by students who have paid more than `x`:

**Plan 1**

1. Probe an index on `enrolled.student`.
2. Sequentially scan `paid` and select rows with `amount > x`.
3. Use an indexed nested-loop join.
4. Project on `course`.

**Plan 2**

1. Probe an index on `enrolled.student`.
2. Sequentially scan `paid`.
3. Use an indexed nested-loop join.
4. Select joined rows with `amount > x`.
5. Project on `course`.

A disk seek takes 4 ms, disk data-transfer bandwidth is 300 MB/s, and checking a tuple to test `amount > x` takes 10 microseconds. Which statement is correct?

- (A) Plan 1 and Plan 2 will not output identical row sets for all databases.
- (B) A course may be listed more than once in the output of Plan 1 for some databases.
- (C) For `x = 5000`, Plan 1 executes faster than Plan 2 for all databases.
- (D) For `x = 9000`, Plan 1 executes slower than Plan 2 for all databases.

**Answer: (C) For `x = 5000`, Plan 1 executes faster than Plan 2 for all databases.**

**Solution:** The two plans apply the same `amount > x` condition to the same joined students, so moving the selection before the join does not change the qualifying course rows; (A) is false. In relational algebra, projection is set-valued, so a course is not listed multiple times; (B) is false. At `x = 5000`, all five possible payment amounts qualify. Plan 1 tests each paid tuple before the join, while Plan 2 tests the amount on joined rows, potentially repeating the comparison for a student taking several courses. Pushing the selection down avoids those repeated checks, so (C) is the intended answer. At `x = 9000`, only the 10000 amount qualifies; filtering before the join can reduce the number of index probes, not make Plan 1 slower in every database, so (D) is false. The strict “for all databases” wording presumes the intended cost comparison in which the later selection is evaluated for joined course rows; the stated constraints do not separately specify enrollment counts.

<a id="q3"></a>

### Q3. [GATE CS 2006] Check functional-dependency closures
The following functional dependencies hold:

```text
AB → CD
AF → D
DE → F
C → G
F → E
G → A
```

Which option is false?

- (A) `CF+ = {A, C, D, E, F, G}`
- (B) `BG+ = {A, B, C, D, G}`
- (C) `AF+ = {A, C, D, E, F, G}`
- (D) `AB+ = {A, B, C, D, F, G}`

**Answer: (C) and (D) are both false; the question has two false options.**

**Solution:**

- `CF+`: `C → G → A`, `F → E`, and `AF → D`, giving `{A,C,D,E,F,G}`. So (A) is true.
- `BG+`: `G → A`, then `AB → CD`, giving `{A,B,C,D,G}`. So (B) is true.
- `AF+`: `AF → D`, `F → E`; no rule derives `C` or `G`. Thus `AF+ = {A,D,E,F}`, so (C) is false.
- `AB+`: `AB → CD`, `C → G`, and `G → A`; no rule derives `E` or `F`. Thus `AB+ = {A,B,C,D,G}`, so (D) is also false.

> Note: GFG marks (C), but (D) is also false under the stated dependencies because `AB+` does not contain `F`.
