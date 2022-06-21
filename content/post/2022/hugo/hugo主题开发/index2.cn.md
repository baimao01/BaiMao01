---
title: "hugo | 主题开发 | 第二章"
date: 2022-06-14T18:59:43+08:00
categories:
    - 技术
tags: 
    - hugo
---

## 相关链接
[html菜鸟教程](https://www.runoob.com/html/html-tutorial.html)
## 前言
在完成第一章以后，我们就要开始接触`html`和`scss`了，这两者几乎是搭建网站时必备的，首先我们先来了解`html`。
{{< notice notice-note >}}
本文章的所有代码都是以猫猫的习惯写的，如果你会`html`，`go摸板`语言和`scss`那么你可以自己写，猫猫的教程只是参考。
并且是基于`card`主题制作的。
{{< /notice >}}
## 了解html
### 前言
首先我们要知道`html`为网站做了什么，以及它在hugo主题中如何使用。
### html
### html在hugo主题中使用
了解完`html`后就要知道怎么在主题中使用了，hugo是由`go`语言制作的，并且`go`有一个`go摸板`语言，`go摸板`语言会在开发hugo主题的路上经常用到。例如我想让我的网站能够显示我在`config`文件中的网站标题。那么就要写：
```html
<title>{{ .Title }}</title>
```
中间带`{{  }}`的就是`go摸板`语言，用它可以实现一些`html`无法实现的功能。
## 开始制作
### 显示标题
首先我们要制作主页面，在这之前我会先教大家怎么显示网站标题，先打开`themes/<你的主题名>/latouts/partials/head.html`（猫猫的路径改过了，等会会教大家怎么改路径。直接改是不行的）打开后里面是空的，这时我们输入以下代码：
```html
<title>{{ .Title }}</title>
```
这样就可以在每个页面中显示标题了（如果打开的是除首页以外的页面则会显示那个页面的名称）。
然后就是刚刚的修改路径了，为了方便管理猫猫一般会将这些文件放到一些文件夹里。
在`themes/<你的主题名>/latouts/partials/`下新建文件夹`head`这里是引用一些所以页面的东西的，将之前的`head.html`移动到此目录下。然后再打开`themes/<你的主题名>/latouts/_default/baseof.html`，将里面的代码改为：
```html
<head>
    {{- partial "head/head" . -}} <!-- > 引用刚刚的head.html <-->
    {{- block "head" . -}}{{ end }}
</head>

<body class="{{ block `body-class` . }}{{ end }}">  <!-- > 这个是从其他主题那拿的，暂时不知道啥意思:( <-->

    {{/* The container is wider when there's any activated widget */}}
    {{- $hasWidget := false -}}
    {{- range .Site.Params.widgets -}}
    {{- if gt (len .) 0 -}}
    {{- $hasWidget = true -}}
    {{- end -}}
    {{- end -}}
    <div class="container main-container flex on-phone--column {{ if $hasWidget }}extended{{ else }}compact{{ end }}">
        <main class="main full-width">
            {{- block "main" . }}{{- end }}
        </main>
        {{- block "right-sidebar" . -}}{{ end }}
    </div>
</body>

{{- partial "footer.html" . -}}  <!-- > 页脚信息的文件 <-->
```


这样就能引用`head.html`文件了，接下来还要修改这个文件，为了以后的一些东西准备。把里面的内容改成：
```html
<title>{{ .Title }}</title> <!-- > 显示网站名 <-->

<link rel='canonical' href='{{ .Permalink }}'>
{{- partial "head/style.html" . -}}  <!-- > 引用scss文件，如果没有就无法使用scss样式 <-->

{{ with .Site.Params.myBlog.favicon }}  <!-- > 你的网站图标 <-->
<link rel="shortcut icon" href="{{ . }}" />
{{ end }}

<div class="mainContainer">
    {{ block "up-sidebar" . }}
    {{ partial "sidebar/up.html" . }} <!-- > 这里是顶部的菜单栏，等会会讲到的 <-->
    {{ end }}
</div>
```
完成后就要准备好`style.html`文件了，在`themes/<你的主题名>/latouts/partials/head/`目录下新建此文件。
### 首页
完成以上步骤后就要开始制作博客的首页了，先创建一些文件，这些文件会在`index.html`文件中引用，这样做可以方便后期管理。

接下来创建以下文件（全部创建在`themes/<你的主题名>/latouts/partials/page/`这个文件夹中，如果没有就新建。这些文件的名称都是可以自定义的，只是在引用的时候要使用你自定义的名字，猫猫的名字只是参考哦）：
```cmd
home.html

post.html
```
创建完成后在`home.html`中输入以下代码：
```html
<main>
    <div class="home">
        <div class="home-site-name">
            <h2 class="home-site-name1">{{ .Site.Title }} 的个人博客</h2> <!-- 获取config文件中的名称 -->
            <h4 class="home-site-name1">{{ .Site.Params.subtitle }}</h4> <!-- 获取config文件中的简介 -->
        </div>
    </div>
</main>
```
接下来在根目录（不是主题的根目录，是博客的）的`config.toml`中添加并修改：
```toml
baseURL = 'http://baimao01.vercel.app/' #你的博客地址（一定要写对！！！写错了无法在vercel部署）
languageCode = 'zh-cn' #你的博客语言
title = 'Bai Mao' #你的博客名

theme = 'card' #你的主题名

[params]
    favicon = '/img/favicon.jpg' #你的博客图标
    subtitle = '你见过会用电脑的猫吗？' #你的简介
```

## 引用scss
完成以上步骤以后你会看到一个丑丑的页面，在之前我们说过了`html`是网站的骨架，那么接下来就要开始给他们套上外表了。

完成以上步骤以后恭喜你，你成功完成了你的博客首页，下一篇教程将会叫大家怎么制作文章页面以及文章列表（显示所以文章的地方）。
