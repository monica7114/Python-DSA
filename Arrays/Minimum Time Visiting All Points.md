#  Minimum Time Visiting All Points
``` python
class Solution:
    def minTimeToVisitAllPoints(self, points: List[List[int]]) -> int:
        t=0
        n=len(points)
        
        for i in range(1,n):
            x=max(abs(points[i-1][0]-points[i][0]), abs(points[i-1][1]-points[i][1]))
            t+=x
        return t
```
