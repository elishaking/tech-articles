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
  const N = arr.length;

  for (let i = 0; i < N; i++) {
    for (let j = 1; j < N - i; j++) {
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
  const N = arr.length;

  for (let i = 0; i < N; i++) {
    let minIdx = i;
    for (let j = i + 1; j < N; j++) {
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
  const N = arr.length;

  for (let i = 1; i < N; i++) {
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

---

The three sorting algorithms mentioned above are called **elementary sorts** with a poor average time complexity of O(N^2).

However, the sorting algorithms discussed below perform much better with a time complexity of O(NLog(N)). They take a divide and conquer approach.

### Merge Sort

This is one of the most efficient sorting algorithms available and will perform better than others in most cases.

It also preserves the original order for identical items which makes it [stable](https://stackoverflow.com/questions/1517793/what-is-stability-in-sorting-algorithms-and-why-is-it-important).

```javascript
function mergeSort(arr) {
  const N = arr.length;
  if (N === 1) return arr;

  const midIdx = Math.floor(N / 2);
  const left = arr.slice(0, midIdx);
  const right = arr.slice(midIdx);

  return merge(mergeSort(left), mergeSort(right));
}

function merge(left, right) {
  const merged = [];
  let leftIdx = 0;
  let rightIdx = 0;

  while (leftIdx < left.length && rightIdx < right.length) {
    if (left[leftIdx] < right[rightIdx]) {
      merged.push(left[leftIdx]);
      leftIdx++;
    } else {
      merged.push(right[rightIdx]);
      rightIdx++;
    }
  }

  return [...merged, ...left.slice(leftIdx), ...right.slice(rightIdx)];
}
```

**Time Complexity**: O(Nlog(N)) <br>
**Space Complexity**: O(N)

The merge sort uses a recursive approach to achieve an impressive linearithmic time complexity.

It is clear from the **base case** of the recursive `mergeSort` function that the input array of length N is split into N separate parts. These parts are then merged together in the merge function.

### Quick Sort

This is very similar to the merge sort but has a more complex implementation. Unlike the merge sort, splitting is done using something called a **pivot** which is chosen randomly.

It has the same time complexity as the merge sort: O(Nlog(N)). In worst case scenarios, it can have a time complexity of O(N^2)

However, it can perform better than the merge sort under some conditions:

- Smaller datasets (typically)
- When a good pivot is selected

```javascript
function quickSort(arr) {
  const N = arr.length;

  sortQ(arr, 0, Math.floor(N / 2));
}

function sortQ(arr, left, right) {
  let pivotIdx;
  let partitionIdx;

  if (left < right) {
    pivotIdx = right;
    partitionIdx = partition(arr, pivotIdx, left, right);

    sortQ(arr, left, partitionIdx - 1);
    sortQ(arr, partitionIdx + 1, right);
  }
  return arr;
}

function partition(arr, pivotIdx, left, right) {
  let pivotValue = arr[pivotIdx];
  let partitionIdx = left;

  for (let i = left; i < right; i++) {
    if (arr[i] < pivotValue) {
      [arr[i], arr[partitionIdx]] = [arr[partitionIdx], arr[i]];
      partitionIdx++;
    }
  }

  [arr[right], arr[partitionIdx]] = [arr[partitionIdx], arr[right]];
  return partitionIdx;
}
```

**Time Complexity**: <br>

- Good Pivot: O(Nlog(N)) <br>
- Bad Pivot: O(N^2)

**Space Complexity**: O(log(N))

The space complexity for quick sort is much better than that of the merge sort, so if memory is a constraint, quick sort is the better option

<!-- Like the merge sort, it takes a divide and conquer approach to split the array using a **pivot element** that is first chosen at random. -->

---

There are more sorting algorithms to explore but the five discussed so far are used widely. Also, the other algorithms usually have some constraints on the type of data they can sort.

You may never encounter a situation where you need to implement a sorting algorithm from scratch but it's absolutely crucial to know when to use either of the available ones to solve a problem.

Thanks 👍 for making it to the end 👨‍💻 and I really hope you found the content useful.

Leave a comment below or tweet me @ElishaChibueze if you have any questions or suggestions
