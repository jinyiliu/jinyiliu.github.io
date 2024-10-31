---
title: Hexo备忘录
date: 2022-04-13 16:08:06
toc: true
tags:
    - blog
---

{% codeblock lang:bash line_number:false %}
hexo clean                  # clean static files
hexo g -w                   # generate static files
hexo s                      # hexo server
hexo s --draft              # hexo server with drafts
hexo d                      # hexo deploy
hexo new post "blog title"
hexo new draft "blog title"
hexo publish draft "title"
{% endcodeblock %}

如果出现本地显示正常，远程服务器显示不正常的现象，请尝试清除浏览器缓存。

在 Mac Safari 上清除浏览器缓存，Settings -> Privacy -> Manage Website Data 清除所需要的网页的数据。
