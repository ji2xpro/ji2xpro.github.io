---
title: 'Hexo博客指南|第十三篇:Icarus配置 - 网站搜索插件'
toc: true
recommend: 1
keywords: categories-java
uniqueId: '2020-06-08 03:44:24/"Hexo博客指南|第十三篇:Icarus配置 - 网站搜索插件".html'
mathJax: false
abbrlink: ea684c22
date: 2020-06-08 11:44:24
thumbnail:
tags:
  - Icarus主题配置
categories:
  - Hexo教程
  - 主题配置
---
> 本文介绍Icarus 3支持的站内搜索插件的安装配置。

<!-- more -->
<article class="message message-immersive is-primary">
<div class="message-body">
<i class="fas fa-info-circle mr-2"></i>下面的站内搜索插件由<a href="https://github.com/ppoffice/hexo-component-inferno">ppoffice/hexo-component-inferno</a>提供，完整的支持插件列表和配置详情以其为准。
</div>
</article>

<style>
.content ol:not([type]) {
    list-style-type: simp-chinese-informal;
}
</style>

## Algolia

<div>
<strong>安装指南</strong>
<a class="tag is-success" style="margin-left:.8em" href="{% post_path demo/search/Algolia %}">在线预览</a>
</div>

1. 在Hexo站点的根目录安装[hexo-algolia](https://github.com/oncletom/hexo-algolia)插件。

2. 注册并登录[Algolia](https://www.algolia.com/)。
   首次登录控制面板(Dashboard)时点击页面上的“创建索引”(Create Index)按钮。
   然后，输入”索引名称“(Index name)并点击“创建”(Create)完成索引创建。

   {% img "box px-0 py-0 ml-auto mr-auto" https://cdn.jsdelivr.net/gh/ji2xpro/blog_image/Hexo/Plugins/Search/Algolia/algolia-create-index.png 500 '"创建索引 - Algolia" "创建索引 - Algolia"' %}
   <br>

3. 下一步，点击右侧导航栏上的”API密钥“(API Keys)，复制页面上的“应用ID”(Application ID)和“仅限搜索的API Key”
   (Search-Only API Key)。
   打开Hexo站点根目录下的站点配置文件`_config.yml`，填入上面复制的信息到hexo-algolia插件的配置中。

   {% img "box px-0 py-0 ml-auto mr-auto" https://cdn.jsdelivr.net/gh/ji2xpro/blog_image/Hexo/Plugins/Search/Algolia/algolia-api-keys.png 500 '"API密钥 - Algolia" "API密钥 - Algolia"' %}
   <br>

   例如，下面的Algolia索引信息：

    {% codeblock "Algolia索引信息" %}
    Algolia索引名称: My-Hexo-Site
    Application ID: ABCDEFGHIJKL
    Search-Only API Key: 7b08fca7d42412cee901a25643124221
    {% endcodeblock %}

    对应的站点配置为：

    {% codeblock _config.yml lang:yaml %}
    algolia:
        applicationID: My-Hexo-Site
        indexName: ABCDEFGHIJKL
        apiKey: 7b08fca7d42412cee901a25643124221
    {% endcodeblock %}

4. 回到Algolia控制面板的”API密钥“(API Keys)页面并切换到“所有API Keys”(All API Keys)标签页。
   点击“新建API Key”(New API Key)按钮。
   在弹出的“创建API Key”(Create API Key)对话框中，在”索引“(Indices)处选择你在上一步中创建的“索引”(Indices)。
   然后，“ACL”项中添加`addObject`，`deleteObject`，`listIndexes`， `deleteIndex`。
   点击“创建”(Create)完成密钥的创建。
   复制刚刚创建的API Key，例如`727fbd8c998fe419318fa350db6793ca`。

   {% img "box px-0 py-0 ml-auto mr-auto" https://cdn.jsdelivr.net/gh/ji2xpro/blog_image/Hexo/Plugins/Search/Algolia/algolia-create-api-key.png 500 '"创建API密钥 - Algolia" "创建API密钥 - Algolia"' %}
   <br>

5. 打开一个Windows命令行(CMD)或Linux/macOS终端并切换当前目录到你的Hexo站点的根目录。
   设置环境变量`HEXO_ALGOLIA_INDEXING_KEY`为上一步中创建的API Key。
   hexo-algolia插件上传网站索引时会用到这个变量。

   Windows下：

    {% codeblock "Windows命令行(CMD)" lang:cmd %}
    C:\Users\you> cd path/to/your/hexo/site
    C:\Users\you> set HEXO_ALGOLIA_INDEXING_KEY="727fbd8c998fe419318fa350db6793ca"
    {% endcodeblock %}

   Linux/macOS下：

    {% codeblock "Linux/macOS终端" lang:shell %}
    $ cd path/to/your/hexo/site
    $ export HEXO_ALGOLIA_INDEXING_KEY="727fbd8c998fe419318fa350db6793ca"
    {% endcodeblock %}

    然后，运行下面的命令来清理站点并上传网站索引到Algolia：

    {% codeblock "Windows命令行(CMD)或Linux/macOS终端" lang:shell %}
    $ hexo clean
    $ hexo algolia
    {% endcodeblock %}
   
6. 最后，在主题配置中设置搜索引擎为Algolia：

    {% codeblock themes/icarus/_config.yml lang:yaml %}
    search:
        type: algolia
    {% endcodeblock %}


## 百度搜索

**安装指南**

1. 打开主题配置文件并设置搜索为百度搜索：

    {% codeblock themes/icarus/_config.yml lang:yaml %}
    search:
        type: baidu
    {% endcodeblock %}


## 谷歌自定义搜索

<div>
<strong>安装指南</strong>
<a class="tag is-success" style="margin-left:.8em" href="{% post_path demo/search/Google-CSE %}">在线预览</a>
</div>

1. 登录你的谷歌账户并访问[Google CSE](https://cse.google.com/cse/create/new)来创建自定义搜索。
   在“需要搜索的站点”(Sites to Search)中填入你的Hexo站点域名。
   在“语言”(Language)选择框中选择正确的语言。
   然后填写自定义“搜索引擎名称”(Name of the search engine)。
   点击“创建”(Create)按钮完成引擎的创建。

   {% img "box px-0 py-0 ml-auto mr-auto" https://cdn.jsdelivr.net/gh/ji2xpro/blog_image/Hexo/Plugins/Search/Google/google-cse-create.png 500 '"创建自定义搜索 - Google CSE" "创建自定义搜索 - Google CSE"' %}
   <br>

2. 然后，点击页面上的“添加到你的站点”(Add it to your site)右侧的“获取代码”(Get code)按钮。
   从HTML代码中复制`cx`的值填入到对应主题配置项中。

   {% img "box px-0 py-0 ml-auto mr-auto" https://cdn.jsdelivr.net/gh/ji2xpro/blog_image/Hexo/Plugins/Search/Google/google-cse-code.png 500 '"获取代码 - Google CSE" "获取代码 - Google CSE"' %}
   <br>

   例如，下面的HTML代码：

    {% codeblock "Google CSE HTML代码" lang:html %}
    <script async src="https://cse.google.com/cse.js?cx=012345601234560123456:abcdefghijklmn"></script>
    <div class="gcse-search"></div>
    {% endcodeblock %}

    对应下面的主题配置：

    {% codeblock themes/icarus/_config.yml lang:yaml %}
    search:
        type: google_cse
        cx: 012345601234560123456:abcdefghijklmn
    {% endcodeblock %}


## Insight

**安装指南**

1. Insight为本站默认的站内搜索引擎。
   你可以通过下面的主题配置来启用它：

    {% codeblock themes/icarus/_config.yml lang:yaml %}
    search:
        type: insight
    {% endcodeblock %}

参考文章:  
[参考链接]()

<article class="message message-immersive is-warning">
<div class="message-body">
<i class="fas fa-question-circle mr-2"></i>文章内容有误？请点击<a href="https://github.com/ji2xpro/ji2xpro.github.io/edit/sourceCode/source/_posts/hexo/Hexo博客指南-第十三篇-Icarus配置-网站搜索插件.md">此处</a>提交修改。
</div>
</article>