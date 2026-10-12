# DBMS PYQ Bank (Fully Solved)

Every DBMS question from the GeeksforGeeks
[DBMS GATE previous year questions](https://www.geeksforgeeks.org/dbms/database-management-system-gate-questions/)
collection — the five topic quizzes and the "Set 1–10" pages — rewritten and solved step by step.

**Total: 315 questions** (151 from actual GATE CS/IT papers).

| Topic | Questions | From GATE papers |
| --- | --- | --- |
| [ER Model, Relational Model, Relational Algebra & Calculus](./01-er-and-relational-model.md) | 74 | 27 |
| [Functional Dependencies & Normal Forms](./02-functional-dependencies-and-normal-forms.md) | 88 | 47 |
| [SQL](./03-sql.md) | 66 | 38 |
| [Transactions & Concurrency Control](./04-transactions-and-concurrency-control.md) | 48 | 24 |
| [File Organization, Indexing, B & B+ Trees](./05-file-organization-and-indexing.md) | 36 | 12 |
| [Additional Questions (GFG Set pages, not in topic quizzes)](./06-additional-questions.md) | 3 | 3 |

## How to Read This

- Each file starts with a **quick answer key**; each question then has the full problem, the answer and a step-by-step solution.
- Source tags: `GATE CS 2012`, `GATE IT 2005`, etc. are real GATE questions. The GFG collection also includes
  `UGC-NET`, `ISRO`, `GATE CS Mock` and `GFG practice` questions — useful practice, but not GATE PYQs.
- Answers were solved independently and compared with GFG's marked answer. Where they differ, or where the official
  GATE key is disputed, the solution has a **Note** explaining why. Numeric, FD and SQL answers were checked with scripts.
- Duplicate questions that appeared both in a quiz and on a Set page are included only once.
- Questions originally shown as images were transcribed into tables/text.

## Known Answer-Key Disputes Worth Remembering

| Question | Official / GFG answer | Why it is disputed |
| --- | --- | --- |
| GATE CS 2012 — HAVING / GROUP BY | (C) Q and R | Standard SQL allows HAVING without GROUP BY, so P and S (B) are technically true |
| GATE CS 2009 — nested NOT IN supplier query | (A) | The query actually returns suppliers with no blue part; no option is exact |
| GATE CS 2006 — FD closures | (C) | `AB+` lacks F, so (D) is also false |
| GATE CS 2001 — unsafe TRC expression | (C) | (B) can also be unsafe when the implication is vacuous |
