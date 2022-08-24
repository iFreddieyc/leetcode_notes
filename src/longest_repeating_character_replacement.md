# 424. Longest Repeating Character Replacement
[Link to the problem](https://leetcode.com/problems/longest-repeating-character-replacement/)

The idea is to use **sliding window**.

## Solution 1:

For a window of `n` letters and `k` moves, if the frequency of the most occurred letter inside the window plus `k` is greater or equal to `n`, then the length of the longest repeating character can be `n`. Using this idea, we can solve this problem by keeping a sliding window of [`left`, `right`] while using a dictionary `count` to keep track of letter frequencies in the window.

`max_freq` is used to represent the maximum frequency of any letter in a given window so far. Whenever we move on to a new letter(`right`), we see if the `max_freq` has changed. Since only the new letter could techinally have a count higher than `max_freq`, we update `max_freq` with `max(max_freq, c[s[right]])`. 

If the current window cannot have the longest repeating character, i.e. if the `max_freq + k` is less than the length of the window (`right - left + 1`), then we remove the left most letter from the window and move the left bound of the window. We never have to worry about `max_freq` being changed due to the removal of the leftmost character of the window, because as long as it doesn't increase, we can never find a larger window; and the only way for it to increase would be if the newest letter has a higher count.

In the end, the window's length should be `len(s) - left`.

Python solution 1:
```
class Solution:
    def characterReplacement(self, s: str, k: int) -> int:
        left = max_length = max_freq = 0
        count = collections.Counter()
        for right in range(len(s)):
            count[s[right]] += 1
            max_freq = max(max_freq, count[s[right]])
            if right - left + 1 > max_freq + k:
                count[s[left]] -= 1
                left += 1
        return len(s) - left
```

## Solution 2:

Solution 2 is similar to solution 1 in that they both uses a dictionary to store the counts in the current window. The only difference is that `max_length` is used to keep track of the return value, which might be easier to understand. 

Python Solution 2:
```
class Solution:
    def characterReplacement(self, s: str, k: int) -> int:
        left = max_length = 0
        count = collections.Counter()
        for right in range(len(s)):
            count[s[right]] += 1
            if right - left + 1 <= max(count.values()) + k:
                max_length = max(max_length, right - left + 1)
            else:
                count[s[left]] -= 1
                left += 1
        return max_length
```
