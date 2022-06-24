---
title: "hugo | 主题开发 | 第三章"
date: 2022-06-19T13:47:37+08:00
categories:
    - 技术
tags:
    - hugo
---

## 前言
{{< notice notice-note >}}
此教程为hugo0.99.1版本制作的，高版本可能不同。如需使用高版本，请以hugo官方教程为主。
本文章的所有代码都是以猫猫的习惯写的，如果你会`html`，`go摸板`语言和`scss`那么你可以自己写，猫猫的教程只是参考。
并且是基于`card`主题制作的。
{{< /notice >}}
这篇文章会教大家如何实现文章列表以及文章页面，废话不多说，直接开始吧！
## 文章列表
首先是实现文章列表，不先制作这个页面的话你怎么打开文章呢:D
- - -
首先来到你的主题目录下的`layouts/page`在这里我们新建`post.html`打开后输入以下代码以显示文章列表：
```html
<div class="post-menu"> <!-- > 文章列表页面 <-->
    {{ range where .Site.RegularPages "Section" "post" }} <!-- > 将文章显示出来 <-->
    <div class="post-site"> <!-- > 文章卡片 <-->
        <a class="post-sit-img-a" href="{{ .Permalink }}"> <!-- > 文章卡片的图片链接（点击后进入文章页面） <-->
            <div class="post-site-img"> <!-- > 文章卡片的图片，这里猫猫还没搞明白，所以只有一个用来占位置的东西 <-->
            </div>
        </a>
        <div class="post-site-name"> 
            <h5 class="post-name"><a href="{{ .Permalink }}">{{ .Title }}</a></h5> <!-- > 文章名称 <-->
        </div>
    </div>
    {{ end }}
</div>
```
以上代码是显示文章卡片用的，当然你不想要的话可以改成文字（删除文章卡片的图片，文章卡片的灵感来自`bilibili`）
```scss
.post-menu { //文章列表页面
    background-color: var(--background-color);
    margin: var(--margin); 
    padding: var(--padding);
    display: flex;
    flex-wrap: wrap;
    flex-direction: row;
}

.post-site { //文章卡片
    background-color: aliceblue;
    width: 160px;
    margin: 1%;
}

.post-site-img { //文章卡片的图片111111111111111111111111111111111111111111111111111111123333366666666666666666666666
    width: 160px;
    height: 100px;
}

.post-site-name { //文章名卡片
    margin-left: 4%;
    margin-right: 4%;
}

.post-name { //文章名
    margin: 0 0 0 0;
}
```