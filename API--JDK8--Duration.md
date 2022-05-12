# API--JDK8--Duration

### JDK8

#### API

##### jdk8后新增的功能，学会Duration对象的功能

###### 创建测试类

```java
package com.itheima.d4_jdk8_time;
import java.time.Duration;
import java.time.LocalDateTime;
public class Demo8Duration {
    public static void main(String[] args) {
        //本地日期时间对象
        LocalDateTime today = LocalDateTime.now();
        System.out.println(today);
        //出生的日期时间对象
        LocalDateTime birthday = LocalDateTime.of(1999,12,1,12,1,12,1);
        System.out.println(birthday);
        Duration duration = Duration.between(birthday,today);//第二个参数减去第一个
        System.out.println(duration.toDays());//两个时间差的天数
        System.out.println(duration.toHours());//两个时间差的小时数
        System.out.println(duration.toMinutes());//两个时间差的分钟数
        System.out.println(duration.toSeconds());//两个时间差的秒数
        System.out.println(duration.toMillis());//两个时间差的毫秒数
        System.out.println(duration.toNanos());//两个时间差的天纳秒数
    }
}

```

