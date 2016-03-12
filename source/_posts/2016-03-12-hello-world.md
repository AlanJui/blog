---
title: Hello Hexo
categories: {{IT技術}}
tags:
- Hexo
---
使用[Hexo](https://hexo.io/)，可以快速架設個人部落格。 

不過，要能操控它，有些「操作細節」還是得參考[文件](https://hexo.io/docs/)，才能真正運用自如。

若是不幸，遇到了一些操作上的疑難雜症，可還得參考其[茶包射擊（troubleshooting）指南](https://hexo.io/docs/troubleshooting.html)；不然，也可以上[GitHub](https://github.com/hexojs/hexo/issues)「放話」請益！

記憶力不算好的我，做些小抄，以備不時之需！

<!-- more -->
### 新建一則Blog

``` bash
$ hexo new "yyyy-mm-dd-My New Post"
```
### 撰寫Blog文章

撰寫Blog文章時，可以為文章來個「前情提要」，令文章的內容可以有個「切割」；讓文章的前半段內容，像是個「「內容摘要」」；而讀者可藉由這個「摘要」，決定是否要進一步閱讀文章的內容細節。
```
<!-- more -->
```

更多參考資訊：[Writing](https://hexo.io/docs/writing.html)

### 預覽Blog文章

在Local端啟動Web伺服器，預覽輸出，確認顯示的結果是否符合自己的意。

``` bash
$ hexo server
```

更多參考資訊：[Server](https://hexo.io/docs/server.html)

### 製作Blog網頁

已寫好的Blog文章，需要Hexo依據樣版，產出HTML網頁／製作Blog標籤。

``` bash
$ hexo generate (--watch)
```

更多參考資訊：[Generating](https://hexo.io/docs/generating.html)

### 發佈Blog文章

將已寫好的Blog文章，發佈到GitHub Pages網站。

``` bash
$ hexo deploy（-g）
```

【註】：上述工作要能正常運作，當然GitHub儲存器要先建立；還有_config.yml該有的「設定」內容，也得先完成才行。

更多參考資訊：[Deployment](https://hexo.io/docs/deployment.html)
