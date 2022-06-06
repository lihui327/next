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
    <div>
    <span id="jinrishici-sentence">正在加载今日诗词....</span></div>
<script src="https://sdk.jinrishici.com/v2/browser/jinrishici.js" charset="utf-8"></script>
    <p id="poem_info"> 
  <script type="text/javascript">
    jinrishici.load(function(result) {
        var poem_info=document.querySelector("#poem_info") 
      poem_info.innerHTML = '【' + result.data.origin.dynasty + '】' + result.data.origin.author + '《' + result.data.origin.title + '》'
      document.getElementById("poem_info").value(poem_info);  
  });
  </script>
</div>


<!-- more -->


#### 参考文章

1. <https://juejin.cn/post/6997775533840793614#heading-10>.

