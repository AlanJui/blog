---
title:  "如何在Hexo文章放入圖片"
date:   2015-04-26 10:00:00
categories: "IT技術"
tags:
- Hexo
---

![Hexo](https://encrypted-tbn1.gstatic.com/images?q=tbn:ANd9GcR9-YiPtxqPWBo38HqxjiOV1Vr87B_tu5HKDQ8OCzZrD68R-cee)

使用Hexo寫Blog文章，基本上就是用Markdown的「語法」來編輯文章。

當你需要在文章中置入「圖片／相片」時，除了使用標準的Markdown語法外，Hexo還支援了其它進階的用法。

<!-- more -->
## 顯示圖片路徑位置

使用語法
``` hexo
{% asset_path touring.jpg %}
```
如下所示，可顯示圖片檔存放所在的路徑位置：

{% asset_path touring.jpg %}


## 顯示圖片

使用語法
``` hexo
{% asset_img touring.jpg Touring %}
```
等同 HTML Tag
``` html
<img src="2014/12/12/figure-with-caption/touring.jpg">
```

可顯示如下所示之圖片檔：
{% asset_img touring.jpg 單車旅遊 %}


## 置入圖片檔的「連結位置」

使用語法
``` hexo
{% asset_link touring.jpg 單車旅遊 %}
```
等同 HTML Tag
``` html
<a href="touring.jpg" alt="單車旅遊">單車旅遊</a>
```

{% asset_link touring.jpg 單車旅遊 %}
