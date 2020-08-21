---
title: 高数笔记  高数一
date: 2020-08-14 20:59:50
tags: Math
cover:  "/img/c2.jpg"

mathjax: true
---

# 高数一

只挑我感兴趣的随便一记. 重在理解概念

## 微分

**连续** 实际上就是说, 当自变量取某个值时, 函数值存在.并且这个自变量附近的函数值与该点的函数值要差不多...这个附近要多小就多小...

**导数** 要比连续更加严格,所谓"可导必连续, 连续不一定可导"...

求导公式就不说了, so easy..

**光滑曲线** 导数存在且连续, 这样函数处处有切线, 切线随着切点的移动而连续的转动.

**微分** 就是给定函数f(x)的一点x0, 过该点画f(x)切线, 对于一个小的自变量偏移dx, 在区间(x0,x0+dx)内,该切线函数值的增长dy, dy 是 $\Delta f(x)$ 的线性近似

**弧微分** 对应于微分三角形的斜边...且有关系$ds^2=dx^2+dy^2 $,即$ds=\sqrt{1+f'(x)}dx$

**曲率** 曲率与曲率半径互为倒数,曲率以及曲率圆的圆心有具体的计算公式.

**泰勒级数展开** 貌似是物理中最常用的一个公式了,把函数在某点除展开并忽略高阶项

## 积分

### 不定积分

**性质** 线性

**原函数存在定理** 连续函数必有原函数

**第一换元法** 实际上可以理解为导数项把dx约掉了...

$$\int f[\psi(x)]\psi'(x)dx=\int f[\psi(x)]\frac{d\psi(x)}{dx}dx=\int f[\psi(x)]d\psi(x)=\int f[u]du$$

**第二换元法** 跟第一换元法过程相反...

**分部积分法** 也就是导数的乘法公式的逆运算...

**有理函数的积分** 假分式可以利用多项式除法 化为多项式以及真分式的和.
真分式的分子次数小于分母

有理真分式的积分
1.将分式因式分解
2.按照分母将分式写为带系数的最简真分式之和的形式
$$\frac{A}{ax+b} ,\frac{A}{(ax+b)^n},
\frac{Mx+N}{x^2+px+q},\frac{Mx+N}{(x^2+px+q)^n}$$
$x^2+px+q$为二次质因式
3.解出未知系数
4.对各项最简真分式进行积分

实际上还是查积分表比较快...例如:
Table of integrals, series, and products by I.S. Gradshteyn and I.M. Ryzhik (z-lib.org)
用Mathematica更快
目前不是很清楚是不是有的积分只能查表才有结果

### 定积分

**定积分的性质**

1.线性

2.积分区间可加性

3.积分估值

$$m(b-a)\leq\int^b_af(x)dx\leq M(b-a)$$

m和M为积分区间内的最小值和最大值

**积分上限函数及其导数**

$$G'(x)=\frac{d}{dx}\int^x_b f(t)dt=f(x)    (a\leq x \leq b) $$

实际上积分上限函数就是一个原函数(根据导数定义证明)

**微积分基本定理**

由积分上限函数证明

**定积分换元**

注意,使用的换元函数需要在新的积分区间上具有连续导数!
所以只需要注意积分变量的变化,以及换元函数是否有连续导数,
积分的其他部分的只需要带入换元函数即可,记得微分一下dx

**分部积分**

同不定积分,只是每项都有积分上下限

**广义积分**

1.无穷区间上的积分

$$ \int^{+ \infty}_b f(x) dx=\lim_{b \rightarrow+\infty} \int^b_af(x)dx $$


极限收敛,则称为广义积分

2.无界函数的积分

即先当做有界限函数求积分,再令积分限趋近于断点

**广义积分审敛法**

依靠定义判断是否收敛较为困难, 常用法则:
1.比较
2.柯西
3.绝对值
需要可以去查..貌似也没啥用

**$\Gamma$函数**

$$\Gamma(s)=\int^{+\infty}_0x^{s-1}e^{-x}dx(s>0)$$

性质

1.递推公式

$$\Gamma(s)=(s-1)\Gamma (s-1) (s>1)$$
$$\Gamma(n+1)=n!$$

2.余元公式

$$\Gamma(s)\Gamma(1-s)=\frac{\pi}{sin(\pi s)}(0<s<1)$$
3.
$$\int^{+\infty}_0u^t e^{-u^2}du=\frac{1}{2}\Gamma(\frac{1+t}{2})(t>-1)$$

**定积分的应用**
平均值
$$\frac{1}{b-a}\int^b_af(x)dx $$
均方根
$$\sqrt{\frac{1}{b-a}\int^b_af^2(x)dx} $$

# 向量代数与空间解析几何

**三种积**

1.数量积

$$\boldsymbol a \cdot \boldsymbol  b=|a||b|cos(\boldsymbol a,\boldsymbol b)$$

几何意义为a在b上的投影,与b的乘积或者反过来

2.向量积

$$|\boldsymbol a\times\boldsymbol  b|=|a||b|sin(\boldsymbol a,\boldsymbol b)$$

方向与a,b成右手螺旋关系,几何意义为a,b平行四边形面积
不满足交换律,交换变符号

3.混合积(懒得加粗了...)

$$[abc]=(a\times b)\cdot c=|a\times b||c|cos(a\times b,c)$$

几何意义为abc所围平行六面体的体积

$$[a  b  c]=[bca]=[cab]=-[bac]=-[cba]=-[acb]$$

**坐标表示**

点积

$$a\cdot b=a_xb^x$$

叉积

$$
a\times b=\begin{vmatrix}
\boldsymbol i&\boldsymbol j&\boldsymbol k\\
a_x&a_y&a_z\\
b_x&b_y&b_z\\
\end{vmatrix}
$$

混合积

$$
[\boldsymbol a\  \boldsymbol b\ \boldsymbol  c]=\begin{vmatrix}
a_x&a_y&a_z \\
b_x&b_y&b_z \\
c_x&c_y&c_z \\
\end{vmatrix}
$$

混合积的轮换性质由此可以从行列式的性质推出

**曲面方程**

$$F(x,y,z)=0 $$
...
好像没啥好说的

曲面方程可视化请使用Mathematica **ContourPlot3D** 函数..

**平面方程**
 
貌似也没啥好说的..

好了 高数一 到此结束 内容不多