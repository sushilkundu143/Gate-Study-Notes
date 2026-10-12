# 8. Transactions and Concurrency Control

## 8.1 Transaction and ACID

A **transaction** is a unit of work that must happen completely or not at all.

| Property | Meaning | Ensured by |
| --- | --- | --- |
| **A**tomicity | All operations or none | Recovery manager (undo log) |
| **C**onsistency | DB moves from one valid state to another (e.g. total balance unchanged) | Programmer + integrity constraints |
| **I**solation | Concurrent transactions behave as if alone | Concurrency control manager |
| **D**urability | Committed changes survive crashes | Recovery manager (redo log) |

### Transaction states

```text
Active → Partially committed → Committed
   ↓              ↓
 Failed  →  Aborted (rolled back) → restart or kill
```

## 8.2 Schedules

- **Schedule**: ordering of operations of several transactions, preserving each transaction's own order.
- **Serial schedule**: transactions run one after another. `n` transactions → `n!` serial schedules.
- Total schedules (interleavings) for transactions with `n1, n2, …, nk` operations:

```text
(n1 + n2 + … + nk)! / (n1! × n2! × … × nk!)
```

### Anomalies

| Problem | Example |
| --- | --- |
| Lost update (W–W) | T1 and T2 read X, both write; one update lost |
| Dirty read (W–R) | T2 reads X written by uncommitted T1; T1 aborts |
| Unrepeatable read (R–W) | T1 reads X twice and gets different values |
| Phantom | Re-running a range query returns new rows |

## 8.3 Conflict Serializability

Two operations **conflict** if they:

1. belong to **different** transactions,
2. access the **same** data item, and
3. at least one is a **write**.

Conflicting pairs: `R–W`, `W–R`, `W–W`. (`R–R` never conflicts.)

**Precedence graph test**

1. Node per transaction.
2. Edge `Ti → Tj` if an operation of Ti conflicts with a **later** operation of Tj.
3. Schedule is conflict serializable **iff the graph has no cycle**.
4. Equivalent serial orders = topological orders of the graph.

Example: `r2(x) w2(x) r3(x) r1(x) w1(x)` → edges `T2→T3, T2→T1, T3→T1` → acyclic → serial order **T2, T3, T1**.

## 8.4 View Serializability

Two schedules are view equivalent if, for every data item:

1. **Initial read**: the same transaction reads the initial value.
2. **Updated read (reads-from)**: each read reads the value written by the same transaction.
3. **Final write**: the same transaction performs the last write.

- Every conflict serializable schedule is view serializable.
- A view-serializable schedule that is **not** conflict serializable must contain a **blind write** (write without a prior read).
- Testing view serializability is NP-complete in general.

```text
Serial ⊂ Conflict serializable ⊂ View serializable ⊂ All schedules
```

## 8.5 Recoverability

| Class | Condition |
| --- | --- |
| Recoverable | If Tj reads data written by Ti, then **Ti commits before Tj commits** |
| Cascadeless (ACA) | Transactions read only **committed** data |
| Strict | No transaction reads **or writes** an item until the last writer of that item commits/aborts |

```text
Strict ⊂ Cascadeless ⊂ Recoverable ⊂ All schedules
```

- **Irrecoverable**: Tj reads from uncommitted Ti and Tj commits; then Ti aborts.
- **Cascading rollback**: one abort forces others that read its dirty data to abort.
- Serializability and recoverability are **independent** properties.

## 8.6 Lock-Based Protocols

### Lock compatibility

| Held \ Requested | S (shared) | X (exclusive) |
| --- | --- | --- |
| S | ✓ | ✗ |
| X | ✗ | ✗ |

### Two-Phase Locking (2PL) variants

| Protocol | Rule | Conflict serializable | Deadlock-free | Cascadeless / strict |
| --- | --- | --- | --- | --- |
| Basic 2PL | Growing phase then shrinking phase; no lock after the first unlock | Yes | **No** | No |
| Strict 2PL | Basic 2PL + hold **X** locks until commit/abort | Yes | No | Strict (recoverable) |
| Rigorous 2PL | Hold **all** locks until commit/abort | Yes (order = commit order) | No | Strict |
| Conservative (static) 2PL | Acquire all locks before starting | Yes | **Yes** | Not necessarily |

- **Lock point**: moment a transaction acquires its last lock; serial order = order of lock points.
- Locking items in a fixed global order (e.g. increasing address) prevents deadlock.
- 2PL does not produce **all** conflict-serializable schedules.

## 8.7 Deadlock Handling

- **Detection**: wait-for graph; a cycle means deadlock → choose a victim and roll back.
- **Prevention with timestamps** (smaller timestamp = older):

| Scheme | Older Ti requests item held by younger Tj | Younger Ti requests item held by older Tj | Type |
| --- | --- | --- | --- |
| **Wait-Die** | Ti **waits** | Ti **dies** (rolls back) | Non-preemptive |
| **Wound-Wait** | Ti **wounds** Tj (Tj rolls back) | Ti **waits** | Preemptive |

Memory aid: the first word says what the **older** transaction does.
A restarted transaction keeps its original timestamp → no starvation.

- **Timeout**: abort if waiting too long (simple but imprecise).

## 8.8 Timestamp Ordering (TO) Protocol

Each item X keeps `RTS(X)` (largest read timestamp) and `WTS(X)` (largest write timestamp). Transaction T has `TS(T)`.

| T issues | Condition | Action |
| --- | --- | --- |
| `read(X)` | `TS(T) < WTS(X)` | Abort T (would read a value from the future) |
| `read(X)` | otherwise | Read; `RTS(X) = max(RTS(X), TS(T))` |
| `write(X)` | `TS(T) < RTS(X)` | Abort T |
| `write(X)` | `TS(T) < WTS(X)` | Abort T (**Thomas write rule: ignore the write instead**) |
| `write(X)` | otherwise | Write; `WTS(X) = TS(T)` |

Properties:

- Basic TO: conflict serializable (serial order = timestamp order), **deadlock-free** (no waiting), may starve, may produce non-recoverable schedules unless made strict.
- **Thomas write rule** skips obsolete writes → allows some **view-serializable but not conflict-serializable** schedules.

## 8.9 Other Protocols (Awareness Level)

- **Multiversion concurrency control (MVCC)**: keep old versions so readers never wait.
- **Validation (optimistic) protocol**: read → validate → write phases; best when conflicts are rare.
- **Multiple granularity locking**: intention locks `IS`, `IX`, `SIX` on a hierarchy (DB → table → page → row).
- **Isolation levels (SQL)**: Read uncommitted → Read committed → Repeatable read → Serializable.

## 8.10 Recovery Basics

- **Log-based recovery** with **write-ahead logging (WAL)**: log record reaches disk before the data page.
- **Undo** uncommitted transactions; **redo** committed ones after a crash.
- **Checkpoint** limits how far back recovery must scan.
- Deferred update → only redo needed; immediate update → both undo and redo.

## 8.11 Common Traps

1. `R–R` is never a conflict.
2. Draw the edge from the **earlier** conflicting operation's transaction to the later one.
3. Acyclic precedence graph does not guarantee recoverability.
4. Basic 2PL can deadlock and can cascade aborts.
5. Wait-die and wound-wait both abort the **younger** transaction.
6. Thomas write rule ignores a write; it does not abort the transaction.
