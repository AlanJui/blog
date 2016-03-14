---
title: "升級到 OS X 10.9 後讀卡機不能用"
date: 2013-12-28 22:06:50
categories: IT技術
tags:
- Mac
- "OS X"
---

每個月的月底，我需要向銀行繳交信用卡消費。繳款的方式，我習慣使用玉山銀行的 Web ATM ，透過網路來進行轉帳。
<!-- more -->

使用玉山銀行的 Web ATM ，需要這些工具：（1）MacBook Pro 電腦（作業系統 OS X  10.8）；（2）讀卡機；（3）Chrome 瀏覽器。

接在 Mac 電腦的讀卡機（Smart Card Reader），是源自 Windows XP 時代，就擁有的。

![](http://2.bp.blogspot.com/-Oo6vjqCiAYY/Ur0e_byZcgI/AAAAAAAAWX8/eQdYEuD4FsI/s320/IMG_0803.jpg)

在 11 月初，Apple 發佈新版的 Mac OS X 10.9 ，我將 Mac 電腦的作業系統，升級。

到了月底，我一如往常，再次使用 Web ATM 進行轉帳，但那次的轉帳，玉山銀行 Web ATM 的應用系統（網站），一直認定我的電腦並沒有安裝讀卡機。

原本以為，我那台服務多年的讀卡機，不耐歲月的催殘，終於壽終正寢，回歸天家了。因此，只好掏出銀兩，請購了以下這台新的讀卡機 GoodTec CR-508 。

![](http://4.bp.blogspot.com/-MIH-9nOjIpI/Ur0e9T69RaI/AAAAAAAAWX0/dnFjfcA66oQ/s320/IMG_0802.JPG)

會買這台讀卡機的原因，是因為看到包裝盒上印有「適用 MAC 10.6.4 以上版本」的規格說明。

可是......結果，還是被玉山銀行認定「沒有完成讀卡機安裝」，哇嘞.......  

照著玉山銀行，如下網址處的操作指引，執行安裝及檢驗程序，結果還是「失敗」。

[https://netbank.esunbank.com.tw/webatm/Q&A_017.htm#02](https://netbank.esunbank.com.tw/webatm/Q&A_017.htm#02)

實在不甘心，寫 e-mail 及打電話到 GoodTec 公司，尋求技術支援，想找出問題根源及可能的解決方法。

最後的答案，竟然是讀卡機驅動程式 PCSCD ，在  OS X 10.9 版本後，變成不認識 RealTec 晶片，以致作業系統無法認定讀卡機已安裝。（據那工程師的講法，台灣製造的讀卡機，都是用這款晶片）

每次作業系統升級都要經歷的痛，這次，最叫人＠！＃＄％＾＆＊＃

趁著這次找問題導因的事件，順便整理出－「如何在 Mac 安裝讀卡機的操作程序」，如以下影片所示。這程序也適用於「玉山銀行 Web ATM」的安裝。

{% youtube "zX0dJn7NWPg" %}
