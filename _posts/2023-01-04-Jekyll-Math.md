---
title: Markdown渲染器与MathJax数学公式显示的严重冲突及解决方案
summary: 静态页面Markdown渲染与LaTex数学公式引擎MathJax之间的冲突及其解决方案
published: true
---


令人惊讶的是，在Jekyll或其他任何静态博客中，Markdown这一排版工具与LaTex数学公式从来都是不合适的一对儿。
在静态页面生成时，Markdown渲染器按照语法将原始的`.md`文件转换为HTML形式，在这一过程中，每两个下划线"_"会被转换成一对`<em>` `</em>`标签, 导致页面加载时Mathjax无法正确识别LaTex公式中表示下标的下划线。这是一个广泛存在、并且在Jekyll社区、Commonmark 社区、StackOverFlow、以及Kramdown、Jekyll、MathJax等项目的Github Issue中均得到大量讨论的问题，MathJax的开发者Davide Cervone也参与了问题的讨论, 但从未有人给出过真正的解决方案。

MathJax文档中有这样一段：

> Such systems need to be told not to modify the mathematics that appears between math delimiters. That usually involves modifying the content-management system itself, which is beyond the means of most page authors. If you are lucky, someone else will already have done this for you, and you may be able to find a MathJax plugin for your system using a web search.
> If there is no plugin for your system, or if the plugin doesn’t handle the subtleties of isolating the mathematics from the other markup that it supports, then you may have to “trick” the content-management system into leaving your mathematics untouched. Most content-management systems provide some means of indicating text that should not be modified (“verbatim” text), often for giving code snippets for computer languages. You may be able use that to enclose your mathematics so that the system leaves it unchanged and MathJax can process it.


由于可用的Markdown渲染器(Kramdown、redCarpet、rDiscount等)均没有针对此问题的插件或设置项，网络上给出的所有临时解决方案也基本采用了这种思路, 均为用代码块或者`<div>`标签, 或者Liquid中的{% raw %}`{% raw %}`{% endraw %} 标签等环境手动包裹住所有的数学表达式, 从而让Markdown渲染器跳过数学表达式部分,避免其破坏原有公式。但这是一个相当敷衍的办法，经常使用数学公式的作者需要不断地做额外的工作来正确显示公式，并且严重地影响了文章的可迁移性。

# 我的解决方案

既然没有现成的插件或配置方法,我只能自己想想办法。基于一种新思路，我基本上完美解决了这个问题，公式可以正确显示，且不需要对原文档做额外修改。
其原理为，在页面的`footer`部分插入一段JavaScript片段, 把所有`<em>` 和`</em>`标签重新转换回"_".

这里以Jekyll为例, 也可以类似应用在其他静态页面生成器中.
在 \_includes 文件夹中新建一个math.html文件,内容为对MathJax的加载:

```
<script>
    MathJax = {
      loader: {load: ['[tex]/ams']},
      tex: {
        autoload: {
          action: ['toggle', 'mathtip', 'texttip'],
          amscd: [[], ['CD']],
          bbox: ['bbox'],
          boldsymbol: ['boldsymbol'],
          braket: ['bra', 'ket', 'braket', 'set', 'Bra', 'Ket', 'Braket', 'Set', 'ketbra', 'Ketbra'],
          cancel: ['cancel', 'bcancel', 'xcancel', 'cancelto'],
          color: ['color', 'definecolor', 'textcolor', 'colorbox', 'fcolorbox'],
          enclose: ['enclose'],
          extpfeil: ['xtwoheadrightarrow', 'xtwoheadleftarrow', 'xmapsto',
                    'xlongequal', 'xtofrom', 'Newextarrow'],
          html: ['href', 'class', 'style', 'cssId'],
          mhchem: ['ce', 'pu'],
          newcommand: ['newcommand', 'renewcommand', 'newenvironment', 'renewenvironment', 'def', 'let'],
          unicode: ['unicode'],
          verb: ['verb']
        },
        inlineMath: [['$', '$'],['\\(','\\)']],
        displayMath: [['$$', '$$'],['\\[','\\]']],
        processEscapes: true,
        packages: {'[+]': ['ams']}
        }
    };

  </script>

<script type="text/javascript" id="MathJax-script" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3.0.0/es5/tex-chtml.js">
</script>
```

再新建一个replace.html ,插入JavaScript来实现内容的替换:

```javascript
<script>
    function rep() 
    {
        document.body.innerHTML
            = document.body.innerHTML
            .replaceAll("<em>", "_").replaceAll("</em>", "_")
        
    }
    rep()
</script>
```

由于Jekyll使用Liquid来渲染页面 ,我们在footer.html中利用Liquid Tag 来引用上述脚本, 注意math.html必须在replace.html之后引用.
{% raw %}
```

{% if page.math %}  
    {% include replace.html %}
    {% include math.html %} 
{% endif %}
```
{% endraw %}

这样, 在文章的Frontmatter中加上 `math: true`, 即可正确显示数学公式.



