# 235. Lowest Common Ancestor of a Binary Search Tree
[Link to the problem](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/)

Since this is a BST, just use its property where left child is less than root and right child is greater than root. 
If two nodes have a LCA, then its value must be between these two nodes. Just traverse the tree in the direction of the two nodes.

```
class Solution:
    def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':
        def helper(node, p, q):
            if p.val <= node.val <= q.val or q.val <= node.val <= p.val:
                return node
            else:
                if p.val < node.val and q.val < node.val:
                    return helper(node.left, p, q)
                else:
                    return helper(node.right, p, q)
        return helper(root, p, q)
```
