# Linear Probing

**Linear Probing** is a collision resolution technique in hash tables that employs **open addressing**. Instead of storing multiple items at a single index (as in chaining), linear probing ensures that each index contains only one item. When collisions occur, the method searches for the next available index by probing sequentially.

## Collision Resolution: Open Addressing

In open addressing, if the initial index calculated by the hash function is already occupied, the algorithm searches for the next available index, wrapping around the table if necessary. This avoids using secondary data structures like linked lists.

### Probing Sequence
When a key $k$ is hashed to index $i$, the probing sequence checks consecutive indices until an empty slot is found:
$$
i, (i + 1) \mod m, (i + 2) \mod m, (i + 3) \mod m, \ldots
$$
where $m$ is the size of the table.

### Table Structure
- The hash table is treated as a **circular array**. If the end of the array is reached, the search continues from the beginning.
- **Clusters**: Linear probing can lead to **clusters** — groups of consecutive occupied slots. Clustering increases search and insertion times by creating longer probing sequences.

---

## Algorithms

### Insertion

1. **Hash**: Compute the hash index for the key.
2. **Probe**: If the index is occupied, probe the next index sequentially.
3. **Wrap Around**: If the end of the table is reached, wrap around to the beginning.
4. **Insert**: Place the item in the first available slot.

### Search

1. **Hash**: Calculate the index where the key should be located.
2. **Probe**: If the desired key is not found at the calculated index, probe the next index.
3. **Stop Condition**: If an empty slot is found, stop searching, as the key is not in the table.

### Deletion

1. **Find**: Use the search algorithm to locate the key to be deleted.
2. **Delete**: Mark the slot as empty or deleted.
3. **Reorganize**: To maintain the integrity of the cluster, adjust any following records in the cluster as necessary.

---

## Example

Consider a hash table of size 10. The following keys and their respective hash indices are shown:

| Key | Hash Index |
|-----|------------|
| k1  | 8          |
| k2  | 7          |
| k3  | 9          |
| k4  | 1          |
| k5  | 8          |

### Insertion Steps

1. **Insert $k1$** at index 8 (no collision).
2. **Insert $k2$** at index 7 (no collision).
3. **Insert $k3$** at index 9 (no collision).
4. **Insert $k4$** at index 1 (no collision).
5. **Insert $k5$**: The hash index for $k5$ is 8, but index 8 is occupied by $k1$. Linear probing checks index 9 (occupied by $k3$) and index 0 (empty), so $k5$ is placed at index 0.

### Search Example: $k6$

The hash index for $k6$ is 9. Probing starts at index 9 but $k6$ is not found. The search continues to index 0, then index 1, and stops at index 2 (an empty slot), indicating $k6$ is not in the table.

### Deletion Example: $k3$

When $k3$ (at index 9) is deleted, any following records within the cluster must be checked to preserve the cluster's integrity. In this case, no adjustments are needed, and index 9 is marked as empty.

---

## Tombstoning

An alternative to immediately removing items in open addressing is **tombstoning**. In tombstoning, deleted slots are marked as **Deleted** rather than cleared, to maintain the search path. The three possible states of each slot are:

- **Empty**: The slot has never been used.
- **Used**: The slot contains an active record.
- **Deleted**: A record once existed but has since been deleted.

### Tombstoning Algorithms

#### Insertion
Items are inserted into the first slot marked as **Empty** or **Deleted**.

#### Search
The search skips over slots marked as **Deleted** and stops at **Empty** slots, as these indicate the end of the probe.

#### Deletion
Items are marked as **Deleted** without moving other records.

---

## Advanced Probing Techniques

### Quadratic Probing

**Quadratic Probing** reduces clustering by increasing the gap between successive probes. Instead of checking the next index linearly, it probes based on a quadratic function:
$$
\text{hash}(k) + 1^2, \text{hash}(k) + 2^2, \text{hash}(k) + 3^2, \ldots
$$
This spreads out the probing sequence, reducing the likelihood of creating long clusters.

#### Example
If the hash index for $k4$ is 7, the quadratic probe sequence would be:
$$
(7 + 0^2) \mod 10, (7 + 1^2) \mod 10, (7 + 2^2) \mod 10, \ldots = 7, 8, 1, 6, \ldots
$$
$k4$ would be inserted at index 1 if indices 7 and 8 are occupied.

### Double Hashing

**Double Hashing** reduces clustering further by using two hash functions. The first hash function calculates the initial index, and the second hash function provides the offset for probing. The general form is:
$$
\{ \text{hash1}(k), (\text{hash1}(k) + \text{hash2}(k)) \mod m, (\text{hash1}(k) + 2 \cdot \text{hash2}(k)) \mod m, \ldots \}
$$
Double hashing is effective at spreading out the probe sequence, preventing the formation of clusters.

#### Example
Let:
- $ \text{hash1}(k1) = 8 $
- $ \text{hash2}(k1) = 6 $

The probe sequence would be:
$$
8, (8 + 6) \mod 10 = 4, (8 + 2 \cdot 6) \mod 10 = 0, \ldots
$$
If $k1$ is placed at index 8, the next record would be placed at index 4 if there’s a collision, and then index 0.
