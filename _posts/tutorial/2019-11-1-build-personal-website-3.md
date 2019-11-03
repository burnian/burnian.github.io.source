---
title: （三）从零开始搭建个人静态博客网站
tags: 个人网站 Jekyll
image: https://wx4.sinaimg.cn/mw690/6fbea8e9ly1g8kv72h9caj20fk0fk41s.jpg
description: 这一章我们将展开学习利用 Jekyll + GitHub Pages 搭建个人网站时会频繁用到的相关知识。
---
* TOC
{:toc}

## 楔子

这一章我们将展开学习利用 Jekyll + GitHub Pages 搭建个人网站时会频繁用到的相关知识。

## Ruby 是什么

[Ruby][1]是一门开源的面向对象动态编程语言。它由日本人[松本行弘][2]（まつもとゆきひろ/Yukihiro Matsumoto）创建于1993年。类似于 Perl 语言，Ruby 擅长文本处理。同 Smalltalk 语言一样，Ruby 中的任何符号都是 object（对象），并且 Ruby 有 blocks（代码块），iterators（迭代器），meta-classes（元类）等很好的概念。你可以用 Ruby 来写服务器，带原型的实验以及每日的编程任务。作为一种完全集成的面向对象语言，Ruby具有良好的伸缩性。以下是 Ruby 的特点：

* 简单的语法
* 基础的面向对象特征（支持类，方法，对象等等）
* 特殊的面向对象特征（支持 mixins[^mixins]，singleton methods[^singleton-methods]，renaming[^renaming] 等等）
* 操作符重载
* 异常处理
* 迭代器和闭包
* 垃圾自动回收
* 动态加载（依赖架构）
* 高可移植性（可在各种操作系统下运行，如：Unices、Windows、DOS、macOS、OS/2、Amiga 等）

只有当学习深入到自定义插件时我们才会涉及 Ruby 语言编程，所以这里只要求对 Ruby 有个大概的了解即可，不再展开，感兴趣的同学可以去[rubylearning.com][3]自学。

## gem 是什么

广义地说，一个 gem 就是一个 Ruby 语言写的组件程序包。具体来说，每个 gem 都有一个包名，版本和平台，某些 gem 还会提供命令行工具来帮助你加速任务和任务自动化。例如：`rake`版本为0.8.7（2009年5月），平台是 Ruby，这意味着任何一个可以运行 Ruby 语言的平台都可以运行`rake`。

一个 gem 由以下部分构成：

* 代码（通常包括可执行文件，测试代码和支持工具）
* 文档（通常包括嵌入在代码中的注释和 README 文件，当你安装了该 gem 之后就会自动为你生成文档）
* gemspec（即 gem 的相关信息。通常包括 gem 所含的文件，测试信息，平台，版本号以及作者的邮箱和名字)

## RubyGems 是什么

[RubyGems][4]是一个 gem 的管理器，它允许你在你的系统上简单地下载、安装和使用 Ruby 软件包，用户可以在控制台通过`gem`后跟一系列指令符来对远端的 gem 进行下载安装等操作，其作用类似于 JavaScript 的`npm`和 python 的`pip`。

## Jekyll 是什么

Jekyll 是一种用 Ruby 语言开发的静态网页生成系统，我们的网站就是由它生成的。Jekyll 可以识别的文件中既能有语句又能有HTML（称为超文本标记语言，是一种标识性的语言。文件后缀通常为.html）语句。

## Markdown 是什么

Markdown 是一种可以使用普通文本编辑器编写的标记语言，通过简单的标记语法，它可以使普通文本内容具有一定的格式，文件后缀通常为.md或.markdown。其使用方法参见`https://www.zybuluo.com/mdeditor`

![repo-create](https://help.github.com/assets/images/help/repository/repo-create.png)

## 后记

Congratulations! 到这一步，我们就已经学会了发布网站的整个流程，至于 git 的相关内容则不在本教程的讨论范围之内，同学们需自行学习，之后如果有空，我也可能专门出一个 git 的系列教程。

从下一章开始，我们将从基础知识入手，一步步学习如何润色我们的网站，并最终做出炫酷的效果。

[^mixins]: 混入，就是定义一部分公共的方法或者计算属性，然后混入到各个组件中使用，方便管理与统一修改。
[^singleton-methods]: 单例方法，即同一个方法多处引用，只保存了单个该方法的实例，而不是每引用一次便新建一个实例。
[^renaming]: 重命名。

[1]: https://www.ruby-lang.org/en/
[2]: https://baike.baidu.com/item/%E6%9D%BE%E6%9C%AC%E8%A1%8C%E5%BC%98/539636?fr=aladdin
[3]: http://rubylearning.com/satishtalim/tutorial.html
[4]: https://guides.rubygems.org