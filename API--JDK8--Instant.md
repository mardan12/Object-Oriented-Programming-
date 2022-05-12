# API--JDK8--Instant

### JDK8

#### API

##### jdk8后新增的功能，学会时间戳对象的功能

###### 创建测试类

```java
package com.itheima.d4_jdk8_time;
import java.text.SimpleDateFormat;
import java.time.Instant;
import java.time.ZoneId;
import java.util.Date;
public class Demo5instant {
    public static void main(String[] args) {
        //得到一个instant时间戳对象
        Instant instant = Instant.now();
        //全国统一的时间--跟中国有八个小时的差距
        System.out.println(instant);
        //得到系统此刻的时间戳怎么办？
        System.out.println(instant.atZone(ZoneId.systemDefault()));
        //如何去返回Date对象
        Date date = Date.from(instant);
        System.out.println(date);

        System.out.println("---------------------------------------");
        System.out.println(new SimpleDateFormat("yyyy-MM-dd HH:mm:ss EEE a")
                .format(Date.from(Instant.from((Instant.now().atZone(ZoneId.systemDefault()))))));
        System.out.println(date.toInstant());
    }
}

```

