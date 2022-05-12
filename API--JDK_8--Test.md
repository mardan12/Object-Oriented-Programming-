# API--JDK_8--Test

## Java SE

### Time,Date,SimpleDateFormat,Period,Duration,ChronoUtil

#### 综合练习

###### 创建测试类

```java
package com.itheima.d4_jdk8_time;
import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.time.Instant;
import java.time.LocalDate;
import java.time.Period;
import java.time.ZoneId;
import java.time.format.DateTimeFormatter;
import java.time.temporal.ChronoUnit;
import java.util.Date;
import java.util.Scanner;

public class Test {
    static Scanner sc = new Scanner(System.in);
    public static void main(String[] args) throws ParseException {
            scanner();
    }
    public static void scanner() throws ParseException {
        System.out.println("请输入出生年：");int year = sc.nextInt();
        System.out.println("请输入出生月：");int month = sc.nextInt();
        System.out.println("请输入出生日：");int day  = sc.nextInt();
        LocalDate birthday = LocalDate.of(year, month, day);
        LocalDate currentDate = LocalDate.now();
        System.out.println("现在是中国时间："+new SimpleDateFormat("yyyy-MM-dd HH:mm:ss EEE a").format(Date.from(Instant.from(Instant.now().atZone(ZoneId.systemDefault())))));
        System.out.println(currentDate.equals(birthday) ? "今天是您生日哟，祝您生日快乐~~" : "今天不是您生日哟!!" +"离您生日还有《"+ Math.abs(ChronoUnit.DAYS.between(LocalDate.of(currentDate.getYear(),month,day), currentDate))+"》天");
        Period period = Period.between(birthday, currentDate);
        System.out.printf("年龄：%d岁 %d月 %d天\n",period.getYears(),period.getMonths(),period.getDays());
        System.out.println("您的生日是：" + new SimpleDateFormat("yyyy年MM月dd日").format(new SimpleDateFormat("yyyy-MM-dd").parse(DateTimeFormatter.ofPattern("yyyy-MM-dd").format(birthday))));

    }
}

```

