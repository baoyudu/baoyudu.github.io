---
layout: post
title: 对完美的追逐
categories: [blog ]
tags: [Blog]
description: Ghost Markdown样式自定义
---



上图为markdown标志

在网站成功转移至Ghost上后，我修改了主题风格至GitHub上的crossing。这样我发现了一个细节，即文章页面的quote字段风格很丑，是斜体且居中。 追求完美的我绝不能容忍。懒得打开电脑的我用juiceSSH生成密匙ssh链接服务器。cd到themes目录。一段时间的探索后，我发现markdown风格数据似乎储存在/content/themes/css/style.css中。 ssh控制台输入：

`vim style.css`

于是我就在迟钝的控制台移动着光标，在千余行代码中寻找。真有种80年代的感觉。 忽然，我看到了blackquote这个字眼，停下端详一下，应该没错了。 然而，怎么办？ 好吧，我还是打开电脑。准备用winscp冒险修改下。 密匙是在juicessh生成，而winscp必须用putty格式的密匙。我只好迎头乱撞，直接导出私匙，记事本打开一个ppk文件，保存。 导入winscp不成功，忽然想起什么，打开putty，选择Load XXXX key 程序提示可以转化key。转化后点击Save key 打开winscp居然成功链接上了。

打开默认主题，发现它没有style.css，而是screen.css，但是内容相似，找到quote那一段，复制粘贴替换 然后重启

`ctl_all restart`

嘿 上网页一瞧 真的有变化 但是与原版不同，缺了前面的线。 我发先后面还有一段有关代码，内容与前面的线有关。 那么 完全覆盖style.css 把整个代码端移动过来。 再次重启。

就是这个效果

> 嘿 我就是效果

而原来是直接居中文字 就是这么一个细节，花费了我的一个晚上，至少我克服了它，而它是Google和百度上所没有的。


