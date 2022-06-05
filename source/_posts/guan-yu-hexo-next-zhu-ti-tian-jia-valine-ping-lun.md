---
title: hexo+next主题添加valine评论
date: 2022-05-07 14:34:05
categories: hexo
tags:
- next
- valine
---

#### 前言

参考文章：[Why remove the valine comment in the latest version？](https://github.com/next-theme/hexo-theme-next/issues/188#issuecomment-766578906).

<!-- more -->

![](https://photo.lihui327.cn/blog/2022/2022-05-07_143721.jpg)

#### 解决

1. 换一个评论系统，完事...
2. 参考[Hexo NexT Valine](https://github.com/next-theme/hexo-next-valine).

① powershell管理员模式下cd到博客根目录，执行`npm install next-theme/hexo-next-valine`

② 进入主题配置文件夹，加入如下代码

```yaml
# Valine
# For more information: https://valine.js.org, https://github.com/xCss/Valine
valine:
  enable: false
  appId:  # your leancloud application appid
  appKey:  # your leancloud application appkey
  serverURLs: # When the custom domain name is enabled, fill it in here
  placeholder: Just go go # comment box placeholder
  avatar: mm # gravatar style
  meta: [nick, mail, link] # Custom comment header
  pageSize: 10 # pagination size
  visitor: false # leancloud-counter-security is not supported for now. When visitor is set to be true, appid and appkey are recommended to be the same as leancloud_visitors' for counter compatibility. Article reading statistic https://valine.js.org/visitor.html
  comment_count: true # If false, comment count will only be displayed in post page, not in home page
  recordIP: false # Whether to record the commenter IP
```

③ [leancloud](https://www.leancloud.cn/). 创建开发板项目，获取appid和appkey，并将其填入上面的appId和appKey中

④ 调试，一般情况下到这里就完成了，不过因为我的是next主题，所以有点特殊，经过上述配置后，调试时，在文章底部会看到如下问题：

![](https://photo.lihui327.cn/blog/2022/2022-05-07_144622.jpg)

**解决办法**：进入leancloud控制台，在设置-应用凭证里复制`REST API 服务器地址`，粘贴到上面代码中的`serverURLs`中，即可解决。

参考文章：[Next主题设置-安装Valine和Artitalk](https://zhuanlan.zhihu.com/p/424932976).

