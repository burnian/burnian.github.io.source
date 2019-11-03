---
title: （一）从零开始搭建个人静态博客网站
tags: 个人网站 Jekyll
image: https://wx4.sinaimg.cn/mw690/6fbea8e9ly1g8kv72h9caj20fk0fk41s.jpg
description: 从零开始的起始篇，该篇主要介绍环境的搭建步骤：1.下载带 Devkit 的 Ruby 安装包；2.安装 Ruby；3.安装 Jekyll 和 bundler；4.创建你的第一个 jekyll 默认网站项目并运行。
---
* TOC
{:toc}

## 简单的开始

### 1.下载带 Devkit 的 Ruby[^Ruby] 安装包

网上搜一下就能找到下载链接，这里以 Windows 操作系统为例，可以去[RubyInstaller for Windows][1]官网下载对应安装包。

![RubyInstaller](https://wx4.sinaimg.cn/mw690/6fbea8e9ly1g8kv8ts9k6j20cf07adfz.jpg)

根据自己的操作系统情况选择对应的最新安装包下载即可，包名中的 Devkit 表示该安装包会自带许多 gem[^gem]，其中就包括了 RubyGems[^RubyGems] 以及很多 Jekyll[^Jekyll] 相关的组件，方便我们接下来的网站开发。

由于官网的下载链接对于国内的小伙伴而言速度很迷，所以下载不了的小伙伴可以尝试下面的链接（都是64位安装包）：

* [CSDN][2]的源，不差积分的小伙伴可以随意取用
* [百度网盘][3]的源，提取码: exc7

### 2.安装

各种下一步，安装好后打开 Windows 控制台[^console]，输入`ruby -v`，若出现下图所示内容（版本号不同没关系）则证明安装成功。

![setup-success](https://wx2.sinaimg.cn/mw690/6fbea8e9ly1g8kvgub7enj20cp014myv.jpg)

### 3.安装 Jekyll 和 bundler

在控制台界面输入`gem install jekyll bundler`，其中 bundler 是一个辅助工具，它会根据你项目根目录下的 Gemfile 文件中的指定记录来安装 gem，并能确保用户在不同的环境下运行的都是同一个版本的 Jekyll 和 Jekyll plugin （Jekyll插件）。

### 4.创建你的第一个 jekyll 默认网站项目并运行

在控制台界面输入`jekyll new myblog`，其中 myblog 指代你的项目名称。然后输入`cd myblog`切换到 myblog 文件夹，最后输入`bundle exec jekyll serve`，Jekyll就会在 myblog 文件夹下生成一个目标网站文件夹 _site ，并在本地开启一个 Jekyll 服务器，于是用户就可以通过地址 [http://localhost:4000][7] 来访问自己的网站了。

## 后记

Congratulations! 到这一步，我们就已经正式开启了基于 Jekyll 引擎的个人静态网站搭建之旅，在经过后面的认真学习之后我们将能够制作出让自己惊叹的个人网站，肆意体验在互联网的汪洋大海中表达自己、吸引他人的乐趣。

下一章，我们将学习如何把本地代码部署到网站托管平台上去，让他人也能访问我们的网站。

So what are we waiting for? Let's go for it!

[^Ruby]: [Ruby][4]是一门开源的面向对象动态脚本语言。它由日本人[松本行弘][5]（まつもとゆきひろ/Yukihiro Matsumoto）创建于1993年。
[^gem]: 一个 gem 就是一个 Ruby 语言的组件包。
[^RubyGems]: [RubyGems][6]是一个 Ruby 组件包的管理器，用户可以在控制台通过`gem install`命令来安装所需的组件。
[^Jekyll]: Jekyll 简单来说就是支撑我们网站的引擎，后面会详细讲，这里不展开。
[^console]: 按下`win+R`，然后输入`cmd`回车。

[1]: https://rubyinstaller.org/downloads/
[2]: https://download.csdn.net/download/burnian/11929849
[3]: https://pan.baidu.com/s/17x-3ZNJ8N1UgdmvsbnyinQ
[4]: https://www.ruby-lang.org/zh_cn/
[5]: https://baike.baidu.com/item/%E6%9D%BE%E6%9C%AC%E8%A1%8C%E5%BC%98/539636?fr=aladdin
[6]: https://rubygems.org/
[7]: http://localhost:4000