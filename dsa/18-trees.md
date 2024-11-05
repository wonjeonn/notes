# Trees

A **tree** is a hierarchical data structure for efficiently organizing and classifying data. Trees reduce search overhead and are used widely in computing for their structured approach to data.

![trees](https://github.com/user-attachments/assets/09828a64-97c8-41d9-8e41-c37874eb9810)

### Tree Terminology
- **Node**: Each element or data holder in the tree.
- **Root Node**: The top node from which all other nodes descend. For example, `A` in a given tree.
- **Subtree**: A section of the tree with a specific root and all of its descendants. For example, node `B` and all nodes below it form a subtree.
- **Empty Tree**: A tree with no nodes.
- **Leaf Node**: A node with no children (e.g., `D`, `E`, `F`).
- **Children**: Nodes directly connected and one level below a parent node. For example, `B` is a child of `A`.
- **Parent**: A node directly above and connected to a given node. `A` is the parent of `B`.
- **Sibling**: Nodes sharing the same parent. For instance, `E` and `F` are siblings of `D`.
- **Ancestor**: Any node that can be reached by moving only upward from a given node. `A` is an ancestor of `I`.
- **Descendant**: Nodes that can be reached by moving downward from a given node. Descendants of `C` include `G`, `H`, `I`, and `J`.
- **Depth**: Distance from the root node. Root node has a depth of 0. B and C are at depth 1.
- **Height**: The length of the longest path from the root to a leaf. The height of a tree is the maximum depth. Example tree has a height of 4.
- **Path**: The sequence of nodes between an ancestor and a descendant.
- **Binary Tree**: A type of tree where each node has at most two children, designated as the left and right children.

### Tree Implementation
- **Node-Based (Linked)**: Each node contains data and pointers to its children, similar to a linked list. This structure is common for most tree types.
- **Array-Based**: Used in specific tree structures like binary heaps. In this case, the root is stored at index 0, and other elements' indices can be calculated based on position.
