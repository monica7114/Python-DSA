# Rotting Oranges
## Using BFS
``` python
from collections import deque
from typing import List
class Solution:
    def orangesRotting(self, grid: List[List[int]]) -> int:
        if not grid or not grid[0]:
            return 0
        q = deque()  # Queue stores coordinates (r, c) AND the time/minute
        fresh_count = 0
        minutes = 0

        rows, cols = len(grid), len(grid[0])
        
        def bfs(q, fresh_count,rows,cols,grid):
            minutes=0
            
            while q:
                r, c, time = q.popleft()
                minutes=time
                directions=[(0,1),(0,-1),(1,0),(-1,0)]
                for dr,dc in directions:
                    new_r,new_c=r+dr,c+dc
                    if 0<=new_r<rows and 0<=new_c<cols :
                        if grid[new_r][new_c]==1:
                            grid[new_r][new_c]=2
                            fresh_count -= 1
                            q.append((new_r, new_c, time + 1))
            return minutes,fresh_count
        
        for r in range(rows):
            for c in range(cols):
                if grid[r][c] == 2:
                    q.append((r, c, 0))
                elif grid[r][c] == 1:
                    fresh_count += 1
        final_minutes, final_fresh_count =bfs(q, fresh_count,rows,cols,grid)
        return final_minutes if final_fresh_count == 0 else -1
```



