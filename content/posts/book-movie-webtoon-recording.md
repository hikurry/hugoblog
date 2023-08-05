---
title: "书籍影视漫画标记"
date: 2022-09-29T08:05:38+08:00
categories: [LIFE]
tags: [花里胡哨, 标记平台, obsidian, watcha pedia, anime-planet, anilist]
img: https://i.imgur.com/16BGdls.jpg
---

所谓学习的时候干什么都有趣，之前复习考试时到处 google 发现了一些书籍影视漫画标记平台，使用感受还不错，推荐给需要的朋友们！

## Watcha Pedia 왓챠피디아

iOS 韩区应用，可以标记电影、电视剧、书籍和漫画。从功能和体验来讲是我觉得最接近豆瓣使用感受的平台。

它的自我介绍是“One of world's best recommendation apps for movies, TV shows. based on 600 million ratings & reviews. ”数据库体量还算大，可以反映韩国人的偏好和热门。

虽然是韩国软件，但是提供韩语、日语、英语三种语言。需要注意的是如果想要标记书影剧漫四种类型的话一定要在网页端注册，并将地区勾选为韩国，否则在手机端注册平台根据系统自动识别到韩国以外地区的只会显示电影和电视剧两种类型。

watcha pedia 起家是电影和电视剧数据库，所以影视的词条很全，英文搜索友好。书籍只提供韩文版本，应该是只要有在韩国出版的书都能找到，就是得先找到书籍的原名再找到韩文译名，这点上不是很方便。漫画以网漫为主，日漫如果有单行本并且被引进到网络平台上的话会同时出现在书籍和漫画两个分类当中。

### 首页
具体以电影页面为例，watcha pedia 提供了韩国票房实时排名、watcha 热门、网飞热门、热门导演和演员的作品，并根据以往的标记和评分推荐类型相似的电影、、用户预期高分作品、其他用户的收藏单（like 豆列），最后也提供了 watcha pedia 官方的收藏片单。

和其他标记平台不同的一点是，watcha pedia 的作品下方都提供一个预期评分，是根据用户以往的打分预测出来的，但是可能因为我现在标记得不多，所以这个预期评分还不太准。

{{< gallery "https://i.imgur.com/16BGdls.jpg" "https://i.imgur.com/ef3DuIj.jpg" "https://i.imgur.com/3rI0UhD.jpg" >}}

### 条目页面
点开条目可以对条目标记状态、评分和写评论。评分是五星标准，允许半颗星。除了最基本的条目信息外，条目页面也显示了该条目的全部评论和评分分布图，评论会按点赞数排序显示。如果关注的朋友标记了，那么也会看到朋友的评分和评论。

### 个人信息页
在用户个人信息页面，watcha pedia 提供了书籍影视漫画的归档、评论归档、以及简单的标记数据分析。

{{< gallery "https://i.imgur.com/RjOa4xb.jpg" "https://i.imgur.com/iB0nONF.jpg" >}}
{{< gallery "https://i.imgur.com/31g6ZkG.jpg" "https://i.imgur.com/sCiE7Ub.jpg" >}}

数据分析有总标记数统计、评分分布、喜欢的电影标签、喜欢的导演演员、喜欢的电影按国家统计、喜欢的电影类型、观看总小时数、喜欢的书籍标签、喜欢的作者。

![](https://i.imgur.com/MWMcf13.png "数据分析页面部分截图")

### 朋友动态
和豆瓣友邻动态类似，在 APP 端“News Feed”中可以看到“Friend‘s Activity”，可以看到关注的人的评分、评论等，并且可以点赞评论。

![](https://i.imgur.com/b9kasZi.jpg "关注了一位据说是韩国著名评论家，but 我什么都看不懂==")

## Anime-Planet（AP） / Anilist
这两个都是漫画和动画标记平台，中日韩都有，数据库很全。但从数据库上来说，二者没有太大差别，主要是使用上有些微妙的不同。我个人体验简单来说 AP 条目搜索更方便，评分评论起来更丝滑，Anilist在已标记的漫画中筛选和数据分析可视化功能更强大。

用了 watcha pedia 之后我就没怎么用这两个网页端了，因为我个人还是觉得 APP 方便些。

## 本地 Obsidian
用 obsidian + mininal 主题+dataview 插件+DB folder 插件+obsidian douban 插件可以在本地实现类 notion 管理书籍影视。

主要分成两个部分，一个是表格数据库，利用 DB folder 和 obsidian douban 实现，可以直接在表格内编辑而不用打开 markdown 文件，非常方便。

![](https://i.imgur.com/l4x50TL.png)

![](https://i.imgur.com/u3SIAZS.png "条目信息模版示例")

还有一个是图片画廊。利用 dataview 查询语句，结合 minimal 主题自带的 cards 展示来实现画廊效果。

![](https://i.imgur.com/8qZfjTU.jpg)

标记的 workflow 就是，先在表格页面新插入一个条目，然后点击打开 markdown 文件，用快捷键运行 obsidian douban 插件查询当前文件名拉去条目信息，最后手动填写状态、评分、评论等，完美解决了之前想要本地保存但是懒于手动输入条目信息的问题！
