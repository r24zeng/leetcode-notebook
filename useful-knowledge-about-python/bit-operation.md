# Bit operation

* n &lt;&lt; 1 向左移位，低位变高位，低位0补齐
* n &gt;&gt; 1 向右移位，高位变低位
* n & 1 得到最低位
* \(n &gt;&gt; 31\) & 1 得到最高位
* \(n & 1\) &lt;&lt; 31 最低位和最高位互换

{% hint style="danger" %}
一个数最多左移或右移31位，然后留下最后一个bit，再移一定是0
{% endhint %}

