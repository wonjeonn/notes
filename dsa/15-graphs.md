# Graph Definition

A **graph** $G = (V, E)$ consists of:

- **Vertices (V)**: The nodes or points, representing objects or entities in a dataset.
- **Edges (E)**: The connections or relationships between pairs of vertices, denoted as $(u, v)$, where $u$ and $v$ are vertices in $V$. These edges may be directed (pointing from one vertex to another) or undirected (a two-way connection).

### Applications of Graphs

Graphs are widely used to model relationships and connections in various fields, such as:

- **Flight routes** between cities, where cities are vertices, and flights between them are directed edges.
- **Social media networks**, where people or accounts are vertices, and connections (like followers) are directed edges.

### Vertices and Edges

- **Vertices**: Represent individual objects, such as cities in a network of flights. Each vertex can be identified by a label (like A, B, C) or an identifier (often a number).

  ![vertices](https://github.com/user-attachments/assets/b33cc7ac-c030-4f6a-b8a6-4c57199f1149)
- **Edges**: Represent relationships between vertices and can have:
  - **Weights**: These can convey additional information, such as the distance between cities or the strength of a connection.
    ![edges-weights](https://github.com/user-attachments/assets/552d54f6-3905-4d87-9cda-7a92053a409e)
  - **Direction**: Directed edges indicate a one-way relationship, making the graph a _digraph_.
    ![edges-weights-directions](https://github.com/user-attachments/assets/7ea5bfc0-ba49-4e2d-a2ca-eee7ca551098)

### Additional Terminology

- **Adjacent**: If there is a direct edge from vertex A to vertex B, then B is adjacent to A.
- **Edge Weight/Cost**: A numerical value associated with an edge, such as the distance or capacity of a connection.
- **Path**: An ordered sequence of vertices connected by edges.
- **Simple Path**: A path where each vertex is unique, without repetitions.
- **Path Length**: The number of edges in a path.
- **Cycle**: A path that begins and ends at the same vertex.
- **Strongly Connected**: In a directed graph, the graph is strongly connected if there’s a path between every pair of vertices.
- **Weakly Connected**: If direction is ignored and every pair of vertices is reachable, the graph is weakly connected.

### Graph Representations

Two common methods for storing graphs are **Adjacency Matrix** and **Adjacency List**:

#### Adjacency Matrix

- **Structure**: A 2D array where each cell at position $(i, j)$ represents an edge from vertex $i$ to vertex $j$. For unweighted graphs, a 1 indicates an edge exists, and a 0 means no connection. For weighted graphs, the cell contains the weight of the edge.
- **Efficiency**: Suitable for dense graphs, where there are many edges. Checking if two vertices are connected takes constant time $O(1)$.
- **Example**:
  ```
       A B C D E F G
    A [0 2 0 0 0 0 0]
    B [0 0 0 0 4 0 0]
    C [3 0 0 0 0 0 0]
    D [0 0 1 0 0 0 0]
    E [0 0 0 2 0 4 0]
    F [0 0 0 0 3 0 1]
    G [0 5 0 0 0 0 0]
  ```

#### Adjacency List

- **Structure**: An array (or dictionary) of linked lists. Each vertex has a list of connected vertices, making it efficient to traverse neighbors. For weighted graphs, each connection in the list includes the weight.
- **Efficiency**: Suitable for sparse graphs, where most pairs of vertices are not connected. However, checking if two vertices are connected takes longer since the list for the first vertex must be searched.
- **Example**:
  ```
    A -> [(B, 2)]
    B -> [(E, 4)]
    C -> [(A, 3)]
    D -> [(C, 1)]
    E -> [(D, 2), (F, 4)]
    F -> [(E, 3), (G, 1)]
    G -> [(B, 5)]
  ```

### Examples

#### A graph with no weights or directions
![graph-no-weights-no-directions](https://github.com/user-attachments/assets/5b232752-7dcc-470f-bb0a-acff849b56de)

#### A graph with weights but no directions
![graph-weights-no-directions](https://github.com/user-attachments/assets/6a0c15d0-0ca8-4ceb-be66-130fa98ef646)

#### A graph with weights and directions
![graph-weights-directions](https://github.com/user-attachments/assets/c778c9e1-9209-46f6-9674-353e64a59234)
