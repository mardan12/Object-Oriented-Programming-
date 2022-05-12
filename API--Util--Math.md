# API--Util--Math

## Java SE

### object oriented programming

#### API

##### 工具类Math的简单的使用

###### 创建测试类

```java
package com.itheima.d12_Math;

/**
 *                        math类
 *      包含执行基本数字运算的方法，Math类没有提供公开的构造器
 *      使用类中的成员，先看是否是静态的，如果是，通过类名就可以调用。
 *      工具类
 */
public class MathDemo {
    public static void main(String[] args) {
        //1.取绝对值：返回整数
        System.out.println(Math.abs(10));//10
        System.out.println(Math.abs(-10.3));//10.3
        //2.向上取整:5
        System.out.println(Math.ceil(4.00000000004));//5
        //3.向下取整：4
        System.out.println(Math.floor(4.0000000004));//4
        //4.求指数次方
        System.out.println(Math.pow(2,3));//2^3 = 8.0
        //5.四舍五入 10
        System.out.println(Math.round(4.4999999));//4
        System.out.println(Math.round(4.50000001));//5

        System.out.println(Math.random());//0.0---1.0（包前不包后）
        //扩展：0-9之间的随机数    (0 --- 6) + 3
        System.out.println((Math.random() * 7) + 3);
        int date = (int)(Math.random()*7)+3;
        System.out.println(date);
    }
}

```

