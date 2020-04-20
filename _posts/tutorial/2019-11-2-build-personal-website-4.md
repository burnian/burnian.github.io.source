---
title: （四）从零开始搭建个人静态博客网站
tags: 个人网站 Jekyll
image: https://i.loli.net/2019/11/04/Vk6w24jRNMKpiOf.jpg
description: 这一章主要把整个项目的文件夹结构剖析出来。
---

* TOC
{:toc}

这一章主要把整个项目的文件夹结构剖析出来。

## Jekyll 网站项目的基本文件夹结构

{% highlight factor linenos %}
.
├── _config.yml
├── _data
|   └── members.yml
├── _drafts
|   ├── begin-with-the-crazy-ideas.md
|   └── on-simplicity-in-technology.md
├── _includes
|   ├── footer.html
|   └── header.html
├── _layouts
|   ├── default.html
|   └── post.html
├── _posts
|   ├── 2007-10-29-why-every-programmer-should-play-nethack.md
|   └── 2009-04-26-barcamp-boston-4-roundup.md
├── _sass
|   ├── _base.scss
|   └── _layout.scss
├── _site
├── .jekyll-metadata
└── index.html # can also be an 'index.md' with valid front matter
{% endhighlight %}

## 各文件夹详解

| 文件 / 文件夹 | 描述 |
| ----- | ---- |
| _config.yml | 整个网站的全局配置信息都可以保存在这里，具体可以看看博主的[_config.yml][4]，当我们修改了该文件后一定要重启 Jekyll server 修改才会生效，通过在命令行中按下`ctrl+c`来关闭服务器，再输入`jekyll serve`来开启服务器。|
| _drafts | 这个文件夹作用不大，可以略过，因为它的功能可以通过对`_posts`文件夹内的文件扉页添加`publish: false`（使得某篇博文不发布）来实现。|
| _includes | 这里面存放的是各个页面的通用组件，可以通过`{% raw %}{% include filename.ext %}{% endraw %}`语句把该文件夹下的某个`filename.ext`文件的内容插入到调用这条语句的页面中去。 |
| _layouts | 这里保存的都是布局类文件，可以用作某文件`file.ext`扉页中的 layout 属性的值，而`file.ext`的内容则会替换掉布局类文件的`{% raw %}{{ content }}{% endraw %}`变量。 |
| _posts | 这里存放的是你的博文，通常是 Markdown 文档。 |
| _data | Jekyll 引擎会自动加载这个文件夹下的所有数据文件（文件可以使用 .yml，.yaml，.jso，.csv，.tsv 格式）如果该文件夹下有一个叫做`members.yml`的文件，那么我们可以通过`site.data.members`来获取它的信息。 |
| _sass | 这里存放的是用 Sass[^Sass] 语言编写的 .scss 文件，这些文件最终将被导入到`assets/css/main.scss`文件中去，最终生成一个单独的 css[^css] 样式文件`main.css`。 |
| _site | 这个文件夹不需要用户关心，它是 jekyll 生成的，由最终会部署到服务器上的目标文件构成，可以把它添加到`.gitignore`文件中，让 git 不去关心它。 |
| .jekyll-metadata | 它可以帮助 Jekyll 追踪自上次 build 以来哪些文件没有被修改，以及哪些文件需要在下一次 build 的时候重新生成。这个文件夹不会被包含到`_site`文件夹里面去。可以把它添加到`.gitignore`文件中去。 |

### 1._includes 文件传参举例

假如在`_includes`中有个文件`note.html`，其中有一条语句

{% highlight html linenos %}
{% raw %}
<div> {{ include.myVar }} and {{ include.url }} </div>
{% endraw %}
{% endhighlight %}

则我们在`index.html`中可以通过调用下列语句来给`{% raw %}{{ include.myVar }}{% endraw %}`和`{% raw %}{{ include.url }}{% endraw %}`赋值

{% highlight liquid linenos %}
{% raw %}
{% include note.html myVar="This is my var." url="http://jekyllrb.com" %}
{% endraw %}
{% endhighlight %}

### 2.布局文件

我们通常会有多个布局相同的页面，当这类页面很多的时候，比如50个，这时重复代码就多到不可接受了。于是布局文件应运而生，例如我的布局文件`default.html`如下：

{% highlight html linenos %}
{% raw %}
<!doctype html>
<html lang="zh-CN">
    {% include head.html  %}
    <body>
        {% include header.html %}
        {% include navigation.html %}
        <section id="bcontent" class="container-fluid">
            {{ content }}
        </section>
        {% include footer.html %}
        <script src="{{ '/assets/js/autoload.js' | prepend: site.baseurl }}"></script>
    </body>
</html>
{% endraw %}
{% endhighlight %}

假如现在有一个文件`note.html`，它的布局是 default 的，则只需要在其扉页中添加`layout: default`即可，`note.html`的内容会自动填充到上面代码中的`{% raw %}{{ content }}{% endraw %}`处。

### 3.数据文件

数据文件`_data/navigation.yml`的内容大致如下所示：

{% highlight yml linenos %}
- id: navbar-blog
  name: Blog
  link: /#bnavbar
- id: navbar-gallery
  name: Gallery
  link: /pages/gallery/#bnavbar
{% endhighlight %}

我们可以通过以下语句来遍历`navigation.yml`中的每一组数据（一个小横线代表一组数据）：

{% highlight html linenos %}
{% raw %}
{% for item in site.data.navigation %}
<a href="{{ item.link }}"> {{ item.name }} </a>
{% endfor %}
{% endraw %}
{% endhighlight %}

### 4.资源文件

由于 Jekyll 的默认文件夹结构中并没有资源文件夹，所以我们需要自己来有序地整合这些文件，通常把它们统一存放在`assets`文件夹中，结构大致如下所示：

![assets-dir](https://i.loli.net/2019/11/04/W5wRLSkjHE3v2gn.png)

* `css`存放 .css 和`main.scss`文件。
* `fonts`存放字体资源。
* `img`存放图片文件。
* `js`存放 JavaScript 脚本文件，用于各页面的业务逻辑。
* 根目录下存放其他文件，如 .json 类型的第三方配置文件。

[^Sass]: [Sass][2]是一款强化 CSS 的辅助工具，它在 CSS 语法的基础上增加了变量 (variables)、嵌套 (nested rules)、混合 (mixins)、导入 (inline imports) 等高级功能，这些拓展令 CSS 更加强大与优雅。
[^css]: [css][3]即层叠样式表(Cascading Style Sheets)是一种用来表现 HTML 或 XML（标准通用标记语言的一个子集）等文件样式的程序语言。

[1]: https://www.ruby-lang.org/en/
[2]: https://www.sass.hk/
[3]: https://www.w3school.com.cn/css/index.asp
[4]: https://github.com/burnian/burnian.github.io.source/blob/master/_config.yml
