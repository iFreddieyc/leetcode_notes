# Subtree of another tree
[Link to the problem](https://leetcode.com/problems/subtree-of-another-tree/)

If node value is the same, then call `isSubtree`.

```
class Solution:
    def isSubtree(self, root: Optional[TreeNode], subRoot: Optional[TreeNode]) -> bool:
        
        def isSameTree(p: Optional[TreeNode], q: Optional[TreeNode]) -> bool:
            if p and q:
                return p.val == q.val and isSameTree(p.left,q.left) and isSameTree(p.right,q.right)
            if not p and not q:
                return True
            return False
        
        if root and subRoot:
            if root.val == subRoot.val:
                if isSameTree(root, subRoot) == True:
                    return True
            else:
                return self.isSubtree(root.left, subRoot) or self.isSubtree(root.right, subRoot)
        return root is subRoot
```
