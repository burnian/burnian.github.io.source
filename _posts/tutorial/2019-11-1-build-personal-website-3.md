---
title: （三）从零开始搭建个人静态博客网站
tags: 个人网站 Jekyll
image: https://i.loli.net/2019/11/04/Vk6w24jRNMKpiOf.jpg
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

Jekyll 是一个原生支持 GitHub Pages 且创建流程简单的静态网站生成系统，能够识别 Markdown[^Markdown] 和 HTML[^HTML] 文件，并根据你的布局生成一个完全静态的网站。Jekyll 还支持 Markdown 和 Liquid 语法。我们的网站就是以 Jekyll + GitHub Pages 为核心来支撑的。

## Liquid 是什么

[Liquid][8]由 Shopify 创造并用 Ruby 实现。它既是一门开源的标记语言，又是一个安全且面向用户的灵活网页应用模板引擎。其代码可分为对象（object）、标记（tag）和过滤器（filter）。我们不用记那么多，只需要知道它在项目中怎么使用即可。

## Front Matter 是什么

Front matter（扉页）是一个如下所示的 YAML[^YAML] 代码块，由插件[jekyll-coffeescript][9]实现。

{% highlight factor linenos %}
---
layout: post
title: Blogging Like a Hacker
---
{% endhighlight %}

对于你网站项目中的每一个文件，但凡包含上述代码块的都会被 Jekyll 视为一个特殊文件进行特殊处理，其主要作用是给该文件添加各种属性。

## Jekyll 的全局变量

| 变量 | 描述 |
| - | - |
| [site][10] | `_config.yml`文件中的所有配置信息都可以通过这个变量获取。 |
| [page][11] | 表示一个 .html 文件，该页面的特定数据和定义在其扉页中的数据都可以通过这个变量获取。 |
| content | 该变量主要用于 layout 类型的文件。表示其他使用了某布局类型 default 的文件会把自己的内容填在 default 中的`{% raw %}{{ content }}{% endraw %}`位置。|
| [paginator][12] | 当我们使用了分页插件以后，这个变量就可用了 |

## 后记

Congratulations! 到这一步，我们就基本掌握了利用 Jekyll + GitHub Pages 来搭建个人网站的所有相关知识，在之后的学习中如果碰到哪里不懂我们就可以问出有价值的问题并通过网络途经自行解决了。

下一章我将把整个项目的文件夹结构剖析给大家看，让大家对整个项目有个较为清晰的认识，不再畏手畏脚。

[^mixins]: 混入，就是定义一部分公共的方法或者计算属性，然后混入到各个组件中使用，方便管理与统一修改。
[^singleton-methods]: 单例方法，即同一个方法多处引用，只保存了单个该方法的实例，而不是每引用一次便新建一个实例。
[^renaming]: 重命名。
[^Markdown]: [Markdown][5]是一种目前比较流行的标记语言，能使普通文本内容具有一定的格式，文件后缀通常为 .md 或 .markdown，常用来写博客。
[^HTML]: [HTML][6]属于 web 开发的基础内容，但不属于本教程的讲解范畴，同学们务必自学，可以看看[HTML标准][7]。
[^YAML]: YAML 不是标记语言，而是一个面向所有编程语言的数据序列化标准。

[1]: https://www.ruby-lang.org/en/
[2]: https://baike.baidu.com/item/%E6%9D%BE%E6%9C%AC%E8%A1%8C%E5%BC%98/539636?fr=aladdin
[3]: http://rubylearning.com/satishtalim/tutorial.html
[4]: https://guides.rubygems.org
[5]: https://www.zybuluo.com/mdeditor
[6]: https://baike.baidu.com/item/HTML/97049?fr=aladdin
[7]: https://whatwg-cn.github.io/html/#toc-introduction
[8]: https://liquid.bootcss.com/
[9]: https://github.com/jekyll/jekyll-coffeescript
[10]: https://jekyllrb.com/docs/variables/#site-variables
[11]: https://jekyllrb.com/docs/variables/#page-variables
[12]: https://jekyllrb.com/docs/variables/#paginator
