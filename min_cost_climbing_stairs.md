# 746. Min Cost Climbing Stairs
[Link to the problem](https://leetcode.com/problems/min-cost-climbing-stairs/)

The idea is to use **dynamic programming**.

The only slightly difficult thing about this problem is to understand the problem. 
Understand only when u take a step from a step of stair you pay its cost, instead of paying the cost when u land on that step of stair.
Also, the final destination also counts as a step, despite it has no cost nor does it consist in the array.

Python code:
```
class Solution:
    def minCostClimbingStairs(self, cost: List[int]) -> int:
        dp = [0] * (len(cost) + 1)
        for i in range(len(cost) + 1):
            if i <= 1:
                continue
            dp[i] = min(dp[i-2] + cost[i-2], dp[i-1] + cost[i-1])
        return dp[-1]
```
