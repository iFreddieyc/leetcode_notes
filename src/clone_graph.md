# 133. Clone Graph
[Link to the problem](https://leetcode.com/problems/clone-graph/)

Note that node.val is unique.

Using an iterative BFS, we can traverse the graph. While traversing the graph, we can use a dictionary of node.val -> Node to keep track of the cloned node, and all its neighbors. 

```
from collections import deque
class Solution:
    def cloneGraph(self, node: 'Node') -> 'Node':
        if not node:
            return node
        q = deque([node])
        clones = {node.val: Node(node.val, [])}
        while q:
            cur = q.popleft()
            cur_clone = clones[cur.val]
            for neighbor in cur.neighbors:
                if neighbor.val not in clones:
                    clones[neighbor.val] = Node(neighbor.val, [])
                    q.append(neighbor)
                    
                cur_clone.neighbors.append(clones[neighbor.val])
        return clones[node.val]
```
