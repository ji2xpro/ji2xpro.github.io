---
title: 'Hexo博客指南|第四篇:永久链接之abbrlink'
toc: true
recommend: 1
keywords: categories-java
uniqueId: '2020-05-27 08:24:53/"Hexo博客指南|第四篇:永久链接之abbrlink".html'
mathJax: false
abbrlink: f41f3eae
date: 2020-05-27 16:24:53
thumbnail: https://cdn.jsdelivr.net/gh/removeif/blog_image/img/2019/20190919221611.png
tags:
  - hexo博客
categories:
  - Hexo教程
  - 博客搭建
---
> 唯一永久文章链接
Hexo-abbrlink 是一个 hexo 博客链接永久化的解决方案

<!-- more -->
# 前言
hexo的默认永久链接是在 _config.yml 里配置的，其生成规则是permalink: :year/:month/:day/:title/，是按照年、月、日、标题来生成的。

这种默认配置有个很不能接受的缺点，当文件名为中文时，会导致url链接中也出现中文。复制后的链接会编码，非常不利于阅读，也不简洁。

为此可以使用一个比较方便好用的解决方案：hexo-abbrlink 插件。

Hexo-abbrlink 支持使用不同的算法和进制对文章链接进行转换：

算法|进制|生成链接
-|-|-
crc16|hex|https://post.zz173.com/posts/3ab2.html
crc16|dec|https://post.zz173.com/posts/12345.html
crc32|hex|https://post.zz173.com/posts/9a8b6c4d.html
crc32|dec|https://post.zz173.com/posts/1690090958.html

# 安装
- 方法1
  {% codeblock "命令行" %}
  npm install hexo-abbrlink --save
  {% endcodeblock %}

- 方法2：
  在 package.json 中配置所需的安装包「"hexo-abbrlink": "^2.0.5"」，重新执行一次 npm install 即可

# 配置
1. 修改根目录站点配置文件_config.yml：
{% codeblock _config.yml lang:yaml %}
# 可选 permalink: abbrlink 短链接模式
permalink: :abbrlink/ #文章的永久链接 或者 permalink: posts/:abbrlink.html 如：http://localhost:4000/post/abaf7e89.html
# abbrlink config
abbrlink:
  alg: crc32  #算法: crc16(default) and crc32
  rep: hex    #进制: dec(default) and hex
{% endcodeblock %}

2. 使用 hexo g 会自动在你的文章中加上 abbrlink: fbf5310d

> 可能存在的问题：
配置完成后，存在老文章的链接都变成了 undefined ，而新的文章没问题。这个问题其实我们仔细想一下就能明白，我们首先要执行 hexo clean 清除掉以前生成的文章缓存，然后 hexo g 重新渲染就可以了。

# 参考文章:  
参考github：[hexo-abbrlink](https://github.com/Rozbo/hexo-abbrlink)

<article class="message message-immersive is-warning">
<div class="message-body">
<i class="fas fa-question-circle mr-2"></i>文章内容有误？请点击<a href="https://github.com/ji2xpro/ji2xpro.github.io/edit/sourceCode/source/_posts/hexo/Hexo博客指南-第四篇-永久链接之abbrlink.md">此处</a>提交修改。
</div>
</article>