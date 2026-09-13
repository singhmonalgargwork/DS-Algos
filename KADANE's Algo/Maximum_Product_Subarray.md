# Leetcode 152. Maximum Product Subarray

- This question is different from Maximum Subarray problem as , in Maximum Subarray, negatives always decrease our final answer hence , we discard as soon as our sum < 0 , but in this problem , negatives ```may``` contribute to the final answer as negative * negative results in positive value;

- In Maximum Subarray Sum , we maintained only 1 maximum subarray sum variable which was ```minimum``` , but here , we need to maintain both maximum product vakue and minimum product value ending at current position; 

## CODE

- This code can be called as Modified- Kadane's algorithm

```cpp

class Solution {
public:
    int maxProduct(vector<int>& nums) {
        int n=nums.size();
        int maxprod=nums[0];
        int minprod=nums[0];

        int ans=nums[0]; // value to be returned;

        for(int i=1;i<n;i++){
            int x=nums[i];

            int newmax=max({x,maxprod*x,minprod*x});
            int newmin=min({x,maxprod*x,minprod*x});

            maxprod=newmax;
            minprod=newmin;

            ans=max(ans,maxprod);
        }

        return ans;
    }
};

```
Time Complexity- O(N) <br>
Space Complexity- O(1)