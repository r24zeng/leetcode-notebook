---
description: '# Medium'
---

# 3. Longest Substring Without Repeating Characters

{% hint style="info" %}
Two methods:

1. Dynamic Programming
2. Sliding Window
{% endhint %}

### Solution 1:

Know the longest length of first `i` chars, then the longest length of first `i+1` chars is max\(`longest[i]`, longest length from `i+1` to `0`\).

```python
class Solution(object):
    def lengthOfLongestSubstring(self, s):
        """
        :type s: str
        :rtype: int
        """
        # edge case
        if len(s) == 0:
            return 0
        
        # initialize
        longest = 1
        
        # compute based on last element
        for i in range(1, len(s)):
            sub = []
            for j in reversed(range(0, i+1)):
                if s[j] in sub:
                    break
                else:
                    sub.append(s[j])
            longest = max(len(sub), longest)
            
        return longest
```

Time complexity = $$O(n^2)$$ , space complexity = $$O(n)$$ .效率很低

### Solution 2:

Keep a sliding window by left and right pointers, left pointer doesn't move, right pointer moves. If s\[right\] is duplicated in sliding window, s\[left\] is removed from the set pf sliding window and left pointer moves one step, repeat this step until s\[right\] is not duplicated in sliding window. At the same time, record the longest length of the sliding window.

```python
class Solution(object):
    def lengthOfLongestSubstring(self, s):
        """
        :type s: str
        :rtype: int
        """
        left = 0
        window = set()
        result = 0
        for right in range(len(s)):
            while s[right] in window:
                window.remove(s[left])
                left += 1
            window.add(s[right])
            result = max(result, right-left+1)
        return result
```

Time complexity = $$O(n)$$ , space complexity = $$O(n)$$ .

