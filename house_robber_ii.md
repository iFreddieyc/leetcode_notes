# 213. House Robber II
[Link to the problem](https://leetcode.com/problems/house-robber-ii/)

This problem is related to [House Robber](https://leetcode.com/problems/house-robber/). 
The new constraint is that the houses are in circle now, meaning that house 0 and house n-1 cannot be robbed at the same time.

**Dynamic Programming** can still be used for this problem, similar to House Robber.

Since the first house and last house cannot be robbed at the same time, we can split the problem into two cases:
1. Rob the first house and don't rob the last house. The problem becomes `rob(nums[:-1])`.
2. Don't rob the first house and rob the last house. The problem becomes `rob(nums[1:])`.

## Solution 1:

This method is not too concise, but gets the job done.

Python code:
```
class Solution:
    def rob(self, nums: List[int]) -> int:
        if len(nums) == 1:
            return nums[0]
        dp_with = [0] * len(nums)
        dp_without = [0] * len(nums)
        dp_with[0] = nums[0]
        dp_with[1] = nums[0]
        dp_without[1] = nums[1]
        for i in range(2, len(nums)):
            dp_with[i] = max(dp_with[i-2] + nums[i], dp_with[i-1])
            dp_without[i] = max(dp_without[i-2] + nums[i], dp_without[i-1])
            
        return max(dp_with[-2], dp_without[-1])
```

## Solution 2:

This solution is quite elegant, the link to original post can be found [here](https://leetcode.com/problems/house-robber-ii/discuss/893957/Python-Just-use-House-Robber-twice).

Note that if we are choosing to rob house 0, we cannot rob the house 1. Hence `nums[0] + rob_helper(nums[2:-1]` in the last line.

```
class Solution:
    def rob(self, nums):
        def rob_helper(nums):
            dp1, dp2 = 0, 0
            for num in nums:
                dp1, dp2 = dp2, max(dp1 + num, dp2)          
            return dp2
    
        return max(nums[0] + rob_helper(nums[2:-1]), rob_helper(nums[1:]))
```
