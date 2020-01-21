---
description: 二分查找法原型代码
---

# Fundamentation

{% hint style="info" %}
### Key point:

* start + 1 &lt; end   （防止死循环）
* start + \(send-start\)/2
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
class Soultion{
    def binarySearch(nums, target){
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
    }
}
```
{% endtab %}
{% endtabs %}

