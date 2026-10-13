# Dutch National Flag Algorithm 

##  What is the Dutch National Flag Algorithm?
- The Dutch National Flag (DNF) algorithm is an in-place array partitioning technique used to divide an array into three groups in a single traversal.

- DNF exploits the fact that there are exactly three categories of values.

- It is commonly used when an array contains three distinct categories of elements, such as 0, 1, and 2.

- Suppose:-
```text
Input:  [2, 0, 2, 1, 1, 0]
Output: [0, 0, 1, 1, 2, 2]
```
The objective is to group all 0s first, followed by all 1s, and finally all 2s.

  - The algorithm maintains three pointers:

    - low: boundary of the region containing 0s.

    - mid: current element being examined.

    - high: boundary of the region containing 2s.

- Initialize these 3 pointers as
  ```text
  int low = 0;
  int mid = 0;
  int high = n - 1;
  ```

## Code Template
```cpp
while (mid <= high) {
    if (nums[mid] == 0) { // current element belongs to leftmost region
        swap(nums[low], nums[mid]);
        low++;
        mid++;
    }
    else if (nums[mid] == 1) { // The current element already belongs in the middle region.
        mid++;
    }
     else { // The current element belongs in the rightmost region.
        swap(nums[mid], nums[high]);
        high--;
    }
}
```

## Complexity Analysis
Time Complexity: O(n)  
Space Complexity: O(1)