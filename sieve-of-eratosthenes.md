# Sieve of Eratosthenes

The Sieve of Eratosthenes is a simple and fast algorithm for finding all the prime numbers in the range [2, n]. It works by removing multiples of consecutive numbers.

Other algorithms used to accomplish this are less efficient and will typically produce time complexities of **O(N^2)** or **O(N^(3/2))**.

Below is a JavaScript implementation of the Sieve of Eratosthenes:

```javascript
const sieveOfEratosthenes = (n) => {
  // initially label every number from [0, n] as a prime number
  const primeNumbersSieve = new Array(n + 1).fill(true);

  // since 0 and 1 are not prime numbers, label them as false
  primeNumbersSieve[0] = primeNumbersSieve[1] = false;

  /**
   * we stop the loop when i > sqrt(n) which is equivalent
   * to i * i <= n. this is because the maximum divisor of n
   * is sqrt(n), therefore if we allow values of i > sqrt(n)
   * in the loop, we will end up with a value for i where i * i > n
   */
  for (let i = 2; i * i <= n; i++) {
    if (primeNumbersSieve[i]) {
      /**
       * skip all multiples of i < i * i because they have
       * already been checked
       */
      let k = i * i;
      while (k <= n) {
        // remove all multiples of i starting from i * i
        primeNumbersSieve[k] = false;
        k += i;
      }
    }
  }

  return primeNumbersSieve;
};
```

The time complexity of the sieve is **O(nlog(log(n)))**. It is currently the most efficient algorithm for finding all prime numbers in the range [2, n].
