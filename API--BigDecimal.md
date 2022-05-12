# API--BigDecimal

## Java SE

### API

#### BingDecimal的简单的使用

###### 创建测试类

```java
package com.itheima.d14_BigDecimal;

import java.math.BigDecimal;
import java.math.RoundingMode;

public class BigDecimalDemo {
    public static void main(String[] args) {
        //浮点型运算的时候直接  +  -  *  / 可能会出现数据失真（精度问题）
        System.out.println(0.09+0.1);
        System.out.println(1.0-0.32);
        System.out.println(1.015*100);
        System.out.println(1.310/100);

        System.out.println("------------------------");
        double a = 0.1;
        double b = 0.2;
        double c = a+b;
        System.out.println(c);
        System.out.println("--------------------------");
        //包装浮点型数据成为大数据对象--- BigDecimal
        //一般不用构造器，BigDecimal s = new BigDecimal();
        //要调用它的valueOf方法或者用字符串的构造器---BigDecimal s = new BigDecimal(”1.0“);
        BigDecimal b1 = BigDecimal.valueOf(a);
        BigDecimal b2 = BigDecimal.valueOf(b);
        //加法
        BigDecimal c1 = b1.add(b2);
        System.out.println(c1);//0.3
        //减法
        c1 = b1.subtract(b2);
        System.out.println(c1);//-0.1
        //乘法
        c1 = b1.multiply(b2);
        System.out.println(c1);//0.02
        //除法
        c1 = b1.divide(b2);
        System.out.println(c1);//0.5
        //因为这些数据是BigDecimal类型的
        // double db = c1;报错
        // 我们的目的还是要double类型传输
        //所以要用doubleValue方法获取double类型
        double db = c1.doubleValue();
        System.out.println(db);
        System.out.println("--------------------");
        //注意事项：BigDecimal一定要精度运算的
        //这样它就会报错，因为它一生就是为了精度运算，来了个无法精度运算的它想不开就挂了~~
        BigDecimal b11 = BigDecimal.valueOf(10.0);
        BigDecimal b22 = BigDecimal.valueOf(3.0);
        //为了解决它遇到就自杀这个问题，这个方法可以加保留几位和四舍五入等多种功能~~
        /*
        参数一：除数
        参数二：保留小数位
        参数三：舍入模式---有多种模式用RoundingMode.去查看或者选择
         */
 BigDecimal c11 = b11.divide(b22,2, RoundingMode.HALF_DOWN);//3.3333333.......
        System.out.println(c11);
    }
}

```

