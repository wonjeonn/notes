# Searching Algorithms

**Searching** is the process of locating a specific piece of data (the key) within a data structure. The efficiency of searching largely depends on how the data is organized.

## Linear Search
The **linear search** algorithm iterates through a list to find the key, returning the first index where it is found or -1 if it is not present.

#### Implementation
**Python:**
```python
def linear_search(my_list, key):
    for i in range(len(my_list)):
        if my_list[i] == key:
            return i
    return -1
```
- **Time Complexity**: O(n)
- Sorting the list before searching does not improve efficiency, as the overhead from sorting results in a total cost greater than O(n).

## Binary Search
The **binary search** algorithm operates only on sorted lists that support random access.

### Preconditions for Binary Search
1. The list must be sorted to allow division into potential halves.
2. The list must allow fast random access.

### Algorithm Steps
1. Track the range of possible indexes with `low_index` and `high_index`.
2. Calculate the midpoint index.
3. Compare the middle element:
   - If it matches the key, return the index.
   - If the key is smaller, adjust `high_index`.
   - If the key is larger, adjust `low_index`.
4. Repeat until the range is exhausted.

#### Implementation
**Python:**
```python
def binary_search(my_list, key):
    low_index = 0
    high_index = len(my_list) - 1

    while low_index <= high_index:
        mid_index = (low_index + high_index) // 2
        if key == my_list[mid_index]:
            return mid_index
        elif key < my_list[mid_index]:
            high_index = mid_index - 1
        else:
            low_index = mid_index + 1

    return -1
```
