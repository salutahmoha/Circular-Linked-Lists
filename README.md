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

## Implementation of Circular Singly Linked List

### Diagram

Below is the structure of a Circular Singly Linked List:
Node 1 (head) -> Node 2 -> Node 3 -> Node 4 -> (back to head)


### Code

```javascript
class Node {
  constructor(data) {
    this.data = data;
    this.next = null;
  }
}

class CircularSinglyLinkedList {
  constructor() {
    this.head = null;
  }

  // Insert at the end
  insertAtEnd(data) {
    const newNode = new Node(data);
    if (!this.head) {
      this.head = newNode;
      newNode.next = this.head;
    } else {
      let temp = this.head;
      while (temp.next !== this.head) {
        temp = temp.next;
      }
      temp.next = newNode;
      newNode.next = this.head;
    }
  }

  // Delete a node by value
  deleteByValue(value) {
    if (!this.head) return;

    let current = this.head;
    let prev = null;

    // Find the node to delete
    do {
      if (current.data === value) {
        if (prev) {
          prev.next = current.next;
        } else {
          // Deleting the head node
          let temp = this.head;
          while (temp.next !== this.head) {
            temp = temp.next;
          }
          this.head = current.next;
          temp.next = this.head;
        }
        return;
      }
      prev = current;
      current = current.next;
    } while (current !== this.head);
  }

  // Traverse the list
  traverse() {
    if (!this.head) return;
    let temp = this.head;
    const result = [];
    do {
      result.push(temp.data);
      temp = temp.next;
    } while (temp !== this.head);
    console.log(result.join(" -> "));
  }
}

// Example Usage
const cll = new CircularSinglyLinkedList();

cll.insertAtEnd(10);
cll.insertAtEnd(20);
cll.insertAtEnd(30);
cll.traverse(); // Output: 10 -> 20 -> 30

cll.deleteByValue(20);
cll.traverse(); // Output: 10 -> 30
