title: 学习语言表达数学模型
date: 2015-06-21 22:20:35
categories: python
tags: 数学模型
---
           
用大蟒蛇表达数学模型?
<!--more-->

数学，貌似从小就开始接触了吧。语言，接触有三四年了吧。但是，现在想把一个数学模型表达出来，貌似都感觉还是有点困难。
先玩玩简单的吧,搞个球面(貌似matlab有个直接的函数可以画出来?但是事实还是不知道是如何画出来的，并且更喜欢大蟒蛇些…).

哦，球面模型，忘了呢。得赶紧复习复习数学去了,66666……
球面的数学模型
{% img http://7xjv8u.com1.z0.glb.clouddn.com/qiumian/qiumain.png 800 200 球面数学模型 %}
以坐标原点为球心，半径为R的球面的参数方程:
{% img http://7xjv8u.com1.z0.glb.clouddn.com/qiumian/bf096b63f6246b60f60cc951ebf81a4c510fa291.jpg %}
（0≤θ≤2π，0≤φ≤π）
这东西，高中的时候就学了.但是，用语言搞出来，好像不知道了…

额，上面的表达式也都还算好吧。就是角度问题。用个范围，然后还是变化得。这个不好搞呢。
好吧。其实最近在看python科学计算。
np.linspace(a,b,n) —> 把a到b划分成n个等分……
然后，np.outer还有这么个东西…
a = [a0, a1, …, aM]
b = [b0, b1, …, bM]
np.outer(a,b) —> [[a0b0, a0b1,…,a0bM], …, [aMb0, …, aM * bM]]

积分计算还scipy里面有 quad， dblquad, tplquad等，暂时用不到.
两个角度就表示成了
np.linspace(0, 2*np.pi, 100)
np.linspace(0, np.pi, 100)
然后表示出x,y,z
最后，画图吧。
```python
#!/usr/bin/env python
#encoding:utf-8

from mpl_toolkits.mplot3d import Axes3D
import matplotlib.pyplot as plt
import numpy as np

########### 半径与角度 ###############
R = 10
u = np.linspace(0, 2*np.pi, 100)  
v = np.linspace(0, np.pi, 100)

###########  表示x,y,z  ###############
x = R * np.outer(np.cos(u), np.sin(v))
y = R * np.outer(np.sin(u), np.sin(v)) 
z = R * np.outer(np.size(u), np.cos(v)) 

###########   画出来  ################
fig = plt.figure()
ax  = Axes3D(fig)
ax.plot_surface(x,y,z)
plt.show()
```

最后的结果

{% img http://7xjv8u.com1.z0.glb.clouddn.com/qiumian/2015-07-12-yuan.png 800 400 %}

