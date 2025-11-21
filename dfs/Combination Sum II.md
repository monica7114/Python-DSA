# Combination Sum II
``` python
class Solution:
    def combinationSum2(self, candidates: List[int], target: int) -> List[List[int]]:
        res=[]
        candidates.sort()
        def dfs(start,current,remain):
            if remain==0:
                res.append(current[:])
                return

            for i in range(start,len(candidates)):
                if i>start and candidates[i]==candidates[i-1]:
                    continue
                if candidates[i]>remain:
                    break
                current.append(candidates[i])
                dfs(i+1,current,remain-candidates[i])
                current.pop()
            
            
        dfs(0, [], target)
        return res

```
