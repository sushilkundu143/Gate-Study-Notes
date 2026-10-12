# PYQs — SQL

[← All PYQ topics](./README.md) · [DBMS notes](../README.md)

**66 questions** (38 from GATE papers). Try each question before opening its solution.

## Quick Answer Key

| Q | Source | Answer |
| --- | --- | --- |
| [Q1](#q1) | GATE CS 2012 | (B) 3 |
| [Q2](#q2) | GATE CS 2011 | (A) 127 |
| [Q3](#q3) | GATE CS 2011 | (C) 5 |
| [Q4](#q4) | GATE CS 2010 | (C) 1, 3 |
| [Q5](#q5) | GATE CS 2009 | (A) I and II |
| [Q6](#q6) | GATE CS 2009 | No listed option exactly matches; it returns suppliers with no cata… |
| [Q7](#q7) | GATE CS 1996 | (A) and (B) |
| [Q8](#q8) | GFG practice | (C) Names of students who got an A in at least one course taught by… |
| [Q9](#q9) | GFG practice | No listed option exactly matches; it returns suppliers with no cata… |
| [Q10](#q10) | GFG practice | (D) Only I is correct. |
| [Q11](#q11) | GFG practice | (A) Avg |
| [Q12](#q12) | GFG practice | (B) The average marks of male students is greater than the average … |
| [Q13](#q13) | GFG practice | (C) 10 |
| [Q14](#q14) | GFG practice | (D) 4 and 2 |
| [Q15](#q15) | GFG practice | (A) `CREATE ASSERTION ... CHECK ...` |
| [Q16](#q16) | GFG practice | (B) Pids of parts supplied only by Sachin (under the intended first… |
| [Q17](#q17) | GFG practice | (A) M=4, N=2 |
| [Q18](#q18) | GFG practice | (B) Fragments |
| [Q19](#q19) | GFG practice | (B) 1 and 2 |
| [Q20](#q20) | GFG practice | (D) Average salary of male employees is more than the average salar… |
| [Q21](#q21) | GATE CS Mock 2018 | (C) Third highest salary |
| [Q22](#q22) | GFG practice | (A) R has no duplicates and S is non-empty. |
| [Q23](#q23) | GFG practice | (C) Titles of the seven most expensive books. |
| [Q24](#q24) | GATE CS 2021 | (B) Employees in the company. |
| [Q25](#q25) | GATE IT 2006 | (A) 2000 |
| [Q26](#q26) | GATE CS 2014 | (D) Both S1 and S2 are FALSE. |
| [Q27](#q27) | GATE CS 2014 | (D) Employees whose customers are all rated GOOD. |
| [Q28](#q28) | GATE CS 2006 | (B) |
| [Q29](#q29) | GFG practice | (D) Trigger |
| [Q30](#q30) | GATE CS 2004 | (A) 8, 8 |
| [Q31](#q31) | GATE CS 2012 | (C) Q and R (official GATE key) |
| [Q32](#q32) | GFG practice | (D) `DROP` |
| [Q33](#q33) | GATE CS 2004 | (D) The average salary of male employees is greater than the averag… |
| [Q34](#q34) | GATE CS 2015 | (D) Projection in relational algebra, except SQL `SELECT` retains d… |
| [Q35](#q35) | GATE IT 2005 | (B) 4 |
| [Q36](#q36) | GATE CS 2007 | (A) Q1 is correct |
| [Q37](#q37) | GATE CS 2014 | (B) It executes and gives the correct result |
| [Q38](#q38) | GATE CS 2014 | (C) Join with the distinct values of `S.a` |
| [Q39](#q39) | GATE CS 2006 | (C) 1 and 4 |
| [Q40](#q40) | GATE CS 2005 | (C) `(5,2)`, `(7,2)`, and `(9,5)` |
| [Q41](#q41) | GATE CS 2005 | (D) Titles of the five most expensive books |
| [Q42](#q42) | GATE CS 2003 | (A) Projection after selection from the Cartesian product |
| [Q43](#q43) | GATE CS 2003 | (C) Students who got an A in at least one course taught by Korth |
| [Q44](#q44) | GATE CS 2000 | (A) `r` has no duplicates and `s` is non-empty |
| [Q45](#q45) | GATE CS 2000 | (C) `x <> 5` and `NOT (x = 5)` |
| [Q46](#q46) | GATE CS 2015 Mock | (B) Names of students enrolled in both DBMS and OS |
| [Q47](#q47) | GATE CS 2015 Mock | (B) 5 |
| [Q48](#q48) | GATE CS 2015 | (C) 2 |
| [Q49](#q49) | GATE CS 2015 | (A) `P1.capacity >= ALL (...)` |
| [Q50](#q50) | GATE CS 2015 | (D) T3, then T2, then T1 |
| [Q51](#q51) | GFG practice | (D) Titles of the five most expensive books |
| [Q52](#q52) | GATE IT 2005 | (D) Suppliers who supply two or more items |
| [Q53](#q53) | GATE CS 2016 | (B) 2 |
| [Q54](#q54) | GATE IT 2008 | (D) Nothing; the query has a syntax error |
| [Q55](#q55) | GATE CS 1999 | (D) None of the above |
| [Q56](#q56) | GATE CS 1998 | SQL query: |
| [Q57](#q57) | GATE CS 1998 | Relational-algebra expression: |
| [Q58](#q58) | GATE CS 1997 |  |
| [Q59](#q59) | GATE CS 2018 Mock | (C) Find the third-highest salary |
| [Q60](#q60) | GATE CS 2018 | (D) Query 4 |
| [Q61](#q61) | GFG practice | (B) Only (b) |
| [Q62](#q62) | GFG practice | (C) `AVG` |
| [Q63](#q63) | GFG practice | No correct option; the standard SQL command is `UPDATE`. |
| [Q64](#q64) | GFG practice | (D) 3 |
| [Q65](#q65) | GFG practice | (B) `R1` has no duplicates and `R2` is non-empty |
| [Q66](#q66) | GFG practice | (B) 4 |

---

## Questions and Solutions

<a id="q1"></a>

### Q1. [GATE CS 2012] `ALL` with an empty subquery
Tables A, B, and C are given:

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
|---:|---:|---|
| 10 | 2200 | 02 |
| 99 | 2100 | 01 |

How many tuples are returned by this query?

```sql
SELECT A.id
FROM A
WHERE A.age > ALL (
  SELECT B.age
  FROM B
  WHERE B.name = "arun"
);
```

(A) 4  
(B) 3  
(C) 0  
(D) 1

**Answer: (B) 3**

**Solution:** No row in B has name `arun`, so the subquery returns an empty set. A comparison with `ALL` over an empty set is true. Therefore all three rows in A qualify.

<a id="q2"></a>

### Q2. [GATE CS 2011] Repeated insertions and a filtered SQL result
Relation `T(X,Y)` initially contains `(1,1)`. Insert 128 records, each computed as `X = MX + 1` and `Y = 2*MY + 1`, where `MX` and `MY` are the current maximum values. The supplied prompt also asks for `MAX(X)` and `MAX(Y)` after the insertions, and gives this query:

```sql
SELECT Y FROM T WHERE X=7;
```

What value does the query return?

(A) 127  
(B) 255  
(C) 129  
(D) 257

**Answer: (A) 127**

**Solution:** After insertion number `n`, `X=1+n`, so `X=7` identifies insertion 6. Starting at `Y=1`, the recurrence gives `Y_n=2^(n+1)-1`; hence `Y_6=2^7-1=127`. After all insertions the maxima are `MAX(X)=129` and `MAX(Y)=2^129-1`. The maxima sentence in the supplied stem does not match the scalar answer choices; those choices match the displayed `SELECT` query.

<a id="q3"></a>

### Q3. [GATE CS 2011] Cardinality of a natural join
`Loan_Records` contains:

| Borrower | Bank_Manager | Loan_Amount |
|---|---|---:|
| Ramesh | Sunderajan | 10000 |
| Suresh | Ramgopal | 5000 |
| Mahesh | Sunderajan | 7000 |

What is the result of this query?

```sql
SELECT Count(*)
FROM ((SELECT Borrower, Bank_Manager FROM Loan_Records) AS S
      NATURAL JOIN
      (SELECT Bank_Manager, Loan_Amount FROM Loan_Records) AS T);
```

(A) 3  
(B) 9  
(C) 5  
(D) 6

**Answer: (C) 5**

**Solution:** The natural join matches on `Bank_Manager`. Sunderajan occurs twice on each side, producing `2×2=4` joined rows. Ramgopal occurs once on each side, producing one more. Total: `4+1=5`.

<a id="q4"></a>

### Q4. [GATE CS 2010] Correlated `EXISTS` and passenger ages
The schemas are `Passenger(pid, pname, age)` and `Reservation(pid, class, tid)`.

**Passenger**

| pid | pname | age |
|---:|---|---:|
| 0 | Sachin | 65 |
| 1 | Rahul | 66 |
| 2 | Sourav | 67 |
| 3 | Anil | 69 |

**Reservation**

| pid | class | tid |
|---:|---|---:|
| 0 | AC | 8200 |
| 1 | AC | 8201 |
| 2 | SC | 8201 |
| 5 | AC | 8203 |
| 1 | SC | 8204 |
| 3 | AC | 8202 |

Which pids are returned by the intended query below? (The source has typographical errors in `SELECT`, `FROM`, and the comparison symbols.)

```sql
SELECT pid
FROM Reservation
WHERE class = 'AC'
  AND EXISTS (
    SELECT *
    FROM Passenger
    WHERE age > 65 AND Passenger.pid = Reservation.pid
  );
```

(A) 1, 0  
(B) 1, 2  
(C) 1, 3  
(D) 1, 5

**Answer: (C) 1, 3**

**Solution:** The AC reservations have pids 0, 1, 5, and 3. The correlated condition requires a matching passenger older than 65; those passenger pids are 1, 2, and 3. The intersection is `{1,3}`.

<a id="q5"></a>

### Q5. [GATE CS 2009] Equivalent formulations of relational division
Let relational schemas `R={a,b,c}` and `S={c}`. Consider the following three queries (where `r` and `s` denote relations over those schemas):

```text
I.   π_(R−S)(r) − π_(R−S)( π_(R−S)(r) × s − π_(R−S,S)(r) )

II.  { t | t ∈ π_(R−S)(r) ∧ ∀u ∈ s (∃v ∈ r (u = v[S] ∧ t = v[R−S])) }

III. { t | t ∈ π_(R−S)(r) ∧ ∀v ∈ r (∃u ∈ s (u = v[S] ∧ t = v[R−S])) }
```

Which queries are equivalent?

(A) I and II  
(B) I and III  
(C) II and IV  
(D) III and IV

**Answer: (A) I and II**

**Solution:** I is the relational-algebra expression for division: it retains an `R−S` tuple if it has a matching `R` tuple for every `S` tuple. II states exactly that condition using tuple calculus. III instead quantifies over every `v` in `r`, so it does not express the same “for every S value” test. There is no query IV in the supplied list; the two options mentioning IV therefore cannot be correct.

<a id="q6"></a>

### Q6. [GATE CS 2009] Interpreting nested `NOT IN` supplier query
Schema: `Suppliers(sid, sname, city, street)`, `Parts(pid, pname, color)`, and `Catalog(sid, pid, cost)`. Assume the relations are not empty. Interpret:

```sql
SELECT S.sname
FROM Suppliers S
WHERE S.sid NOT IN (
  SELECT C.sid
  FROM Catalog C
  WHERE C.pid NOT IN (
    SELECT P.pid
    FROM Parts P
    WHERE P.color <> 'blue'
  )
);
```

(A) Names of all suppliers who have supplied a non-blue part.  
(B) Names of all suppliers who have not supplied a non-blue part.  
(C) Names of all suppliers who have supplied only blue parts.  
(D) Names of all suppliers who have not supplied only blue parts.

**Answer: No listed option exactly matches; it returns suppliers with no cataloged blue part.**

**Solution:** The innermost query lists non-blue part ids. A catalog row qualifies in the middle query when its part id is *not* in that list—i.e. it is blue (assuming non-null ids and valid catalog part ids). The outer `NOT IN` excludes suppliers appearing among those blue suppliers. Thus it returns suppliers that supplied no blue part, including suppliers with no catalog rows if `sid` is non-null. Neither “supplied a non-blue part” nor the literal negation in option D states this correctly.

> Note: The official GATE 2009 key is (A), and GFG marks (D) here. Strictly, the query returns suppliers who have supplied **no blue part** (including suppliers with no catalog rows), which none of the options states exactly. If asked in the exam, prefer the official key (A).

<a id="q7"></a>

### Q7. [GATE CS 1996] Describing relational-algebra queries
Schema:

```text
USERS(User#, UserName, HomeTown)
BOOKS(Book#, BookTitle, AuthorName)
ISSUED(Book#, User#, Date)
```

Explain in one English sentence what each query determines:

```text
(a) σ_(User#=6) ( π_(User#, Book Title) ((USERS ⋈ ISSUED) ⋈ BOOKS) )
(b) π_(Author Name) ( BOOKS ⋈ σ_(Home Town=Delhi) (USERS ⋈ ISSUED) )
```

(A) (a) Show all book titles issued by User# 6.  
(B) (b) Show all author names for books issued by users whose hometown is Delhi.

**Answer: (A) and (B)**

**Solution:** For (a), join users to issued books and book details, then keep User# 6 and project the title. For (b), retain issued records belonging to Delhi users, join those records to book details, and project author names. Both descriptions match.

<a id="q8"></a>

### Q8. [GFG practice] Students earning an A in Sriram's courses
Relations are `Students(Roll_number, Name, Date_of_birth)`, `Courses(Course_number, Course_name, Instructor)`, and `Grades(Roll_number, Course_number, Grade)`. Consider:

```sql
SELECT DISTINCT Name
FROM Students, Courses, Grades
WHERE Students.Roll_number = Grades.Roll_number
  AND Courses.Instructor = 'Sriram'
  AND Courses.Course_number = Grades.Course_number
  AND Grades.Grade = 'A';
```

Which set is computed?

(A) Names of students who got an A in all courses taught by Sriram.  
(B) Names of students who got an A in all courses.  
(C) Names of students who got an A in at least one course taught by Sriram.  
(D) None of the above.

**Answer: (C) Names of students who got an A in at least one course taught by Sriram.**

**Solution:** The joins produce a row for each matching student/course/grade. The conditions require that course to be taught by Sriram and the grade to be A. `DISTINCT` removes repeated names; there is no universal condition requiring an A in every such course.

<a id="q9"></a>

### Q9. [GFG practice] Interpreting a nested supplier query
Schema: `Suppliers(sid, sname, city, street)`, `Parts(pid, pname, color)`, and `Catalog(sid, pid, cost)`. Assume the relations are not empty. Interpret:

```sql
SELECT S.sname
FROM Suppliers S
WHERE S.sid NOT IN (
  SELECT C.sid
  FROM Catalog C
  WHERE C.pid NOT IN (
    SELECT P.pid
    FROM Parts P
    WHERE P.color <> 'blue'
  )
);
```

(A) Names of all suppliers who have supplied a non-blue part.  
(B) Names of all suppliers who have not supplied a non-blue part.  
(C) Names of all suppliers who have supplied only non-blue parts.  
(D) Names of all suppliers who have not supplied only non-blue parts.

**Answer: No listed option exactly matches; it returns suppliers with no cataloged blue part.**

**Solution:** The innermost query returns non-blue pids, so the middle query finds catalog entries for blue pids (those not in the non-blue list). The outer query then excludes those suppliers. It therefore selects suppliers with no blue supply, rather than the positive “has supplied a non-blue part” condition in A or the literal conditions in B–D.

> Note: This is a variant of GATE CS 2009, whose official key is (A); GFG also marks (A). Strictly, the query returns suppliers who have supplied **no blue part**, so no option is exact.

<a id="q10"></a>

### Q10. [GFG practice] SQL joins and self-joins
Which statements are true?

I. A self-join can be implemented in SQL using a table alias.  
II. Outer join is a basic operation in relational algebra.  
III. Natural join and outer join are equivalent.

(A) I and II are correct.  
(B) II and III are correct.  
(C) Only III is correct.  
(D) Only I is correct.

**Answer: (D) Only I is correct.**

**Solution:** A table can appear twice under different aliases, enabling a self-join. Outer join is an extension rather than a basic classical relational-algebra operation, and natural join does not preserve unmatched rows the way outer join does. Thus II and III are false.

<a id="q11"></a>

### Q11. [GFG practice] SQL aggregate function
Which of the following is an aggregate function in SQL?

(A) Avg  
(B) Select  
(C) Ordered by  
(D) Distinct

**Answer: (A) Avg**

**Solution:** `AVG` calculates one average from values in a group (or the whole input). `SELECT` is a statement keyword, while `ORDER BY` and `DISTINCT` are query clauses/modifiers.

<a id="q12"></a>

### Q12. [GFG practice] Comparing male department averages with university average
`STUDENT(Name, SEX, Marks, DEPT_Name)` stores university student information. Consider the intended query (the supplied text omits parentheses around the scalar subquery):

```sql
SELECT DEPT_Name
FROM STUDENT
WHERE SEX = 'M'
GROUP BY DEPT_Name
HAVING AVG(Marks) > (SELECT AVG(Marks) FROM STUDENT);
```

It returns department names for which:

(A) The average marks of male students is greater than the average marks of students in the same department.  
(B) The average marks of male students is greater than the average marks of students in the university.  
(C) The average marks of male students is greater than the average marks of male students in the university.  
(D) The average marks of students is greater than the average marks of male students in the university.

**Answer: (B) The average marks of male students is greater than the average marks of students in the university.**

**Solution:** `WHERE SEX='M'` filters the grouped rows to male students, so each group average is a department's male-student average. The uncorrelated subquery averages `Marks` over the entire `STUDENT` table. The `HAVING` comparison is between those two quantities.

<a id="q13"></a>

### Q13. [GFG practice] Possible row count for an `OR` condition
Given:

```sql
(a) SELECT Name FROM people WHERE Age > 21;
(b) SELECT Name FROM people WHERE Height > 180;
(c) SELECT Name FROM people WHERE (Age > 21) OR (Height > 180);
```

If (a) returns 10 rows and (b) returns 7 rows, which is one possible number of rows returned by (c)?

(A) 3  
(B) 7  
(C) 10  
(D) 21

**Answer: (C) 10**

**Solution:** The `OR` result contains records satisfying either condition. Its row count is at least the larger individual result (10) and at most 17, depending on overlap. If all seven height-qualified records are among the ten age-qualified records, the union has exactly 10 rows. 3 and 7 are too small; 21 exceeds the maximum 17.

<a id="q14"></a>

### Q14. [GFG practice] Full join versus inner join cardinality
`R(A,B)={(1,2),(1,3),(3,4)}` and `S(B,C)={(2,5),(4,6),(7,8)}`. Consider:

```sql
SQ1: SELECT * FROM R FULL JOIN S ON R.B = S.B;
SQ2: SELECT * FROM R INNER JOIN S ON R.B = S.B;
```

How many tuples do SQ1 and SQ2 return, respectively?

(A) 2 and 6  
(B) 6 and 2  
(C) 2 and 4  
(D) 4 and 2

**Answer: (D) 4 and 2**

**Solution:** Inner join has matches for `B=2` and `B=4`, hence two rows. Full join also includes the unmatched R row with `B=3` and unmatched S row with `B=7`, giving `2+1+1=4`.

<a id="q15"></a>

### Q15. [GFG practice] SQL assertion syntax
An assertion is a predicate expressing a condition that the database must always satisfy. Which is the correct syntax?

(A) `CREATE ASSERTION 'ASSERTION Name' CHECK 'Predicate'`  
(B) `CREATE ASSERTION 'ASSERTION Name'`  
(C) `CREATE ASSERTION, CHECK Predicate`  
(D) `SELECT ASSERTION`

**Answer: (A) `CREATE ASSERTION ... CHECK ...`**

**Solution:** SQL assertion syntax introduces a named assertion and gives its condition in a `CHECK` clause: `CREATE ASSERTION assertion_name CHECK (predicate)`. Option A is the only choice with that structure; its quotation marks are just how the option renders the name and predicate.

<a id="q16"></a>

### Q16. [GFG practice] Set difference and supplier parts
Schema: `Suppliers(sid, sname, saddress)`, `Parts(pid, pname, pcolor)`, `Catalog(sid, pid, pcost)`. What is the result of:

```sql
(SELECT Catalog.pid FROM Suppliers, Catalog
 WHERE Suppliers.sid = Catalog.pid)
MINUS
(SELECT Catalog.pid FROM Suppliers, Catalog
 WHERE Suppliers.sname <> 'sachin'
   AND Suppliers.sid = Catalog.sid)
```

(A) Pids of parts supplied by all except Sachin.  
(B) Pids of parts supplied only by Sachin.  
(C) Pids of parts available in the catalog supplied by Sachin.  
(D) Pids of parts available in catalogs supplied by all except Sachin.

**Answer: (B) Pids of parts supplied only by Sachin (under the intended first join).**

**Solution:** Under the apparent intended query, the first set is all cataloged pids and the second set is pids supplied by any supplier other than Sachin. Subtracting the latter leaves pids supplied only by Sachin. However, the first join is written `Suppliers.sid = Catalog.pid`, while the second uses `Catalog.sid`; if the first equality is literal, it does not compute “all cataloged pids” and option B is not generally justified. The likely intended first condition is `Suppliers.sid = Catalog.sid`.

<a id="q17"></a>

### Q17. [GFG practice] Counting results of two Oracle queries
The supplied tuple instances are incomplete: `R(A,B,C) = {, , , , , }` and `S(B,C,D) = {, , , , }`. The query text in the source is also truncated at `WHERE R.A = S.C AND S.D ...` before the definition of SQ2. It reports:

```sql
SQ1: SELECT R.B, AVG(S.B)
     FROM R, S
     WHERE R.A = S.C AND S.D ...

SQ2: SELECT DISTINCT S.B, MIN(S.C)
     FROM S
     GROUP BY S.B
     HAVING COUNT(DISTINCT S.D) > 1;
```

If SQ1 returns `M` tuples and SQ2 returns `N` tuples, choose the pair:

(A) M=4, N=2  
(B) M=5, N=3  
(C) M=2, N=2  
(D) M=3, N=3

**Answer: (A) M=4, N=2**

**Solution:** The supplied batch does not contain the relation values or the complete SQ1 condition, so its counts cannot be recomputed from the available statement. The only supported selection is the starred answer in the provided source: `M=4, N=2`.

> Note: Original relation values and part of SQ1 are missing from the supplied input, so this answer cannot be independently verified here.

<a id="q18"></a>

### Q18. [GFG practice] Location transparency in distributed databases
In a distributed database, location transparency lets users, programmers, and administrators treat data as if it were at one location. A SQL query that uses location transparency needs to specify:

(A) Inheritances  
(B) Fragments  
(C) Locations  
(D) Local formats

**Answer: (B) Fragments**

**Solution:** Location transparency hides the physical site where a fragment resides. The query can refer to the logical fragments, while the distributed DBMS resolves their actual locations.

<a id="q19"></a>

### Q19. [GFG practice] `EXCEPT` versus `EXCEPT ALL`
The supplied instance values for `One(x,y)` and `Two(x,y)` are missing from the input (`One` is shown as six blank tuples and `Two` as eight blank tuples). Consider:

```sql
SQ1: SELECT * FROM One
     EXCEPT
     SELECT * FROM Two;

SQ2: SELECT * FROM One
     EXCEPT ALL
     SELECT * FROM Two;
```

What are the cardinalities of SQ1 and SQ2, respectively?

(A) 2 and 1  
(B) 1 and 2  
(C) 2 and 2  
(D) 1 and 1

**Answer: (B) 1 and 2**

**Solution:** `EXCEPT` removes duplicates and returns one remaining distinct tuple in the intended instance. `EXCEPT ALL` subtracts duplicate multiplicities rather than collapsing them, leaving two rows. The tuple values are absent in the supplied input, so the stated multiplicity cannot be checked against the instance.

> Note: The tuple values are missing from the supplied input; the answer follows the provided starred option and its described set-versus-bag distinction.

<a id="q20"></a>

### Q20. [GFG practice] Male department salary versus company average
Schema: `Emp(Empcode, Name, Sex, Salary, Deptt)`. The supplied query is:

```sql
SELECT Deptt FROM Emp
WHERE sex = 'M'
GROUP BY Dept
HAVING AVG(Salary) > (SELECT AVG(Salary) FROM Emp);
```

The output identifies departments where the:

(A) Average salary of male employees is the average salary of the organization.  
(B) Average salary of male employees is less than the average salary of the organization.  
(C) Average salary of male employees is equal to the average salary of the organization.  
(D) Average salary of male employees is more than the average salary of the organization.

**Answer: (D) Average salary of male employees is more than the average salary of the organization.**

**Solution:** The `WHERE` condition restricts each group to male employees. `HAVING` compares that group's average salary with the scalar average over all rows of `Emp`. Thus a returned department has a male-employee average above the company-wide average. (The supplied `GROUP BY Dept` differs from the schema's `Deptt`.)

<a id="q21"></a>

### Q21. [GATE CS Mock 2018] Identifying the third-highest distinct salary
The `EMPLOYEE` table contains:

| EmpId | EmpName | ManagerId | DeptId | Salary | DOB |
|---:|---|---:|---:|---:|---|
| 11 | Ram | 0 | 1 | 40000 | 01/01/1991 |
| 12 | Murali | 0 | 2 | 35000 | 21/02/1987 |
| 13 | Tarang | 1 | 1 | 30000 | 25/08/1989 |
| 15 | Lisa | 2 | 2 | 42000 | 31/05/1992 |
| 27 | Fatima | 2 | 1 | 39000 | 17/04/1990 |

The question asks what this query selects:

```sql
SELECT *
FROM EMPLOYEE E
WHERE 2 = (
  SELECT COUNT(DISTINCT E1.SALARY)
  FROM EMPLOYEE E1
  WHERE E1.SALARY > E.SALARY
);
```

(A) Second highest salary  
(B) Two distinct salary values of employees  
(C) Third highest salary  
(D) Employee with second highest salary

**Answer: (C) Third highest salary**

**Solution:** The subquery counts the distinct salary amounts above each employee's salary. Exactly two distinct values exceed 39000 (42000 and 40000), so the query returns the row(s) at the third-highest distinct salary. In this table that is Fatima, with salary 39000. The query returns the employee row, not just a scalar salary.

<a id="q22"></a>

### Q22. [GFG practice] When a Cartesian-product query returns relation R
Given relations `R(w,x)` and `S(y,z)`, when is the result of this query guaranteed to be the same as `R`?

```sql
SELECT DISTINCT w, x
FROM R, S;
```

(A) R has no duplicates and S is non-empty.  
(B) R and S have no duplicates.  
(C) S has no duplicates and R is non-empty.  
(D) R and S have the same number of tuples.

**Answer: (A) R has no duplicates and S is non-empty.**

**Solution:** With no join predicate, the `FROM` clause forms `R×S`. Each R tuple is repeated once per S tuple, and `DISTINCT` collapses those repetitions. The output equals R if R itself has no duplicates and S has at least one row; an empty S makes the product empty.

<a id="q23"></a>

### Q23. [GFG practice] Seven most expensive books
Relation `book(title, price)` contains book titles and prices; assume no two books have the same price. What does this query list?

```sql
SELECT title
FROM book AS B
WHERE (
  SELECT COUNT(*)
  FROM book AS T
  WHERE T.price > B.price
) < 7;
```

(A) Titles of the six most expensive books.  
(B) Title of the sixth most expensive book.  
(C) Titles of the seven most expensive books.  
(D) Title of the seventh most expensive book.

**Answer: (C) Titles of the seven most expensive books.**

**Solution:** For a book ranked from the top, the number of strictly more expensive books is its zero-based rank. The top seven have 0 through 6 more expensive books, all less than 7. The uniqueness assumption avoids ties.

<a id="q24"></a>

### Q24. [GATE CS 2021] Salary compared to the company average
In `emp(empId, name, gender, salary, deptId)`, `empId` is the key and each employee belongs to exactly one department. Consider:

```sql
SELECT deptId, COUNT(*)
FROM emp
WHERE gender = 'female'
  AND salary > (SELECT AVG(salary) FROM emp)
GROUP BY deptId;
```

For each department, the query counts female employees whose salary exceeds the average salary of:

(A) Employees in the department.  
(B) Employees in the company.  
(C) Female employees in the department.  
(D) Female employees in the company.

**Answer: (B) Employees in the company.**

**Solution:** The subquery has no correlation to the outer query and has no `WHERE` condition, so it averages salaries over the entire `emp` table. The outer filter then selects female employees above that company-wide average before grouping by department.

<a id="q25"></a>

### Q25. [GATE IT 2006] Maximum size of a join with a primary key
Relations `r1(P,Q,R)` and `r2(R,S,T)` have primary keys `P` and `R`, respectively. `r1` contains 2000 tuples and `r2` contains 2500 tuples. What is the maximum size of `r1 ⋈ r2`?

(A) 2000  
(B) 2500  
(C) 4500  
(D) 5000

**Answer: (A) 2000**

**Solution:** The natural join matches on the common attribute R. Since R is a key of r2, each r1 row can match at most one r2 row. Thus the join can have at most as many rows as r1: 2000. This maximum is achievable if every r1.R value appears in r2.

<a id="q26"></a>

### Q26. [GATE CS 2014] Foreign keys and composite referenced keys
Consider these statements:

S1: A foreign-key declaration can always be replaced by an equivalent SQL check assertion.

S2: Given table `R(a,b,c)` where `a` and `b` together form the primary key, the following is a valid table definition:

```sql
CREATE TABLE S (
  a INTEGER,
  d INTEGER,
  e INTEGER,
  PRIMARY KEY (d),
  FOREIGN KEY (a) REFERENCES R
);
```

Which is correct?

(A) S1 is TRUE and S2 is FALSE.  
(B) Both S1 and S2 are TRUE.  
(C) S1 is FALSE and S2 is TRUE.  
(D) Both S1 and S2 are FALSE.

**Answer: (D) Both S1 and S2 are FALSE.**

**Solution:** S1 is false: a check assertion is not generally an equivalent replacement for referential actions and integrity enforcement of a foreign key. S2 is false because `R(a,b)` is the composite primary key; `a` alone is not a candidate key that can be referenced. A foreign key must reference a declared unique key, and a matching referenced column list would be needed.

<a id="q27"></a>

### Q27. [GATE CS 2014] Employees whose customers all rate them good
Schema: `employee(empId, empName, empDept)` and `customer(custId, custName, salesRepId, rating)`. `salesRepId` is a foreign key to `employee.empId`. Assume every employee makes a sale to at least one customer. What does this query return?

```sql
SELECT empName
FROM employee E
WHERE NOT EXISTS (
  SELECT custId
  FROM customer C
  WHERE C.salesRepId = E.empId
    AND C.rating <> 'GOOD'
);
```

(A) Employees with at least one customer rated GOOD.  
(B) Employees with at most one customer rated GOOD.  
(C) Employees with no customers rated GOOD.  
(D) Employees whose customers are all rated GOOD.

**Answer: (D) Employees whose customers are all rated GOOD.**

**Solution:** The subquery searches for a customer of the current employee with a rating other than GOOD. `NOT EXISTS` keeps only employees for whom no such customer exists. Since each employee has at least one customer, all of each selected employee's customers have rating GOOD.

<a id="q28"></a>

### Q28. [GATE CS 2006] Comparing membership queries and joins
`enrolled(student, course)` has primary key `(student, course)`. `paid(student, amount)` has primary key `student`. Assume no null values and no foreign keys or other integrity constraints.

```sql
Query1: SELECT student FROM enrolled
        WHERE student IN (SELECT student FROM paid);

Query2: SELECT student FROM paid
        WHERE student IN (SELECT student FROM enrolled);

Query3: SELECT E.student FROM enrolled E, paid P
        WHERE E.student = P.student;

Query4: SELECT student FROM paid
        WHERE EXISTS (SELECT * FROM enrolled
                      WHERE enrolled.student = paid.student);
```

Which statement is correct?

(A) All queries return identical row sets for every database.  
(B) Query2 and Query4 return identical row sets for every database, but some database makes Query1 and Query2 differ.  
(C) Some database makes Query3 return strictly fewer rows than Query2.  
(D) Some database makes Query4 encounter an integrity violation at runtime.

**Answer: (B)**

**Solution:** `paid.student` is unique, so Query2 and Query4 each return a paid student once exactly when that student occurs in enrolled. Query1 reads from enrolled, where a student may appear in several courses, so it can repeat that student. For example, a paid student enrolled in two courses appears twice in Query1 but once in Query2. Query3's join likewise can repeat matches; it does not return fewer than Query2.

<a id="q29"></a>

### Q29. [GFG practice] Automatic action after database modification
Which statement is executed automatically by the system as a side effect of a database modification?

(A) Backup  
(B) Assertion  
(C) Recovery  
(D) Trigger

**Answer: (D) Trigger**

**Solution:** A trigger is defined to execute automatically in response to specified database events, such as an insert, update, or delete. The other choices are not event-fired SQL actions of this kind.

<a id="q30"></a>

### Q30. [GATE CS 2004] Minimum and maximum natural-join sizes
Schema:

```text
Student(rollno, name, address)
Enroll(rollno, courseno, coursename)
```

The primary keys are underlined in the original question; the numbers of tuples in Student and Enroll are 120 and 8, respectively. What are the maximum and minimum numbers of tuples in `Student ⋈ Enroll` (`⋈` is natural join)?

(A) 8, 8  
(B) 120, 8  
(C) 960, 8  
(D) 960, 120

**Answer: (A) 8, 8**

**Solution:** The common attribute is `rollno`. Under the intended student-enrollment interpretation, each of the eight enrollment rows references one student, and `Student.rollno` is unique, so each enrollment matches exactly one student. The join therefore has eight rows at both its minimum and maximum under that intended foreign-key assumption. If only the explicitly stated primary-key constraints are enforced and there is no foreign key from `Enroll.rollno`, the minimum could instead be zero; the question omits that constraint.

<a id="q31"></a>

### Q31. [GATE CS 2012] `HAVING` and `GROUP BY` statements
Which statements are true about an SQL query?

P: An SQL query can contain a `HAVING` clause even if it does not have a `GROUP BY` clause.  
Q: An SQL query can contain a `HAVING` clause only if it has a `GROUP BY` clause.  
R: All attributes used in the `GROUP BY` clause must appear in the `SELECT` clause.  
S: Not all attributes used in the `GROUP BY` clause need to appear in the `SELECT` clause.

(A) P and R  
(B) P and S  
(C) Q and R  
(D) Q and S

**Answer: (C) Q and R (official GATE key)**

**Solution:** The official GATE key is reported as (C), applying the exam's interpretation that `HAVING` requires `GROUP BY` and grouped attributes must appear in the select list. However, standard SQL permits `HAVING` without an explicit `GROUP BY` (the input is treated as one group), and it does not require every grouping attribute to be selected. Under standard SQL, P and S are true, so (B) is the technically correct standards-based choice.

> Note: GFG marks (B); the official GATE key is (C), although standard SQL supports (B).

<a id="q32"></a>

### Q32. [GFG practice] Command that removes a table
Which SQL command is used to delete a table?

(A) `DELETE`  
(B) `TRUNCATE`  
(C) `REMOVE`  
(D) `DROP`

**Answer: (D) `DROP`**

**Solution:** `DROP TABLE` removes the table definition and its data. `DELETE` removes rows, and `TRUNCATE` empties a table while leaving its definition in place.

<a id="q33"></a>

### Q33. [GATE CS 2004] Male department averages above company average
Employee information is stored in `Employee(name, sex, salary, deptName)`. Consider:

```sql
SELECT deptName
FROM Employee
WHERE sex = 'M'
GROUP BY deptName
HAVING AVG(salary) > (SELECT AVG(salary) FROM Employee);
```

It returns department names for departments in which:

(A) The average salary is greater than the average salary in the company.  
(B) The average salary of male employees is greater than the average salary of all male employees in the company.  
(C) The average salary of male employees is greater than the average salary of employees in the same department.  
(D) The average salary of male employees is greater than the average salary in the company.

**Answer: (D) The average salary of male employees is greater than the average salary in the company.**

**Solution:** The `WHERE` clause leaves only male employees before the rows are grouped by department, so each group's `AVG(salary)` is a male-only departmental average. The uncorrelated scalar subquery computes the average over all employees. The `HAVING` condition compares those values, matching D.

<a id="q34"></a>

### Q34. [GATE CS 2015] SQL `SELECT` and relational algebra
Select operation in SQL is equivalent to which relational-algebra operation?

(A) Selection in relational algebra  
(B) Selection in relational algebra, except SQL `SELECT` retains duplicates  
(C) Projection in relational algebra  
(D) Projection in relational algebra, except SQL `SELECT` retains duplicates

**Answer: (D) Projection in relational algebra, except SQL `SELECT` retains duplicates**

**Solution:**
1. Relational-algebra projection chooses columns and removes duplicate rows.
2. SQL `SELECT` also chooses columns, but keeps duplicates unless `DISTINCT` is specified. Thus it corresponds to projection with bag/duplicate retention.

<a id="q35"></a>

### Q35. [GATE IT 2005] Comparing SQL and relational-algebra row counts
The tables are:

**Student(roll, name, hostel, marks)**

| roll | name | hostel | marks |
|---:|---|---:|---:|
| 1798 | Manoj Rathod | 7 | 95 |
| 2154 | Soumic Banerjee | 5 | 68 |
| 2369 | Gumma Reddy | 7 | 86 |
| 2581 | Pradeep Pendse | 6 | 92 |
| 2643 | Suhas Kulkarni | 5 | 78 |
| 2711 | Nitin Kadam | 8 | 72 |
| 2872 | Kiran Vora | 5 | 92 |
| 2926 | Manoj Kunkalikar | 5 | 94 |
| 2959 | Hemant Karkhanis | 7 | 88 |
| 3125 | Rajesh Doshi | 5 | 82 |

**Hobby(roll, hobbyname)**

| roll | hobbyname |
|---:|---|
| 1798 | chess |
| 1798 | music |
| 2154 | music |
| 2369 | swimming |
| 2581 | cricket |
| 2643 | chess |
| 2643 | hockey |
| 2711 | volleyball |
| 2872 | football |
| 2926 | cricket |
| 2959 | photography |
| 3125 | music |
| 3125 | chess |

Compare the number of rows from this SQL query with the number of tuples in the relational-algebra result below. What is the difference?

```sql
SELECT hostel
FROM student NATURAL JOIN hobby
WHERE marks >= 75 AND roll BETWEEN 2000 AND 3000;
```

`S` and `H` contain the same tuples as Student and Hobby. The relational-algebra expression is:

`S' = π_hostel( σ_(S.roll = H.roll)( σ_(marks > 75 AND roll > 2000 AND roll < 3000)(S) × H ) )`

(A) 6  
(B) 4  
(C) 2  
(D) 0

**Answer: (B) 4**

**Solution:**
1. The SQL join returns seven rows: rolls 2369, 2581, 2643 twice (two hobbies), 2872, 2926, and 2959. It uses `>= 75` and includes the `BETWEEN` endpoints.
2. Relational-algebra projection removes duplicates. Its stricter predicates (`marks > 75`, `roll > 2000`, `roll < 3000`) leave three distinct hostel values: 5, 6, and 7.
3. The difference is `7 − 3 = 4`.

<a id="q36"></a>

### Q36. [GATE CS 2007] Salaries higher than every salary in a department
For `employee(empId, name, department, salary)`, assume department 5 has more than one employee. We want employees whose salary is higher than every salary in department 5. Which statement is true for every possible employee table?

```sql
Q1: SELECT e.empId
    FROM employee e
    WHERE NOT EXISTS
          (SELECT * FROM employee s
           WHERE s.department = '5' AND s.salary >= e.salary);

Q2: SELECT e.empId
    FROM employee e
    WHERE e.salary > ANY
          (SELECT DISTINCT salary FROM employee s
           WHERE s.department = '5');
```

(A) Q1 is correct  
(B) Q2 is correct  
(C) Both give the same answer  
(D) Neither is correct

**Answer: (A) Q1 is correct**

**Solution:**
1. Q1 returns an employee only if no department-5 salary is greater than or equal to theirs. This means their salary is strictly greater than every department-5 salary.
2. `> ANY` in Q2 means greater than at least one value, not all values. It can include employees who are below the department's maximum, so Q2 does not meet the requirement.

<a id="q37"></a>

### Q37. [GATE CS 2014] Latest hires in departments at a location
Given:

- `employees(emp-id, first-name, last-name, hire-date, dept-id, salary)`
- `departments(dept-id, dept-name, manager-id, location-id)`

The goal is to display last names and hire dates for all latest hires in their departments at location 1700. What is the outcome of this query?

```sql
SELECT last-name, hire-date
FROM employees
WHERE (dept-id, hire-date) IN
      (SELECT dept-id, MAX(hire-date)
       FROM employees JOIN departments USING (dept-id)
       WHERE location-id = 1700
       GROUP BY dept-id);
```

(A) It executes but does not give the correct result.  
(B) It executes and gives the correct result.  
(C) It generates an error because of pairwise comparison.  
(D) It generates an error because `GROUP BY` cannot be used with table joins in a subquery.

**Answer: (B) It executes and gives the correct result**

**Solution:**
1. The subquery returns one `(dept-id, latest hire-date)` pair per department at location 1700.
2. SQL permits a row-value pair to be tested with `IN` against a two-column subquery.
3. The outer query returns every employee whose department/date pair matches, including ties for latest date. A grouped join in a subquery is valid.

<a id="q38"></a>

### Q38. [GATE CS 2014] `IN` subquery versus join duplicates
SQL results can contain duplicate tuples. Which query always returns the same result as the nested query?

```sql
SELECT * FROM R WHERE a IN (SELECT S.a FROM S);
```

(A) `SELECT R.* FROM R, S WHERE R.a = S.a`  
(B) `SELECT DISTINCT R.* FROM R, S WHERE R.a = S.a`  
(C) `SELECT R.* FROM R, (SELECT DISTINCT a FROM S) AS S1 WHERE R.a = S1.a`  
(D) `SELECT R.* FROM R, S WHERE R.a = S.a AND IS UNIQUE R`

**Answer: (C) Join with the distinct values of `S.a`**

**Solution:**
1. `IN` tests whether a value occurs at least once. Repeated matching values in `S` do not multiply an `R` row, and duplicate rows already in `R` remain duplicates.
2. The distinct subquery creates one join-side row per `a`, so the join preserves exactly the multiplicity from `R`.
3. A direct join can multiply rows when `S.a` repeats (A); `DISTINCT R.*` can wrongly collapse duplicate rows from `R` (B).

<a id="q39"></a>

### Q39. [GATE CS 2006] Two SQL attempts to assign ranks
`account(customer, balance)` has `customer` as its primary key and no nulls. Customers are ranked by decreasing balance: a largest balance gets rank 1; ties share a rank and later ranks are skipped (if two customers tie for first, rank 2 is skipped).

```sql
Query1:
SELECT A.customer, COUNT(B.customer)
FROM account A, account B
WHERE A.balance <= B.balance
GROUP BY A.customer;

Query2:
SELECT A.customer, 1 + COUNT(B.customer)
FROM account A, account B
WHERE A.balance < B.balance
GROUP BY A.customer;
```

Consider these statements:
1. Query1 and Query2 give the same row set for some, but not all, databases.
2. Both queries implement the specification.
3. Query1 implements the specification, but Query2 does not.
4. Neither query implements the specification.
5. A pure relational query assigns rank faster than scanning in decreasing balance order and assigning ranks with ODBC.

Which two statements are correct?

(A) 2 and 5  
(B) 1 and 3  
(C) 1 and 4  
(D) 3 and 5

**Answer: (C) 1 and 4**

**Solution:**
1. Query1 counts customers with balance `>=` A's balance (including A itself). With a tie at the top, both tied customers get rank 2 instead of 1 → Query1 is wrong.
2. Query2 counts customers with a strictly greater balance and adds 1, which would give correct ranks — **but** it is an inner join. The customer(s) with the highest balance have no `B` row with a larger balance, so they produce no rows at all and are **missing from the output**. Query2 is also wrong.
3. So neither query implements the specification → statement 4 is true; 2 and 3 are false.
4. Statement 1: when balances are all distinct, every non-top customer gets the same number from both queries, but the row sets still differ for the top customer; for some databases (for example, an empty table) the outputs are identical, so "same for some but not all databases" holds.
5. Statement 5 is false: the self-join is quadratic, while one sorted scan is linear.

<a id="q40"></a>

### Q40. [GATE CS 2005] Cascading deletes through a self-reference
A table has attributes `A` and `C`; `A` is the primary key and `C` is a foreign key referencing `A` with `ON DELETE CASCADE`.

| A | C |
|---:|---:|
| 2 | 4 |
| 3 | 4 |
| 4 | 3 |
| 5 | 2 |
| 7 | 2 |
| 9 | 5 |
| 6 | 4 |

When tuple `(2,4)` is deleted, which tuples must additionally be deleted to preserve referential integrity?

(A) `(3,4)` and `(6,4)`  
(B) `(5,2)` and `(7,2)`  
(C) `(5,2)`, `(7,2)`, and `(9,5)`  
(D) `(3,4)`, `(4,3)`, and `(6,4)`

**Answer: (C) `(5,2)`, `(7,2)`, and `(9,5)`**

**Solution:**
1. Deleting key value 2 cascades to rows whose `C=2`: `(5,2)` and `(7,2)`.
2. Row `(9,5)` references key 5, which was just deleted, so it is also cascaded.
3. No row references 7 or 9, so the cascade stops there.

<a id="q41"></a>

### Q41. [GATE CS 2005] Selecting the five most expensive books
`book(title, price)` has no two books with the same price. What does this query list?

```sql
SELECT title
FROM book AS B
WHERE (SELECT COUNT(*)
       FROM book AS T
       WHERE T.price > B.price) < 5;
```

(A) Titles of the four most expensive books  
(B) Title of the fifth most inexpensive book  
(C) Title of the fifth most expensive book; titles of the five most expensive books  
(D) Titles of the five most expensive books

**Answer: (D) Titles of the five most expensive books**

**Solution:**
1. For each book, the correlated subquery counts how many books cost more.
2. The most expensive book has count 0, the next has 1, and so on. Counts less than 5 select exactly the top five.

<a id="q42"></a>

### Q42. [GATE CS 2003] SQL query and relational algebra
For arbitrary predicate `P`, which relational-algebra expression is equivalent to this query?

```sql
SELECT DISTINCT a1, a2, ..., an
FROM r1, r2, ..., rm
WHERE P;
```

(A) `π_a1,...,an (σ_P (r1 × r2 × ... × rm))`  
(B) `π_a1,...,an (σ_P (r1 ⋈ r2 ⋈ ... ⋈ rm))`  
(C) `π_a1,...,an (σ_P (r1 ∪ r2 ∪ ... ∪ rm))`  
(D) `π_a1,...,an (σ_P (r1 ∩ r2 ∩ ... ∩ rm))`

**Answer: (A) Projection after selection from the Cartesian product**

**Solution:**
1. Listing several tables in `FROM` forms their Cartesian product.
2. `WHERE P` selects rows satisfying `P`; selecting the listed attributes projects them.
3. Relational-algebra projection removes duplicates, matching SQL `DISTINCT`.

<a id="q43"></a>

### Q43. [GATE CS 2003] Names of students with an A in a Korth course
The relations are `Students(Roll_number, Name, Date_of_birth)`, `Courses(Course_number, Course_name, Instructor)`, and `Grades(Roll_number, Course_number, Grade)`. Consider:

```sql
SELECT DISTINCT Name
FROM Students, Courses, Grades
WHERE Students.Roll_number = Grades.Roll_number
  AND Courses.Instructor = 'Korth'
  AND Courses.Course_number = Grades.Course_number
  AND Grades.Grade = 'A';
```

Which set is computed?

(A) Students who got an A in all courses taught by Korth  
(B) Students who got an A in all courses  
(C) Students who got an A in at least one course taught by Korth  
(D) None of the above

**Answer: (C) Students who got an A in at least one course taught by Korth**

**Solution:**
1. The joins find grade records for the student and course, and the conditions retain only Korth-taught courses with grade A.
2. A student needs just one matching record to appear. `DISTINCT` removes repeated names; there is no condition requiring an A in every course.

<a id="q44"></a>

### Q44. [GATE CS 2000] Distinct projection of a Cartesian product
Given relations `r(w,x)` and `s(y,z)`, when is the result guaranteed to equal `r`?

```sql
SELECT DISTINCT w, x
FROM r, s;
```

(A) `r` has no duplicates and `s` is non-empty  
(B) `r` and `s` have no duplicates  
(C) `s` has no duplicates and `r` is non-empty  
(D) `r` and `s` have the same number of tuples

**Answer: (A) `r` has no duplicates and `s` is non-empty**

**Solution:**
1. The Cartesian product has at least one copy of each `r` tuple exactly when `s` is non-empty.
2. Projecting `w,x` with `DISTINCT` then returns the distinct tuples of `r`. This equals `r` precisely when `r` itself has no duplicates.

<a id="q45"></a>

### Q45. [GATE CS 2000] SQL comparisons when null is treated as false
Suppose comparisons with `NULL` are treated as false. Which pair of expressions is not equivalent?

(A) `x = 5` and `NOT (NOT (x = 5))`  
(B) `x = 5` and `x > 4 AND x < 6`, where `x` is an integer  
(C) `x <> 5` and `NOT (x = 5)`  
(D) None of the above

**Answer: (C) `x <> 5` and `NOT (x = 5)`**

**Solution:**
1. If `x` is null, each comparison is false by the question's assumption.
2. In (C), `x <> 5` is false, while `NOT (x=5)` is true. The expressions therefore differ for null.
3. In (A), double negation preserves the result. For integer `x`, the condition in (B) is true exactly when `x=5`.

<a id="q46"></a>

### Q46. [GATE CS 2015 Mock] Students enrolled in both DBMS and OS
Tables: `Student(EnrollNo, Name)`, `Course(CourseID, Name)`, and `Enrollments(EnrollNo, CourseID)`. What does this query return?

```sql
SELECT S.Name
FROM Student S, Course C, Enrollments E
WHERE S.EnrollNo = E.EnrollNo
  AND C.Name = 'DBMS'
  AND E.CourseID = C.CourseID
  AND S.EnrollNo IN
      (SELECT S2.EnrollNo
       FROM Student S2, Course C2, Enrollments E2
       WHERE S2.EnrollNo = E2.EnrollNo
         AND E2.CourseID = C2.CourseID
         AND C2.Name = 'OS');
```

(A) Names of students enrolled in DBMS or OS  
(B) Names of students enrolled in both DBMS and OS  
(C) Names of students enrolled in DBMS, OS, or both  
(D) None of the above

**Answer: (B) Names of students enrolled in both DBMS and OS**

**Solution:**
1. The outer query returns students enrolled in DBMS.
2. The `IN` subquery returns enrollment numbers for students enrolled in OS.
3. The outer `IN` condition keeps the intersection: students enrolled in both courses.

<a id="q47"></a>

### Q47. [GATE CS 2015 Mock] Employees with salary above a CS employee
The `Employee(ID, salary, DeptName)` table contains:

| ID | salary | DeptName |
|---:|---:|---|
| 1 | 10000 | EC |
| 2 | 40000 | EC |
| 3 | 30000 | CS |
| 4 | 40000 | ME |
| 5 | 50000 | ME |
| 6 | 60000 | ME |
| 7 | 70000 | CS |

How many rows does the following query return?

```sql
SELECT E.ID
FROM Employee E
WHERE EXISTS
      (SELECT E2.salary
       FROM Employee E2
       WHERE E2.DeptName = 'CS'
         AND E.salary > E2.salary);
```

(A) 6  
(B) 5  
(C) 4  
(D) 0

**Answer: (B) 5**

**Solution:**
1. The CS salaries are 30000 and 70000. `EXISTS` is true when the employee's salary exceeds at least one of these, so it must exceed 30000.
2. IDs 2, 4, 5, 6, and 7 qualify. The 10000 and 30000 salaries do not.

<a id="q48"></a>

### Q48. [GATE CS 2015] SQL aggregate over an image table
The figure in the question gives `Student` and `Performance` relations. The query is:

```sql
SELECT S.Student_Name, SUM(P.Marks)
FROM Student S, Performance P
WHERE S.Roll_No = P.Roll_No
GROUP BY S.Student_Name;
```

How many rows are returned?

(A) 0  
(B) 1  
(C) 2  
(D) 3

> Note: The original figure contains Student and Performance tables and is not reproduced. The accompanying worked result identifies the two grouped names as Raj (sum 310) and Rohit (sum 140).

**Answer: (C) 2**

**Solution:**
1. The join matches performance records to students by roll number.
2. Grouping by `Student_Name` produces one result row per distinct student name with a match.
3. The figure's result has two names, Raj and Rohit, so there are two rows.

<a id="q49"></a>

### Q49. [GATE CS 2015] Finding addresses of maximum-capacity theaters
For relation `Cinema(theater, address, capacity)`, which condition should finish this query so it always finds the addresses of theaters with maximum capacity?

```sql
SELECT P1.address
FROM Cinema P1
-- condition goes here
```

(A) `WHERE P1.capacity >= ALL (SELECT P2.capacity FROM Cinema P2)`  
(B) `WHERE P1.capacity >= ANY (SELECT P2.capacity FROM Cinema P2)`  
(C) `WHERE P1.capacity > ALL (SELECT MAX(P2.capacity) FROM Cinema P2)`  
(D) `WHERE P1.capacity > ANY (SELECT MAX(P2.capacity) FROM Cinema P2)`

**Answer: (A) `P1.capacity >= ALL (...)`**

**Solution:**
1. `>= ALL` means the capacity is at least every capacity in the table, i.e. it equals the maximum. It returns all tied maximum-capacity theaters.
2. `>= ANY` only requires beating one capacity. Options C and D compare strictly greater than the maximum (or its single aggregate value), so they return no maximum row.

<a id="q50"></a>

### Q50. [GATE CS 2015] Commission updates in separate transactions
The table is `salesinfo(salespersonid, totalsales, commission)`. Three separate transactions are:

```sql
T1: UPDATE salesinfo
    SET commission = commission * 1.02
    WHERE commission <= 50000;

T2: UPDATE salesinfo
    SET commission = commission * 1.04
    WHERE commission > 50000 AND commission <= 100000;

T3: UPDATE salesinfo
    SET commission = commission * 1.06
    WHERE commission > 100000;
```

Which execution order updates every commission correctly?

(A) T1, then T2, then T3  
(B) T2, then T3, with T1 concurrent throughout  
(C) T3, then T2, with T1 concurrent throughout  
(D) T3, then T2, then T1

**Answer: (D) T3, then T2, then T1**

**Solution:**
1. Each update changes the commission, which can move a salesperson into a higher slab.
2. Process the highest slab first, then the middle, then the lowest. This prevents a row updated in a lower slab from being picked up again by a later higher-slab transaction.
3. For example, 99,999 becomes 103,998 in T2; because T3 has already run, the employee receives only the intended 4% enhancement.

<a id="q51"></a>

### Q51. [GFG practice] Correlated query for the five highest book prices
`book(title, price)` contains distinct prices. What does this query list?

```sql
SELECT title
FROM book AS B
WHERE (SELECT COUNT(*)
       FROM book AS T
       WHERE T.price > B.price) < 5;
```

(A) Titles of the four most expensive books  
(B) Title of the fifth most inexpensive book  
(C) Title of the fifth most expensive book  
(D) Titles of the five most expensive books

**Answer: (D) Titles of the five most expensive books**

**Solution:**
1. For a given book, the subquery counts books with higher prices.
2. The five most expensive books have respectively 0, 1, 2, 3, and 4 books above them. All satisfy `< 5`.

<a id="q52"></a>

### Q52. [GATE IT 2005] Suppliers with multiple items at Nagpur
`Supply(supplierid, itemcode)` records which items suppliers supply. `Inventory(itemcode, warehouse, stocklevel)` records items at warehouses. What suppliers does this query find for Nagpur?

```sql
SELECT DISTINCT STMP.supplierid
FROM Supply AS STMP
WHERE NOT UNIQUE
      (SELECT ITMP.supplierid
       FROM Inventory, Supply AS ITMP
       WHERE STMP.supplierid = ITMP.supplierid
         AND ITMP.itemcode = Inventory.itemcode
         AND Inventory.warehouse = 'Nagpur');
```

(A) Suppliers who do not supply any item  
(B) Suppliers who supply exactly one item  
(C) Suppliers who supply one or more items  
(D) Suppliers who supply two or more items

**Answer: (D) Suppliers who supply two or more items**

**Solution:**
1. For each outer supplier, the subquery returns that supplier ID once for each supplied item matched to inventory in Nagpur.
2. `NOT UNIQUE` is true when the subquery result contains duplicates. That requires at least two matching item rows.

<a id="q53"></a>

### Q53. [GATE CS 2016] District totals at or above average
An image shows the rows in `water_schemes`. The query groups capacities by district, computes the average of those totals, and selects names whose total is at least that average:

```sql
WITH total(name, capacity) AS
     (SELECT district_name, SUM(capacity)
      FROM water_schemes
      GROUP BY district_name),
     total_avg(capacity) AS
     (SELECT AVG(capacity) FROM total)
SELECT name
FROM total, total_avg
WHERE total.capacity >= total_avg.capacity;
```

How many tuples are returned?

(A) 1  
(B) 2  
(C) 3  
(D) 4

> Note: Original figure not reproduced. Its district totals are Ajmer 20, Bikaner 40, Charu 30, and Dungargarh 10.

**Answer: (B) 2**

**Solution:**
1. The average of the four district totals is `(20 + 40 + 30 + 10) / 4 = 25`.
2. Bikaner (40) and Charu (30) are at least 25. Thus two names are returned.

<a id="q54"></a>

### Q54. [GATE IT 2008] Number of 100 marks in large schools
Schemas: `Student(school-id, sch-roll-no, sname, saddress)`, `School(school-id, sch-name, sch-address, sch-phone)`, `Enrolment(school-id, sch-roll-no, erollno, examname)`, and `ExamResult(erollno, examname, marks)`. What does the following query output?

```sql
SELECT sch-name, COUNT(*)
FROM School C, Enrolment E, ExamResult R
WHERE E.school-id = C.school-id
  AND E.examname = R.examname
  AND E.erollno = R.erollno
  AND R.marks = 100
  AND S.school-id IN
      (SELECT school-id
       FROM student
       GROUP BY school-id
       HAVING COUNT(*) > 200)
GROUP BY school-id;
```

(A) For each school with over 200 students appearing in exams: its name and number of 100s scored by its students  
(B) For each school with over 200 students: its name and number of 100s scored by its students  
(C) For each school with over 200 students: its name and number of students scoring 100 in at least one exam  
(D) Nothing; the query has a syntax error

**Answer: (D) Nothing; the query has a syntax error**

**Solution:**
1. The query refers to alias `S` in `S.school-id`, but there is no table alias `S` in the outer `FROM` clause.
2. Also, `sch-name` is selected while the query groups only by `school-id`; the query as written is invalid under the stated SQL grouping rules.

<a id="q55"></a>

### Q55. [GATE CS 1999] Basic SQL properties
Which statement is correct?

(A) An SQL query automatically eliminates duplicates.  
(B) An SQL query will not work if the relations have no indexes.  
(C) SQL permits attribute names to be repeated in the same relation.  
(D) None of the above.

**Answer: (D) None of the above**

**Solution:**
1. SQL normally preserves duplicates; `DISTINCT` is needed to remove them, so A is false.
2. Indexes can improve performance but are not required for queries to work, so B is false.
3. A relation's attributes must be distinguishable by their names, so C is false.

<a id="q56"></a>

### Q56. [GATE CS 1998] Students frequenting a parlor serving an ice-cream they like
Relations: `FREQUENTS(student, parlor)` gives parlors each student visits; `SERVES(parlor, ice-cream)` gives flavors served; `LIKES(student, ice-cream)` gives flavors liked. Each student likes at least one flavor and visits at least one parlor. Write SQL to print students who frequent at least one parlor serving some flavor they like.

**Answer: SQL query:**

```sql
SELECT DISTINCT F.student
FROM FREQUENTS AS F
JOIN SERVES AS S ON F.parlor = S.parlor
JOIN LIKES AS L ON L.student = F.student
               AND L.ice_cream = S.ice_cream;
```

**Solution:**
1. The first join connects each visited parlor to the flavors it serves.
2. The next join keeps only served flavors that the same student likes.
3. `DISTINCT` prints a student once even if several visited parlors/flavors match.

<a id="q57"></a>

### Q57. [GATE CS 1998] Courses whose prerequisites are all completed
Relations:

- `COURSES(Cno, name)` lists available courses.
- `PRE-REQ(Cno, pre_Cno)` lists a prerequisite for a course.
- `COMPLETED(student_no, Cno)` lists courses completed by students.

Express in relational algebra: list all courses for which student 2310 has completed all prerequisites.

**Answer: Relational-algebra expression:**

Let `Done = ρ_pre_Cno←Cno(π_Cno(σ_student_no=2310(COMPLETED)))`. Then define missing prerequisites as:

`Missing = π_Cno,pre_Cno(PRE-REQ) − π_Cno,pre_Cno(PRE-REQ ⋈_(PRE-REQ.pre_Cno = Done.pre_Cno) Done)`

The requested course IDs are:

`π_Cno(COURSES) − π_Cno(Missing)`

**Solution:**
1. `Done` renames the completed course number to `pre_Cno` so it can match the prerequisite field.
2. Subtracting completed prerequisite pairs from all prerequisite pairs leaves the missing pairs.
3. Any course appearing in `Missing` has at least one unmet prerequisite. Subtract those from all course IDs; courses with no prerequisites remain included, as required by “all.”

<a id="q58"></a>

### Q58. [GATE CS 1997] Employee/project relational algebra
Schemas: `EMP(eno, name, age)`, `PROJ(pno, name)`, and `INVOLVED(eno, pno)`. The underlined attributes are primary keys. `EMP` stores employees, `PROJ` projects, and `INVOLVED` which employees participate in which projects.

(a) Give an expression using one or more of `{σ, π, ×, ∪, −}` equivalent to:

```sql
SELECT eno
FROM EMP, INVOLVED
WHERE EMP.eno = INVOLVED.eno
  AND INVOLVED.pno = 3;
```

(b) In English (at most 15 words), state what each expression determines:

(i) `π_eno(INVOLVED) − π_eno((π_eno(INVOLVED) × π_pno(PROJ)) − INVOLVED)`  
(ii) `π_age(EMP) − π_Eage<EMP.age(ρ_E(EMP) × EMP)`

**Answer:**

(a) `π_EMP.eno(σ_EMP.eno=INVOLVED.eno ∧ INVOLVED.pno=3(EMP × INVOLVED))`

(b) (i) Employees involved in every project. (ii) The maximum employee age.

**Solution:**
1. In (a), form all employee/involvement pairs, keep matching employee IDs and project 3, then project the employee ID.
2. In (b)(i), the product lists every employee/project pair. Subtracting actual involvement finds missing pairs; subtracting employees with a missing pair leaves those involved in all projects.
3. In (b)(ii), the comparison selects ages that have a larger age in the relation. Removing those from all ages leaves the maximum age value(s).

<a id="q59"></a>

### Q59. [GATE CS 2018 Mock] Query for the third-highest salary
Given `EmployeeDetail(EmpId, FullName, ManagerID, DateOfJoining)` and `EmployeeSalary(EmpID, Project, Salary)`, assume both relations are nonempty. Interpret:

```sql
SELECT Salary
FROM EmployeeSalary Emp1
WHERE 2 =
      (SELECT COUNT(DISTINCT Emp2.Salary)
       FROM EmployeeSalary Emp2
       WHERE Emp2.Salary > Emp1.Salary);
```

(A) Find the highest salary  
(B) Find the second-highest salary  
(C) Find the third-highest salary  
(D) None of the above

**Answer: (C) Find the third-highest salary**

**Solution:**
1. For each row, the subquery counts distinct salary values above its salary.
2. Exactly two distinct salary levels above means this is the third-highest distinct salary. Duplicate rows at the same salary do not change the rank.

<a id="q60"></a>

### Q60. [GATE CS 2018] Which join query is a superset?
Given `Book(isbn, bname)` and `Stock(isbn, copies)`, consider:

```sql
Query 1:
SELECT B.isbn, S.copies
FROM Book B INNER JOIN Stock S ON B.isbn = S.isbn;

Query 2:
SELECT B.isbn, S.copies
FROM B B LEFT OUTER JOIN Stock S ON B.isbn = S.isbn;

Query 3:
SELECT B.isbn, S.copies
FROM Book B RIGHT OUTER JOIN Stock S ON B.isbn = S.isbn;

Query 4:
SELECT B.isbn, S.copies
FROM B B FULL OUTER JOIN Stock S ON B.isbn = S.isbn;
```

Which query is certain to have output that is a superset of the outputs of the other three?

(A) Query 1  
(B) Query 2  
(C) Query 3  
(D) Query 4

**Answer: (D) Query 4**

**Solution:**
1. A full outer join includes all matching rows plus unmatched rows from both sides.
2. It therefore includes the inner, left-outer, and right-outer join results. (The two `FROM B B` occurrences appear to be source typos for `Book B`.)

<a id="q61"></a>

### Q61. [GFG practice] What defines a database view?
Which statement(s) about a DBMS view is/are true?

(a) A view is a special stored procedure executed when a certain event occurs.  
(b) A view is a virtual table produced by executing a precompiled query.

(A) Only (a)  
(B) Only (b)  
(C) Both (a) and (b)  
(D) Neither (a) nor (b)

**Answer: (B) Only (b)**

**Solution:**
1. A view is a named virtual table defined by a query; it is not an event-triggered stored procedure.
2. Thus (b) is the true description.

<a id="q62"></a>

### Q62. [GFG practice] SQL aggregate function
Which of the following is an aggregate function in SQL?

(A) `SELECT`  
(B) `CREATE`  
(C) `AVG`  
(D) `MODIFY`

**Answer: (C) `AVG`**

**Solution:** `AVG` computes one average over a set of values (or per group). `SELECT` is a query clause/statement and `CREATE` is a schema command, not aggregate functions.

<a id="q63"></a>

### Q63. [GFG practice] SQL command that changes record fields
Which SQL command changes one or more fields in a record?

(A) LOOK-UP  
(B) INSERT  
(C) MODIFY  
(D) CHANGE

**Answer: No correct option; the standard SQL command is `UPDATE`.**

**Solution:** `UPDATE table SET column = value ...` changes existing row fields. `INSERT` adds a row, and `MODIFY` / `CHANGE` are not the standard SQL DML command for updating record values.

> Note: GFG marks (C); standard SQL uses `UPDATE`, which is not among the choices.

<a id="q64"></a>

### Q64. [GFG practice] Sailors query with grouping and `HAVING`
For `Sailors(sid, sname, rating, age)`, the data is:

| sid | sname | rating | age |
|---:|---|---:|---:|
| 22 | Dustin | 7 | 45 |
| 29 | Borg | 1 | 33 |
| 31 | Pathy | 8 | 55 |
| 32 | Robert | 8 | 25 |
| 58 | Raghu | 10 | 17 |
| 64 | Herald | 7 | 35 |
| 71 | Vishnu | 10 | 16 |
| 74 | King | 9 | 35 |
| 85 | Archer | 3 | 26 |
| 84 | Bob | 3 | 64 |
| 96 | Flinch | 3 | 17 |

How many rows does this query return?

```sql
SELECT S.rating, AVG(S.age) AS avgage
FROM Sailors S
WHERE S.age >= 18
GROUP BY S.rating
HAVING 1 < (SELECT COUNT(*)
            FROM Sailors S2
            WHERE S.rating = S2.rating);
```

(A) 6  
(B) 5  
(C) 4  
(D) 3

**Answer: (D) 3**

**Solution:**
1. The correlated `HAVING` count checks all Sailors at a rating, including sailors younger than 18; the `WHERE` filters only the rows used in the outer groups and averages.
2. Ratings 3 (three sailors), 7 (two), 8 (two), and 10 (two) meet the count condition, but rating 10 has no age-eligible row and so forms no group in the outer query.
3. Ratings 3, 7, and 8 remain: three result rows.

<a id="q65"></a>

### Q65. [GFG practice] Cartesian product and distinct projection
Given relations `R1(A,B)` and `R2(C,D)`, when is this query guaranteed to return exactly `R1`?

```sql
SELECT DISTINCT A, B
FROM R1, R2;
```

(A) `R1` has no duplicates and `R2` is empty  
(B) `R1` has no duplicates and `R2` is non-empty  
(C) Both `R1` and `R2` have no duplicates  
(D) `R2` has no duplicates and `R1` is non-empty

**Answer: (B) `R1` has no duplicates and `R2` is non-empty**

**Solution:**
1. A non-empty `R2` ensures every `R1` row occurs in the Cartesian product.
2. `DISTINCT A,B` returns the distinct `R1` tuples, so this equals `R1` when `R1` has no duplicates.

<a id="q66"></a>

### Q66. [GFG practice] Natural join of projected overtime data
What is the output of this query?

```sql
SELECT COUNT(*)
FROM ((SELECT Employee, Department FROM Overtime_allowance) AS S
      NATURAL JOIN
      (SELECT Department, OT_allowance FROM Overtime_allowance) AS T);
```

(A) 16  
(B) 4  
(C) 8  
(D) None of the above

The input also contains a stray extra choice: `(4) none`.

**Answer: (B) 4**

**Solution:**
1. The two subqueries share only the `Department` column, so the natural join matches rows on department.
2. The source data has four departments, each occurring once on both sides (Mechanical, Electrical, Computer, Civil). The join has four rows, and `COUNT(*)` returns 4.
