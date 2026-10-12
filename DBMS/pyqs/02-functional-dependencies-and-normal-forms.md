# PYQs — Functional Dependencies & Normal Forms

[← All PYQ topics](./README.md) · [DBMS notes](../README.md)

**88 questions** (47 from GATE papers). Try each question before opening its solution.

## Quick Answer Key

| Q | Source | Answer |
| --- | --- | --- |
| [Q1](#q1) | GATE CS 2012 | (C) Every relation in BCNF is also in 3NF |
| [Q2](#q2) | GATE CS 2013 | (A) In 1NF, but not in 2NF |
| [Q3](#q3) | GATE CS 2011 | (A) `BankAccount_Num` is a candidate key |
| [Q4](#q4) | GATE CS 2009 | (A) The schema is in BCNF |
| [Q5](#q5) | UGC-NET CS 2017 Dec 2 | (D) Normal forms |
| [Q6](#q6) | UGC-NET CS 2015 Dec-II | (A) Indexes |
| [Q7](#q7) | ISRO 2017 | (B) In 3NF, but not in BCNF |
| [Q8](#q8) | UGC-NET CS 2015 Dec-II | (B) Matching (2) |
| [Q9](#q9) | UGC-NET CS 2015 Dec-II | (C) `SELECT * FROM customers WHERE city LIKE '%GAR%';` |
| [Q10](#q10) | ISRO 2013 | (B) Second normal form |
| [Q11](#q11) | UGC-NET CS 2016 July-III | (D) Only D2 |
| [Q12](#q12) | UGC-NET CS 2016 July-II | (C) Entity integrity |
| [Q13](#q13) | UGC-NET CS 2016 Aug-III | (D) Matching (4) |
| [Q14](#q14) | ISRO 2014 | (B) `{x}` and `{a,b}` |
| [Q15](#q15) | UGC-NET CS 2016 Aug-III | (B) I and IV only |
| [Q16](#q16) | ISRO 2014 | (A) Preserves dependencies but cannot perform a lossless join |
| [Q17](#q17) | UGC-NET CS 2016 Aug-II | (B) `SELECT A, COUNT(*) FROM R;` |
| [Q18](#q18) | UGC-NET CS 2016 Aug-II | (B) DML |
| [Q19](#q19) | ISRO 2015 | (B) `EC` |
| [Q20](#q20) | UGC-NET CS 2017 Jan-III | (A) 1NF but not 2NF |
| [Q21](#q21) | UGC-NET CS 2017 Jan-II | (A) Dependency preserving but not lossless join |
| [Q22](#q22) | UGC-NET CS 2017 Jan-II | (B) 3, 20 |
| [Q23](#q23) | UGC-NET CS 2017 Nov-III | (A) Dependency preserving and lossless join |
| [Q24](#q24) | UGC-NET CS 2017 Nov-III | (B) Second normal form |
| [Q25](#q25) | UGC-NET CS 2015 Jun-III | (A) (GFG-marked; technically, no option is correct because (A) desc… |
| [Q26](#q26) | UGC-NET CS 2018 July-II | (A) 1NF but not 2NF |
| [Q27](#q27) | ISRO 2007 | (D) Two mutually exclusive foreign keys |
| [Q28](#q28) | UGC-NET CS 2014 Dec-III | (B) `ABCD`, `E` |
| [Q29](#q29) | GFG practice | (B) 2NF |
| [Q30](#q30) | UGC-NET CS 2018 July-II | (A) 1NF |
| [Q31](#q31) | GATE CS 2021 Set 1 | (A) 820 |
| [Q32](#q32) | GATE CS 2013 | (B) 4 |
| [Q33](#q33) | GATE CS 2021 Set 2 | (A), (C), and (D) |
| [Q34](#q34) | GATE CS 2021 Set 2 | (D) Both S1 and S2 are false |
| [Q35](#q35) | GATE CS 2020 | (A) It has a nontrivial FD `X → A` where `X` is not a superkey and … |
| [Q36](#q36) | ISRO 2011 | (C) Object-oriented DBMS |
| [Q37](#q37) | ISRO 2018 | (C) Both (A) and (B) |
| [Q38](#q38) | ISRO 2018 | (A) First normal form but not second normal form |
| [Q39](#q39) | UGC-NET CS 2014 Dec-III | (A) Every binary relation is never in BCNF. |
| [Q40](#q40) | UGC-NET CS 2014 Dec-II | (B) Third normal form |
| [Q41](#q41) | UGC-NET CS 2015 Jun-III | (B) Lossless, dependency-preserving decomposition into BCNF is alwa… |
| [Q42](#q42) | ISRO 2009 | (B) Referential integrity |
| [Q43](#q43) | UGC-NET CS 2015 Dec-III | (A) (a) |
| [Q44](#q44) | UGC-NET CS 2015 Dec-III | (A) 5 |
| [Q45](#q45) | ISRO CS 2011 | (B) Second Normal Form |
| [Q46](#q46) | GATE CS 2004 | (D) Names of girl students with more marks than all the boy students |
| [Q47](#q47) | GATE CS 2001 | (C) — official GATE key |
| [Q48](#q48) | GATE CS 2001 | (C) `AB→C, C→AD` |
| [Q49](#q49) | GATE CS 2001 | (C) `σ_(A=a)(r) ⋈ s` |
| [Q50](#q50) | GATE CS 2001 | (D) List all vertices reachable from a given vertex |
| [Q51](#q51) | GATE CS 2001 | (C) Dependency-preserving but not lossless join |
| [Q52](#q52) | GATE CS 2002 | (C) `B` does not functionally determine `C` |
| [Q53](#q53) | GATE CS 2002 | (C) BCNF definition |
| [Q54](#q54) | GATE CS 2002 | (A) Zero |
| [Q55](#q55) | GATE CS 2003 | (D) None of the above |
| [Q56](#q56) | GATE CS 2001 | (C) A tuple `(z,w)` with `w < x` is deleted |
| [Q57](#q57) | GATE CS 2004 | (B) 3NF |
| [Q58](#q58) | GATE CS 2004 | (B) 2 |
| [Q59](#q59) | GATE CS 2005 | (D) `AEH, BEH, DEH` |
| [Q60](#q60) | GATE CS 2005 | (C) `r ⊂ s` |
| [Q61](#q61) | GATE CS 2005 | (C) A lossless, dependency-preserving decomposition into BCNF is al… |
| [Q62](#q62) | GATE CS 2014 Set 2 | (B) 19 |
| [Q63](#q63) | GATE CS 2014 Set 2 | (D) 8 |
| [Q64](#q64) | GATE CS Mock 2017 | (C) A logical unit of work in one database session |
| [Q65](#q65) | GATE CS Mock 2017 | (A) Intended choice: a string range from the A boundary to the D bo… |
| [Q66](#q66) | GATE CS 2018 | (B) Schema II |
| [Q67](#q67) | GATE CS 2016 Set 1 | (B) `VWXZ` |
| [Q68](#q68) | GATE IT 2005 | (A) 1NF |
| [Q69](#q69) | GATE IT 2005 | (C) `Lodging` |
| [Q70](#q70) | GATE CS 2014 Set 1 | (A) S1 is true and S2 is false |
| [Q71](#q71) | GATE CS 2014 Set 1 | (B) `{E,F,H}` |
| [Q72](#q72) | GATE CS 2008 | (C) Book is in 2NF and Collection is in 3NF |
| [Q73](#q73) | GATE IT 2008 | (D) Not in 2NF |
| [Q74](#q74) | GATE CS Mock 2018 | (A) 2, 2, and 1, respectively |
| [Q75](#q75) | GATE CS Mock 2018 | (B) The expression that removes people with any unsuitable frequent… |
| [Q76](#q76) | GATE CS Mock 2018 | (B) `B→D` |
| [Q77](#q77) | GATE CS 1997 | (A) In 1NF but not 2NF |
| [Q78](#q78) | GATE CS 1998 | (a) BCNF; (b) 2NF, assuming only the stated FDs and the changed key |
| [Q79](#q79) | GATE CS 1998 | (D) 3NF |
| [Q80](#q80) | GATE CS 1999 | (D) In both 2NF and 3NF |
| [Q81](#q81) | GATE CS 1999 | (B) `EC` |
| [Q82](#q82) | GATE IT 2004 | (D) 6 rows and 5 columns |
| [Q83](#q83) | GATE IT 2004 | (B) 3 |
| [Q84](#q84) | GATE CS 2015 Set 3 | (C) `{P,S}→{S}` |
| [Q85](#q85) | GATE CS 2015 Set 1 | (C) 4 |
| [Q86](#q86) | GATE CS 2000 | (B) `YZ→X` and `Y→Z` |
| [Q87](#q87) | GATE CS 2000 | (C) The sum of all employees’ salaries |
| [Q88](#q88) | GATE CS 2000 | (B) `EC` |

---

## Questions and Solutions

<a id="q1"></a>

### Q1. [GATE CS 2012] BCNF and 3NF
Which statement is true?

(A) Every relation in 3NF is also in BCNF  
(B) A relation is in 3NF if every non-prime attribute is fully functionally dependent on every key  
(C) Every relation in BCNF is also in 3NF  
(D) No relation can be in both BCNF and 3NF

**Answer: (C) Every relation in BCNF is also in 3NF**

**Solution:**
1. BCNF requires every nontrivial FD determinant to be a superkey.
2. This implies the weaker 3NF condition, which also allows a prime attribute on the right side. So BCNF implies 3NF, but not conversely.

<a id="q2"></a>

### Q2. [GATE CS 2013] Normal form of a relation with multiple candidate keys
For `R(ABCDEFGH)`, let `F = {CH → G, A → BC, B → CHF, E → A, F → EG}`, and suppose these are exactly the FDs that hold (together with their implications). The relation has atomic values. Which is true?

(A) In 1NF, but not in 2NF  
(B) In 2NF, but not in 3NF  
(C) In 3NF, but not in BCNF  
(D) In BCNF

**Answer: (A) In 1NF, but not in 2NF**

**Solution:**
1. `D` never appears on the right side of an FD, so every key must contain `D`.
2. `A+`, `B+`, `E+`, and `F+` each contain every attribute other than `D`; thus `AD`, `BD`, `ED`, and `FD` are candidate keys.
3. `A → BC`, `B → CHF`, and `F → EG` determine non-prime attributes from a proper subset of these composite keys. That violates 2NF. Atomic values give 1NF.

<a id="q3"></a>

### Q3. [GATE CS 2011] Identify the incorrect key statement
A student table has one record per registered student and these attributes:
- `Registration_Num`: unique for each registered student.
- `UID`: unique nationally for each citizen.
- `BankAccount_Num`: primary account number; a student may have several accounts, and accounts may be joint.
- `Name`: student name.
- `Hostel_Room`: hostel room number.

Which statement is incorrect?

(A) `BankAccount_Num` is a candidate key  
(B) `Registration_Num` can be a primary key  
(C) `UID` is a candidate key if all students are from the same country  
(D) If `S` is a superkey and `S ∩ UID` is empty, then `S ∪ UID` is also a superkey

**Answer: (A) `BankAccount_Num` is a candidate key**

**Solution:**
1. A candidate key must uniquely identify every row. Joint account holders can have the same primary account number, so this attribute is not guaranteed unique.
2. Registration numbers are unique by definition. A nationally unique UID is also unique when the students are citizens of the same country.
3. Adding attributes to a superkey preserves the superkey property, so (D) is true.

<a id="q4"></a>

### Q4. [GATE CS 2009] Normal form of supplier, parts, and catalog schemas
Consider:

```text
Suppliers(sid: integer, sname: string, city: string, street: string)
Parts(pid: integer, pname: string, color: string)
Catalog(sid: integer, pid: integer, cost: real)
```

In `Suppliers`, each supplier and each street within a city has a unique name, and `(sname, city)` is a candidate key. No other FDs hold except those implied by primary and candidate keys. Which statement is true?

(A) The schema is in BCNF  
(B) It is in 3NF but not BCNF  
(C) It is in 2NF but not 3NF  
(D) It is not in 2NF

**Answer: (A) The schema is in BCNF**

**Solution:**
1. By the stated uniqueness constraints, each relation's key attributes determine the remaining attributes: for example, `sid` and `(sname, city)` determine the supplier row, and `pid` determines a parts row.
2. The catalog row is identified by its supplier-part pair; there are no additional non-key determinants specified.
3. Thus all nontrivial determinants are keys (or superkeys), satisfying BCNF under the stated key assumptions.

<a id="q5"></a>

### Q5. [UGC-NET CS 2017 Dec 2] Preventing modification anomalies
In an RDBMS, different classes of relations are created using which technique to prevent modification anomalies?

(A) Functional dependencies  
(B) Data integrity  
(C) Referential integrity  
(D) Normal forms

**Answer: (D) Normal forms**

**Solution:** Normalization organizes relations into normal forms to reduce redundancy and prevent insertion, update, and deletion anomalies. Functional dependencies describe constraints; referential integrity concerns references between tables.

<a id="q6"></a>

### Q6. [UGC-NET CS 2015 Dec-II] Data that improves database access
Data that improves the performance and accessibility of a database is called:

(A) Indexes  
(B) User data  
(C) Application metadata  
(D) Data dictionary

**Answer: (A) Indexes**

**Solution:** An index is an auxiliary lookup structure that helps the DBMS locate rows more quickly. A data dictionary stores metadata; it is not the lookup accelerator meant here.

<a id="q7"></a>

### Q7. [ISRO 2017] Normal form of the Faculty relation
Consider the following relation:

| facName | dept | office | rank | dateHired |
|---|---|---|---|---:|
| Ravi | Art | A101 | Professor | 1975 |
| Murali | Math | M201 | Assistant | 2000 |
| Narayanan | Art | A101 | Associate | 1992 |
| Lakshmi | Math | M201 | Professor | 1982 |
| Mohan | CSC | C101 | Professor | 1980 |
| Lakshmi | Math | M201 | Professor | 1982 |
| Sreeni | Math | M203 | Associate | 1990 |
| Tanuja | CSC | C101 | Instructor | 2001 |
| Ganesh | CSC | C105 | Associate | 1995 |

Assume no faculty member within one department has the same name, and each faculty member has one office, identified by `office`. Which is true?

(A) Not in 3NF, but in BCNF  
(B) In 3NF, but not in BCNF  
(C) In both 3NF and BCNF  
(D) In neither 3NF nor BCNF

**Answer: (B) In 3NF, but not in BCNF**

**Solution:**
1. The stated dependencies include `facName → dept, office, rank, dateHired` and `office → dept`.
2. `office` is not a superkey, so `office → dept` violates BCNF.
3. The department attribute is prime under the candidate-key assumptions for this question (it participates in a candidate key such as `{dept, rank}`), so that FD does not violate 3NF. The key determinant `facName` satisfies both forms.

<a id="q8"></a>

### Q8. [UGC-NET CS 2015 Dec-II] Match database terms to functions
Match each term to its function:

1. Normalization  
2. Data dictionary  
3. Referential integrity  
4. External schema

Functions: reduces redundancy; stores metadata describing database structure; enforces valid primary-key/foreign-key references; defines views for particular users.

(A) Matching (1)  
(B) Matching (2)  
(C) Matching (3)  
(D) Matching (4)

**Answer: (B) Matching (2)**

**Solution:** The correct term-to-function associations are: normalization—reduces redundancy; data dictionary—describes database structure; referential integrity—validates references; external schema—user-specific view. Together these are matching (2). The source embeds the matching choices in an image; the associations are transcribed here.

<a id="q9"></a>

### Q9. [UGC-NET CS 2015 Dec-II] Find a substring in SQL
A `CUSTOMERS` table has a `CITY` column containing Indian city names in uppercase. Which SQL finds city names containing `GAR` anywhere?

(A) `SELECT * FROM customers WHERE city = '%GAR%';`  
(B) `SELECT * FROM customers WHERE city = '$GAR$';`  
(C) `SELECT * FROM customers WHERE city LIKE '%GAR%';`  
(D) `SELECT * FROM customers WHERE city AS '%GAR';`

**Answer: (C) `SELECT * FROM customers WHERE city LIKE '%GAR%';`**

**Solution:** In SQL `LIKE`, `%` matches any sequence of characters. Putting `%` on both sides of `GAR` finds it anywhere within the city name; `=` compares a literal string.

<a id="q10"></a>

### Q10. [ISRO 2013] Highest normal form of the BOOK relation
A `BOOK` relation has these FDs:

```text
ISBN → Title
ISBN → Publisher
Publisher → Address
```

Determine its highest normal form.

(A) First normal form  
(B) Second normal form  
(C) Third normal form  
(D) BCNF

**Answer: (B) Second normal form**

**Solution:**
1. `ISBN` determines all listed attributes, so it is a single-attribute candidate key.
2. There can be no partial dependency on a proper subset of a one-attribute key, so the relation is in 2NF (assuming atomic values).
3. `Publisher → Address` has a non-superkey determinant and a non-prime right-side attribute, violating 3NF. Hence the highest form is 2NF.

<a id="q11"></a>

### Q11. [UGC-NET CS 2016 July-III] Lossless decompositions
Which statement is true?

`D1`: Decomposing `R(A,B,C)` into `R1(A,B)` and `R2(A,C)` is always lossless.  
`D2`: For `R(A,B,C,D,E)` with `AD → B`, `C → DE`, `B → AE`, and `AE → C`, decomposing into `R1(A,B,D)` and `R2(A,C,D,E)` is lossless.

(A) Both D1 and D2  
(B) Neither D1 nor D2  
(C) Only D1  
(D) Only D2

**Answer: (D) Only D2**

**Solution:**
1. In `D1`, the common attributes are only `{A}`. No FD is provided that makes `A` determine either entire component, so losslessness is not guaranteed.
2. In `D2`, `AD+ = ABCDE`: `AD → B`, `B → AE`, then `AE → C`, and `C → DE`. Thus `AD` is a key of the original relation.
3. The common attributes of the components are `{A,D}`, which determine `R1`; therefore the binary decomposition is lossless.

<a id="q12"></a>

### Q12. [UGC-NET CS 2016 July-II] Key attributes and NULL
In an RDBMS, what is the constraint that a key attribute (column) may not be NULL called?

(A) Referential integrity  
(B) Multivalued dependency  
(C) Entity integrity  
(D) Functional dependency

**Answer: (C) Entity integrity**

**Solution:** Entity integrity requires primary-key values to be non-NULL so each row can be identified. Referential integrity applies to references between relations; an FD states a determination between attributes.

<a id="q13"></a>

### Q13. [UGC-NET CS 2016 Aug-III] Match ER-model terms and descriptions
Match the following ER-model concepts to their definitions:

1. Generalization  
2. Aggregation  
3. Mapping cardinalities  
4. Specialization

Definitions: combining lower-level entity sets into a higher-level set; treating a relationship and its participating entity sets as a higher-level entity; specifying how many entities may be associated through a relationship; forming lower-level entity sets from a higher-level entity set.

(A) Matching (1)  
(B) Matching (2)  
(C) Matching (3)  
(D) Matching (4)

**Answer: (D) Matching (4)**

**Solution:** Specialization creates lower-level entity sets from a higher-level entity set; generalization is the reverse. Aggregation treats a relationship as a higher-level abstraction, while mapping cardinalities describe association counts. The four concepts and definitions are transcribed from the embedded figure.

<a id="q14"></a>

### Q14. [ISRO 2014] Find candidate keys from listed superkeys
An entity has attributes `x, y, z, a, b, c`. The following are superkeys: `{x}`, `{x,y}`, `{a,b}`, `{a,b,c}`, and `{x,y,z}`. Which are candidate keys?

(A) `{x,y}` and `{a,b}`  
(B) `{x}` and `{a,b}`  
(C) `{x,y,z}` and `{a,b,c}`  
(D) `{z}` and `{c}`

**Answer: (B) `{x}` and `{a,b}`**

**Solution:** A candidate key is a minimal superkey. `{x}` has no proper subset, and `{a,b}` is listed as a superkey with neither singleton identified as a superkey. The remaining listed superkeys contain one of these and are not minimal.

<a id="q15"></a>

### Q15. [UGC-NET CS 2016 Aug-III] OODBMS advantages
Which statements describe advantages of an object-oriented DBMS (OODBMS) over a relational database?

I. It avoids the impedance mismatch problem.  
II. It avoids the phantom problem.  
III. It provides higher-performance concurrency control than most relational databases.  
IV. It gives faster access to individual data objects once they have been read from disk.

(A) II and III only  
(B) I and IV only  
(C) I, II, and III only  
(D) I, III, and IV only

**Answer: (B) I and IV only**

**Solution:** OODBMS object representations align with object-oriented programs, reducing impedance mismatch; object references can also make subsequent in-memory object access fast. OODBMS does not inherently eliminate phantom anomalies or guarantee better concurrency control, so II and III are not general advantages.

<a id="q16"></a>

### Q16. [ISRO 2014] Dependency preservation and lossless join
For `R(A,B,C,D)` with FDs `A → B` and `C → D`, decompose into `R1(A,B)` and `R2(C,D)`. Which is true?

(A) Preserves dependencies but cannot perform a lossless join  
(B) Preserves dependencies and performs a lossless join  
(C) Does not preserve dependencies and cannot perform a lossless join  
(D) Does not preserve dependencies but performs a lossless join

**Answer: (A) Preserves dependencies but cannot perform a lossless join**

**Solution:**
1. Each FD is wholly contained in one component, so both dependencies are preserved.
2. `R1` and `R2` have no common attributes. Joining them forms combinations of their rows and cannot in general reconstruct the original relation without spurious tuples; therefore it is not guaranteed lossless.

<a id="q17"></a>

### Q17. [UGC-NET CS 2016 Aug-II] Illegal aggregate query
Given a table `R(A,B)`, which SQL query is illegal?

(A) `SELECT A FROM R;`  
(B) `SELECT A, COUNT(*) FROM R;`  
(C) `SELECT A, COUNT(*) FROM R GROUP BY A;`  
(D) `SELECT A, B, COUNT(*) FROM R GROUP BY A, B;`

**Answer: (B) `SELECT A, COUNT(*) FROM R;`**

**Solution:** `COUNT(*)` aggregates rows, but (B) also selects ungrouped `A`. Standard SQL requires every selected non-aggregate column to appear in `GROUP BY`. The other aggregate queries group by their non-aggregate columns.

<a id="q18"></a>

### Q18. [UGC-NET CS 2016 Aug-II] Language for accessing data
DBMS provides the facility of accessing data from a database through:

(A) DDL  
(B) DML  
(C) DBA  
(D) Schema

**Answer: (B) DML**

**Solution:** Data manipulation language includes operations such as `SELECT`, `INSERT`, `UPDATE`, and `DELETE`, through which users retrieve and change stored data. DDL defines database structures.

<a id="q19"></a>

### Q19. [ISRO 2015] Find a key from functional dependencies
Let `R(A,B,C,D,E,F)` have FDs `C → F`, `E → A`, `EC → D`, and `A → B`. Which is a key?

(A) `CD`  
(B) `EC`  
(C) `AE`  
(D) `AC`

**Answer: (B) `EC`**

**Solution:** Compute `(EC)+`: `E → A`, `A → B`, `EC → D`, and `C → F`, giving `{E,C,A,B,D,F}`—all attributes. Neither `E` nor `C` alone determines all attributes, so `EC` is a candidate key.

<a id="q20"></a>

### Q20. [UGC-NET CS 2017 Jan-III] Normal form under two FDs
For `R(A,B,C,D)`, attributes have atomic values and the only FDs (apart from implications) are `A → C` and `B → D`. Which is true?

(A) 1NF but not 2NF  
(B) In both 1NF and 2NF  
(C) 2NF but not 3NF  
(D) In both 2NF and 3NF

**Answer: (A) 1NF but not 2NF**

**Solution:**
1. `(AB)+ = ABCD`, and neither `A` nor `B` alone is a key, so `AB` is the candidate key.
2. `A → C` and `B → D` are dependencies of non-prime attributes on proper subsets of the composite key. This violates 2NF.
3. The atomic-value condition gives 1NF.

<a id="q21"></a>

### Q21. [UGC-NET CS 2017 Jan-II] Decomposition of MNPQ
For `R(M,N,P,Q)` with `M → N` and `P → Q`, decompose into `R1(M,N)` and `R2(P,Q)`. The decomposition is:

(A) Dependency preserving but not lossless join  
(B) Dependency preserving and lossless join  
(C) Lossless join but not dependency preserving  
(D) Neither dependency preserving nor lossless join

**Answer: (A) Dependency preserving but not lossless join**

**Solution:** The two FDs occur directly in the two components, so they are preserved. The components have no common attribute; their join can generate spurious combinations, so it is not lossless in general.

<a id="q22"></a>

### Q22. [UGC-NET CS 2017 Jan-II] Storage for VARCHAR and CHAR
In Oracle, attribute `A VARCHAR(20)` has value `'Ram'` and attribute `B CHAR(20)` has value `'Sita'`. How many character spaces do `A` and `B` use, respectively?

(A) 20, 20  
(B) 3, 20  
(C) 3, 4  
(D) 20, 4

**Answer: (B) 3, 20**

**Solution:** `VARCHAR(20)` stores a variable-length string, so `'Ram'` uses 3 characters. `CHAR(20)` is fixed-length and uses 20 characters, padding the shorter value as needed.

<a id="q23"></a>

### Q23. [UGC-NET CS 2017 Nov-III] Dependency-preserving and lossless decomposition
For `R(A,B,C,D)` with FDs `A → B`, `B → C`, `C → D`, and `D → B`, decompose into `R1(A,B)`, `R2(B,C)`, and `R3(B,D)`. The decomposition is:

(A) Dependency preserving and lossless join  
(B) Lossless join but not dependency preserving  
(C) Dependency preserving but not lossless join  
(D) Neither dependency preserving nor lossless join

**Answer: (A) Dependency preserving and lossless join**

**Solution:**
1. `A → B` is in `R1`, `B → C` in `R2`, and `D → B` in `R3`.
2. From the projected dependencies, `C → B` (via `C → D → B`) and `B → D` (via `B → C → D`) are also available. Together the projections imply the original `C → D`, so the decomposition preserves all FDs.
3. `B` determines all attributes of `R2` and `R3`; successive joins on `B` reconstruct the relation without spurious tuples.

<a id="q24"></a>

### Q24. [UGC-NET CS 2017 Nov-III] Meaning of dependence on a primary key
If every non-key attribute is fully functionally dependent on the primary key, and the relation is in 1NF, the relation is in:

(A) First normal form  
(B) Second normal form  
(C) Third normal form  
(D) Fourth normal form

**Answer: (B) Second normal form**

**Solution:** 2NF requires 1NF and no non-key attribute to depend on only a proper subset of a candidate key. Full functional dependence on the primary key is exactly the needed condition; it does not by itself establish 3NF.

<a id="q25"></a>

### Q25. [UGC-NET CS 2015 Jun-III] A purported reason for 2NF in Vendor Order
Consider `Vendor Order(V_no, V_ord_no, V_name, Qty_sup, unit_price)`. The question says it is in 2NF because:

(A) Non-key attribute `V_name` depends on `V_no`, which is part of a composite key  
(B) Non-key attribute `V_name` depends on `Qty_sup`  
(C) Key attribute `Qty_sup` depends on primary key `unit_price`  
(D) Key attribute `V_ord_no` depends on primary key `unit_price`

**Answer: (A) (GFG-marked; technically, no option is correct because (A) describes a 2NF violation)**

**Solution:**
1. Taking `(V_no, V_ord_no)` as the composite key, `V_no` is a proper subset of that key.
2. A non-key attribute `V_name` depending on `V_no` alone is a partial dependency, which violates 2NF.
3. Thus option (A), despite the question's wording, is evidence that the relation is *not* in 2NF. The other choices do not establish the condition for 2NF.

> Note: GFG marks (A); that dependency is partial and therefore contradicts 2NF.

<a id="q26"></a>

### Q26. [UGC-NET CS 2018 July-II] Normal form of R(a,b,c,d)
For `R(a,b,c,d)`, domains are atomic and the only FDs (and their implications) are `a → c` and `b → d`. The relation is in:

(A) 1NF but not 2NF  
(B) 2NF but not 3NF  
(C) 3NF  
(D) BCNF

**Answer: (A) 1NF but not 2NF**

**Solution:** `(ab)+ = {a,b,c,d}`, and `ab` is a candidate key. `a → c` and `b → d` each determine a non-prime attribute from only part of that composite key, violating 2NF. Atomic domains ensure 1NF.

<a id="q27"></a>

### Q27. [ISRO 2007] When BCNF is not used
BCNF is not used for cases where a relation has:

(A) Two or more candidate keys  
(B) Two candidate keys that are composite  
(C) Overlapping candidate keys  
(D) Two mutually exclusive foreign keys

**Answer: (D) Two mutually exclusive foreign keys**

**Solution:** BCNF is concerned with functional dependencies and candidate-key determinants. Multiple, composite, or overlapping candidate keys can create FD anomalies that BCNF addresses. Foreign-key relationships, including mutually exclusive ones, are not the BCNF condition described here.

<a id="q28"></a>

### Q28. [UGC-NET CS 2014 Dec-III] Attribute closures
Let `R = ABCDE` and `F = {A → B, B → C, AC → D}`. What are the closures of `A` and `E`?

(A) `ABCD`, `∅`  
(B) `ABCD`, `E`  
(C) `∅`, `∅`  
(D) `ABC`, `E`

**Answer: (B) `ABCD`, `E`**

**Solution:** Start with `A`: `A → B`, then `B → C`; now `AC → D`. Thus `A+ = ABCD`. No FD adds anything to `E`, so `E+ = E`.

<a id="q29"></a>

### Q29. [GFG practice] Highest normal form of a chain of FDs
For `R(A,B,C,D,E)` with `F = {A → B, B → C, C → D, D → E}`, find the highest normal form.

(A) 1NF  
(B) 2NF  
(C) 3NF  
(D) BCNF

**Answer: (B) 2NF**

**Solution:** `A+ = ABCDE`, so `A` is the single-attribute candidate key. A one-attribute key cannot have a partial dependency, so the relation is in 2NF. But `B → C` has a non-superkey determinant and non-prime right side, violating 3NF.

<a id="q30"></a>

### Q30. [UGC-NET CS 2018 July-II] Normal form of relations from an ER model
Relations produced from an ER model will always be in:

(A) 1NF  
(B) 2NF  
(C) 3NF  
(D) 4NF

**Answer: (A) 1NF**

**Solution:** Mapping an ER model to relations gives tables whose attribute values are atomic, which guarantees 1NF. The mapping alone does not guarantee higher normal forms.

<a id="q31"></a>

### Q31. [GATE CS 2021 Set 1] Estimate a selection result size
Relation `r(A,B)` has 1200 tuples. `A` is uniformly distributed over integers 6 through 20, and `B` over integers 1 through 20; assume independence. Estimate the number of tuples selected by `σ((A > 10) ∨ (B = 18))(r)`.

(A) 820  
(B) 1200  
(C) 960  
(D) 1000

**Answer: (A) 820**

**Solution:**
1. Values of `A` are 6–20, 15 possibilities; 10 satisfy `A > 10`, so `P(A>10)=10/15=2/3`.
2. `P(B=18)=1/20`. Independence gives intersection probability `(2/3)(1/20)=1/30`.
3. Union probability is `2/3 + 1/20 − 1/30 = 41/60`. Estimated rows: `1200 × 41/60 = 820`.

<a id="q32"></a>

### Q32. [GATE CS 2013] Count candidate keys
Relation `R` has attributes `ABCDEFGH` and exactly the FDs implied by `F = {CH → G, A → BC, B → CFH, E → A, F → EG}`. The values are atomic. How many candidate keys does `R` have?

(A) 3  
(B) 4  
(C) 5  
(D) 6

**Answer: (B) 4**

**Solution:**
1. `D` never occurs on an FD right side, so every candidate key must include `D`.
2. `A+`, `B+`, `E+`, and `F+` each determine all attributes except `D`. Therefore `AD`, `BD`, `ED`, and `FD` are keys.
3. Each is minimal, and no other attribute singleton closure can generate all remaining attributes. There are four candidate keys.

<a id="q33"></a>

### Q33. [GATE CS 2021 Set 2] Infer functional dependencies
On relation `U(P,Q,R,S,T)`, suppose `P → QR` and `RS → T`. Which FDs can be inferred?

(A) `PS → T`  
(B) `R → T`  
(C) `P → R`  
(D) `PS → Q`

**Answer: (A), (C), and (D)**

**Solution:**
1. By decomposition, `P → Q` and `P → R`; hence (C) is true.
2. Since `P → R`, `PS` determines both `R` and `S`, and `RS → T`; hence `PS → T` (A).
3. `P → Q` implies `PS → Q` by augmentation (D).
4. `R` alone does not determine `S`, so (B) does not follow.

<a id="q34"></a>

### Q34. [GATE CS 2021 Set 2] Foreign-key statements
Consider these statements about the relational model:

`S1`: A relation scheme can have at most one foreign key.  
`S2`: A foreign key in a relation scheme `R` cannot be used to refer to tuples of `R`.

Choose the correct answer.

(A) Both S1 and S2 are true  
(B) S1 is true and S2 is false  
(C) S1 is false and S2 is true  
(D) Both S1 and S2 are false

**Answer: (D) Both S1 and S2 are false**

**Solution:** A relation can contain multiple foreign keys. Also, a foreign key can reference a key of the same relation, as in an employee table whose manager ID refers to another employee row.

<a id="q35"></a>

### Q35. [GATE CS 2020] A relation in 3NF but not BCNF
A relational table `R` is in 3NF but not BCNF. Which statement must be true?

(A) It has a nontrivial FD `X → A` where `X` is not a superkey and `A` is prime  
(B) It has a nontrivial FD `X → A` where `X` is not a superkey, `A` is non-prime, and `X` is not a proper subset of any key  
(C) It has a nontrivial FD `X → A` where `X` is not a superkey, `A` is non-prime, and `X` is a proper subset of some key  
(D) A cell in `R` holds a set instead of an atomic value

**Answer: (A) It has a nontrivial FD `X → A` where `X` is not a superkey and `A` is prime**

**Solution:** Since BCNF fails, some nontrivial FD has a determinant that is not a superkey. For the same FD to satisfy 3NF, its right-side attribute must be prime. That is precisely (A).

<a id="q36"></a>

### Q36. [ISRO 2011] DBMS and entity versions
Which type of DBMS provides support for maintaining several versions of the same entity?

(A) Relational DBMS  
(B) Hierarchical DBMS  
(C) Object-oriented DBMS  
(D) Network DBMS

**Answer: (C) Object-oriented DBMS**

**Solution:** Object-oriented DBMSs represent entities as objects and support object-oriented features such as creating and maintaining versions or variants of objects.

<a id="q37"></a>

### Q37. [ISRO 2018] Full functional dependency
A set of attributes `X` is fully functionally dependent on a set of attributes `Y` when:

(A) `X` is functionally dependent on `Y`  
(B) `X` is not functionally dependent on any subset of `Y`  
(C) Both (A) and (B)  
(D) Neither (A) nor (B)

**Answer: (C) Both (A) and (B)**

**Solution:** Full dependency requires `Y → X`, and no proper subset of `Y` may determine `X`. Both conditions are necessary.

<a id="q38"></a>

### Q38. [ISRO 2018] Normal form from partial dependencies
For `R(a,b,c,d)`, domains are atomic, and the only FDs (plus their implications) are `a → c` and `b → d`. Which is true?

(A) First normal form but not second normal form  
(B) Second normal form but not third normal form  
(C) Third normal form  
(D) None of the above

**Answer: (A) First normal form but not second normal form**

**Solution:** `ab` is a candidate key because its closure is `abcd`, while neither `a` nor `b` alone is a key. The dependencies `a → c` and `b → d` are partial dependencies of non-prime attributes on parts of that key, so 2NF fails; atomic domains give 1NF.

<a id="q39"></a>

### Q39. [UGC-NET CS 2014 Dec-III] False statement about normal forms
Which statement is false?

(A) Every binary relation is never in BCNF.  
(B) Every BCNF relation is in 3NF.  
(C) 1NF, 2NF, 3NF, and BCNF are based on functional dependencies.  
(D) A multivalued dependency (MVD) is a special case of a join dependency (JD).

**Answer: (A) Every binary relation is never in BCNF.**

**Solution:** This says a two-attribute relation cannot be in BCNF, which is false: every binary relation is in BCNF. A nontrivial FD between its two attributes makes the determinant a key. The other statements are true.

<a id="q40"></a>

### Q40. [UGC-NET CS 2014 Dec-II] Highest normal form for R(A,B,C,D)
For `R(A,B,C,D)` with `F = {AB → C, AB → D, C → A, D → B}`, determine the highest normal form.

(A) BCNF  
(B) Third normal form  
(C) Second normal form  
(D) First normal form

**Answer: (B) Third normal form**

**Solution:**
1. Candidate keys include `AB`, `BC`, `CD`, and `AD`; thus every attribute is prime.
2. `C → A` and `D → B` have determinants that are not superkeys, so BCNF is violated.
3. Their right-side attributes are prime, so these dependencies satisfy the 3NF alternative. The relation is in 3NF but not BCNF.

<a id="q41"></a>

### Q41. [UGC-NET CS 2015 Jun-III] False statement about normal-form decomposition
Select the false statement.

(A) Lossless, dependency-preserving decomposition into 3NF is always possible.  
(B) Lossless, dependency-preserving decomposition into BCNF is always possible.  
(C) Any relation with two attributes is in BCNF.  
(D) BCNF is stronger than 3NF.

**Answer: (B) Lossless, dependency-preserving decomposition into BCNF is always possible.**

**Solution:** A BCNF decomposition can be made lossless, but it may lose dependency preservation. In contrast, a lossless, dependency-preserving 3NF synthesis is always possible. BCNF is stronger than 3NF, and every two-attribute relation is in BCNF.

<a id="q42"></a>

### Q42. [ISRO 2009] Purpose of a foreign key
The purpose of a foreign key in a table is to ensure:

(A) Null integrity  
(B) Referential integrity  
(C) Domain integrity  
(D) Null and domain integrity

**Answer: (B) Referential integrity**

**Solution:** A foreign-key constraint ensures referenced values match an appropriate key in the referenced relation (subject to NULL rules). This maintains referential integrity.

<a id="q43"></a>

### Q43. [UGC-NET CS 2015 Dec-III] Natural join result
The input relations are:

**R(A,B)**

| A | B |
|---:|---:|
| 1 | 2 |
| 3 | 2 |
| 5 | 6 |
| 7 | 8 |
| 9 | 8 |

**S(B,C)**

| B | C |
|---:|---:|
| 6 | 2 |
| 2 | 4 |
| 8 | 1 |
| 8 | 3 |
| 2 | 5 |

**T(A,C)**

| A | C |
|---:|---:|
| 7 | 1 |
| 1 | 2 |
| 9 | 3 |
| 5 | 4 |
| 3 | 5 |

All joins are natural joins (`⨝`) and `π` denotes projection. Choose the matching result among the image choices:

**(a)**

| A | B | C |
|---:|---:|---:|
| 1 | 2 | 4 |
| 1 | 2 | 5 |
| 3 | 2 | 4 |
| 3 | 2 | 5 |
| 5 | 6 | 2 |
| 7 | 8 | 1 |
| 7 | 8 | 3 |
| 9 | 8 | 1 |
| 9 | 8 | 3 |

**(b)**

| A | B | C |
|---:|---:|---:|
| 1 | 2 | 2 |
| 3 | 2 | 5 |
| 5 | 6 | 4 |
| 7 | 8 | 1 |
| 9 | 8 | 3 |

**(c)**

| A | B | C |
|---:|---:|---:|
| 1 | 6 | 2 |
| 3 | 2 | 5 |
| 5 | 2 | 4 |
| 7 | 8 | 1 |
| 9 | 8 | 3 |

**(d)**

| A | B | C |
|---:|---:|---:|
| 3 | 2 | 5 |
| 7 | 8 | 1 |
| 9 | 8 | 3 |

(A) (a)  
(B) (b)  
(C) (c)  
(D) (d)

**Answer: (A) (a)**

**Solution:** The result in (a) is `R ⨝ S`, joining on common attribute `B`. For each `R` row with `B=2`, it pairs with both `S` rows having `B=2`; rows with `B=6` pair with the `S` row `(6,2)`, and rows with `B=8` pair with both rows having `B=8`. These nine combinations are exactly table (a). The original image carries the expression/diagram; the input text does not preserve an explicit algebra expression, so the image tables are transcribed and the marked matching is shown.

<a id="q44"></a>

### Q44. [UGC-NET CS 2015 Dec-III] Maximum rows allowed by SQL constraints
Consider the table definition:

```sql
CREATE TABLE test (
    one INTEGER,
    two INTEGER,
    PRIMARY KEY (one),
    UNIQUE (two),
    CHECK (one >= 1 AND = 1 AND <= 5)
);
```

How many records at most can this table contain?

(A) 5  
(B) 10  
(C) 15  
(D) 50

**Answer: (A) 5**

**Solution:** Interpreting the malformed check expression as the intended condition `1 <= one AND one <= 5`, the primary-key value `one` can take only five distinct integer values: 1 through 5. Because `one` is unique and non-NULL as a primary key, at most five rows can be stored. `two` being unique cannot increase this maximum.

<a id="q45"></a>

### Q45. [ISRO CS 2011] Full functional dependency and normal form
Which normal form is based on the concept of “full functional dependency”?

(A) First Normal Form  
(B) Second Normal Form  
(C) Third Normal Form  
(D) Fourth Normal Form

**Answer: (B) Second Normal Form**

**Solution:**
1. A non-prime attribute is fully dependent on a candidate key when it depends on the whole key, not a proper subset.
2. Second Normal Form (2NF) rules out partial dependencies of non-prime attributes on a candidate key.

<a id="q46"></a>

### Q46. [GATE CS 2004] Relational algebra and girls who outperform all boys
Consider `Student(name, sex, marks)`, where `name` is the primary key. The class contains at least one boy and one girl. What does the relational-algebra expression below produce? Here `ρ` is rename, `σ` is selection, and `π` is projection.

```text
π_name(ρ_sex=female(Student))
− π_name(σ_(sex=female ∧ x=male ∧ marks≤m)
        (Student × ρ_(n,x,m)(Student)))
```

The condition pairs a student `(name, sex, marks)` with a renamed student `(n, x, m)`.

(A) Names of girl students with the highest marks  
(B) Names of girl students with more marks than some boy student  
(C) Names of girl students with marks not less than some boy students  
(D) Names of girl students with more marks than all the boy students

**Answer: (D) Names of girl students with more marks than all the boy students**

**Solution:**
1. The first projection lists every girl's name.
2. The second lists girls for which there exists a boy with marks at least as high (`marks ≤ m`).
3. Subtracting removes every girl who fails to beat at least one boy. The remaining girls scored more than every boy.

<a id="q47"></a>

### Q47. [GATE CS 2001] Unsafe tuple relational-calculus expression
Which of the following tuple relational-calculus expressions is not safe? The original options are shown in tuple-calculus notation:

(A) `{t | ∃u ∈ R1 (t[A] = u[A]) ∧ ¬∃s ∈ R2 (t[A] = s[A])}`  
(B) `{t | ∀u ∈ R1 (u[A] = "x" ⇒ ∃s ∈ R2 (t[A] = s[A] ∧ s[A] = u[A]))}`  
(C) `{t | ¬(t ∈ R1)}`  
(D) `{t | ∃u ∈ R1 (t[A] = u[A]) ∧ ∃s ∈ R2 (t[A] = s[A])}`

**Answer: (C) — official GATE key** (technically (B) is also unsafe)

**Solution:**
1. Safety requires a finite result whose values come from the database.
2. In (C), every tuple **not** in `R1` qualifies — infinitely many → unsafe. This is the official answer.
3. (A) and (D) bind `t[A]` to values from finite relations → safe.
4. Subtle point: in (B), if `R1` has no tuple with `A = "x"`, the `∀ … ⇒ …` is vacuously true for every `t`, so (B) can also be unbounded.

> Note: Official key and GFG mark (C). Choose (C) in the exam; (B) is a known technicality.

<a id="q48"></a>

### Q48. [GATE CS 2001] Lossless, dependency-preserving BCNF decomposition
For `R(A,B,C,D)`, which FD set does **not** have a lossless-join, dependency-preserving BCNF decomposition?

(A) `A→B, B→CD`  
(B) `A→B, B→C, C→D`  
(C) `AB→C, C→AD`  
(D) `A→BCD`

**Answer: (C) `AB→C, C→AD`**

**Solution:**
1. In (C), `AB` is a candidate key, and `BC` is another: from `C→A,D`, `BC` determines all attributes. But `C→D` violates 3NF because `C` is not a superkey and `D` is non-prime.
2. A BCNF decomposition must split on the `C`-based dependency. It can preserve `C→AD`, but no resulting component contains both `A,B,C`; thus `AB→C` is not preserved by the projected dependencies.
3. The other three sets can be decomposed along their violating FDs while retaining the original dependencies and obtaining a lossless join.

<a id="q49"></a>

### Q49. [GATE CS 2001] Pushing a selection through a natural join
Let `r` and `s` have schemas `R` and `S`, and let `A` be an attribute of `R`. Which expression is always equal to `σ_(A=a)(r ⋈ s)`? The options in the figure are transcribed below.

(A) `σ_(A=a)(r)`  
(B) `r`  
(C) `σ_(A=a)(r) ⋈ s`  
(D) None of the above

**Answer: (C) `σ_(A=a)(r) ⋈ s`**

**Solution:**
1. The condition uses only attribute `A`, which belongs to `r`.
2. Filtering `r` by `A=a` before joining removes only tuples that could not appear in the selected join result.
3. Therefore the selection can be pushed to the `r` side without changing the result.

<a id="q50"></a>

### Q50. [GATE CS 2001] Reachability in relational algebra
Suppose the graph's adjacency relation is stored in `Adj(X,Y)`. Which query cannot be expressed by a relational-algebra expression of constant length?

(A) List all vertices adjacent to a given vertex.  
(B) List all vertices with self-loops.  
(C) List all vertices belonging to cycles of fewer than three vertices.  
(D) List all vertices reachable from a given vertex.

**Answer: (D) List all vertices reachable from a given vertex**

**Solution:**
1. (A) is one selection/projection; (B) tests `X=Y`.
2. (C) needs only self-loops and two-edge cycles, expressible with a fixed number of joins.
3. Reachability may require paths of arbitrary length. Ordinary relational algebra has no recursion/iteration, so no single fixed-length expression handles paths of every length.

<a id="q51"></a>

### Q51. [GATE CS 2001] Lossless join versus dependency preservation
For `R(A,B,C,D)` with FDs `A→B` and `C→D`, consider decomposition into `R1(A,B)` and `R2(C,D)`. Is it dependency-preserving and lossless?

(A) Dependency-preserving and lossless join  
(B) Lossless join but not dependency-preserving  
(C) Dependency-preserving but not lossless join  
(D) Neither dependency-preserving nor lossless join

**Answer: (C) Dependency-preserving but not lossless join**

**Solution:**
1. Each FD appears wholly in one component: `A→B` in `R1`, and `C→D` in `R2`. Thus dependencies are preserved.
2. The components have no common attributes, so their natural join is a Cartesian product. It can combine unrelated `AB` and `CD` pairs, creating spurious tuples; the decomposition is lossy.

<a id="q52"></a>

### Q52. [GATE CS 2002] What an instance can establish about FDs
Given this instance of `R(A,B,C)`, which statement can we conclude?

| A | B | C |
|---:|---:|---:|
| 1 | 1 | 1 |
| 1 | 1 | 0 |
| 2 | 3 | 2 |
| 2 | 3 | 2 |

(A) `A→B` and `B→C`  
(B) `A→B` and not `B→C`  
(C) `B` does not functionally determine `C`  
(D) Neither `A→B` nor `B→C`

**Answer: (C) `B` does not functionally determine `C`**

**Solution:**
1. The two rows with `B=1` have different `C` values (1 and 0), directly disproving `B→C`.
2. Even though `A→B` happens to hold in these rows, one finite instance cannot establish that an FD must hold in every valid future instance.
3. Thus (A), (B), and (D) claim more than can be concluded; only (C) is certain.

<a id="q53"></a>

### Q53. [GATE CS 2002] Identifying BCNF versus 3NF decompositions
A relation `R` is decomposed using FDs `F`, and a relation `S` using FDs `G`. One decomposition is definitely BCNF and the other definitely 3NF, but we do not know which is which. Assume `F+` and `G+` are available. Which test guarantees identification?

(A) Dependency preservation  
(B) Lossless join  
(C) BCNF definition  
(D) 3NF definition

**Answer: (C) BCNF definition**

**Solution:**
1. A BCNF decomposition is also in 3NF, so testing only 3NF cannot distinguish the two.
2. Both may be lossless and dependency-preserving, so those tests do not distinguish them either.
3. Apply the BCNF condition directly: for every non-trivial projected FD `X→Y`, `X` must be a superkey. The one satisfying it is the BCNF decomposition; the other is only 3NF.

> Note: GFG marks (B), but its explanation gives (C). Lossless join cannot distinguish them; the BCNF definition can, so (C) is the correct test.

<a id="q54"></a>

### Q54. [GATE CS 2002] Redundancy after BCNF decomposition
A relation `R` with FD set `F` is decomposed into BCNF. What is the resulting redundancy arising from functional dependencies?

(A) Zero  
(B) More than zero but less than that of an equivalent 3NF decomposition  
(C) Proportional to the size of `F+`  
(D) Indeterminate

**Answer: (A) Zero**

**Solution:**
1. BCNF eliminates redundancy caused by non-trivial functional dependencies: every determinant in each resulting relation is a superkey.
2. Other kinds of redundancy (not caused by FDs) are outside what BCNF guarantees.

<a id="q55"></a>

### Q55. [GATE CS 2003] Normal form of a relation with birth-date dependencies
The following FDs hold:

```text
Date_of_Birth → Age       Age → Eligibility
Name → Roll_number        Roll_number → Name
Course_number → Course_name
Course_number → Instructor
(Roll_number, Course_number) → Grade
```

What is the highest normal form of `R(Roll_number, Name, Date_of_birth, Age)`?

(A) 2NF but not 3NF  
(B) 3NF but not BCNF  
(C) BCNF  
(D) None of the above

**Answer: (D) None of the above**

**Solution:**
1. The candidate keys for this four-attribute relation are `{Date_of_birth, Roll_number}` and `{Date_of_birth, Name}`: date of birth is not determined by any FD, and `Name` and `Roll_number` determine each other.
2. `Date_of_Birth→Age` makes the non-prime attribute `Age` depend on a proper subset of either candidate key.
3. This partial dependency violates 2NF, so the relation is not in any of (A)–(C).

<a id="q56"></a>

### Q56. [GATE CS 2001] Self-referencing foreign key and cascading deletes
A relation `geq(lb, ub)` represents pairs `(x,y)` only when `y ≥ x`. `lb` is the primary key and `ub` is a foreign key referencing `geq(lb)` with `ON DELETE CASCADE`. Which event is possible when tuple `(x,y)` is deleted?

(A) A tuple `(z,w)` with `z > y` is deleted  
(B) A tuple `(z,w)` with `z > x` is deleted  
(C) A tuple `(z,w)` with `w < x` is deleted  
(D) The deletion of `(x,y)` is prohibited

**Answer: (C) A tuple `(z,w)` with `w < x` is deleted**

**Solution:**
1. Rows whose `ub=x` reference the deleted row's primary-key value `lb=x`; cascading deletion removes them. Such a row `(z,x)` has `z≤x`.
2. If a deleted child has `lb=z`, its own children with `ub=z` are also deleted. For `z<x`, those rows have `w=z<x`.
3. Hence a cascade can reach a tuple whose upper bound is below `x`; the other choices do not describe this downward chain.

<a id="q57"></a>

### Q57. [GATE CS 2004] Highest normal form of student-performance relation
`StudentPerformance(name, courseNo, rollNo, grade)` has these FDs:

```text
(name, courseNo) → grade
(rollNo, courseNo) → grade
name → rollNo
rollNo → name
```

What is the highest normal form?

(A) 2NF  
(B) 3NF  
(C) BCNF  
(D) 4NF

**Answer: (B) 3NF**

**Solution:**
1. Candidate keys are `{name, courseNo}` and `{rollNo, courseNo}`. Thus `name` and `rollNo` are both prime attributes.
2. Each grade FD has a candidate key on its left. The other two FDs have a non-superkey determinant, so BCNF fails.
3. Their right sides are prime attributes, so the 3NF condition holds. Therefore 3NF is the highest listed form.

<a id="q58"></a>

### Q58. [GATE CS 2004] Foreign-key integrity and relational algebra
Let `R1(A,B,C)` and `R2(D,E)` be schemas with their primary keys as indicated in the original question. `C` is a foreign key in `R1` referencing the primary key `D` of `R2`, and referential integrity is not violated. Which expression must return the empty relation?

1. `π_D(R2) − π_C(R1)`  
2. `π_C(R1) − π_D(R2)`  
3. `π_D(R1 ⋈_(predicate on C,D) R2)` (the subscripts in the original image are too blurred to read exactly)  
4. `π_C(R1 ⋈_(C=D) R2)`

> Note: Original figure not reproduced. Option 3’s join predicate is illegible in the source image; its readable structure is a projection of a join.

(A) 1  
(B) 2  
(C) 3  
(D) 4

**Answer: (B) 2**

**Solution:**
1. Referential integrity requires every foreign-key value in `R1.C` to appear as a referenced key in `R2.D`.
2. Therefore `π_C(R1) ⊆ π_D(R2)`, so subtracting the latter set from the former, `π_C(R1)−π_D(R2)`, is empty.
3. The reverse difference need not be empty: `R2` may contain keys unused by `R1`.

<a id="q59"></a>

### Q59. [GATE CS 2005] Candidate keys under functional dependencies
For `R(A,B,C,D,E,H)`, the FDs are `A→B`, `BC→D`, `E→C`, and `D→A`. What are the candidate keys?

(A) `AE, BE`  
(B) `AE, BE, DE`  
(C) `AEH, BEH, BCH`  
(D) `AEH, BEH, DEH`

**Answer: (D) `AEH, BEH, DEH`**

**Solution:**
1. `E` and `H` never occur on any FD right side, so every key must contain both.
2. `AEH+`: `A→B`, then `BC→D`, and `E→C`; this yields all six attributes.
3. `BEH+`: `E→C`, then `BC→D`, `D→A`, and `A→B`. `DEH+`: `D→A→B`, and `E→C`; again all attributes.
4. Each is minimal: removing `E` or `H` is impossible by step 1, and removing its remaining `A`, `B`, or `D` leaves no way to obtain that missing attribute.

<a id="q60"></a>

### Q60. [GATE CS 2005] Lossy decomposition and relation containment
For an instance `r` on schema `(A,B,C,D)`, let `r1=π_(A,B,C)(r)`, `r2=π_(A,D)(r)`, and `s=r1 ⋈ r2`. Given that this decomposition is lossy, which statement is true?

(A) `s ⊂ r`  
(B) `r ∪ s`  
(C) `r ⊂ s`  
(D) `r ⋈ s = s`

**Answer: (C) `r ⊂ s`**

**Solution:**
1. Each original tuple projects into both `r1` and `r2`, so joining those projections always reconstructs every tuple of `r`: `r ⊆ s`.
2. A lossy join creates at least one spurious tuple, so the containment is strict: `r ⊂ s`.

<a id="q61"></a>

### Q61. [GATE CS 2005] False statement about normal forms
Which statement about normal forms is false?

(A) BCNF is stricter than 3NF.  
(B) A lossless, dependency-preserving decomposition into 3NF is always possible.  
(C) A lossless, dependency-preserving decomposition into BCNF is always possible.  
(D) Any relation with two attributes is in BCNF.

**Answer: (C) A lossless, dependency-preserving decomposition into BCNF is always possible.**

**Solution:**
1. BCNF is stricter than 3NF, and two-attribute relations cannot have a non-trivial FD with a determinant that is not a superkey.
2. A lossless and dependency-preserving 3NF synthesis is always possible.
3. BCNF decomposition is lossless, but it may lose dependency preservation. For example, with `AB→C` and `C→B`, no BCNF decomposition preserves both dependencies.

<a id="q62"></a>

### Q62. [GATE CS 2014 Set 2] Key constraint on a student table instance
The table below is given. For `(StudentName, StudentAge)` to be a key for this instance, what must `X` not equal?

| StudentID | StudentName | StudentEmail | StudentAge | CPI |
|---:|---|---|---:|---:|
| 2345 | Shankar | shankar@math | X | 9.4 |
| 1287 | Swati | swati@ee | 19 | 9.5 |
| 7853 | Shankar | shankar@cse | 19 | 9.4 |
| 9876 | Swati | swati@mech | 18 | 9.3 |
| 8765 | Ganesh | ganesh@civil | 19 | 8.7 |

(A) 18  
(B) 19  
(C) 17  
(D) 20

**Answer: (B) 19**

**Solution:**
1. A key cannot repeat the pair `(StudentName, StudentAge)`.
2. There is already a row `(Shankar,19)` (student 7853). If `X=19`, the first row repeats that pair.
3. For each other offered value, `(Shankar,X)` is distinct from every existing name-age pair.

<a id="q63"></a>

### Q63. [GATE CS 2014 Set 2] Number of superkeys when a key is known
For schema `R(E,F,G,H)`, `E` is a key. What is the maximum number of superkeys?

(A) 5  
(B) 6  
(C) 7  
(D) 8

**Answer: (D) 8**

**Solution:**
1. Every superkey must contain `E`.
2. Each of the other three attributes may be included or omitted independently, giving `2^3=8` superkeys.

<a id="q64"></a>

### Q64. [GATE CS Mock 2017] Definition of a transaction
Which option defines a transaction correctly?

(A) A transaction consists of DDL statements on the database schema.  
(B) A transaction consists of `COMMIT` or `ROLLBACK` in a database session.  
(C) A transaction consists of a collection of DML statements, or a DDL/DCL/TCL statement, forming a logical unit of work in a database session.  
(D) A transaction consists of DML and DDL statements in different database sessions.

**Answer: (C) A logical unit of work in one database session**

**Solution:**
1. A transaction groups database work as a logical unit in one session; it is not just a commit/rollback command.
2. Statements from different sessions do not form one transaction. DDL/DCL transaction behavior (including implicit commits) can vary by DBMS, but that does not make choices (A), (B), or (D) a correct general definition.

<a id="q65"></a>

### Q65. [GATE CS Mock 2017] `BETWEEN` with string operands
What is true about this query?

```sql
SELECT firstName, lastName
FROM Employee
WHERE lastName BETWEEN 'A%' AND 'D%';
```

(A) It displays last names starting with letters A through D, including A and excluding D.  
(B) It errors because `BETWEEN` can only be used for numbers.  
(C) It displays names starting with A and ending with D.  
(D) It displays names in a range of starting letters A through D, excluding names starting with A and D.

**Answer: (A) Intended choice: a string range from the A boundary to the D boundary**

**Solution:**
1. `BETWEEN` is valid for strings as well as numbers; its comparison is a collation/lexicographic range comparison.
2. Here `'A%'` and `'D%'` are literal string bounds. `%` is **not** a wildcard in `BETWEEN` (only `LIKE` treats it as one). Under the intended alphabetic-range interpretation, the query covers names from the A bound up to but not beyond the D bound; the other descriptions do not match.
3. The exact set depends on the database's collation and the actual strings, so this should not be used as a prefix search; use `LIKE 'A%'` etc. for that purpose.

<a id="q66"></a>

### Q66. [GATE CS 2018] Which schema is in 3NF but not BCNF?
Four registration schemas have the following non-trivial FDs. In Schema I, `courses` is set-valued.

- **Schema I:** `Registration(rollno,courses)`; `rollno→courses`.
- **Schema II:** `Registration(rollno,courseid,email)`; `rollno,courseid→email` and `email→rollno`.
- **Schema III:** `Registration(rollno,courseid,marks,grade)`; `rollno,courseid→marks,grade` and `marks→grade`.
- **Schema IV:** `Registration(rollno,courseid,credit)`; `rollno,courseid→credit` and `courseid→credit`.

Which schema is in 3NF but not BCNF?

(A) Schema I  
(B) Schema II  
(C) Schema III  
(D) Schema IV

**Answer: (B) Schema II**

**Solution:**
1. In Schema II, candidate keys are `{rollno,courseid}` and `{email,courseid}`. Thus all three attributes are prime.
2. `email→rollno` violates BCNF: `email` alone does not determine `courseid`, so it is not a superkey.
3. It satisfies 3NF because the FD's right-side attribute `rollno` is prime. Schema I's stated key FD is BCNF; Schema III has non-prime `grade` transitively dependent via `marks`; in Schema IV `courseid→credit` violates 3NF because `credit` is non-prime.

<a id="q67"></a>

### Q67. [GATE CS 2016 Set 1] Attribute set that is not a superkey
A relation has attributes `V,W,X,Y,Z` and primary key `(V,Y)`. Which set is **not** a superkey?

(A) `VXYZ`  
(B) `VWXZ`  
(C) `VWXY`  
(D) `VWXYZ`

**Answer: (B) `VWXZ`**

**Solution:**
1. A superkey must contain the primary key `{V,Y}`.
2. Choices (A), (C), and (D) contain both `V` and `Y`; (B) omits `Y`, so it is not guaranteed to identify a row.

<a id="q68"></a>

### Q68. [GATE IT 2005] Partial dependencies in a five-field relation
A relation has fields `F1,F2,F3,F4,F5` and FDs:

```text
F1 → F3
F2 → F4
(F1,F2) → F5
```

What normal form does it satisfy?

(A) 1NF  
(B) 2NF  
(C) 3NF  
(D) None

**Answer: (A) 1NF**

**Solution:**
1. `{F1,F2}` is a candidate key: it determines `F3`, `F4`, and `F5`, and neither `F1` nor `F2` alone determines all attributes.
2. `F1→F3` and `F2→F4` are partial dependencies of non-key attributes on proper subsets of the composite key.
3. These violate 2NF, so the highest guaranteed form is 1NF.

<a id="q69"></a>

### Q69. [GATE IT 2005] Attribute for rent-payment information
In an ER model, `HotelRoom` and `Person` have a many-to-many relationship `Lodging`. Where should rent-payment information for a person occupying a particular room be stored?

(A) `Person`  
(B) `HotelRoom`  
(C) `Lodging`  
(D) None of these

**Answer: (C) `Lodging`**

**Solution:**
1. The payment is about a particular person-room pairing, not about a person or room independently.
2. A many-to-many relationship row identifies that pairing, so its attribute belongs to `Lodging`.

<a id="q70"></a>

### Q70. [GATE CS 2014 Set 1] Two statements about normal forms and a minimal cover
Given:

- **S1:** Every table with two single-valued attributes is in 1NF, 2NF, 3NF, and BCNF.
- **S2:** `{AB→C, D→E, E→C}` is a minimal cover for `{AB→C, D→E, AB→E, E→C}`.

Which choice is correct?

(A) S1 true and S2 false  
(B) Both true  
(C) S1 false and S2 true  
(D) Both false

**Answer: (A) S1 is true and S2 is false**

**Solution:**
1. With two single-valued attributes, 1NF holds. Any non-trivial FD has one attribute determining the other, so that determinant is a key; if there is no such FD, the full pair is a key. The relation is therefore BCNF (and consequently 2NF and 3NF).
2. In S2, `AB→E` cannot be removed: the proposed remaining dependencies do not imply it. Its left side does not determine `D`, so `D→E` cannot help, and `E→C` only determines `C` after `E` is known.
3. Therefore the proposed set is not equivalent to the original FD set and is not a minimal cover.

<a id="q71"></a>

### Q71. [GATE CS 2014 Set 1] Candidate key of a ten-attribute relation
For `R(E,F,G,H,I,J,K,L,M,N)`, the FDs are:

```text
{E,F} → G
F → I,J
{E,H} → K,L
K → M
L → N
```

Which is a key for `R`?

(A) `{E,F}`  
(B) `{E,F,H}`  
(C) `{E,F,H,K,L}`  
(D) `{E}`

**Answer: (B) `{E,F,H}`**

**Solution:**
1. `{E,F,H}+` initially contains `E,F,H`. Then `EF→G`, `F→I,J`, and `EH→K,L`; finally `K→M` and `L→N`.
2. The closure is `{E,F,G,H,I,J,K,L,M,N}`, all attributes of `R`.
3. `E`, `F`, and `H` are not obtainable from other attributes because none appears on an FD right side. All three are necessary, so this is a candidate key. (A) lacks `H`; (C) is a nonminimal superkey; (D) is incomplete.

<a id="q72"></a>

### Q72. [GATE CS 2008] Normal forms of Book and Collection
Consider:

```text
Book(Title, Author, Catalog_no, Publisher, Year, Price)
Collection(Title, Author, Catalog_no)
```

The FDs are:

```text
Title, Author → Catalog_no
Catalog_no → Title, Author, Publisher, Year
Publisher, Title, Year → Price
```

Assume `{Author, Title}` is the key for both schemes. Which statement is true?

(A) Both Book and Collection are in BCNF.  
(B) Both are in 3NF only.  
(C) Book is in 2NF and Collection is in 3NF.  
(D) Both are in 2NF only.

**Answer: (C) Book is in 2NF and Collection is in 3NF**

**Solution:**
1. In `Book`, the assumed composite key has no FD from `Author` alone or `Title` alone to a non-prime attribute, so there is no partial dependency and it is in 2NF.
2. `Catalog_no` is not a superkey of `Book`, and its FD determines non-prime attributes `Publisher` and `Year`; that violates 3NF (and BCNF).
3. In `Collection`, `Title,Author→Catalog_no`, and `Catalog_no→Title,Author`; each determinant is a key for this three-attribute relation. It is actually BCNF, hence also satisfies the stated 3NF choice.

<a id="q73"></a>

### Q73. [GATE IT 2008] Normal form with a partial dependency
For `R(A,B,C,D,E,P,G)`, the known FDs are:

```text
AB → CD
DE → P
C → E
P → C
B → G
```

Which statement is true?

(A) In BCNF  
(B) In 3NF but not BCNF  
(C) In 2NF but not 3NF  
(D) Not in 2NF

**Answer: (D) Not in 2NF**

**Solution:**
1. `AB+` contains `C,D`; then `C→E`, `DE→P`, `P→C`, and `B→G`, so `AB` is a candidate key.
2. `B→G` is a dependency of a non-prime attribute on the proper subset `B` of key `AB`.
3. This partial dependency violates 2NF.

<a id="q74"></a>

### Q74. [GATE CS Mock 2018] Minimum relation count for three ER models
The figure contains three ER models: **Model 1** is 1:N, with partial participation on both sides; **Model 2** is 1:N, with total participation on the N side (`E2`); **Model 3** is N:M, with total participation on both sides. How many minimum relation tables are required to represent them in 1NF, respectively?

(A) 2, 2, and 1  
(B) 2, 2, and 2  
(C) 1, 2, and 1  
(D) 1, 1, and 1

**Answer: (A) 2, 2, and 1, respectively**

**Solution:**
1. In Model 1, the 1:N association can be represented by a foreign key on the N side, but both entity sets must be retained because participation is partial: two tables.
2. Model 2 still needs a separate representation for the 1-side entities that can participate without a corresponding N-side tuple, so the minimum is two tables.
3. In Model 3, both sides participate totally and the diagram has no entity or relationship attributes. The participating pairs alone can be stored as one relation; projecting it recovers each entity set.

<a id="q75"></a>

### Q75. [GATE CS Mock 2018] People who frequent suitable pizzerias
The database schema is:

```text
Person(name, age, gender)                 key: name
Frequents(name, pizzeria)                 key: (name, pizzeria)
Eats(name, pizza)                          key: (name, pizza)
Serves(pizzeria, pizza, price)             key: (pizzeria, pizza)
```

Choose the relational-algebra expression for “names of all people who frequent only pizzerias serving at least one pizza they eat.” The original options are formulas rendered as images.

(A) [Relational-algebra formula in the original figure]  
(B) [Relational-algebra formula in the original figure]  
(C) [Relational-algebra formula in the original figure]  
(D) None of the above

> Note: Original figure not reproduced. The three option formulas could not be retrieved/read in the source images; the question and answer are retained, and the unreadable options are described rather than reproduced.

**Answer: (B) The expression that removes people with any unsuitable frequented pizzeria**

**Solution:**
1. A person is disqualified if they frequent even one pizzeria that serves none of the pizzas they eat.
2. Define `GoodPairs = π_(name,pizzeria)(Frequents ⋈ Eats ⋈ Serves)`, joining on equal person names, pizzeria names, and pizza names. Then `Frequents − GoodPairs` contains the unsuitable frequentings.
3. The result is `π_name(Frequents) − π_name(Frequents − GoodPairs)`: remove every person with at least one unsuitable frequenting. The source marks (B) as the expression for this set.

<a id="q76"></a>

### Q76. [GATE CS Mock 2018] FD not implied by a given set
Which FD cannot be implied by `{A→B, A→BC, C→D}`?

(A) `A→C`  
(B) `B→D`  
(C) `BC→D`  
(D) All of the above

**Answer: (B) `B→D`**

**Solution:**
1. `A→BC` directly gives `A→C` by decomposition.
2. `C→D` gives `BC→D` by augmentation.
3. Nothing determines `D` from `B` alone, so `B→D` is not implied.

<a id="q77"></a>

### Q77. [GATE CS 1997] Normal form with atomic attributes and partial dependencies
For `R(a,b,c,d)`, all attribute domains are atomic, and the only FDs are `a→c` and `b→d` (plus those inferred from them). What is the relation's normal form?

(A) In 1NF but not 2NF  
(B) In 2NF but not 1NF  
(C) In 3NF  
(D) None of the above

**Answer: (A) In 1NF but not 2NF**

**Solution:**
1. Attributes `a` and `b` never appear on right sides, and `{a,b}` determines all attributes; it is the candidate key.
2. `a→c` and `b→d` are partial dependencies of non-prime attributes on parts of this composite key.
3. Atomic domains give 1NF, but the partial dependencies violate 2NF.

<a id="q78"></a>

### Q78. [GATE CS 1998] Normal forms before and after changing the key
A relation contains `Book_id`, `Subject_Category_of_book`, `Name_of_Author`, and `Nationality_of_Author`, with `Book_id` as the primary key.

(a) What is its highest normal form?  
(b) If `Book_title` and `Author_address` are added and the primary key is changed to `(Name_of_Author, Book_title)`, what is its highest normal form?

**Answer: (a) BCNF; (b) 2NF, assuming only the stated FDs and the changed key**

**Solution:**
1. In (a), the stated key `Book_id` determines the other attributes. Thus every non-trivial FD has a key determinant, satisfying BCNF.
2. In (b), the new composite key is `{Name_of_Author, Book_title}`. Under the stated key/FD information, neither key component alone determines a non-prime attribute, so the relation has no partial dependency and satisfies 2NF.
3. The old `Book_id` is no longer designated as a key but still determines the old book details. That determinant is not a superkey of the enlarged relation, and it determines non-prime details such as subject category and author nationality; the 3NF condition fails.

<a id="q79"></a>

### Q79. [GATE CS 1998] Adequate normal form for database design
Which normal form is generally considered adequate for relational database design?

(A) 2NF  
(B) 5NF  
(C) 4NF  
(D) 3NF

**Answer: (D) 3NF**

**Solution:**
1. 3NF removes the main anomalies due to functional dependencies while allowing a lossless, dependency-preserving decomposition.
2. It is often used as a practical design target; BCNF can be stricter but may fail to preserve all dependencies.

<a id="q80"></a>

### Q80. [GATE CS 1999] Normal forms under a cyclic FD set
Let `R(S,T,U,V)` have FDs `S→T`, `T→U`, `U→V`, and `V→S`. Let `R` be decomposed into `R1` and `R2` with `R1∩R2 ≠ ∅`. The decomposition is:

(A) Not in 2NF  
(B) In 2NF but not in 3NF  
(C) In 3NF but not in 2NF  
(D) In both 2NF and 3NF

**Answer: (D) In both 2NF and 3NF**

**Solution:**
1. The FDs form a cycle: every one of `S,T,U,V` determines all four. Thus each attribute is a candidate key of `R`.
2. In any nonempty projected component, each included attribute determines every other included attribute (the projected dependencies follow from the original closures).
3. Hence the components satisfy BCNF, and therefore also 2NF and 3NF. In particular, the stated nonempty common attribute does not create a partial dependency.

<a id="q81"></a>

### Q81. [GATE CS 1999] Finding a key from FD closures
For `R(A,B,C,D,E,F)`, the FDs are `C→F`, `E→A`, `EC→D`, and `A→B`. Which is a key?

(A) `CD`  
(B) `EC`  
(C) `AE`  
(D) `AC`

**Answer: (B) `EC`**

**Solution:**
1. Start with `(EC)+={E,C}`. From `EC→D`, add `D`; from `E→A`, add `A`; from `A→B`, add `B`; and from `C→F`, add `F`.
2. Thus `(EC)+={A,B,C,D,E,F}`. Neither `E` nor `C` can be removed: neither occurs on any FD right side, so both are required in every key.

<a id="q82"></a>

### Q82. [GATE IT 2004] Rows and columns from a Cartesian product
The empty tables are populated as follows:

```sql
INSERT INTO department VALUES (1, 'Mathematics');
INSERT INTO department VALUES (2, 'Physics');
INSERT INTO student VALUES (1, 'Navin', 1);
INSERT INTO student VALUES (2, 'Mukesh', 2);
INSERT INTO student VALUES (3, 'Gita', 1);
```

`student` has columns `(roll_no, name, dept_id)` and `department` has `(dept_id, dept_name)`. How many rows and columns does this query return?

```sql
SELECT * FROM student, department;
```

(A) 0 rows and 4 columns  
(B) 3 rows and 4 columns  
(C) 3 rows and 5 columns  
(D) 6 rows and 5 columns

**Answer: (D) 6 rows and 5 columns**

**Solution:**
1. With no join condition, the query forms the Cartesian product: `3×2=6` rows.
2. It returns all columns from both tables: `3+2=5` columns.

<a id="q83"></a>

### Q83. [GATE IT 2004] Tables for a 1:m ER model with a multivalued attribute
An ER diagram has entities `E1` and `E2` joined by a 1:m relationship `R` (one `E1` to many `E2`), with no relationship attributes. `E1` has key `A11` and attributes `A12,A13`; `E2` has key `A21`, attribute `A22`, and multivalued attribute `A23`. What is the minimum number of tables needed so each table is in 3NF?

(A) 2  
(B) 3  
(C) 5  
(D) 4

**Answer: (B) 3**

**Solution:**
1. Use one table for `E1(A11,A12,A13)`.
2. Represent the 1:m relationship by including `A11` as a foreign key in `E2(A21,A22,A11)`; no separate relation table is needed for `R`.
3. The multivalued attribute needs its own table, such as `(A21,A23)`. Total: three tables.

<a id="q84"></a>

### Q84. [GATE CS 2015 Set 3] Trivial FD in the closure
For `X(P,Q,R,S,T,U)`, let `F={{P,R}→{S,T}, {P,S,U}→{Q,R}}`. Which is a trivial FD in `F+`?

(A) `{P,R}→{S,T}`  
(B) `{P,R}→{R,T}`  
(C) `{P,S}→{S}`  
(D) `{P,S,U}→{Q}`

**Answer: (C) `{P,S}→{S}`**

**Solution:**
1. An FD `X→Y` is trivial exactly when `Y⊆X`.
2. In (C), the right side `{S}` is contained in `{P,S}`. The other choices have a right-side attribute not present on the left.

<a id="q85"></a>

### Q85. [GATE CS 2015 Set 1] Minimum number of 3NF relations from an ER model
An ER model has entities and relationships as follows:

- `E1(a11,a12)`, with key `a11`.
- `E2(a21,a22)`, with key `a22`.
- `E3(a31,a32)`, with key `a31`.
- `R12` is an m:n relationship between `E1` and `E2`.
- `R13` is a 1:n relationship (`1` at `E1`, `n` at `E3`).
- Neither relationship has attributes.

What is the minimum number of relations generated, with each in 3NF?

(A) 2  
(B) 3  
(C) 4  
(D) 5

**Answer: (C) 4**

**Solution:**
1. Retain one relation for each entity: three relations.
2. The 1:n relationship `R13` can be represented by storing `a11` as a foreign key in the `E3` relation, so it requires no extra table.
3. The m:n relationship `R12` needs a separate relation with key `(a11,a22)`. Total: `3+1=4`.

<a id="q86"></a>

### Q86. [GATE CS 2000] FDs satisfied by a relation instance
Given this instance, which pair of FDs is satisfied?

| x | y | z |
|---:|---:|---:|
| 1 | 4 | 2 |
| 1 | 5 | 3 |
| 1 | 6 | 3 |
| 3 | 2 | 2 |

(A) `XY→Z` and `Z→Y`  
(B) `YZ→X` and `Y→Z`  
(C) `YZ→X` and `X→Z`  
(D) `XZ→Y` and `Y→X`

**Answer: (B) `YZ→X` and `Y→Z`**

**Solution:**
1. Every `Y` value is unique in this instance, so equal `Y` values cannot disagree on either `X` or `Z`. Both `Y→Z` and the stronger-determinant FD `YZ→X` hold.
2. `Z→Y` fails because `Z=2` appears with `Y=4` and `Y=2`; `X→Z` fails because `X=1` appears with `Z=2` and `Z=3`; `XZ→Y` fails for `(X,Z)=(1,3)`; so (A), (C), and (D) fail.

<a id="q87"></a>

### Q87. [GATE CS 2000] Basic relational algebra and aggregation
Given:

```text
employee(name, salary, deptno)
department(deptno, deptname, address)
```

Which query cannot be expressed using only union (`∪`), difference (`−`), Cartesian product (`×`), projection (`π`), selection (`σ`), and rename (`ρ`)?

(A) Department address of every employee  
(B) Employees whose name is the same as their department name  
(C) The sum of all employees’ salaries  
(D) All employees of a given department

**Answer: (C) The sum of all employees’ salaries**

**Solution:**
1. The relational-algebra operators listed support selection, joins (via product and selection), and projection; each of (A), (B), and (D) can be expressed using them.
2. A sum is an aggregate operation, which is not in basic relational algebra. Extended relational algebra adds aggregate operators such as `SUM`.

<a id="q88"></a>

### Q88. [GATE CS 2000] Correctness of candidate-key selection
For `R(A,B,C,D,E,F)`, let the FDs be `C→F`, `E→A`, `EC→D`, and `A→B`. Which is a key?

(A) `CD`  
(B) `EC`  
(C) `AE`  
(D) `AC`

**Answer: (B) `EC`**

**Solution:**
1. From `EC`, derive `D` using `EC→D`, `A` using `E→A`, `B` using `A→B`, and `F` using `C→F`.
2. Therefore `(EC)+={A,B,C,D,E,F}`. Since neither `E` nor `C` can be derived from other attributes, the set is minimal and is a candidate key.
