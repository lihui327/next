---
title: 为博客添加每日一言或诗
date: 2022-06-05 18:44:22
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

#### 为子标题添加今日诗词

**今日诗词官方API文档**：<https://www.jinrishici.com/doc/>.

**使用方法**：直接在主题根目录subtitle上加入代码`<span id="jinrishici-sentence">正在加载今日诗词....</span><script src="https://sdk.jinrishici.com/v2/browser/jinrishici.js" charset="utf-8"></script>`，一行即可。

#### 为博客文章添加今日诗词、每日一言

`themes\next\source\css\_schemes\Muse\index.styl`

使用的哪个样式就直接在那个样式下的index.styl文件中更改，直接在后面加上如下代码：

```css
/*诗*/
.poem-wrap {
    position: relative;
    width: 730px;
    max-width: 80%;
    border: 2px solid #797979;
    border-top: none;
    text-align: center;
    margin: 80px auto;
}
 
.poem-wrap h1 {
    font-size: 30px;
    position: relative;
    margin-top: -20px;
    display: inline-block;
    letter-spacing: 4px;
    color: #797979
}
 
.poem-wrap p {
    width: 70%;
    margin: auto;
    line-height: 30px;
    color: #797979;
}
 
.poem-wrap p#poem {
    font-size: 25px;
}
 
.poem-wrap p#info {
    font-size: 15px;
    margin: 15px auto;
}
 
.poem-border {
    position: absolute;
    height: 2px;
    width: 27%;
    background-color: #797979;
}
 
.poem-right {
    right: 0;
}
 
.poem-left {
    left: 0;
}
 
@media (max-width: 685px) {
    .poem-border {
        width: 18%;
    }
}
 
@media (max-width: 500px) {
    .poem-wrap {
        margin-top: 60px;
        margin-bottom: 20px;
        border-top: 2px solid #797979;
    }
 
    .poem-wrap h1 {
        margin: 20px 6px;
    }
 
    .poem-border {
        display: none;
    }
}
```

然后在.md文件中添加代码

```html
<div class="poem-wrap">
  <div class="poem-border poem-left"></div>
  <div class="poem-border poem-right"></div>
    <h1>念两句诗</h1>
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
```

```html
<p id="hitokoto">获取中...</p>
<script src="https://v1.hitokoto.cn/?encode=js&select=%23hitokoto" defer></script>
```

挺简单的，但是对新手不大友好。

#### 参考文章

1. <https://blog.csdn.net/qq_44036990/article/details/105088198>.
2. <https://cnhuazhu.top/butterfly/2021/05/29/Hexo%E9%AD%94%E6%94%B9/Hexo%E6%B7%BB%E5%8A%A0%E4%B8%A4%E5%8F%A5%E8%AF%97%E8%AF%8D/>.
3. <https://juejin.cn/post/6997775533840793614#heading-2>.