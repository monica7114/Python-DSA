# Spiral Matrix
## Using 4 Pointers
``` python
class Solution:
    def spiralOrder(self, matrix: List[List[int]]) -> List[int]:
        r=len(matrix)
        c=len(matrix[0])
        top=0
        bottom=r-1
        left=0
        right=c-1
        res=[]
        while top<=bottom and left<=right:
            for j in range(left,right+1):
                res.append(matrix[top][j])
            top+=1
            for i in range(top,bottom+1):
                res.append(matrix[i][right])
            right-=1
            if top<=bottom:
                for j in range(right,left-1,-1):
                    res.append(matrix[bottom][j])
                bottom-=1
            if left<=right:
                for i in range(bottom,top-1,-1):
                    res.append(matrix[i][left])
                left+=1
        return res
```



        
