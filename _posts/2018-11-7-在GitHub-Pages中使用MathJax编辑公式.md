---
layout:     post
title:      在GitHub-Pages中使用MathJax编辑公式
subtitle:   Paper reading
date:       2018-11-7
author:     hyang
header-img: img/post-bg-2015.jpg
catalog: true
tags:
    - Blog
    - MathJax
---

##问题的解决

在10多天查文档，试了各种解决方案之后，终于在StackOverflow里找到了原因（不得不说这个网站真的挺不错的）。具体请看这里[Redefining displayMath delimiters to $$ … $$ for MathJax does not work, using Jekyll and Github pages](https://stackoverflow.com/questions/40610558/redefining-displaymath-delimiters-to-for-mathjax-does-not-work-using)
解决办法居然就是在display math前后空一行，然而这居然就是[kramdown自带的功能](https://kramdown.gettalong.org/syntax.html#math-blocks)啊~~~~
