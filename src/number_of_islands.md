# 200. Number of Islands
[Link to the problem](https://leetcode.com/problems/number-of-islands/)

This is a graph problem that can be both approached using **DFS/BFS**.

## DFS:

### Solution 1:

This is my own solution, not consise but gets the job done.

Python code

```
class Solution:
    def numIslands(self, grid: List[List[str]]) -> int:
        def DFS_helper(node, visited, grid):
            visited.add(node)
            i, j = node
            for neighbor in [(i-1, j), (i+1, j), (i, j-1), (i, j+1)]:
                if not is_valid(neighbor, grid):
                    continue
                p, q = neighbor
                if neighbor not in visited and grid[p][q] == '1':
                    DFS_helper(neighbor, visited, grid)
        
        def is_valid(node, grid):
            m, n = len(grid), len(grid[0])
            i, j = node
            if i < 0 or i >= m or j < 0 or j >= n:
                return False
            return True
        
        if not grid:
            return 0
        visited = set()
        count = 0
        for i in range(len(grid)):
            for j in range(len(grid[0])):
                if grid[i][j] == '1' and (i,j) not in visited:
                    DFS_helper(((i, j)), visited, grid)
                    count += 1
        return count
```

### Solution 2:

This is a more elegant solution that I found, link to original is [here](https://leetcode.com/problems/number-of-islands/discuss/56340/Python-Simple-DFS-Solution).

```
def numIslands(self, grid):
    if not grid:
        return 0
        
    count = 0
    for i in range(len(grid)):
        for j in range(len(grid[0])):
            if grid[i][j] == '1':
                self.dfs(grid, i, j)
                count += 1
    return count

def dfs(self, grid, i, j):
    if i<0 or j<0 or i>=len(grid) or j>=len(grid[0]) or grid[i][j] != '1':
        return
    grid[i][j] = '#'
    self.dfs(grid, i+1, j)
    self.dfs(grid, i-1, j)
    self.dfs(grid, i, j+1)
    self.dfs(grid, i, j-1)
```
