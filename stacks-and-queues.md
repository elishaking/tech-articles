Stacks and Queues are some of the basic data structures that have great utility while building your apps

# What is a Stack
A **stack** is a collection of items that supports only two operations: the **push** operation and the **pop** operation. A stack is a LIFO (Last In First Out) data structure which means that the last item pushed into a stack will be the first item poped from the stack.

Usually, the **push** and **pop** operations of a typical stack datastructure are constant time operations denoted by **O(1)** irrespective of the size of the stack.

There is no **Stack** object available in JavaScript out of the box but a stack can easily by represented by an **Array** object that only allows push and pop operations

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

