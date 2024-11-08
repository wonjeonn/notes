# Minimum Spanning Trees (MST)

A **spanning tree** of a graph $G = (V, E)$ is a connected, acyclic subgraph that includes all vertices in $V$. For graphs that are not connected, this concept generalizes to a **spanning forest**.

A **minimum spanning tree (MST)** of a graph $G = (V, E)$, with a weight function $w(e)$ for each $e \in E$, is a spanning tree with the smallest possible total weight.

---

## Methods to Find a Minimum Spanning Tree

To find an MST, there are two main approaches:

1. **Edge Removal**: Start with all edges in the graph and remove edges with the highest weights, provided that this does not disconnect any vertex. This approach is inefficient. For a graph with $n$ nodes, a spanning tree has $n - 1$ edges, while there may be up to $\frac{n(n - 1)}{2}$ edges, leading to poor performance.

2. **Edge Addition (Greedy Approach)**: Start with an empty set of edges and add edges one at a time until a spanning tree forms. This is done as follows:

    ```python
    greedyMST(G=(V, E)):
        T = []  # empty set of edges
        while(T is not an MST):
            find an edge e from E that is safe for T
            add e to T
    ```

An edge $e$ is **safe** for $T$ if adding $e$ makes $T$ a subset of some MST of $G$. This relies on the following theorem:

**Theorem**: If $G$ is a connected, undirected weighted graph, $T$ is a subset of some MST of $G$, and $e$ is any edge of minimum weight connecting different connected components of $T$, then adding $e$ is safe for $T$.

---

## Kruskal's Algorithm

**Kruskal's Algorithm** finds the MST by sorting edges according to weights and adding edges to $T$ if they connect different components. To quickly check connected components, a **disjoint set** (union-find) is used.

```python
KruskalsMST(G=(V, E)):
    T = []  # initially empty MST set
    sort edges in E by weight

    # create a set for each vertex
    for each vertex v in V:
        makeSet(v)

    for each edge e = (u, v) in E:
        ep1 = findSet(u)
        ep2 = findSet(v)

        if ep1 != ep2:
            union(ep1, ep2)
            add e to T
```

### Example Graph

![graph](https://github.com/user-attachments/assets/96766d97-975c-4306-99c4-1e5b113c0af8)

Given a graph, assume the edges sorted in non-descending order by weight are: $(C, D), (F, G), (A, B), (D, E), (A, C), (B, E), (E, F), (B, G)$.

**Step-by-Step Execution:**

| Step | MST $T$ | Disjoint Sets                | Comments                                                                                       |
|------|-------------|------------------------------|------------------------------------------------------------------------------------------------|
| 0    | $T = \emptyset$     | $\{A\}, \{B\}, \{C\}, \{D\}, \{E\}, \{F\}, \{G\}$ | Initially, each vertex is in its own set.                                                      |
| 1    | $T = \{(C, D)\}$    | $\{A\}, \{B\}, \{CD\}, \{E\}, \{F\}, \{G\}$       | Add $(C, D)$; $C$ and $D$ were in different sets.                                  |
| 2    | $T = \{(C, D), (F, G)\}$ | $\{A\}, \{B\}, \{CD\}, \{E\}, \{FG\}$            | Add $(F, G)$; $F$ and $G$ were in different sets.                                  |
| 3    | $T = \{(C, D), (F, G), (A, B)\}$ | $\{AB\}, \{CD\}, \{E\}, \{FG\}$                 | Add $(A, B)$; $A$ and $B$ were in different sets.                                  |
| 4    | $T = \{(C, D), (F, G), (A, B), (D, E)\}$ | $\{AB\}, \{CDE\}, \{FG\}$                      | Add $(D, E)$; $D$ and $E$ were in different sets.                                  |
| 5    | $T = \{(C, D), (F, G), (A, B), (D, E), (A, C)\}$ | $\{ABCDE\}, \{FG\}$              | Add $(A, C)$; $A$ and $C$ were in different sets.                                  |
| 6    | $T = \{(C, D), (F, G), (A, B), (D, E), (A, C)\}$ | $\{ABCDEFG\}$                      | Skip $(B, E)$ since $B$ and $E$ are in the same set. Final MST found.                |

### Kruskal's Algorithm Example
![Kruskal's Algorithm Example](https://he-s3.s3.amazonaws.com/media/uploads/6322896.jpg)

---

## Prim's Algorithm

In **Prim's Algorithm**, a root vertex is chosen, and the MST grows by repeatedly adding the smallest edge that connects an isolated vertex to the MST. This process uses a **MinHeap** to store and retrieve the smallest edge quickly.

**Execution Steps:**

| Step | MST $T$                  | MinHeap                           | Comments                                                                                |
|------|------------------------------|-----------------------------------|------------------------------------------------------------------------------------------|
| 0    | $T = \emptyset$          | $(A, \text{NIL}, 0), (B, \text{NIL}, -), \ldots, (G, \text{NIL}, -)$ | Initial state, with $A$ as the root.                                                |
| 1    | $T = \{(A, B)\}$         | $(C, A, 3), (E, B, 4), (G, B, 5)$ | Added $(A, B)$; updated weights and parents of neighbors $E, G$.                |
| 2    | $T = \{(A, B), (A, C)\}$ | $(D, C, 1), (E, B, 4), (G, B, 5)$ | Added $(A, C)$; updated weights and parent of $D$.                              |
| 3    | $T = \{(A, B), (A, C), (C, D)\}$ | $(E, D, 2), (G, B, 5)$  | Added $(C, D)$; updated weights and parent of $E$, as it is closer via $D$. |
| 4    | $T = \{(A, B), (A, C), (C, D), (D, E)\}$ | $(F, E, 4), (G, B, 5)$ | Added $(D, E)$; updated weight and parent of $F$.                               |
| 5    | $T = \{(A, B), (A, C), (C, D), (D, E), (E, F)\}$ | $(G, F, 1)$            | Added $(E, F)$; updated weight and parent of $G$ via $F$.                   |
| 6    | $T = \{(A, B), (A, C), (C, D), (D, E), (E, F), (F, G)\}$ | empty                  | Final MST obtained by adding $(F, G)$.                                              |

Kruskal’s and Prim’s algorithms both find Minimum Spanning Trees (MST), but they differ in approach and efficiency based on graph type.

### Prim's Algorithm Example
![Prim's Algorithm Example](https://he-s3.s3.amazonaws.com/media/uploads/16597fe.jpg)

---

### Summary

1. **Algorithm Type**:
   - **Kruskal’s**: Edge-focused. It sorts edges by weight and adds the smallest available edge, connecting separate components until all vertices are included without forming cycles.
   - **Prim’s**: Vertex-focused. It starts from one vertex and expands the tree by selecting the lowest-weight edge connecting a new vertex.

2. **Graph Structure**:
   - **Kruskal’s**: Best for sparse graphs, as it considers all edges, adding them only if they connect disjoint components.
   - **Prim’s**: Ideal for dense graphs, as it only considers edges adjacent to the growing MST.

3. **Data Structures**:
   - **Kruskal’s**: Uses a **disjoint set** to avoid cycles efficiently.
   - **Prim’s**: Uses a **min-heap** to quickly find the next smallest edge connected to the MST.

4. **Time Complexity**:
   - **Kruskal’s**: $O(E \log E)$, efficient with fewer edges.
   - **Prim’s**: $O(E + V \log V)$, often faster with more edges.
