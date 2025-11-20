# House Robber
## Using Memoiztion
``` python
class Solution:
    def rob(self, nums: List[int]) -> int:
        memo={}
        def solve(i):
            if i>=len(nums):
                return 0
            if i in memo:
                return memo[i]
            rob=nums[i]+solve(i+2)
            skip=solve(i+1)
            memo[i]=max(rob,skip)
            return memo[i]
        return solve(0)
```
## Using DP
``` python
class Solution:
    def rob(self, nums: List[int]) -> int:
        n=len(nums)
        if n==1:
            return nums[0]
        dp=[0]*(n+1)
        dp[n]=0
        dp[n-1]=nums[n-1]
        for i in range(n-2,-1,-1):
            dp[i]=max(nums[i]+dp[i+2], dp[i+1])
        return dp[0]
```
