# Dijkstra's Algorithm

Dijkstra's Algorithm is an algorithm for finding the shortest path to all other vertices in a weighted graph.

![Dijkstra's Algorithm Example](https://upload.wikimedia.org/wikipedia/commons/5/57/Dijkstra_Animation.gif)

- Dijkstra's Algorithm is an example of s a *greedy* approach, expanding the path from the nearest known vertex to unvisited vertices.
- The graph must have non-negative weights on its edges for the algorithm to function correctly.

---

### **Algorithm Steps**

1. **Initialize**:
   - Set the distance of the starting vertex to zero, while all other vertices' distances are set to infinity.
   - Track each vertex's "previous" vertex in the path to facilitate reconstruction of the shortest path later.

2. **Expand from the Starting Vertex**:
   - Select the vertex with the smallest tentative distance (initially, this will be the starting vertex).
   - Update the distances for each neighboring vertex. If the new distance to a neighbor is smaller than its current known distance, update it.

3. **Mark as Known**:
   - Once a vertex is fully expanded (i.e., all its neighbors have been checked), mark it as "known," indicating that the shortest path to this vertex from the starting vertex has been found.
   - Repeat this process by selecting the next closest "unknown" vertex until all vertices have been processed.

4. **Path Reconstruction**:
   - To determine the actual path to a vertex, trace backward using the “previous vertex” table.

---

### **Example Walkthrough**

Consider a simple graph where the shortest path from vertex **A** to every other vertex is determined. The graph has edges with the following distances:

![non-directed-graph](https://github.com/user-attachments/assets/d794e793-e20f-45ca-a926-1c3c1ee5d020)

- **A** ↔ **B** with a weight of 7
- **A** ↔ **E** with a weight of 3
- **E** ↔ **B** with a weight of 1
- **E** ↔ **D** with a weight of 2
- **B** ↔ **D** with a weight of 2
- **B** ↔ **C** with a weight of 6
- **D** ↔ **C** with a weight of 4

#### Initial Table Setup

| Vertex | Shortest Distance from A | Previous Vertex | Known  |
|--------|---------------------------|-----------------|--------|
| **A**  | 0                         | -               | false  |
| **B**  | ∞                         | -               | false  |
| **C**  | ∞                         | -               | false  |
| **D**  | ∞                         | -               | false  |
| **E**  | ∞                         | -               | false  |

#### Step-by-Step Expansion

1. **Expand from A**:
   - Update distances for **B** (7) and **E** (3).
   - Mark **A** as known.

   Updated Table:

   | Vertex | Shortest Distance from A | Previous Vertex | Known  |
   |--------|---------------------------|-----------------|--------|
   | **A**  | 0                         | -               | true   |
   | **B**  | 7                         | A               | false  |
   | **C**  | ∞                         | -               | false  |
   | **D**  | ∞                         | -               | false  |
   | **E**  | 3                         | A               | false  |

2. **Expand from E** (smallest known distance, 3):
   - Update **B** to 4 (3 + 1) and **D** to 5 (3 + 2).
   - Mark **E** as known.

   Updated Table:

   | Vertex | Shortest Distance from A | Previous Vertex | Known  |
   |--------|---------------------------|-----------------|--------|
   | **A**  | 0                         | -               | true   |
   | **B**  | 4                         | E               | false  |
   | **C**  | ∞                         | -               | false  |
   | **D**  | 5                         | E               | false  |
   | **E**  | 3                         | A               | true   |

3. **Expand from B**:
   - Update **C** to 10 (4 + 6) and **D** to 6 (4 + 2). Since **D**’s current shortest distance (5) is less, no update is made.
   - Mark **B** as known.

   Updated Table:

   | Vertex | Shortest Distance from A | Previous Vertex | Known  |
   |--------|---------------------------|-----------------|--------|
   | **A**  | 0                         | -               | true   |
   | **B**  | 4                         | E               | true   |
   | **C**  | 10                        | B               | false  |
   | **D**  | 5                         | E               | false  |
   | **E**  | 3                         | A               | true   |

4. **Expand from D**:
   - Update **C** to 9 (5 + 4).
   - Mark **D** as known.

   Updated Table:

   | Vertex | Shortest Distance from A | Previous Vertex | Known  |
   |--------|---------------------------|-----------------|--------|
   | **A**  | 0                         | -               | true   |
   | **B**  | 4                         | E               | true   |
   | **C**  | 9                         | D               | false  |
   | **D**  | 5                         | E               | true   |
   | **E**  | 3                         | A               | true   |

5. **Expand from C**:
   - No updates are needed as there are no unvisited neighbors.
   - Mark **C** as known, completing the algorithm.

   Final Table:

   | Vertex | Shortest Distance from A | Previous Vertex | Known  |
   |--------|---------------------------|-----------------|--------|
   | **A**  | 0                         | -               | true   |
   | **B**  | 4                         | E               | true   |
   | **C**  | 9                         | D               | true   |
   | **D**  | 5                         | E               | true   |
   | **E**  | 3                         | A               | true   |

---

### **Reconstructing the Shortest Path**
To determine the shortest path from **A** to **C**:
   - Start at **C**, which points back to **D**.
   - **D** points back to **E**, and **E** points back to **A**.
   - Thus, the path from **A** to **C** is **A → E → D → C** with a total distance of 9.
