# Algorithm Analysis
- **Objective**: Analyze resource consumption (time and memory) of a program based on input size.
- **Key Resources**:
  - **Time**: How long the algorithm takes to execute.
  - **Memory**: The amount of storage needed to run the algorithm.
- **Trade-offs**: Sometimes an algorithm that consumes less time may require more memory, and vice versa.

---

### **Measuring Resource Consumption**
- **Time Resource**: Measured by the number of operations performed by the program. Assumes each operation takes equal time.
- **Memory Resource**: Measured based on how much space (memory) is used, such as variables or dynamic memory allocation.

---

### **Growth Rates of Common Functions**
Growth rates describe how resource consumption scales with data size.

1. **Constant Growth (O(1))**: 
   - **Curve**: Horizontal line (y = 1).
   - **Example**: Accessing a specific element in an array (e.g., push and pop in a stack).
   - **Growth**: No growth, regardless of data size.

2. **Logarithmic Growth (O(log n))**: 
   - **Curve**: Flattens out as data size increases (y = log(n)).
   - **Example**: Binary search, tree operations.
   - **Growth**: Grows slower as data size increases, making it efficient for large datasets.

3. **Linear Growth (O(n))**: 
   - **Curve**: Straight line (y = n).
   - **Example**: A single for loop.
   - **Growth**: Directly proportional to the size of the data.

4. **Loglinear Growth (O(n log n))**: 
   - **Curve**: Slight curve (y = n log n).
   - **Example**: Sorting algorithms (e.g., Merge Sort, Quick Sort, Heap Sort).
   - **Growth**: More than linear but better than quadratic.

5. **Quadratic Growth (O(n²))**: 
   - **Curve**: Parabola-shaped (y = n²).
   - **Example**: Nested loops, Insertion Sort, Bubble Sort, Selection Sort.
   - **Growth**: Resource needs grow exponentially with input size.

6. **Cubic Growth (O(n³))**: 
   - **Curve**: Steeper parabola (y = n³).
   - **Example**: Triple nested loops.
   - **Growth**: Consumes resources very quickly.

7. **Exponential Growth (O(2ⁿ))**: 
   - **Curve**: Shoots up rapidly (y = 2ⁿ).
   - **Example**: Brute-force algorithms (e.g., Fibonacci Sequence).
   - **Growth**: Resource needs double with each additional data point, highly inefficient.

---

### **Asymptotic Notation**
Asymptotic notation is used to describe the efficiency of an algorithm by its upper and lower resource bounds.

1. **Big-O Notation (O(f(n)))**: 
   - Upper bound for resource consumption.
   - Example: O(n), O(n²).

2. **Omega Notation (Ω(f(n)))**: 
   - Lower bound for resource consumption.
   - Example: Ω(n), Ω(log n).

3. **Theta Notation (Θ(f(n)))**: 
   - Exact bound (both upper and lower) for resource consumption.
   - Example: Θ(n log n).

4. **Little-O Notation (o(f(n)))**: 
   - Upper bound, but not tight (doesn't reach f(n)).
   - Example: o(n²).

---

### **Formal Definitions**:

1. **Big-O (O)**:  
   - *T(n) is O(f(n))* iff there exist constants **c** and **n₀** such that T(n) ≤ c × f(n) for all n ≥ n₀.
   
2. **Omega (Ω)**:  
   - *T(n) is Ω(f(n))* iff there exist constants **c** and **n₀** such that T(n) ≥ c × f(n) for all n ≥ n₀.

3. **Theta (Θ)**:  
   - *T(n) is Θ(f(n))* iff T(n) is both O(f(n)) and Ω(f(n)).

4. **Little-o (o)**:  
   - *T(n) is o(f(n))* iff T(n) is O(f(n)) but not Θ(f(n)).

---

### **Worst, Best, and Average Cases**
- **Worst Case**: Maximum resource consumption in the worst scenario.
- **Best Case**: Minimum resource consumption in the best scenario.
- **Average Case**: Expected resource consumption across various possible inputs.

---

### **Understanding Asymptotic Notation in Practice**
- **T(n) is O(f(n))**: T(n) represents the actual resource consumption, while f(n) is an upper bound (e.g., O(n²)).
- **Constants c and n₀**: Constants **c** and **n₀** are used to describe when T(n) will be below the curve of cf(n).
- **Relaxing Exactness**: Asymptotic notation doesn't provide an exact measure, but rather a general description of resource consumption trends as data size grows.

---

### **Rankings from Most Efficient to Least Efficient**
![Big-O Complexity Chart](https://miro.medium.com/v2/resize:fit:1276/format:webp/0*pf4IeOADaqtJGsz7.jpeg)

1. **O(1)** → Constant
2. **O(log n)** → Logarithmic
3. **O(n)** → Linear
4. **O(n log n)** → Loglinear
5. **O(n²)** → Quadratic
6. **O(n³)** → Cubic
7. **O(2ⁿ)** → Exponential
