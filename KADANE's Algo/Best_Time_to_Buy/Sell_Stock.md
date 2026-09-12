# LEETCODE- 121. Best Time to Buy and Sell Stock

## BRUTE FORCE
- Generate all the subarrays and check....

```cpp
int n=prices.size();
int maxprofit=INT_MIN;

for(int i=0;i<n;i++){
    int profit=0;
    for(int j=i+1;j<n;j++){
        profit=prices[j]-prices[i];
        maxprofit=max(maxprofit,profit);
    }
}

return maxprofit<0 ?  0 :  maxprofit;
```

Time Complexity- O(N^2) <br>
Space Complexity- O(1)

## OPTIMAL APPROACH
### KADANE'S ALGO

- Calculate change (current value-previous value) for every element and then decide whether to continue with the subarray or start fresh from the current element;

```cpp
int n=prices.size();
int maxprofit=INT_MIN;

int profit=0;

    for(int i=1;i<n;i++){
        int change=prices[i]-prices[i-1];

        profit=max(change,change+profit); // either continue the subarray(change+profit) or discard and simply start a new subarray

        maxprofit=max(maxprofit,profit);
    }

    return maxprofit<0 ? 0 : maxprofit;
``` 

Time Complexity- O(N) <br>
Space Complexity- O(1)