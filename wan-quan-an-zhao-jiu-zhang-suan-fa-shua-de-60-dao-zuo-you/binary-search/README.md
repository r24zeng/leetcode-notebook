---
description: '#704. Binary Search (二分查找法原型代)'
---

# I. Binary Search

Recursive is easier to write and understand;

While loop is more complicated to write, but not easy to enter dead loop, and you'll impresive the interviewer because most interviewees prefer recursive. 

If it's too complicated to code with while then use recursive to save time, otherwise use while.

{% hint style="info" %}
### Key point:

* start + 1 &lt; end   （防止死循环）
* mid = start + \(end-start\)/2
* A\[mid\] =, &lt; , &gt;
* A\[start\]  A\[end\]  ? target
{% endhint %}

{% tabs %}
{% tab title="Java" %}
```java
class Solution{
    public int binarySearch(int[] nums, int target){
        int result = -1, start = 0, end = nums.length-1, mid;
        if(num.length == 0){
            return result;
        }    
        while(start+1 < end){
            mid = start + (end - start)/2;
            if(target > nums[mid]){
                start = mid;
            }
            else if(target < nums[mid]){
                end = mid;
            }
            else{
                result = mid;
                break;
            }
        }
        if(target == nums[start]){
            result = start;
        }
        else if(target == nums[end]){
            result = end;
        }
        return result;
    }
}
```
{% endtab %}

{% tab title="Python" %}
```python
class Soultion:
    def binarySearch(nums, target):
        start = 0
        end = len(nums)-1
        if len(nums)==0:
            return -1
            
        while start+1 < end:
            mid = start + (end-start)/2
            if nums[mid]==target:
                return mid
            elif target < nums[mid]:
                end = mid
            else:
                start = mid
        
        if nums[start]==target:
            return start
        elif nums[end]==target:
            return end
        else:
            return -1
```

> 这个方法跳出while循环后，结果是left &lt;= target &lt;= right 或者target &lt; left 或者target &gt; right，并且确保如果数组里有重复的target，一定会被至少保留一个
{% endtab %}

{% tab title="Python\(II\)" %}
```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        left = 0
        right = len(nums) - 1
        while left <= right:
            mid = left + (right - left)//2
            if nums[mid] == target:
                return mid
            elif target > nums[mid]:
                left = mid + 1
            else:
                right = mid - 1
        return -1
```

> 这个方法只要跳出了while循环，结果是不管数组里有多少个重复的target，仅能迅速找到其中的一个，不是很通用
{% endtab %}
{% endtabs %}

Binary search time complexity is $$O(lgN)$$ , space comlexity is $$O(lgN)$$ 

