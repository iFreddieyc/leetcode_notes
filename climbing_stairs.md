# 70. Climbing Stairs
[Link to the problem](https://leetcode.com/problems/climbing-stairs/)

One of the easier apporaches is **dynamic programming**.

Python code:
```
class Solution:
    def climbStairs(self, n: int) -> int:
        if n == 1 or n == 2:
            return n
        dp = [0] * (n + 1)
        for i in range(n+1):
            if i <= 2:
                dp[i] = i
            else:
                dp[i] = dp[i-1] + dp[i-2]
        return dp[n]
```
