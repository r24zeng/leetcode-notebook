---
description: '# Medium'
---

# Divid two integer

{% hint style="info" %}
不难想，但是很难写对。只能用位运算完成。

Find largest `n` such that $$divider*2^n <= remained$$ using Recursive.

Be careful with negative number. Some `bit` manipulation knoledge:

$$d<<i === d*2^i$$ 

$$1<<i === 2^i$$ 

$$x >> 1 === x/2$$ 

$$x >> 1 \text{ then } x << 1 === x$$ 位左移右移可抵消

如果一个数有32 bit，那么最高位就是符号位，比如要判断两个数符号是否相等：

$$x1>>31 \text{  ?=  } x2>>31$$ 
{% endhint %}

{% tabs %}
{% tab title="Python" %}
```python
class Solution:
    def divide(self, dividend: int, divisor: int) -> int:
        # edge case
        Min = -(1<<31)
        Max = (1<<31) - 1
        print(Min, Max)
        if dividend < Min or dividend > Max:
            print("yes")
            return (1<<31) - 1
        if abs(divisor) > abs(dividend):
            return 0
        if divisor == dividend:
            return 1

        result = self.divid(abs(dividend), abs(divisor))
        if (divisor >> 31) != (dividend >> 31):
            result = min(max(-result, Min), Max)
        else:
            result = min(max(result, Min), Max)
            
        return result
        
    
    def divid(self, target, divisor):
        # stop condition
        if divisor > target:
            return 0
        if divisor == target:
            return 1

        # regular case
        i = 0
        x = divisor
        while x < target:
            i = i + 1
            x = divisor << i
            # print(i, x)
        target = target - (x >> 1)
        return (1 << (i-1)) + self.divid(target, divisor)
            
```
{% endtab %}
{% endtabs %}

