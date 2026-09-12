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