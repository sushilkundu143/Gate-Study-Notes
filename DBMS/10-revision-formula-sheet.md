# 10. DBMS Revision and Formula Sheet

One page to read in the last week before GATE.

## ER Model

- Strong / weak entity → 1 table each; weak key = owner key + discriminator.
- M:N relationship → own table. 1:N → FK on the N side. 1:1 → FK on either side.
- Multivalued attribute → own table.
- 1:1 with total participation on both sides → merge into one table.

## Relational Algebra

- Complete set: `σ, π, ∪, −, ×, ρ`.
- `R ∩ S = R − (R − S)`; `R ⋈_θ S = σ_θ(R × S)`.
- `R ÷ S = π_A(R) − π_A((π_A(R) × S) − R)` → "for all" queries.
- Natural join with no common attribute = Cartesian product.
- Join on a key of S: `|R ⋈ S| ≤ |R|`.
- FK `r.B → s.C`: `π_B(r) − π_C(s) = ∅`.

## Calculus

- `∀ t ∈ R (P) ≡ ¬∃ t ∈ R (¬P)`.
- RA ≡ safe TRC ≡ safe DRC.

## SQL

- Order: `FROM → WHERE → GROUP BY → HAVING → SELECT → DISTINCT → ORDER BY`.
- Aggregates ignore NULL; `COUNT(*)` doesn't.
- `x = NULL` → UNKNOWN; use `IS NULL`.
- `NOT IN` list with a NULL → no rows.
- `> ALL (∅)` = TRUE; `> ANY (∅)` = FALSE.
- `UNION` removes duplicates; `UNION ALL` keeps them.
- Double `NOT EXISTS` = division.

## Keys and Constraints

- Super keys with a single candidate key of size k in n attributes: `2^(n−k)`.
- Delete from parent / insert into child can violate referential integrity.
- CASCADE deletes recursively.

## FDs and Normal Forms

- Attributes never on any RHS are in every key.
- 2NF: no non-prime attribute depends on a proper subset of a key.
- 3NF: for each `X → A`, X super key **or** A prime.
- BCNF: for each `X → A`, X super key.
- Binary decomposition lossless ⇔ `R1 ∩ R2 → R1` or `R1 ∩ R2 → R2`.
- Lossy join gives **extra** tuples.
- BCNF: lossless, maybe not dependency preserving. 3NF synthesis: both.
- Every 2-attribute relation is in BCNF.

## File Organization and Indexing

- `bfr = ⌊B / R⌋`; `blocks = ⌈r / bfr⌉`.
- Binary search on b blocks: `⌈log₂ b⌉`.
- Primary index: sparse, entries = data blocks. Clustering: entries = distinct values. Secondary on key: dense, entries = records.
- B+ internal: `p·P + (p − 1)·K ≤ B`.
- B+ leaf: `n·(K + Pr) + P ≤ B`.
- B tree node: `p·P + (p − 1)(K + Pr) ≤ B`.
- Record fetch via B+ tree = levels + 1.
- B tree min keys with L levels: `2⌈p/2⌉^(L−1) − 1`; max keys: `p^L − 1`.

## Transactions

- Conflict: different transactions, same item, at least one write.
- Precedence graph acyclic ⇔ conflict serializable.
- View serializable but not conflict serializable ⇒ blind write exists.
- Strict ⊂ cascadeless ⊂ recoverable.
- Schedules count: `(Σnᵢ)! / Π(nᵢ!)`; serial: `n!`.
- 2PL → conflict serializable, can deadlock. Strict 2PL → also strict schedules. Conservative 2PL → deadlock-free.
- Wait-die: old waits, young dies. Wound-wait: old wounds young, young waits.
- TO: read aborts if `TS < WTS`; write aborts if `TS < RTS` or `TS < WTS` (Thomas: ignore when only `TS < WTS`).
- TO is deadlock-free; Thomas write rule allows view-serializable, non-conflict-serializable schedules.
