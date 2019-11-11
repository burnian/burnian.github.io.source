---
title: spark 学习踩坑记录
tags: spark
image: http://spark.apache.org/images/spark-logo-trademark.png
description: 记录 spark 学习过程中的坑，持续更新
---
**1.** hadoop 有其匹配的 JDK 版本，比如：hadoop 版本 >= 2.7 时，要求`Java 7`或`java 8(openjdk/oracle)`，`java 13`运行 hadoop 会出错。hadoop 版本 < 2.7 只能基于`java 6`运行。

**2.** `hadoop-env.cmd`文件里面有一条设置 JAVA_HOME 的语句：
<!-- console or escape-->
{% highlight escape linenos %}
set JAVA_HOME=%JAVA_HOME%
{% endhighlight %}

如果 java 按照默认路径安装在`C:\Program Files`，则会因为 Program 后面的空格导致 JAVA_HOME 配置出错。

**3.** 运行`spark-shell`报错 hadoop 缺了`winutils.exe`文件，则需要去下载对应 hadoop 版本的`winutils.exe`文件，可以去[这里][1]下载然后放入 hadoop 的 bin 目录下。

[1]: https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe
