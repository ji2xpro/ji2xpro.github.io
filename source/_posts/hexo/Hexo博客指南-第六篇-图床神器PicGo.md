---
title: 'Hexo博客指南|第六篇:图床神器PicGo'
toc: true
recommend: 1
keywords: categories-java
uniqueId: '2020-05-29 03:27:46/"Hexo博客指南|第六篇:图床神器PicGo".html'
mathJax: false
abbrlink: 73d224e9
date: 2020-05-29 11:27:46
thumbnail:
tags:
  - hexo博客
categories:
  - Hexo教程
  - 博客搭建
---
> 所谓图床工具，就是自动把本地图片转换成链接的一款工具，网络上有很多图床工具，就目前使用种类而言，PicGo 算得上一款比较优秀的图床工具。它是一款用 Electron-vue 开发的软件，可以支持微博，七牛云，腾讯云COS，又拍云，GitHub，阿里云 OSS，SM.MS，imgur 等8种常用图床，功能强大，简单易用。

<!-- more -->
# 安装
- 安装包安装  
[PicGo下载](https://github.com/Molunerfinn/PicGo/releases)

>注意：github网站提供三个版本的下载：mac 系统选择 dmg 安装包，windows 选择 exe 安装包，如果不是下载安装包，想看源码的话，可以选择 ```git clone https://github.com/Molunerfinn/PicGo.git``` 克隆到本地

- 特别的：mac 用户  
  直接使用brew cask来安装PicGo，简单方便：
  {% codeblock "命令行" %}
  brew cask install picgo
  {% endcodeblock %}

# 配置
>目前主要拿 Github 作为图床进行介绍，后续持续补充其他图床。  
由于在国内访问 GitHub 速度不是很快，不过如果你有特殊工具或者适应这样的速度的话，那就不妨使用一下，这是个不错的选择，关于加速访问 GitHub 图床的方法请参考文章：<a href="/91a14ab9/"> Hexo博客指南|第四篇:github page网站cdn优化加速</a>

### 1. Github
- 创建 GitHub 仓库
  - 首先新建一个仓库或者也可以使用一个已有仓库
   
  {% img "box px-0 py-0 ml-auto mr-auto" https://cdn.jsdelivr.net/gh/ji2xpro/blog_image/Hexo/PicGo/picgo-create-github-repo.png 500 '"github - 新建仓库" "github - 新建仓库"' %}
  <br>

  - 创建好后，需要在 GitHub 上生成一个 token 以便 PicGo 来操作我们的仓库，来到个人中心（点击网页右上角的个人头像，选 Settings ），选择 Developer settings 就能看到 Personal access tokens，选择此 tab ，我们在这里创建需要的 token
  - 点击 Generate new token 创建一个新 token，选择 repo，同时它会把包含其中的都会勾选上，我们勾选这些就可以了。然后拉到最下方点击绿色按钮，Generate token 即可。之后就会生成一个 token ，记得复制保存到其他地方，这个 token 只显示一次！！

  {% img "box px-0 py-0 ml-auto mr-auto" https://cdn.jsdelivr.net/gh/ji2xpro/blog_image/Hexo/PicGo/picgo-generate-github-token-1.png 500 '"github - 生成token" "github - 生成token"' %}
  <br>

  {% img "box px-0 py-0 ml-auto mr-auto" https://cdn.jsdelivr.net/gh/ji2xpro/blog_image/Hexo/PicGo/picgo-generate-github-token-2.png 500 '"github - 生成token" "github - 生成token"' %}
  <br>

- PicGo配置(使用github图传，免费方便，同时配合github.io博客真是方便)
>必填的内容填写完整后就ok
  - 仓库名格式为 用户名/仓库名
  - 分支名：master
  - token：上一步我们创建的token
  - 存储路径：可指定生成在仓库的某个路径下，默认为仓库根目录

  {% img "box px-0 py-0 ml-auto mr-auto" https://cdn.jsdelivr.net/gh/ji2xpro/blog_image/Hexo/PicGo/picgo-github-configuration.png 500 '"github - GitHub设置" "github - GitHub设置"' %}
  <br>

然后点击确定即可完成绑定，并设置成默认图床

# 使用
- 上传区（三种上传方式）
  - menubar 图标拖拽上传（仅支持 macOS）
  - 主窗口拖拽或者选择图片上传
  - 剪贴板图片（最常见的是截图）上传（支持自定义快捷键）

>其中前两种都是可以明确获得文件名，而第三种无法获取文件名（因为剪贴板里有些图片比如截图根本就不存在文件名）

{% img "box px-0 py-0 ml-auto mr-auto" https://cdn.jsdelivr.net/gh/ji2xpro/blog_image/Hexo/PicGo/picgo-pic-upload.png 500 '"github - 上传区" "github - 上传区"' %}
<br>

链接格式：选择需要的格式，默认选项：Markdown

- 相册区

{% img "box px-0 py-0 ml-auto mr-auto" https://cdn.jsdelivr.net/gh/ji2xpro/blog_image/Hexo/PicGo/picgo-album.png 500 '"github - 相册区" "github - 相册区"' %}
<br>

上传完成之后，我们到相册就会看到上传成功后的照片，另外在自己的仓库里，也能够看到上传的图片。

接着在相册区点击复制时，你会发现，它会给我们复制为 Markdown 的样式（如果你是在写 Markdown 的话，就不再需要再转化格式了）。

**建议**
<article class="message message-immersive is-primary">
<div class="message-body">
<i class="fas fa-info-circle mr-2"></i>加速访问 GitHub 图床的方法可参考博客：<a href="/91a14ab9/">Hexo博客指南|第四篇:github page网站cdn优化加速</a>，完整的配置详情以其为准。
</div>
</article>

>PicGo 上传动图 gif 时注意：如果直接复制网页上的动图，去上传的话是截取的某帧，是静图。应该下载到本地，然后在拖进去上传就可以了。

- 其他功能
可在PicGo中依次设置，比较常见的：自定义链接格式，重命名，时间戳重命名等

{% img "box px-0 py-0 ml-auto mr-auto" https://cdn.jsdelivr.net/gh/ji2xpro/blog_image/Hexo/PicGo/picgo-configuration-1.png 500 '"github - PicGo设置1" "github - PicGo设置1"' %}
<br>

{% img "box px-0 py-0 ml-auto mr-auto" https://cdn.jsdelivr.net/gh/ji2xpro/blog_image/Hexo/PicGo/picgo-configuration-2.png 500 '"github - PicGo设置2" "github - PicGo设置2"' %}
<br>

# 扩展
PicGo 的配置文件在不同系统里是不一样的。
- Windows: ```%APPDATA%\picgo\data.json```
- Linux: ```$XDG_CONFIG_HOME/picgo/data.json``` or ```~/.config/picgo/data.json```
- macOS: ```~/Library/Application\ Support/picgo/data.json```

>举例：  
在windows里你可以在：  
```C:\Users\你的用户名\AppData\Roaming\picgo\data.json``` 找到它。  
在linux里你可以在：  
```~/.config/picgo/data.json``` 里找到它。

# 参考文章
[PicGo源码](https://github.com/Molunerfinn/PicGo)  
[一个开源的图床软件PicGo](https://www.jianshu.com/p/5c8a0072f3fc)  
[图床工具的使用---PicGo](https://www.jianshu.com/p/9d91355e8418)

<article class="message message-immersive is-warning">
<div class="message-body">
<i class="fas fa-question-circle mr-2"></i>文章内容有误？请点击<a href="https://github.com/ji2xpro/ji2xpro.github.io/edit/sourceCode/source/_posts/hexo/Hexo博客指南-第六篇-图床神器PicGo.md">此处</a>提交修改。
</div>
</article>