---
description: Back Tracing Algorithm
---

# IV. Permutations and Subsets

### Subsets coding:

```python
class Solution:
    def helper(self, nums, index, level, result):
        # stop condition
        if index == len(nums):
            return 
        
        # regular case
        for i in range (index, len(nums)):
            level.append(nums[i])
            result.append(level[:])
            self.helper(nums, i+1, level, result)
            level.pop()
        
    
    def subsets(self, nums: List[int]) -> List[List[int]]:
        # edge case
        result = []
        result.append([])
        if len(nums) == 0:
            return nums
        
        # regular case
        level = []
        self.helper(nums, 0, level, result)
        return result
```

### Permutation:

```python
class Solution:
    def helper(self, nums, level, result, index):
        # stop condition
        if len(level) == len(nums):
            result.append(level[:])
            return result
        
        # regular case
        for i in range (0, len(nums)):
            if i != index and nums[i] == nums[i-1]:
                continue
            level.append(nums[i])
            self.helper(nums, level, result, index)
            level.pop()
        
    
    def subsets(self, nums: List[int]) -> List[List[int]]:
        # edge case
        result = []
        if len(nums) == 0:
            return result
        
        # regular case
        level = []
        self.helper(nums, level, result, 0)
        return result
```

### When using the above methods, think about three questions:

1. `Array.sort()` -- remove duplicates
2. `result.append()` -- when output the result
3. `if (condition): continue` -- skip condition

### Difference between Subsets and Permutation:

The usage of `index`, stop condition in `helper` function, the time of adding levels to result.

### 常见的变形题：

是否能接受重复的元素，是否能接受重复的levels

大多数变型题都是permutation\(排列\)。

