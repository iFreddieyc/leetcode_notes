# 424. Longest Repeating Character Replacement
[Link to the problem](https://leetcode.com/problems/longest-repeating-character-replacement/)

The idea is to use **sliding window**.

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
