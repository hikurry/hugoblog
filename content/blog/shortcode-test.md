---
title: "短代码测试"
date: 2022-05-26T13:47:59+08:00
categories: [LEARN]
tags: [HUGO, Shortcode]
---

测试了一下 Hugo 的短代码，包括内置和自定义的。捡捡补补，程序员的共享精神真伟大。

<!--more-->

## HUGO 内置短代码

### Figure

```markdown
{{</* figure src="https://unsplash.it/1920/1080/?random=4" title="Unplash Random" */>}}
```

{{< figure src="https://unsplash.it/1920/1080/?random=4" title="Unplash Random" >}}

我自定义了 `figcaption` 的样式。

### Gist

```markdonw
{{</* gist spf13 7896402 */>}}
```

{{< gist spf13 7896402 >}}

原生引入的 Gist 在黑暗模式下奇丑无比，我无法忍受，所以也修改了 Gist 的 CSS 样式，其中代码高亮没有改完，只修改了这里引入出现的标签等，剩下的以后再说吧毕竟我估计不会怎么用到这个短代码。

### 代码高亮

```markdown
{{</* highlight html */>}}

<div class="shortcode">
    <p>shortcode test</p>
</div>
{{</* /highlight */>}}
```

{{< highlight html >}}

<div class="shortcode">
    <p>shortcode test</p>
</div>
{{< /highlight >}}

MemE 主题中本来就自带代码高亮，所以这个短代码没啥用。

### Param

```markdown
{{</* param categories */>}}
```

{{< param categories >}}

### Ref 和 Relref

```markdown
[2021 年度总结]({{</* ref 2021-personal-summary.md */>}})

[2021 年度总结 | 阅读]({{</* relref "2021-personal-summary.md#阅读" */>}})
```

[2021 年度总结]({{< ref 2021-personal-summary.md >}})

[2021 年度总结 | 阅读]({{< relref "2021-personal-summary.md#阅读" >}})

### Tweet

```markdown
{{</* tweet user="cottonsprout" id="1469024461223776256" */>}}
```

{{< tweet user="cottonsprout" id="1469024461223776256" >}}

### Vimeo

```markdown
{{</* vimeo 146022717 */>}}
```

{{< vimeo 146022717 >}}

### Youtube

```markdown
{{</* youtube y5WZ2htfiZU */>}}
```

{{< youtube y5WZ2htfiZU >}}

## 自定义短代码

### Rating

```markdown
{{</* rating 10 8 */>}}
```

{{< rating 10 8 >}}

### 折叠

用 `detials` 和 `summary` 时列表会失效，手打列表标签还挺麻烦的，用短代码替代。

```markdown
{{</* accordion "以 TXT 为圆心" */>}}

- THE BOYZ 为半径
- 中间忘记了
- 召唤五代丝
  {{</* /accordion */>}}
```

{{< accordion "以 TXT 为圆心">}}

- THE BOYZ 为半径
- 中间忘记了
- 召唤五代丝
  {{< /accordion >}}

### 图片轮播

```markdown
{{</* carousel "https://unsplash.it/1920/1080/?random=1,https://unsplash.it/1920/1080/?random=2,https://unsplash.it/1920/1080/?random=3" */>}}
```

{{< carousel "https://unsplash.it/1920/1080/?random=1,https://unsplash.it/1920/1080/?random=2,https://unsplash.it/1920/1080/?random=3" >}}

### Spotify

```markdown
{{</* spotify track 3UZ46DvXvB2R7sBUZornlv */>}}
```

{{< spotify track 3UZ46DvXvB2R7sBUZornlv >}}

{{< accordion "插播一下自定义短码时学到的语法：" >}}

- 循环短代码中变量 `.Params` 时和其他语言一样用的是 `range`

- 统计变量的数量用 `len`，`len $variable`

{{< /accordion >}}

### PDF

```markdown
{{</* pdf src="https://www.blatchingtonmill.org.uk/assets/Uploads/All-Of-Me-Sheet-Music-John-Legend-All-Of-Me-Piano-Sheet-Music-Medium-Vocals-Piano-Guitar.pdf" */>}}
```

{{< pdf src="https://www.blatchingtonmill.org.uk/assets/Uploads/All-Of-Me-Sheet-Music-John-Legend-All-Of-Me-Piano-Sheet-Music-Medium-Vocals-Piano-Guitar.pdf" >}}

手机端不太方便，电脑端看着挺舒服的。

## 参考来源

- [Create Your Own Shortcodes | Hugo](https://gohugo.io/templates/shortcode-templates/)

- [一种在 MemE 主题中实现轮播图功能的思路 | 荷戟独彷徨](https://guanqr.com/tech/website/a-way-to-realize-carousel-in-meme/)

- [GitHub - Ice-Hazymoon/hugo-theme-luna: A simple, performance-first, SEO-friendly Hugo theme / 一个轻量，快速，SEO 友好的 Hugo 主题](https://github.com/Ice-Hazymoon/hugo-theme-luna)

- [GitHub - dillonzq/LoveIt: ❤️A clean, elegant but advanced blog theme for Hugo 一个简洁、优雅且高效的 Hugo 主题](https://github.com/dillonzq/LoveIt)

- [Hugo 博客自定义 shortcodes | Sulv's Blog](https://www.sulvblog.cn/posts/blog/shortcodes/)
