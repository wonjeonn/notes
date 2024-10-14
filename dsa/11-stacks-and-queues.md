# Stacks and Queues

- **Stacks** utilize the **LIFO** structure, whereas **queues** employ the **FIFO** structure.
- Both data structures can be implemented using either arrays or linked lists.

## Stacks

A **stack** is a data structure that follows the Last In, First Out (LIFO) principle. Items are added and removed from the top of the stack, resembling a stack of trays where only the top tray can be accessed.

### Operations
- **Push**: Add an item to the top of the stack.
- **Pop**: Remove and return the top item.
- **Top**: Access the item at the top without removing it.
- **isEmpty**: Check if the stack is empty.

### Array Implementation
```python
class ArrayStack:
    def __init__(self):
        self.stack = []
    
    def push(self, item):
        self.stack.append(item)  # Add item to the end (top of the stack)
    
    def pop(self):
        if not self.isEmpty():
            return self.stack.pop()  # Remove and return the last item (top of the stack)
        else:
            raise IndexError("Pop from an empty stack")
    
    def top(self):
        if not self.isEmpty():
            return self.stack[-1]  # Return the last item without removing it
        else:
            raise IndexError("Top from an empty stack")
    
    def isEmpty(self):
        return len(self.stack) == 0

# Example usage
stack = ArrayStack()
stack.push(1)
stack.push(2)
print(stack.top())  # Output: 2
print(stack.pop())  # Output: 2
print(stack.isEmpty())  # Output: False
```

### Linked List Implementation
A stack can also be implemented using a linked list.

```python
class Node:
    def __init__(self, value):
        self.value = value
        self.next = None

class LinkedListStack:
    def __init__(self):
        self.top_node = None
    
    def push(self, item):
        new_node = Node(item)
        new_node.next = self.top_node  # Point to the previous top node
        self.top_node = new_node  # Update the top node to the new node
    
    def pop(self):
        if self.isEmpty():
            raise IndexError("Pop from an empty stack")
        popped_value = self.top_node.value
        self.top_node = self.top_node.next  # Move the top node pointer to the next node
        return popped_value
    
    def top(self):
        if self.isEmpty():
            raise IndexError("Top from an empty stack")
        return self.top_node.value
    
    def isEmpty(self):
        return self.top_node is None

# Example usage
stack = LinkedListStack()
stack.push(1)
stack.push(2)
print(stack.top())  # Output: 2
print(stack.pop())  # Output: 2
print(stack.isEmpty())  # Output: False
```

---

## Queues

A **queue** is a data structure that follows the First In, First Out (FIFO) principle. Items are added to the back and removed from the front, similar to a line of people waiting for service.

### Operations
- **Enqueue**: Add an item to the back of the queue.
- **Dequeue**: Remove and return the front item.
- **Front**: Access the front item without removing it.
- **isEmpty**: Check if the queue is empty.

### Array Implementation
```python
class ArrayQueue:
    def __init__(self, capacity=10):
        self.queue = [None] * capacity
        self.front = 0
        self.back = 0
        self.size = 0
    
    def enqueue(self, item):
        if self.size == len(self.queue):
            raise IndexError("Enqueue on a full queue")
        self.queue[self.back] = item
        self.back = (self.back + 1) % len(self.queue)  # Circular increment
        self.size += 1
    
    def dequeue(self):
        if self.isEmpty():
            raise IndexError("Dequeue from an empty queue")
        item = self.queue[self.front]
        self.front = (self.front + 1) % len(self.queue)  # Circular increment
        self.size -= 1
        return item
    
    def front_item(self):
        if self.isEmpty():
            raise IndexError("Front from an empty queue")
        return self.queue[self.front]
    
    def isEmpty(self):
        return self.size == 0

# Example usage
queue = ArrayQueue()
queue.enqueue(1)
queue.enqueue(2)
print(queue.front_item())  # Output: 1
print(queue.dequeue())  # Output: 1
print(queue.isEmpty())  # Output: False
```

### Linked List Implementation
A queue can also be implemented using a linked list.

```python
class LinkedListNode:
    def __init__(self, value):
        self.value = value
        self.next = None

class LinkedListQueue:
    def __init__(self):
        self.front_node = None
        self.back_node = None
    
    def enqueue(self, item):
        new_node = LinkedListNode(item)
        if self.isEmpty():
            self.front_node = self.back_node = new_node  # First node in the queue
        else:
            self.back_node.next = new_node  # Link new node at the back
            self.back_node = new_node  # Update back node pointer
    
    def dequeue(self):
        if self.isEmpty():
            raise IndexError("Dequeue from an empty queue")
        dequeued_value = self.front_node.value
        self.front_node = self.front_node.next  # Move the front pointer to the next node
        if self.front_node is None:
            self.back_node = None  # If queue becomes empty, update back pointer
        return dequeued_value
    
    def front_item(self):
        if self.isEmpty():
            raise IndexError("Front from an empty queue")
        return self.front_node.value
    
    def isEmpty(self):
        return self.front_node is None

# Example usage
queue = LinkedListQueue()
queue.enqueue(1)
queue.enqueue(2)
print(queue.front_item())  # Output: 1
print(queue.dequeue())  # Output: 1
print(queue.isEmpty())  # Output: False
```
