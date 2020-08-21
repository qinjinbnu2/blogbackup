---
title: Ubuntu 缺失字体安装
date: 2020-08-14 21:00:46
tags: Linux & Tools
cover:  "/img/c9.jpg"
---

**1.**
找一台Windows电脑,进入```C:\Windows\Fonts```,你需要的字体文件都在里面.
如果你安装的是双系统,就可以直接把里面的文件拷到ubuntu里.例如,如果需要微软雅黑,
就要拷贝```msyh.ttc,msyhl.ttc,msyhbd.ttc```三个文件.

**2.**

把字体文件放到ubuntu的fonts文件夹里,你可以新建一个myfonts文件夹

```
cd /usr/share/fonts
sudo mkdir myfonts
sudo mv /你存放字体文件的路径/*.ttc /usr/share/fonts/myfonts
```

**3.**

记录安装新字体

```
sudo mkfontscale
sudo mkfontdir
sudo fc -cache -fv
```

现在你应该可以在ubuntu使用新字体了,可以打开wps看看是否安装成功.
