---
title: "Markdown 入門"
date: 2015-04-25 12:05:01
categories: "IT技術"
tags:
- Hexo
---

![Hexo](https://encrypted-tbn1.gstatic.com/images?q=tbn:ANd9GcR9-YiPtxqPWBo38HqxjiOV1Vr87B_tu5HKDQ8OCzZrD68R-cee)

幫自己做個小抄，條列Markdown入門常用的基礎語法！

<!-- more -->
# Markdown 語法

## 標題

### 【語法】：

``` Markdown
# 第一階標題
## 第二階標題
### 第三階標題
#### 第四階標題
##### 第五階標題
###### 第六階標題
```
### 【輸出】：

# 第一階標題
## 第二階標題
### 第三階標題
#### 第四階標題
##### 第五階標題
###### 第六階標題



## 無序號清單（Unordered List）

### 【語法】：
```
* 蘋果
* 洋蔥
* 蕃茄
```

### 【輸出】：
* 蘋果
* 洋蔥
* 蕃茄



## 無序號清單（Ordered List）

### 【語法】：
```
1. 關啟電源
2. 插好音源線
3. 按「播放」鈕
```

### 【輸出】：
1. 關啟電源
2. 插好音源線
3. 按「播放」鈕



## 帶有標題的清單（Definition List）

`《註》：這不是 Markdown 的語法，但在.MD檔案中，可使用的 HTML 語法。`

### 【語法】：
```
<dl>
  <dt>驗證（Verification，VER）</dt>
  <dd>發展中的工作產品，能符合「規格」中定義的需求。</dd>
  <dt>確認（Validation，VAL）</dt>
  <dd>交付的產品在「上線」的環境中運作，能滿足預期的使用需求。</dd>
</dl>
```

### 【輸出】：
<dl>
  <dt>驗證（Verification，VER）</dt>
  <dd>發展中的工作產品，能符合「規格」中定義的需求。</dd>
  <dt>確認（Validation，VAL）</dt>
  <dd>交付的產品在「上線」的環境中運作，能滿足預期的使用需求。</dd>
</dl>

## 表格（Table）

  * 第一欄：靠左排列
  * 第二欄：靠中排列
  * 第三欄：靠右排列

### 【語法】：
```
|Product   |      Spec.          |   Price   |
|----------|:-------------------:|----------:|
|HDD       | 7200 RPM, 540 GB    | $30,000   |
|Monitor   | 1280 x 1024         | $6,000    |
```

### 【輸出】：
|Product   |      Spec.          |   Price   |
|----------|:-------------------:|----------:|
|HDD       | 7200 RPM, 540 GB    | $30,000   |
|Monitor   | 1280 x 1024         | $6,000    |
