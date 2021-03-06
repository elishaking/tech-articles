# What is a Linked List

A **linked list** is a data structure that stores a collection of nodes. Each node in a **doubly linked list** contains data and two **pointers**. In simple terms, a pointer is a variable that contains the address of some other object in memory.

![Doubly Linked List](https://github.com/elishaking/tech-articles/blob/master/doubly%20linked%20lists.png?raw=true)

This first pointer in the **doubly linked list** holds the memory address of the previous node while the second pointer holds the memory address of the next node in the list.

### Time Complexity (Big O)

One great benefit of a **doubly linked list** is the fact that it enables the insertion of new nodes to the beginning and end of the list in constant time - **O(1)**.

In contrast, a typical array will produce a linear time complexity - **O(n)** - when inserting to the beginning because the addresses of all the succeeding items in the array must be shifted by 1. This can quickly become inefficient as the array grows in size. Also, a regular **linked list** produces linear time complexity - **O(n)** - when inserting an item to the end of the list.

This dual contant time property makes **doubly linked lists** a good candidate for the implementation of **Queues**.

### Doubly Linked List Implementation

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

A typical implementation for a queue will involve the storage of the queue items in an **array**. This is not a great solution because the dequeue operation requires the removal of the first element in the **array** which is a linear time - **O(n)** - operation.

Consequently, a doubly linked list is a great alternative for storing queue items because it enables both the **enqueue** and **dequeue** operations to be performed in constant time - **O(1)**.

### Queue Implementation

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
      items: [${this._items.toString()}]
    }`;
  }
}
```

In the above **Queue** class, the **dequeue** and **enqueue** methods both have constant time complexity. This meets the requirement for a good queue implementation.

### Queue Test

```javascript
const queue = new Queue();
console.log(queue.toString());
/*
  Queue {
    size: 0
    _items: []
  }
*/

queue.enqueue(10);
queue.enqueue(-19);
queue.enqueue(1000);
console.log(queue.toString());
/*
  Queue {
    size: 3
    _items: [10,-19,1000]
  }
*/

queue.dequeue();
console.log(queue.toString());
/*
  Queue {
    size: 2
    _items: [-19,1000]
  }
*/
```

Find out more about the applications of queues in this article: {% link https://dev.to/elishaking/stacks-and-queues-9o6 %}

Thanks 👍 for making it to the end 👨‍💻 and I really hope you found the content useful.

Leave a comment below or tweet me @ElishaChibueze if you have any questions or suggestions
