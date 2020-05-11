---
description: '# Easy'
---

# \# Recover rotated sorted array

{% hint style="info" %}
Three steps rotation\(三步翻转法\)
{% endhint %}

### Solution:

Exmple: `[4, 5, 1, 2, 3] --> [1, 2, 3, 4, 5]`

1. split: `[4, 5]` and `[1, 2, 3]`
2. rotate: `[5, 4]` and `[3, 2, 1]`  --&gt;  `[5, 4, 3, 2, 1]`
3. rotate again: `[1, 2, 3, 4, 5]`

Time complexity = $$O(n)$$ , **space complexity =** $$O(1)$$ ****

