# Practice Log

## 08-31-2022
1. [79. Word Search](https://leetcode.com/problems/word-search/) Wrote a dfs solution but exceeds time limit for some test cases, looked at and copied another dfs solution with less time complexity. 
2. [41. First Missing Positive](https://leetcode.com/problems/first-missing-positive/) Attempted
3. [256. Paint House](https://leetcode.com/problems/paint-house/) Revisited
4. [322. Coin Change](https://leetcode.com/problems/coin-change/) Revisited, couldn't remember the solution. 
5. [1746. Maximum Subarray Sum After One Operation](https://leetcode.com/problems/maximum-subarray-sum-after-one-operation/) Looked at and implemented O(n) solution.
6. [1230. Toss Strange Coins](https://leetcode.com/problems/toss-strange-coins/) Looked at and implemented O(n) solution.

## 08-30-2022
1. [42. Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water/) Figured out and wrote two-pointer solution, looked at stack solution, didn't understand DP solution.

## 08-29-2022

1. [152. Maximum Product Subarray](https://leetcode.com/problems/maximum-product-subarray/) Looked at solutions and copied its O(N) DP optimal solution. This problem is really similar to [53. Maximum Subarray](https://leetcode.com/problems/maximum-subarray/).
2. [53. Maximum Subarray](https://leetcode.com/problems/maximum-subarray/) Revisited this question, did well.
## 08-24-2022

1. [3. Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)
Reviewing this question, despite having the right idea, took a bit long to write error free code. Updated the [markdown file](src/longest_substring_without_repeating_characters.md) with inclusive/exclusive left bound solutions and explanations.
2. [424. Longest Repeating Character Replacement](https://leetcode.com/problems/longest-repeating-character-replacement/)
Reviewing this question, have the right idea but forget the meaning of `max_freq` and how to calculate it. Updated the the [markdown file](src/longest_repeating_character_replacement.md) with a further explanation on `max_freq`.
3. [567. Permutation in String](https://leetcode.com/problems/permutation-in-string/) Attempted and finished a O(26n) solution. There was a faster solution at O(n) which is quite easy to understand.

## 08-19-2022

1. [121. Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)
2. [714. Best Time to Buy and Sell Stock with Transaction Fee](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-transaction-fee/)
Not quite sure about this one, need to understand a bit more about `cash` and `hold` and their relationships.

## 08-18-2022

1. [256. Paint House](https://leetcode.com/problems/paint-house/)
Never attempted, looked at [solution](https://leetcode.com/problems/paint-house/discuss/68232/python-clean-and-clear-python-dp-solution) after 10 minutes.
2. [265. Paint House II](https://leetcode.com/problems/paint-house-ii/)
Similar to the last problem, but the optimal solution which is O(nk) is not easy to arrive at. Finished O(nk^2) solution but not the optimal one. 
3. [57. Insert Interval](https://leetcode.com/problems/insert-interval/)
Could use both binary search and linear search for this question. Binary search should be faster in practice, but both upper bound is O(n) because of overhead. Linear search is definitely the harder to mess up approach.
4. [56. Merge Intervals](https://leetcode.com/problems/merge-intervals/)
Similar to last problem, only difference is to use sort.
5. [435. Non-overlapping Intervals](https://leetcode.com/problems/non-overlapping-intervals/)
Several approaches to this question, understood greedy solution but didn't check out other approaches yet.
