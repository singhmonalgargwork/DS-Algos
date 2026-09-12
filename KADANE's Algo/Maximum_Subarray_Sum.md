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

## BETTER APPROACH

