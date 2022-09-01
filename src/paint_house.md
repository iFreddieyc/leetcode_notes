# 256. Paint House
[Link to the problem](https://leetcode.com/problems/paint-house/)

This problem can be solved using **dynamic programming**.

Initializing variables `cr`, `cb`, `cg` to the cost of painting the first house red, blue and green, respectively.
At ith iteration, `cr` stores the minimum total cost to paint the ith house red, thus `cr = min(cb, cg) + r`. Same for `cb` and `cg`.

Assign the values simultaneously to avoid using array. Choose the smallest value in the end.

Python code:
```
class Solution:
    def minCost(self, costs: List[List[int]]) -> int:
        n = len(costs)
        cr, cb, cg = costs[0]
        for i in range(1, n):
            r, b, g = costs[i]
            cr, cb, cg = min(cb, cg)+r, min(cr, cg)+b, min(cr, cb)+g
        return min(cr, cg, cb)
```
