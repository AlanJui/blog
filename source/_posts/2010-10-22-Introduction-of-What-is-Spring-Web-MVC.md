---
title: "了解什麼是 Spring Web MVC"
date: 2010-10-22 20:51:10
categories: IT技術
tags:
- Java
- UML
- Spring
---

循前例，我還是自NetBeans的官網，取用如下之教學指引，以為自修研習用教材，開始了我對 Spring 的初步探究--「Spring是什麼東東啊？」
<!-- more -->

[Introduction to Spring Web MVC](https://netbeans.org/kb/docs/web/quickstart-webapps-spring.html)

## 文件導讀

上述教材研讀及實作完畢後，摘錄心得如下，當成是自己的讀書筆記，也希望對需要了解Spring的朋友，能提供那麼一點助益。

根據教材內容的說明，可知此處所探討的只是Spring Web MVC的運作原理，可能這教材裡的說明，只是讓我們了解在 Spring Framework 下，Controller、View、Model 三種類別是如何協同運作，還不能算是給了 Spring Framework 的總體概述。

此教材主要的章節架構如下：

 * Setting up a New Project with Spring Web MVC Support
 * Overview of the Application
 * Implementing a Service
 * Implementing the Controller and Model
 * Implementing the Views

對於以上之章節，可將「Setting up a New Project with Spring Web MVC Support」章節視為本文章的第一篇。

至於「Overview of the Application」到「Implementing the Views」的章節，則屬於本文章的第二篇。

## 第一篇內容摘要

### 認識DispatcherServlet

指導NetBeans的使用者，如何透過專案建置精靈，建立一個支援Spring Framework 3.0的NetBeans專案資料夾。

完成了上述專案建置工作後，即可依據教材中的指示，體驗一下，Spring有什麼樣的特性。

第一件要了解的事，偉大的DispatcherServle：從web.xml檔案內容的描述，可以發覺在Spring Framework有著一個神奇的Servlet，它的名字叫DispatcherServlet。從以下自web.xml節錄的內容，可以看出，只要有使用者對伺服器發出讀取.htm檔案的Request時，往後的處理工作，皆由偉大的DispatcherServlet來負責操盤。

{% codeblock lang:java %}
<servlet>
    <servlet-name>dispatcher</servlet-name>
    <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
    <load-on-startup>2</load-on-startup>
</servlet>
<servlet-mapping>
    <servlet-name>dispatcher</servlet-name>
    <url-pattern>*.htm</url-pattern>
</servlet-mapping>
{% endcodeblock %}

第二件要了解的事，網站的首頁是如何被找到的：別懷疑，同時，我也沒有侮辱您的專業。本來網站的首頁用腳指想也知，不是index.hm；就是index.jsp檔案。

可是，從下列web.xml的設定，可知以上皆非，預設為redirect.jsp。

```java
<welcome-file-list>
    <welcome-file>redirect.jsp</welcome-file>
</welcome-file-list>
```


當redirect.jsp檔案打開後，可以看到如下的內容：

``` java
<% response.sendRedirect(“index.htm”); %>
```

結果.....，才知，這網站的首頁仍由index.htm擔綱。但是.....，在Web Pages之下，根本沒有index.htm這個檔案啊！

![](http://lh3.googleusercontent.com/_40BYSx3mIfk/TME2a3TF0qI/AAAAAAAAA4s/q8rhJEdeCiM/s1600/image%5B2%5D.png)

可是......，這個網站在執行時候，明明可以看到如下的網頁內容，同時，在Web瀏覽器中的URL網址，也出現了index.htm啊！

![](http://lh3.googleusercontent.com/_40BYSx3mIfk/TME2cLkOd7I/AAAAAAAAA40/2_UylvnIRgA/s1600/image%5B6%5D.png)

如果你不死心到處找，可以在路徑「___Web Pages\WEB-INF\jsp\___」處，找到一個最最最標準的首頁檔案**index.jsp**。

![](http://lh3.googleusercontent.com/_40BYSx3mIfk/TME2dvrnzqI/AAAAAAAAA48/jTuOjbVwSek/s1600/image%5B12%5D.png)

把這個網頁檔案打開後，可以查覺其內容，跟前述網站首頁內容是相同的。

![](http://lh3.googleusercontent.com/_40BYSx3mIfk/TME2fERSynI/AAAAAAAAA5E/9vG6XkB1ef8/s1600/image%5B16%5D.png)

啊......！現在是怎麼回事？怎麼會這樣？



### 謎題的解答dispatcher-servlet.xml

其實在網站所見的首頁內容，其來源正是出自index.jsp。但是，從要進入index.htm網頁，卻是顯示index.jsp的「無中生有」過程，是怎麼回事？以下我們來一一分解詳述：

由於redirect.jsp檔案，說要將網頁轉到index.htm。所以，根據web.xml的設定，只要是*.htm檔案，通通交由DispatcherServlet負責。

當DispatcherServlet這個血統純正的Java Servlet，聽說有人要求瀏覽index.htm網頁的內容時，便會查閱 ***dispatcher-servlet.xml*** 檔案中的設定，並嚴格遵循當中的規矩，照章行事。

當DispatcherServlet讀到 id 為 __urlMapping__ 的 __bean__ 設定，它知道若有人要看 "/index.htm" 的檔案時，它要以 __indexController__ 頂替 。

於是DispatcherServlet，再到 __dispatcher-servlet.xml__ 檔案尋找 name 為 indexController 的 bean 。結果，自 __p:viewName__ 的屬性查出，indexController 要找主要檔名叫 index 的檔案。

最後，DispatcherServlet藉由 id 為 __viewResolver__ 的 bean ，其中的 __p:prefix__ 、 __p:suffix__ ，查出主檔名為 index 的檔案，要到路徑為「***/WEB-INF/jsp/***」處尋找；找到這個檔案後，再配以 __jsp__ 的副檔名。

![](http://lh3.googleusercontent.com/_40BYSx3mIfk/TME2g4cp0mI/AAAAAAAAA5M/CKWLHGG6_OE/s1600/image%5B21%5D.png)

經過上述無中生有的過程，DispatcherServlet終於完成解讀，知道有人要看 index.htm 時，就給它 /WEB-INF/jsp/index.jsp 的檔案。

瞭了嗎？！

只是.....，不過是要喝杯牛奶，幹啥要自行蓋個牧場來養牛，生產年奶。為什麼要把事情搞得這麼大，如此複雜？別問我，我那知！



## 第二篇內容摘要

### Spring Web MVC運作架構

這篇教材真正的重點，從此處開始。它用了如下的應用例子，說明在 Spring Framework 下MVC是怎樣運作的。

假設您的網站要提供一個功能，這功能會透過一個網頁向使用者詢問其姓名。當使用者輸入了姓名之後，則會用另一個網頁向使用者說聲嗨！

有了上述初步的功能需求後，在設計上我們需使用 2 個 __View__，以 nameView.jsp 網頁來向使用者詢問，要求輸入姓名。使用者輸入的姓名，經過系統的處理後，再透過名為helloView.jsp 的網頁，向使用者 Say Hello。且此功能的啟動執行點，設計成「當使用者瀏覽 __/hello.htm__ 網頁便執行」。

在 Spring Web MVC 的設計模式下，View (可以直接想成網頁) 之間的切換係由 Controller 的類別 (亦即 MVC 中的 Control) 來控制。所以，依據上述的設計規格，我們需要有個名為 helloController ，屬 __Controller__ 的類別，以便有人想瀏覽 /hello.htm 網頁時，便提供 nameView.jsp 給他；待取得使用者輸入的姓名後，則再顯示 helloView.jsp 網頁給使用者。

關於使用者在 nameView.jsp 輸入的資料，可以使用一名為 __Name__ ，屬 __Model__ 的類別，用以接收輸入的結果。

至於從使用者接收到的資料，該做什麼處理，完成什麼樣的輸出，這活就由屬 __Service__ (亦即一般所謂之 ***Business Logic***) 的類別來幹。因此，根據設計，需要一名為 _helloService_ 的類別，以便能將使用者輸入的姓名進行加工處理。

綜合上述，整個功能的運作過程，所需使用的網頁及類別，其設計可以用以下，UML 的穩建圖來表示：

![](http://lh4.ggpht.com/_40BYSx3mIfk/TME2jaihn8I/AAAAAAAAA5Y/3J-7uQf-RLo/image_thumb%5B12%5D.png?imgmax=800)

上圖的 __dispatcher-servlet.xml__ ，用於表示 helloController 類別須在這個檔案內做登記。同樣，helloService 類別的存在，亦須記錄相關設定在 __applicationContext.xml__ 檔案之中。 如此，helloController 類別才能正常運作。甚至說得更白點，非得這樣做，Web Container 才有辦法，遇到有人要瀏覽 /hello.htm 時， 知道該怎麼做。

根據上述設計，需要撰寫製作的網頁及各個類別(class)，在專案資料夾的放置處，則如下圖所示：

![](http://lh3.googleusercontent.com/_40BYSx3mIfk/TME2kDdeB2I/AAAAAAAAA5c/gtVGg8Txwdg/s1600/image%5B34%5D.png)

### 研習須細讀重點

有了上述 Spring Web MVC 在架構上的認知後，請再加強下列事項的研習。

__HelloController.java 的建構子__：細讀其程式碼，了解 Controller 啟動後，怎麼知道該先顯示那個網頁，然後又該顯示那個網頁。網頁輸入的資料，要用那個類別去接收；當靜態的類別(class)變成可執行的物件(object)時，要用什麼作為變數名稱。

__HelloController.java 的 onSubmit 方法__：當第一個網頁完成輸入 (nameView.jsp)，onSubmit 事件發生後，Controller 要如何接收第一個網頁所傳來的輸入；然後又如何透過 Service ，對輸入的資料進行加工，完成輸出；最後又如何將加工後輸出，餵給第二個網頁 (helloView.jsp)。

__nameView.jsp網頁__：研究網頁中，屬 Spring 專用的 Tag 如何自 Controller 接收由 Name 類別所產生的 ***name*** 物件。而使用者的輸入，如何以 Spring Tag ，將之存入 name 物件中的 value 屬性。

__helloView.jsp網頁__：研究網頁中欲輸出的內容，如何能透過 EL 表示式 ***${helloMessage}*** 顯示出來。EL 表示中的變數 helloMessage ， 與 HelloController 類別中的 onSubmit 方法，有什麼互為因果的關係。



## 總結

哇！好棒！終於寫完了。這篇文章花了我 5 小時，才搞定。可是這篇文章的內容，我花了一天讀完，又再花了三天反覆思考 Spring Web MVC 運作的架構；網頁、Controller類別、Service類別、Model類別各個之間的互動關係；三個設定檔 web.xml 、 dispatcher-servlet.xml 、applicationContext.xml 各個的作用。

這個研習過程，對我而言有些吃力。因此，希望我這研究心得報告，可以幫大家減少一些學習過程的障礙。
