# 1. Entity–Relationship (ER) Model

The ER model is a **design-time** picture of the data: *what things exist* and *how they are related*.
It is converted into tables (relational model) later.

## 1.1 Building Blocks

| Concept | Meaning | Diagram symbol |
| --- | --- | --- |
| Entity | A real-world object, e.g. one student | — |
| Entity set | Collection of similar entities, e.g. `Student` | Rectangle |
| Weak entity set | Cannot be identified by its own attributes alone | Double rectangle |
| Attribute | Property of an entity, e.g. `name` | Ellipse |
| Key attribute | Uniquely identifies an entity | Underlined ellipse |
| Relationship set | Association between entity sets, e.g. `Enrolls` | Diamond |
| Identifying relationship | Connects a weak entity to its owner | Double diamond |

### Attribute types

| Type | Example | Notes |
| --- | --- | --- |
| Simple (atomic) | `age` | Cannot be split |
| Composite | `name = (first, last)` | Stored as separate columns |
| Single-valued | `dob` | One value per entity |
| Multivalued | `phone_numbers` | Double ellipse → becomes a **separate table** |
| Derived | `age` from `dob` | Dashed ellipse → usually not stored |
| Key | `roll_no` | Underlined |

## 1.2 Cardinality (Mapping Constraints)

For a binary relationship R between A and B:

| Cardinality | Meaning |
| --- | --- |
| One-to-one (1:1) | Each A relates to at most one B and vice versa |
| One-to-many (1:N) from A to B | One A relates to many B; each B relates to at most one A |
| Many-to-one (N:1) from A to B | Many A relate to one B; each A relates to at most one B |
| Many-to-many (M:N) | No restriction |

## 1.3 Participation

- **Total participation** (double line): every entity must take part in the relationship.
  Example: every `Loan` must belong to some `Branch`.
- **Partial participation** (single line): some entities may not take part.

> Trap: cardinality says "at most how many"; participation says "at least one or zero".
> "Many-to-one from E1 to E2 with total participation of E1" means **every E1 is related to exactly one E2**.

## 1.4 Weak Entity Sets

- Has no primary key of its own; has a **partial key (discriminator)** (dashed underline).
- Primary key of weak entity = **owner's primary key + discriminator**.
- Always has **total participation** in the identifying relationship.
- Identifying relationship is many-to-one from weak entity to owner.

Example: `Dependent(name, age)` owned by `Employee(emp_id)` → table `Dependent(emp_id, name, age)` with key `(emp_id, name)`.

## 1.5 Extended ER Features

- **Specialization** (top-down): `Employee` → `Engineer`, `Manager`.
- **Generalization** (bottom-up): `Car`, `Truck` → `Vehicle`.
- Constraints: *disjoint* vs *overlapping*; *total* vs *partial* specialization.
- **Aggregation**: treat a relationship set as an entity so it can take part in another relationship.

## 1.6 Converting ER to Tables (Most Asked in GATE)

| ER element | Tables needed |
| --- | --- |
| Strong entity | 1 table with its simple attributes; key = entity key |
| Composite attribute | Store only its component attributes |
| Multivalued attribute | **Separate table** (entity key + value); key = both |
| Weak entity | 1 table with owner key + own attributes; key = owner key + discriminator |
| 1:1 relationship | No new table; put a foreign key on either side (prefer the side with total participation) |
| 1:N / N:1 relationship | No new table; put the FK on the **many side** |
| M:N relationship | **Separate table**: keys of both sides (+ relationship attributes); key = both keys |
| n-ary relationship (n ≥ 3) | Separate table with keys of all participants |
| 1:1 with total participation on both sides | Both entities can be merged into **one** table |

### Minimum number of tables — quick rule

1. One table per strong entity and per weak entity.
2. One table per M:N relationship.
3. One table per multivalued attribute.
4. 1:1 and 1:N relationships need no extra table.
5. If a 1:1 relationship has total participation on both sides, the two entity tables can merge (subtract one).

### Worked example

`Student(sid, name)` —M:N— `Course(cid, title)` via `Enrolls(grade)`; `Student` has multivalued `phone`.

Tables: `Student(sid, name)`, `Course(cid, title)`, `Enrolls(sid, cid, grade)`, `StudentPhone(sid, phone)` → **4 tables**.

## 1.7 Common Traps

1. Relationship attributes on a 1:N relationship go to the **many side** table.
2. A weak entity's table key always includes the owner's key.
3. Self (recursive) relationships use role names, e.g. `Employee manages Employee`; for 1:N add `manager_id` FK in the same table.
4. A many-to-one relationship can be merged into the **many side's** table — not the one side.
