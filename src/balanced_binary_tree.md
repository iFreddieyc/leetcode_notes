# 110. Balanced Binary Tree
[Link to the problem](https://leetcode.com/problems/balanced-binary-tree/)

Use recursion to return heights, once a subtree is unbalanced, return -1 for all recursive calls from that point.

```
class Solution:
    def isBalanced(self, root: Optional[TreeNode]) -> bool:
        def height(node):
            if not node:
                return 0
            l = height(node.left)
            r = height(node.right)
            if l == -1 or r == -1 or abs(r-l) > 1:
                return -1
            return max(r,l)+1
        return False if height(root) == -1 else True
```
