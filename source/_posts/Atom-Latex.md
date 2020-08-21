---
title: 使用 Atom 写 Latex
date: 2020-08-14 21:01:52
tags: Linux & Tools
cover:  "/img/c8.jpg"
---

环境: ubuntu18.04

## 安装
#### 1.Texlive
终端输入

```bash
sudo apt-get install texlive-full
```
#### 2.Atom插件

首先，打开atom设置的扩展界面，点击``` 编辑->Preferences->扩展 ```搜索以下三个插件并安装：

**language-latex**
**pdf-view**
**latex**


## 配置使用

在latex插件的设置里```Opener```选项，设置为```pdf-preview```


按理来说,这时候应该就可以了，在Atom里的.tex文件编辑界面，按```control+alt+b```就可运行并预览编译好的pdf，其他快捷键可以在latex插件的设置里找到。

但是我遇到了一些问题

## 可能遇到的问题

#### 1.与虚拟键盘冲突
按```control+alt+b```屏幕出现了虚拟键盘，弄了半天，发现键盘貌似不能关掉，否则搜狗输入法的选词板会显示不出来。
所以就把atom的快捷键改了：
在atom```编辑->Preferences->快捷键绑定```界面点击```用户键盘映射```打开```keymap.cson```文件，输入：

```
'atom-text-editor[data-grammar~="latex"]':
  'f5': 'latex:build'
  'f6': 'latex:sync'
  'f7': 'latex:clean'
```
其中我把F5，F6，F7键设置了快捷键，可以自行更改。注意有缩进，去掉缩进会出错！最后保存并重启一下atom。现在，就可以用F5编译预览，F7清除编译文件,F6 sync不是很清楚是干吗用的。。。


#### 2.中文包ctex编译错误

这个很简单，在插件latex的设置里，把```Engine```选项选择```xelatex```即可

## 现在，你应该可以使用atom来编译latex文件了！

## 一些优点

**1**.语法主题和UI主题可以比较随意的更换,看起来更加赏心悦目

**2**.文件目录结构比texstudio要清晰!

**3** 相比texstudio，atom更加简洁，pdf预览界面更大更好一些

**4**.点击右侧预览的pdf可以定位到左侧的latex代码中相应的位置! 超实用! texstudio
貌似没有这个 功能
