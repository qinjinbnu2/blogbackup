---
title: Hexo 博客写作
date: 2020-08-14 16:43:35
tags: Blog
cover:  "/img/c4.jpg"
mathjax: true
---

## hexo 写作初步


### 高亮

```Mathematica 测试高亮 https://www.wolfram.com Wolfram 网站
Plot[Sin[x],{x,0,3}]
```

### 公式
需要在主题.yml 中设置mathjax  enable为true 如果你没有设置 per_page 为true
那么还需要在front-matter 中打开mathjax  即 'mathjax: true'
$$\int^b_a f(x) dx$$
双括号要加空格
$$\frac{1}{ {(2\pi)}^\frac{D}{2} }$$

$$x_i$$

### 表格
 | 位运算     | 符号   | 计算             |
| ---------- | ------ | ---------------- |
| 按位与     | &      | 相同为1，不同为0 |
| 按位或     | &#124;         | 有1则1           |
| 按位异或   | ^      | 相同为0，不同位1 |
| 按位取反   | ~      |                  |
| 左移       | <<     | 相当于乘以2^n^   |
| 右移       | `>>`   | 相当于除以2^n^   |
| 无符号右移 | `>>>`  |                  |


持续更新中...
