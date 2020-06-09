---
title: 'Hexo博客指南|第五篇:github page网站cdn优化加速'
toc: true
recommend: 1
keywords: categories-java
uniqueId: '2020-05-27 08:24:12/"Hexo博客指南|第五篇:github page网站cdn优化加速".html'
mathJax: false
abbrlink: 91a14ab9
date: 2020-05-27 16:25:12
thumbnail:
tags:
  - hexo博客
categories:
  - Hexo教程
  - 博客搭建
---
> CDN的全称是 Content Delivery Network ，即内容分发网络。CDN是构建在网络之上的内容分发网络，依靠部署在各地的边缘服务器，通过中心平台的负载均衡、内容分发、调度等功能模块，使用户就近获取所需内容，降低网络拥塞，提高用户访问响应速度和命中率。CDN 的关键技术主要有内容存储和分发技术。——[百度百科](https://baike.baidu.com/item/CDN)

放在Github的资源在国内加载速度比较慢，因此需要使用 CDN 加速来优化网站打开速度，jsDelivr + Github 便是免费且好用的 CDN ，非常适合博客网站使用。

<!-- more -->
# 前言
因为 Github 服务器在国外，且服务器带宽小，导致静态资源请求速度慢，最终导致全站访问速度被拖慢。最常用的解决方案是使用国内 IDC 厂商提供的对象存储(镜像回源)+ CDN 来提升静态资源访问速度，但这难免会产生费用。就算是付费的，也有一定的限制。那有没有一款造福人类的，或者造福中国大陆的公用 CDN 呢？

# JSDelivr
先来看下[官网](https://www.jsdelivr.com/)的介绍:

{% img "box px-0 py-0 ml-auto mr-auto" https://cdn.jsdelivr.net/gh/ji2xpro/blog_image/Hexo/JSDelivr/jsdelivr-in-china.png 500 '"JSDelivr - 官网" "JSDelivr - 官网"' %}
<br>

>Wow, Awesome!

jsDelivr由ProspectOne维护的公共库，使用的融合CDN技术，由Cloudflare、Fastly、StackPath、QUANTIL等CDN供应商提供了全球超过**750个CDN节点**。最重要的是，jsDelivr在**中国大陆**也拥有超过数百个节点，因为jsDelivr拥有**正规的ICP备案**，解决了中国大陆的访问速度优化，实现真正的**全球极速低延迟体验**。

jsDelivr是**免费**的、**不限制带宽**的，可以加速**NPM**、**Github**、**WordPress**内的文件。

{% img "box px-0 py-0 ml-auto mr-auto" https://cdn.jsdelivr.net/gh/ji2xpro/blog_image/Hexo/JSDelivr/jsdelivr-network-map.png 500 '"JSDelivr - 全球节点分布地图" "JSDelivr - 全球节点分布地图"' %}
<br>

本文采用的方法就是将静态文件资源放到Github的仓库内，再使用jsDelivr进行加速访问，达到完全零成本优化访问速度。相当于一个高速访问的图床！

# 使用
>jsDelivr官网提供了**NPM**、**Github**、**WordPress**三种方法，有兴趣的可以去[官网](https://www.jsdelivr.com/)了解，本博客重点介绍Github的使用

### 创建github仓库
在Github新建一个公开仓库，用于存放我们的静态文件资源。这里不再过多赘述，下面的链接是我的静态文件资源仓库。  
https://github.com/ji2xpro/image

### 使用jsDelivr访问资源

##### 访问github的用法
{% codeblock "链接" %}
https://cdn.jsdelivr.net/gh/用户名称/仓库名称@版本号/目录
{% endcodeblock %}

>//加载资源(版本号不填的话，默认引用最新)
https://cdn.jsdelivr.net/gh/ji2xpro/blog_image/Hexo/JSDelivr/jsdelivr-in-china.png
//打开目录（后面的"/"是必要的，不然的话，打不开）
https://cdn.jsdelivr.net/gh/ji2xpro/image/

注意：版本号不是必需的，是为了区分新旧资源，如果不使用版本号，将会直接引用最新资源，除此之外还可以使用某个范围内的版本，查看所有资源等，具体使用方法如下：

>// 加载任何Github发布、提交或分支
https://cdn.jsdelivr.net/gh/user/repo@version/file  
// 加载 jQuery v3.2.1
https://cdn.jsdelivr.net/gh/jquery/jquery@3.2.1/dist/jquery.min.js  
// 使用版本范围而不是特定版本
https://cdn.jsdelivr.net/gh/jquery/jquery@3.2/dist/jquery.min.js
https://cdn.jsdelivr.net/gh/jquery/jquery@3/dist/jquery.min.js  
// 完全省略该版本以获取最新版本
https://cdn.jsdelivr.net/gh/jquery/jquery/dist/jquery.min.js
// 将“.min”添加到任何JS/CSS文件中以获取缩小版本，如果不存在，将为会自动生成
https://cdn.jsdelivr.net/gh/jquery/jquery@3.2.1/src/core.min.js
// 在末尾添加 / 以获取资源目录列表
https://cdn.jsdelivr.net/gh/jquery/jquery/

**扩展**
- 打开github文件列表，可查看指定分支，列表结构简单实用：  
  文件列表：https://cdn.jsdelivr.net/gh/user/repo/  
  比如参考：https://cdn.jsdelivr.net/gh/ji2xpro/ji2xpro.github.io@sourceCode/
  {% img "box px-0 py-0 ml-auto mr-auto" https://cdn.jsdelivr.net/gh/ji2xpro/blog_image/Hexo/JSDelivr/jsdelivr-get-user-repo.png 500 '"github - 文件列表" "github - 文件列表"' %}
<br>

- 访问统计github文件（github必须存在release发布后才有数据）  
  访问统计：https://www.jsdelivr.com/package/gh/user/repo  
  比如参考：https://www.jsdelivr.com/package/gh/Molunerfinn/PicGo
  {% img "box px-0 py-0 ml-auto mr-auto" https://cdn.jsdelivr.net/gh/ji2xpro/blog_image/Hexo/JSDelivr/jsdelivr-get-user-package.png 500 '"github - 统计" "github - 统计"' %}
<br>

**补充**
<article class="message message-immersive is-primary">
<div class="message-body">
<i class="fas fa-info-circle mr-2"></i>关于 GitHub 作为图床的使用方法可参考博客：<a href="/73d224e9/">Hexo博客指南|第六篇:图床神器PicGo</a>，完整的配置详情以其为准。
</div>
</article>

##### 访问npm的用法
{% codeblock "链接" %}
https://cdn.jsdelivr.net/npm/包名@版本号/目录
{% endcodeblock %}

>//加载资源
https://cdn.jsdelivr.net/npm/lw_firewords@1.0.3/index.js  
//打开目录（后面的"/"是必要的，不然的话，打不开）
https://cdn.jsdelivr.net/npm/lw_firewords/

##### 访问wordpress的用法
>// 加载任何插件从WordPress.org插件SVN repo
https://cdn.jsdelivr.net/wp/plugins/project/tags/version/file  
// 加载精确版本
https://cdn.jsdelivr.net/wp/plugins/wp-slimstat/tags/4.6.5/wp-slimstat.js  
// 加载最新版本  
https://cdn.jsdelivr.net/wp/plugins/wp-slimstat/trunk/wp-slimstat.js  
// 从WordPress.org的主题SVN repo加载任何主题
https://cdn.jsdelivr.net/wp/themes/project/version/file  
// 加载精确版本
https://cdn.jsdelivr.net/wp/themes/twenty-eightteen/1.7/assets/js/html5.js

# 参考文章: 
[jsDelivr官网](https://www.jsdelivr.com/)  
[免费CDN：jsDelivr+Github 使用方法](https://blog.csdn.net/qq_36759224/article/details/86936453)  
[Github+jsDelivr+PicGo 打造稳定快速、高效免费图床](https://blog.csdn.net/qq_36759224/article/details/98058240)

<article class="message message-immersive is-warning">
<div class="message-body">
<i class="fas fa-question-circle mr-2"></i>文章内容有误？请点击<a href="https://github.com/ji2xpro/ji2xpro.github.io/edit/sourceCode/source/_posts/hexo/Hexo博客指南-第五篇-github-page网站cdn优化加速.md">此处</a>提交修改。
</div>
</article>
