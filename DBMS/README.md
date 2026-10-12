# DBMS for GATE CSE — Complete Study Notes

## Official Syllabus (Section 9: Databases)

> ER-model. Relational model: relational algebra, tuple calculus, SQL. Integrity constraints, normal forms.
> File organization, indexing (e.g., B and B+ trees). Transactions and concurrency control.

## Study Order

Read the files in this order. Each later topic uses ideas from the earlier ones.

| # | File | Syllabus item | GATE weight (typical) |
| --- | --- | --- | --- |
| 1 | [ER Model](./01-er-model.md) | ER-model | Low (0–2 marks) |
| 2 | [Relational Model & Relational Algebra](./02-relational-model-and-algebra.md) | Relational model, relational algebra | Medium (1–3 marks) |
| 3 | [Tuple (and Domain) Relational Calculus](./03-relational-calculus.md) | Tuple calculus | Low (0–2 marks) |
| 4 | [SQL](./04-sql.md) | SQL | High (2–4 marks) |
| 5 | [Integrity Constraints & Keys](./05-integrity-constraints-and-keys.md) | Integrity constraints | Low–Medium |
| 6 | [Functional Dependencies & Normal Forms](./06-functional-dependencies-and-normalization.md) | Normal forms | High (2–4 marks) |
| 7 | [File Organization & Indexing (B / B+ trees)](./07-file-organization-and-indexing.md) | File organization, indexing | Medium–High (2–3 marks) |
| 8 | [Transactions & Concurrency Control](./08-transactions-and-concurrency-control.md) | Transactions and concurrency control | High (2–4 marks) |
| 9 | [Solved PYQs (topic-wise)](./09-solved-pyqs.md) | All topics | Practice |
| 10 | [Revision & Formula Sheet](./10-revision-formula-sheet.md) | All topics | Last-week revision |
| 11 | [Full PYQ Bank — 315 solved questions](./pyqs/README.md) | All topics | Topic-wise practice |

DBMS usually carries about **7–9 marks** in GATE CSE.

## Syllabus Checklist

- [ ] ER model: entities, attributes, relationships, cardinality, participation, weak entities, ER → tables
- [ ] Relational model: relation, tuple, schema, keys, NULLs
- [ ] Relational algebra: σ, π, ×, ∪, −, ρ, ⋈, θ-join, outer joins, ÷, query equivalences, tuple-count bounds
- [ ] Tuple relational calculus: syntax, ∃ / ∀, safe expressions, equivalence with RA
- [ ] SQL: DDL, DML, joins, NULL logic, aggregation, GROUP BY / HAVING, nested and correlated queries, set ops, views
- [ ] Integrity constraints: domain, key, entity, referential (ON DELETE CASCADE / SET NULL), CHECK, assertions
- [ ] FDs: Armstrong's axioms, closure, candidate keys, minimal cover, equivalence
- [ ] Normal forms: 1NF, 2NF, 3NF, BCNF, (4NF/MVD awareness), lossless join, dependency preservation, decomposition algorithms
- [ ] File organization: heap, sorted, hashing, blocking factor, spanned vs unspanned
- [ ] Indexing: primary, clustering, secondary, dense vs sparse, multilevel index
- [ ] B tree and B+ tree: order, node capacity, height, insertion/deletion, number of disk accesses
- [ ] Transactions: ACID, states, schedules, conflict & view serializability, recoverable / cascadeless / strict
- [ ] Concurrency control: locks, 2PL variants, deadlock prevention (wait-die / wound-wait), timestamp ordering, Thomas write rule
- [ ] Solve all PYQs in [09-solved-pyqs.md](./09-solved-pyqs.md) without looking at the solutions first
- [ ] Work through the full [PYQ bank](./pyqs/README.md) topic by topic

## About the PYQ Bank

The PYQ file contains GATE previous year questions rewritten in our own words and fully solved, grouped
by topic. A year tag is shown only where the source year is well known; otherwise the question is marked
**GATE-pattern**. Numerical answers were re-checked with small scripts (closure, serializability, B+ tree
arithmetic and SQL execution in SQLite).

The bank covers the frequently repeated GATE question types across the full syllabus. It is not claimed
to be an exact copy of every DBMS question ever asked; for that, also practise the official papers
published by the GATE organising IITs.
