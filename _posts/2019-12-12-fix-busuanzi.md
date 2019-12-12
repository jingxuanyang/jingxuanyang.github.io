---
layout: post
title:  "Fix UV PV at the bottom of my page"
date:   2019-12-12
categories: bug-fix
tags: bug-fix UV PV
author: Jingxuan Yang
---

* content
{:toc}


## Introduction
建立本站时，页面最下方的本站访问量三个数字均无法显示，设置了百度统计与谷歌分析以后还是没有数字显示。
最后通过与最开始的设计者代码相比较，发现了错误所在之处，我fork的那位作者没有更改这个错误。

## 更改方法
在`_includes`文件夹中找到`footer.html`文件并进入编辑模式，将最下面一行代码更改为

```html
<script async src="//busuanzi.ibruce.info/busuanzi/2.3/busuanzi.pure.mini.js"></script>
```

这样，页面最下方的三个统计数字就可以正常显示了~~
