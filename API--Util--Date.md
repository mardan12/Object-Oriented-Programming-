# API--Util--Date

## Java SE

### Date类的使用

###### 创建测试类

```java
package com.itheima.d1_date;

import java.util.Date;

/**
 * 目标： 学会date类处理时间，获取时间的信息
 */
public class DateDemo1 {
    public static void main(String[] args) {
        //创建一个date类的对象：代表系统此刻日期时间对象
        Date d = new Date();
        System.out.println(d);
        //获取时间毫秒值
        System.out.println(d.getTime());
        System.out.println(System.currentTimeMillis());
        System.out.println("------------------------------------------");
        //得到当前的时间
        Date d1 = new Date();
        System.out.println(d1);
        //当前时间往后走一个小时121秒
        long time = System.currentTimeMillis();
        time += (60*60+121)*1000;
        //把毫秒值变成对应的日期
        System.out.println("---------------------------------------------");
        Date d2 = new Date(time);
        System.out.println(d2);
        System.out.println("-----------------------------------------");
        Date d3 = new Date();
        d3.setTime(time);
        System.out.println(d3);
    }
}

```

