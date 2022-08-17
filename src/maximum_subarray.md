# 53. Maximum Subarray
[Link to the problem](https://leetcode.com/problems/maximum-subarray/)

## Dynamic Programming

For array `[-1, 3, 2, 4, 5]`, the maximum subarray is `[3, 2, 4, 5]` as we shouldn't increase the negative value.
Similarly, if the array is `[-4, 3, -4, 5, 6]`, we should return `[5, 6]` as the previous parts adds up to a negative value.
Therefore, at each index, we should only include the previous array if it adds up to a positive value.

### Solution 1 dynamic programming:
```
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        n = len(nums)
        if n == 1:
            return nums[0]
        dp = [0] * (n+1)
        dp[0] = res = nums[0]
        for i in range(1, n):
            dp[i] = nums[i] if dp[i-1] < 0 else dp[i-1] + nums[i]
            res = dp[i] if dp[i] > res else res
        return res
```
**Time Complexity O(N), Space Complexity O(N)**

We can improve upon solution 1 as we don't need to store some of the dp values if they as negative, since we are returning the sum of a **contiguous** subarray. 

### Solution 2 optimized dynamic programming:
```
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        prev_best = curr_best = nums[0]
        for i in range(1, len(nums)):
            prev_best = max(nums[i], prev_best+nums[i])
            curr_best = max(prev_best, curr_best)
        return curr_best
```
**Time Complexity O(N), Space Complexity O(1)**

In solution 2, we used two values, `prev_best` is the maximum subarray from the left of the current index (contiguous), while `curr_best` is the overall best result. 
At each index, we compare `prev_best + nums[i]` and `nums[i]`. (Checking if prev_best is negative). This variable can replace the dp array from solution 1.

## Divide and Conquer

Note that this solution is not as fast as dynamic programming as  its time complexity is higher, but its an alternative approach to the problem that is useful to know.
For any array, we can split it into 3 parts, left part of array, `nums[mid]` and right part of array. The result can either be from the left part, or the right part, or go through the middle element.
The left and right cases are easy, for the third case, we iterate from mid to its left to find the left maximum subarray, then iterate from mid to its right to find the right maximum subarray.
We then add `left_sum`, `nums[mid]` and `right_sum` together. Finally, we choose the maximum result between 3 cases and return it.

### Solution 3 divide and conquer:
```
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        if not nums:
            return float("-inf")
        if len(nums) == 1:
            return nums[0]
        
        mid = len(nums) // 2
        curr = best_left_sum = best_right_sum = 0
        
        for i in range(mid - 1, -1, -1):
            curr += nums[i]
            best_left_sum = max(best_left_sum, curr)
        
        curr = 0
        for i in range(mid + 1, len(nums)):
            curr += nums[i]
            best_right_sum = max(best_right_sum, curr)
            
        center = best_left_sum + best_right_sum + nums[mid]
        left = self.maxSubArray(nums[:mid])
        right = self.maxSubArray(nums[mid+1:])
        return max(center, left, right)
```
**Time Complexity O(NlogN), Space Complexity O(logN)**
The extra space we use relative to input size is solely occupied by the recursion stack.
