# PYQs — ER Model, Relational Model, Relational Algebra & Calculus

[← All PYQ topics](./README.md) · [DBMS notes](../README.md)

**74 questions** (27 from GATE papers). Try each question before opening its solution.

## Quick Answer Key

| Q | Source | Answer |
| --- | --- | --- |
| [Q1](#q1) | GATE CS 2012 | (C) In a row of a relational table, an attribute can have more than… |
| [Q2](#q2) | GATE CS 2012 | (A) `π_B(r1) − π_C(r2) = ∅` |
| [Q3](#q3) | GATE CS 2012 | (A) 7 |
| [Q4](#q4) | GATE CS 2011 | (C) Hashing outperforms ordered indexing on Q1, but not on Q2. |
| [Q5](#q5) | GFG practice | (B) `GRANT` and `REVOKE` |
| [Q6](#q6) | GFG practice | (B) `D1 × D2 × … × Dn` |
| [Q7](#q7) | GFG practice | (A) A Cartesian product of two relations followed by a selection. |
| [Q8](#q8) | GFG practice | (D) `UPDATE` |
| [Q9](#q9) | GFG practice | (C) Owner entity set |
| [Q10](#q10) | GFG practice | (C) (d) |
| [Q11](#q11) | GFG practice | (D) `ABD` |
| [Q12](#q12) | GFG practice | (A) To allow duplicate tuples by filling the primary-key column(s) … |
| [Q13](#q13) | GFG practice | (C) II only |
| [Q14](#q14) | GFG practice | (C) II and III only |
| [Q15](#q15) | GFG practice | (B) III and IV only |
| [Q16](#q16) | GFG practice | (D) `3, 4, 1` respectively |
| [Q17](#q17) | GFG practice | (B) `A → B` and `A ↠ C` |
| [Q18](#q18) | GFG practice | (B) A small open diamond at the end of a line connecting two tables |
| [Q19](#q19) | GFG practice | (A) I only |
| [Q20](#q20) | GFG practice | (D) (a), (b), and (c) |
| [Q21](#q21) | GFG practice | (A) Reduce the number of joins needed to satisfy a query. |
| [Q22](#q22) | GATE CS 2022 | (A) A relation with only two attributes is always in BCNF. |
| [Q23](#q23) | GFG practice | (D) (d) and (a) |
| [Q24](#q24) | GATE CS 2013 | (A) I, II, III, and IV |
| [Q25](#q25) | GFG practice | (D) Normal forms |
| [Q26](#q26) | GFG practice | (D) Tuples in a weak entity set are not partitioned according to th… |
| [Q27](#q27) | GFG practice | (B) Transitivity, augmentation, and reflexivity |
| [Q28](#q28) | GFG practice | (C) (a) and (c) |
| [Q29](#q29) | GFG practice | (A) Project |
| [Q30](#q30) | GFG practice | (B) Subschema |
| [Q31](#q31) | GFG practice | (A) The `Person`–`Animal` association labelled `pet`, with `0…*` at… |
| [Q32](#q32) | GFG practice | (D) Adding suitable attributes |
| [Q33](#q33) | GFG practice | (B) If `Y` is deleted, then `X` is also deleted. |
| [Q34](#q34) | GFG practice | (C) The sum of all employees' salaries |
| [Q35](#q35) | GATE CS 2020 | (A) Diamonds with double/bold border |
| [Q36](#q36) | GFG practice | (A) `Pk(r1) → Pk(r2)` |
| [Q37](#q37) | GFG practice | (A) Inner join |
| [Q38](#q38) | ISRO CS 2018 | (B) Logical data independence |
| [Q39](#q39) | UGC NET CS 2014 Dec-II | (B) `AE` |
| [Q40](#q40) | GATE CS 2014 Set 3 | (D) All of his/her dependents |
| [Q41](#q41) | GATE CS 1999 | (C) `σ_(A=10)(r) ∩ σ_(B=20)(r)` |
| [Q42](#q42) | GATE CS 1999 | (B) `mn` and `0` |
| [Q43](#q43) | GATE CS Mock 2017 | (C) Minimum 2, maximum 3 |
| [Q44](#q44) | GATE CS Mock 2017 | (C) 3 |
| [Q45](#q45) | GATE IT 2006 | (D) I, II and III |
| [Q46](#q46) | GATE CS 2016 Set 1 | (B) 2NF |
| [Q47](#q47) | GATE IT 2005 | (B) `BD → CD` |
| [Q48](#q48) | GATE CS 2005 | (B) 3 |
| [Q49](#q49) | GATE CS 1998 | (D) `R1 ∩ R2` |
| [Q50](#q50) | GATE CS 2014 Set 3 | (A) `π_A1(σ_(F1 ∧ F2)(r))` |
| [Q51](#q51) | GATE CS 2014 Set 2 | (A) Put `r` in the outer loop. |
| [Q52](#q52) | GATE CS 2007 | (C) Names of employees with no immediate female subordinates. |
| [Q53](#q53) | GATE CS 2007 | (B) Courses in which a proper subset of female students are enrolled. |
| [Q54](#q54) | GATE CS 2008 | (A) `{M1, M2, M3, P1}` |
| [Q55](#q55) | GATE CS 2008 | (B) 3 |
| [Q56](#q56) | GATE CS 2008 | (D) Only I, III and IV |
| [Q57](#q57) | GATE CS 2008 | (C) III only |
| [Q58](#q58) | UGC NET CS 2017 Nov-III | (A) In 1NF but not in 2NF |
| [Q59](#q59) | ISRO CS 2016 | (D) All of the above |
| [Q60](#q60) | ISRO CS 2016 | (B) Both II and III |
| [Q61](#q61) | ISRO CS 2016 | (B) `mn` and `0` |
| [Q62](#q62) | UGC NET CS 2017 Jan-III | (B) `pk(R1) → pk(R2)` |
| [Q63](#q63) | UGC NET CS 2017 Jan-III | (B) `primary key ⊆ candidate key ⊆ super key` |
| [Q64](#q64) | UGC NET CS 2017 Jan-II | (D) 3 |
| [Q65](#q65) | UGC NET CS 2017 Jan-II | (C) (A) and (B) are true; (C) is false. |
| [Q66](#q66) | ISRO CS 2017 May | (B) Dashed ellipse |
| [Q67](#q67) | ISRO CS 2015 | (C) `Exam(ExamID, NID, ExamName)` |
| [Q68](#q68) | ISRO CS 2017 Dec | (A) Names of sailors who have reserved all boats called Ganga. |
| [Q69](#q69) | UGC NET CS 2017 Dec 2 | (B) Code (2) |
| [Q70](#q70) | GATE CS 2018 | (C) `r LOJ (σ_(B<5)(s))` |
| [Q71](#q71) | GATE CS 2018 | (A) Every entity in `E1` is associated with exactly one entity in `… |
| [Q72](#q72) | GATE CS Mock 2018 Set 2 | (A) 0 |
| [Q73](#q73) | GATE CS 1996 | (A) and (B), respectively. |
| [Q74](#q74) | GATE CS 1998 | (D) d |

---

## Questions and Solutions

<a id="q1"></a>

### Q1. [GATE CS 2012] Atomicity in the relational model
Given the basic ER and relational models, which statement is **INCORRECT**?

- (A) An attribute of an entity can have more than one value.
- (B) An attribute of an entity can be composite.
- (C) In a row of a relational table, an attribute can have more than one value.
- (D) In a row of a relational table, an attribute can have exactly one value or a `NULL` value.

**Answer: (C) In a row of a relational table, an attribute can have more than one value.**

**Solution:** ER attributes may be multivalued or composite. In the relational model, each cell contains one atomic value (or `NULL`); it cannot hold a set of values. Thus (C) is incorrect.

<a id="q2"></a>

### Q2. [GATE CS 2012] Foreign-key referential integrity
Let `(A, B)` and `(C, D)` be relation schemas with instances `r1` and `r2`. Attribute `B` is a foreign key referring to `C` in `r2`. If referential integrity holds, which statement is always true?

- (A) `π_B(r1) − π_C(r2) = ∅`
- (B) `π_C(r2) − π_B(r1) = ∅`
- (C) `π_B(r1) = π_C(r2)`
- (D) `π_B(r1) − π_C(r2) ≠ ∅`

**Answer: (A) `π_B(r1) − π_C(r2) = ∅`**

**Solution:** Every non-`NULL` foreign-key value in `r1.B` must occur among the referenced key values in `r2.C`. Therefore there is no value in `π_B(r1)` absent from `π_C(r2)`. The reverse containment and equality are not required because the referenced table can have keys that no row references.

<a id="q3"></a>

### Q3. [GATE CS 2012] Tuple count after union and theta join
Relations `A`, `B`, and `C` are shown below. Assume `A ∪ B` has the same schema as `A`. Find the number of tuples in the result of the expression

`(A ∪ B) ⋈_{A.Id > 40 ∨ C.Id < 15} C`.

**A**

| Id | Name | Age |
|---:|---|---:|
| 12 | Arun | 60 |
| 15 | Shreya | 24 |
| 99 | Rohit | 11 |

**B**

| Id | Name | Age |
|---:|---|---:|
| 15 | Shreya | 24 |
| 25 | Hari | 40 |
| 98 | Rohit | 20 |
| 99 | Rohit | 11 |

**C**

| Id | Phone | Area |
|---:|---:|---:|
| 10 | 2200 | 02 |
| 99 | 2100 | 01 |

- (A) 7
- (B) 4
- (C) 5
- (D) 9

**Answer: (A) 7**

**Solution:**
1. `A ∪ B` contains 5 distinct tuples: the 3 in `A` plus `(25,Hari,40)` and `(98,Rohit,20)`; the rows with IDs 15 and 99 are duplicates across the relations.
2. For the `C` row with `Id=10`, the predicate `C.Id < 15` is true, so it joins with all 5 left-side rows.
3. For `C.Id=99`, the second condition is false. The first condition holds only for left IDs 99 and 98, adding 2 rows.
4. Total: `5 + 2 = 7`.

<a id="q4"></a>

### Q4. [GATE CS 2011] Hashing versus ordered indexing
For a relation `r(A1, A2, …, An)` with enough records, where `1 ≤ p ≤ n`, consider:

- `Q1: π_{A1,…,An}(σ_{Ap=c}(r))`, where `c` is a constant.
- `Q2: π_{A1,…,An}(σ_{c1≤Ap≤c2}(r))`, where `c1` and `c2` are constants.

The database can use ordered indexing on `Ap` or hashing on `Ap`. Which statement is true?

- (A) Ordered indexing always outperforms hashing for both queries.
- (B) Hashing always outperforms ordered indexing for both queries.
- (C) Hashing outperforms ordered indexing on Q1, but not on Q2.
- (D) Hashing outperforms ordered indexing on Q2, but not on Q1.

**Answer: (C) Hashing outperforms ordered indexing on Q1, but not on Q2.**

**Solution:** Q1 is an equality lookup for one value, which hashing supports efficiently. Q2 is a range lookup; ordered indexes can locate the range and scan its entries, while a hash index does not preserve key order. Hence hashing does not outperform ordered indexing for Q2.

<a id="q5"></a>

### Q5. [GFG practice] Commands controlling access
Which commands control access to objects in a relational database?

- (A) `CASCADE` and MVD
- (B) `GRANT` and `REVOKE`
- (C) `QUE` and `QUIST`
- (D) None of these

**Answer: (B) `GRANT` and `REVOKE`**

**Solution:** `GRANT` assigns database privileges to a user or role; `REVOKE` withdraws them. These are the access-control commands.

<a id="q6"></a>

### Q6. [GFG practice] A relation as a Cartesian-product subset
If `D1, D2, …, Dn` are domains in the relational model, a relation with these domains is a subset of which set?

- (A) `D1 ⊕ D2 ⊕ … ⊕ Dn`
- (B) `D1 × D2 × … × Dn`
- (C) `D1 ∪ D2 ∪ … ∪ Dn`
- (D) `D1 ∩ D2 ∩ … ∩ Dn`

**Answer: (B) `D1 × D2 × … × Dn`**

**Solution:** An n-attribute tuple has one component from each domain, so all possible tuples form the Cartesian product. A relation is a set of some of those tuples.

<a id="q7"></a>

### Q7. [GFG practice] Definition of join
The join operation can be defined as:

- (A) A Cartesian product of two relations followed by a selection.
- (B) A Cartesian product of two relations.
- (C) A union of two relations followed by their Cartesian product.
- (D) A union of two relations.

**Answer: (A) A Cartesian product of two relations followed by a selection.**

**Solution:** A theta/equi-join forms candidate pairs using the Cartesian product, then selects pairs satisfying the join condition. A natural join additionally matches common attributes and removes duplicate copies of those attributes.

<a id="q8"></a>

### Q8. [GFG practice] Updating from another table
Which SQL command is used to change the contents of one database table using contents of another table linked by a common key field?

- (A) `REPLACE`
- (B) `JOIN`
- (C) `CHANGE`
- (D) `UPDATE`

**Answer: (D) `UPDATE`**

**Solution:** `UPDATE` changes stored values; in SQL dialects that support joined updates, it can use matching rows from another table as the source. `JOIN` combines rows for a query but is not itself the data-modification command.

<a id="q9"></a>

### Q9. [GFG practice] Owner of a weak entity set
A weak entity set is meaningful only when associated with another entity set and some of its attribute values. What is that other entity set called?

- (A) Neighbour set
- (B) Strong entity set
- (C) Owner entity set
- (D) Weak set

**Answer: (C) Owner entity set**

**Solution:** A weak entity is existence-dependent on an identifying (owner) entity set. Its identity is formed using the owner's key together with the weak entity's partial key.

<a id="q10"></a>

### Q10. [GFG practice] Dropping a referenced table
`DROP TABLE` cannot be used to drop a table referenced by which constraint?

(a) Primary key  
(b) Sub key  
(c) Super key  
(d) Foreign key

- (A) (a)
- (B) (a), (b), and (c)
- (C) (d)
- (D) (a) and (d)

**Answer: (C) (d)**

**Solution:** A foreign-key constraint in another table may depend on the referenced table's key. The DBMS prevents dropping the referenced table while that dependency remains, unless the constraint is removed or an appropriate cascade is specified. Primary, candidate, and superkeys do not themselves reference another table.

<a id="q11"></a>

### Q11. [GFG practice] Candidate key from functional dependencies
For `R(A, B, C, D, E, F, G)`, let

`F = { AD → E, BE → F, B → C, AF → G }`.

Which is a candidate key?

- (A) `A`
- (B) `AB`
- (C) `ABC`
- (D) `ABD`

**Answer: (D) `ABD`**

**Solution:**
1. `A` and `B` never appear on the right side of an FD, so every key must contain both.
2. `(ABD)+`: `AD→E` gives `E`; then `BE→F` gives `F`; then `AF→G` gives `G`; and `B→C` gives `C`. Thus `(ABD)+ = {A,B,C,D,E,F,G}`.
3. `AB` (and `ABC`) cannot derive `D` or `E`, so they are not keys. Removing any attribute from `ABD` also loses an attribute that is required or needed to derive the rest, so `ABD` is minimal.

<a id="q12"></a>

### Q12. [GFG practice] Use of NULL values
In a relational database, `NULL` values can be used for all of the following **except**:

- (A) To allow duplicate tuples by filling the primary-key column(s) with `NULL`.
- (B) To distinguish missing information from legitimate values such as integer `0` or the empty string `''`.
- (C) To mark a value as unknown.
- (D) To represent a value that does not exist or is not applicable for a particular tuple.

**Answer: (A) To allow duplicate tuples by filling the primary-key column(s) with `NULL`.**

**Solution:** A primary key must be unique and non-`NULL`; a row cannot evade primary-key rules by storing `NULL` in the key. The other options describe common reasons for representing absent, unknown, or inapplicable values.

<a id="q13"></a>

### Q13. [GFG practice] Candidate-key minimality in an instance
Consider the following relation instance with attributes `A, B, C, D`:

| A | B | C | D |
|---|---|---|---|
| a1 | b1 | c1 | d1 |
| a2 | b3 | c3 | d1 |
| a1 | b2 | c1 | d2 |

Four possible candidate keys are:

- I: `{B}`
- II: `{B, C}`
- III: `{A, D}`
- IV: `{C, D}`

If distinct symbols denote distinct values, which listed set could **not** be a candidate key for the instance?

- (A) I and III only
- (B) III and IV only
- (C) II only
- (D) I only

**Answer: (C) II only**

**Solution:** `B` has a different value in every row, so `{B}` is already a key; consequently `{B,C}` is not minimal and cannot be a candidate key. `{A,D}` gives `(a1,d1), (a2,d1), (a1,d2)`, all distinct, and neither attribute alone is unique. `{C,D}` similarly gives three distinct pairs, with neither `C` nor `D` alone unique. Those pairs are candidate keys for this instance.

<a id="q14"></a>

### Q14. [GFG practice] DROP TABLE versus DELETE
For relation `R`, consider:

- `C1: DROP TABLE R;`
- `C2: DELETE FROM R;`

Which statements are true?

I. Both C1 and C2 delete the schema for `R`.  
II. C2 retains relation `R` but deletes all its tuples.  
III. C1 deletes all tuples of `R` and its schema.

- (A) I only
- (B) I and II only
- (C) II and III only
- (D) I, II, and III

**Answer: (C) II and III only**

**Solution:** `DELETE FROM R` without a `WHERE` clause removes the rows but leaves the table definition. `DROP TABLE R` removes the table itself, including its schema. Thus I is false, while II and III are true.

<a id="q15"></a>

### Q15. [GFG practice] Statements about relational DBMS
Which statements are **FALSE**?

I. Views can support access control by showing users only a subset of database data.  
II. E-R diagrams are useful for logically modelling concepts.  
III. An update anomaly is when information cannot be stored unless unrelated information is also stored.  
IV. SQL is a procedural language.

- (A) I and IV only
- (B) III and IV only
- (C) I, II, and III only
- (D) II, III, and IV only

**Answer: (B) III and IV only**

**Solution:** I and II are true. Statement III describes an **insertion** anomaly, not an update anomaly. SQL is primarily declarative/non-procedural: users specify what data they want, rather than a step-by-step algorithm. Therefore III and IV are false.

<a id="q16"></a>

### Q16. [GFG practice] Join and outer-join tuple counts
Let `T1(P,R) = {(10,5), (15,8), (25,6)}` and `T2(A,C) = {(10,6), (25,3), (10,5)}`. Find the tuple counts for:

- `RA1: T1 ⋈_{T1.P=T2.A} T2`
- `RA2: T1 ⟕_{T1.P=T2.A} T2` (left outer join)
- `RA3: T1 ⋈_{T1.P=T2.A ∧ T1.R=T2.C} T2`

- (A) `2, 4, 2` respectively
- (B) `2, 3, 2` respectively
- (C) `3, 3, 1` respectively
- (D) `3, 4, 1` respectively

**Answer: (D) `3, 4, 1` respectively**

**Solution:** For `P=A`, the `P=10` tuple matches both `T2` rows with `A=10` (2 matches), and `P=25` matches one row (1 match), so RA1 has 3. The left outer join also retains the unmatched `(15,8)` with `NULL` right-side attributes, giving 4. RA3 requires both equalities; only `(10,5)` matches `(10,5)`, giving 1.

<a id="q17"></a>

### Q17. [GFG practice] Functional and multivalued dependencies
Every time attribute `A` appears, it is matched with the same value of `B`, but not necessarily the same value of `C`. Which statement captures this?

- (A) `A → (B,C)`
- (B) `A → B` and `A ↠ C`
- (C) `A → B` and `C ↠ A`
- (D) `A ↠ B` and `B → C`

**Answer: (B) `A → B` and `A ↠ C`**

**Solution:** “The same value of B” means `A` functionally determines `B`. “Not the same value of C” allows multiple `C` values for one `A`; the intended multivalued dependency is `A ↠ C`.

<a id="q18"></a>

### Q18. [GFG practice] Aggregation symbol
In an entity/class diagram, an aggregation association is drawn using which symbol?

- (A) A line that loops back to the same table
- (B) A small open diamond at the end of a line connecting two tables
- (C) A small filled diamond at the end of a line connecting two tables
- (D) A small filled triangle at the end of a line connecting two tables

**Answer: (B) A small open diamond at the end of a line connecting two tables**

**Solution:** UML aggregation uses a hollow (open) diamond at the aggregate/whole end of the association. A filled diamond denotes composition, which is a stronger ownership relationship.

<a id="q19"></a>

### Q19. [GFG practice] Validity of a four-way relationship instance
An E-R diagram has a relationship among entity sets `P`, `Q`, `S`, and `T`, with arrows from the relationship to `S` and `T`. The arrows mean that the other participating entity values determine at most one value of the arrowed-to entity. Three proposed relationship sets are:

| Set | Tuples `(P,Q,S,T)` |
|---|---|
| I | `(p1,q1,s1,t1)`, `(p1,q1,s1,t2)` |
| II | `(p1,q1,s1,t1)`, `(p1,q1,s2,t2)` |
| III | `(p1,q1,s1,t1)`, `(p1,q2,s1,t1)` |

Which proposed set could **not** be the relationship set for the diagram?

- (A) I only
- (B) I and II only
- (C) II only
- (D) I, II, and III

**Answer: (A) I only**

**Solution:** The arrow to `T` requires `(P,Q,S) → T`; the arrow to `S` requires `(P,Q,T) → S`. In I, the same `(p1,q1,s1)` is paired with two different `T` values, violating the first constraint. In II, the `S` and `T` values both change, so neither determining combination repeats with a different target. In III, `Q` changes, so the determining combinations differ and no constraint is violated.

<a id="q20"></a>

### Q20. [GFG practice] NULLs, 3NF, BCNF, and projection
Consider these statements about the relational model:

(a) A `NULL` value can be used to opt a tuple out of enforcement of a foreign key.  
(b) If a relation has only one candidate key and is in 3NF, then it is in BCNF.  
(c) Relational-algebra projection `Π` removes duplicate tuples, whereas SQL `SELECT` returns duplicate rows unless `DISTINCT` is specified.

Which statements are true?

- (A) (a) and (b)
- (B) (a) and (c)
- (C) (b) and (c)
- (D) (a), (b), and (c)

**Answer: (D) (a), (b), and (c)**

**Solution:** (a) is true under the usual SQL foreign-key semantics: a `NULL` foreign-key value has no referenced value to check. (c) is the set-versus-bag distinction between relational projection and SQL selection. (b) is also true. In 3NF, every nontrivial FD `X → A` either has `X` as a superkey or has prime attribute `A` on its right. If the latter applied while `X` was not a superkey, then with the unique candidate key `K`, the set `X ∪ (K − {A})` would be a superkey. Since the FD is nontrivial, `A` is not in `X`, so this set omits `A` and contains a candidate key distinct from `K`—a contradiction. Therefore every nontrivial determinant must be a superkey, which is BCNF.

<a id="q21"></a>

### Q21. [GFG practice] Purpose of normalization
Relational-schema normalization is **not** intended to:

- (A) Reduce the number of joins needed to satisfy a query.
- (B) Eliminate uncontrolled data redundancy.
- (C) Reduce anomalies that can occur during insertions and deletions.
- (D) Ensure functional dependencies are enforced.

**Answer: (A) Reduce the number of joins needed to satisfy a query.**

**Solution:** Normalization organizes data to reduce redundancy and modification anomalies and to structure constraints. Decomposing relations can require *more* joins when reconstructing answers; minimizing query joins is not its goal.

<a id="q22"></a>

### Q22. [GATE CS 2022] Which statement about normal forms is true?
In the relational data model, which statement is true?

- (A) A relation with only two attributes is always in BCNF.
- (B) If all attributes of a relation are prime, then the relation is in BCNF.
- (C) Every relation has at least one non-prime attribute.
- (D) BCNF decompositions preserve functional dependencies.

**Answer: (A) A relation with only two attributes is always in BCNF.**

**Solution:** In a two-attribute relation, any nontrivial FD must determine one attribute from the other; that determinant is then a key. Thus no nontrivial FD violates BCNF. (B) is false: for example, in `R(A,B,C)` with `A→C`, `B→C`, and `C→A`, all attributes are prime, yet `A→C` has a non-superkey determinant. (C) is false because every attribute may be prime. (D) is false because BCNF decomposition is not always dependency-preserving.

<a id="q23"></a>

### Q23. [GFG practice] Operations that can violate a foreign key
Let `R1(a,b,c)` and `R2(x,y,z)` have `a` as a foreign key in `R1` referring to the primary key `x` in `R2`. Which operations can cause a referential-integrity violation?

(a) Insert into `R1`  
(b) Insert into `R2`  
(c) Delete from `R1`  
(d) Delete from `R2`

- (A) (a) and (b)
- (B) (b) and (c)
- (C) (c) and (d)
- (D) (d) and (a)

**Answer: (D) (d) and (a)**

**Solution:** An inserted `R1.a` value may have no matching `R2.x`, so (a) can violate the constraint. Deleting an `R2` row may leave an `R1.a` reference dangling, so (d) can violate it unless deletion is cascaded or otherwise handled. Inserting a referenced key into `R2` and deleting a referencing row from `R1` do not create dangling references.

<a id="q24"></a>

### Q24. [GATE CS 2013] Queries for students scoring above 90
Use the schemas:

```text
Students(rollno: integer, sname: string)
Courses(courseno: integer, cname: string)
Registration(rollno: integer, courseno: integer, percent: real)
```

Which expressions are equivalent to: “Find the distinct names of all students who score more than 90% in the course numbered 107”?

**I. SQL**
```sql
SELECT DISTINCT S.sname
FROM Students AS S, Registration AS R
WHERE R.rollno = S.rollno
  AND R.courseno = 107
  AND R.percent > 90;
```

**II. Relational algebra**
`Π_sname(σ_{courseno=107 ∧ percent>90}(Registration ⋈ Students))`

**III. Tuple relational calculus**
`{ T | ∃S∈Students, ∃R∈Registration (S.rollno=R.rollno ∧ R.courseno=107 ∧ R.percent>90 ∧ T.sname=S.sname) }`

**IV. Domain relational calculus**
`{ <S_N> | ∃S_R ∃R_P (<S_R,S_N>∈Students ∧ <S_R,107,R_P>∈Registration ∧ R_P>90) }`

- (A) I, II, III, and IV
- (B) I, II, and III only
- (C) I, II, and IV only
- (D) II, III, and IV only

**Answer: (A) I, II, III, and IV**

**Solution:** Each expression matches student registration rows by `rollno`, keeps course 107 registrations with `percent > 90`, and returns the student name. SQL I explicitly removes duplicate names; relational-algebra projection has set semantics and does the same. The tuple and domain calculus expressions impose the same predicates and project the name. `Courses` is not needed because the course number is given directly.

<a id="q25"></a>

### Q25. [GFG practice] Preventing modification anomalies
In an RDBMS, different classes of relations are created using which technique to prevent modification anomalies?

- (A) Functional dependencies
- (B) Data integrity
- (C) Referential integrity
- (D) Normal forms

**Answer: (D) Normal forms**

**Solution:** Normalization decomposes relations into normal forms (such as 1NF, 2NF, 3NF, and BCNF) to reduce redundancy and avoid insertion, update, and deletion anomalies.

<a id="q26"></a>

### Q26. [GFG practice] Weak-entity properties
Which statement about a weak entity set is **FALSE**?

- (A) Weak entities can be deleted automatically when their strong entity is deleted.
- (B) A weak entity set avoids duplicating the strong entity's key throughout the dependent entity data and the resulting inconsistencies.
- (C) A weak entity set has no complete primary key unless the key of its identifying strong entity is included.
- (D) Tuples in a weak entity set are not partitioned according to their relationship with tuples in a strong entity set.

**Answer: (D) Tuples in a weak entity set are not partitioned according to their relationship with tuples in a strong entity set.**

**Solution:** A weak entity is identified in the context of its owner; its tuples are associated/partitioned by the owner entity. Its key combines the owner's key and the weak entity's partial key. The dependency also permits cascading deletion, so (A)–(C) describe standard weak-entity properties; (D) reverses that property.

<a id="q27"></a>

### Q27. [GFG practice] Armstrong's inference axioms
Armstrong's inference rules for functional dependencies refer to which rules?

- (A) Reflexivity, augmentation, and decomposition
- (B) Transitivity, augmentation, and reflexivity
- (C) Augmentation, transitivity, reflexivity, and decomposition
- (D) Reflexivity, transitivity, and decomposition

**Answer: (B) Transitivity, augmentation, and reflexivity**

**Solution:** The three basic Armstrong axioms are reflexivity, augmentation, and transitivity. Decomposition is a derived rule, not one of the three basic axioms.

<a id="q28"></a>

### Q28. [GFG practice] Lossless-join decomposition condition
The relation schemas `R1` and `R2` form a lossless-join decomposition of `R` if and only if which listed conditions hold?

(a) `R1 ∩ R2 ↠ (R1 − R2)`  
(b) `R1 → R2`  
(c) `R1 ∩ R2 ↠ (R2 − R1)`  
(d) `(R2 → R1) ∩ R2`

- (A) (a) and (b)
- (B) (a) and (d)
- (C) (a) and (c)
- (D) (b) and (c)

**Answer: (C) (a) and (c)**

**Solution:** For a binary decomposition, let `X = R1 ∩ R2`, `Y = R1 − R2`, and `Z = R2 − R1`. The lossless condition can be expressed as `X ↠ Y` (equivalently, by complementation, `X ↠ Z`). These are statements (a) and (c); the listed functional-dependency forms are not the stated MVD condition.

<a id="q29"></a>

### Q29. [GFG practice] Extracting columns
Which relational operation extracts specified columns from a table?

- (A) Project
- (B) Join
- (C) Extract
- (D) Substitute

**Answer: (A) Project**

**Solution:** Projection `π` selects columns (attributes). In relational algebra it also removes duplicate resulting tuples.

<a id="q30"></a>

### Q30. [GFG practice] Application-level database view
A view of a database that appears to an application program is known as:

- (A) Schema
- (B) Subschema
- (C) Virtual table
- (D) Index table

**Answer: (B) Subschema**

**Solution:** A subschema is the application/user-specific view of the database, exposing the portion and structure needed by that program rather than the entire conceptual schema.

<a id="q31"></a>

### Q31. [GFG practice] Modelling a person keeping animals as pets
How can the fact that some person keeps animals as pets be expressed? The choices show `Person` and `Animal` entity boxes and alternative placements/names for the association or multiplicity:

- (A) `Person` — `Animal`, with a `0…*` multiplicity at the animal end and association label `pet`.
- (B) `Person` — `Animal`, with the text `pet 0…*` placed together by the animal end.
- (C) `Person` — `Pet`, with `0…*` at the pet end and label `animal`.
- (D) `Person` — `Animal`, with the line labelled `keep pet as →` pointing to `Animal`.

**Answer: (A) The `Person`–`Animal` association labelled `pet`, with `0…*` at the animal end.**

**Solution:** “Keeps animals as pets” is a relationship between people and animals, not a separate `Pet` entity in this representation. A person may be associated with zero or more animals, so the multiplicity is `0…*` at the `Animal` end, and the association is labelled `pet`.

<a id="q32"></a>

### Q32. [GFG practice] Converting a weak entity to a strong entity
What mechanism converts a weak entity set into a strong entity set in an E-R diagram?

- (A) Generalization
- (B) Aggregation
- (C) Specialization
- (D) Adding suitable attributes

**Answer: (D) Adding suitable attributes**

**Solution:** A weak entity lacks enough attributes to form its own key. Add suitable identifying attribute(s) so it has a key independent of its owner, and it can be represented as a strong entity set.

<a id="q33"></a>

### Q33. [GFG practice] Dominant and subordinate entities
In an E-R model, `Y` is the dominant entity and `X` is the subordinate entity. Which statement is correct?

- (A) None of the above
- (B) If `Y` is deleted, then `X` is also deleted.
- (C) If `Y` is deleted, then `X` is not deleted.
- (D) If `X` is deleted, then `Y` is also deleted.

**Answer: (B) If `Y` is deleted, then `X` is also deleted.**

**Solution:** The subordinate entity depends on the dominant entity. Deleting the dominant entity removes its dependent subordinate entity; deleting the subordinate does not require deleting the dominant one.

<a id="q34"></a>

### Q34. [GFG practice] Expressive limits of basic relational algebra
Given `employee(name, salary, dept-no)` and `department(dept-no, dept-name, address)`, which query cannot be expressed using the basic relational algebra operations `(σ, π, ×, −, ∪, ρ)`?

- (A) Department address of every employee
- (B) Employees whose name is the same as their department name
- (C) The sum of all employees' salaries
- (D) All employees of a given department

**Answer: (C) The sum of all employees' salaries**

**Solution:** The basic operators select, project, combine, and rename tuples, but do not compute aggregate values such as `SUM`. A sum requires an aggregate/grouping extension to relational algebra. The other queries can be expressed with joins (or product plus selection) and projection/selection.

<a id="q35"></a>

### Q35. [GATE CS 2020] Identifying relationship for a weak entity
Which symbol represents the supporting many-one relationship of a weak entity set in an E-R diagram?

- (A) Diamonds with double/bold border
- (B) Rectangles with double/bold border
- (C) Ovals with double/bold border
- (D) Ovals containing underlined identifiers

**Answer: (A) Diamonds with double/bold border**

**Solution:** The identifying relationship connecting a weak entity set to its owner is shown by a double diamond. The weak entity itself uses a double rectangle; attributes are ovals, and key attributes are underlined.

<a id="q36"></a>

### Q36. [GFG practice] Functional dependency for a many-to-one relationship
A many-to-one relationship exists from entity set `r1` to entity set `r2`. If `Pk(r)` denotes the primary-key attribute of relation `r`, which FD represents it?

- (A) `Pk(r1) → Pk(r2)`
- (B) `Pk(r2) → Pk(r1)`
- (C) `Pk(r2) → Pk(r1)` and `Pk(r1) → Pk(r2)`
- (D) `Pk(r2) → Pk(r1)` or `Pk(r1) → Pk(r2)`

**Answer: (A) `Pk(r1) → Pk(r2)`**

**Solution:** In a many-to-one mapping from `r1` to `r2`, each `r1` entity is associated with one `r2` entity, but an `r2` entity may be associated with many `r1` entities. Therefore an `r1` key determines the corresponding `r2` key, not vice versa.

<a id="q37"></a>

### Q37. [GFG practice] Join returning matching rows
In an RDBMS, which type of join returns all rows that satisfy the join condition?

- (A) Inner join
- (B) Outer join
- (C) Semi join
- (D) Anti join

**Answer: (A) Inner join**

**Solution:** An inner join returns the row pairs for which the join condition is true. Outer joins additionally preserve unmatched rows from one or both sides; semi and anti joins return only one side's matching or non-matching rows.

<a id="q38"></a>

### Q38. [ISRO CS 2018] Logical data independence
Immunity of external schemas (or application programs) to changes in the conceptual schema is called:

(A) Physical data independence  
(B) Logical data independence  
(C) Both (A) and (B)  
(D) None of the above

**Answer: (B) Logical data independence**

**Solution:** Logical data independence means the conceptual schema can change without requiring changes to external views or application programs. Physical data independence instead isolates the logical schema from changes to physical storage.

<a id="q39"></a>

### Q39. [UGC NET CS 2014 Dec-II] Minimal key from functional dependencies
Find a minimal key for `R(A, B, C, D, E)` with `F = {A → B, B → C, AC → D}`.

(A) `A`  
(B) `AE`  
(C) `BE`  
(D) `CE`

**Answer: (B) `AE`**

**Solution:** From `A → B` and `B → C`, `A` determines `A, B, C`; then `AC → D` gives `D`. Thus `A+ = {A,B,C,D}`. No dependency determines `E`, so a key must include `E`. `AE+` contains all five attributes, and neither `A` nor `E` alone is a key.

<a id="q40"></a>

### Q40. [GATE CS 2014 Set 3] Employees older than all their dependents
Let `employee(empId, empName, empAge)` and `dependent(depId, eId, depName, depAge)`, where `dependent.eId` is a foreign key to `employee.empId`. Assume each employee has at least one dependent. Evaluate:

```text
π_empId(employee)
− π_empId(employee ⋈_(empId=eId ∧ empAge≤depAge) dependent)
```

The result is the set of employee IDs of employees whose age is greater than that of:

(A) Some dependent  
(B) All dependents (globally)  
(C) Some of his/her dependents  
(D) All of his/her dependents

**Answer: (D) All of his/her dependents**

**Solution:** The join inside the subtraction finds employees having at least one dependent whose age is greater than or equal to the employee’s age. Subtracting those IDs removes anyone who fails the “older than every dependent” test. The stated nonempty-dependent assumption makes this exactly “older than all of his/her dependents.”

<a id="q41"></a>

### Q41. [GATE CS 1999] Tuple calculus to relational algebra
The tuple relational calculus expression

```text
{ t | t ∈ r ∧ (t[A] = 10 ∧ t[B] = 20) }
```

is equivalent to which relational algebra expression?

(A) `σ_(A=10 ∨ B=20)(r)`  
(B) `σ_(A=10)(r) ∪ σ_(B=20)(r)`  
(C) `σ_(A=10)(r) ∩ σ_(B=20)(r)`  
(D) `σ_(A=10)(r) − σ_(B=20)(r)`

**Answer: (C) `σ_(A=10)(r) ∩ σ_(B=20)(r)`**

**Solution:** The tuple must satisfy both conditions at once. The intersection keeps exactly the tuples that meet `A=10` and `B=20`. A and B use OR/union, while D removes tuples satisfying the second condition.

<a id="q42"></a>

### Q42. [GATE CS 1999] Minimum and maximum join size
Consider the join of relations `R` and `S`. If `R` has `m` tuples and `S` has `n` tuples, what are the maximum and minimum possible sizes of the join, respectively?

(A) `m+n` and `0`  
(B) `mn` and `0`  
(C) `m+n` and `m−n`  
(D) `mn` and `m+n`

**Answer: (B) `mn` and `0`**

**Solution:** At most every tuple of `R` can match every tuple of `S`, giving `m×n` pairs. If no tuples match on the join condition, the join is empty, so the minimum is zero.

<a id="q43"></a>

### Q43. [GATE CS Mock 2017] Number of tables from a two-entity ER model
What are the minimum and maximum numbers of tables needed to map an ER diagram with two entities and one relationship, when both entities have partial participation?

(A) Minimum 1, maximum 2  
(B) Minimum 1, maximum 3  
(C) Minimum 2, maximum 3  
(D) Minimum 2, maximum 2

**Answer: (C) Minimum 2, maximum 3**

**Solution:** The two entity sets require two tables. With a one-to-many relationship, the relationship can be represented by a foreign key on the many side, so two tables suffice. A many-to-many relationship requires a separate relationship table, giving three. Partial participation does not allow eliminating an entity table.

<a id="q44"></a>

### Q44. [GATE CS Mock 2017] Candidate keys from FDs
For relation `R(A,B,C,D)` with FDs `{A→BC, B→A, A→C, A→D, D→A}`, how many candidate keys are there?

(A) 1  
(B) 2  
(C) 3  
(D) 4

**Answer: (C) 3**

**Solution:** `A+ = {A,B,C,D}`; `B+` contains `A` and then all of `C,D`; and `D+` contains `A` and then all of `B,C`. Thus `{A}`, `{B}`, and `{D}` are candidate keys. `C+={C}`, so C is not a key.

<a id="q45"></a>

### Q45. [GATE IT 2006] Expressive power of relational query languages
Which listed languages have the same expressive power?

I. Relational algebra  
II. Tuple relational calculus restricted to safe expressions  
III. Domain relational calculus restricted to safe expressions

(A) II and III only  
(B) I and II only  
(C) I and III only  
(D) I, II and III

**Answer: (D) I, II and III**

**Solution:** Relational algebra, safe tuple relational calculus, and safe domain relational calculus are equivalent in expressive power (relationally complete). They differ in style—procedural versus declarative—not in which relational queries they can express.

<a id="q46"></a>

### Q46. [GATE CS 2016 Set 1] Normal form after decomposition
A journal-article database has schema `(VOLUME, NUMBER, STARTPGE, ENDPAGE, TITLE, YEAR, PRICE)` and primary key `(VOLUME, NUMBER, STARTPAGE, ENDPAGE)`. Its FDs are:

```text
(VOLUME, NUMBER, STARTPAGE, ENDPAGE) → TITLE
(VOLUME, NUMBER)                     → YEAR
(VOLUME, NUMBER, STARTPAGE, ENDPAGE) → PRICE
```

It is redesigned as:

```text
(VOLUME, NUMBER, STARTPAGE, ENDPAGE, TITLE, PRICE)
(VOLUME, NUMBER, YEAR)
```

What is the weakest normal form satisfied by the new design but not the old one? (The source uses `STARTPGE` in the first schema and `STARTPAGE` in the key and FDs.)

(A) 1NF  
(B) 2NF  
(C) 3NF  
(D) BCNF

**Answer: (B) 2NF**

**Solution:** In the old relation, `YEAR` depends on only `(VOLUME, NUMBER)`, a proper subset of the composite key. This is a partial dependency of a non-prime attribute, so the old relation violates 2NF. The decomposition separates this dependency: each new relation has its non-key attributes fully dependent on its key. Thus the new design reaches at least 2NF, the weakest listed form that distinguishes the designs.

<a id="q47"></a>

### Q47. [GATE IT 2005] Test whether an FD is implied
For attributes `A, B, C, D, E`, let the FDs be:

```text
A → B
A → C
CD → E
B → D
E → A
```

Which FD is **not** implied?

(A) `CD → AC`  
(B) `BD → CD`  
(C) `BC → CD`  
(D) `AC → BC`

**Answer: (B) `BD → CD`**

**Solution:** Compute the closure of each left side.

- `CD+`: `CD → E`, `E → A`, `A → B` → `{A,B,C,D,E}` contains `A,C` → (A) implied.
- `BD+`: only `B → D` applies (no FD has `B` or `D` alone leading to `A` or `C`) → `{B,D}`. It does **not** contain `C` → (B) **not implied**.
- `BC+`: `B → D` → `{B,C,D}` contains `C,D` → (C) implied.
- `AC+`: `A → B` → `{A,B,C}` contains `B,C` → (D) implied.

<a id="q48"></a>

### Q48. [GATE CS 2005] Tables for two relationship sets
Let `E1` and `E2` be entity sets with simple, single-valued attributes. `R1` and `R2` are relationships between them: `R1` is one-to-many and `R2` is many-to-many. Neither relationship has attributes of its own. What is the minimum number of relational tables needed?

(A) 2  
(B) 3  
(C) 4  
(D) 5

**Answer: (B) 3**

**Solution:** Each entity needs its own table. The many-to-many relationship `R2` needs a third table containing the keys of both entities. The one-to-many relationship `R1` can be represented by a foreign key on its many side, so it does not require another table.

<a id="q49"></a>

### Q49. [GATE CS 1998] Join of union-compatible relations
Given union-compatible relations `R1(A,B)` and `R2(C,D)`, what is the result of

```text
R1 ⋈_(A=C ∧ B=D) R2
```

(A) `R1 ∪ R2`  
(B) `R1 × R2`  
(C) `R1 − R2`  
(D) `R1 ∩ R2`

**Answer: (D) `R1 ∩ R2`**

**Solution:** The join condition matches a row of `R1` with a row of `R2` exactly when both corresponding values agree. Since the relations are union-compatible (with attributes aligned), those are precisely their common tuples: the intersection.

<a id="q50"></a>

### Q50. [GATE CS 2014 Set 3] Optimize a relational algebra expression
What is an optimized version of

```text
π_A1(π_A2(σ_F1(σ_F2(r))))
```

where `A1` and `A2` are sets of attributes in `r`, `A1 ⊆ A2`, and `F1` and `F2` are Boolean expressions based on attributes in `r`?

(A) `π_A1(σ_(F1 ∧ F2)(r))`  
(B) `π_A1(σ_(F1 ∨ F2)(r))`  
(C) `π_A2(σ_(F1 ∧ F2)(r))`  
(D) `π_A2(σ_(F1 ∨ F2)(r))`

**Answer: (A) `π_A1(σ_(F1 ∧ F2)(r))`**

**Solution:** Consecutive selections combine into one selection with the conjunction `F1 ∧ F2`. The two projections collapse to the outer projection because `A1 ⊆ A2`, and the final output only needs `A1`. The OR alternatives change which rows qualify; projection onto `A2` returns extra attributes.

<a id="q51"></a>

### Q51. [GATE CS 2014 Set 2] Outer relation in nested-loop join
Relations `r(R)` and `s(S)` are joined using the nested-loop method. There are three buffers, each one disk block in size, and one buffer is reserved for intermediate results. Assume `size(r) < size(s)`. Which choice gives fewer disk-block accesses?

(A) Put `r` in the outer loop.  
(B) Put `s` in the outer loop.  
(C) The join selection factor is greater than 0.5.  
(D) The join selection factor is less than 0.5.

**Answer: (A) Put `r` in the outer loop.**

**Solution:** In a tuple/block nested-loop join, the inner relation is rescanned for each outer block (or tuple, for the tuple version). The cost is reduced by making the smaller relation the outer relation. Since `r` is smaller than `s`, choose `r` outside; the selection factor does not determine this I/O comparison.

<a id="q52"></a>

### Q52. [GATE CS 2007] Tuple calculus and employees without male subordinates
Relation `employee(name, sex, supervisorName)` has `name` as its key; `supervisorName` is the supervisor’s name for that employee. What does this tuple relational calculus expression return?

```text
{ e.name | employee(e) ∧ (∀x)[¬employee(x) ∨ x.supervisorName ≠ e.name ∨ x.sex = "male"] }
```

(A) Names of employees with a male supervisor.  
(B) Names of employees with no immediate male subordinates.  
(C) Names of employees with no immediate female subordinates.  
(D) Names of employees with a female supervisor.

**Answer: (C) Names of employees with no immediate female subordinates.**

**Solution:** For every employee `x`, if `x` reports to `e`, the formula requires `x.sex` to be male. Thus no immediate subordinate of `e` can be female.

<a id="q53"></a>

### Q53. [GATE CS 2007] Courses with a proper subset of female students enrolled
Let `studinfo(studId, name, sex)` and `enroll(studId, courseId)` record students and enrollments. Assume every course is taken by at least one male and at least one female student. What does this expression represent?

```text
π_courseId(
  (π_studId(σ_(sex="female")(studinfo)) × π_courseId(enroll)) − enroll
)
```

(A) Courses in which all female students are enrolled.  
(B) Courses in which a proper subset of female students are enrolled.  
(C) Courses in which only male students are enrolled.  
(D) None of the above.

**Answer: (B) Courses in which a proper subset of female students are enrolled.**

**Solution:** The product creates every possible female-student/course pair. Subtracting `enroll` leaves female/course pairs that are missing. Projecting course IDs finds courses with at least one female not enrolled. By the assumption, each course also has at least one female enrolled, so the enrolled female students form a proper subset, not an empty set or the full set.

<a id="q54"></a>

### Q54. [GATE CS 2008] Attribute set for a mapped ER table
Consider the ER diagram described here: strong entities `M(M1,M2,M3)` and `P(P1,P2)`, with `M1` and `P1` as keys; `R1` is a many-to-one relationship from `M` to `P` (total participation by `M`); `N(N1,N2)` is a weak entity identified through `P` by `R2`, with `N1` a partial key. Which is a correct attribute set for one mapped table?

(A) `{M1, M2, M3, P1}`  
(B) `{M1, P1, N1, N2}`  
(C) `{M1, P1, N1}`  
(D) `{M1, P1}`

**Answer: (A) `{M1, M2, M3, P1}`**

**Solution:** `M` is on the many side of `R1`, so store the key `P1` as a foreign key in the `M` table. The resulting table is `(M1,M2,M3,P1)`. The weak entity `N` has a separate table containing `P1` and its own attributes.

<a id="q55"></a>

### Q55. [GATE CS 2008] Minimum number of tables for an ER diagram
Using the ER diagram described in Q17—strong entities `M` and `P`, weak entity `N` identified by `P`, and many-to-one `R1` from `M` to `P`—what is the minimum number of tables needed to represent `M`, `N`, `P`, `R1`, and `R2`?

(A) 2  
(B) 3  
(C) 4  
(D) 5

**Answer: (B) 3**

**Solution:** `M`, `P`, and weak entity `N` require three tables. Put `P1` as a foreign key in `M` for the many-to-one `R1`; put the identifying owner key `P1` in `N`’s table for `R2`. Neither relationship needs its own table.  
> Note: GFG marks (C), but its own explanation describes the three-table mapping; the correct minimum is 3 (option B).

<a id="q56"></a>

### Q56. [GATE CS 2008] Equivalent relational algebra queries
Let `R(P,Q,R1,R2,R3)` and `S(P,Q,S1,S2)` have `{P,Q}` as the key in both relations. Which of these expressions are equivalent?

```text
I.   π_P(R ⋈ S)
II.  π_P(R) ⋈ π_P(S)
III. π_P(π_(P,Q)(R) ∩ π_(P,Q)(S))
IV.  π_P(π_(P,Q)(R) − (π_(P,Q)(R) − π_(P,Q)(S)))
```

(A) Only I and II  
(B) Only I and III  
(C) Only I, II and III  
(D) Only I, III and IV

**Answer: (D) Only I, III and IV**

**Solution:** The natural join in I matches equal `(P,Q)` pairs, then projects their `P` values. III explicitly intersects the projected `(P,Q)` pairs before projecting `P`. In IV, `X − (X − Y)` is `X ∩ Y`, so it has the same result. II joins only on `P`, losing the `Q` requirement; a `P` value can match across different `Q` values.

<a id="q57"></a>

### Q57. [GATE CS 2008] Equivalent tuple calculus expressions
Which tuple relational calculus expression(s) is/are equivalent to the condition shown in the question, `∀t ∈ r (P(t))`?

```text
I.   ¬∃t ∈ r (P(t))
II.  ∃t ∉ r (P(t))
III. ¬∃t ∈ r (¬P(t))
IV.  ∃t ∉ r (¬P(t))
```

(A) I only  
(B) II only  
(C) III only  
(D) III and IV only

**Answer: (C) III only**

**Solution:** “Every tuple in `r` satisfies `P`” is equivalent to “there is no tuple in `r` that fails `P`,” which is III. I says there is no tuple satisfying `P`; II and IV quantify over tuples outside `r`, so they do not express the required universal condition.

<a id="q58"></a>

### Q58. [UGC NET CS 2017 Nov-III] Normal form from functional dependencies
Consider `R(A,B,C,D,E,F,G,H)`, with atomic attributes and FDs:

```text
CH → G
A  → BC
B  → CFH
E  → A
F  → EG
```

Which normal-form statement is correct?

(A) In 1NF but not in 2NF  
(B) In 2NF but not in 3NF  
(C) In 3NF but not in BCNF  
(D) In BCNF

**Answer: (A) In 1NF but not in 2NF**

**Solution:** `D` never appears on an FD right-hand side, so every candidate key must include it. `A+` contains every attribute except `D`; therefore `AD` is a candidate key. But `A → C` is a dependency from a proper subset of this key to non-prime attribute `C`, violating 2NF. Atomic attributes give 1NF.  
> Note: GFG marks (B), but its explanation itself identifies a partial dependency and says the relation is not in 2NF; (A) follows.

<a id="q59"></a>

### Q59. [ISRO CS 2016] Goals of logical-schema design
Goals for the design of a logical schema include:

(A) Avoiding data inconsistency  
(B) Being able to construct queries easily  
(C) Being able to access data efficiently  
(D) All of the above

**Answer: (D) All of the above**

**Solution:** A good logical schema should preserve consistency while representing relationships clearly, support understandable queries, and enable efficient data access. Hence all three goals apply.

<a id="q60"></a>

### Q60. [ISRO CS 2016] Operations that can violate referential integrity
Let `R(a,b,c)` and `S(d,e,f)` have `d` as a foreign key referencing the primary key of `R`. Which operations can violate this referential-integrity constraint?

I. Insert into `R`  
II. Insert into `S`  
III. Delete from `R`  
IV. Delete from `S`

(A) Both I and IV  
(B) Both II and III  
(C) All of these  
(D) None of these

**Answer: (B) Both II and III**

**Solution:** Inserting an `S` row with a nonexistent referenced key violates the constraint. Deleting an `R` row that is still referenced by `S` also violates it (absent a cascading action). Inserting a parent row or deleting a child row cannot create a dangling reference.

<a id="q61"></a>

### Q61. [ISRO CS 2016] Maximum and minimum join cardinalities
If relation `R` has `m` tuples and relation `S` has `n` tuples, what are the maximum and minimum sizes of their join, respectively?

(A) `m+n` and `0`  
(B) `mn` and `0`  
(C) `m+n` and `|m−n|`  
(D) `mn` and `m+n`

**Answer: (B) `mn` and `0`**

**Solution:** A join can pair each tuple in `R` with each tuple in `S`, so the maximum is `mn`. If no pair satisfies the join condition, there are no result tuples, giving a minimum of zero.

<a id="q62"></a>

### Q62. [UGC NET CS 2017 Jan-III] FD for a many-to-one relationship
Let `pk(R)` denote the primary key of relation `R`. A many-to-one relationship from `R1` to `R2` can be expressed as:

(A) `pk(R2) → pk(R1)`  
(B) `pk(R1) → pk(R2)`  
(C) `pk(R2) → R1 ∩ R2`  
(D) `pk(R1) → R1 ∩ R2`

**Answer: (B) `pk(R1) → pk(R2)`**

**Solution:** Each `R1` entity is associated with at most one `R2` entity. Thus an `R1` key determines the associated `R2` key. The reverse direction would incorrectly assert that each `R2` entity maps to only one `R1` entity.

<a id="q63"></a>

### Q63. [UGC NET CS 2017 Jan-III] Relationship between key types
Which statement is correct for keys in an RDBMS?

(A) `primary key ⊆ super key ⊆ candidate key`  
(B) `primary key ⊆ candidate key ⊆ super key`  
(C) `super key ⊆ candidate key ⊆ primary key`  
(D) `super key ⊆ primary key ⊆ candidate key`

**Answer: (B) `primary key ⊆ candidate key ⊆ super key`**

**Solution:** Every primary key is a chosen candidate key. Candidate keys are minimal superkeys, while superkeys may contain extra attributes. So the intended hierarchy is primary key, then candidate key, then superkey.

<a id="q64"></a>

### Q64. [UGC NET CS 2017 Jan-II] Minimum ER-to-relational table count
Entities `M` and `N` have simple, single-valued attributes. `R1` and `R2` relate `M` and `N`; `R1` is one-to-many and `R2` is many-to-many. What is the minimum number of tables needed for `M`, `N`, `R1`, and `R2`?

(A) 4  
(B) 6  
(C) 7  
(D) 3

**Answer: (D) 3**

**Solution:** Use one table for each entity (`M` and `N`) and one associative table for the many-to-many relationship `R2`. The one-to-many `R1` is represented with a foreign key on the many side, so no fourth table is needed.

<a id="q65"></a>

### Q65. [UGC NET CS 2017 Jan-II] Examples of integrity constraints
Which statements are true?

(A) An instructor ID cannot be null if it is the primary key.  
(B) No two citizens have the same Aadhaar ID.  
(C) A company’s budget must be zero.

(A) (A), (B), and (C) are true.  
(B) (A) is false; (B) and (C) are true.  
(C) (A) and (B) are true; (C) is false.  
(D) (A), (B), and (C) are false.

**Answer: (C) (A) and (B) are true; (C) is false.**

**Solution:** A primary key must be unique and non-null. An Aadhaar identifier is intended to uniquely identify a citizen. A zero budget is not a general integrity rule for companies, so statement C is false.

<a id="q66"></a>

### Q66. [ISRO CS 2017 May] ER notation for derived attributes
Which symbol denotes a derived attribute in an ER model?

(A) Double ellipse  
(B) Dashed ellipse  
(C) Squared ellipse  
(D) Ellipse with the attribute name underlined

**Answer: (B) Dashed ellipse**

**Solution:** A dashed ellipse denotes an attribute whose value is derived from other stored data rather than stored independently. A double ellipse commonly denotes a multivalued attribute; underlining indicates a key attribute.

<a id="q67"></a>

### Q67. [ISRO CS 2015] Mapping a relationship entity to relations
Consider an ER diagram with entities `Person` and `Exam`, related by `Qualification`, which has attribute `QualifiedDate`. Which possible relation schema will **not** hold when this ERD is mapped to a relational model?

(A) `Person(NID, Name)`  
(B) `Qualification(NID, ExamID, QualifiedDate)`  
(C) `Exam(ExamID, NID, ExamName)`  
(D) `Exam(ExamID, ExamName)`

> Note: The source block omitted the ERD graphic; the entity and relationship attributes above are the details available from the question text and options.

**Answer: (C) `Exam(ExamID, NID, ExamName)`**

**Solution:** Keep the `Exam` entity in its own relation with its identifier and descriptive attributes. The relationship (including its `QualifiedDate` attribute) is represented separately with the keys of `Person` and `Exam`. Placing `NID` directly in `Exam` would impose a one-to-many direction not justified by the ERD. Thus A, B, and D are appropriate schemas; C is not.

<a id="q68"></a>

### Q68. [ISRO CS 2017 Dec] Division for sailors reserving every Ganga boat
Use the schemas:

```text
Sailors(sid, sname, rating, age)
Boats(bid, bname, colour)
Reserves(sid, bid, day)
```

Two boats can have the same name; their colours distinguish them. Let `/` denote relational division. The relations are:

```text
Tempsids ← π_(sid,bid)(Reserves) / π_bid(σ_(bname='Ganga')(Boats))
π_sname(Tempsids ⋈ Sailors)
```

What does the result represent?

(A) Names of sailors who have reserved all boats called Ganga.  
(B) Names of sailors who have not reserved any Ganga boat.  
(C) Names of sailors who have reserved at least one Ganga boat.  
(D) Names of sailors who have reserved at most one Ganga boat.

**Answer: (A) Names of sailors who have reserved all boats called Ganga.**

**Solution:** The divisor is the set of IDs of all boats named Ganga. Division returns sailor IDs paired with every boat ID in that set—that is, sailors who reserved each Ganga boat. Joining those IDs to `Sailors` and projecting `sname` produces their names.

<a id="q69"></a>

### Q69. [UGC NET CS 2017 Dec 2] Match integrity constraints
Match the constraint type with its description:

| Type | Description |
|---|---|
| (a) Entity integrity | (i) Enforces a specific business rule not covered by entity or domain integrity |
| (b) Domain integrity | (ii) Rows used by other records cannot be deleted |
| (c) Referential integrity | (iii) Enforces valid entries for a column |
| (d) User-defined integrity | (iv) No duplicate rows in a table |

Codes:

| Code | (a) | (b) | (c) | (d) |
|---|---|---|---|---|
| (1) | (iii) | (iv) | (i) | (ii) |
| (2) | (iv) | (iii) | (ii) | (i) |
| (3) | (iv) | (ii) | (iii) | (i) |
| (4) | (ii) | (iii) | (iv) | (i) |

(A) Code (1)  
(B) Code (2)  
(C) Code (3)  
(D) Code (4)

**Answer: (B) Code (2)**

**Solution:** Entity integrity prevents duplicate entity rows (iv); domain integrity restricts valid column values (iii); referential integrity protects referenced rows (ii); and user-defined integrity encodes additional business rules (i). This is code (2).

<a id="q70"></a>

### Q70. [GATE CS 2018] Left outer join and selection
Let `r(A,B)` and `s(B,C)` be relations. In `s`, `B` is a primary key; in `r`, `B` is a foreign key referencing `s.B`. Assume no null values. Let `LOJ` mean natural left outer join. The query is

```text
Q = r ⋈ σ_(B<5)(s)
```

Which expression is **not** equivalent to `Q`?

(A) `σ_(B<5)(r ⋈ s)`  
(B) `σ_(B<5)(r LOJ s)`  
(C) `r LOJ (σ_(B<5)(s))`  
(D) `σ_(B<5)(r) LOJ s`

**Answer: (C) `r LOJ (σ_(B<5)(s))`**

**Solution:** The original is an inner join: it returns only `r` rows whose matching `s` row has `B<5`. Because `r.B` is a foreign key to `s.B`, that is equivalent to filtering the joined result (A), filtering the left rows before an outer join (D), or applying the stated filter after the outer join (B), since unmatched rows have no qualifying `B<5` value. C is different: its left outer join preserves every row of `r`, including those with `B≥5`, with nulls on the `s` side.

<a id="q71"></a>

### Q71. [GATE CS 2018] Participation in a many-to-one relationship
In an ER model, `R` is many-to-one from entity set `E1` to `E2`. Both entity sets participate totally in `R`, and `E1` has greater cardinality than `E2`. Which statement is true?

(A) Every entity in `E1` is associated with exactly one entity in `E2`.  
(B) Some entity in `E1` is associated with more than one entity in `E2`.  
(C) Every entity in `E2` is associated with exactly one entity in `E1`.  
(D) Every entity in `E2` is associated with at most one entity in `E1`.

**Answer: (A) Every entity in `E1` is associated with exactly one entity in `E2`.**

**Solution:** Many-to-one means an `E1` entity maps to at most one `E2` entity. Total participation of `E1` means it maps to at least one. Together these give exactly one. The inverse direction permits an `E2` entity to relate to multiple `E1` entities.

<a id="q72"></a>

### Q72. [GATE CS Mock 2018 Set 2] Cascading deletes and foreign keys
The table contents are:

**T1(P,Q)**

| P | Q |
|---:|---:|
| 2 | 2 |
| 3 | 8 |
| 7 | 3 |
| 5 | 8 |
| 6 | 9 |
| 8 | 5 |
| 9 | 8 |

**T2(R,S)**

| R | S |
|---:|---:|
| 2 | 2 |
| 8 | 3 |
| 3 | 2 |
| 9 | 7 |
| 5 | 7 |
| 7 | 2 |

In `T1`, `P` is the primary key and `Q` is a foreign key referencing `T2.R`, with `ON DELETE CASCADE` and `ON UPDATE CASCADE`. In `T2`, `R` is the primary key and `S` is a foreign key referencing `T1.P`, with `ON DELETE SET NULL` and `ON UPDATE CASCADE`. To delete row `(3,8)` from `T1`, how many additional records must be deleted from `T1`?

(A) 0  
(B) 1  
(C) 2  
(D) 3

**Answer: (A) 0**

**Solution:** Deleting `(3,8)` deletes the `T1` row whose primary key is `P=3`. Rows in `T2` that refer to `P=3` have `S` set to `NULL`; they are not deleted. `T1.Q` referencing `T2.R` affects what happens when a `T2` parent row is deleted, not when this `T1` row is deleted. No additional `T1` row must be removed.

<a id="q73"></a>

### Q73. [GATE CS 1996] Interpret library relational algebra queries
A library database has:

```text
USERS(User#, UserName, HomeTown)
BOOKS(Book#, BookTitle, AuthorName)
ISSUED(Book#, User#, Date)
```

Explain what each query determines:

```text
a. σ_(User#=6)(π_(User#,BookTitle)((USERS ⋈ ISSUED) ⋈ BOOKS))

b. π_(AuthorName)(BOOKS ⋈ σ_(HomeTown=Delhi)(USERS ⋈ ISSUED))
```

(A) Show all book titles issued by User# 6.  
(B) For users whose hometown is Delhi and who issued a book, show the authors’ names for their issued books.

**Answer: (A) and (B), respectively.**

**Solution:** In (a), joining `USERS`, `ISSUED`, and `BOOKS` connects borrowers to issued titles; selecting `User#=6` and projecting `BookTitle` returns titles issued by user 6. In (b), the selection keeps Delhi users and their issued records; joining `BOOKS` and projecting `AuthorName` returns authors of those books.

<a id="q74"></a>

### Q74. [GATE CS 1998] Identify an invalid relational-algebra transformation
Which query transformation (replacing the left-hand expression by the right-hand expression) is incorrect? `R1` and `R2` are relations; `C1`, `C2` are selection conditions; `A1`, `A2` are attributes of `R1`.

(a) `σ_C1(σ_C2(R1)) → σ_C2(σ_C1(R1))`  
(b) `σ_C1(π_A1(R1)) → π_A1(σ_C1(R1))`  
(c) `σ_C1(R1 ∪ R2) → σ_C1(R1) ∪ σ_C1(R2)`  
(d) `π_A1(σ_C1(R1)) → σ_C1(π_A1(R1))`

(A) a  
(B) b  
(C) c  
(D) d

**Answer: (D) d**

**Solution:** A projection onto `A1` may discard the attribute used by condition `C1`. Then the right-hand side cannot evaluate the selection (or has lost information needed to do so), while the left-hand side applies the condition before projection. Selections commute, and selection distributes over union; transformation (d) is not valid in general.
