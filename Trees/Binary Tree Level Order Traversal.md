# Binary Tree Level Order Traversal
``` python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def levelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
        if not root:
            return []
        res=[]
        q=deque([root])
        
        while q:
            
            l=len(q)
            current_lvl=[]
            for i in range(l):
                
                node=q.popleft()
                current_lvl.append(node.val)



                if node.left:
                    q.append(node.left)
                if node.right:
                    q.append(node.right)
            res.append(current_lvl)
        return res
```
