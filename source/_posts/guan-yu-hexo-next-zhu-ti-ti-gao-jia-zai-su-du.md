---
title: 关于hexo+next主题提高加载速度
date: 2022-05-08 10:36:02
categories: hexo
tags:
- next
---

#### 参考文章

[Hexo-Next提高加载速度](http://t.zoukankan.com/lfri-p-12221963.html).

<!-- more -->

文章里面介绍很详细，不过有几点需要注意。

1. 首先不是所有的js都可以用，这个要视具体情况而定，另外这个是针对next主题的，不同主题有一些不一样。
2. 即使有些可以用，但是不是所有的都能正常显示，比如说我使用`fontawesome: //cdn.jsdelivr.net/npm/font-awesome@4/css/font-awesome.min.css`，就出现一个问题，如图示：

![](https://photo.lihui327.cn/blog/2022/2022-05-08_104411.jpg) 

图标加载不出来，正常情况下应该是这样的：

![](https://photo.lihui327.cn/blog/2022/2022-05-08_104540.jpg) 

所以有些虽然能用但不一定好用。

发下我能使用的代码

```yaml
internal: lib
  anime: //cdn.jsdelivr.net/npm/animejs@3.1.0/lib/anime.min.js
  mathjax: //cdn.jsdelivr.net/npm/mathjax@2/MathJax.js?config=TeX-AMS-MML_HTMLorMML
  mhchem: //cdn.jsdelivr.net/npm/mathjax-mhchem@3
  katex: //cdn.jsdelivr.net/npm/katex@0/dist/katex.min.css
  copy_tex_js: //cdn.jsdelivr.net/npm/katex@0/dist/contrib/copy-tex.min.js
  copy_tex_css: //cdn.jsdelivr.net/npm/katex@0/dist/contrib/copy-tex.min.css
  pjax: //cdn.jsdelivr.net/gh/theme-next/theme-next-pjax@0/pjax.min.js
  jquery: //cdn.jsdelivr.net/npm/jquery@3/dist/jquery.min.js
  fancybox: //cdn.jsdelivr.net/gh/fancyapps/fancybox@3/dist/jquery.fancybox.min.js
  fancybox_css: //cdn.jsdelivr.net/gh/fancyapps/fancybox@3/dist/jquery.fancybox.min.css
  mediumzoom: //cdn.jsdelivr.net/npm/medium-zoom@1/dist/medium-zoom.min.js
  lazyload: //cdn.jsdelivr.net/npm/lozad@1/dist/lozad.min.js
  pangu: //cdn.jsdelivr.net/npm/pangu@4/dist/browser/pangu.min.js
  quicklink: //cdn.jsdelivr.net/npm/quicklink@1/dist/quicklink.umd.js
  disqusjs_js: //cdn.jsdelivr.net/npm/disqusjs@1/dist/disqus.js
  disqusjs_css: //cdn.jsdelivr.net/npm/disqusjs@1/dist/disqusjs.css
  valine: //cdn.jsdelivr.net/npm/valine@1/dist/Valine.min.js
  gitalk_js: //cdn.jsdelivr.net/npm/gitalk@1/dist/gitalk.min.js
  gitalk_css: //cdn.jsdelivr.net/npm/gitalk@1/dist/gitalk.css
  algolia_instant_js: //cdn.jsdelivr.net/npm/instantsearch.js@2/dist/instantsearch.min.js
  algolia_instant_css: //cdn.jsdelivr.net/npm/instantsearch.js@2/dist/instantsearch.min.css
  pdfobject: //cdn.jsdelivr.net/npm/pdfobject@2/pdfobject.min.js
  mermaid: //cdn.jsdelivr.net/npm/mermaid@8/dist/mermaid.min.js
  velocity: //cdn.jsdelivr.net/npm/velocity-animate@1/velocity.min.js
  velocity_ui: //cdn.jsdelivr.net/npm/velocity-animate@1/velocity.ui.min.js
  pace: //cdn.jsdelivr.net/npm/pace-js@1/pace.min.js
  pace_css: //cdn.jsdelivr.net/npm/pace-js@1/themes/blue/pace-theme-minimal.css
  three: //cdn.jsdelivr.net/gh/theme-next/theme-next-three@1/three.min.js
  three_waves: //cdn.jsdelivr.net/gh/theme-next/theme-next-three@1/three-waves.min.js
  canvas_lines: //cdn.jsdelivr.net/gh/theme-next/theme-next-three@1/canvas_lines.min.js
  canvas_sphere: //cdn.jsdelivr.net/gh/theme-next/theme-next-three@1/canvas_sphere.min.js
  canvas_nest: //cdn.jsdelivr.net/gh/theme-next/theme-next-canvas-nest@1/canvas-nest.min.js
  canvas_nest_nomobile: //cdn.jsdelivr.net/gh/theme-next/theme-next-canvas-nest@1/canvas-nest-nomobile.min.js
  canvas_ribbon: //cdn.jsdelivr.net/gh/theme-next/theme-next-canvas-ribbon@1/canvas-ribbon.js
```

图片懒加载也可以用一下。

这里需要强调一下，国内提供的CDN加速服务都是需要域名备案才能用的，所以想白嫖是不大可能的，趁早死了这条心吧（￣︶￣）↗　