# Pacific Atlantic Water Flow
## Using Reverse DFS
``` python
class Solution:
    def pacificAtlantic(self, heights: List[List[int]]) -> List[List[int]]:
        if not heights or not heights[0]:
            return []
        pacific=set()
        atlantic=set()
        rows,cols=len(heights),len(heights[0])
        def dfs(r,c,reach):
            if (r,c)in reach:
                return
            reach.add((r,c))
            directions=[(0,1),(0,-1),(1,0),(-1,0)]
            for dr,dc in directions:
                new_r,new_c= dr+r,dc+c
                if 0<=new_r<rows and 0<=new_c<cols:
                    if heights[new_r][new_c]>=heights[r][c]:
                        dfs(new_r,new_c,reach)
        for r in range(rows):
            dfs(r,0,pacific)
            dfs(r,cols-1,atlantic)
        for c in range(cols):
            dfs(0,c,pacific)
            dfs(rows-1,c,atlantic)
        return list(pacific.intersection(atlantic))
```
