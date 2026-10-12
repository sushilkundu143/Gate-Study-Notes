# 7. File Organization and Indexing (B and B+ Trees)

Disk I/O is slow, so GATE questions count **block accesses**. All formulas below assume one node = one disk block.

## 7.1 Basic Terms

| Term | Meaning |
| --- | --- |
| Block (page) | Unit of transfer between disk and memory, size `B` bytes |
| Record size | `R` bytes |
| Blocking factor `bfr` | Records per block = `⌊B / R⌋` (unspanned) |
| Number of blocks | `b = ⌈r / bfr⌉` for `r` records |
| Unspanned | A record never crosses a block boundary (wastes leftover space) |
| Spanned | Records may cross blocks; `bfr = B / R` (no waste, extra pointer) |

## 7.2 File Organizations

| Organization | Insert | Search on key | Notes |
| --- | --- | --- | --- |
| Heap (unordered) | O(1): append | Linear: average `b/2`, worst `b` | Simple, slow search |
| Sorted (sequential) | Expensive (shift / overflow) | Binary: `⌈log₂ b⌉` | Good for range queries |
| Hashed | O(1) average | ~1 block (equality only) | Bad for range queries |

### Hashing

- **Static hashing**: fixed number of buckets; overflow chains when buckets fill.
- **Extendible hashing**: directory of size `2^(global depth)`; each bucket has a local depth.
  On overflow, split the bucket; if `local depth = global depth` the directory doubles.
- **Linear hashing**: buckets split one by one in round-robin order; no directory.

## 7.3 Index Types

| Index | Built on | Dense / Sparse | Number of index entries | Per file |
| --- | --- | --- | --- | --- |
| Primary | Ordering **key** field | Sparse | Number of data **blocks** | At most 1 |
| Clustering | Ordering **non-key** field | Sparse | Number of **distinct values** | At most 1 |
| Secondary (key) | Non-ordering key field | Dense | Number of **records** | Many |
| Secondary (non-key) | Non-ordering non-key field | Dense (with indirection block) | Distinct values | Many |

- **Dense index**: one entry per search-key value / record.
- **Sparse index**: entries for only some values (one per block); needs sorted data.
- A file can have **either** one primary **or** one clustering index (data can be sorted only one way) plus many secondary indexes.
- **Clustered index**: data records are physically ordered the same way as the index.

### Single-level index cost

```text
Index entry size   = key size + block pointer size
Index bfr (bfri)   = ⌊B / entry size⌋
Index blocks (bi)  = ⌈entries / bfri⌉
Search cost        = ⌈log₂ bi⌉ + 1  (binary search on index + 1 data block)
```

### Multilevel index

Treat the index as a file and index it again until one block remains.

```text
fan-out fo = bfri
level 1 blocks = ⌈entries / fo⌉
level 2 blocks = ⌈level1 / fo⌉   ... until 1
Search cost    = number of levels + 1 (data block)
```

### Worked example

16,384 records, record size 32 B, key size 6 B, block size 1024 B, block pointer 10 B, secondary index on the key field.

- Entry = 6 + 10 = 16 B → `bfri = 1024 / 16 = 64`.
- Dense secondary index → 16,384 entries → level 1 = `16384 / 64 = 256` blocks.
- Level 2 = `⌈256 / 64⌉ = 4` blocks; level 3 = 1 block.

## 7.4 B Tree

A balanced search tree where **every node stores keys with record (data) pointers**.

Node of order `p` (max `p` children):

```text
p × (block pointer) + (p − 1) × (key + record pointer) ≤ B
```

Properties for order `p`:

| Node | Children | Keys |
| --- | --- | --- |
| Root (non-leaf) | 2 … p | 1 … p − 1 |
| Internal | ⌈p/2⌉ … p | ⌈p/2⌉ − 1 … p − 1 |
| Leaf | 0 | ⌈p/2⌉ − 1 … p − 1 |

All leaves are at the same level.

## 7.5 B+ Tree (Most Asked)

- Internal nodes store **only keys + child pointers** (more fan-out).
- **All data pointers are in leaves**; leaves are linked for range scans.
- Every key appears in a leaf; some keys are repeated in internal nodes as separators.

### Node capacity formulas

```text
Internal node order p (max children):
  p × Pblock + (p − 1) × K ≤ B

Leaf order p_leaf (max key–record-pointer pairs):
  p_leaf × (K + Precord) + Pblock (next-leaf pointer) ≤ B
```

Example: `B = 512`, `K = 14`, block pointer = 6 →
`6p + 14(p − 1) ≤ 512` → `20p ≤ 526` → **p = 26**.

### Height and disk accesses

With fan-out `p` and `L` leaf nodes, internal levels = `⌈log_p L⌉` (roughly).

Search cost for a record = (levels of B+ tree including leaf) + 1 (data block).

Example: `B = 4096`, `K = 12`, pointer = 8, 1,000,000 records:

- Internal order: `8p + 12(p − 1) ≤ 4096` → `p = 205`.
- Leaf capacity: `20n + 8 ≤ 4096` → `n = 204` → leaves = `⌈10⁶ / 204⌉ = 4902`.
- Internal levels: `⌈4902 / 205⌉ = 24` → `⌈24 / 205⌉ = 1` → 2 internal levels.
- Accesses = 2 internal + 1 leaf + 1 data block = **4**.

### Minimum / maximum keys (order p = max children, height h counted in levels)

| | B+ tree (keys stored in leaves, L ≥ 2) | B tree (keys) |
| --- | --- | --- |
| Max keys in tree with L levels | `p^(L−1) × p_leaf` | `p^L − 1` |
| Min keys in tree with L levels | `2⌈p/2⌉^(L−2) × ⌈p_leaf/2⌉` | `2⌈p/2⌉^(L−1) − 1` |

### Insertion (B+ tree)

1. Find the correct leaf and insert in sorted order.
2. If the leaf overflows (more than `p_leaf` keys): split into two halves,
   **copy** the first key of the right half up to the parent.
3. If an internal node overflows: split it and **move** the middle key up (not copied).
4. If the root splits, a new root is created → height grows by 1 (trees grow at the **root**).

### Deletion (B+ tree)

1. Remove the key from the leaf.
2. If the leaf underflows, **borrow** from a sibling (update parent separator), else **merge** with a sibling and delete the separator from the parent.
3. Underflow can propagate upward; if the root becomes empty, height shrinks.

## 7.6 B Tree vs B+ Tree

| Feature | B tree | B+ tree |
| --- | --- | --- |
| Data pointers | All nodes | Leaves only |
| Fan-out | Smaller | Larger (internal nodes have only keys) |
| Height | Taller | Shorter |
| Range queries | In-order traversal | Linked leaf scan (fast) |
| Duplicate keys | No | Keys repeated in internal nodes |
| Search ends | May end at internal node | Always ends at a leaf |

## 7.7 Common Traps

1. Read the definition of "order" in the question (max children, max keys, or min keys).
2. Leaf nodes use **record** pointers; internal nodes use **block (tree)** pointers.
3. Don't forget the **next-leaf pointer** in a B+ tree leaf.
4. Add **+1** block access to reach the data block when the question asks for the record.
5. Primary index is sparse (one entry per block); secondary index on a key is dense (one per record).
