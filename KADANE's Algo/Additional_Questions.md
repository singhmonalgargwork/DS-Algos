# Some additional questions on KADANE's algorithm 

## Leetcode 918. Maximum Sum Circular Subarray
- This question demands a comprehensive thinking on Kadane's algo and also the concept of ```wrapping``` in ```circular arrays```

### Case 1: Non-wrapping subarray 
- The subarray lies entirely within the normal array boundaries. <br>
- We can solve this using ```ordinary Kadane's algorithm.```

### Case 2: Wrapping subarray
- A wrapping subarray consists of:
  - A suffix of the array.
  - A prefix of the array.
  - The elements between the selected suffix and prefix are excluded.

- In such scenarios/case - 
  - ``` return max(maxSum , TotalSum - minSum)``` , where maxSum is the sum according to normal maximize Kdane's algo , minSum is the sum according to normal minimize Kdane's algo

- ### ** Edge case ** - All elements are negative
``` straightaway return the maxSum obtained using kadane's algo``` 

## CODE

```cpp
class Solution {
public:
    int maxSubarraySumCircular(vector<int>& nums) {
        int n=nums.size();

        int totalSum=0;

        int currentMaxsum=0;
        int maxSum=nums[0];

        int currentMinsum=0;
        int minSum=nums[0];

        for(int i=0;i<n;i++){
            totalSum+=nums[i];

            currentMaxsum=max(currentMaxsum+nums[i] , nums[i]);
            maxSum=max(maxSum,currentMaxsum);

            currentMinsum=min(currentMinsum+nums[i] , nums[i]);
            minSum=min(minSum,currentMinsum);
        }

        if(maxSum<0) return maxSum; // all elements are negative 
        
        else return max(maxSum,totalSum-minSum);
    }
};
```
Time Complexity- O(N) <br>
Space Complexity- O(1) 

## Leetcode 1749. Maximum Absolute Sum of Any Subarray
