# 226. Invert Binary Tree
[Link to the problem](https://leetcode.com/problems/invert-binary-tree/)

Recursion seems to be the easiest option. One syntactic sugar of python is that you can assign the value of two variables at the same time.

Recursive Solution
```
class Solution:
    def invertTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]: 
        if not root:
            return None
        root.left, root.right = self.invertTree(right), self.invertTree(left)
        return root
```
