---
title: "hugo ｜ 一键部署到gitee或github上"
date: 2022-02-17
categories:
    - 技术
tags:
    - hugo
---

## 简介
这个教程可以让你只打开一个程序就将你的网站部署到github page上。
## 部署脚本
### 第一次使用
如果是第一次使用的话不推荐使用，因为只有在第一次部署完成后需要更新才适合此脚本。
### 更新博客
在网站根目录添加一个cmd后缀的文件(名称随意，作者使用deploy.cmd)。
>cmd、bat、sh均可使用，cmd、bat执行速度较快。
之后使用任意文本编辑器打开cmd文件添加以下代码:
```
hugo -D

cd public

git add .

git commit -am"init"

git push -f origin_ssh master
```
之后打开此脚本即可完成更新。