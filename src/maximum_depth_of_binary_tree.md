# 104. Maximum Depth of Binary Tree
[Link to the problem](https://leetcode.com/problems/maximum-depth-of-binary-tree/)

### Recursive Solution

Recursion seems really easy here, one thing to keep in mind is choosing 0 or 1 for the base case.
I find that choosing 0 for the base case if node is `None` is easier because no need to check if left or right children exist.

```
class Solution:
    def maxDepth(self, root: Optional[TreeNode]) -> int:
        if not root:
            return 0
        return 1+max(self.maxDepth(root.left), self.maxDepth(root.right))
```

### Iterative Solution using BFS

Note that for level-order-traversal, need to create a double-ended queue and iterate all nodes in one level. 
To do so, we need to see the `size` of the queue at the beginning of the while loop, and pop out `size` nodes, which are all nodes at that level.

```
class Solution:
    def maxDepth(self, root: Optional[TreeNode]) -> int:
        if not root:
            return 0
        depth = 0
        queue = collections.deque([root])
        while queue:
            for i in range(len(queue)):
                node = queue.popleft()
                if node.left:
                    queue.append(node.left)
                if node.right:
                    queue.append(node.right)
            depth += 1
        return depth
```
