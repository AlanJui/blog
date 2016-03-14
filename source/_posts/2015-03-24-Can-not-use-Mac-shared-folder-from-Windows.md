---
title: "升級到 OS X 10.10後，再也無法自 Windows 使用 Mac 的共享資料夾"
date: 2015-03-24 09:52:13
categories: IT技術
tags:
- "OS X"
- Mac
---

我的 MacBookPro 升級到 OS X 10.10 的另一個災難，那就是 Windows Client 再也無法使用 Mac 分享出來的「共用資料夾」！   ＝..＝
<!-- more -->
家裡有台 Windows Server 2008 R2 的電腦，經常需要透過「檔案總管」，去存取位於 Mac 電腦端的共享資料夾。

當我的 MacBookPro ，其作業系統還是 OS X 10.9 的時候，自 Windows Server 2008 R2 的電腦，去存取 Mac 端共享資料夾的檔案，一切運作良好。

但......，升級到 OS X 10.10 之後，我想「外甥打燈籠－照舊」，仍自 Windows Server 2008 R2 電腦的檔案總管，去存取 Mac 端的共享資料夾......

這時，Windows 端會跳出以下這對話方塊，跟我做使用者身份的驗證工作。（這時心中已暗叫：不妙！）

{% img https://lh3.googleusercontent.com/-npZgrmNxm94/VFTzcQWCftI/AAAAAAAAeL0/1bX2iV6mP7s/s429/2014-11-01_22-40-00.png %}

我一再地重複輸入「使用者帳戶名」及「密碼」，無論做幾十次，通通過不了關！  QQ

被這問題困擾了近兩週，今天發狠，下定決心要跟這個問題奮戰。搞了快一天，才找到問題的解決方法。

## 【問題導因】

網路上的文章說：「在 OS X 10.10 ，變更了 Mac 電腦所使用的 SMB 通信協定，改為 SMB3.......」。因此個人推斷，這就是為什麼原來可正常運作的網路分享，竟會變成異常的原因。

## 【解決方案】

解決上述問題的解法，就是要變更 Windows Server 2008 R2 電腦端的「網路安全性：LAN Manager驗證等級」設定，將它自原先的「傳送 LM 和 NTLM－ 如有交涉，使用 NTLMv2 工作階段安全性」，改成「只傳送 NTLMv2 回應」。

其設定的操作程序，如下所示：

 1. 點擊〔開始〕鈕。
    {% img https://lh3.googleusercontent.com/-qnaEsuIqJuw/VFTuwLfLDCI/AAAAAAAAeLc/pMfcW7KFiNo/s698/MacShare-01.png %}

 2. 點擊〔所有程式〕／〔系統管理工具〕／〔本機安全性原則〕。
    {% img https://lh3.googleusercontent.com/-OLT--5tgKK8/VFTuwKdXOfI/AAAAAAAAeLU/Z54dUHclygw/s398/MacShare-02.png %}

 3. 在〔本機安全性原則〕視窗，於左邊窗格，點選〔本機原則〕／〔安全性選項〕。
    {% img http://3.bp.blogspot.com/-bTiYB18k_Go/VFTuwJrqCSI/AAAAAAAAeLY/kQ04OXkF7uk/s1600/MacShare-03.png %}

 4. 於右窗格，透過捲軸調整清單的可視範圍，直到可以看到〔網路安全性：LAN Manager驗證等級〕項目。

 5. 雙擊〔網路安全性：LAN Manager驗證等級〕項目。

 6. 在〔網路安全性：LAN Manager驗證等級－內容〕視窗，透過下拉式選項清單，變更選項成〔只傳送 NTLMv2 回應〕。點擊〔確定〕鈕。
    {% img 'https://lh3.googleusercontent.com/-OK0MLr_4ZtY/VFTuwzYrHAI/AAAAAAAAeLo/3DawE5HnxuY/s465/MacShare-04.png' %}

 7. 關閉〔本機安全性原則〕視窗。（設定到此完成）


## 【後記】

在 Mac 電腦端，如何設定資料夾的共享；如何自 Windows 端電腦連上 Mac 電腦，使用 Mac 共享的資料，對此設定仍有困惑的朋友，可參考這篇「[How to Share Folders from Mac OS X with Windows 7 & Windows 8 PCs](http://www.7tutorials.com/how-share-os-x-folders-windows-7)」網路PO文。
