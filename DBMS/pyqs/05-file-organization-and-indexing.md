# PYQs — File Organization, Indexing, B & B+ Trees

[← All PYQ topics](./README.md) · [DBMS notes](../README.md)

**36 questions** (12 from GATE papers). Try each question before opening its solution.

## Quick Answer Key

| Q | Source | Answer |
| --- | --- | --- |
| [Q1](#q1) | GATE CS 2010 | (B) 2 |
| [Q2](#q2) | UGC-NET CS 2015 June-II | (D) (i), (ii), (iii) and (iv) |
| [Q3](#q3) | UGC-NET CS 2015 June-III | (B) Linked |
| [Q4](#q4) | UGC-NET CS 2014 December-II | (A) Symbol table |
| [Q5](#q5) | ISRO CS 2018 | (C) Secondary index |
| [Q6](#q6) | UGC-NET CS 2018 July-II | (A) The administrator enjoys more control on the grant option. |
| [Q7](#q7) | GATE CS 2008 | (A) Non-key and ordering |
| [Q8](#q8) | ISRO CS 2007 | (A) Detailed |
| [Q9](#q9) | GATE CS 2021 Set 2 | (A) 698 |
| [Q10](#q10) | UGC-NET CS 2015 June-III | (B) Size of blocks and size of address |
| [Q11](#q11) | ISRO CS 2011 | (C) RAID 6 |
| [Q12](#q12) | ISRO CS 2017 December | (C) Dimension tables are normalized. |
| [Q13](#q13) | GATE CS 2002 | (C) The size of the blocks, the number of blocks used for the index… |
| [Q14](#q14) | GATE CS 2013 | (C) The data records of the file are organized in the same order as… |
| [Q15](#q15) | GFG practice | (C) Dimension tables are normalized. |
| [Q16](#q16) | GATE IT 2005 | (C) 32020 |
| [Q17](#q17) | ISRO CS 2017 December | (D) Bit-mapped hashing |
| [Q18](#q18) | UGC-NET CS 2018 July-II | (B) Root |
| [Q19](#q19) | ISRO CS 2016 | (D) A statement executed automatically by the system as a side effe… |
| [Q20](#q20) | GATE CS 2014 Set 2 | (A) 99.55 to 99.65 |
| [Q21](#q21) | GATE CS Mock 2018 Set 2 | (D) 56 |
| [Q22](#q22) | GATE CS 2015 Set 1 | (C) Clustered |
| [Q23](#q23) | GATE IT 2005 | (B) 30400 |
| [Q24](#q24) | GATE CS 1998 | (C) Occupation |
| [Q25](#q25) | GATE CS 1997 | (B) (a) `L−1`; (b) 13; (c) `2(d+1)^(h−1)` |
| [Q26](#q26) | ISRO CS 2017 December | (C) The index can be hash or B+ tree, and clustered or non-clustered. |
| [Q27](#q27) | ISRO CS 2008 | (D) A and B |
| [Q28](#q28) | ISRO CS 2016 | (A) 63 |
| [Q29](#q29) | ISRO CS 2016 | (A) Non-key and ordering |
| [Q30](#q30) | UGC-NET CS 2017 January-III | (A) Diagram (1) |
| [Q31](#q31) | ISRO CS 2015 | (A) `13n/30` |
| [Q32](#q32) | ISRO CS 2013 | (C) `p_leaf = 46` and `p = 50` |
| [Q33](#q33) | ISRO CS 2013 | (A) Hashed file |
| [Q34](#q34) | ISRO CS 2013 | (A) A secondary access path |
| [Q35](#q35) | ISRO CS 2008 | (A) A secondary access path |
| [Q36](#q36) | GATE CS 1999 | (B) Range queries are faster on B+ trees. |

---

## Questions and Solutions

<a id="q1"></a>

### Q1. [GATE CS 2010] Minimum keys in a non-root B+ tree node
Consider a B+ tree in which the maximum number of keys in a node is 5. What is the minimum number of keys in any non-root node?

- (A) 1
- (B) 2
- (C) 3
- (D) 4

**Answer: (B) 2**

**Solution:** Five keys require at most six child pointers, so the tree has order 6. A non-root internal node must have at least half the maximum child pointers: `ceil(6/2) = 3`. Three pointers require two separator keys. (Leaves have their own occupancy rule, but internal non-root nodes can have two keys, so that is the minimum across non-root nodes.)

<a id="q2"></a>

### Q2. [UGC-NET CS 2015 June-II] Drawbacks of file systems addressed by databases
Database applications were built directly on top of file systems to overcome which drawbacks?

(i) Data redundancy and inconsistency  
(ii) Difficulty in accessing data  
(iii) Data isolation  
(iv) Integrity problems

- (A) (i)
- (B) (i) and (iv)
- (C) (i), (ii) and (iii)
- (D) (i), (ii), (iii) and (iv)

**Answer: (D) (i), (ii), (iii) and (iv)**

**Solution:** Database systems centralize shared data, provide query languages, integrate data from multiple files, and enforce integrity constraints. These address all four listed weaknesses of traditional file-processing systems.

<a id="q3"></a>

### Q3. [UGC-NET CS 2015 June-III] File block allocation method
In which file-system disk-block allocation method is insertion and deletion of blocks in a file easy?

- (A) Index
- (B) Linked
- (C) Contiguous
- (D) Bitmap

**Answer: (B) Linked**

**Solution:** In linked allocation, each file block points to the next block. Inserting or deleting a block mainly requires changing a link, rather than shifting later blocks as in contiguous allocation. Finding an arbitrary block is slower, but that does not prevent easy insertion/deletion.

<a id="q4"></a>

### Q4. [UGC-NET CS 2014 December-II] Directory data structure
The directory can be viewed as a ________ that translates filenames into their directory entries.

- (A) Symbol table
- (B) Partition
- (C) Swap space
- (D) Cache

**Answer: (A) Symbol table**

**Solution:** A directory maps a name to the corresponding file entry (metadata and location information). This is the same basic lookup role performed by a symbol table, which maps names to their associated records.

<a id="q5"></a>

### Q5. [ISRO CS 2018] Dense index
Which of the following is a dense index?

- (A) Primary index
- (B) Clustered index
- (C) Secondary index
- (D) Secondary non-key index

**Answer: (C) Secondary index**

**Solution:** A secondary index is on a field that does not determine the physical ordering of the data file. It generally needs an index entry for every search-key value/record (or a posting list covering all records), so it is dense. A primary or clustering index on an ordered data file can instead be sparse.

<a id="q6"></a>

### Q6. [UGC-NET CS 2018 July-II] Using operating-system authorization
A database system stores each relation in a separate operating-system file and uses the operating system’s authorization scheme instead of defining its own. Which statement is false?

- (A) The administrator enjoys more control on the grant option.
- (B) It is difficult to differentiate among update, delete, and insert authorizations.
- (C) It cannot store more than one relation in a file.
- (D) Operations on the database are speeded up because authorization is carried out at the operating-system level.

**Answer: (A) The administrator enjoys more control on the grant option.**

**Solution:** File permissions are coarse-grained: they do not naturally distinguish SQL operations such as insert, update, and delete, nor express the database's grant-option semantics. Separate files also mean one relation per file in this setup. The claim that OS permissions give the administrator more control over the database grant option is therefore the false statement.

<a id="q7"></a>

### Q7. [GATE CS 2008] Fields used for a clustering index
A clustering index is defined on fields that are of which type?

- (A) Non-key and ordering
- (B) Non-key and non-ordering
- (C) Key and ordering
- (D) Key and non-ordering

**Answer: (A) Non-key and ordering**

**Solution:** A clustering index orders the data records physically by a non-unique field, so several records can share a value and form a cluster. If the ordering field is a key, the usual term is primary index.

<a id="q8"></a>

### Q8. [ISRO CS 2007] Information aggregation for operational control
The level of aggregation of information required for operational control is:

- (A) Detailed
- (B) Aggregate
- (C) Qualitative
- (D) None of the above

**Answer: (A) Detailed**

**Solution:** Operational control concerns day-to-day work and individual transactions, so it needs detailed, current information rather than highly aggregated summaries.

<a id="q9"></a>

### Q9. [GATE CS 2021 Set 2] Blocks in an index file
A data file with 150,000 student records is stored on a hard disk with block size 4096 bytes. The data file is sorted on primary key `RollNo`. The record-pointer size is 7 bytes. Each student record has a candidate-key attribute `ANum` of size 12 bytes. An index file has records consisting of the `ANum` value and the corresponding student-record pointer and is stored on the same disk. Assume records of neither file are split across blocks. How many blocks does the index file occupy?

- (A) 698
- (B) 898
- (C) 899
- (D) 4096

**Answer: (A) 698**

**Solution:** One index record uses `12 + 7 = 19` bytes. A block holds `floor(4096/19) = 215` whole records. Therefore the number of index blocks is `ceil(150000/215) = 698`.

<a id="q10"></a>

### Q10. [UGC-NET CS 2015 June-III] Maximum file size with indexed allocation
In the indexed scheme of blocks for a file, the maximum possible file size depends on:

- (A) The number of blocks used for the index and the size of the index
- (B) Size of blocks and size of address
- (C) Size of index
- (D) Size of block

**Answer: (B) Size of blocks and size of address**

**Solution:** In the usual single-index-block scheme, a block of size `B` can hold about `B/P` block addresses, where `P` is the address size. Each address identifies one data block of size `B`, so the maximum data capacity depends on the block size and the address size. Indexing multiple levels would add the number/organization of index blocks as another parameter, but that is not specified here.

<a id="q11"></a>

### Q11. [ISRO CS 2011] RAID with double distributed parity
Which RAID level provides block-level striping with double distributed parity?

- (A) RAID 10
- (B) RAID 2
- (C) RAID 6
- (D) RAID 5

**Answer: (C) RAID 6**

**Solution:** RAID 5 distributes one parity block across the disks. RAID 6 distributes two independent parity blocks, allowing recovery from two disk failures; it also stripes data at block level.

<a id="q12"></a>

### Q12. [ISRO CS 2017 December] Snowflake schema
Which statement about a snowflake schema is true?

- (A) Each dimension is represented by a single dimensional table.
- (B) Maintenance efforts are less.
- (C) Dimension tables are normalized.
- (D) It is not an extension of the star schema.

**Answer: (C) Dimension tables are normalized.**

**Solution:** A snowflake schema normalizes dimension data into related tables, reducing repeated values. It is an extension of the star schema, typically with more joins and more maintenance, while a star schema keeps dimensions denormalized in single tables.

<a id="q13"></a>

### Q13. [GATE CS 2002] Indexed allocation and maximum file size
In the index-allocation scheme of blocks to a file, the maximum possible file size depends on:

- (A) The size of the blocks and the size of the address of the blocks
- (B) The number of blocks used for the index and the size of the blocks
- (C) The size of the blocks, the number of blocks used for the index, and the size of the address of the blocks
- (D) None of these

**Answer: (C) The size of the blocks, the number of blocks used for the index, and the size of the address of the blocks**

**Solution:** Each index block holds a finite number of block addresses, determined by its size divided by the size of an address. The number of index blocks available determines how many such addresses can be stored overall, and the data-block size converts the number of addressed blocks into bytes. All three quantities in (C) can therefore constrain the maximum file size.

<a id="q14"></a>

### Q14. [GATE CS 2013] Definition of a clustered index
An index is clustered if:

- (A) It is on a set of fields that form a candidate key.
- (B) It is on a set of fields that include the primary key.
- (C) The data records of the file are organized in the same order as the data entries of the index.
- (D) The data records of the file are organized not in the same order as the data entries of the index.

**Answer: (C) The data records of the file are organized in the same order as the data entries of the index.**

**Solution:** “Clustered” describes the physical relationship between the data-file order and index-entry order. Key status alone does not define clustering; an index whose data order does not follow its entries is unclustered.

<a id="q15"></a>

### Q15. [GFG practice] Snowflake schema normalization
Which statement about a snowflake schema is true?

- (A) Each dimension is represented by a single dimensional table.
- (B) Maintenance efforts are less.
- (C) Dimension tables are normalized.
- (D) It is not an extension of the star schema.

**Answer: (C) Dimension tables are normalized.**

**Solution:** In a snowflake schema, dimensions are split into normalized related tables. This contrasts with the denormalized, single-table dimensions of a typical star schema; the extra joins mean a snowflake is still an extension of the star design, not a replacement for that relationship.

<a id="q16"></a>

### Q16. [GATE IT 2005] Tuple nested-loop join block accesses
Table `T1` has 2000 records and occupies 80 disk blocks. Table `T2` has 400 records and occupies 20 disk blocks. The tables must be joined using a condition evaluated for every pair of records. Memory can hold exactly one block of `T1` and one block of `T2` at once. There are no indexes. Using nested-loop join and choosing the more appropriate relation for the outer loop, how many block accesses are required to read the data?

- (A) 800000
- (B) 40080
- (C) 32020
- (D) 100

**Answer: (C) 32020**

**Solution:** Put the relation with fewer tuples, `T2`, in the outer loop. For each of its 400 tuples, scan all 80 blocks of `T1`, then read `T2` once: `400 × 80 + 20 = 32,020` block accesses.

<a id="q17"></a>

### Q17. [ISRO CS 2017 December] Index for a low-cardinality query
Consider `Customers(custid, name, gender, rating)`. `rating` is an integer from 1 to 5, and `gender` has only two values, male and female. For the query “how many male customers have a rating of 5?”, which indexing mechanism is most appropriate?

- (A) Linear hashing
- (B) Extendible hashing
- (C) B+ tree
- (D) Bit-mapped hashing

**Answer: (D) Bit-mapped hashing**

**Solution:** Both queried attributes have very few possible values. Bitmap indexes can represent the rows for `gender = male` and `rating = 5` as bit vectors; intersecting them identifies exactly the qualifying customers, whose bits can then be counted.

<a id="q18"></a>

### Q18. [UGC-NET CS 2018 July-II] Hashing in a hierarchical database
In a hierarchical database, a hashing function is used to locate the ________.

- (A) Collision
- (B) Root
- (C) Foreign key
- (D) Records

**Answer: (B) Root**

**Solution:** In the hierarchical access method described by this question, the hash is used to find the root entry from which the hierarchy is traversed. It does not locate a collision or a relational foreign key.

<a id="q19"></a>

### Q19. [ISRO CS 2016] Definition of a trigger
A trigger is:

- (A) A statement that enables the DBMS to start.
- (B) A statement executed by the user while debugging an application program.
- (C) The condition the system tests to validate a database user.
- (D) A statement executed automatically by the system as a side effect of a database modification.

**Answer: (D) A statement executed automatically by the system as a side effect of a database modification.**

**Solution:** A trigger is associated with events such as insert, update, or delete. The DBMS runs its action automatically when the specified event occurs and its trigger condition is met.

<a id="q20"></a>

### Q20. [GATE CS 2014 Set 2] Maximum file size with a FAT
A FAT-based file system uses 4 bytes of overhead per FAT entry. The disk has capacity `100 × 10^6` bytes and the data-block size is `10^3` bytes. What is the maximum file size that can be stored on this disk, in units of `10^6` bytes?

- (A) 99.55 to 99.65
- (B) 100.5 to 101.4
- (C) 97.2 to 98.5
- (D) 89.1 to 91.2

**Answer: (A) 99.55 to 99.65**

**Solution:** The disk has `100×10^6 / 10^3 = 100,000` data blocks, so the FAT takes `100,000×4 = 400,000` bytes, or `0.4×10^6` bytes. The remaining space is `100−0.4 = 99.6×10^6` bytes, which is in interval (A).

<a id="q21"></a>

### Q21. [GATE CS Mock 2018 Set 2] Keys in a B+ tree non-leaf node
A B+ tree has search-key values of 12 bytes, block pointers of 6 bytes, and block size 1024 bytes. What is the maximum number of keys that can fit in each non-leaf node?

- (A) 57
- (B) 54
- (C) 58
- (D) 56

**Answer: (D) 56**

**Solution:** If an internal node has `m` pointers, it has `m−1` keys. Its size must satisfy `6m + 12(m−1) ≤ 1024`, or `18m ≤ 1036`, so `m ≤ 57`. Thus it can hold at most `57−1 = 56` keys. Record pointers are not stored in internal nodes.

<a id="q22"></a>

### Q22. [GATE CS 2015 Set 1] Clustered index definition
A file is organized so that the ordering of its data records is the same as, or close to, the ordering of data entries in an index. That index is called:

- (A) Dense
- (B) Sparse
- (C) Clustered
- (D) Unclustered

**Answer: (C) Clustered**

**Solution:** A clustered index has its data records stored in the same physical order as the index entries (or close to it). Density describes how many index entries exist, not the ordering relationship; an unclustered index does not preserve that physical order.

<a id="q23"></a>

### Q23. [GATE IT 2005] Reduction from block nested-loop join
Use the same data and memory constraints as follows: `T1` has 2000 records in 80 blocks and `T2` has 400 records in 20 blocks. The join condition is evaluated for every pair of records, memory holds one block of each relation at a time, and no index exists. If block nested-loop join is used instead of tuple nested-loop join, with the most appropriate outer relation, what is the reduction in block accesses?

- (A) 0
- (B) 30400
- (C) 38400
- (D) 798400

**Answer: (B) 30400**

**Solution:** Tuple nested-loop join costs `400×80+20 = 32,020` accesses with `T2` outer. With one block from each relation in memory, block nested-loop join scans the 80 blocks of `T1` once for each of the 20 blocks of `T2`: `20×80+20 = 1,620`. The reduction is `32,020−1,620 = 30,400` accesses.

<a id="q24"></a>

### Q24. [GATE CS 1998] Identify the field from an index order
A database has the following five records:

| Name | Age | Occupation | Category |
|---|---:|---|---|
| Rama | 27 | CON | A |
| Abdul | 22 | ENG | A |
| Jeniffer | 28 | DOC | B |
| Maya | 32 | SER | D |
| Dev | 24 | MUS | C |

An index file associated with these records contains the values `1, 3, 2, 5, 4`. Which field is the index built from?

- (A) Age
- (B) Name
- (C) Occupation
- (D) Category

**Answer: (C) Occupation**

**Solution:** Sorting the occupations alphabetically gives `CON` (record 1), `DOC` (3), `ENG` (2), `MUS` (5), `SER` (4), exactly `1,3,2,5,4`. Sorting by the other fields does not give that sequence.

<a id="q25"></a>

### Q25. [GATE CS 1997] Key counts and internal nodes in a B+ tree
A B+ tree of order `d` has between `d` and `2d` key values in each internal node, and an internal node with `M` keys has `M+1` children. The root, if internal, has between 1 and `2d` keys. All leaves are at the same distance from the root; height is the distance from the root to a leaf.

(a) What is the total number of key values in the internal nodes of a B+ tree with `L` leaves (`L ≥ 2`)?  
(b) What is the maximum number of internal nodes in a B+ tree of order 4 with 52 leaves?  
(c) What is the minimum number of leaves in a B+ tree of order `d` and height `h` (`h ≥ 1`)?

- (A) (a) `L+1`; (b) 8; (c) `2(d+1)^(h−1)`
- (B) (a) `L−1`; (b) 13; (c) `2(d+1)^(h−1)`
- (C) (a) `L−1`; (b) 17; (c) `2(d−1)^(h−1)`
- (D) (a) `L−1`; (b) 9; (c) `2(d−1)^(h+1)`

**Answer: (B) (a) `L−1`; (b) 13; (c) `2(d+1)^(h−1)`**

**Solution:** Across the tree, each internal key separates child subtrees, so the total number of internal keys is `L−1`. For order 4, every non-root internal node has at least 4 keys and the root at least 1. If there are `I` internal nodes, then `51 = L−1 ≥ 1+4(I−1)`, giving `I ≤ 13`; this bound is attainable. For minimum leaves, the root has at least two children, and each later internal level has at least `d+1` children, so the minimum is `2(d+1)^(h−1)`.

<a id="q26"></a>

### Q26. [ISRO CS 2017 December] Counting using only an index
Consider the query:

```sql
SELECT E.eno, COUNT(*)
FROM Employees E
GROUP BY E.eno;
```

If an index on `eno` is available, the query can be answered by scanning only the index if:

- (A) The index is only hash and clustered
- (B) The index is only B+ tree and clustered
- (C) The index can be hash or B+ tree, and clustered or non-clustered
- (D) The index can be hash or B+ tree and clustered

**Answer: (C) The index can be hash or B+ tree, and clustered or non-clustered.**

**Solution:** The query needs only `eno` and the number of index entries for each value. A dense index contains an `eno` entry for every employee record, so the other columns and data pages need not be read. The index entries can be scanned and grouped whether the index is hash/tree or clustered/non-clustered.

<a id="q27"></a>

### Q27. [ISRO CS 2008] Purpose of RAID
RAID configurations of disks are used to provide:

- (A) Fault tolerance
- (B) High speed
- (C) High data density
- (D) A and B

**Answer: (D) A and B**

**Solution:** Striping can improve throughput, while mirroring or parity provides redundancy and fault tolerance. RAID is not defined by higher data density, so both (A) and (B) are the intended benefits.

<a id="q28"></a>

### Q28. [ISRO CS 2016] Order of leaf records in a B+ tree
The order of a leaf node is the maximum number of `(value, data-record pointer)` pairs it can hold. The block size is 1 KB, a data-record pointer is 7 bytes, a value is 9 bytes, and a block pointer is 6 bytes. What is the order of the leaf node?

- (A) 63
- (B) 64
- (C) 67
- (D) 68

**Answer: (A) 63**

**Solution:** A leaf stores `m` key/record-pointer pairs and one 6-byte link to the next leaf. Therefore `m(9+7)+6 ≤ 1024`, so `m ≤ floor(1018/16) = 63`.

<a id="q29"></a>

### Q29. [ISRO CS 2016] Fields used for a clustering index
A clustering index is defined on fields that are of which type?

- (A) Non-key and ordering
- (B) Non-key and non-ordering
- (C) Key and ordering
- (D) Key and non-ordering

**Answer: (A) Non-key and ordering**

**Solution:** A clustering index organizes physically ordered records by a non-unique field. A unique ordering field corresponds to a primary index; a non-ordering field does not cluster the stored records.

<a id="q30"></a>

### Q30. [UGC-NET CS 2017 January-III] Insertions into an order-3 B+ tree
Keys are inserted, in this order, into a B+ tree with `K = 3` pointers:

`8, 5, 1, 7, 3, 12, 9, 6`

Which of the following is the correct B+ tree?

- (A) Diagram (1)
- (B) Diagram (2)
- (C) Diagram (3)
- (D) Diagram (4)

> Note: The original option diagrams are not reproduced. Diagram (1) was identified as the keyed answer; the resulting tree is shown below for a readable check.

**Answer: (A) Diagram (1)**

**Solution:** With at most three child pointers, each internal node has at most two keys. On overflow, split the leaf and copy its first key in the new right leaf up to the parent. In insertion order, the final tree is:

```text
                         [7]
                /                 \\
             [5]                 [8 | 9]
           /     \\             /   |    \\
       [1 | 3] [5 | 6]        [7]  [8]  [9 | 12]
```

The separator keys route searches to the leaves, and the leaves are in sorted order. This is the described first diagram; it is the only choice consistent with the splits.

<a id="q31"></a>

### Q31. [ISRO CS 2015] Blocks for data and dense index
A block can hold either 3 data records or 10 key pointers. A database contains `n` records. How many blocks are needed for the data file and a dense index?

- (A) `13n/30`
- (B) `n/3`
- (C) `n/10`
- (D) `n/30`

**Answer: (A) `13n/30`**

**Solution:** The data file uses `n/3` blocks and the dense index has one pointer per record, so it uses `n/10` blocks. Their sum is `n/3+n/10 = 13n/30`. For arbitrary integer `n`, exact allocation uses `ceil(n/3)+ceil(n/10)`; the listed expression is the usual capacity-ratio answer (exact when `n` is divisible by 30).

<a id="q32"></a>

### Q32. [ISRO CS 2013] Leaf and internal node capacity in a B+ tree
Calculate the order of leaf (`p_leaf`) and non-leaf (`p`) nodes of a B+ tree given:

- Search-key field: 12 bytes
- Record pointer: 10 bytes
- Block pointer: 8 bytes
- Block size: 1 KB

- (A) `p_leaf = 51` and `p = 46`
- (B) `p_leaf = 47` and `p = 52`
- (C) `p_leaf = 46` and `p = 50`
- (D) `p_leaf = 52` and `p = 47`

**Answer: (C) `p_leaf = 46` and `p = 50`**

**Solution:** For a leaf with `n` key/record-pointer pairs and one 8-byte next-leaf pointer, `22n+8 ≤ 1024`, giving `n = 46`. For a non-leaf node with `n` keys and `n+1` block pointers, `12n+8(n+1) ≤ 1024`, so `20n+8 ≤ 1024` and `n ≤ 50`. The option uses `p` for the maximum key count; if “order” is instead defined as the maximum number of child pointers, that internal fan-out is `p+1 = 51`.

<a id="q33"></a>

### Q33. [ISRO CS 2013] Formula-based record location
The physical location of a record is determined by a formula that transforms a file key into a record location. This describes a:

- (A) Hashed file
- (B) B-tree file
- (C) Indexed file
- (D) Sequential file

**Answer: (A) Hashed file**

**Solution:** A hash function transforms the key into a bucket or record address. A B-tree or other index uses a search structure rather than directly computing the location from the key.

<a id="q34"></a>

### Q34. [ISRO CS 2013] Embedded pointer
An embedded pointer provides:

- (A) A secondary access path
- (B) A physical record key
- (C) An inverted index
- (D) A prime key

**Answer: (A) A secondary access path**

**Solution:** An embedded pointer stored with a record can point to related records, allowing retrieval through an access path other than the file’s primary physical sequence. It is not itself a key or an inverted index.

<a id="q35"></a>

### Q35. [ISRO CS 2008] Embedded pointer
An embedded pointer provides:

- (A) A secondary access path
- (B) A physical record key
- (C) An inverted index
- (D) A primary key

**Answer: (A) A secondary access path**

**Solution:** The pointer supplies an alternate way to reach a related record, hence a secondary access path. The other choices describe keys or a different index structure.

<a id="q36"></a>

### Q36. [GATE CS 1999] B-trees and B+ trees
Which statement is correct?

- (A) B-trees are for storing data on disk and B+ trees are for main memory.
- (B) Range queries are faster on B+ trees.
- (C) B-trees are for primary indexes and B+ trees are for secondary indexes.
- (D) The height of a B+ tree is independent of the number of records.

**Answer: (B) Range queries are faster on B+ trees.**

**Solution:** B+ trees keep data entries at the leaves and link leaves in key order. After locating the start of a range, a scan can follow the leaf links. Both B- and B+ trees are used for disk indexing, either can support index types, and the height grows logarithmically with the number of records rather than being independent of it.
