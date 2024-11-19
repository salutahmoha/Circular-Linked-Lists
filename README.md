# Circular Linked List (CLL)

## What is a Circular Linked List?

A **Circular Linked List** is a type of linked list where the last node points back to the first node, forming a circular chain. It can either be:
- **Singly Circular Linked List**: Each node has a single pointer pointing to the next node.
- **Doubly Circular Linked List**: Each node has two pointers: one pointing to the next node and the other to the previous node.

---
## Key Characteristics of Circular Linked Lists

1. **Circular Nature**:
   - The last node's pointer is not `null`; it points to the first node.

2. **Traversal**:
   - You can traverse the list indefinitely because it forms a loop.

3. **Efficient Operations**:
   - Allows insertion or deletion at the beginning, end, or any position efficiently by maintaining the circular structure.

4. **Flexible Starting Point**:
   - You can start traversal from any node and eventually return to the starting node.

---
