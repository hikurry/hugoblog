---
title: "豆瓣卡片测试"
date: 2023-04-09T08:53:12+08:00
categories: [LEARN]
tags: [Hugo, shortcode]
img: https://i.imgur.com/h8yWG2b.jpg
---

原来的豆瓣 API 挂了，刚好看到 Neodb 的 [API](https://neodb.social/api-doc/) 更新了，逃避给老板做 Farewell 册子于是开始尝试。方法论：一个萝卜一个坑，指哪塞哪，已有的代码和 ChatGPT 缝合大法。

短代码：
```markdown
{{</* db "https://neodb.social/movie/5x5G0qUlH3JmEIAkH8aOhR" */>}}
```

效果：

{{< db "https://neodb.social/movie/5x5G0qUlH3JmEIAkH8aOhR" >}}

{{< db "https://neodb.social/book/6YtZZFTFJ7X3u2bw5ihv5R" >}}

{{< db "https://neodb.social/tv/3q1DZycszvvvlUeQsfnlUA" >}}

{{< db "https://neodb.social/game/2XTjC4uAk6yQKWVaucsspS" >}}

{{< db "https://neodb.social/podcast/55pPDZBO9lnmKmOgIQnqAt" >}}

{{< db "https://neodb.social/album/0N4JA2WyWL43W5zFu4GN34" >}}

{{< db "https://neodb.social/tv/season/2ndrjrm986DTBmyuSEfnFl" >}}

在想哪个更好看一点（~~放弃装修是不可能的~~）：
![](https://i.imgur.com/h8yWG2b.jpg)

