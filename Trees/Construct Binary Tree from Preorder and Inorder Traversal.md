# Construct Binary Tree from Preorder and Inorder Traversal
``` python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def buildTree(self, preorder: List[int], inorder: List[int]) -> Optional[TreeNode]:
        in_map={val:i for i,val in enumerate(inorder)}
        self.preorder_index=0
        def build_optimized(inorder_start: int, inorder_end: int) -> Optional[TreeNode]:
            if inorder_start > inorder_end:
                return None
            
            # 1. Find the Root: The current root is determined by the global preorder index.
            root_val = preorder[self.preorder_index]
            root = TreeNode(root_val)
            self.preorder_index+=1
            root_index_inorder=in_map[root_val]
            root.left=build_optimized(inorder_start,root_index_inorder-1)
            root.right=build_optimized(root_index_inorder+1,inorder_end)
            return root
        return build_optimized(0,len(inorder)-1)
```
