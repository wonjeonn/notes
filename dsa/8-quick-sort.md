# Quick Sort

Quick Sort is a **divide-and-conquer** algorithm that sorts a list by partitioning it into three sections.
1. All elements smaller than a chosen **pivot**.
2. The **pivot** itself.
3. All elements larger than the **pivot**.

The pivot is placed in its correct sorted position, and the process is recursively applied to the sublists before and after the pivot.

- **Average Time Complexity**: $O(n\ \log\ n)$
- **Worst Case Time Complexity**: $O(n²)$ (occurs when the pivot consistently splits the array unevenly, such as picking the smallest or largest element repeatedly).
- **Space Complexity**: $O(log\ n)$ due to the recursion stack.
- **In-Place Algorithm**: Quick sort sorts the list in place and requires no extra storage space, unlike merge sort.

### Steps of Quick Sort

1. **Base Case**
   - If the sublist is small (below a certain threshold, typically between 16–32 elements), quick sort may switch to **insertion sort** for efficiency.

2. **Recursive Case**
   - Partition the list into three sections: elements smaller than the pivot, the pivot, and elements larger than the pivot.
   - Recursively apply quick sort to the sublists on either side of the pivot.

### Quick Sort Algorithm

1. **Choose a Pivot**
   - A pivot is randomly selected from the list to minimize the risk of worst-case performance.
   
2. **Move Pivot to End**
   - Swap the pivot with the element at the end of the list to simplify partitioning.

3. **Partitioning**
   - Traverse the list. For each element smaller than the pivot, swap it into the smaller partition.
   - After partitioning, swap the pivot back to its correct position between the smaller and larger elements.

4. **Recursive Sorting**
   - Apply quick sort recursively to the sublists created before and after the pivot.

### Example
![Quick Sort Example](https://upload.wikimedia.org/wikipedia/commons/9/9c/Quicksort-example.gif)

###  Implementation

#### 1. `quick_sort()`

This function initiates the recursive quick sort algorithm.

```python
def quick_sort(mylist):
    recursive_quick_sort(mylist, 0, len(mylist) - 1)  # Start recursive quick sort
```

#### 2. `recursive_quick_sort()`

The recursive function divides the list into smaller partitions and sorts them. If the partition size is small, it switches to **insertion sort** for efficiency.

```python
def recursive_quick_sort(mylist, left, right, THRESHOLD=32):
    if right - left <= THRESHOLD:  # Use insertion sort for small partitions
        insertion_sort(mylist, left, right)
    else:
        pivot_position = partition(mylist, left, right)  # Partition the list
        recursive_quick_sort(mylist, left, pivot_position - 1)  # Sort left sublist
        recursive_quick_sort(mylist, pivot_position + 1, right)  # Sort right sublist
```

#### 3. `insertion_sort()`

This function performs insertion sort on a sublist of the array. Insertion sort is more efficient for small datasets.

```python
def insertion_sort(mylist, left, right):
    for i in range(left + 1, right + 1):
        curr = mylist[i]  # Current element to insert
        j = i
        # Shift elements to the right to make space for curr
        while j > left and mylist[j - 1] > curr:
            mylist[j] = mylist[j - 1]
            j -= 1
        mylist[j] = curr  # Insert curr at the correct position
```

#### 4. `partition()`

The partition function rearranges the list so that all elements smaller than the pivot are on the left, and all larger elements are on the right.

```python
import random

def partition(mylist, left, right):
    # Randomly choose a pivot
    pivot_location = random.randint(left, right)
    pivot = mylist[pivot_location]

    # Move pivot to the end
    mylist[pivot_location], mylist[right] = mylist[right], mylist[pivot_location]

    # Initialize the end of the smaller partition
    end_of_smaller = left - 1

    # Partition the list based on the pivot
    for j in range(left, right):
        if mylist[j] <= pivot:
            end_of_smaller += 1
            mylist[end_of_smaller], mylist[j] = mylist[j], mylist[end_of_smaller]

    # Move the pivot to its correct position
    mylist[end_of_smaller + 1], mylist[right] = mylist[right], mylist[end_of_smaller + 1]

    # Return the pivot's final position
    return end_of_smaller + 1
```

- **Pivot Selection**: A random pivot helps reduce the likelihood of the worst-case time complexity $O(n²)$.
- **In-Place Sorting**: Unlike merge sort, quick sort sorts the list in place to save space.
- **Small Partitions**: Quick sort may switch to **insertion sort** for small partitions to improve performance.

### Time and Space Complexity of Quick Sort

- **Best Case**: $O(n\ \log\ n)$ - occurs when the pivot consistently splits the list into two equal halves.
- **Average Case**: $O(n\ \log\ n)$ - the pivot usually splits the list into reasonably balanced partitions.
- **Worst Case**: $O(n²)$ - occurs when the pivot consistently splits the list unevenly (e.g., choosing the smallest or largest element repeatedly).
- **Space Complexity**: $O(log\ n)$ - for the recursion stack in the average case.

### Applications of Quick Sort

- **Efficient In-Place Sorting**: Widely used in applications where memory is limited, as it requires minimal additional storage.
- **Large Datasets**: Performs well on large datasets, especially when the pivot is chosen efficiently.
- **Performance Optimization**: Often used in systems that require fast and efficient sorting in real-time operations, like databases and operating systems.
