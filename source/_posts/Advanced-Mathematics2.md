---
title: 高数笔记  高数二
date: 2020-08-20 23:28:30
tags: Math
cover:  "/img/c3.jpg"
mathjax: true
---

# 高数二


# 多元函数微分

1.高阶混合偏导数在连续的条件下与求导次序无关

2.偏导数

实际上单变量函数的导数是偏微分的特殊形式,导数(除了方向导数),都需要依附坐标轴:

$$lim_{\Delta x_j\rightarrow0}\frac{f(x_1,...,x_j+\Delta x_j,...,x_n)-f(x_1,...,x_j,...,x_n)}{\Delta x_j}=\sum_{i=1}^n \partial_{x_j}f\partial_{x_i}x_j $$

如果各个坐标独立也就是$\partial_{x_i}x_j=\delta_{ij}$,那么,就是偏导数定义,如果不独立,那么就相当于复合函数求偏导的定义

全微分是所有变量同时变化导致的因变量的总体变化的线性近似(无限接近目标点时微分与函数总体变化趋于一致):
$$df(x_1,...,x_i,...,x_n)=\sum_{i=1}^n \partial_{x_i}fdx_i $$


**复合函数全微分**
1.链式法则
$$ \partial_{x}f(u_0,u_1,...,u_n) =\sum_i^n\partial_{u_i}f \partial_xu_i$$

2.全微分形式不变

**隐函数求导**

光滑函数$F(x,y)$构成的方程$F(x,y)=0$, 隐函数$y=f(x)$可以通过方程两边求x的导数得到:
$$\frac{dy}{dx}=-\frac{F_x(x,y)}{F_y(x,y)}$$
更多元的情况类似

方程组确定的隐函数类似,具体可再重新查阅

**方向导数与梯度**


### 未完待续...
