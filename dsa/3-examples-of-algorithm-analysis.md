# Examples of Algorithm Analysis

## **Analysis of Linear Search**

### **Python Code**:
```python
def linear_search(my_list, key):
    for i in range(0, len(my_list)): 
        if my_list[i] == key:
            return i
    return -1
```

### **Assumptions**:
1. **Worst Case**: Key is not in the array. The search requires scanning the entire array.
2. **Best Case**: Key is at the beginning of the array. The search stops immediately.
3. **Average Case**: Key is equally likely to be in any position. On average, the search will look through half the array.

### **Worst Case Analysis (Unsuccessful Search)**:
- **Number of Operations**:
  - **Loop Iterations**: The loop runs **n** times (where **n** is the size of the array).
  - **Operations per Iteration**:
    - `for i in range(0, len(my_list))`: **n** operations (n iterations + 2 additional constant operations for checking range and incrementing `i`).
    - `if my_list[i] == key`: **n** operations (each iteration checks if the current element equals the key).
    - `return -1`: **1** operation (only executed when the key is not found).

- **Expression for Operations**:
  $$T(n) = n + 2 + n + 1 = 2n + 3$$

- **Big-O Notation**:
  - For large **n**, the constant term **+3** becomes less significant.
  - Therefore, **T(n)** is dominated by **2n**, and the complexity is **O(n)**.

### **Average Case Analysis**:
- On average, the search will find the key after checking half of the elements.
- **Number of Operations**:
  - **Average Iterations**: **n/2**
  - **Expression for Operations**:
    $$T(n) = n/2 + 2 + n/2 + 1 = n + 3$$

- **Big-O Notation**:
  - The dominating term is **n**, so the complexity is **O(n)**.

---

## **Analysis of Binary Search**

### **Python Code**:
```python
def binary_search(my_list, key):
    rc = -1
    low = 0
    high = len(my_list) - 1

    while rc == -1 and low <= high:
        mid = (low + high) // 2
        if key < my_list[mid]:
            high = mid - 1
        elif key > my_list[mid]:
            low = mid + 1
        else:
            rc = mid

    return rc
```

### **Assumptions**:
- The list must be sorted.
- The binary search algorithm halves the search space in each iteration.

### **Worst Case Analysis (Unsuccessful Search)**:
- **Number of Operations**:
  - Initial assignments:
    - `rc = -1`: **1**
    - `low = 0`: **1**
    - `high = len(my_list) - 1`: **3** (1 function call, 1 subtraction, 1 assignment)
  - Inside the loop:
    - `rc == -1 and low <= high`: **3 operations per iteration**
    - `mid = (low + high) // 2`: **3 operations per iteration**
    - `if key < my_list[mid]`: **1 operation**
    - `elif key > my_list[mid]`: **1 operation**
    - `high = mid - 1` or `low = mid + 1`: **2 operations**

- **Total Operations Per Iteration**: Approximately **10** operations (worst case).

- **Number of Iterations**:
  - Each iteration halves the number of elements to search.
  - Number of iterations: **log₂(n)** (where **n** is the size of the array).

- **Expression for Operations**:
  $$T(n) = 10 \cdot (1 + \log n) + 6 = 10\log n + 16$$

- **Big-O Notation**:
  - The dominating term is **10log(n)**.
  - Therefore, **T(n)** is **O(log n)**.

---

## **Analysis of Factorial Algorithm**

### **Python Code**:
```python
def factorial(n):
    rc = 1                  # 1
    for i in range(2, n+1): # (n-1) + 1 + 1
                                # (n-1) loop iterations
                                # 1 more for + operator
                                # 1 more for call to range function
        rc *= i             # 2 (n-1)
                                # 2 as there are two operators
                                # (n-1) as loop runs n-1 times
    return rc               # 1
```

### **Operations**:
- **Initialization**:
  - `rc = 1`: **1**
- **Loop**:
  - **Iterations**: **n - 1**
  - **Operations per Iteration**:
    - `rc *= i`: **2 operations per iteration**

- **Expression for Operations**:
  $$T(n) = 1 + (n - 1) + 1 + 1 + 2(n - 1) + 1 = 3n + 1$$

- **Big-O Notation**:
  - The dominating term is **3n**.
  - Therefore, **T(n)** is **O(n)**.

---

## **Steps for Algorithm Analysis**:

1. **Establish Variables & Functions**:
   - Define input size **n** and number of operations **T(n)**.

2. **Count Operations**:
   - Identify and count operations in each part of the code.

3. **Establish the Expression for T(n)**:
   - Sum the total operations to form an expression.

4. **Simplify the Expression**:
   - Combine terms and focus on the dominating term.

5. **State the Final Complexity**:
   - Use the dominating term to determine the Big-O notation.
