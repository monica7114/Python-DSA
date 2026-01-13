#  Separate Squares I
``` python
class Solution:
    def separateSquares(self, squares: List[List[int]]) -> float:
        t=0
        for i,j,l in squares:
            t+= (l*l)
        half= t/2
        squares.sort(key=lambda s: s[1])
        low=min(y for x,y,l in squares)
        high=max(y+l for x,y,l in squares)
        for i in range(60):
            mid=(low+high)/2
            
            belo=0
            for x,y,l in squares:
                if mid<=y:
                    continue
                elif mid>=y+l:
                    belo+= l*l
                else:
                    belo+= l * (mid - y)
            if belo<half:
                low=mid
            else:
                high=mid
        return (low + high) / 2


```
