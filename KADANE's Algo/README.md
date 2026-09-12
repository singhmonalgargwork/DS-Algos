# Kadane's Algorithm

## Theory

Kadane's Algorithm is used to find the **maximum sum of a contiguous subarray**.

The main idea is to decide at every element:

> **Should I start a new subarray from this element, or extend the previous subarray?**

For every `nums[i]`:

```text
currentSum = max(nums[i], currentSum + nums[i])
```

There are two choices:

* `nums[i]` → Start a new subarray.
* `currentSum + nums[i]` → Extend the previous subarray.

We then store the overall maximum:

```text
maxSum = max(maxSum, currentSum)
```

If the previous sum is hurting our answer, we discard it and start fresh from the current element.

---

## How to Identify Kadane's Algorithm

Kadane's Algorithm is likely applicable when the question contains:

* **Contiguous subarray**
* **Maximum/minimum sum**
* **Largest/smallest sum of a continuous segment**

### Quick Recognition Pattern

```text
Array
  +
Contiguous
  +
Maximum/Minimum Sum
```

➡️ **Think about Kadane's Algorithm.**

However, don't apply it blindly. Problems involving fixed-size windows, circular arrays, deletion of elements, etc. may require a modified version.

---

## Worked Dry Run

Consider:

```text
nums = [-2, 1, -3, 4, -1, 2, 1, -5, 4]
```

Initialize:

```text
currentSum = -2
maxSum = -2
```

Now process each element:

| `i` | `nums[i]` | `currentSum` | `maxSum` | Decision                |
| --: | --------: | -----------: | -------: | ----------------------- |
|   0 |        -2 |           -2 |       -2 | Start                   |
|   1 |         1 |            1 |        1 | Start new: `1 > -2 + 1` |
|   2 |        -3 |           -2 |        1 | Extend: `1 + (-3)`      |
|   3 |         4 |            4 |        4 | Start new: `4 > -2 + 4` |
|   4 |        -1 |            3 |        4 | Extend                  |
|   5 |         2 |            5 |        5 | Extend                  |
|   6 |         1 |            6 |        6 | Extend                  |
|   7 |        -5 |            1 |        6 | Extend                  |
|   8 |         4 |            5 |        6 | Extend                  |

Therefore:

```text
Maximum Subarray Sum = 6
```

The subarray responsible for this is:

```text
[4, -1, 2, 1]
```

Its sum is:

```text
4 + (-1) + 2 + 1 = 6
```

### What Kadane's Algorithm is Doing

At every position:

```text
                    ┌── Start new
nums[i] ────────────┤
                    └── Extend previous
```

Choose whichever gives the larger sum:

```text
currentSum = max(nums[i], currentSum + nums[i])
```

---

## Code Template

### Standard Template

```cpp
int currentSum = nums[0];
int maxSum = nums[0];

for(int i = 1; i < nums.size(); i++) {

    currentSum = max(nums[i], currentSum + nums[i]);

    maxSum = max(maxSum, currentSum);
}

return maxSum;
```

### Alternative Template

```cpp
int sum = 0;
int maxi = INT_MIN;

for(int i = 0; i < nums.size(); i++) {

    sum += nums[i];

    maxi = max(maxi, sum);

    if(sum < 0) {
        sum = 0;
    }
}

return maxi;
```

> The first template is generally safer to remember because it naturally handles arrays containing only negative numbers.

---

## Complexity

```text
Time Complexity:  O(n)
Space Complexity: O(1)
```

## One-Line Summary

> **At every element, choose between starting a new subarray and extending the previous one, while keeping track of the best sum found so far.**
