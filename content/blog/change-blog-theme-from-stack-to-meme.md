---
title: "博客主题更换：Stack to MemE"
date: 2022-02-28T10:02:45+08:00
draft: false
categories: [LEARN]
tags: [HUGO]
---

是的我换主题了，永远年轻，永远爱换皮肤。曾经的我嫌弃单栏过于简陋，现在的我觉得单栏才是最好看的，回归简洁，选择了[ MemE ](https://github.com/reuixiy/hugo-theme-meme)这个主题。在 MemE 主题之上又做了一些个性化的修改。

<!--more-->

## 配置 waline 评论

Stack 主题里用的是 waline 评论，MemE 主题的评论插件中没有提供 waline，不想再去创建一个应用，搜了一圈发现刚好有在 MemE 中配置 waline 评论的帖子，就直接搬来用了。

帖子是这篇：[Waline 评论系统的介绍与基础配置](https://guanqr.com/tech/website/introduction-and-basic-setting-of-waline/)

配合主题修改评论的暗黑模式，只需要在配置中添加 `dark: 'html[data-theme="dark"]'`即可。不同主题可能会有所不同，具体看[官方文档](https://waline.js.org/guide/client/style.html#%E6%9A%97%E9%BB%91%E6%A8%A1%E5%BC%8F%E6%94%AF%E6%8C%81)。如果要自定义样式，加在 `custom.scss`中是不会生效的，需要在`Waline.html`的`<style>`标签中自定义。

```HTML
<!--Waline.html-->
<script>
...
function newWaline() {
 new Waline({
 el: '#waline',
 serverURL: '{{ .Site.Params.walineServerURL }}',
 ...
<!--在此处加入-->
 dark: 'html[data-theme="dark"]'
 });
...
}
</script>
<style>
/* 自定义样式 */
</style>
```

## 配置说说功能

(已删)

最开始是看到[哔哔点啥 :: 木木木木木](https://immmmm.com/bb/)这个页面，觉得非常适合用来发我的铲屎官日记，看了大佬的教程，显然——我没有看懂。原理清楚，看着简单，插入到自己的主题里又摸不着路子，学习 Hugo 模板语法的时间成本太多，再加上用微信公众号、捷径等发哔哔的方式其实我也不是很需要，于是只好放弃。

才怪！

自己码不了难道还找不到现成的了吗！我使出搜索大法，最后找到了这个插件：[Artitalk.js](https://artitalk.js.org/). （一个小 Tip: 由于 Hugo 使用的人还不算很多，在找博客功能的时候不妨用 Hexo 试试。）看看这介绍，“基于 LeanCloud 实现的可实时发布说说/微语的 js”，这不正是我想要的吗！

在 LeanCloud 的配置很简单，跟着 [使用文档](https://artitalk.js.org/doc.html)一步步配置。然后是在 MemE 主题中引入：

1. 配置菜单栏，在 config 文件中新增菜单：

```TOML
[[menu.main]]
        pageref = "/cat/"
        name = "猫咪"
        weight = 5 //权重，表示菜单栏的顺序
```

2. 在`content`文件夹下新建`cat`文件夹，下面再新建一个`_index.md`：

```md
---
title: "铲屎官日记"
layout: "cat"
comments: false
---

: 说说页面需要的文字
```

3. 在`layouts/_default/`下新增`cat.html`, 作为说说的 HTML 页面，并修改样式。内容如下:

```HTML
{{ define "main" }}
 <!-- 引用 artitalk -->
 <script type="text/javascript" src="https://unpkg.com/artitalk"></script>
 <!--container和主题结构保持一致-->
 <div class="container">
 {{ partial "header.html" . }}
 {{ if ne .Site.Params.headerLayout "flex" }}
   {{ if or (and .IsHome .Site.Params.displayMenuInHome) (and (not .IsHome) .Site.Params.enableMenu) }}
     {{ partial "menu.html" . }}
   {{ end }}
   {{ partial "components/multilingual.html" . }}
   {{ partial "components/dark-mode.html" . }}
 {{ end }}
 <main class="main list" id="main">
   <div class="main-inner">
     <div class="content cat">
 <!--页面标题-->
       <h1 class="list-title">{{ .Title }}</h1>
 <!--页面介绍-->
       <div class="post-body e-content">
 {{ .Content }}
       </div>
 <!-- 存放说说的容器 -->
       <div id="artitalk_main"></div>
     </div>
   </div>
 </main>
 </div>
 <script>
 new Artitalk({
 appId: "", // Your LeanCloud appId
 appKey: "", // Your LeanCloud appKey
 pageSize: 10, // 每页说说数量
 color3: "var(--color-contrast-high)", // 文字颜色
 color1: "hsla(var(--color-contrast-lower-h), var(--color-contrast-lower-s), var(--color-contrast-lower-l), 0.5)", //背景颜色1
 color2: "hsla(var(--color-contrast-lower-h), var(--color-contrast-lower-s), var(--color-contrast-lower-l), 0.5)" // 背景颜色2
 });
 </script>
 <!--修改样式-->
 <style>
 /* 说说文字颜色和阴影 */
 #artitalk_main .cbp_tmtimeline>li .cbp_tmlabel{
 box-shadow: none;
 }

 /* 加载按钮颜色 */
 #operare_artitalk .at_button, #artitalk_main .at_button{
 background-color: var(--color-contrast-lower);
 color: var(--color-contrast-high);
 transition: background-color .5s;
 }

 #operare_artitalk .at_button, #artitalk_main .at_button:hover{
 background-color: hsla(var(--color-primary-h), var(--color-primary-s), var(--color-primary-l), 0.3);
 box-shadow: none;
 }

 /* 最底下artitalk链接颜色 */
 #artitalk_main .power a{
 color: var(--color-primary);
 }
 </style>
{{ end }}
```

配置完成，顺利的话博客就拥有了说说页面啦。

## 折叠目录

用`<details><summary></summary></details>`标签，添加在`layouts/partials/utils/toc.html` :

```HTML
<!-- Inject TOC Title -->
{{- if .Site.Params.displayTOCTitle -}}
 {{- $regexPatternTOC := `(<nav class="contents">\n.+)(<(ol|ul) class="toc">)` -}}
<!-- 在这里修改 -->
 {{- $regexReplacementTOC := (printf `$1<details open><summary class="toc"><h2 id="contents" class="contents-title">%s</h2></summary>$2` (i18n "tocTitle")) -}}
 {{- $toc = $toc | replaceRE $regexPatternTOC $regexReplacementTOC -}}
{{- end -}}
```
