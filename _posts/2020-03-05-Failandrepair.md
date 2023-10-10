---
title: 部署失败与更新
tags: Internet
---

大概一个星期前，从本地推送后，部署发生错误
```
2020/02/29 06:48:56 Gem::InstallError: zeitwerk requires Ruby version >= 2.4.4.
2020/02/29 06:48:56 An error occurred while installing zeitwerk (2.3.0), and Bundler cannot
2020/02/29 06:48:56 .
2020/02/29 06:48:56 Make sure that `gem install zeitwerk -v '2.3.0'` succeeds before bundling.
2020/02/29 06:48:56 In Gemfile:
2020/02/29 06:48:56   github-pages was resolved to 204, which depends on
2020/02/29 06:48:56     jekyll-mentions was resolved to 1.5.1, which depends on
2020/02/29 06:48:56       html-pipeline was resolved to 2.12.3, which depends on
2020/02/29 06:48:56         activesupport was resolved to 6.0.2.2, which depends on
2020/02/29 06:48:56           zeitwerk
```
*原始日志已经找不到了，这是复现的日志*

令人疑惑的是在本次commit中几乎没有对核心的部署文件作出任何改动，尽管从日志上来看是依赖的Ruby版本出现问题，但这个原因十分可疑，在使用`git reset --hard`还原到上一版本后，部署不会出现问题。
一个几乎『不存在』的原因导致了多次重复的失败。  

这些年来，也尝试解决了不少网站的部署问题，最大的困难是在整个中文互联网上，对于Jekyll的非本地部署的许多细节问题可供参考的资料几乎为零，一切都要靠翻阅原始的英文文档，而其中往往不存在直接的解决方案，效率很低。
但不管怎么样，我决定从日志入手开始尝试。  

显然，至少从表面上看，zeitwerk依赖的Ruby版本需要更新。在根目录的 .ruby-version文件中我将Ruby-version改为2.7.0

重新部署，很长的log在眼前滚动而过，部署成功了。  

详尽的日志，85个gems，人是而物非。原来还有开发者在努力维护着它们。

![](/images/图像329.png)
也有它们  

`Ruby Sass has reached end-of-life and should no longer be used.`


*2020-03-29 08:50:22 Github上经请教与讨论 问题已经彻底解决*

