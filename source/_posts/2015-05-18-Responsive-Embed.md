---
title: "讓網頁內的影片、地圖能自動調整顯示寬度"
date: 2015-05-18 20:10:33
categories: IT技術
tags:
- Web
- Markdown
- HTML
- CSS
---

這年頭，網頁技術時興 RWD (Responsive Web Design) 。放在網站上的網頁，你得考量使用者是使用什麼樣的「裝置（Device）」來閱讀。

「網頁」本身須具備「見人說人話，見鬼說鬼話」的本事；要能依據閱讀使用裝置螢幕的寬度，將網頁的內容重新排版，以提供閱讀網頁時最佳的格式。

![](http://img.labnol.org/di/responsive-google-maps.gif)
<!-- more -->
最近發覺，我部落格中放入的「Google地圖」、「YouTube影片」都有一個共同的問題，那就是：在「電腦螢幕」看時，一切 OK ；但若是到「手機螢幕」閱瀏，都有圖片過大，超過頁面右邊界的問題。

在網路上尋找解法配方，結果均有所獲。做個筆記，分享這些先知的妙法、良方！  ^^y

## 令 Google 地圖可自動調寬度的作法

參考這篇文章提供的內容：
[《How to Make Google Maps Embeds Responsive》](http://www.labnol.org/internet/embed-responsive-google-maps/28333/)

想要在網頁中放入一個長寬為： 450 x 600 的 Google 地圖，其內容如下：

```html
<iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d28936.799438545575!2d121.64887512170407!3d24.96271450708865!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x3467ffe48f4f609d%3A0x2af02bac3ed123d3!2z5paH5bGx6I2J5aCC!5e0!3m2!1szh-TW!2stw!4v1431754924154" width="640" height="480" frameborder="0" style="border:0"></iframe>
```

先在 CSS 檔案中，加入如下所示 Class 樣式：

{% codeblock 'CSS樣式設定：' lang:css %}
.google-maps {
  position: relative;
  padding-bottom: 75%;
  height: 0;
  overflow: hidden;
}

.google-maps iframe {
  position: absolute;
  top: 0;
  left: 0;
  width: 100% !important;
  height: 100% !important;
}
{% endcodeblock %}

然後在「網頁」或「Markdown」檔案中，使用 div 這個 tag ，置入 Google 地圖的內容：

```html
<div class="google-maps">
  <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d28936.799438545575!2d121.64887512170407!3d24.96271450708865!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x3467ffe48f4f609d%3A0x2af02bac3ed123d3!2z5paH5bGx6I2J5aCC!5e0!3m2!1szh-TW!2stw!4v1431754924154" width="640" height="480" frameborder="0" style="border:0"></iframe>
</div>
```

**成果：**

<div class="google-maps">
  <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d28936.799438545575!2d121.64887512170407!3d24.96271450708865!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x3467ffe48f4f609d%3A0x2af02bac3ed123d3!2z5paH5bGx6I2J5aCC!5e0!3m2!1szh-TW!2stw!4v1431754924154" width="640" height="480" frameborder="0" style="border:0"></iframe>
</div>

## 令 YouTube 影片可自動調寬度的作法

參考這篇文章提供的內容：
[《Responsive Youtube Embed》](http://avexdesigns.com/responsive-youtube-embed/)

想要在網頁中放入一個長寬為： 560 x 315 的 Youtube 影片，其內容如下：

```html
<iframe width="560" height="315" src="https://www.youtube.com/embed/8ChCu6ivL5o?rel=0" frameborder="0" allowfullscreen></iframe>
```

先在 CSS 檔案中，加入如下所示的 Class 樣式：

{% codeblock 'CSS樣式設定：' lang:css %}
.youtube-video {
  position: relative;
  padding-bottom: 56.25%;
  padding-top: 30px; height: 0; overflow: hidden;
}

.youtube-video iframe,
.youtube-video object,
.youtube-video embed {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}
{% endcodeblock %}

然後在「網頁」或「Markdown」檔案中，使用 div 這個 tag ，置入 Youtube 影片的內容：

```html
<div class="youtube-video">
  <iframe width="560" height="315" src="https://www.youtube.com/embed/8ChCu6ivL5o?rel=0" frameborder="0" allowfullscreen></iframe>
</div>
```

**成果：**

<div class="youtube-video">
  <iframe width="560" height="315" src="https://www.youtube.com/embed/8ChCu6ivL5o?rel=0" frameborder="0" allowfullscreen></iframe>
</div>

試著在「電腦螢幕」、「平板螢幕」及「手機螢幕」各種不同寬度的畫面瀏覽，驗證一下效果吧！
