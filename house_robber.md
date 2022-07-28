# 198. House Robber
[Link to the problem](https://leetcode.com/problems/house-robber/)

The idea is to use **dynamic programming**.

Subproblem:

`dp[i]` is the maximum amount of money the robber can rob for houses 0 through `i`.

Base case:

`dp[0]` is `nums[0]`, since there is only one house.
`dp[1]` is maximum between `nums[0]` and `nums[1]`, since we cannot rob both houses.

Recurrence relation:

`dp[i]` can either include the current house, i.e. `dp[i-2] + nums[i]`, or doesn't include the current house, i.e. `dp[i-1]`. Pick the maximum between these two.

Python code:
```
class Solution:
    def rob(self, nums: List[int]) -> int:
        if len(nums) == 1:
            return nums[0]
        dp = [0] * len(nums)
        dp[0] = nums[0]
        dp[1] = max(nums[0], nums[1])
        for i in range(2, len(nums)):
            dp[i] = max(dp[i-1], nums[i]+dp[i-2])
        return dp[-1]
```
