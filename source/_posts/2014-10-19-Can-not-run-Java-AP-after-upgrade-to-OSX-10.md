---
title: "更新到 OS X 10.10 ， Java 應用軟體無法正常執行"
date: 2014-10-19 11:35:42
categories: IT技術
tags:
- Mac
- "OS X"
- Java
---

每回更換 Mac 的作業系統版本，總會有些「驚喜」，這回也不例外！ ^^!!

我的 MacBook Pro ，更新到 OS X 10.10（Yosemite）後，我所有的 Java Application ，如：Visual Paradigm 11.2、Android Studio（Beta）0.8.9 、IntelliJ IDEA 13.1 CE ，通通都不能用，無法正常啟動了！ ＝..＝
<!-- more -->

一開始，我的直覺反應，該不會是 Mac 版的 JVM 太過老舊，無法支援 OS X 10.10 ，所以，先更新 JDK 到「JDK 8 Update 25」這版本。然而，原問題並無改善。 QQ

接著，又再胡亂試了一陣子，沒轍了！只好向 Google 搬救兵，尋求指引，後來，看到一絲依稀、彷彿、可能......的答案：「Java for OS X 2014-001」。

於是，自上述的網頁將「Java for OS X 2014-001」，先行下載，接著再安裝，原先的狀況，終於解除了！ ^^y

## 【結論】：

朋友若也遇有同樣的問題：「OS X 更新到 10.10 版本後，以 Java 開發的應用軟體，再也無法再正常啟動」。建議您依下列的步驟，將問題給排除掉：

 1. 先下載及裝「[Java for OS X 2014-001](https://support.apple.com/kb/DL1572?locale=zh_TW)」。

 2. 執行一個 Java 應用軟體，用以試驗問題是否已解決，例如：Android Studio。

       若原先的問題，從此解除，那做到這步驟就可；若否，請再照著「步驟 3」做下去。

 3. 再下載及安裝 「[JDK 8 Update 25](http://www.oracle.com/technetwork/java/embedded/embedded-se/downloads/javase-embedded-downloads-2209751.html?ssSourceSiteId=ocomen)」。

       根據網路上看到的文章，風傳：「JDK 8 Update 25 已改善無法在 OS X 10.10 安裝 Java 8 的問題」，因此個人推測此版的 JVM 應該沒有與 OS X 10.10 不相容的問題；但...... ，如果問題仍未解，那我也沒轍了！ ^^!!
      【參考文章網址】： [如何在 Mac OS X 10.10 上安裝 Java？](https://www.java.com/zh_TW/download/help/mac_10_10.xml)

## 【附註】：

 * 不知道有沒有人，堅持一定得用 JDK 7 的開發環境，如果有的話，上述的步驟（3），請改下載： JDK 7 Update 71 。

 * 是否有那種苦命人，老需要在不同版本的 Java 環境中切換（Java 6 / 7 / 8）；若有，請參考如下這網址的作法，我用「有效」；希望您也有效（有笑）！
     【參考文章網址】：[How to switch JDK version on Mac OS X](http://www.jayway.com/2014/01/15/how-to-switch-jdk-version-on-mac-os-x-maverick/)

 * 我的 SmartCard Reader ，在 OS X 10.9 ，因更新而致「無法正常使用」的問題；在 OS X 10.10 依然再度發生，目前還沒找到解法！ T__T
