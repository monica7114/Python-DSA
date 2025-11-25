# Validate Binary Search Tree
``` python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def isValidBST(self, root: Optional[TreeNode]) -> bool:
        if not root:
            return True
        def validate(node,min_val,max_val):
            if not node:
                return True
            if not (min_val<node.val<max_val):
                return False
            is_right=validate(node.right,node.val,max_val)
            is_left=validate(node.left,min_val,node.val)
            return is_right and is_left
        return validate(root, -math.inf,math.inf)
```
