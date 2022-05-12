# API--JDK8--Period

### JDK8

#### API

##### jdk8后新增的功能，学会Period对象的功能

###### 创建测试类

```java
package com.itheima.d4_jdk8_time;
import java.time.LocalDate;
import java.time.Period;
public class Demo7Period {
    public static void main(String[] args) {
        //当前本地年月日
        LocalDate today = LocalDate.now();
        System.out.println(today);
        //生日的年月日
        LocalDate brithDate = LocalDate.of(1999,12,1);
        System.out.println(brithDate);
        Period period = Period.between(brithDate,today);
        //System.out.println("您活了"+period.getYears()+"年"+ period.getMonths()+"月"+ period.getDays()+"天");
        System.out.printf("年龄：%d岁 %d月 %d天",period.getYears(),period.getMonths(),period.getDays());
    }
}

```

