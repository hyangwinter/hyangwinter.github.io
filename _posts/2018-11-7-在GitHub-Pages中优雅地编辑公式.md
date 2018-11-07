---
layout:     post
title:      在GitHub Pages中优雅地编辑公式
subtitle:   Paper reading
date:       2018-11-7
author:     hyang
header-img: img/post-bg-2015.jpg
catalog: true
tags:
    - Blog
    - MathJax
---

由于这个博客会记录一些看过的论文的分析和我自己的想法，所以不可避免的会在博客里面引入公式。最简单粗暴的方式就时贴图片，但这样会比较麻烦。那有没有更加优雅的方式来解决这个问题呢？

那就是使用**Mathjax**来解析用$Latex$编写的公式!

由于在GitHub中是使用`Jekyll`来生成静态网页的，`Jekyll`中引用**Mathjax**只需在`_includes/head.html`的`<head>...</head>`标签中加入如下代码
```
<script type="text/x-mathjax-config">
    MathJax.Hub.Config({
        jax: ["input/TeX", "output/HTML-CSS"],
        tex2jax: {
            skipTags: ['script', 'noscript', 'style', 'textarea', 'pre', 'code'],
            inlineMath: [ ['$','$'] ],
            displayMath: [ ['$$', '$$'] ],
            processEscapes: true
        }
    });
</script>
<script type="text/javascript" async 
    src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/latest.js?config=TeX-MML-AM_CHTML"></script>
```
参数具体含义请参见[Mathjax config](https://docs.mathjax.org/en/latest/options/preprocessors/tex2jax.html),另外在根目录下`_config.yml`中最好将`markdown`编辑器设置成`kramdown`,因为这个解析器对**Mathjax**的支持比较好。

### 但是

在我的主页上利用`$$...$$`编辑的行间公式居然没被解析出来，要么行间公式根本就直接消失，要么解析成了行内公式

## 问题的解决

在10多天查文档，试了各种解决方案之后，终于在StackOverflow里找到了原因（不得不说这个网站真的挺不错的）。具体请看这里[Redefining displayMath delimiters to $$ … $$ for MathJax does not work, using Jekyll and Github pages](https://stackoverflow.com/questions/40610558/redefining-displaymath-delimiters-to-for-mathjax-does-not-work-using)

解决办法居然就是在`display math`前后空一行，然而这居然就是[kramdown自带的功能](https://kramdown.gettalong.org/syntax.html#math-blocks)啊~~~~
