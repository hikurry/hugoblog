---
title: "博主口癖一览"
date: 2024-01-27T22:59:27+08:00
categories: [LEARN]
tags: [Hugo, 词云, 统计, 花里胡哨]
img: https://i.imgur.com/KDlYMn7.jpg
---
![20240128151425](https://i.imgur.com/KDlYMn7.jpg)


论文遇到文本识别词频统计我卖惨求换题，博客想做点年终统计我二话不说火速开动。

一开始只是想着年终了要不也做点什么博客总结，比如看看这一年的关键词是什么。用 python 又是 jieba 又是 wordcloud 筛选了两个字及以上的非数字、英文词语后发现根本没有啥关键词，只是口癖大赏罢了。（用的是建站以来所有的博文不单是 24 年的）

前十高频词全部都是习惯用语，引用毛象上看到的一条，“真的感觉没有真的感觉就不会说话了”，“真的特别喜欢用真的感觉”。倒是“没有”断层第一有点意料之外，居然会说得这么经常。十一至二十高频词开始有了一些主题，比如“眼睛”、“女性”、“女足”、“粉丝”、“猫咪”。第二十个词是“晚上”，晚起晚睡人士大概很多事情都是在晚上做的所以提到的次数多吧。

| 排名 | 词语   | 词频 | 排名 | 词语   | 词频 |
|------|--------|------|------|--------|------|
| 1    | 没有   | 121  | 11   | 眼睛   | 36   |
| 2    | 最后   | 52   | 12   | 女性   | 35   |
| 3    | 喜欢   | 51   | 13   | 这种   | 32   |
| 4    | 现在   | 47   | 14   | 需要   | 30   |
| 5    | 真的   | 46   | 15   | 可能   | 29   |
| 6    | 特别   | 46   | 16   | 女足   | 29   |
| 7    | 看到   | 43   | 17   | 粉丝   | 29   |
| 8    | 感觉   | 43   | 18   | 猫咪   | 28   |
| 9    | 很多   | 41   | 19   | 感受   | 27   |
| 10   | 觉得   | 36   | 20   | 晚上   | 26   |

呈上词云（用了猫咪图片做遮罩，P2 试了下用图片颜色做文字颜色）：

{{<gallery "https://i.imgur.com/pkiuumO.png" "https://i.imgur.com/gmRkKgG.png" >}}

{{< accordion "代码" >}}
```python
import os
import jieba
from wordcloud import WordCloud,ImageColorGenerator
import re
from collections import Counter
import imageio


# 设置停用词,哈工大版from github & 手工加了些词
stopwords_file = '/Users/joy/Desktop/hit_stopwords.txt'
with open(stopwords_file, 'r', encoding='utf-8') as f:
    stopwords = set(f.read().splitlines())

# 遍历指定文件夹下的所有md文件
md_folder = '/Users/joy/Documents/hugoblog/content/posts'
text = ''
for root, dirs, files in os.walk(md_folder):
    for file in files:
        if file.endswith('.md'):
            filepath = os.path.join(root, file)
            with open(filepath, 'r', encoding='utf-8') as f:
                text += f.read()

# 使用jieba进行分词
words = jieba.lcut(text)

# 过滤停用词、单个字母数字组合以及长度小于2的词
words = [word for word in words if len(word) >= 2 and word.strip() and word not in stopwords and not re.match(r'^[a-zA-Z0-9]+$', word)]

# 计算词频
word_counter = Counter(words)

top_words = word_counter.most_common(100)
print("输入二个字及以上单词的词频:")
for word, count in top_words:
    print(word, count)

# 生成遮罩
mask_image = '/Users/joy/Desktop/cat.png'
mask = imageio.imread(mask_image)

# 生成词云，mac 需要把字体定位到系统字体文件夹，不如中文会显示框框
wc1 = WordCloud(font_path="/System/Library/fonts/PingFang.ttc", width=800, height=400, background_color='white',mask=mask).generate_from_frequencies(word_counter)

# 保存词云图像
wc1.to_file('wc1.png')

# 生成遮罩
color_image = '/Users/joy/Desktop/test.png'
color=imageio.imread(color_image)

# 提取颜色
img_colors = ImageColorGenerator(color)
#生成词云
wc2 = WordCloud(font_path="/System/Library/fonts/PingFang.ttc", width=800, height=400, background_color='white',mask=color).generate_from_frequencies(word_counter)
#修改字体颜色
wc2.recolor(color_func=img_colors)
#保存图像
wc2.to_file('wc2.png')
```
{{< /accordion >}}