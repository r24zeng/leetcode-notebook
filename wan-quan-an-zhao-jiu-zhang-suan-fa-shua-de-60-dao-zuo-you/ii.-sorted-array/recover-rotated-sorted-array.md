---
description: '# Easy'
---

# \# Recover rotated sorted array

{% hint style="success" %}
Three steps rotation\(三步翻转法\)
{% endhint %}

### Solution:

Exmple: `[4, 5, 1, 2, 3] --> [1, 2, 3, 4, 5]`

1. split: `[4, 5]` and `[1, 2, 3]`
2. rotate: `[5, 4]` and `[3, 2, 1]`  --&gt;  `[5, 4, 3, 2, 1]`
3. rotate again: `[1, 2, 3, 4, 5]`

Time complexity = $$O(n)$$ , **space complexity =** $$O(1)$$ ****\# recover rotated sorted array

```python
def recoverArray(nums):
    # consider edge case
    left = 0
    right = len(nums) - 1

    # find pivot
    while left + 1 < right:
        mid = left + (right - left)//2
        if nums[mid] < nums[left]:
            right = mid
        else:
            left = mid
    print("pivot is: ", right)

    # right is the pivot
    # rotate two parts
    for i in range(0, right//2):
        x = nums[i]
        nums[i] = nums[right-1-i]
        nums[right-1-i] = x

    for i in range(right, (len(nums)+right)//2):
        x = nums[i]
        nums[i] = nums[-1-i+right]
        nums[-1-i+right] = x

    # rotate whole array
    for i in range(0, len(nums)//2):
        x = nums[i]
        nums[i] = nums[-1-i]
        nums[-1-i] = x
```

