# Sorting Algorithms

**Sorting** is the process of arranging elements in a specific order (e.g., ascending or descending) based on certain criteria. Sorting can be applied to various data types such as numbers, strings, or objects.

## Simple Sorts: Time Complexity O(n²)

These algorithms are intuitive and easy to implement, but inefficient for large datasets. They work best for small or nearly sorted datasets.

---

### 1. Bubble Sort

**Bubble Sort** repeatedly compares adjacent elements and "bubbles" the largest one to the end of the list by swapping them if needed. This process continues until the entire list is sorted.

#### Algorithm Steps:
1. Compare adjacent elements and swap them if they are out of order.
2. Continue comparing and swapping for each adjacent pair.
3. Repeat this process for **n-1 passes** (where **n** is the number of elements).

#### Example:
![Bubble Sort Example](https://upload.wikimedia.org/wikipedia/commons/c/c8/Bubble-sort-example-300px.gif)

#### Implementation:
```python
def bubble_sort(my_list):
    n = len(my_list)
    for i in range(n - 1):
        for j in range(n - 1 - i):
            if my_list[j] > my_list[j + 1]:
                my_list[j], my_list[j + 1] = my_list[j + 1], my_list[j]
```

#### Features:
- **Time Complexity**: O(n²)
- **Space Complexity**: O(1)
- **Stability**: Yes (maintains the relative order of equal elements)
- **Best Case**: O(n) (when the array is already sorted, no swaps are needed)

---

### 2. Selection Sort

**Selection Sort** selects the smallest element from the unsorted portion of the list and swaps it with the first element of the unsorted portion. The process repeats until the list is sorted.

#### Algorithm Steps:
1. Find the smallest element in the unsorted portion.
2. Swap it with the first element of the unsorted portion.
3. Repeat for the next index until all elements are sorted.

#### Example:
![Selection Sort Example](https://upload.wikimedia.org/wikipedia/commons/9/94/Selection-Sort-Animation.gif)

#### Implementation:
```python
def selection_sort(my_list):
    n = len(my_list)
    for i in range(n - 1):
        min_idx = i
        for j in range(i + 1, n):
            if my_list[j] < my_list[min_idx]:
                min_idx = j
        if min_idx != i:
            my_list[min_idx], my_list[i] = my_list[i], my_list[min_idx]
```

#### Features:
- **Time Complexity**: O(n²)
- **Space Complexity**: O(1)
- **Stability**: No (equal elements might not maintain their relative order)
- **Best Case**: O(n²) (there is no improvement even for sorted lists)

---

### 3. Insertion Sort

**Insertion Sort** works by dividing the list into a sorted and unsorted portion. It repeatedly takes an element from the unsorted portion and inserts it into the correct position within the sorted portion. This algorithm is efficient for small or nearly sorted datasets.

#### Algorithm Steps:
1. Start with the second element (consider the first element as sorted).
2. Store the current element in a temporary variable.
3. Compare the current element with elements in the sorted portion, moving larger elements one position to the right to create space.
4. Insert the current element into its correct position in the sorted portion.
4. Repeat for all elements in the unsorted portion until all elements are sorted.

#### Example:
![Insertion Sort Example](https://upload.wikimedia.org/wikipedia/commons/0/0f/Insertion-sort-example-300px.gif)

#### Implementation:
```python
def insertion_sort(my_list):
    for i in range(1, len(my_list)):
        curr = my_list[i]
        j = i
        while j > 0 and my_list[j - 1] > curr:
            my_list[j] = my_list[j - 1]
            j -= 1
        my_list[j] = curr
```

#### Features:
- **Time Complexity**: O(n²)
- **Space Complexity**: O(1)
- **Stability**: Yes (maintains the relative order of equal elements)
- **Best Case**: O(n) (for already sorted lists, the algorithm only compares elements, no shifts required)
