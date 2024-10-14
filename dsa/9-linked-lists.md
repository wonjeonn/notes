# Lists

A **list** is a **sequence of values** that maintains an order. The ordering of the data indicates positions (e.g., "first," "second," etc.). Lists can have properties like being sorted or unsorted, and they may contain duplicate values or be unique.
1. **Array-based Lists** – Elements are stored contiguously in memory.
2. **Linked Lists** – Elements (nodes) are scattered in memory but linked by pointers.

### Linked Lists
A **linked list** is a dynamic data structure where elements (or nodes) are connected by pointers. Each node contains two components.
- **Data** – The actual information stored.
- **Pointer** – A reference to the next node (and sometimes a reference to the previous node in the case of doubly linked lists).

#### Types of Linked Lists
1. **Singly Linked List** – Each node has a pointer to the next node.
2. **Doubly Linked List** – Each node has pointers to both the next and previous nodes.

#### Basic Operations on Linked Lists
- **push_front** – Add an item at the beginning.
- **push_back** – Add an item at the end.
- **pop_front** – Remove the first item.
- **pop_back** – Remove the last item.
- **insert** – Insert a node at a specific position.
- **erase** – Remove a node from a specific position.
- **traversal** – Apply a function to every node in the list.

### Comparison Between Array-Based Lists and Linked Lists

#### **Array-Based Lists**
- **Advantages**
  - **Random access**: Accessing any element is fast (`O(1)`) using an index.
  - **Binary search**: If sorted, array-based lists can use binary search for fast lookups (`O(log n)`).
- **Drawbacks**
  - **Memory waste**: Extra memory is allocated even if not all of it is used.
  - **Costly insertions and deletions**: Inserting or removing elements, especially in the middle of the list, requires shifting elements, leading to a time complexity of (`O(n)`).

#### **Linked Lists**
- **Advantages**
  - **Dynamic size**: Memory is only used when nodes are created, so no space is wasted.
  - **Efficient insertions/deletions**: Inserting or removing a node (if its position is known) is done in constant time (`O(1)`).
- **Drawbacks**
  - **No random access**: Traversal from the beginning of the list is required to access a node, resulting in a linear time complexity (`O(n)`).
  - **Extra memory for pointers**: Each node requires storage for one or more pointers in addition to the actual data.

### Memory Considerations
- **Array-Based Lists**: Pre-allocate more space than needed to avoid resizing, but resizing is expensive.
- **Linked Lists**: Memory usage is more efficient until the array is nearly full. However, each node in a linked list carries additional overhead from storing pointers.

### Iterators
An **iterator** is an abstraction that allows you to traverse a container like a list without exposing its underlying implementation.
- **first**: Access the first item.
- **next**: Move to the next item.
- **isDone**: Check if the traversal is complete.
- **currentItem**: Access the current item.

In linked lists, iterators provide a consistent interface for accessing elements, allowing the structure of the list to be hidden from the user.

### Implementation Considerations:
- **Node Structure**: In a linked list, a node contains the data and pointers to other nodes. In a doubly linked list, two pointers (to the next and previous nodes) are necessary.

**Python Implementation**
```python
class LinkedList:
    class Node:
        def __init__(self, data, next=None, prev=None):
            self.data = data
            self.next = next
            self.prev = prev

    def __init__(self):
        self.front = None
        self.back = None
```
