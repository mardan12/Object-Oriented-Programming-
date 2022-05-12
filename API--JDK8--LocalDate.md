# API--JDK8--LocalDate

## Java SE

### JDK8

#### API

##### jdk8后新增的功能，学会日期对象的功能

###### 创建测试类

```java
package com.itheima.d4_jdk8_time;
import java.time.LocalDate;
/**
 * ----学会jdk8更新后的时间对象功能----
 */
public class Demo1LocalDate {
    public static void main(String[] args) {
        //1.获取本地日期对象
        LocalDate localDate = LocalDate.now();
        System.out.println(localDate);//2022-05-09--现在的年月日
        System.out.println(localDate.getYear());//2022---年
        System.out.println(localDate.getMonth());//MAY---月
        System.out.println(localDate.getMonth().getValue());//5--值
        System.out.println(localDate.getMonthValue());//也可以这样~
        System.out.println(localDate.getDayOfMonth());//9--当月的第几天
        System.out.println(localDate.getDayOfWeek());//MONDAY--当星期的第几天--星期几
        System.out.println(localDate.getDayOfWeek().getValue());//1---值
        System.out.println(localDate.getDayOfYear());//129---当年的第几天
        System.out.println("------------------------------------");
        LocalDate bt = LocalDate.of(1999,12,1);
        System.out.println(bt);
        System.out.println(LocalDate.of(1999, 12, 1));
    }
}

```

