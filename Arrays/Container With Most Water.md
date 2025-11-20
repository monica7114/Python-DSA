# Container With Most Water
## Using Two Pointers
``` python
class Solution:
    def maxArea(self, height: List[int]) -> int:
        area=0
        left=0
        n=len(height)
        right=n-1
        while left<right:
            d=right-left
            h=min(height[left], height[right])
            area=max(area, h*d)
            if height[left]<height[right]:
                left+=1
            else:
                right-=1
            
        return area
```
