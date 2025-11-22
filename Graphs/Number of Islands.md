# Number Of Islands
## Using BFS
``` python
from collections import deque
from typing import List
class Solution:
    def numIslands(self, grid: List[List[str]]) -> int:
        if not grid or not grid[0]:
            return 0

        rows, cols = len(grid), len(grid[0])
        island_count = 0
        
        def bfs(r,c):
            q = deque([(r, c)])
            grid[r][c] = "0"
            while q:
                row,col=q.popleft()
                directions=[(0,1),(0,-1),(1,0),(-1,0)]
                for dr,dc in directions:
                    new_r,new_c=row+dr,col+dc
                    if 0<=new_r<rows and 0<=new_c<cols and grid[new_r][new_c]=="1":
                        grid[new_r][new_c]="0"
                        q.append((new_r,new_c))

        for row in range(rows):
            for col in range(cols):
                if grid[row][col]=="1":
                    island_count+=1
                    bfs(row,col)
        return island_count


```
