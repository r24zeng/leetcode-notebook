---
description: '# Medium'
---

# 134. Gas Station

{% hint style="info" %}
我们首先要知道能走完整个环的前提是gas的总量要大于cost的总量，这样一定有起点的存在。假设开始设置起点start = 0, 并从这里出发，如果当前的gas值大于cost值，就可以继续前进，此时到下一个站点，剩余的gas加上当前的gas再减去cost，看是否大于0，若大于0，则继续前进。当到达某一站点时，若这个值小于0了，则说明从起点到这个点中间的任何一个点都不能作为起点，则把起点设为下一个点，继续遍历。当遍历完整个环时，当前保存的起点即为所求。代码如下：Python
{% endhint %}

```python
class Solution:
    def canCompleteCircuit(self, gas: List[int], cost: List[int]) -> int:
        start = 0
        s = 0
        total = 0
        for i in range(len(gas)):
            s += gas[i] - cost[i]
            total += gas[i] - cost[i]
            if s < 0:
                start = i + 1
                s = 0
        
        if total < 0:
            return -1
        else:
            return start
```

其实没有很懂到底怎么计算和操作的，题目的例子都没看懂，初始油量怎么来的？

