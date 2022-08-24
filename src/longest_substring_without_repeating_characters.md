# 3. Longest Substring Without Repeating Characters
[Link to the problem](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

The idea is to use **sliding window**. 

Create three variables: `left`, `right` and `max_length`. 
`left` means left boundary of the window, `right` means right boundary of the window, and `max_length` means the length of the current longest substring.
Also create a dictionary `last_seen` to use the characters as keys and their last seen or latest position as values.

Initialize `left` and `max_length` to -1 and 0.
Iterate string from left to right using `right` as index.

In each iteration:

If the current character `s[right]` is in `last_seen` and its value is greater than `left`, this means that we can't add `s[right]` to the current sliding window without removing its duplicate first.
Therefore, we move `left` to `last_seen[s[right]]` (its last seen position before `right`), thus removing the duplicate(old copy) from the sliding window. Update `last_seen[s[right]]` to `right`, and calculate `max_length` to see if it needs to be updated.

Exclusive left case:
```
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        if not s:
            return 0
        last_seen = {}
        l = -1
        max_length = 0
        for r in range(len(s)):
            if s[r] in last_seen and last_seen[s[r]] > l:
                l = last_seen[s[r]]
            last_seen[s[r]] = r
            max_length = max(max_length, r-l)
        return max_length
```

We also need to consider whether `left` and `right` are inclusive or exclusive. If `left` is exclusive, then the window is from `right` to `left+1`, and its length would be `right-(left+1)+1 = right - left`. This way when we encounter a new character, we have to check if its last seen position is **greater than `left`**. We would also need to initialize `left` to -1, instead of zero. The above solution is for this exclusive left case.

Inclusive left case:
```
from collections import Counter
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        last_seen = {}
        l, best = 0, 0
        for r, char in enumerate(s, start=0):
            if char in last_seen and last_seen[char] >= l:
                l = last_seen[char]+1
            last_seen[char] = r
            best = max(best, r - l + 1)
        return best
```
