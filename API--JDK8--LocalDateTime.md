# API--JDK8--LocalDateTime

## Java SE

### JDK8

#### API

##### jdk8后新增的功能，学会时间日期对象的功能

##### Demo 1

###### 创建测试类

```java
package com.itheima.d4_jdk8_time;
import java.time.LocalDate;
import java.time.LocalDateTime;
import java.time.LocalTime;

/**
 * LocalDateTime更完全
 */
public class Demo3LocalDateTime {
    public static void main(String[] args) {

        LocalDateTime nowDateTime = LocalDateTime.now();
        System.out.println(nowDateTime);//2022-05-09T18:22:33.990886600
        //LocalDateTime包含着LocalTime和LocalDate
        //有api把这个对象转换成LocalTime和LocalDate对象
        System.out.println("----------------------------");
        LocalDate localDate = nowDateTime.toLocalDate();
        LocalTime localTime = nowDateTime.toLocalTime();
        System.out.println(localDate);//2022-05-09
        System.out.println("----------------------------");
        System.out.println(localTime);//18:31:43.374951500
    }
}

```

##### Demo 2

###### 创建测试类

```java
package com.itheima.d4_jdk8_time;

import java.time.LocalDate;
import java.time.LocalTime;
import java.time.MonthDay;

public class Demo4UpDateTime {
    public static void main(String[] args) {
        LocalTime time = LocalTime.now();
        System.out.println(time);//当前时间
        System.out.println("-------------------------------");
        System.out.println(time.minusHours(1));//一个小时前
        System.out.println(time.minusMinutes(1));//一分钟前
        System.out.println(time.minusSeconds(1));//一秒钟前
        System.out.println(time.minusNanos(1));//一纳秒前
        System.out.println("------------------------------");
        System.out.println(time.plusHours(1));//一个小时后
        System.out.println(time.plusMinutes(1));//一分钟后
        System.out.println(time.plusSeconds(1));//一秒钟后
        System.out.println(time.plusNanos(1));//一纳秒后
        System.out.println("----------------------------");
        //不可变对象，每次修改都会创建新的对象
        System.out.println(time);
        LocalDate myDate = LocalDate.of(2022,5,8);
        LocalDate nowDate = LocalDate.now();
        //相等比较
        System.out.println("今天是2022-5-9吗？"+(nowDate.equals(myDate) ? "是":"不是"));
        //xxx.是在之后（yyy）    true --- false
        System.out.println(myDate+"是否在"+nowDate +"之后？"+myDate.isAfter(nowDate));
        //xxx.是在之前（yyy）    true --- false
        System.out.println(myDate+"是否在"+nowDate +"之前？"+myDate.isBefore(nowDate));
        System.out.println("-----------------------------");
        //判断是否是你生日
        //你生日
        LocalDate birDate = LocalDate.of(1999,5,9);
        //现在的时间
        LocalDate date = LocalDate.now();
        //创建月日对象，拿取你生日的月和日包装到对象
        MonthDay birMd = MonthDay.of(birDate.getMonthValue(),birDate.getDayOfMonth());
        MonthDay birMd1 = MonthDay.from(birDate);
        //直接从date对象中拿取月日包装到nowMd对象中
        MonthDay nowMd = MonthDay.from(date);
        System.out.println("今天是你生日吗?"+(nowMd.equals(birMd)? "是":"不是"));
        System.out.println("今天是你生日吗?"+(nowMd.equals(birMd1)? "是":"不是"));
    }
}

```

