# Sieve of Eratosthenes

## 1. Overview

The **Sieve of Eratosthenes** is an efficient algorithm used to find all prime numbers smaller than a given integer `n`.

Instead of checking each number individually for primality, the algorithm repeatedly marks the multiples of each prime number as non-prime.

- **Algorithm:** Sieve of Eratosthenes
- **LeetCode Problem:** [204. Count Primes](https://leetcode.com/problems/count-primes/)
- **Difficulty:** Medium
- **Time Complexity:** `O(n log log n)`
- **Space Complexity:** `O(n)`

---

## 2. Intuition

A prime number is a number greater than `1` that has exactly two positive divisors: `1` and itself.

For example:

- Prime numbers: `2, 3, 5, 7, 11`
- Non-prime numbers: `4, 6, 8, 9, 10`

The main observation behind the Sieve of Eratosthenes is:

**If a number is prime, all its multiples greater than itself are non-prime.**

For example:

- `2` is prime, so mark `4, 6, 8, 10, 12, ...` as non-prime.
- `3` is prime, so mark `6, 9, 12, 15, ...` as non-prime.
- `5` is prime, so mark `10, 15, 20, 25, ...` as non-prime.

After processing all relevant prime numbers, the unmarked numbers greater than or equal to `2` are prime.

---

## 3. Algorithm

1. Create a boolean array `isPrime` of size `n`, initially setting every element to `true`.
2. Mark `0` and `1` as non-prime.
3. Iterate through numbers `i` starting from `2`, while `i * i < n`.
4. If `isPrime[i]` is `true`, mark all multiples of `i` starting from `i * i` as non-prime.
5. Count all numbers from `2` to `n - 1` that

## 10. LeetCode-Based C++ Solution

### Problem: [204. Count Primes](https://leetcode.com/problems/count-primes/)

**Problem Statement:** Given an integer `n`, return the number of prime numbers strictly less than `n`.

### Approach

Use the Sieve of Eratosthenes to identify all prime numbers in the range `[2, n - 1]`.

1. If `n <= 2`, return `0` because no prime number is strictly less than `n`.
2. Create a Boolean array `isPrime` of size `n`, initialized to `true`.
3. Mark `0` and `1` as non-prime.
4. For every prime candidate `i` satisfying `i * i < n`, mark its multiples starting from `i * i` as non-prime.
5. Count all entries that remain `true` from `2` to `n - 1`.
6. Return the count.

## C++ Code
Problem: 204. Count Primes

```cpp
class Solution {
public:
    int countPrimes(int n) {
        if (n <= 2) {
            return 0;
        }

        vector<bool> isPrime(n, true);

        isPrime[0] = false;
        isPrime[1] = false;

        for (int i = 2; i * i < n; i++) {
            if (isPrime[i]) {
                for (int j = i * i; j < n; j += i) {
                    isPrime[j] = false;
                }
            }
        }

        int count = 0;

        for (int i = 2; i < n; i++) {
            if (isPrime[i]) {
                count++;
            }
        }

        return count;
    }
};
```

### Example

**Input:**
```text
n = 10
```

**Output:**
```text
4
```

**Explanation:** The prime numbers strictly less than `10` are `2, 3, 5, 7`. Therefore, the answer is `4`.

### Complexity Analysis

- **Time Complexity:** `O(n log log n)` — marking the multiples of prime numbers takes this amount of time overall.
- **Space Complexity:** `O(n)` — the Boolean array stores primality information for numbers from `0` to `n - 1`.

### Important LeetCode-Specific Detail

The standard sieve often finds primes **up to and including** `N`, using an array of size `N + 1` and conditions such as `j <= N`.

However, LeetCode 204 asks for primes **strictly less than** `n`. Therefore:

- Array size: `n`
- Outer loop condition: `i * i < n`
- Inner loop condition: `j < n`
- Counting range: `2` through `n - 1`

