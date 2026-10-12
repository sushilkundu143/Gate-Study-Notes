# 6. Functional Dependencies and Normal Forms

Normalization removes **redundancy** and the insert/update/delete anomalies it causes.

## 6.1 Functional Dependency (FD)

`X → Y` means: if two tuples agree on X, they must agree on Y.

- **Trivial FD**: `Y ⊆ X` (e.g. `AB → A`).
- A table **instance** can only *disprove* an FD (find two rows with same X, different Y); it can never prove one holds for the schema.

### Armstrong's Axioms (sound and complete)

1. **Reflexivity**: if `Y ⊆ X` then `X → Y`.
2. **Augmentation**: if `X → Y` then `XZ → YZ`.
3. **Transitivity**: if `X → Y` and `Y → Z` then `X → Z`.

Derived rules: **Union** (`X→Y, X→Z ⇒ X→YZ`), **Decomposition** (`X→YZ ⇒ X→Y`), **Pseudo-transitivity** (`X→Y, WY→Z ⇒ WX→Z`).

> Not valid: `XY → Z` does **not** imply `X → Z`.

## 6.2 Attribute Closure `X⁺`

Start with `X`; repeatedly add the right side of any FD whose left side is already inside.

Example: `R(A,B,C,D,E)`, `F = {A→B, B→C, CD→E}`

```text
(AD)+ = AD → ABD (A→B) → ABCD (B→C) → ABCDE (CD→E)  ⇒ AD is a super key
```

Uses: test `X → Y` (is `Y ⊆ X⁺`?), find keys, test equivalence of FD sets.

## 6.3 Finding All Candidate Keys (Exam Method)

1. Attributes that **never appear on any right side** must be in **every** key. Call this set `Core`.
2. Attributes appearing **only on right sides** are never in any key.
3. Compute `Core⁺`. If it is all attributes, `Core` is the only key.
4. Otherwise add the remaining "both-side" attributes one at a time, then pairs, … ; keep only minimal ones.

Example (`R(A,B,C,D,E,H)`, `A→B, BC→D, E→C, D→A`):

- Never on right: `E, H` → Core = `EH`; `(EH)+ = EHC` (not all).
- Try `EH + A`: `AEH → ABCDEH` ✓; `EH + B`: `BEH → BCDEAH` ✓; `EH + D`: `DEH → DAEBCH` ✓; `EH + C` → `CEH` only ✗.
- Candidate keys: **AEH, BEH, DEH**.

Shortcut: if `X` is a key and some FD `Y → Z` with `Z ∩ X ≠ ∅`, then replacing that part of X with Y may give another key.

## 6.4 Equivalence and Minimal (Canonical) Cover

`F` and `G` are **equivalent** if each covers the other (every FD in F follows from G and vice versa).

**Minimal cover algorithm**

1. Split right sides to single attributes (`A → BC` ⇒ `A→B`, `A→C`).
2. Remove **extraneous left-side attributes**: in `XA → B`, A is extraneous if `B ∈ X⁺`.
3. Remove **redundant FDs**: drop `X → A` if `A ∈ X⁺` computed with the remaining FDs.

Example: `{V→W, VW→X, Y→VX, Y→Z}`

1. Split: `V→W, VW→X, Y→V, Y→X, Y→Z`.
2. `VW→X`: `V⁺ ⊇ W`, so W is extraneous → `V→X`.
3. `Y→X` is redundant (`Y→V→X`).

Minimal cover: **`V→W, V→X, Y→V, Y→Z`**.

## 6.5 Decomposition Properties

### Lossless join

Decomposition of `R` into `R1`, `R2` is lossless **iff** `R1 ∩ R2 → R1` or `R1 ∩ R2 → R2` (common attributes form a key of at least one part).

- Lossy decomposition produces **extra (spurious)** tuples: `r ⊂ π_R1(r) ⋈ π_R2(r)`. Never fewer.
- For more than two parts, use the **chase / tableau** test or repeatedly apply the binary test.

### Dependency preservation

Decomposition preserves dependencies if `(F1 ∪ F2 ∪ …)⁺ = F⁺`, where `Fi` is the projection of `F⁺` on `Ri`.
Quick check: every FD in F can be checked inside a single part, or derived from the FDs that can.

| | Lossless | Dependency preserving |
| --- | --- | --- |
| 3NF synthesis | Always | Always |
| BCNF decomposition | Always | **Not always** |

## 6.6 Normal Forms

Let **prime attribute** = part of some candidate key.

| NF | Condition | Removes |
| --- | --- | --- |
| 1NF | All values atomic (no repeating groups / multivalued cells) | Non-atomic values |
| 2NF | 1NF + no **partial dependency**: no non-prime attribute depends on a **proper subset** of a candidate key | Partial dependencies |
| 3NF | For every non-trivial `X → A`: **X is a super key OR A is prime** | Transitive dependencies |
| BCNF | For every non-trivial `X → A`: **X is a super key** | All non-key determinants |
| 4NF | For every non-trivial MVD `X ↠ Y`: X is a super key | Multivalued dependencies |
| 5NF | Every join dependency is implied by candidate keys | Join dependencies |

Hierarchy: `5NF ⊂ 4NF ⊂ BCNF ⊂ 3NF ⊂ 2NF ⊂ 1NF`.

### How to find the highest normal form

1. Find all candidate keys and prime attributes.
2. For each non-trivial FD `X → A`:
   - X super key → fine for all.
   - Else if A prime → violates BCNF only (still 3NF).
   - Else if X is a proper subset of a candidate key → violates **2NF**.
   - Else → violates **3NF** (transitive).
3. The relation is in the highest NF that no FD violates.

Facts worth memorizing:

- Every **two-attribute** relation is in BCNF.
- If every candidate key is a **single attribute**, the relation is automatically in 2NF.
- If all attributes are prime, the relation is automatically in 3NF.
- 3NF but not BCNF ⇒ some `X → A` with X not a super key and A prime (needs overlapping composite keys).

## 6.7 Decomposition Algorithms

### BCNF decomposition

```text
while some Ri is not in BCNF:
    pick violating X → Y in Ri
    replace Ri by (X ∪ Y) and (Ri − Y)
```

Always lossless; may lose dependencies.

### 3NF synthesis

1. Find minimal cover `Fc`.
2. For each `X → A` in `Fc` make a relation `XA` (group FDs with same left side).
3. If no relation contains a candidate key, add one relation that is a key.
4. Remove relations contained in others.

Always lossless and dependency preserving.

## 6.8 Multivalued Dependency (Awareness Level)

`X ↠ Y`: for a given X, the set of Y values is independent of the remaining attributes.
Example: `Emp ↠ Skill` and `Emp ↠ Language` in `Emp(emp, skill, language)` → decompose to `(emp, skill)` and `(emp, language)` for 4NF.
Every FD is also an MVD (`X → Y ⇒ X ↠ Y`).

## 6.9 Common Traps

1. Find **all** candidate keys before judging prime attributes.
2. `AB → C` with key `AB` is fine; `A → C` with key `AB` is partial (2NF violation) only if C is **non-prime**.
3. BCNF decomposition is lossless but may lose dependencies; 3NF can keep both.
4. A lossy join gives **more** tuples, not fewer.
5. Check FDs after projection on a decomposed relation using **F⁺**, not only the listed FDs.
