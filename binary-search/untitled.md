---
description: '# easy'
---

# 35. Search Insert Position



{% hint style="info" %}
### Key idea: the condition of jump out of while loop

### 核心： 跳出while循环的关键
{% endhint %}

### Solution 1:

* `while start+1 < end`; `start = mid` or `end  = mid`
* 跳出循环的条件start 和 end 相邻，因此跳出后要判断target和mid是否相等；无法判断此时target与start/end在数轴上的关系，因此要判断很多：
* `target<start, return max(0,start-1)`
* `target>end, return end+1`
* `target == start, return start`
* `target == end, return end`

### Soultion 2:

* `while start <= end; start = mid+1 or end = mid-1`
* 跳出循环的条件是，end和start交叉，即end&lt;start，可能性有两种：`mid=start=end`  =&gt;  `target<mid`  =&gt;  `end=mid-1`，则应该插入的位置为`start`；`mid = start, start+1=end`  =&gt; `target<mid`  =&gt; `end=mid-1`, 则应该插入的位置依然为`start`。

两种方法的时间复杂度一样，但是方法二返回值更简单，死循环也避免了（因为`start=mid+1, end=mid-1`）

### Solution 2 coding:

```python
def searchInsert(nums: List[int], target: int)->int:
    start = 0
    end = len(nums)-1
    while start<=end:
        mid = int((start+end)/2)
        if target == nums[mid]:
            return mid
        elif target < nums[mid]:
            end = mid-1
        else:
            start = mid+1
    return start

```



