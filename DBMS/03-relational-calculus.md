# 3. Tuple Relational Calculus (TRC) and Domain Relational Calculus (DRC)

Relational calculus is **declarative**: you describe *what* rows you want, not how to compute them.

## 3.1 TRC Syntax

```text
{ t | P(t) }        "the set of all tuples t for which predicate P is true"
```

Building blocks of `P`:

| Piece | Example | Meaning |
| --- | --- | --- |
| Membership | `t ∈ Student` | t is a row of Student |
| Comparison | `t.age > 20`, `t.id = s.id` | Compare attribute values |
| Connectives | `∧`, `∨`, `¬`, `⇒` | and, or, not, implies |
| Existential | `∃ s ∈ R (P(s))` | At least one s in R satisfies P |
| Universal | `∀ s ∈ R (P(s))` | Every s in R satisfies P |

Useful identities:

```text
∀ t ∈ R (P(t))   ≡   ¬∃ t ∈ R (¬P(t))
P ⇒ Q            ≡   ¬P ∨ Q
```

## 3.2 Worked TRC Examples

Schema: `Student(sid, name)`, `Course(cid)`, `Enroll(sid, cid)`.

**Names of students enrolled in some course**

```text
{ t | ∃ s ∈ Student ( t.name = s.name ∧ ∃ e ∈ Enroll (e.sid = s.sid) ) }
```

**Students not enrolled in any course**

```text
{ s | s ∈ Student ∧ ¬∃ e ∈ Enroll (e.sid = s.sid) }
```

**Students enrolled in all courses** (division)

```text
{ s | s ∈ Student ∧ ∀ c ∈ Course ( ∃ e ∈ Enroll (e.sid = s.sid ∧ e.cid = c.cid) ) }
```

## 3.3 Safe Expressions

An expression is **safe** if its result is guaranteed to be finite and only contains values from the database.

- Unsafe: `{ t | ¬(t ∈ Student) }` — infinitely many tuples are "not students".
- Rule of thumb: every free tuple variable must be tied to some relation by a positive membership condition.

## 3.4 Domain Relational Calculus (DRC)

Variables range over **attribute values** (domains) instead of whole tuples.

```text
{ <n> | ∃ s ( <s, n> ∈ Student ∧ ∃ c ( <s, c> ∈ Enroll ) ) }
```

## 3.5 Expressive Power (Codd's Theorem)

```text
Relational Algebra  ≡  Safe TRC  ≡  Safe DRC
```

- Basic SQL (without aggregates, recursion, ordering) can be expressed in these.
- Unsafe TRC/DRC is **more** expressive than RA (but produces infinite answers, so is not useful).
- RA/TRC cannot express aggregation (`COUNT`, `SUM`) or transitive closure (recursion).

## 3.6 Common Traps

1. `¬∃ t ∈ R (P(t))` means **no** tuple satisfies P; it is **not** `∀ t ∈ R (P(t))`.
2. `∃ t ∉ R` style expressions are usually unsafe.
3. `∀ c ∈ Course (...)` is true **vacuously** if Course is empty.
4. Read nested quantifiers from outside to inside, and translate `∀` to "for every", `∃` to "there is some".
