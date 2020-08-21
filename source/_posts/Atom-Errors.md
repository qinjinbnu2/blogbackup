---
title: Atom 的一个错误修正
date: 2020-08-14 21:02:05
tags: Linux & Tools
cover:  "/img/c6.jpg"
---
# Atom 报错：Cannot load the system dictionary for zh-CN. Checked the following paths for dictionary files

每次打开Atom的时候会报错：
Cannot load the system dictionary for zh-CN. Checked the following paths for dictionary files

在编辑->Preferences>扩展中搜索spell-check 即可找到如下插件
这是一个核心插件，用于拼写检查

{% asset_img AtomErrors1.png [] %}

点击设置，将图中Use Locales 的勾去掉
在下面填入en-US

{% asset_img AtomErrors2.png [] %}

重启一下atom，发现已经没有错误了。

最后发现如果再将这个选项改回来，错误也没有再出现。
