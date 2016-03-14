---
title: "Eclipse 及 Plug-in 的下載及安裝"
date: 2010-07-04 20:34:05
categories: IT技術
tags:
- Eclipse
- Java
- IDE
---

常言道：「工欲善其事，必先利其器」。Java 程式語言的初學者，常被推薦：採用Eclipse 做為 Java IDE 工具。

所以，踏上 Java 學習之路的第一步：下載及安裝 Eclipse；然後，為強化使用的便利性，需再加掛各種 Plug-in。

上述工作，雖不需要天大的學問，但對初學者而言，卻常有不知所措的問題。以下彙集整理個人在學習路上跌跌撞撞後，歸納的心得重點，希望對 Java 的初學者，能有那麼一點助益！
<!-- more -->

## 下載新版或舊版

對於下載，Eclipse 的官網，基本分：「新版下載」、「舊版下載」兩種：
<dl>
  <dt>
    {% link '新版下載處：' 'http://eclipse.org/downloads/' %}</dt>
  <dd>需要最新發行的版本，自此處下載。</dd>
  <dd>
    {% img https://lh3.googleusercontent.com/-jTmDtQKf1gk/VUgzGfKm4kI/AAAAAAAAhHM/pk-r6RzIoPM/s912/Eclipse-new-version-download.png '新版下載網頁' 480 640 %}
  </dd>

  <dt>
    {% link '舊版下載處：' 'http://wiki.eclipse.org/Older_Versions_Of_Eclipse' %}</dt>
  <dd>需要以前發行，某一個舊版本，從此處下載。</dd>
  <dd>
      {% img https://lh3.googleusercontent.com/-Y4hLeWp3oZw/VUgzGQ8clFI/AAAAAAAAhHQ/lfNiUbemPjw/s912/Eclipse-old-version-download.png '新版下載網頁' 480 640 %}
    </dd>
</dl>



## 下載那個產品的識別法

Eclipse 產品發展至今，衍生出不少的旁支，初學者進到「新版下載」網站的網頁後，面對一拖拉古可供下載的項目，大概都會儍眼，不知該從何處著手。

對於 Java 的初學者，您需要下載的產品，應該會是下列兩項，其中的一個。各項產品的名稱，及特性說明，摘述如下：

  * __Eclipse IDE for Java Developers__：只需要開發傳統 Java 應用程式的朋友，則請下載這個標準版本。（初學 Java 程式語言，尚未涉及 Java 網站開發的朋友，用這個產品足矣！）

  * __Eclipse IDE for Java EE Developers__：需要開發傳統 Java 應用程式，同時亦需開發 Serverlet 與 JSP 網頁的朋友，請下載這個企業級的產品。

上述兩項的 Eclipse 產品，在 Windows 作業系統的平台上，又分：32位元、64位元，兩種版本。

綜合「產品」的兩個選擇，及「32/64作業系統位」的兩個分項，Windows 作業系統的使用者，可供下載的選擇就有四種。

初學者往往因不清楚自己的需求，不知道該下載那個項目。所以，前前後後下載了好幾次，在硬碟裡存了好個檔案。事後，面對這些檔案，常常可能會分不清：每個檔案，誰是誰？！

以下，用 Windows 作業系統的 Eclipse 3.6 (Helios) 為例，教您如何自「檔案名稱」，辨識下載的 Eclipse ：是那一個「產品」；該產品是「32/64位元」的那一種。


|Eclipse產品名稱                    |32位元版本檔案名稱                 |64位元版本檔案名稱                      |
|----------------------------------|-------------------------------|-------------------------------------|
|Eclipse IDE for Java Developers   | eclipse-java-helios-win32.zip | eclipse-java-helios-win32-x86_64.zip|
|Eclipse IDE for Java EE Developer | eclipse-jee-helios-win32.zip  | eclipse-jee-helios-win32-x86_64.zip |


自上述的表格做歸納，可以發覺 Eclipse 的「檔案命名規則」如下：
eclipse-`<<識別一>>`-`<<識別二>>`-`<<識別三>>`.zip

  * 識別一：「java」表標準版；「jee」表 Java EE 企業級版本；

  * 識別二：「helios」表版本編號為：3.6；「galileo」表版本編號為：3.5；

  * 識別三：「win32」表可在 Windows 32 位元作業系統執行，如：Windows XP、Windows Server 2003；「win32-x86_64」表可在 Windows 64位元作業系統，如：Windows 7 (x64)、 Windows Server 2008 R2。

## Eclipse 的 plug-in

寫程式的工作，檔案的版本管理，也會是重要的一環。所以 Eclipse 的使用者，可能會需要讓 Eclipse 化身成為 SVN Client，以便能直接在 Eeclipse 的環境中，直接進行 Java 程式碼的簽入 (Commit) / 簽出 (Check-out) 工作；對於「開發 Google App 雲端應用系統」的人，建立 Project 、 開發完成的程式要部署到 Google 雲端 。

以上的各種需求，都可以透過 Eclipse plug-in 的下載及安裝，添加 Eclipse 原先不具有的功能。

上述兩種的 Eclipse Plug-in ，其下載網址條列如下：


  * {% link 'Sublipse plug-in for eclipse' 'http://subclipse.tigris.org/update_1.6.x/' %}：令 Eclipse 化身成 SVN Client。撰寫本文時最新版本為1.6.x，經過個人的測試，這個版本的 plug-in 可在 Eclipse 3.4, 3.5, 3.6（32位元）版本執行。雖然這個版本亦可在 3.6 (64位元) 版本執行，但很容易看到 JavaHL 的錯誤警示。

  * {% link 'Google App Engine plug-in for eclipse' 'https://cloud.google.com/appengine/docs/java/tools/eclipse' %}：令 Eclipse 可開發 Google App 雲端應用系統。不論是使用 Eclipse 3.4, 3.5, 3.6 那一個版本，皆可在這找到適合您使用的plug-in版本。

好了，報告完畢。祝各位 Eclipse 的初學者順利步上學習之路，在未來的日子，能開發出偉大的軟體 -- 是幸。 ^^
