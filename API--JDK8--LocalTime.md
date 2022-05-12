# API--JDK8--LocalTime

## Java SE

### JDK8

#### API

##### jdk8后新增的功能，学会时间对象的功能

###### 创建测试类

```java
package com.itheima.d4_jdk8_time;

import java.time.LocalDateTime;
import java.time.LocalTime;

public class Demo2LocalTIme {
    public static void main(String[] args) {
        //获取本地时间对象
        LocalTime nowTime = LocalTime.now();
        System.out.println(nowTime);//18:05:53.240868200
        System.out.println(nowTime.getHour());//18--小时
        System.out.println(nowTime.getMinute());//8--分
        System.out.println(nowTime.getSecond());//32--秒
        System.out.println(nowTime.getNano());//945597600--纳秒
        System.out.println("------------------------------------------");
        System.out.println(LocalTime.of(6, 6, 6, 6));//小时、分钟、秒、纳秒
        LocalTime time = LocalTime.of(6,6,6,6);
        System.out.println(time);
        System.out.println("--------------------------------------------");
        System.out.println(LocalDateTime.of(1999, 6, 6, 6, 6, 6, 6));
    }
}

```

