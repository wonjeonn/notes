# Recursion

**Recursion** is a programming technique where a function calls itself to solve smaller instances of the same problem. It's particularly useful for algorithms involving structures like trees and graphs.

### The Run-time Stack
The run-time stack is a data structure that tracks function calls and their local variables. 

- Each function call adds a new stack frame on top.
- Each frame contains the function’s parameters and local variables.
- When a function returns, its frame is removed from the stack, and control goes back to the previous function.

### Writing Recursive Functions
1. **Base Case**: The simplest instance of the problem that can be solved directly. For example, in the factorial function, $0! = 1$ and $1! = 1$.
2. **Recursive Case**: The formulation of the problem in terms of itself. For factorial, $n! = n × (n-1)!$.

### Example: Factorial Function
The factorial of a number n, denoted as n!, is the product of all positive integers less than or equal to n. By definition, $0! = 1$.

```c
unsigned int factorial(unsigned int n) {
    unsigned int rc = 1;           // Base case result
    if (n > 1) {                   // Recursive case
        rc = n * factorial(n - 1); // rc is n * (n - 1)!
    }
    return rc;
}
```

### Stack Trace for `factorial(4)`
1. **Start**: `main()` is on the stack with local variable `x`.
2. **Call**: `factorial(4)` is pushed onto the stack (calls `factorial(3)`, down to `factorial(1)`).
3. **Base Case**: `factorial(1)` returns `1`.
4. **Return**:
   - From `factorial(2)`: computes $rc = 2 × 1 = 2$.
   - From `factorial(3)`: computes $rc = 3 × 2 = 6$.
   - From `factorial(4)`: computes $rc = 4 × 6 = 24$.
5. **End**: Final result `24`, stack pops back to `main()`.

### Analysis of a Recursive Function
- Let $n$ be the number for which the factorial is calculated.
- Let $T(n)$ represent the number of operations required to compute n!.

Counting operations:
- For $n = 0$ or $n = 1$: $T(0) = 3$, $T(1) = 3$.
- For $n ≥ 2$: $T(n) = 6 + T(n-1)$.

  The 6 accounts for:
  - 1 operation for initializing `rc`.
  - 1 operation for the `if` condition.
  - 1 operation for the `return`.
  - 3 operations for the multiplication and function call.

### Recursive Formula Solution
To derive $T(n)$:
1. Start with:
   $$T(n) = 6 + T(n-1)$$
2. Substitute repeatedly until reaching the base case:
   $$T(n) = 6 + (6 + T(n-2)) = 6 + 6 + (6 + T(n-3)) = ... = 6(n-1) + 3$$
3. Thus, the overall complexity is:
   $$T(n) = 6n - 3$$
   This indicates that $T(n)$ is $O(n)$.

### Drawbacks of Recursion
- **Performance**: Recursive functions can incur overhead due to multiple function calls, making them slower than iterative solutions.
- **Stack Space**: Excessive recursion can lead to stack overflow if the depth of recursion is too great.

### When to Use Recursion
- The problem is **naturally recursive** (can be defined in terms of itself).
- A straightforward iterative solution is not available or is complex.
