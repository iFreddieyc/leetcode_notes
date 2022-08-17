# 1647. Minimum Deletions to Make Character Frequencies Unique
[Link to the problem](https://leetcode.com/problems/minimum-deletions-to-make-character-frequencies-unique/)

Approach 1: Decrement Each Duplicate Until it is Unique

Solution:
```
class Solution:
    def minDeletions(self, s: str) -> int:
        freqs = [0] * 26
        for c in s:
            freqs[ord(c)-ord('a')] += 1
            
        deletions = 0
        seen = {}
        for c in freqs:
            while True and c > 0:
                if c not in seen:
                    seen[c] = True
                    break
                else:
                    c -= 1
                    deletions += 1
        return deletions
```
