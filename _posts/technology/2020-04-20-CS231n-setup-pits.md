---
title: CS231n环境搭建踩坑记录
tags: 计算机视觉
image: https://i.loli.net/2020/04/20/oD6A2ZWvNkbdV8a.png
description: CS231n 环境搭建的踩坑记录
---

**1. 跳转到assignment1文件夹**

在working locally的Installing packages这一栏，教程指引我们要先在命令行窗口中激活刚创建的cs231n环境，然后执行`cd assignment1`。这里的*assignment1* 文件夹其实包含在*assignment1_jupyter.zip* （或*assignment1_colab.zip* ）文件中，解压后把*assignment1* 文件夹放在自己喜欢的路径下即可，*requirements.txt* 文件也在里面。

**2. 下载CIFAR-10图片库**

教程中的`./get_datasets.sh`指令在linux系统下执行没问题，但在windows系统下执行需要安装*git* 。很多同学在趟过第一个坑后会发现执行完`get_datasets.sh`指令，一个小黑窗一闪而过就没了，图片库根本没有下载下来，这里并非网络问题，在*git bash* 命令行窗口中执行`sh get_datasets.sh`指令后就会发现，原来是`wget`[^wget]命令不存在。那么我们要做的就是在windows系统下安装该命令。

首先去[这里下载][1]安装包，然后添加环境变量`GNU_HOME=C:\Program Files (x86)\GnuWin32`这里的路径是默认安装路径，你也可以改为自定义安装路径。最后在*path* 中添加`%GNU_HOME%\bin`。

搞定后就可以成功下载图片库了，发布该博文时，图片库的大小为177MB。

[^wget]: linux操作系统命令

[1]: https://jaist.dl.sourceforge.net/project/gnuwin32/wget/1.11.4-1/wget-1.11.4-1-setup.exe
