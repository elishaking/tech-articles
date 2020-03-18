# What is a Linked List

A **linked list** is a data structure that stores a collection of nodes. Each node in the linked list contains data and two **pointers**. In simple terms, a pointer is a variable that contains the address of some object in memory.

![Doubly Linked List](https://github.com/elishaking/tech-articles/blob/master/doubly%20linked%20lists.png?raw=true)

In a **doubly linked list**, each node contains two pointers. This first pointer holds the memory address of the previous node while the second pointer holds the memory address of the next node in the list.

### Time Complexity (Big O)

One great benefit of doubly linked list is the fact that it enables the insertion of new nodes to beginning and end of the list in constant time - O(1).

In contrast, a typical array will produce a linear time complexity - O(n) - when inserting to the beginning because the addresses of all the succeeding elements in the array needs to be shifted by 1. This can quickly become inefficient as the array grows in size.

This unique contant time complexity makes doubly linked lists a good candidate for the implementation of **Queues**.

```javascript
class ListNode {
  constructor(data) {
    this.data = data;
    this.prev = null;
    this.next = null;
  }
}

class DoublyLinkedList {
  constructor() {
    this.size = 0;
    this.head = null;
    this.tail = null;
  }

  /**
   * Add node to the end of the list
   *
   * Time complexity: O(1)
   * @param {any} data
   */
  push(data) {
    const newNode = new ListNode(data);

    if (this.size === 0) {
      this.head = newNode;
      this.tail = newNode;
    } else {
      this.tail.next = newNode;

      newNode.prev = this.tail;

      this.tail = newNode;
    }

    this.size++;

    return newNode;
  }

  /**
   * Remove node from the beginning of the list
   *
   * Time complexity: O(1)
   */
  shift() {
    if (this.size === 0) {
      return null;
    }

    const nodeToRemove = this.head;

    if (this.size === 1) {
      this.head = null;
      this.tail = null;
    } else {
      this.head = nodeToRemove.next;

      this.head.prev = null;
      nodeToRemove.next = null;
    }

    this.size--;

    return nodeToRemove;
  }

  /**
   * Return list items
   */
  toString() {
    const list = [];
    let currentNode = this.head;

    while (currentNode !== null) {
      list.push(JSON.stringify(currentNode.data));
      currentNode = currentNode.next;
    }

    return list.toString();
  }
}
```

There are more methods that can be added to the `DoublyLinkedList` class but we only need `push` and `shift` to implement the basic **queue operations** as explained below.

# What is a Queue

A **queue** is a collection of items that supports only two operations: the **add or enqueue** operation and the **remove or dequeue** operation.

A typical implementation for a queue will involve the storage of the queue items in an **array**. This is not a great solution because the dequeue operation requires the removal of the first element in the **array** which is linear time operation. In this case, a doubly linked list is a great alternative for storing the queue items and enabling both enqueue and dequeue to be performed in constant time.

```javascript
class Queue {
  constructor() {
    this._items = new DoublyLinkedList();
  }

  /**
   * Add an item to the queue
   *
   * Time complexity: O(1)
   * @param {any} newItem
   */
  enqueue(newItem) {
    return this._items.push(newItem);
  }

  /**
   * Remove an item from the queue
   *
   * Time complexity: O(1)
   */
  dequeue() {
    return this._items.shift();
  }

  /**
   * Return number of items in the queue
   */
  size() {
    return this._items.size;
  }

  /**
   * Return Queue items
   */
  toString() {
    return `Queue {
      size: ${this.size()}
      _items: [${this._items.toString()}]
    }`;
  }
}
```
