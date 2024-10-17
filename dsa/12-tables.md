# Tables

A **table** is a collection of records, each with a unique key and a value. Keys must be unique, while values can repeat. Tables are flexible for managing data and provide fast access, updates, and enumeration.

### Table Operations

1. **initialize**: Create an empty table.
2. **isEmpty**: Check if the table has no records.
3. **isFull**: Check if the table is at capacity.
4. **insert**: Add a new `key:value` record.
5. **delete**: Remove the record with a specific key.
6. **update**: Change the value for a given key.
7. **find**: Look up a record by key.
8. **enumerate**: List or count all records.

### Simple Implementation (Sorted Array)

A basic table can be implemented as an array sorted by keys.

#### Insertion/Update

1. **Find the position** using binary search, which takes **O(log n)**.
2. If the key exists, **replace the value**.
3. If the key doesn’t exist, **shift records** and insert, taking **O(n)**.

#### Remove

1. **Find the record** with binary search: **O(log n)**.
2. **Shift records** to fill the gap, taking **O(n)**.

#### Search

Use binary search to find records in **O(log n)**.

### Drawbacks

The sorted array makes search fast (**O(log n)**), but insert and delete are slow because of shifting (**O(n)**).

### Time Complexities

| Operation   | Time Complexity |
|-------------|-----------------|
| Search      | O(log n)        |
| Insert      | O(n)            |
| Update      | O(log n)        |
| Remove      | O(n)            |
