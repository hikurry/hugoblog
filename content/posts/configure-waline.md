---
title: "配置 Waline 评论"
date: 2022-06-28T12:35:38+08:00
categories: [LEARN]
tags: [花里胡哨, Waline, Hugo]
---
虽然无人问津但还是要“五脏俱全”，依葫芦画瓢，知其然但不知其所以然，主要是配置了头像和评论TG通知。

## 头像配置

waline头像使用gravatar，到[官网](http://en.gravatar.com/)注册账号后上传图片即可，注册邮箱需要和评论填写的邮箱一致。

非自定义的头像默认是很丑的蓝色图像，之前的配置中只要修改 `avatar` 的设置即可，但是我设置成 `monsterid` 后还是没有改变。找了好久都不知道哪里有问题，而且 Waline 版本更新后出的新的官方文档中删掉了 `avatar` 这个组建属性，两个官方文档我切换来切换去都搞懵了。 最后在官方 [issue](https://github.com/walinejs/waline/issues/775) 中看到了这条，就索性更新版本后按照评论中的方式设置环境变量试一试。

![](https://s2.loli.net/2022/06/28/YK7qjVbOcl8sIxh.png "非自定义头像配置")

更新到最新版本后在 vercel 中配置环境变量：

`GRAVATAR_STR = https://cravatar.cn/avatar/{{mail|md5}}?d=monsterid `

然后重新部署，最后测试发现小怪兽头像配置成功了！

![](https://s2.loli.net/2022/06/28/RBfEw9egUZXSGNy.png)

## 配置评论通知

虽然 Waine 提供了后台，但每次登录查看也还是不方便。于是按照[官方文档](https://waline.js.org/guide/server/notification.html#telegram-%E9%80%9A%E7%9F%A5)配置了评论 TG通知。选择 TG 的原因是我会经常看，同时消息较少不容易被错过。

TG 推送评论通知效果如下：

![](https://s2.loli.net/2022/06/28/XMOtsASYGcHfkd7.png)

## 其他环境变量

隐藏评论者的用户代理：

`DISABLE_USERAGENT = true`

隐藏评论者的归属地：

`DISABLE_REGION = true`

