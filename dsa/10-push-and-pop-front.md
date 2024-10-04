# Push Front and Pop Front Implementations

### Without Sentinel Nodes

**`push_front(data)`**

1. **Create a new node**: The new node is initialized with the specified data and its `next` pointer points to the current front.
2. **Check if the list is empty**: If the list is empty, set `back` to the new node.
3. **Update pointers**: If the list is not empty, update the current front's `prev` pointer to reference the new node.
4. **Update the front pointer**: Set the new node as the new front.

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

    def push_front(self, data):
        nn = self.Node(data, self.front)
        if self.front is None:
            self.back = nn
        else:
            self.front.prev = nn
        self.front = nn
```

**`pop_front()`**

1. **Check if the list is empty**: If it is, do nothing.
2. **Save the current front node**: Temporarily store the front node.
3. **Update the front pointer**: Move to the next node.
4. **Update the back pointer**: If the new front is `None`, set `back` to `None`.
5. **Update the new front's `prev` pointer**: Set it to `None` if there's a new front.
6. **Delete the temporary node**: Clean up the reference to the removed node.

**Python Implementation**
```python
    def pop_front(self):
        if self.front is not None:
            rm = self.front
            self.front = self.front.next
            if self.front is None:
                self.back = None
            else:
                self.front.prev = None
            del rm
```

### With Sentinel Nodes

**Sentinel Nodes**

Sentinel nodes are special nodes that simplify operations on the linked list by ensuring that the `front` and `back` pointers are never `None`. The linked list always maintains at least two nodes: a front sentinel and a back sentinel.

**Constructor with Sentinels**
```python
    def __init__(self):
        self.front = self.Node(None)  # Front sentinel
        self.back = self.Node(None, None, self.front)  # Back sentinel
        self.front.next = self.back  # Link front to back
```

**`push_front(data)` with Sentinels**

1. **Create a new node**: The new node points to the current first node (the one following the front sentinel).
2. **Update pointers**: Set the new node's `prev` pointer to the front sentinel.
3. **Adjust sentinel pointers**: Update the next pointer of the front sentinel to point to the new node, and update the previous pointer of the old first node to the new node.

**Python Implementation**
```python
    def push_front(self, data):
        nn = self.Node(data, self.front.next, self.front)
        self.front.next.prev = nn
        self.front.next = nn
```

**`pop_front()` with Sentinels**

1. **Check if the list is empty**: If the next pointer of the front sentinel points to the back sentinel, it means the list is empty.
2. **Save the node to be removed**: Retrieve the node that follows the front sentinel.
3. **Update sentinel pointers**: Adjust the front sentinel's next pointer and the new front node's previous pointer.
4. **Delete the temporary node**: Clean up the reference to the removed node.

**Python Implementation**
```python
    def pop_front(self):
        if self.front.next is not self.back:  # Check if there's any node
            rm = self.front.next  # Node to remove
            rm.next.prev = self.front  # Update the new front node's previous pointer
            self.front.next = rm.next  # Remove the node
            del rm
```
