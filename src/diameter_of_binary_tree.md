# 543. Diameter of Binary Tree
[Link to the problem](https://leetcode.com/problems/diameter-of-binary-tree/)

The concept of diameter of a tree seems a bit hard to understand, but essential can be broken down into three situations:
1. The longest path exists purely in the left subtree of root.
2. The longest path exists purely in the right subtree of root.
3. The longest path path through the root node itself.

The first two situations can be easily handled with recursion. 
For the third situation, the longest path should be the from the node with the max depth in left subtree, 
to node, then to the node with the max depth in the right subtree.

Therefore, we can either create a instance variable `self.max_diameter` to keep track of the result, which is probably a better idea,
or return two values instead of one in our recursive helper: `max_diameter` and `max_depth`.

```
class Solution:
    def diameterOfBinaryTree(self, root: Optional[TreeNode]) -> int:
          
        def helper(node):
            if not node:
                return (0, 0)

            l_dia, l_depth = helper(node.left)
            r_dia, r_depth = helper(node.right)

            return (max([l_dia, r_dia, l_depth+r_depth]), 1+max(l_depth, r_depth))
        
        return helper(root)[0]  
```
