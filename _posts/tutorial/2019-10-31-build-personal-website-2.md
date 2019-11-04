---
title: （二）从零开始搭建个人静态博客网站
tags: 个人网站 Jekyll
image: https://i.loli.net/2019/11/04/Vk6w24jRNMKpiOf.jpg
description: 这一章我们将要学习的是如何把本地代码部署到网站托管平台GitHub上去。
---
* TOC
{:toc}

## 楔子

这一章我们将要学习的是如何把本地代码部署到网站托管平台上去，在开始讲解部署步骤之前我们需要弄明白两个概念。

### GitHub 是什么

[GitHub][1]是一个开源的托管服务，有点像代码的云。它以各种不同的编程语言托管您的源代码项目，并跟踪每次迭代所做的各种更改。该服务可以通过使用 git[^git] 来完成此操作，本章内容的学习要求读者有一定的 git 基础，理解何为[版本控制][7]、[代码托管][8]等等。

### GitHub Pages 是什么

[GitHub Pages][4]是一个静态网站托管服务，该服务会直接从 GitHub 上的一个库中取出 HTML、CSS 和 JavaScript 等文件，并由用户选择是否要通过一个创建过程来运行这些文件，并最终发布一个网站。点击这个[链接][5]可以查看通过 GitHub Pages 发布的网站实例。我们的网站可以托管在 GitHub 的`github.io`域名或自定义域名下。

## 部署网站

### 1.在 GitHub 账号下创建新库 username.github.io

点击[GitHub][1]链接，注册并登陆自己的 GitHub 账号，点击右上角`+`按钮并选择`New repository`。

![repo-create](https://help.github.com/assets/images/help/repository/repo-create.png)

接下来配置待新建的库。下图中的`Owner`下拉菜单可以用来选择该库的所属账号，默认自己的账号就行。在后面的 Repository name 中填上 username.github.io 其中 username 为你的账号名。**注意： username 必须与你的账号名保持完全一致，否则网站将不可访问！**

![create-repository-owner](https://help.github.com/assets/images/help/repository/create-repository-owner.png)

然后勾选下图所示的选项，给你的库初始化一个`README.md`文档，用来解释说明你的库内容。

![initialize-with-readme](https://help.github.com/assets/images/help/repository/initialize-with-readme.png)

最后点击`Create repository`，网站库就创建完毕。其他配置暂时不用管，感兴趣的同学可以自行了解或者在评论区给我留言。

如图所示，点击`Settings`，跳转库设置页面。下翻该页面，如果看到下图所示的内容，则证明你提交到该库中的网站项目已经可以成功通过`http://username.github.io/`访问了。

![repo-actions-settings](https://help.github.com/assets/images/help/repository/repo-actions-settings.png)

### 2.下载并安装 git

这里以 Windows 操作系统为例：

* 从[git 官网][3]下载，国内用户可能需要翻墙。
* 从[git 国内镜像][6]下载，不过这里只支持64位 Windows 操作系统，选择最新版的`64-bit Git for Windows Setup`下载即可。

安装全程下一步，装完后在任意文件夹下点击右键，菜单会多出两个按钮：

* Git GUI Here
* Git Bash Here

### 3.把项目推送到 GitHub 的对应库

选择一个你认为合适的文件夹，右键点击菜单中的`Git Bash Here`按钮打开 git 命令行界面，输入`git clone https://github.com/username/username.github.io`其中 username 为你的 GitHub 账号名，回车后等待 git 把远端的库文件`clone`到本地来。

![git-bash](https://i.loli.net/2019/11/04/j4FuI2VOR3eBYr5.png)

当你看到上图所示内容时，说明远端库已经`clone`完毕，此时 username.github.io 文件夹内应该只有一个 .git 文件夹和一个 README.md 文件。接下来打开我们上一章创建的网站项目文件夹，忘记路径的同学可以去`C:\Users\UserName\myblog`找。把 myblog 文件夹里面的文件全部拷贝到 username.github.io 文件夹内，然后分别输入下面的指令：

{% highlight factor linenos %}
git add --all
git commit -m "Initial commit"
git push -u origin master
{% endhighlight %}

这样，本地项目中的所有文件就都被推送到了你的 GitHub 对应的 username.github.io 库中去了。打开你的 username.github.io 库页面，看看你刚推送的内容是否更新到此，若库中依然只有`README.md`这一个文件，那就再等几分钟，等待时长看网速快慢，成功后你就可以在浏览器或手机上打开网站`http://username.github.io/`了。

## 后记

Congratulations! 到这一步，我们就已经学会了发布网站的整个流程，至于 git 的相关内容则不在本教程的讨论范围之内，同学们需自行学习，之后如果有空，我也可能专门出一个 git 的系列教程。

从下一章开始，我们将从基础知识入手，一步步学习如何润色我们的网站，并最终做出炫酷的效果。

## 附录

git 常用命令：
{% highlight factor linenos %}
git clone 你的SSH地址
git pull （联系服务器，用远端库记录更新本地库记录）
git add --all （写入本地的所有新文件）
git commit -m "修改日志" （把本地所有文件的修改提交到本地库记录中去，并填写相关的修改日志）
git push -u origin master （把本地库记录推送到远端库记录中去）
{% endhighlight %}

[^git]: [git][2]是一个免费且开源的分布式版本控制系统，其设计理念是高效地处理从小型到巨型项目的任何事务。

[1]: https://github.com/
[2]: https://git-scm.com/
[3]: https://git-scm.com/download/win
[4]: https://pages.github.com/
[5]: https://github.com/collections/github-pages-examples
[6]: https://github.com/waylau/git-for-win
[7]: https://baike.baidu.com/item/%E7%89%88%E6%9C%AC%E6%8E%A7%E5%88%B6/3311252?fr=aladdin
[8]: https://baike.baidu.com/item/%E6%89%98%E7%AE%A1%E4%BB%A3%E7%A0%81/2886980