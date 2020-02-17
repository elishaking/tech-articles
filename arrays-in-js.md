Arrays are indispensable data-structures in javascript and understanding how to effectively use to solve problems is a crucial skill to master.

Arrays are represented by a robust object in JavaScript that provides several useful methods and operations to work with. I'll be going over most of them in this article

# Iterating over arrays

There are several methods available for array iteration in JavaScript

## forEach

You can iterate over the array to apply an operation to each item using `forEach`

```javascript
const arr = [1, 2, 3, 4, 5];

arr.forEach(item => item + 100); // [101, 102, 103, 104, 105]
```

## map

`map` allows you to create a new array by applying an operation/function to each item

```javascript
const arr = [1, 2, 3, 4, 5];

const newArr = arr.map(item => item + 100); // [101, 102, 103, 104, 105]

// arr remains the same
```

Unlike `forEach`, it does not modify the original array

## filter

Loops through the array and return only the items that satisfy a given condition

```javascript
const arr = [1, 2, 3, 4, 5];

// get all items greater than 2
const greaterThanTwoArr = arr.filter(item => item > 2); // [3, 4, 5]
```

## reduce

The `reduce` function loops through the array, applying an operation/function to each element and an accumulator from left to right and returns the accumulated value

```javascript
const arr = [1, 2, 3, 4, 5];

const sum = arr.reduce((total, item) => total + item, 0); // 8
```

## reduceRight

Identical to reduce but works from right to left

```javascript
const arr = [1, 2, 3, 4, 5];

const sum = arr.reduceRight((total, item) => total + item, 0); // 8
```

# Modifying arrays

JavaScript provides several useful methods and operations for modifying arrays

## push

Adds an item to the end of the array

```javascript
const arr = [1, 2, 3, 4, 5];

arr.push(100); // [1, 2, 3, 4, 5, 100]
```

## pop

Removes an item from the end of the array

```javascript
const arr = [1, 2, 3, 4, 5];

arr.pop(); // [1, 2, 3, 4]
```

## unshift

Adds an item to the beginning of the array

```javascript
const arr = [1, 2, 3, 4, 5];

arr.unshift(100); // [100, 1, 2, 3, 4, 5]
```

## shift

Removes an item from the beginning of the array

```javascript
const arr = [1, 2, 3, 4, 5];

arr.shift(); // [2, 3, 4, 5]
```

## splice

Removes an item from a specified index in the array.

```javascript
const arr = [1, 2, 3, 4, 5];

// remove item at index 1
arr.splice(1, 1); // [1, 3, 4, 5]
```

`splice` can also remove multiple items from a start index.

```javascript
const arr = [1, 2, 3, 4, 5];

// remove 2 items starting from index 1
arr.splice(1, 2);
```

```javascript
const arr = [1, 2, 3, 4, 5];

// remove all items starting from index 2
arr.splice(2, arr.length);
```

## reverse

Reverses the items in the array

```javascript
const arr = [1, 2, 3, 4, 5];

arr.reverse(); // [5, 4, 3, 2, 1]
```

## concat

Adds the items of another array to the end of the original array

```javascript
const arr = [1, 2, 3, 4, 5];

const newArr = arr.concat([100, 200, 300]); // [1, 2, 3, 4, 5, 100, 200, 300]
```

## spread operator

This operator is similar in function to the `concat` method but offers more flexibility

```javascript
const arr = [1, 2, 3, 4, 5];

const newArr = [...arr, ...[100, 200, 300]]; // [1, 2, 3, 4, 5, 100, 200, 300]
```

Add to the beginning

```javascript
const arr = [1, 2, 3, 4, 5];

const newArr = [...[100, 200, 300], ...arr]; // [100, 200, 300, 1, 2, 3, 4, 5]
```

Complex combinations

```javascript
const arr = [1, 2, 3, 4, 5];
const arr2 = [100, 200, 300];

const newArr = [...arr2, ...arr, 10, 9, ...arr, -10]; // [ 100, 200, 300, 1, 2, 3, 4, 5, 10, 9, 1, 2, 3, 4, 5, -10 ]
```

# Searching arrays

There are several convenience method for find items in arrays or verifying a condition

## indexOf

Finds the index of the **first occurence** of a given item within an array

```javascript
const arr = [1, 2, 3, 2, 2, 4, 5];
arr.indexOf(2); // 1
arr.indexOf(5); // 4
arr.indexOf(100); // -1
arr.indexOf(10); // -1
```

## includes

Checks if the array contains the specified item

```javascript
const arr = [1, 2, 3, 2, 2, 4, 5];

arr.includes(10); // false
arr.includes(2); // true
```

## find

This method returns the first item in the array that satisfies a given condition

```javascript
const arr = [1, 4, 8, 2, 2, 4, 5];
arr.find(item => item % 2 === 0); // 4
arr.find(item => item / 2 === 4); // 8
arr.find(item => (item * item) / 2 === 2); // 2
```

## findIndex

Similar to `find` except that it returns the index

```javascript
const arr = [1, 4, 8, 2, 2, 4, 5];
arr.findIndex(item => item % 2 === 0); // 1
arr.findIndex(item => item / 2 === 4); // 2
arr.findIndex(item => (item * item) / 2 === 2); // 3
```

## some

Checks if one or more items in the array satisfies a given condition

```javascript
const arr = [1, 4, 8, 2, 2, 4, 5];
arr.some(item => item > 2); // true
arr.some(item => item % 8 === 0); // true
arr.some(item => item < 0); // false
```

```javascript
const arr = [1, 4, 8, 2, 2, 4, 5];
```
