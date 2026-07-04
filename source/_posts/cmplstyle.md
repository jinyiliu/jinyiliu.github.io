---
title: cmplstyle
date: 2025-08-13 17:04:36
tags:
    - coding
    - python
---

[Complete Traditional Chinese Color Table](https://jinyiliu.github.io/html/chinese-traditional-colors.html)

<!--more-->

### PDF version of color tables

For Chinese readers: [Complete Chinese Color Table with Chinese names](https://jinyiliu.github.io/2025/08/13/cmplstyle/TCC_ncols_5.pdf).

For non-Chinese readers, an [Indexed Color Reference](https://jinyiliu.github.io/2025/08/13/cmplstyle/TCC_indexed_ncols_5.pdf) is available, using numbered keys (`TCC_1` through `TCC_365`).

### 小记

用了这么长时间的 Matplotlib，一直不喜欢它提供的颜色。首先是它的[颜色命名](https://matplotlib.org/stable/gallery/color/named_colors.html)是基于西方文化体系的，很多颜色其实是西方世界的常见植物或者油画颜料，比如 `peachpuff`、`papayawhip`、`lavender`、`honeydew` 等等。对于中国人来说，我们很难理解这些颜色的名字和它们的实际颜色之间的关系。其次，Matplotlib 提供的默认有名字的颜色不够丰富。再者，即使有些西方人知道东方存在一套完整的颜色体系，他们也仅仅对日本颜色体系有所了解，而对中国颜色体系知之甚少，我感到很可惜，这么丰富漂亮的颜色体系却没有被更多人了解和使用。 所以，我决定自己给 Matplotlib 打上一套中国颜色体系的补丁。

我想，每一个中国人在使用这一套颜色体系时，都会更有一种亲切感和自豪感吧。不少颜色的名字都来源于中国古代的诗词歌赋，或者是中国古代的绘画作品，每一个颜色都有它独特的意象，文化背景，和历史渊源。比如`东方既白`指的是黎明时东方天空的颜色，

{% blockquote （北宋）苏东坡, 《赤壁赋》 %}
相与枕藉乎舟中，不知东方之既白。
{% endblockquote %}

`西子`指的是西湖水的颜色，`木兰`是僧服的颜色，`丹罽`是枝头荔枝红的颜色，`三公子`是唐代最高级别的三个官职的官服颜色，`明黄`是升上中天的太阳色，明代之后，成为皇帝的专用颜色，`菡萏`是荷花花苞将开未开时的颜色，`祖母绿`其实是来自波斯的一种宝石的颜色，音译自 zmernd，`綟绶`是汉代相国所佩绶带的颜色，`胭脂虫`是一种进口颜料的颜色，从美洲仙人掌上寄生的雌性胭脂虫体内提取的红色素，`凝夜紫`来自李贺的诗《雁门太守行》，用来描述战场压抑、肃杀又悲壮的气氛 ...

{% blockquote （中唐）李贺, 《雁门太守行》 %}
黑云压城城欲摧，甲光向日金鳞开。
角声满天秋色里，塞上燕脂凝夜紫。
半卷红旗临易水，霜重鼓寒声不起。
报君黄金台上意，提携玉龙为君死。
{% endblockquote %}
