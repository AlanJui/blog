---
title: "Node.JS 入門初探"
date: 2013-02-27 19:49:34
categories: IT技術
tags:
- NodeJS
- JavaScript
---

去年曾參加資策會舉辦的手機 APP 開發的訓練課程，其間有專題談論手機如何與 Web 伺服器介接，授課的老師特別推崇採用 Node.js 技術，那時候光要搞懂 iOS、 Objective-C、各個 Framework......，就已弄得暈頭轉向，根本沒時間去搞清楚 Node.js 是蝦米碗糕。

幾天前安裝 Titanium Studio 工具軟體時，安裝程式在執行過程中，竟有畫面徵詢我「是否允許安裝 Node.js」。也就因此，引發我的好奇心，想要好好了解 Node.js 到底是啥個東東。   ^^
<!-- more -->

拜過古狗大神，研讀過一些文章，並透過程式實作，親身體會了 Node.js 是啥，有些什麼能耐之後，做個彙總的重點整理如下：

 * 認識 Node.js 是啥？
 * 特優的 Node.js 入門指引教材
 * 下載及安裝 Node.js 執行環境
 * 在 IDE 工具發展 Node.js 程式碼

## 認識 Node.js 是啥？

__Node.js ＝ 伺服器端使用的JavaScript__

什麼是Node.js？最簡單的講法：「它是一個 Web Server 伺服器端使用的  JavaScript」。

在網路上看到的文章，有人認為這種講法，會令讀者對 Node.js 的視野給窄化。因為在Node.js 的官網，對於 Node.js 的解釋，認為它是一種
「__simple non-blocking networking network programming model__」......

程式設計人員可在「__sockets, network traffice__」的層級，對伺服器進行低階控制的運用。不用等到 Web Client 端來呼叫， Web Server 端可以主動將「訊息」往 Web Client 端 Push 下去。

所以，Node.js 不僅可以利用它開發「Web 應用系統」；甚至非常適合將它當作「Web Service」來用。

嚴格說來， Node.js 是一個「 JavaScript 執行平台」。不應將它比作 PHP ，當成是 Web Server 端使用的 Script 語言。不過，因為我們是初學者，才剛入門，把 Node.js 當成是 Web Server ，伺服器端使用的 JavaScript ，這樣應該會簡單、易懂。

關於 Node.js 是什麼？以下提供幾篇文章，供有興趣追根究底的朋友參考：
 * [Node.js簡介](http://book.nodejs.tw/zh-tw/node_introduce.html)
 * [2011網頁開發熱門技術 – Node.js](http://www.inside.com.tw/2011/03/13/new-tech-nodejs)
 * [Node.js 究竟是什么？](http://www.ibm.com/developerworks/cn/opensource/os-nodejs/)

## 特優的 Node.js 入門指引教材

聽別人講述 Node.js 是什麼，倒不如下海玩玩，親自體會一下。透過程式的實作，去了解 Node.js 是啥？有些什麼功用？個人以為，這是掌握 Node.js ，最好的方式。

以下這裡有篇好章，向入門初學者，大力推薦：[《Node入門》](http://www.nodebeginner.org/index-zh-tw.html)這篇初學者的入門指引實作教材。

![](http://lh5.ggpht.com/-oY1yyRMOUxU/US3sfqtpuII/AAAAAAAAKsU/YN1cTASOjUk/image_thumb%25255B5%25255D.png?imgmax=800)

這篇文章原本雖為英文，但已有一位網路的善人菩薩譯成「繁體中文」的版本。所以，不用擔心有英文閱讀的障礙。像我這種非 PRO 等級的肉腳軟體技術人員，邊讀文章，邊在 Aptana Studio 輸入 Script 程式、測試執行結果，總共花了約六個小時，就可以完成這個入門教程。

因為這個教程的文章寫得非常棒，所以，當我將整篇文章走完之後，對於 Node.js 就能擁有一個輪廓清晰的認識。建議想認識Node.js是什麼的朋友，不要猶豫，靜下心、耐著性，把這文章好好讀完吧！ ^^y

實作程式之前，您需要先建置 Node.js 的 Rutime 執行環境，甚至可能還會需要在 IDE 開發工具，安裝些小配件，好讓程式開發的工作可以更加稱心順意。

以下就說明，如何備妥 Node.js 的開發環境。

## 下載及安裝 Node.js 執行環境

Node.js 這個 JavaScript 的執行平台，適用於 OS X / Linux / Windows 各作業系統，可自官網 [nodejs.org](https://nodejs.org/) 免費下載。

![](http://lh5.ggpht.com/-w_FlDf84WEo/US3sYntNrgI/AAAAAAAAKr0/KS2osrpx8f8/image_thumb%25255B1%25255D.png?imgmax=800)

## 在 IDE 工具發展 Node.js 程式碼

基本上，開發 Node.js 的程式，只要有文字編輯器就可以撰碼。完成的 Script 程式，想要執行時，在 Windows 作業系統，可用 Command 視窗執行；於 OS X / Linux 作業系統，則改用終端機視窗執行。

![](http://lh4.ggpht.com/-vGZvnk8UwQ8/US3scHaGI3I/AAAAAAAAKsE/MDKHCpaFgok/image_thumb%25255B3%25255D.png?imgmax=800)

可是以上的這種作法，對我個人而言，實在有些太刻苦。對於跟我一樣，喜歡使用 IDE 工具，進行程式開發的人，請根據自己的喜好，參考如下的資料，在您愛用的 IDE 工具安裝 Plug-in。

 * [Eclipse / Aptana Studio Plug-in (Nodeclipse)](http://www.nodeclipse.org/)
 * [NetBeans 7.2 Plug-in](http://plugins.netbeans.org/plugin/36653/nodejs)

以下是我在 Aptana Studio 3 使用 Node.js Plug-in 的截圖：
![](http://lh5.ggpht.com/-pIIq-OpWVHc/US4a-5DzrUI/AAAAAAAAKss/73MBbRjNbKI/image_thumb%25255B1%25255D.png?imgmax=800)

### 撰寫Script程式碼：

![](http://lh5.ggpht.com/-pIIq-OpWVHc/US4a-5DzrUI/AAAAAAAAKss/73MBbRjNbKI/image_thumb%25255B1%25255D.png?imgmax=800)

### 執行Script程式碼：

![](http://lh6.ggpht.com/-zDZ3f7kgOZU/US4bCdpGxAI/AAAAAAAAKs8/6WOG1Kd78s0/image_thumb%25255B5%25255D.png?imgmax=800)

### 觀察在用戶端 Web Browser / 伺服端 Console 的輸出結果：

![](http://lh5.ggpht.com/-CEdVTe8bG-Y/US4bGWExlwI/AAAAAAAAKtM/BoSnDNq8Sps/image_thumb%25255B8%25255D.png?imgmax=800)

以下做個摘要說明，提供給喜歡使用 Eclipse 的朋友，透過下列執行步驟，親身打造一個符合 Node.js 用途的 IDE 開發環境：

 1. 下載與安裝 [Eclipse](http://www.eclipse.org/downloads/)：我用的 Eclipse 版本：[Eclipse Classic 4.2.1 (Juno) 64 bits](http://www.eclipse.org/downloads/packages/eclipse-classic-421/junosr1)

 2. 啟動 Eclipse ，安裝 Plug-in：透過「Install New Software」功能，安裝「[Nodeclipse plug-in](http://www.nodeclipse.org/)。安裝的操作細節，可參考這份[《安裝說明》](http://www.nodeclipse.org/updates)。
