---
title: 个性化博客
date: 2022-06-05 19:45:17
categories: hexo
tags:
- blog
---

<div class="poem-wrap">
  <div class="poem-border poem-left"></div>
  <div class="poem-border poem-right"></div>
    <h1>诗词</h1>
    <p id="poem">挑选中...</p>
    <p id="info">  
   <script src="https://sdk.jinrishici.com/v2/browser/jinrishici.js" charset="utf-8"></script>
  <script type="text/javascript">
    jinrishici.load(function(result) {
      poem.innerHTML = result.data.content
      info.innerHTML = '【' + result.data.origin.dynasty + '】' + result.data.origin.author + '《' + result.data.origin.title + '》'
      document.getElementById("poem").value(poem);
      document.getElementById("info").value(info);  
  });
  </script>
</div>

<!-- more -->

#### 参考文章

1. <https://juejin.cn/post/6997775533840793614#heading-10>.