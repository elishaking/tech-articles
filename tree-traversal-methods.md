There are three ways to traverse or visit all the nodes in a tree. They are:

## In-order Traversal
This form of traversal works by visiting the left branch of the tree, then the current node, and then the right branch.

Below is an implementation of in-order traversal:

```javascript
function inOrder(treeNode) {
  if (treeNode) {
    // explore left branch
    inOrder(treeNode.left);

    // visit/print current node
    console.log(treeNode.value);

    // explore right branch
    inOrder(treeNode.right);
  }
}
```

![Tree](https://raw.githubusercontent.com/elishaking/tech-articles/master/tree.png)

If we had a simple tree like the one above, with in-order traversal, the node values will be printed in this order:

```javascript
[40, 20, 50, 10, 60, 30, 70]
```

## Pre-order Traversal
This form of traversal works by first visiting the current node, then the left branch, and finally, the right branch.

Below is an implementation of pre-order traversal:

```javascript
function preOrder(treeNode) {
  if (treeNode) {
    // visit/print current node
    console.log(treeNode.value);

    // explore left branch
    preOrder(treeNode.left);

    // explore right branch
    preOrder(treeNode.right);
  }
}
```

![Tree](https://raw.githubusercontent.com/elishaking/tech-articles/master/tree.png)

If we had a simple tree like the one above, with pre-order traversal, the node values will be printed in this order:

```javascript
[10, 20, 40, 50, 30, 60, 70]
```

## Post-order Traversal
This form of traversal works by exploring child nodes before the current node.

Below is an implementation of post-order traversal:

```javascript
function postOrder(treeNode) {
  if (treeNode) {
    // explore left branch
    postOrder(treeNode.left);

    // explore right branch
    postOrder(treeNode.right);

    // visit/print current node
    console.log(treeNode.value);
  }
}
```

![Tree](https://raw.githubusercontent.com/elishaking/tech-articles/master/tree.png)

If we had a simple tree like the one above, with post-order traversal, the node values will be printed in this order:

```javascript
[40, 50, 20, 60, 70, 30, 10]
```

___

Thanks 👍 for making it to the end 👨‍💻 and I really hope you found the content useful.

Leave a comment below or tweet me @ElishaChibueze if you have any questions or suggestions