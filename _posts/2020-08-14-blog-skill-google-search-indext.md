---
layout: post
title: "Google Search Console教程，小白入深坑"
date: 2020-08-14
categories: BlogSkill
tags: google blogskill
author: David
excerpt: 为了添加google索引，进行Google Search Console验证，添加sitemap.xml文件，【绑定sitemap.xsl样式文件】，一个个小坑不断。这里做一个小结。
---


* content
{:toc}
> 这篇博客主要回答如下三个问题：Google Search Console如何验证，如何解决sitemap.xml识别错误，以及如何绑定绑定sitemap.xsl样式文件。

# 添加Github Pages上的博客

------

## 1.查看是否被收录

首先查看你的博客地址是否已经被Google收录，在Google的搜索栏中搜索：

> site:https://xxxx.github.io

其中`https://xxxx.github.io`为你的博客地址，如果结果是`尝试使用Google Search Console`，则意味着没有被收录。

如果搜索出你想要的结果，那么不用继续往下看了。

## 2.搜索资源提交

进入Google Web Master，点击：[Google Search Console](https://www.google.com/webmasters/tools/home?hl=zh-CN)（若未登录谷歌账号，需要先登录谷歌账号）

点击添加，提交你的博客网址，然后跳转到如下界面进行验证。

这里需要验证网站所有权，有多种方法进行验证，网站给我们提示了一个推荐验证方法是：通过在你的网站上添加一个它提供的html文件来验证。

![verify-method](https://evanli.github.io/img/20181025/verify-method.jpg)

下载该文件，上传到你的Github Pages的根目录，然后点击验证，即可通过验证。

![verify-completed](https://evanli.github.io/img/20181025/verify-completed.jpg)

或者也可通过其他方法进行验证，比如不想在根目录添加html文件的话，可以选择在网站首页添加元标记，即在_includes目录下的head.html中的head标签之间添加如下元标记即可。

![other-verify-method](https://evanli.github.io/img/20181025/other-verify-method.jpg)

## 3.添加站点地图

站点地图(Site Map)是用来注明网站结构的文件，我们希望搜索引擎的爬虫了解我们的网站结构,以便于高效爬取内容，快速建立索引。

- 点击进入 [XML-Sitemaps.com](https://www.xml-sitemaps.com/) 页面，输入博客地址，点击 start。

![xml-sitemaps-com](https://evanli.github.io/img/20181025/xml-sitemaps-com.jpg)

- 等待搜索完成，点击 VIEW SITEMAP DETAILS。

![sitemap-completed](https://evanli.github.io/img/20181025/sitemap-completed.jpg)

- 下载 SITEMAP 文件sitemap.xml并将其上传到网站的根目录。

![download-sitemap](https://evanli.github.io/img/20181025/download-sitemap.jpg)

- 在 Google Search console 中添加你的 sitemap URL。

还是刚刚的[Google Search Console](https://www.google.com/webmasters/tools/home?hl=zh-CN)网站，点击刚刚验证成功的你的网站进入控制台，在左边侧边栏“抓取”下找到“站点地图”：

![google-search-console-sitemap](https://evanli.github.io/img/20181025/google-search-console-sitemap.jpg)

点击“添加/测试站点地图”，将https://xxxx.github.io/sitemap.xml提交并刷新，就可以看到博客的网站结构了。

![google-search-console-add-sitemap](https://evanli.github.io/img/20181025/google-search-console-add-sitemap.jpg)

如果没有什么问题的话，到这里就结束了，但是现在用Google还不能立即查到博客的内容，要等到搜索引擎下一次更新检索时才会有显示。

## 4.手动提交Google抓取（可选）

等待Google抓取所需时间比较长，可以利用Google抓取工具手动提交网址。（不是必须，等待Gooogle自行抓取也是可以的）

还是刚刚的Google Webmaster，在左侧的“抓取”栏下可以找到“Google抓取工具”，输入你想要被抓取的网址链接，点击“抓取”，然后在下面选择“请求编入索引”，然后提交即可。

![googlebot](https://evanli.github.io/img/20181025/googlebot.jpg)

![googlebot-index](https://evanli.github.io/img/20181025/googlebot-index.jpg)

此时再在Google的搜索栏中搜索：

> site:https://xxxx.github.io

应该就会有你刚刚提交上去的链接的结果了！也就大功告成了！



# sitemap.xml样式文件sitemap.xsl下载

最近白天在看站长后台的数据时，发现多个站长后台显示sitemap.xml文件抓取失败，因此也就为此在找原因，在通过提交的sitemap.xml地址打开时头部总会显示一大串英语提示，具体提示内容如下：

```
This XML file does not appear to have any style information associated with it. The document tree is shown below.
```

[![sitemap.xml样式文件sitemap.xsl下载](https://img.seobti.com/wp-content/uploads/2020/04/2020040814450621.png)](https://img.seobti.com/wp-content/uploads/2020/04/2020040814450621.png)

这段英语的大致意思是缺少与xml关联的样式文件，在网上一搜才知道原来网站地图sitemap.xml文件是有一个类似css样式的文件 —— xsl文件 ，然后给sitemap.xml关联了一个sitemap.xsl后，展示效果确实好看了，效果如下图所示：

[![sitemap.xml样式文件sitemap.xsl下载](https://img.seobti.com/wp-content/uploads/2020/04/2020040814452648.png)](https://img.seobti.com/wp-content/uploads/2020/04/2020040814452648.png)

也就是通过样式文件，使sitemap.xml文件可视化，让其更美观更有可读性。当然没有xsl样式文件，xml文件也是没有问题的。下面具体说下怎么将xsl样式文件绑定xml文件。

## sitemap.xsl样式文件绑定sitemap.xml文件

1、下载xsl样式文件并上传至网站根目录；

sitemap.xsl下载：https://474b.com/file/21890530-435925494

注：文件下载之后可能文件格式会改成txt文件，如果是txt文件，重命名以xsl后缀的文件即可。

2、检查sitemap.xml文件头部代码是否含有以下代码：

```
<?xml version="1.0" encoding="UTF-8"?>
<?xml-stylesheet type="text/xsl" href="sitemap.xsl"?>
```

检查方法：前端访问自己网站的sitemap.xml文件 → Ctrl+U或鼠标右击查看网页源代码；

注：两行代码都需要含有，缺什么补什么。不然xml文件不会关联xsl样式文件。

### 结语

以上便是本文白天整理的关于给sitemap.xml文件关联一个xsl样式文件的全过程，简单来说xsl文件就像是html代码中的css样式文件，xsl的作用就只是让xml文件前端展示可视化、更美观，仅此而已。

------

**References:**

[1] [让Google搜索到搭建在Github Pages上的博客](https://jactor-sue.github.io/zh-CN/how-blog-on-githubpages-can-be-searched-by-google/)

[2] [为自己的博客添加搜索引擎（Google）收录（以Namecheap为例）](http://gracegreat1.me/2017/11/为自己的博客添加搜索引擎-Google-收录-以-Namecheap-为例/)

[3] [Google Search Console](https://www.google.com/webmasters/tools/home?hl=zh-CN)

[4] [SEO技巧！如何最快时间让Google收录你的页面](http://www.guxiaobei.com/submit-your-content-of-google.html)