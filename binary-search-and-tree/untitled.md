---
description: '# Medium'
---

# 287. Find the Duplicate Number

{% hint style="info" %}
特别难想到。

**key: Floyd's Tortoise and Hare \(Cycle Detection\)**

Very similar to \#142 [Linked List Cycle II](https://leetcode.com/problems/linked-list-cycle-ii/solution/)
{% endhint %}

{% tabs %}
{% tab title="Python" %}
```python
class Solution:
    def findDuplicate(self, nums: List[int]) -> int:
        # while nums[nums[0]] != nums[0]:
        #     nums[nums[0]], nums[0] = nums[0], nums[nums[0]]
        # return nums[0]
        
        # phase 1
        slow = nums[0]
        fast = nums[0]
        while True:
            slow = nums[slow]
            fast = nums[nums[fast]]
            if slow == fast:
                break
                
        slow = nums[0]
        while slow != fast:
            slow = nums[slow]
            fast = nums[fast]
            
        return fastp
```

Time complexity = $$O(n)$$ , space complexity = $$O(1)$$ 
{% endtab %}

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}

