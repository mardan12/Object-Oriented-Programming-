# API--SimpleDateFormat

## Java SE

### 简单日期格式化

#### SimpleDateFormat的简单使用

##### Demo 1

###### 创建测试类

```java
package com.itheima.d2_simpledateformat;
import java.text.SimpleDateFormat;
import java.util.Date;
/**
 * 目标：SimpleDateFormat的简单日期格式化类的使用。
 * 格式化日期
 * 解析时间
 */
public class SimpleDateFormatDemo1 {
    public static void main(String[] args) {
        //日期对象
        Date d = new Date();
        System.out.println(d);
        //格式化这个日期对象
        SimpleDateFormat sdf = new SimpleDateFormat("yyyy年MM月dd日HH:mm:ss EEE a");
        //正式开始格式化日期对象成为字符串形式
        String rs = sdf.format(d);
        System.out.println(rs);
        //可以格式化时间毫秒值
        //请问121秒后的时间是多少
        long time = System.currentTimeMillis()+121*1000;
        SimpleDateFormat sss = new SimpleDateFormat("yyyy年MM月dd日HH:mm:ss EEE a");
        String ss = sss.format(time);
        System.out.println(ss);

    }
}

```

##### Demo 2

###### 创建测试类

```java
package com.itheima.d2_simpledateformat;
import java.text.SimpleDateFormat;
import java.util.Date;

public class SimpleDateFormatDemo2 {
    public static void main(String[] args)throws Exception {
        //目标：学会使用SimpleDateFormat解析字符串时间成为日期对象
        //有应该时间：2021年08月06日 11点11分11秒  往后2天14小时49分06秒后的时间是多少
        //1.把字符串时间拿到程序中来
        String dateStr = "2021年08月06日 11:11:11";
        //2.把字符串时间解析成日期对象（本节重点）：形式必须要跟我们要解析的时间的形式完全一样，否则运行时它解析会报错。
        SimpleDateFormat sdf  = new SimpleDateFormat("yyyy年MM月dd日 HH:mm:ss");
        Date date = sdf.parse(dateStr);
        System.out.println(date);
        //3.往后走2天14小时49分钟06秒
        long time = date.getTime()+(2L*24*60*60 + 14*60*60 + 49*60 + 6)*1000;
        //4.格式化这个时间毫秒值就是结果
        SimpleDateFormat simpleDateFormat = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss EEE a");
        System.out.println(simpleDateFormat.format(time));
    }
}

```

##### Demo 3

##### 通过例题更好的去理解

###### 创建测试类

```java
package com.itheima.d2_simpledateformat;

import java.text.SimpleDateFormat;
import java.util.Date;

public class SimpleDateFormatTest {
    public static void main(String[] args) throws Exception{
        //开始   和  结束 时间
        String startTime = "2021-11-11 00:00:00";
        String endTime = "2021-11-12 00:10:00";
        //johny alex
        String johny = "2021-11-12 00:03:37";
        String alex = "2021-11-12 00:10:11";
        SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
        Date d1 = sdf.parse(startTime);
        Date d2 = sdf.parse(endTime);
        Date d3 = sdf.parse(johny);
        Date d4 = sdf.parse(alex);
        if (d3.after(d1) && d3.before(d2)){
            System.out.println("johny秒杀成功~");
        }else{
            System.out.println("johny秒杀失败~");
        }
        if (d4.after(d1) && d4.before(d2)){
            System.out.println("alex秒杀成功~");
        }else{
            System.out.println("alex秒杀失败~");
        }
    }
}

```

