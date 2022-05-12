# API--JDK8--ChronoUtil

### JDK8

#### API

##### jdk8后新增的功能，学会ChronoUtil对象的功能

创建测试类

```java
package com.itheima.d4_jdk8_time;
import java.time.LocalDateTime;
import java.time.temporal.ChronoUnit;
public class Demo9ChronoUnit {
    public static void main(String[] args) {
        LocalDateTime today = LocalDateTime.now();
        System.out.println(today);
        LocalDateTime birthday = LocalDateTime.of(1999, 12, 1, 12, 1, 12, 1);
        System.out.println(ChronoUnit.YEARS.between(birthday, today));//第二个参数减去第一个参数
        //进行两个时间之间的运算
    }
}

```

