# Clone Graph
## Using BFS
``` python

# Definition for a Node.
class Node:
    def __init__(self, val = 0, neighbors = None):
        self.val = val
        self.neighbors = neighbors if neighbors is not None else []


from typing import Optional
class Solution:
    def cloneGraph(self, node: Optional['Node']) -> Optional['Node']:
        if not node:
            return None
        mp={}
        q=deque([node])
        mp[node]=Node(node.val)
        while q:
            original=q.popleft()
            copy=mp[original]
            for nei in original.neighbors:
                if nei not in mp:
                    mp[nei]=Node(nei.val)
                    q.append(nei)
                n_copy=mp[nei]
                copy.neighbors.append(n_copy)
        return mp[node]
```
            

        
