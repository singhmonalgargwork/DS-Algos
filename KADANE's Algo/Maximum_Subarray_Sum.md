# Leetcde 53. Maximum Subarray

## BRUTE FORCE

- Generate all the subarrays possible and calculate sum and compare it with `MaximumSum` and return `MaximumSum`

class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int n=nums.size();

        int MaximumSum=INT_MIN;

        for(int i=0;i<n;i++){
            for(int j=i;j<n;j++){
                int sum=0;
                for(int k=i;k<=j;k++){
                    sum+=nums[k];
                }

                MaximumSum=max(sum,maximum);
            }
        }

        return MaximumSum;
    }
};

Time Complexity- Nearly around O(N^3) <br>
Space Complexity- O(1)


## BETTER APPROACH

-Use prefix sum technique and add new index's value to sum and then compute max of sum and MaximumSum and return MaximumSum <br>
```cpp
for(int i=0;i<n;i++){
    int sum=0;
    for(int j=i;j<n;j++){
        sum+=nums[j];
        maximum=max(sum,maximum);
        }

}

    return maximum;
    ```

Time Complexity- Nearly around O(N^2) <br>
Space Complexity- O(1)