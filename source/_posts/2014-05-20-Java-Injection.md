---
title: "Java注入相依關係的妙用"
date: 2014-05-20 16:02:07
categories: IT技術
tags:
- Java
---

軟體專家告訴哦棉，好的程式設計，要寫成「耦合鬆綁（decouple）」，這樣，每個程式單元，才能隨時利用，任意組合。

But.................   How?!
<!-- more -->

這裡，有一個例子。假設，我們需要開發一個「腳踏車出租管理系統」，供腳踏車店做出租服務。

第一個想開發的功能是：「在螢幕列出店裡所有的腳踏車」。

對於這個功能，我們可以這樣做。

先開發一個： Bike（腳踏車）的 Entity 類別，其程式碼如下。

### Bike 類別

```java
package tw.ccc99.bpandsvc;

/**
 * Created by AlanJui on 2014/5/17.
 */
public class Bike {

    private String manufacturer;
    private String model;
    private int frame;
    private String serialNo;
    private double weight;
    private String status;

    public Bike(String manufacturer, String model, int frame, String serialNo, double weight, String status) {
        this.manufacturer = manufacturer;
        this.model = model;
        this.frame = frame;
        this.serialNo = serialNo;
        this.weight = weight;
        this.status = status;
    }

    public String getManufacturer() {
        return manufacturer;
    }

    public void setManufacturer(String manufacturer) {
        this.manufacturer = manufacturer;
    }

    public String getModel() {
        return model;
    }

    public void setModel(String model) {
        this.model = model;
    }

    public int getFrame() {
        return frame;
    }

    public void setFrame(int frame) {
        this.frame = frame;
    }

    public String getSerialNo() {
        return serialNo;
    }

    public void setSerialNo(String serialNo) {
        this.serialNo = serialNo;
    }

    public double getWeight() {
        return weight;
    }

    public void setWeight(double weight) {
        this.weight = weight;
    }

    public String getStatus() {
        return status;
    }

    public void setStatus(String status) {
        this.status = status;
    }

    public String toString() {
        return "Bike : " +
                "manufacturer -- " + manufacturer +
                "\n: model -- " + model +
                "\n: frame -- " + frame +
                "\n: serialNo -- " + serialNo +
                "\n: weight -- " + weight +
                "\n: status -- " + status +
                ".\n";
    }
}
```

再開發一個：RentABike （租台腳踏車）的類別，用來管理腳踏車出租店的租借業務。在此類別先實作了 2 個方法（method），（1）getBikes：取得店裡所有的腳踏車；（2）getBike ：依「序號」取得某一台特定的腳踏車，其程式碼如下。

### RentABike 類別

```java
package tw.ccc99.bpandsvc;

/**
 * Created by AlanJui on 2014/5/17.
 */

import java.util.*;

public class RentABike {

    private String storeName;
    final List<Bike> bikes = new ArrayList<Bike>();

    public RentABike(String storeName) {
        this.storeName = storeName;
        bikes.add(new Bike("Shimano", "Roadmaster", 20, "11111", 15, "Fair"));
        bikes.add(new Bike("Cannondale", "F2000 XTR", 18, "22222", 12, "Excellent"));
        bikes.add(new Bike("Trek", "6000", 19, "33333", 12.4, "Fair"));
    }

    @Override
    public String toString() {
        return "RentABike: " + storeName;
    }

    public List<Bike> getBikes() {
        return bikes;
    }

    public Bike getBike(String serialNo) {
        Iterator<Bike> iter = bikes.iterator();
        while (iter.hasNext()) {
            Bike bike = iter.next();
            if (serialNo.equals(bike.getSerialNo())) return bike;
        }
        return null;
    }
}
```

為了在螢幕上顯示店裡所有的腳踏車，我們又多開發了一個：「CommandLineView」類別，其程式碼如下。

### CommandLineView 類別

```java
package tw.ccc99.bpandsvc;

/**
 * Created by AlanJui on 2014/5/17.
 */

import java.util.*;
public class CommandLineView {

    private RentABike rentABike;

    public CommandLineView() {
        rentABike = new RentABike("Bruce's Bikes");
    }

    public void printAllBikes() {
        System.out.println(rentABike.toString());
        Iterator<Bike> iter = rentABike.getBikes().iterator();
        while (iter.hasNext()) {
            Bike bike = iter.next();
            System.out.println(bike.toString());
        }
    }

    public static final void main(String[] args) {
        CommandLineView clv = new CommandLineView();
        clv.printAllBikes();
    }
}
```

一般的寫法，我們會很自然地在 CommandLineView 這個類別裡，先用 RentABike 類別建立一個 rentABike 物件。

然後，再利用 rentABike 物件，呼叫方法 － getBikes() ，取出店裡所有的腳踏車。接著在 CommandLineView 類別中，利用迴圈，在螢幕列示出所有的腳踏車。

以上的作法，既簡單，又直覺。但....... 它沒有達到「耦合鬆綁」所要求的程式架構之美！因 CommandLineView 類別與 RentABike 類別，十指緊扣，關係密切啊！ ^^"

那該怎麼辦咧？！

[《Spring 程式高手秘笈》](http://books.google.com.tw/books?id=rnDv9pDj-e0C&pg=PP3&lpg=PP3&dq=spring+%E7%A8%8B%E5%BC%8F%E9%AB%98%E6%89%8B%E7%A7%98%E7%AC%88&source=bl&ots=rwQ3ioGe67&sig=9PwIjxD9WYOn1J9bTfowhTuH42E&hl=zh-TW&sa=X&ei=DqB2U7n1GMWikwXqwICICA&ved=0CIYBEOgBMAg#v=onepage&q=spring%20%E7%A8%8B%E5%BC%8F%E9%AB%98%E6%89%8B%E7%A7%98%E7%AC%88&f=false)這書，在 Page 1 ~ 9 處，教人如何利用 Interface ，進行「相依注入（Dependency Injection）」，讓 CommandLineView 類別，呼叫 getBikes() 方法的這檔事 ，不是寫死在 CommandLineView 類別中，而是由另一個類別，在 Run Time 時期，負責相依關係的相注入，使 CommandLineView 物件，能呼叫  getBikes() 這方法！

這麼神奇的事，是如何做到的？

 1. 原先 RentABike 類別，能提供其它類別使用的 method ，將它當成是 service ，全包進一個名為 RentABike 的 Interface 中。

 2. 另新增一個「service 類別」 ( ArrayListRentABike ) ，須實作 (implements) 上一個 RentABike Interface 。

 3. 要使用「service 類別」，呼叫其中 method 的這種類別，稱作：「client 類別」， 以此例子而言，就是 CommandLineView 類別，它在類別中，須有一個 property ，用來指向「 service 類別」所產生的物件。

 4. 建立一個類別，負責在 Run Time 時期，執行「相依注入」的工作，這種作法，一般被稱作為 assembler 或 container 機制。在這個例子中，由 RentABikeAssembler 類別擔綱。


此相依注入的作法，可用以下的「類別圖」，來說明各個類別之間的相互關係。

{% img http://4.bp.blogspot.com/-30H5WDc1vKE/U3n8885RPJI/AAAAAAAAcuo/6fpssQGG88U/s1600/2014-5-19+%E4%B8%8B%E5%8D%88+08-44-41.png %}

最後，各類別的程式碼，分述如下。

### 將 RentABike 類別改成 Interface

```java
package tw.ccc99.bpandsvc;

/**
 * Created by AlanJui on 2014/5/17.
 */

import java.util.*;

public interface RentABike {
    List<Bike> getBikes();
    Bike getBike(String serialNo);
}
```

### 提供 method 的「Service 類別」：ArrayListRentABike.java

```java
package tw.ccc99.bpandsvc;

/**
 * Created by AlanJui on 2014/5/17.
 */

import java.util.*;

public class ArrayListRentABike implements RentABike {

    private String storeName;
    final List<Bike> bikes = new ArrayList<Bike>();

    public ArrayListRentABike() {
        initBikes();
    }

    public ArrayListRentABike(String storeName) {
        this.storeName = storeName;
        initBikes();
    }

    public void initBikes() {
        bikes.add(new Bike("Shimano", "Roadmaster", 20, "11111", 15, "Fair"));
        bikes.add(new Bike("Cannondale", "F2000 XTR", 18, "22222", 12, "Excellent"));
        bikes.add(new Bike("Trek", "6000", 19, "33333", 12.4, "Fair"));
    }

    @Override
    public String toString() {
        return "RentABike: " + storeName;
    }

    public List<Bike> getBikes() {
        return bikes;
    }

    public Bike getBike(String serialNo) {
        Iterator<Bike> iter = bikes.iterator();
        while (iter.hasNext()) {
            Bike bike = iter.next();
            if (serialNo.equals(bike.getSerialNo())) return bike;
        }
        return null;
    }
}
```

### 使用 method 的「Client 類別」：CommandLineView.java

```java
package tw.ccc99.bpandsvc;

/**
 * Created by AlanJui on 2014/5/17.
 */

import java.util.*;

public class CommandLineView {

    private RentABike rentABike;

    public CommandLineView() {}

    public void setRentABike(RentABike rentABike) {
        this.rentABike = rentABike;
    }

    public RentABike getRentABike() {
        return rentABike;
    }

    public void printAllBikes() {
        for (Bike bike: rentABike.getBikes()) {
            System.out.println(bike.toString());
        }
    }
}
```

### 注入相依的 Assembler 類別：RentABikeAssembler.java

```java
package tw.ccc99.bpandsvc;

/**
 * Created by AlanJui on 2014/5/17.
 */
public class RentABikeAssembler {
    public static final void main(String[] args) {
        CommandLineView clv = new CommandLineView();
        RentABike rentABike = new ArrayListRentABike("Bruce's Bikes");
        clv.setRentABike(rentABike);
        clv.printAllBikes();
    }
}
```

Run Time 時期，由 RentABikeAssembler 類別，負責「注入相依關係」這檔事。

首先，建立一個「Client 物件」： CommandLineView 物件；然後，建立一個「Service 物件」：ArrayListRentABike。

接著令「Client 物件」－ CommandLineView 的 property 指向「Service 件件」 － ArrayListRentABike。最後， CommandLineView 這個「Client 物件」，可以使用 「Service 物件」－ ArrayListRentABike ，提供的 getBikes() 方法，取出店裡所有的腳踏車，丟給類別內的方法處理，顯示在螢幕上 。

透過以上「相依注入」的作法，可達成「耦合鬆綁（decouple）」的目標。軟體開發中所使用的各個類別，就能任意組合，隨時依自己的需要來變化及使用。


***程式碼下載處***： [https://github.com/AlanJui/BPANDSVC](https://github.com/AlanJui/BPANDSVC)
