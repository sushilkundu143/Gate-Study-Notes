# PYQs — Transactions & Concurrency Control

[← All PYQ topics](./README.md) · [DBMS notes](../README.md)

**48 questions** (24 from GATE papers). Try each question before opening its solution.

## Quick Answer Key

| Q | Source | Answer |
| --- | --- | --- |
| [Q1](#q1) | GATE CS 2012 | (B) A schedule that is not conflict serializable |
| [Q2](#q2) | GATE CS 2010 | (A) T1 → T3 → T2 |
| [Q3](#q3) | GFG practice | (B) It is not allowed because T1 is rolled back |
| [Q4](#q4) | GFG practice | (A) Timestamp ordering |
| [Q5](#q5) | GFG practice | (D) Distributed parity |
| [Q6](#q6) | GFG practice | (C) S1 is not conflict-serializable and S2 is conflict-serializable |
| [Q7](#q7) | GFG practice | (D) All employees who earn more than the average salary of employee… |
| [Q8](#q8) | GFG practice | (B) Undo record 6, then redo records 2 and 3 |
| [Q9](#q9) | GFG practice | (C) Both I and II |
| [Q10](#q10) | GFG practice | (C) TO guarantees conflict serializability, but schedules may suffe… |
| [Q11](#q11) | GFG practice | (A) Transaction log |
| [Q12](#q12) | GFG practice | (D) A transaction reads a data item after it is written by an uncom… |
| [Q13](#q13) | GFG practice | No listed option is correct |
| [Q14](#q14) | GFG practice | (B) II and IV |
| [Q15](#q15) | GFG practice | (B) Atomicity, consistency, isolation, durability |
| [Q16](#q16) | GFG practice | (D) S1 is not conflict-serializable and S2 is conflict-serializable |
| [Q17](#q17) | GATE CS 2021 | (A) D1 is lossless, but D2 is lossy |
| [Q18](#q18) | GATE CS 2021 | (B) P is true and Q is false |
| [Q19](#q19) | GATE CS 2010 | (B) II only |
| [Q20](#q20) | GFG practice | No listed option is correct; the receive-side clock is estimated to… |
| [Q21](#q21) | GATE CS 2021 | (A) The same undo and redo list will be used in the next recovery |
| [Q22](#q22) | GFG practice | (B) Checkpointing |
| [Q23](#q23) | GFG practice | (A) RAID 1 |
| [Q24](#q24) | GFG practice | (B) T3 − T1 − T2 |
| [Q25](#q25) | GFG practice | (A) Serializable |
| [Q26](#q26) | GATE IT 2004 | (4) None of these |
| [Q27](#q27) | GATE CS 2014 | (D) `r2(X); w2(X); r3(X); r1(X); w1(X)` |
| [Q28](#q28) | GATE CS 2014 | (C) S is both conflict-serializable and recoverable |
| [Q29](#q29) | GATE CS 2014 | (A) Only S1 is conflict-serializable |
| [Q30](#q30) | GATE CS 2006 | (B) Undo record 6, then redo records 2 and 3 |
| [Q31](#q31) | GATE CS Mock 2018 | (D) It is neither view-serializable nor conflict-serializable |
| [Q32](#q32) | GATE CS 2003 | (D) A transaction reads a data item after it is written by an uncom… |
| [Q33](#q33) | GATE CS 2003 | (D) The schedule is not serializable |
| [Q34](#q34) | GATE CS 2015 | (B) Consistency |
| [Q35](#q35) | GATE CS 2015 | (A) Undo: T3, T1; Redo: T2 |
| [Q36](#q36) | GATE CS 2015 | (B) S is non-recoverable and cannot ensure transaction atomicity |
| [Q37](#q37) | GATE IT 2004 | (C) Row |
| [Q38](#q38) | GFG practice | (A) Topological order |
| [Q39](#q39) | GATE CS 2016 | (D) Deadlock-freedom |
| [Q40](#q40) | GATE CS 2016 | (A) Serializability and deadlock-freedom |
| [Q41](#q41) | GATE CS 2016 | (A) Topological order |
| [Q42](#q42) | GATE CS 2016 | (C) S does not have a cascading abort |
| [Q43](#q43) | GATE IT 2008 | (D) S1 is conflict-equivalent to S2, but not S3 |
| [Q44](#q44) | GATE Mock 2017 | (B) Only 2 |
| [Q45](#q45) | GATE CS 1999 | (D) Not serializable and cannot occur under 2PL |
| [Q46](#q46) | GATE CS 1997 | (D) Both (2) and (3) |
| [Q47](#q47) | GATE CS Mock 2018 | (B) Ti dies; Ti waits; Ti waits; Tj aborts |
| [Q48](#q48) | GFG practice | (D) S4 |

---

## Questions and Solutions

<a id="q1"></a>

### Q1. [GATE CS 2012] Conflict serializability of interleavings
Consider two transactions, with data items `P` and `Q` initially zero:

```text
T1: read(P); read(Q); if P = 0 then Q := Q + 1; write(Q)
T2: read(Q); read(P); if Q = 0 then P := P + 1; write(P)
```

Any non-serial interleaving of T1 and T2 for concurrent execution leads to which result?

(A) A serializable schedule  
(B) A schedule that is not conflict serializable  
(C) A conflict serializable schedule  
(D) A schedule for which a precedence graph cannot be drawn

**Answer: (B) A schedule that is not conflict serializable**

**Solution:** In a genuinely interleaved schedule, `r1(P)` is before `w2(P)`, giving edge T1→T2. Likewise, `r2(Q)` is before `w1(Q)`, giving T2→T1. The precedence graph has a cycle, so the schedule is not conflict-serializable. A precedence graph can always be drawn.

<a id="q2"></a>

### Q2. [GATE CS 2010] Find the serial order of a schedule
The schedule has three transactions. Read/write operations occur in this order (the original figure is transcribed top-to-bottom):

```text
r1(X); r2(Y); r3(Y); w2(Y); w1(X); w3(X); r2(X); w2(X)
```

Which is its correct serialization?

(A) T1 → T3 → T2  
(B) T2 → T1 → T3  
(C) T2 → T3 → T1  
(D) T3 → T1 → T2

**Answer: (A) T1 → T3 → T2**

**Solution:** On X, `w1(X)` precedes `w3(X)` and the later operations of T2, giving T1→T3 and T1→T2. Also `w3(X)` precedes T2's later `r2(X)`/`w2(X)`, giving T3→T2. The acyclic graph forces T1→T3→T2.

<a id="q3"></a>

### Q3. [GFG practice] Basic timestamp-ordering protocol
T1 arrives before T2. Consider the schedule:

```text
S = r1(A); r2(B); w2(A); w1(B)
```

Which statement is true?

(A) The schedule is allowed under basic timestamp ordering.  
(B) It is not allowed because T1 is rolled back.  
(C) It is not allowed because T2 is rolled back.  
(D) None of these.

**Answer: (B) It is not allowed because T1 is rolled back**

**Solution:** Let TS(T1) < TS(T2), and initially the read/write timestamps of each item are 0. Both reads are allowed. `w2(A)` is allowed and makes `WTS(A)=TS(T2)`. But `r2(B)` has already set `RTS(B)=TS(T2)`, so `w1(B)` fails because TS(T1) < RTS(B). The protocol aborts T1.

<a id="q4"></a>

### Q4. [GFG practice] Conflict serializability without deadlock
Which concurrency-control protocol ensures conflict serializability and is free from deadlock?

(A) Timestamp ordering  
(B) Two-phase locking  
(C) Both (A) and (B)  
(D) Neither

**Answer: (A) Timestamp ordering**

**Solution:** Timestamp ordering enforces a serial order and aborts transactions rather than making them wait, so it cannot deadlock. Two-phase locking also ensures conflict serializability, but lock waits can form a deadlock.

<a id="q5"></a>

### Q5. [GFG practice] RAID 5 parity
Which is characteristic of RAID 5?

(A) Dedicated parity  
(B) Double parity  
(C) Hamming-code parity  
(D) Distributed parity

**Answer: (D) Distributed parity**

**Solution:** RAID 5 distributes parity blocks across the member disks. Dedicated parity is characteristic of RAID 4; RAID 6 uses dual distributed parity. Hamming-code parity is associated with RAID 2.

<a id="q6"></a>

### Q6. [GFG practice] Compare two conflict-serializability schedules
For transactions T1 and T2, consider:

```text
S1: r1(X); r1(Y); r2(X); r2(Y); w2(Y); w1(X)
S2: r1(X); r2(X); r2(Y); w2(Y); r1(Y); w1(X)
```

Which statement is true?

(A) Both S1 and S2 are conflict-serializable.  
(B) S1 is conflict-serializable and S2 is not.  
(C) S1 is not conflict-serializable and S2 is conflict-serializable.  
(D) Neither is conflict-serializable.

**Answer: (C) S1 is not conflict-serializable and S2 is conflict-serializable**

**Solution:** In S1, `r1(X)` before `w1(X)` is not cross-transaction; the cross conflicts give T2→T1 from `r2(X)` before `w1(X)`, and T1→T2 from `r1(Y)` before `w2(Y)`. This cycle makes S1 non-serializable. In S2 the cross-conflicts point only T2→T1 (`r2(X)` before `w1(X)` and `w2(Y)` before `r1(Y)`), so its graph is acyclic.

<a id="q7"></a>

### Q7. [GFG practice] Correlated average-salary query
Relation:

```text
Works(emp_name, company_name, salary)
```

`emp_name` is the primary key. What does this query return?

```sql
SELECT emp_name
FROM Works T
WHERE salary > (
  SELECT AVG(salary)
  FROM Works S
  WHERE T.company_name = S.company_name
);
```

(A) The highest-paid employee who earns more than the average salary of all employees of their company.  
(B) The highest-paid employee who earns more than the average salary of all employees of all companies.  
(C) All employees who earn more than the average salary of all employees of all companies.  
(D) All employees who earn more than the average salary of employees of their company.

**Answer: (D) All employees who earn more than the average salary of employees of their company**

**Solution:** For each outer row T, the subquery averages salaries only for rows with the same company name. The predicate tests that employee against that company's average. There is no `MAX` operation, so the query does not find only the highest-paid employee.

<a id="q8"></a>

### Q8. [GFG practice] Log recovery after an uncommitted update
A bank account has an initial balance of 12000. T1 transfers 2000 to a mortgage payment, then T2 applies 5% interest. The log is:

```text
1. T1 start
2. T1 B old=1200 new=10000
3. T1 M old=0 new=2000
4. T1 commit
5. T2 start
6. T2 B old=10000 new=10500
7. T2 commit
```

The system crashes just before record 7 is written. What is true during recovery?

(A) Redo record 6 to set B to 10500.  
(B) Undo record 6 to set B to 10000, then redo records 2 and 3.  
(C) Do not redo records 2 and 3 because T1 committed.  
(D) Redo and undo may be applied in any order because they are idempotent.

**Answer: (B) Undo record 6, then redo records 2 and 3**

**Solution:** T2 has no commit record, so it is a loser transaction and its change to B must be undone. T1 committed, so its changes must be redone to guarantee durability. Applying the loser undo and winner redo restores the committed state. (The input's record 2 says old=1200, despite the stated initial 12000; the recovery decision is unaffected.)

<a id="q9"></a>

### Q9. [GFG practice] Lossless and lossy decompositions
For relation R(A,B,C), the functional dependencies are `A → B` and `C → AB`. Are these statements true?

I. Decomposing R into R1(C,A) and R2(A,B) is lossless.  
II. Decomposing R into R1(A,B) and R2(B,C) is lossy.

(A) Only I  
(B) Only II  
(C) Both I and II  
(D) Neither I nor II

**Answer: (C) Both I and II**

**Solution:** For I, the intersection is A, and A→AB, so the intersection determines all of R2; the binary join is lossless. For II, the intersection is B, but B determines neither AB nor BC under the given dependencies; the join can create spurious tuples, so the decomposition is lossy.

<a id="q10"></a>

### Q10. [GFG practice] Timestamp ordering and cascading rollback
A schedule S is generated by basic timestamp ordering (TO). Which statement about recoverability and cascading rollback is correct?

(A) All schedules generated are strictly recoverable.  
(B) TO guarantees conflict serializability and freedom from cascading rollbacks.  
(C) TO guarantees conflict serializability, but schedules may suffer cascading rollbacks.  
(D) TO does not guarantee conflict serializability but ensures clean recoverability.

**Answer: (C) TO guarantees conflict serializability, but schedules may suffer cascading rollbacks**

**Solution:** TO enforces timestamp order for conflicting operations, hence conflict serializability. Basic TO can nevertheless let a transaction read a value written by an uncommitted transaction. If the writer aborts, the reader may also need to abort. Thus strictness and freedom from cascading rollback are not guaranteed.

<a id="q11"></a>

### Q11. [GFG practice] Record of database activity
Which contains a complete record of all activity that affected database contents during a period?

(A) Transaction log  
(B) Query language  
(C) Report writer  
(D) Data manipulation language

**Answer: (A) Transaction log**

**Solution:** The transaction log records database updates and transaction events for recovery and auditing. A query language and a report writer are interfaces/tools, while DML is a class of commands, not the activity record.

<a id="q12"></a>

### Q12. [GFG practice] Dirty reads and irrecoverable schedules
Which scenario may lead to an irrecoverable error in a database system?

(A) A transaction writes a data item after it is read by an uncommitted transaction.  
(B) A transaction reads a data item after it is read by an uncommitted transaction.  
(C) A transaction reads a data item after it is written by a committed transaction.  
(D) A transaction reads a data item after it is written by an uncommitted transaction.

**Answer: (D) A transaction reads a data item after it is written by an uncommitted transaction**

**Solution:** This is a dirty read. If the writer aborts after the reader commits, the reader has committed based on a value that must be undone, making the schedule irrecoverable. Reading a committed value is safe; read-read conflicts do not cause this problem.

<a id="q13"></a>

### Q13. [GFG practice] Purpose of two-phase commit
Which statement about the two-phase commit protocol is correct?

(A) It ensures serializability.  
(B) It prevents deadlock.  
(C) It detects deadlock.  
(D) It recovers from deadlock.

**Answer: No listed option is correct**

**Solution:** Two-phase commit is a distributed atomic-commit protocol: participants agree to commit or abort together. It does not itself enforce transaction serializability or prevent, detect, or recover from database deadlocks.

> Note: GFG marks (A). The question most likely means two-phase **locking** (2PL), which does ensure serializability — so pick (A). Two-phase **commit** itself only guarantees atomic commit across sites.

<a id="q14"></a>

### Q14. [GFG practice] Classify 2PL and timestamping
Which statements are correct?

I. Two-phase locking is an optimistic protocol.  
II. Two-phase locking is a pessimistic protocol.  
III. Timestamping is an optimistic protocol.  
IV. Timestamping is a pessimistic protocol.

(A) I and III  
(B) II and IV  
(C) I and IV  
(D) II and III

**Answer: (B) II and IV**

**Solution:** 2PL acquires locks to control conflicts as they arise, so it is pessimistic. In the classification used by this question, timestamp ordering checks each operation against timestamp constraints and aborts violations immediately, so it is also treated as pessimistic. Optimistic concurrency control instead delays conflict checking until validation.

<a id="q15"></a>

### Q15. [GFG practice] ACID properties
What are the ACID properties of a transaction?

(A) Atomicity, consistency, isolation, database  
(B) Atomicity, consistency, isolation, durability  
(C) Atomicity, consistency, integrity, durability  
(D) Atomicity, consistency, integrity, database

**Answer: (B) Atomicity, consistency, isolation, durability**

**Solution:** ACID expands to Atomicity, Consistency, Isolation, and Durability. “Database” and “integrity” are not the I or D terms in the acronym.

<a id="q16"></a>

### Q16. [GFG practice] Conflict serializability of two schedules
Consider:

```text
S1: r1(X); r1(Y); r2(X); r2(Y); w2(Y); w1(X)
S2: r1(X); r2(X); r2(Y); w2(Y); r1(Y); w1(X)
```

Which statement is correct?

(A) Both S1 and S2 are conflict-serializable.  
(B) Neither S1 nor S2 is conflict-serializable.  
(C) S1 is conflict-serializable and S2 is not.  
(D) S1 is not conflict-serializable and S2 is conflict-serializable.

**Answer: (D) S1 is not conflict-serializable and S2 is conflict-serializable**

**Solution:** In S1, `r1(Y)` before `w2(Y)` gives T1→T2, while `r2(X)` before `w1(X)` gives T2→T1: a cycle. In S2, the conflicts give only T2→T1, so its graph is acyclic.

<a id="q17"></a>

### Q17. [GATE CS 2021] Test two decompositions for losslessness
Let R(P,Q,S,T,X,Y,Z,W) have these functional dependencies:

```text
PQ → X;  P → YX;  Q → Y;  Y → ZW
```

The decompositions are:

```text
D1: (P,Q,S,T), (P,T,X), (Q,Y), (Y,Z,W)
D2: (P,Q,S),   (T,X),   (Q,Y), (Y,Z,W)
```

Which is correct?

(A) D1 is lossless, but D2 is lossy.  
(B) D1 is lossy, but D2 is lossless.  
(C) Both are lossless.  
(D) Both are lossy.

**Answer: (A) D1 is lossless, but D2 is lossy**

**Solution:** In D1, join the first two pieces on PT: `PT→X`, so PT determines the second piece. The resulting relation contains Q, and `Q→Y` makes the join with (Q,Y) lossless; `Y→ZW` then makes the final join lossless. In D2, (T,X) shares no attribute with any other component, so its join is a Cartesian product with the rest and can introduce spurious tuples.

<a id="q18"></a>

### Q18. [GATE CS 2021] Conflict serializability versus recoverability
The schedule is:

```text
R2(Y); R1(X); R3(Z); R1(Y); W1(X); R2(Z); W2(Y); R3(X); W3(Z)
```

P: S is conflict-serializable.  
Q: If T3 commits before T1 finishes, then S is recoverable.

Which choice is correct?

(A) Both P and Q are true.  
(B) P is true and Q is false.  
(C) P is false and Q is true.  
(D) Both P and Q are false.

**Answer: (B) P is true and Q is false**

**Solution:** The conflicts give T1→T2 (`R1(Y)` before `W2(Y)`), T1→T3 (`W1(X)` before `R3(X)`), and T2→T3 (`R2(Z)` before `W3(Z)`). This graph is acyclic, so P is true. T3 reads X written by T1. If T3 commits before T1, it commits after a dirty read but before its writer commits, violating recoverability; Q is false.

<a id="q19"></a>

### Q19. [GATE CS 2010] Deadlock freedom and serializability
Which protocols ensure both conflict serializability and freedom from deadlock?

I. Two-phase locking  
II. Timestamp ordering

(A) I only  
(B) II only  
(C) Both I and II  
(D) Neither I nor II

**Answer: (B) II only**

**Solution:** 2PL is conflict-serializable but transactions may wait on locks and deadlock. Timestamp ordering enforces a serial order without waiting, so it is deadlock-free.

<a id="q20"></a>

### Q20. [GFG practice] Clock synchronization from four timestamps
Given:

```text
Original timestamp = 46
Receive timestamp = 59
Transmit timestamp = 60
Timestamp at arrival of packet = 69
```

Which statement is correct?

(A) The receive clock should go back by 3 ms.  
(B) Transmit and receive clocks are synchronized.  
(C) The transmit clock should go back by 3 ms.  
(D) The receive clock should go ahead by 1 ms.

**Answer: No listed option is correct; the receive-side clock is estimated to be 2 ms ahead**

**Solution:** Using the four-timestamp offset estimate, `θ = ((59−46) + (60−69))/2 = (13−9)/2 = 2 ms`. The receive/transmit clock is ahead by about 2 ms relative to the originating clock, so it should be adjusted back by 2 ms. None of the choices gives that amount.

> Note: GFG marks (A); the standard four-timestamp calculation gives a 2 ms correction, not 3 ms.

<a id="q21"></a>

### Q21. [GATE CS 2021] Crash during recovery
A database crashes again while recovering from an earlier crash. Assume no checkpoint is made either during transactions or during recovery. Which statement is correct?

(A) The same undo and redo list will be used in the next recovery.  
(B) The system cannot recover any further.  
(C) Transactions already undone and redone will not be recovered again.  
(D) The database will become inconsistent.

**Answer: (A) The same undo and redo list will be used in the next recovery**

**Solution:** With no checkpoint, recovery must again inspect the persistent log from the beginning. Undo/redo work is designed to be repeatable (and logged), so another crash does not prevent recovery. The relevant transaction statuses—and thus the undo/redo classification—are reconstructed from the log rather than assumed lost.

<a id="q22"></a>

### Q22. [GFG practice] Checkpointing and recovery work
__________ rules limit the volume of log information that must be handled after a failure involving loss of volatile information.

(A) Write-ahead log  
(B) Checkpointing  
(C) Log buffer  
(D) Thomas write rule

**Answer: (B) Checkpointing**

**Solution:** A checkpoint records a recovery boundary and limits how far back the system must scan the log. Write-ahead logging governs log-before-data ordering; a log buffer stores log records temporarily; Thomas write rule is a timestamp protocol.

<a id="q23"></a>

### Q23. [GFG practice] RAID transfer rate
Which RAID level provides the highest data-transfer rate (read/write) among these choices?

(A) RAID 1  
(B) RAID 3  
(C) RAID 4  
(D) RAID 5

**Answer: (A) RAID 1**

**Solution:** In the comparison intended here, RAID 1 mirroring allows reads to be served in parallel, while parity updates in RAID 3/4/5 add write overhead. (RAID 0 is not among the listed choices.)

<a id="q24"></a>

### Q24. [GFG practice] Equivalent serial schedule
The operations, read top-to-bottom from the given three-transaction schedule, are:

```text
T3: R(Y); R(Z)
T1: R(X); W(X)
T3: W(Y); W(Z)
T2: W(Z)
T1: R(Y); W(Y)
T2: R(Y); W(Y); R(X); W(X)
```

What is the equivalent serial schedule?

(A) T1 − T2 − T3  
(B) T3 − T1 − T2  
(C) T2 − T1 − T3  
(D) T1 − T3 − T2

**Answer: (B) T3 − T1 − T2**

**Solution:** T3's writes on Y and Z precede conflicting operations of T1/T2, giving T3→T1 and T3→T2. T1's writes on X/Y precede T2's reads/writes, giving T1→T2. The graph is acyclic and forces T3→T1→T2.

<a id="q25"></a>

### Q25. [GFG practice] Highest isolation level
Which is the highest isolation level in transaction management?

(A) Serializable  
(B) Repeated Read  
(C) Committed Read  
(D) Uncommitted Read

**Answer: (A) Serializable**

**Solution:** Serializable gives the strongest isolation here by requiring concurrent transactions to have an effect equivalent to some serial order. Repeatable read, read committed, and read uncommitted provide progressively weaker guarantees.

<a id="q26"></a>

### Q26. [GATE IT 2004] Is the interleaved bank schedule serializable?
T1 transfers 10 from A to B; T2 computes 20% of A and adds it to B. The schedule shown by the two columns is:

```text
T1: Read(A); A := A − 10
T2: Read(A); Temp := 0.2*A; Write(A); Read(B)
T1: Write(A); Read(B); B := B + 10; Write(B)
T2: B := B + Temp; Write(B)
```

(A) S is serializable only as T1, T2.  
(B) S is serializable only as T2, T1.  
(C) S is serializable as both T1,T2 and T2,T1.  
(D) S is serializable either as T1 or as T2.  
(4) None of these.

**Answer: (4) None of these**

**Solution:** `r1(A)` precedes `w2(A)`, giving T1→T2, while `w2(A)` precedes `w1(A)`, giving T2→T1. The cycle means S is not conflict-serializable in either serial order; none of the proposed serial schedules matches it.

<a id="q27"></a>

### Q27. [GATE CS 2014] Identify the conflict-serializable schedule
For three transactions operating on X, which schedule is conflict-serializable?

(A) `r1(X); r2(X); w1(X); r3(X); w2(X)`  
(B) `r2(X); r1(X); w2(X); r3(X); w1(X)`  
(C) `r3(X); r2(X); r1(X); w2(X); w1(X)`  
(D) `r2(X); w2(X); r3(X); r1(X); w1(X)`

**Answer: (D) `r2(X); w2(X); r3(X); r1(X); w1(X)`**

**Solution:** D is a serial schedule: all T2 operations occur before T3, then T1, so its precedence graph is acyclic (T2→T3→T1). For A, B, and C, the ordering of conflicting reads/writes gives a cycle; for example A has T2→T1, T1→T3, and T3→T2.

<a id="q28"></a>

### Q28. [GATE CS 2014] Serializability and recoverability
The schedule below is read top-to-bottom. Each transaction ends at its displayed commit:

```text
T2: R(X)
T3: W(X); Commit
T1: W(X); Commit
T2: W(Y); R(Z); Commit
T4: R(X); R(Y); Commit
```

Which statement is correct?

(A) S is conflict-serializable but not recoverable.  
(B) S is not conflict-serializable but is recoverable.  
(C) S is both conflict-serializable and recoverable.  
(D) S is neither conflict-serializable nor recoverable.

**Answer: (C) S is both conflict-serializable and recoverable**

**Solution:** Conflicts on X give T2→T3→T1→T4, and the Y conflict gives T2→T4; the graph is acyclic. T4 reads X and Y only after the writers T1 and T2 have committed, so no transaction commits after reading another transaction's uncommitted value. Both properties hold.

<a id="q29"></a>

### Q29. [GATE CS 2014] Compare conflict serializability of S1 and S2
Transactions:

```text
T1: r1(X); r1(Z); w1(X); w1(Z)
T2: r2(Y); r2(Z); w2(Z)
T3: r3(Y); r3(X); w3(Y)
```

Schedules:

```text
S1: r1(X); r3(Y); r3(X); r2(Y); r2(Z);
    w3(Y); w2(Z); r1(Z); w1(X); w1(Z)
S2: r1(X); r3(Y); r2(Y); r3(X); r1(Z);
    r2(Z); w3(Y); w1(X); w2(Z); w1(Z)
```

Which statement is true?

(A) Only S1 is conflict-serializable.  
(B) Only S2 is conflict-serializable.  
(C) Both S1 and S2 are conflict-serializable.  
(D) Neither S1 nor S2 is conflict-serializable.

**Answer: (A) Only S1 is conflict-serializable**

**Solution:** S1 has edges T2→T3 (read Y before `w3(Y)`), T3→T1 (read X before `w1(X)`), and T2→T1 (Z conflicts); these are acyclic. S2 has those first two edges and also T1→T2 (`r1(Z)` before `w2(Z)`), creating T2→T3→T1→T2.

<a id="q30"></a>

### Q30. [GATE CS 2006] Recovery from a crash before commit
A bank account has initial balance 12000. T1 transfers 2000 to mortgage payment M, then T2 applies 5% interest. Log:

```text
1. T1 start
2. T1 B old=12000 new=10000
3. T1 M old=0 new=2000
4. T1 commit
5. T2 start
6. T2 B old=10000 new=10500
7. T2 commit
```

The system crashes just before record 7 is written. Which is true?

(A) Redo record 6 to set B to 10500.  
(B) Undo record 6 to set B to 10000 and then redo records 2 and 3.  
(C) Do not redo records 2 and 3 because T1 committed.  
(D) Redo and undo may be applied in any order because they are idempotent.

**Answer: (B) Undo record 6, then redo records 2 and 3**

**Solution:** T2 has not committed, so undo its update. T1 did commit, so redo its account and mortgage updates if needed. Idempotence does not make the order arbitrary when undoing one transaction and redoing another.

<a id="q31"></a>

### Q31. [GATE CS Mock 2018] View versus conflict serializability
Consider:

```text
S = T1:R(X), T1:R(Y), T1:W(X), T2:R(Y), T3:W(Y),
    T1:W(X), T2:R(Y)
```

(A) The schedule is view-serializable.  
(B) It is conflict-serializable but not view-serializable.  
(C) It is view-serializable but not conflict-serializable.  
(D) It is neither view-serializable nor conflict-serializable.

**Answer: (D) It is neither view-serializable nor conflict-serializable**

**Solution:** Conflict edges include T2→T3 (`r2(Y)` before `w3(Y)`) and T3→T2 (`w3(Y)` before the later `r2(Y)`), so there is a cycle. It is also not view-serializable: T2's first read of Y gets the initial value, while its second read gets T3's write. No serial ordering can place all of T2 before T3 and also place T3 before T2.

> Note: GFG marks (C); the two reads by T2 force contradictory serial-order requirements, so C is not view-equivalent to any serial schedule.

<a id="q32"></a>

### Q32. [GATE CS 2003] Irrecoverable error
Which scenario may lead to an irrecoverable error in a database system?

(A) A transaction writes a data item after it is read by an uncommitted transaction.  
(B) A transaction reads a data item after it is read by an uncommitted transaction.  
(C) A transaction reads a data item after it is written by a committed transaction.  
(D) A transaction reads a data item after it is written by an uncommitted transaction.

**Answer: (D) A transaction reads a data item after it is written by an uncommitted transaction**

**Solution:** A read of an uncommitted write is dirty. If the reader commits before the writer later aborts, recovery cannot preserve the reader's committed result while undoing the dirty value. Read-read does not create this dependency, and reading a committed value is safe.

<a id="q33"></a>

### Q33. [GATE CS 2003] Detect a cycle in the precedence graph
The operations in the schedule, read top-to-bottom, are:

```text
r2(D3); r2(D2); w2(D2); r3(D2); r3(D3);
r1(D1); w1(D1); w3(D2); w3(D3); r2(D1);
r1(D2); w1(D2); w2(D1)
```

Here R(D) and W(D) are reads and writes of data item D. Which statement is correct?

(A) The schedule is serializable as T2; T3; T1.  
(B) The schedule is serializable as T2; T1; T3.  
(C) The schedule is serializable as T3; T2; T1.  
(D) The schedule is not serializable.

**Answer: (D) The schedule is not serializable**

**Solution:** On D2, `r2(D2)` precedes `w1(D2)`, giving T2→T1. On D1, `r1(D1)` precedes `w2(D1)`, giving T1→T2. The cycle rules out every serial order.

<a id="q34"></a>

### Q34. [GATE CS 2015] ACID property preserving an account invariant
A transaction transfers 50 from account x to account y:

```text
read(x); x := x − 50; write(x);
read(y); y := y + 50; write(y)
```

The requirement that the sum of x and y remain constant is an example of:

(A) Atomicity  
(B) Consistency  
(C) Isolation  
(D) Durability

**Answer: (B) Consistency**

**Solution:** The transaction must preserve the database invariant `x+y = constant`, moving the database from one valid state to another. Atomicity concerns all-or-nothing execution; isolation concerns concurrency; durability concerns committed results surviving failure.

<a id="q35"></a>

### Q35. [GATE CS 2015] Undo and redo lists after checkpoint
A simple checkpointing protocol has this log:

```text
(start,T4); (write,T4,y,2,3); (start,T1); (commit,T4);
(write,T1,z,5,7); (checkpoint);
(start,T2); (write,T2,x,1,9); (commit,T2);
(start,T3); (write,T3,z,7,2)
```

A crash occurs now. With undo and redo recovery, what are the lists?

(A) Undo: T3, T1; Redo: T2  
(B) Undo: T3, T1; Redo: T2, T4  
(C) Undo: none; Redo: T2, T4, T3, T1  
(D) Undo: T3, T1, T4; Redo: T2

**Answer: (A) Undo: T3, T1; Redo: T2**

**Solution:** T1 was still active at the checkpoint and T3 is active at the crash, so undo both. T2 committed after the checkpoint, so redo it. T4 committed before the checkpoint and does not need to be redone under the simple checkpoint protocol.

<a id="q36"></a>

### Q36. [GATE CS 2015] Recoverability after a transaction failure
The schedule is:

| Time | T1 | T2 |
|---:|---|---|
| 1 | `read(A)` | |
| 2 | `write(A)` | |
| 3 | | `read(C)` |
| 4 | | `write(C)` |
| 5 | | `read(B)` |
| 6 | | `write(B)` |
| 7 | | `read(A)` |
| 8 | | `commit` |
| 9 | `read(B)` | |

Suppose T1 fails immediately after time 9. Which statement is correct?

(A) T2 must be aborted and then both T1 and T2 restarted to ensure atomicity.  
(B) S is non-recoverable and cannot ensure transaction atomicity.  
(C) Only T2 must be aborted and restarted to ensure transaction atomicity.  
(D) S is recoverable and can ensure atomicity; nothing else needs to be done.

**Answer: (B) S is non-recoverable and cannot ensure transaction atomicity**

**Solution:** T2 reads A after T1 writes A but before T1 commits. T2 then commits at time 8, before T1 fails. Thus T2 committed using T1's uncommitted value. This violates recoverability; aborting T1 cannot undo T2's already committed result.

<a id="q37"></a>

### Q37. [GATE IT 2004] Lock granularity and concurrency
Which locking level gives the highest concurrency in a relational database?

(A) Page  
(B) Table  
(C) Row  
(D) Page, table, and row locking allow the same concurrency

**Answer: (C) Row**

**Solution:** Row locks restrict access to individual tuples, allowing unrelated rows to be used concurrently. Page locks block multiple rows at once, and a table lock is coarser still.

<a id="q38"></a>

### Q38. [GFG practice] Serial order from a precedence graph
A schedule involves T1,…,Tn. Its precedence graph has transactions as vertices and conflict edges. If the schedule is serializable, which vertex ordering is guaranteed to yield a serial schedule?

(A) Topological order  
(B) Depth-first order  
(C) Breadth-first order  
(D) Ascending order of transaction indices

**Answer: (A) Topological order**

**Solution:** A conflict-serializable schedule has an acyclic precedence graph. A topological order of that graph respects every conflict edge and is its equivalent serial order. DFS/BFS traversal order and numeric transaction IDs need not respect all edges.

<a id="q39"></a>

### Q39. [GATE CS 2016] Identify the non-ACID property
Which is NOT part of ACID?

(A) Atomicity  
(B) Consistency  
(C) Isolation  
(D) Deadlock-freedom

**Answer: (D) Deadlock-freedom**

**Solution:** ACID stands for Atomicity, Consistency, Isolation, and Durability. Deadlock-freedom is a desirable concurrency-control property, not one of the four ACID properties.

<a id="q40"></a>

### Q40. [GATE CS 2016] Ordered exclusive locks
Consider this locking protocol for a transaction T that accesses objects `{O1,…,Ok}`:

1. T acquires exclusive locks on O1,…,Ok in increasing address order.
2. T performs its required operations.
3. T releases all locks.

What does the protocol guarantee?

(A) Serializability and deadlock-freedom.  
(B) Neither serializability nor deadlock-freedom.  
(C) Serializability but not deadlock-freedom.  
(D) Deadlock-freedom but not serializability.

**Answer: (A) Serializability and deadlock-freedom**

**Solution:** Holding exclusive locks through the transaction's operations gives 2PL and therefore conflict serializability. Acquiring all required locks in a consistent increasing order avoids circular wait; if a lock is unavailable the transaction waits before proceeding, so deadlock is prevented.

<a id="q41"></a>

### Q41. [GATE CS 2016] Topologically order a serializable schedule
A schedule has a precedence graph whose vertices are transactions and edges are conflicts. If it is serializable, which ordering of the vertices is guaranteed to yield a serial schedule?

(A) Topological order  
(B) Depth-first order  
(C) Breadth-first order  
(D) Ascending order of transaction indices

**Answer: (A) Topological order**

**Solution:** Acyclicity is the condition for conflict serializability, and topological sorting of an acyclic graph respects all precedence constraints. DFS/BFS can traverse cyclic graphs too, and transaction numbering has no required relationship to edges.

<a id="q42"></a>

### Q42. [GATE CS 2016] Cascading abort in an aborted schedule
For schedule

```text
S = r2(X); r1(X); r2(Y); w1(X); r1(Y); w2(X); a1; a2
```

`ri(Z)` and `wi(Z)` mean read and write of Z by Ti; `ai` means Ti aborts. Which statement is true?

(A) S is non-recoverable.  
(B) S is recoverable, but has a cascading abort.  
(C) S does not have a cascading abort.  
(D) S is strict.

**Answer: (C) S does not have a cascading abort**

**Solution:** T2 never reads a value written by T1; it only overwrites X after T1's write. Thus T1's abort does not force T2 to abort as a consequence of a dirty read, and there is no cascading abort. The schedule is not strict because T2 writes X while T1's write is still uncommitted. Both transactions abort, so it is not the non-recoverable dirty-read/commit case either.

<a id="q43"></a>

### Q43. [GATE IT 2008] Conflict equivalence of three schedules
Notation `NR O` denotes action R or W by transaction N on object O. Consider:

```text
S1: 2RA, 2WA, 3RC, 2WB, 3WA, 3WC, 1RA, 1RB, 1WA, 1WB
S2: 3RC, 2RA, 2WA, 2WB, 3WA, 1RA, 1RB, 1WA, 1WB, 3WC
S3: 2RA, 3RC, 3WA, 2WA, 2WB, 3WC, 1RA, 1RB, 1WA, 1WB
```

Which statement is true?

(A) S1, S2, and S3 are all conflict-equivalent.  
(B) No two are conflict-equivalent.  
(C) S2 is conflict-equivalent to S3, but not S1.  
(D) S1 is conflict-equivalent to S2, but not S3.

**Answer: (D) S1 is conflict-equivalent to S2, but not S3**

**Solution:** S1 and S2 preserve the relative order of every conflicting pair: on A, B, and C, same-object operations from different transactions occur in the same order. In S3, `3WA` precedes `2WA`, whereas S1/S2 have `2WA` before `3WA`; this reverses a conflicting write-write pair.

<a id="q44"></a>

### Q44. [GATE Mock 2017] Strict 2PL and checkpointing
Which statements are incorrect?

1. A schedule following strict 2PL is conflict-serializable as well as recoverable.  
2. Checkpoints in schedules are inserted to ensure recoverability.

(A) Only 1  
(B) Only 2  
(C) Both 1 and 2  
(D) Neither

**Answer: (B) Only 2**

**Solution:** Strict 2PL guarantees conflict serializability, and holding exclusive locks until commit/abort also prevents dirty reads and gives recoverability, so statement 1 is correct. Checkpoints reduce recovery work by limiting log processing; they do not themselves ensure schedule recoverability, so statement 2 is incorrect.

<a id="q45"></a>

### Q45. [GATE CS 1999] Serializability and two-phase locking
For the schedule below (top-to-bottom), determine which statement is correct:

```text
1  T1: Read(A)
2  T2: Read(B)
3  T1: Write(A)
4  T2: Read(A)
5  T2: Write(A)
6  T2: Write(B)
7  T1: Read(B)
8  T1: Write(B)
```

(A) Serializable and can occur under 2PL.  
(B) Serializable but cannot occur under 2PL.  
(C) Not serializable but can occur under 2PL.  
(D) Not serializable and cannot occur under 2PL.

**Answer: (D) Not serializable and cannot occur under 2PL**

**Solution:** On A, T1's write precedes T2's read/write, giving T1→T2. On B, T2's write precedes T1's read/write, giving T2→T1. The cycle makes the schedule non-serializable. Since 2PL guarantees conflict serializability, it cannot produce this schedule.

<a id="q46"></a>

### Q46. [GATE CS 1997] Foreign-key referential integrity
Let R(a,b,c) and S(d,e,f), where d is a foreign key in S that references the primary key of R. Which operations can violate referential integrity?

1. Insert into R  
2. Insert into S  
3. Delete from R  
4. Delete from S

(A) None of (1), (2), (3), or (4)  
(B) All of (1), (2), (3), and (4)  
(C) Both (1) and (4)  
(D) Both (2) and (3)

**Answer: (D) Both (2) and (3)**

**Solution:** Inserting a child row into S can use a d value absent from R. Deleting a referenced parent row from R can leave an orphan in S. Inserting a parent row and deleting a child row do not by themselves violate this foreign-key constraint.

<a id="q47"></a>

### Q47. [GATE CS Mock 2018] Wait-die and wound-wait actions
If Ti requests a lock held by Tj, the table is:

| Relative age | Wait-die scheme | Wound-wait scheme |
|---|---|---|
| Ti is younger than Tj | W | X |
| Ti is older than Tj | Y | Z |

Fill W, X, Y, Z respectively.

(A) Ti dies; Ti waits; Ti waits; Tj aborts.  
(B) Ti dies; Ti waits; Ti waits; Tj aborts.  
(C) Ti waits; Ti dies; Ti waits; Tj aborts.  
(D) None of these.

**Answer: (B) Ti dies; Ti waits; Ti waits; Tj aborts**

**Solution:** Wait-die is non-preemptive: a younger requester dies, while an older requester may wait. Wound-wait is preemptive: a younger requester waits, while an older requester wounds (aborts) the younger lock holder. Options A and B are identical in the input; both give the correct four actions.

<a id="q48"></a>

### Q48. [GFG practice] Select the conflict-serializable schedule
For three transactions using data item X, which schedule is conflict-serializable?

```text
S1: r1(X); r2(X); w1(X); r3(X); w2(X)
S2: r2(X); r1(X); w2(X); r3(X); w1(X)
S3: r3(X); r2(X); r1(X); w2(X); w1(X)
S4: r2(X); w2(X); r3(X); r1(X); w1(X)
```

(A) S1  
(B) S2  
(C) S3  
(D) S4

**Answer: (D) S4**

**Solution:** In S4, T2's operations precede T3 and T1, and T3's read precedes T1's write, giving the acyclic order T2→T3→T1. S1 has T1→T2, T2→T3, and T3→T2; S2 has T2→T1 and T1→T2; S3 has T3→T2 and T2→T1, but also T1→T2.
