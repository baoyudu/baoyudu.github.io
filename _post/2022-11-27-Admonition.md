---
layout: post
title: 怎样在文章页面显示美观的Admonition
category: 
author: 
tags: []
summary: 
math: true
---

我经常使用Obsidian中的Admonition插件来美化笔记页面. 用这个插件可以重点显示文章中的定理、定义，对可读性和美观度的提升非常明显。

[Admonitions in Markdown, Working or failing gracefully across Apostrophe, Kramdown, and Jekyll. No plugins required.](https://indii.org/blog/admonitions-in-markdown/)
这篇文章中提出了一种在Kramdown渲染器下可以正常工作的解决方案. 经我的改进, 目前可以实现理想效果:

## 示例

> Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. 
{:.success}

> Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. 
{:.danger}

> Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. 
{:.warning}

> Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. 
{:.info}

> Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. 
{:.thm}

> Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. 
{:.def}

> 
> 设 $f(z)=u(x, y)+\mathrm{i} v(x, y)$ 是定义在域 $D$ 上的函数, $z_{0}=x_{0}+\mathrm{i} y_{0} \in$ $D$. 我们说 $f$ 在 $z_{0}$ 处**实可微**, 是指 $u$ 和 $v$ 作为 $x, y$ 的二元函数在 $\left(x_{0}, y_{0}\right)$ 处可微.
{:.def}

## 实现方法

添加如下css代码

```
/* To add support of admonition */
blockquote {
  @extend .alert;
  @extend .alert-primary;
  @extend .pb-0;
  font-size:15px;

}

blockquote.success {
  @extend .alert-success;
  /* set a color for the blockquote */
  border-left-color: #5cb85c;
}
blockquote.success p:before {
  content: "✓ Success \a";
  font-weight:bold;
  font-size:16px;

}

blockquote.danger {
  @extend .alert-danger;
  /* set a color for the blockquote */
  border-left-color: #d9534f;
}
blockquote.danger p:before {
  content: "⊠ Danger ";
  font-weight:bold;
  font-size:16px;
}

blockquote.warning {
  @extend .alert-warning;
  /* set a color for the blockquote */
  border-left-color: #f0ad4e;
}
blockquote.warning p:before {
  content: "⚠ Warning ";
  font-weight:bold;
  font-size:16px;
}

blockquote.info {
  @extend .alert-info;
  /* set a color for the blockquote */
  border-left-color: #ffeb9d;
}
blockquote.info p:before {
  content: "ⓘ Further Information ";
  font-weight:bold;
  font-size:16px;
}

/* add a type of admonition: thm*/
blockquote.thm {
  @extend .alert-info;
  /* set a color for the blockquote:blue */
  border-left-color: #45cdff;
  /* change text color to black */
  color: #000;
  /* cancel italics */
  font-style: normal;
}

blockquote.thm p:before {
  content: "Theorem \a";
  font-weight:bold;
  font-size:16px;
  display: block;
}

/* add a type of admonition: def */
blockquote.def {
  @extend .alert-info;
  /* set a color for the blockquote:deep blue */
  border-left-color: #1a8cff;
  /* change text color to black */
  color: #000;
  /* cancel italics */
  font-style: normal;
}

blockquote.def p:before { 
  content: "Definition \a ";
  font-weight:bold;
  font-size:16px;
  display: block;
}

/*end of admonition*/
```

每个CSS代码块包含两个部分的样式：

1.扩展了CSS类“alert-success”等的样式，用“success”类来替代它，指定块引用元素的左边框颜色

2.在blockquote元素的p元素之前，添加一个带有如“✓ Success”文字内容的伪元素

为了在伪元素和p元素之间添加一个换行，尝试在伪元素的content属性中使用 \a 表示换行符,但换行符没有生效. 查阅相关资料后尝试使用 display: block 或 display: table 形式将其强制转换为块级元素即可.

