Stacks and Queues are some of the basic data structures that have great utility while building your apps

# What is a Stack
A **stack** is a collection of items that supports only two operations: the **push** operation and the **pop** operation. A stack is a LIFO (Last In First Out) data structure which means that the last item pushed into a stack will be the first item poped from the stack.

Usually, the **push** and **pop** operations of a typical stack datastructure are constant time operations denoted by **O(1)** irrespective of the size of the stack.

There is no **Stack** object available in JavaScript out of the box but a stack can easily by represented by an **Array** object that only allows push and pop operations. 

The **push** and **pop** operations of a JavaScript Array are both constant time operations [**O(1)**] which meets the requirement for a good stack implementation

```javascript
class Stack {
  constructor(items) {
    this._items = items;
  }

  push(newItem) {
    this._items.push(newItem);
  }

  pop() {
    return this._items.pop();
  }

  size() {
    return this._items.length;
  }
}

const x = new Stack([1, 2, 3]); // stack: [1, 2, 3]
x.pop(); // stack: [1, 2]
x.push(100); // stack: [1, 2, 100]
```

There are many good use cases for the stack datastructure. A simple example is reversing a string

```javascript
const firstName = "King";
const nameStack = new Stack(firstName.split(""));
let reversedName = "";

for (let i = 0; i < firstName.length; i++) {
  reversedName += nameStack.pop();
}
console.log(reversedName); // gniK
```

JavaScript also uses something called a **call stack**  while executing scripts

# What is a Queue
A **queue** is a collection of items that supports only two operations: the **add or enqueue** operation and the **remove or dequeue** operation. Unlike a stack, a queue is a FIFO (First In First Out) data structure which means that the first item added to a queue must be the first item removed from the queue.

Similar to the stack, the **add** and **remove** operations of a queue are constant time operations.

There also no **Queue** object available in JavaScript out of the box but a stack can easily by represented by an **Array** object that only allows **enqueue** and **dequeue** operations

As mention earlier, the **push** operation on a JavaScript Array is a constant time operation which makes it idle for implementing the **enqueue** operation for the queue. The **shift** operation on a JavaScript Array can be used to implement **dequeue**, however, the **shift** operation has a linear time complexity [**O(n)**] and can get slow if the queue grows big enough. A clever work-around is shown below

```javascript
class Queue {
  startPos = 0;

  constructor(items) {
    this._items = items;
  }

  enqueue(newItem) {
    this._items.push(newItem);
  }

  dequeue() {
    if (this.startPos < this._items.length) 
      return this._items[this.startPos++];
  }

  size() {
    return this._items.length - this.startPos;
  }
}

const x = new Queue([1, 2, 3]); // queue: [1, 2, 3]
x.enqueue(10); // queue: [1, 2, 3, 10]
x.dequeue(); // queue: [2, 3, 10]
x.size(); // 3
x.enqueue(1000); // queue: [2, 3, 10, 1000]
```

In the above **Queue** class, the **dequeue** implementation has a constant time complexity which meets the queue datastructure requirement