\*As more data gets handled by computers - which is a big trend in computing -, **sorting** and **searching** are two of the biggest problems in the software world

Now, there are several great languages and frameworks that have sorting algorithms already implemented, so you may never need to write them from scratch. However, to be an effective software engineer, you need to know they work underneath and the tradeoffs between each of them for a given problem.

## Sorting Algorithms

When choosing a sorting algorithm, one key thing to consider is the scalability in terms of time and space complexities.

The time complexity is the number of operations required to perform a certain computation task.

The space complexity is the amount of memory required to perform a computation task.

Both are denoted by the Big-O notation.

### Bubble Sort

This may not be the most performant choice but it's implementation is simple and clear enough to understand and replicate. It provides a clear picture of how sorting works.

```javascript
function bubbleSort(arr) {
  for (let i = 0; i < arr.length; i++) {
    for (let j = 1; j < arr.length - i; j++) {
      if (arr[j] < arr[j - 1]) [arr[j], arr[j - 1]] = [arr[j - 1], arr[j]];
    }
  }

  return arr;
}
```

**Time Complexity**: O(N^2) <br>
**Space Complexity**: O(1)

For an array of length N, the bubble sort requires N^2 operations to completely sort the array and this is evident in the nested for loop.

By looking at the implementation, it's relatively easy to understand how it sorts the array. For every **ith** iteration, several comparisons and swappings are done in the second [j] for loop to move the larger numbers to the right.

### Selection Sort

This is one of the simpler sorting algorithms to understand but it also has a poor time complexity.

In most cases, the selection sort is usually the slowest of the sorting algorithms available.

```javascript
function selectionSort(arr) {
  for (let i = 0; i < arr.length; i++) {
    let minIdx = i;
    for (let j = i + 1; j < arr.length; j++) {
      if (arr[j] < arr[minIdx]) {
        minIdx = j;
      }
    }
    [arr[minIdx], arr[i]] = [arr[i], arr[minIdx]];
  }

  return arr;
}
```

**Time Complexity**: O(N^2) <br>
**Space Complexity**: O(1)

Also evident in the nested for loops, for an array of length N, the selection sort requires N^2 operations to completely sort the array.

For every **ith** iteration, the index of the minimum item in the range (i, N-1) is determined in the second [j] for loop. Then the minimum item is swapped with the current **ith** item.

### Insertion Sort

This one is a bit more complex than the first two. It can be the fastest of all the sorting algorithms if the data is nearly sorted but performs almost as badly as the two above for random data.

```javascript
function insertionSort(arr) {
  for (let i = 1; i < arr.length; i++) {
    if (arr[i] < arr[0]) {
      const val = arr.splice(i, 1)[0];
      arr.unshift(val);
    } else {
      for (let j = 1; j < i; j++) {
        if (arr[i] > arr[j - 1] && arr[i] < arr[j]) {
          const val = arr.splice(i, 1)[0];
          arr.splice(j, 0, val);
        }
      }
    }
  }
  return arr;
}
```

**Time Complexity**: <br>

- Nearly Sorted Data: O(N) <br>
- Random Data: O(N^2)

**Space Complexity**: O(1)
