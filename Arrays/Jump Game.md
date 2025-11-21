# Jump Game
``` python
class Solution:
    def canJump(self, nums: List[int]) -> bool:
        n=len(nums)
        farthest = 0
        for i in range(n):
            if i > farthest: return False
            farthest = max(farthest, i + nums[i])
        return True
```
## Another Optimized Method
``` python
class Solution:
    def canJump(self, nums: List[int]) -> bool:
        goal = len(nums) - 1

        for i in range(len(nums) - 2, -1, -1):
            if i + nums[i] >= goal:
                goal = i
        
        return True if goal == 0 else False
```
