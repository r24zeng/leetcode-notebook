---
description: '# Easy'
---

# Two Sum III - Data structure design

{% hint style="info" %}
题意：设计一个数据结构，能完成add\(number\)和find\(target\)两个函数。find\(target\) 如果能找到一对数字之和等于target，返回True，否则返回False.

eg1: add\(3\);  add\(5\);  add\(7\);  find\(4\)-&gt;true;  find\(7\)-&gt;false

eg2: add\(3\);  add\(1\);  add\(2\);  find\(3\)-&gt;true; find\(6\)-&gt;false

Key idea: hashMap = {number: count}, if \(target-currentValue\) exists in hasMap, then True.
{% endhint %}

```python
class solution:
    def __inint__(self):
        self.hashMap = {}
        
    def add(self, number):
        if number in self.hashMap:
            self.hashMap[number] += 1
        else:
            self.hashMap[number] = 1
            
    def find(self, value):
        for key, value in self.hashMap:
            t = value - key
            if (t != key and t in self.hashMap) or (t == key and value > 1):
                return True
        return False
```

{% hint style="danger" %}
一定别忘了find\(\)有两种情况，一种是两个相同的值相加得到目标（\[1, 2, 1, 4\], target = 2），另一种是两个不同的值相加得到目标（\[1, 2, 1, 4\], target = 3）.
{% endhint %}



