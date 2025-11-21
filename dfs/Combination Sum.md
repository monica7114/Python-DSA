# Combination Sum
``` python
class Solution:
    def combinationSum(self, candidates: List[int], target: int) -> List[List[int]]:
        res = []

        def dfs(i, current, total):
            if total == target:
                res.append(current[:])   # store a COPY of current
                return

            if i == len(candidates) or total > target:
                return

            # OPTION 1: take candidates[i]
            current.append(candidates[i])
            dfs(i, current, total + candidates[i])
            current.pop()

            # OPTION 2: skip candidates[i]
            dfs(i + 1, current, total)

        dfs(0, [], 0)
        return res
```
