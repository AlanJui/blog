---
title: "使用 Hexo 的 new 指令，總有 Error 發生"
date: 2015-05-18 20:19:16
categories: IT技術
tags:
- Hexo
- Blog
---

最近，每當我在「終端機」使用 Hexo 的指令 new 建立新的 Post 檔案時，系統總是回應，有 Error 發生的問題：

```
MAC2012:hexo-01 AlanJui$ hexo new 2015-05-18_Responsive-Embed

[Error: Module did not self-register.]

{ [Error: Cannot find module './build/default/DTraceProviderBindings'] code: 'MODULE_NOT_FOUND' }

{ [Error: Cannot find module './build/Debug/DTraceProviderBindings'] code: 'MODULE_NOT_FOUND' }
INFO  Created:

~/workspace/Hexo/hexo-01/source/_posts/2015-05-18-Responsive-Embed.md

MAC2012:hexo-01 AlanJui$  
```
<!-- more -->
這個使用 new 指令建立的 Post 檔案，雖然在「建立」的過程，有異常發生；但在後續完成文章內容的撰寫後，一樣可以 正常「發佈（deploy）」到我的部落格網站，後續沒再發生任何的異常狀況。

這個有些異常的現象，似乎可以忽略它，不予理會。但是，每當執行 new 指令，就會看到的 Error 警告，總是叫人內心感到不痛快。

今天又再 Google 了一下，找到了如下的一篇分享文章：
**[《Hexo常见问题解决方案》](http://wp.huangshiyang.com/hexo%E5%B8%B8%E8%A7%81%E9%97%AE%E9%A2%98%E8%A7%A3%E5%86%B3%E6%96%B9%E6%A1%88)**

根據作者提供的解決良方，我在 Hexo Project 的**根目錄**，透過終機機輸入如下的指令，再次安裝 hexo 的 NodeJS Module ：

```
MAC2012:hexo-01 AlanJui$ npm install hexo --no-optional

hexo@3.0.1 node_modules/hexo
├── hexo-front-matter@0.2.2
├── pretty-hrtime@1.0.0
├── abbrev@1.0.5
├── titlecase@1.0.2
├── archy@1.0.0
├── text-table@0.2.0
├── strip-indent@1.0.1 (get-stdin@4.0.1)
├── tildify@1.0.0 (user-home@1.1.1)
├── hexo-i18n@0.2.1 (sprintf-js@1.0.2)
├── chalk@1.0.0 (escape-string-regexp@1.0.3, ansi-styles@2.0.1, supports-color@1.3.1, strip-ansi@2.0.1, has-ansi@1.0.3)
├── through2@1.1.1 (xtend@4.0.0, readable-stream@1.1.13)
├── minimatch@2.0.7 (brace-expansion@1.1.0)
├── bunyan@1.3.5
├── swig-extras@0.0.1 (markdown@0.5.0)
├── bluebird@2.9.25
├── js-yaml@3.3.1 (esprima@2.2.0, argparse@1.0.2)
├── hexo-fs@0.1.3 (escape-string-regexp@1.0.3, graceful-fs@3.0.6, chokidar@0.12.6)
├── nunjucks@1.3.4 (optimist@0.6.1, chokidar@0.12.6)
├── warehouse@1.0.2 (graceful-fs@3.0.6, cuid@1.2.5, JSONStream@0.10.0)
├── cheerio@0.19.0 (entities@1.1.1, dom-serializer@0.1.0, css-select@1.0.0, htmlparser2@3.8.2)
├── hexo-cli@0.1.4 (minimist@1.1.1)
├── moment@2.9.0
├── hexo-util@0.1.6 (ent@2.2.0, highlight.js@8.5.0)
├── moment-timezone@0.3.1
├── lodash@3.8.0
└── swig@1.4.2 (optimist@0.6.1, uglify-js@2.4.22)
MAC2012:hexo-01 AlanJui$
```

為驗證問題已解決了，我於終端機下指令，再次使用 Hexo 的 new 指令，建立新的 Post 檔案：

```
MAC2012:hexo-01 AlanJui$ hexo new 2015-05-18_Hexo-error

INFO  Created: ~/workspace/Hexo/hexo-01/source/_posts/2015-05-18-Hexo-error.md
MAC2012:hexo-01 AlanJui$
```

如上所示，問題真的已獲決了！   ^^y
