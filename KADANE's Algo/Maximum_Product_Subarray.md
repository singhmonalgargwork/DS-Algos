# Leetcode 152. Maximum Product Subarray

- This question is different from Maximum Subarray problem as , in Maximum Subarray, negatives always decrease our final answer hence , we discard as soon as our sum < 0 , but in this problem , negatives ```may``` contribute to the final answer as negative * negative results in positive value;

- In Maximum Subarray Sum , we maintained only 1 maximum subarray sum variable which was ```minimum``` , but here , we need to maintain both maximum product vakue and minimum product value ending at current position; 

