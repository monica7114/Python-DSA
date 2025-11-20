# Maximum Product Subarray
## Time Complexity: O(n)
## Space Complexity: O(1)
``` python
class Solution:
    def maxProduct(self, nums: List[int]) -> int:
        current_max=nums[0]
        current_min=nums[0]
        res=nums[0]
        for num in nums[1:]:
            if num<0:
                current_max, current_min=current_min, current_max
            current_max=max(num,current_max*num)
            current_min=min(num, current_min*num)
            res=max(res,current_max)
        return res

```
