# 322. Coin Change
[Link to the problem](https://leetcode.com/problems/coin-change/)\

We could use **dynamic programming** to solve this problem.

## Bottom-up DP

Python code:
```
class Solution:
    def coinChange(self, coins: List[int], amount: int) -> int:
        MAX = float("inf")
        dp = [0] + [MAX] * amount
        for i in range(1, amount+1):
            dp[i] = 1 + min([dp[i-c] if i >= c else MAX for c in coins])
        return dp[-1] if dp[-1] != MAX else -1
```
