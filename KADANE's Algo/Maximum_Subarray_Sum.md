# Leetcde 53. Maximum Subarray

## BRUTE FORCE

- Generate all the subarrays possible and calculate sum and compare it with `MaximumSum` and return `MaximumSum`
```cpp
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
```
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

## OPTIMAL APPROACH

### Kadane's algo 

- whenever sum < 0 , we leave that element and start a new subarray from that element 

```cpp
int maximum=INT_MIN;
int sum=0;
for(int i=0;i<n;i++){
    sum+=nums[i];
    
    if(sum>maximum) maximum=sum;
    
    if(sum<0) sum=0; if sum<0 , reinitialize sum to 0 and leave that element;
 }

    return maximum;
```

Time Complexity- O(N)
Space Complexity- O(1)
