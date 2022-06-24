---
title: "Rime小狼毫 ｜ 输入法『中』"
date: 2022-03-09T13:23:20+08:00
description: 聪明的输入法懂我心意
image: img/配图.png
categories:
    - 软件
tags:
    - 输入法
---

## 前言
{{< quote >}}
上一篇文章教了大家如何安装小狼毫输入法，但是小狼毫输入法自己的样式不是很好看『不过作者发现一个自带的黑色样式很好看，不过还是换成仿win10输入法样式了』，所以这篇文章将会教大家如何修改小狼毫输入法的样式『让这个输入法更像win10自带的输入法』
{{</ quote >}}
## 食用方式
首先右键你的小狼毫图标『这里应该有什么不用我多说了吧。』选择`用户文件夹`之后在文件夹中找到`weasel.custom.yaml`文件，如果没有就新建一个，打开这个文件删除里面的内容之后把以下代码复制进去
### 仿win10样式『Bai Mao』款
原作者为『Bai Mao』如需搬运请复制此段标明原作者。
```yaml
patch:
  "preset_color_schemes/Micosoft『Bai Mao』":
    author: Bai Mao
    back_color: 0xF0F1F1
    border_color: 0xD7D8D8
    candidate_text_color: 0x000000
    hilited_back_color: 0xffffff
    hilited_candidate_back_color: 0xF7CB98
    hilited_candidate_text_color: 0xffffff
    hilited_text_color: 0x000000
    name: Micosoft『Bai Mao』
    text_color: 0x000000
  "style/color_scheme": Micosoft『Bai Mao』
  "style/display_tray_icon": true
  "style/font_face": "Microsoft YaHei"
  "style/font_point": 14
  "style/horizontal": true
  "style/inline_preedit": true
  "style/layout/border": 0
  "style/layout/border_width": 0
  "style/layout/candidate_spacing": 24
  "style/layout/hilite_padding": 15
  "style/layout/hilite_spacing": 3
  "style/layout/margin_x": 8
  "style/layout/margin_y": 6
  "style/layout/round_corner": 0
  "style/layout/spacing": 10
```