# Combination Sum III
``` python
class Solution:
    def combinationSum3(self, k: int, n: int) -> List[List[int]]:
        res=[]
        def dfs(start,current,remain):
            if remain==0 and len(current)==k:
                res.append(current[:])
                return
            
            
            for j in range(start,10):
                if j>remain:
                    break
                

                current.append(j)
                dfs(j+1,current,remain-j)
                current.pop()
        dfs(1,[],n)
        return res
```
