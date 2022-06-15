---
title: 关于一个PC里面使用多个github账号的问题
date: 2022-05-07 14:56:22
categories: github
tags:
- blog
---

因为我有两个github账号，但是在git push仓库时发现在同一台PC上只能对一个账号下的仓库进行git push操作，另外一个执行git push会出现denied to错误。参考网上的文章，问题得到了解决。

<!-- more -->

#### 参考文章

[如何在一台电脑上使用多个github账号？ - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/373072996).

#### 解决办法

这里推荐第二种

1. 进入windows控制面板，快捷键`win+r`，`control`，回车；
2. 点击用户账户

![](https://photo.lihui327.cn/blog/2022/2022-05-07_150427.jpg) 

3. 选择凭据管理器

![](https://photo.lihui327.cn/blog/2022/2022-05-07_150602.jpg) 

4. 选择windows凭据

![](https://photo.lihui327.cn/blog/2022/2022-05-07_150757.jpg) 

5. 找到github，编辑，改为你需要进行git push操作的账号和密码，然后保存，就ok了。

![](https://photo.lihui327.cn/blog/2022/2022-05-07_150949.jpg) 

希望上面的内容能帮到你，如有疑问请留下你的评论。