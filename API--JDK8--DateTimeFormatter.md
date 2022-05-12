# API--JDK8--DateTimeFormatter

### JDK8

#### API

##### jdk8后新增的功能，学会日期时间格式化对象的功能

###### 创建测试类

```java
package com.itheima.d4_jdk8_time;
import java.time.LocalDateTime;
import java.time.format.DateTimeFormatter;
public class Demo6DateTimeFormatter {
    public static void main(String[] args) {
        //本地此刻日期时间对象
        LocalDateTime ldt = LocalDateTime.now();
        System.out.println(ldt);//2022-05-10T16:33:51.315539400
        //解析格式化器
        DateTimeFormatter dtf = DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm:ss EEE a");
        System.out.println(dtf.format(ldt));
        //逆向式格化
        System.out.println(ldt.format(dtf));
        //解析字符串时间
        DateTimeFormatter dtf1 = DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm:ss");
        //解析当前字符串时间成为本地日期时间对象
        LocalDateTime ldt1 = LocalDateTime.parse("2019-11-11 11:11:11",dtf1);
        System.out.println(ldt1);
        //可以拿这个对象来操作，拿取年中的第几天等
        System.out.println(ldt1.getDayOfYear());
    }
}

```

