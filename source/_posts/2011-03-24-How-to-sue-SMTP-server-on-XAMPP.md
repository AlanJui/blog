---
title: "如何啟用 XAMPP 中的 SMTP Server 功能"
date: 2011-03-24 22:29:19
categories: IT技術
tags:
- XAMPP
- SMTP
---

現在的Web應用系統，經常需要有透過e-mail發通知的功能。

可在Windows作業系統環境執行的XAMPP套件，其中的Mercury/32 (以下簡稱：Mercury)，就具有SMTP Server的功能。透過這個子套件，我們就可以在程式中，使用SMTP來發送e-mail。

只是.......，Mercury的使用，可沒像XAMPP中的Apache或MySQL一樣的簡單，只需輕輕鬆鬆按個 ［Start］鈕，就能將功能啟動。
<!-- more -->

為了搞定Ｍercury的設定，可真是快把我搞瘋。今天，我的 Lucky Day 總算到來了，所以，借著好運之助，我Google到一篇文章，參考其中的作法，再加上自己的測試與摸索，終於…..，把這個我「孝想」已久的功能給安裝妥當。
整個安裝設定的主要程序如下：

 1. 啟動Mercury功能
 2. 設定Core Module組態
 3. 設定MercuryS SMTP Server組態
 4. 設定MercuryE SMTP Client組態
 5. 設定PHP.INI組態
 6. 重新啟動Ｍercury與Apache功能

上述各個「程序步驟」的執行細節，詳述說明如後。

## 啟動Mercury功能

 1. 自「XAMPP Control Panel Application」啟動Ｍercury。
    ![](http://lh3.googleusercontent.com/_40BYSx3mIfk/TYsfu1LH_9I/AAAAAAAABEc/X-T78iNf2OA/s1600/SNAGHTML123213b%5B3%5D.png)

 2. 系統啟動Mercury。
    ![確定 Mercury 旁已顯示「Running」](http://lh3.googleusercontent.com/_40BYSx3mIfk/TYsfwUf2kDI/AAAAAAAABEk/X3BkCstBIUE/s1600/SNAGHTML12487f9%5B3%5D.png)

 3. 點選［Admin］鈕，啟動［Mercury/32］的管理軟體。
    ![](http://lh3.googleusercontent.com/_40BYSx3mIfk/TYsfx65fiDI/AAAAAAAABEs/F3ft5kZ8tWA/s1600/SNAGHTML126a2aa%5B3%5D.png)

 4. Windows出現［Mercury/32］管理介面的畫面。
    ![](http://lh3.googleusercontent.com/_40BYSx3mIfk/TYsfzTXFE4I/AAAAAAAABE0/LT1v6G0-U_w/s1600/SNAGHTML128d34b%5B3%5D.png)


## 設定Core Module組態

 1. 自［Configuration］功能表，選擇［Ｍercury core module］指令。
    ![](http://lh3.googleusercontent.com/_40BYSx3mIfk/TYsf0ttQhhI/AAAAAAAABE8/xKTNaNbtSG8/s1600/SNAGHTML12b1dc2%5B3%5D.png)

 2. 在［Mercury Core Module Configuration］的對話方塊，預設的［General］活頁籤，完成下列項目設定：

  * 在［Internet name for this system］欄位，填「__localhost__」

  * 只勾選［Send copies of all errors to the postmaster］設定
    ![](http://lh3.googleusercontent.com/_40BYSx3mIfk/TYsf2BN18DI/AAAAAAAABFE/t0kuy3HvSeg/s1600/SNAGHTML12cae9c%5B3%5D.png)

 3. 在［Local domains］活頁籤，確定有如下標紅框處之localhost設定：
    ![](http://lh3.googleusercontent.com/_40BYSx3mIfk/TYsf3purYYI/AAAAAAAABFM/ko9OqYBgQK4/s1600/SNAGHTML135232f%5B3%5D.png)

 4. 按［確定］鈕，儲存設定值，並關閉［Mercury Core Module Configuration］對話方塊。


## 設定MercuryS SMTP Server組態

 1. 自［Configuration］功能表，選擇［Ｍercury core module］指令。
    ![](http://lh3.googleusercontent.com/_40BYSx3mIfk/TYsf5bYg6OI/AAAAAAAABFU/1sb9h5WYAHI/s1600/SNAGHTML13a8b63%5B3%5D.png)

 2. 在［Mercury SMTP Server］的對話方塊，預設的［General］活頁籤，完成下列項目設定：

  * 在［Announce myself as］欄位，填「__SMTP__」

  * 在［IP Interface to use］欄位，填「__127.0.0.1__」  (因為我有其它的考量，所以我在此欄填了一個Private IP)
    ![](http://lh3.googleusercontent.com/_40BYSx3mIfk/TYsf7OX4fVI/AAAAAAAABFc/l8WY0KH29wE/s1600/SNAGHTML1455547%5B3%5D.png)

 3. 點選［Connection control］活頁籤，看到如下畫面：
    ![](http://lh3.googleusercontent.com/_40BYSx3mIfk/TYsf8WHbziI/AAAAAAAABFk/exl5pNcKTh4/s1600/SNAGHTML1486c11%5B3%5D.png)

 4. 按［Add restriction］鈕，準備設定 IP: 127.0.0.1 為 SMTP Server 會提供服務的 IP 網址。

 5. 在［IP Address reang］的［from］及［to］欄位填入「127.0.0.1」 ；確認［Attributes for this entry］的選項，設定為［Allow connections］；最後按［OK］鈕，結束此設定動作。
    ![](http://lh3.googleusercontent.com/_40BYSx3mIfk/TYsf9xzxclI/AAAAAAAABFs/B0IPPeuzFow/s1600/SNAGHTML14e57a7%5B3%5D.png)

 6. 再度回到［Connection control］活頁籤時，可在［Connection control］的清單中，看到IP Address為127.0.0.1的網址，為允許(Allow)的設定項目。
    ![](http://lh3.googleusercontent.com/_40BYSx3mIfk/TYsf_ZUlikI/AAAAAAAABF0/ZZ11Ms8g9PU/s1600/SNAGHTML1521aa8%5B3%5D.png)

 7. 按［確定］鈕，儲存設定值，並關閉［Mercury SMTP Server］對話方塊。

## 設定MercuryE SMTP Client組態

 1. 自［Configuration］功能表，選擇［ＭercuryE SMTP Client］指令。

 2. 出現［MercuryE End-to-end SMTP Client Configuration］對話方塊。

 3. 在［Name servers］欄位，輸入「168.95.1.1」。
    ![](http://lh3.googleusercontent.com/_40BYSx3mIfk/TYsgA9LagAI/AAAAAAAABF8/bol4e691rg4/s1600/SNAGHTML155dc51%5B3%5D.png)

 4. 按［Save］鈕，儲存設定值，並關閉［MercuryE End-to-end SMTP Client Configuration］對話方塊。

## 設定PHP.INI組態

1. 使用您喜愛的文字處理器(Editor) ，打開路徑應 在___C:\xampp\php___ 的 __PHP.INI__ 檔案。

2. 加入 `sendmail_from = postmaster@localhost` 設定。
    ![](http://lh3.googleusercontent.com/_40BYSx3mIfk/TYsjinAU2ZI/AAAAAAAABGc/uXkSgKr_xWA/s1600/SNAGHTML16b095a%5B3%5D.png)

3. 儲存並關閉這個檔案。


## 重新啟動Ｍercury與Apache功能

 1. 切換到［XAMPP Control Panel Application］視窗。
    ![](http://lh3.googleusercontent.com/_40BYSx3mIfk/TYsgCScZemI/AAAAAAAABGE/V7GbZhrmg9Y/s1600/SNAGHTML15ae278%5B3%5D.png)

 2. 按 Ｍercury 右邊的［Stop］鈕，結束 Mercury 的功能（等於關閉SMTP Server的功能）。
    ![](http://lh3.googleusercontent.com/_40BYSx3mIfk/TYsgDg6lZkI/AAAAAAAABGM/XkP50MyU5yo/s1600/SNAGHTML15cba40%5B3%5D.png)

 3.  如法泡製，按 Apache 右邊的［Stop］鈕，結束 Appache 的功能（等於關閉Web Server的功能）。

 4. 按 Apache 右邊的［Start］鈕，再次啟動 Apache 的功能（等於重新啟動Web Server的功能）。

 5. 按 Ｍercury 右邊的［Start］鈕，再次啟動 Mercury 的功能（等於重新啟動SMTP Server的功能，執行這個重新啟動的程序，為的是要讓剛才的設定能正常運作）。
    ![](http://lh3.googleusercontent.com/_40BYSx3mIfk/TYsgFNBabBI/AAAAAAAABGU/04jiP72Cnh8/s1600/SNAGHTML16069ff%5B3%5D.png)
