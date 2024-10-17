# Hash Tables

A **hash table** is a data structure that maps keys to specific locations (indices) in an array. This is done using a **hash function**, which generates an index from each key, enabling fast data retrieval.

## Hash Functions

A **hash function** takes a key and returns a numeric index, which represents the location in the hash table.

- **Deterministic**: Always returns the same index for a given key.
- **Uniform distribution**: Spreads keys evenly across the table, reducing collisions.
- **Randomness**: Avoids predictable patterns that can lead to clustering.

### Example Hash Function

For a table storing customer data based on phone numbers, relying solely on the area code for the hash function would lead to poor distribution, as many customers may share the same area code. A better option would be using the last four digits, which vary more widely.

## Load Factor

The **load factor** (λ) is a measure of how full a hash table is, and it is calculated by:

$$
λ = \frac{\text{number of records (n)}}{\text{table capacity (m)}}
$$

A higher load factor increases the likelihood of collisions.

## Collisions

When two keys hash to the same index, a **collision** occurs. Since the number of possible keys usually exceeds the number of available slots, collisions are inevitable.

### Collision Handling: Chaining

One way to resolve collisions is **chaining**. In this method, each index in the hash table points to a linked list. Multiple records can be stored in the same slot as part of the list.

#### Example of Chaining

Suppose six keys—$k1, k2, k3, k4, k5, k6$—map to the following indices:

- $k1$ → index 0
- $k2$ → index $m - 3$
- $k3$ → index $m - 1$
- $k4$ → index $m - 3$
- $k5$ → index 0
- $k6$ → index $m - 3$

This results in a table with linked lists at index 0 (holding $k1$ and $k5$) and index $m-3$ (holding $k2, k4, k6$).

## Time Complexity

### Worst-Case Complexity

In the worst case, all keys could hash to the same index, creating a long linked list:

- **Insert**: Θ(n)
- **Search**: Θ(n)
- **Delete**: Θ(n)

Finding the linked list is constant time Θ(1), but searching through it can take Θ(n) if the list is long.

### Average-Case Complexity

Under the **Simple Uniform Hash Assumption (SUHA)**, which assumes keys are uniformly distributed across the hash table, the average time complexity is:

$$
O(1 + λ)
$$

Where λ is the load factor. A well-distributed table ensures shorter chains and faster operations.

| Operation   | Average Time Complexity | Worst Case Time Complexity |
|-------------|--------------------------|----------------------------|
| Insert      | O(1 + λ)                  | O(n)                       |
| Search      | O(1 + λ)                  | O(n)                       |
| Delete      | O(1 + λ)                  | O(n)                       |
