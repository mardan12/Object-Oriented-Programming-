# API--Util--Calender

## Java SE

### API

#### 日历对象的简单使用

###### 创建测试类

```java
package com.itheima.d3_calender;
import java.text.SimpleDateFormat;
import java.util.Calendar;
public class CalenderDemo1 {
    public static void main(String[] args)throws Exception {
        //1.拿到系统此刻日历对象
        Calendar calendar = Calendar.getInstance();
        //2.获取日历的信息
        int year = calendar.get(Calendar.YEAR);
        System.out.println(year);
        int moth = calendar.get(Calendar.MONTH)+1;
        System.out.println(moth);
        int days = calendar.get(Calendar.DAY_OF_YEAR);
        System.out.println(days);
        //3.修改日历的某个字段
        /*calendar.set(Calendar.HOUR,12);
        System.out.println(calendar);
        一般不会去改
         */
        //4.为某个字段增加、减少指定的值
        calendar.add(Calendar.DAY_OF_YEAR,64);
        calendar.add(Calendar.DAY_OF_MONTH,59);
        //5.拿到此刻日历对象  calendar.getTime()----date 类型
        SimpleDateFormat simpleDateFormat = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss  EEE a");
        System.out.println(simpleDateFormat.format(calendar.getTime()));
        //6.拿到日历对象的时间毫秒值
        System.out.println(calendar.getTimeInMillis());
    }
}

```

