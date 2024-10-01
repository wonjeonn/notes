# Merge Sort

Merge Sort is a **divide-and-conquer** algorithm that breaks down a list into smaller sublists, sorts those sublists, and merges them to form a sorted list.

- **Time Complexity**: $O(n\ \log\ n)$ for all cases (best, average, worst).
- **Space Complexity**: $O(n)$, as it requires additional space for merging.
- **Stable**: Preserves the relative order of equal elements.

### Steps of Merge Sort

1. **Divide the List**
   - Recursively split the list into two halves until the sublists are of size 1. A list with 1 element is already sorted.
   
2. **Merge Sorted Sublists**
   - Combine two sorted sublists into a single sorted list using the merge process. Merging takes **$O(n)$** time, where $n$ is the total number of elements in the sublists.

### Merge Sort Algorithm

1. **Temporary List for Merging**
   - A temporary list is created to hold the merged result during each merge step, avoiding repeated memory allocation.

2. **Recursive Merge Sort**
   - The list is recursively divided into halves.
   - The sublists are merged by comparing elements from each half.

3. **Merge Two Sorted Sublists**
   - Use two pointers to track the smallest elements in each sublist.
   - Compare the elements pointed to by the pointers, copy the smaller one into the temporary list, and move the pointer forward.
   - Continue until all elements from both sublists are copied.
   - The merged sorted list is copied back into the original list.

### Example
![Merge Sort Example](https://upload.wikimedia.org/wikipedia/commons/c/cc/Merge-sort-example-300px.gif)

### Implementation

#### 1. `merge_sort()`

This function initializes the temporary list and calls the recursive function to sort the list.

```python
def merge_sort(mylist):
    empty_list = [0] * len(mylist)  # Temporary list for merging
    recursive_merge_sort(mylist, 0, len(mylist) - 1, empty_list)  # Start recursive merge sort
```

#### 2. `recursive_merge_sort()`

This function recursively splits the list into two halves and calls the merge function to merge them.

```python
def recursive_merge_sort(mylist, first_index, last_index, empty_list):
    if first_index < last_index:  # Base case: stop when list has 1 or 0 elements
        mid_index = (first_index + last_index) // 2  # Find the middle index
        recursive_merge_sort(mylist, first_index, mid_index, empty_list)  # Sort first half
        recursive_merge_sort(mylist, mid_index + 1, last_index, empty_list)  # Sort second half
        merge(mylist, first_index, mid_index + 1, last_index, empty_list)  # Merge the sorted halves
```

#### 3. `merge()`

This function merges two sorted sublists into a single sorted list.

```python
def merge(mylist, a_first_index, b_first_index, b_last_index, empty_list):
    a_ptr = a_first_index  # Pointer for the first sublist (a)
    b_ptr = b_first_index  # Pointer for the second sublist (b)
    empty_list_index = a_ptr  # Pointer for the merged list

    # Merge the sublists into empty_list
    while a_ptr < b_first_index and b_ptr <= b_last_index:
        if mylist[a_ptr] <= mylist[b_ptr]:
            empty_list[empty_list_index] = mylist[a_ptr]
            a_ptr += 1
        else:
            empty_list[empty_list_index] = mylist[b_ptr]
            b_ptr += 1
        empty_list_index += 1

    # Copy any remaining elements from the first sublist
    while a_ptr < b_first_index:
        empty_list[empty_list_index] = mylist[a_ptr]
        a_ptr += 1
        empty_list_index += 1

    # Copy any remaining elements from the second sublist
    while b_ptr <= b_last_index:
        empty_list[empty_list_index] = mylist[b_ptr]
        b_ptr += 1
        empty_list_index += 1

    # Copy the merged list back into the original list
    for i in range(a_first_index, b_last_index + 1):
        mylist[i] = empty_list[i]
```

### Time and Space Complexity of Merge Sort

- **Time Complexity**: $O(n\ \log\ n)$
   - Each level of recursion splits the list in half, creating $O(\log\ n)$ levels.
   - At each level, merging the sublists takes $O(n)$, leading to the overall complexity of $O(n\ \log\ n)$.

- **Space Complexity**: $O(n)$
   - A temporary list of size $n$ is required for the merging process.

### Applications of Merge Sort

- **Large Datasets**: Useful for handling large datasets that need guaranteed performance ($O(n\ \log\ n)$).
- **External Sorting**: Efficient for sorting data that doesn’t fit entirely into memory, such as when working with data stored on disks.
- **Stable Sorting**: Suitable for sorting databases where the order of records with equal keys must be preserved.
