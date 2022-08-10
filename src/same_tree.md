# 100. Same Tree
[Link to the problem](https://leetcode.com/problems/same-tree/)

Recursively check is each subtree is the same. 

```
class Solution:
    def isSameTree(self, p: Optional[TreeNode], q: Optional[TreeNode]) -> bool:
        if p and q:
            return p.val == q.val and self.isSameTree(p.left,q.left) and self.isSameTree(p.right,q.right)
        if not p and not q:
            return True
        return False
```
