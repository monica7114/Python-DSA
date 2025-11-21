# Longest Increasing Subsequence
## Using DP
Time Complexity: O(N^2)
``` python
class Solution:
    def lengthOfLIS(self, nums: List[int]) -> int:
        dp=[0]*(len(nums))
        
        for i in range(len(nums)):
            dp[i]=1
            for j in range(0,i):
                if nums[j]<nums[i]:
                    dp[i] = max(dp[i], dp[j] + 1)
        return max(dp)
        
```
## Using Binary Search
Time Complexity O(N logN)
``` python
from bisect import bisect_left
class Solution:
    def lengthOfLIS(self, nums: List[int]) -> int:
        tails=[]
        for num in nums:
            pos=bisect_left(tails,num)
            if pos==len(tails):
                tails.append(num)
            else:
                tails[pos]=num
        return len(tails)
        
```
