---
title: 关于hexo+next主题valine评论设置邮件提醒
date: 2022-05-08 21:36:07
categories: hexo
tags:
- next
- valine
---

#### 前言

可能是我眼睛不好使的缘故，本来网上的教程讲得很详细，我硬是没有看到操作界面，这，我也比较无语...

<!-- more -->

#### 参考文章

[为Valine评论系统添加邮件提醒](https://blog.csdn.net/weixin_43167980/article/details/113808068).

[Valine-Admin](https://github.com/zhaojun1998/Valine-Admin).

**说明**：网上的教程千篇一律，大致相同，但是我选择这篇，因为它让我找到了正确的位置。

#### 步骤

1. 打开leancloud官网<>登录进入控制台，然后按照图示来(PS: 就为了找到这个Git部署，我花了好长时间，真的感觉自己眼睛不大好使啊😂)

![](https://photo.lihui327.cn/blog/2022/2022-05-08_214953.jpg)

**注意**：可能一开始看不到Git部署，要先部署项目，然后选择Git部署；

2. 选择配置Git

![](https://photo.lihui327.cn/blog/2022/2022-05-08_215700.jpg) 

3. 配置Git填写`https://github.com/zhaojun1998/Valine-Admin`(固定)，分支填写master，点击部署；

![](https://photo.lihui327.cn/blog/2022/2022-05-08_220215.jpg)

![](http://photo.lihui327.cn/blog/2022/2022-05-08_215946.jpg)

4. 设置6个变量；

![](https://photo.lihui327.cn/blog/2022/2022-05-08_220601.jpg) 

**注意**：

`SMTP_PASS`就是邮箱授权码，需要支持smtp，如何获取请百度或者谷歌。

`SMEP_SERVICE`支持列表<https://nodemailer.com/smtp/well-known/#supported-services>.

`SMTP_USER`就是邮箱地址。

5. 需要设置邮箱的休眠策略，需要有管理后台的必须域名备案(国际版好像不用，但我用的是国内开发版)，然后参考上面的文章即可，没有备案的可忽略，表达式填写`0 */20 7-23 * * ?`

![](https://photo.lihui327.cn/blog/2022/2022-05-08_221657.jpg)

6. 重启服务，重新部署，不要忘记填写分支master

![](https://photo.lihui327.cn/blog/2022/2022-05-08_221956.jpg) 

7. 到这里就结束了，不用更新hexo，等待一会儿之后，在博客网站里面提交评论时就会收到邮件提醒了。