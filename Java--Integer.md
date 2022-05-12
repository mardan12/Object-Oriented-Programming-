# Java--Integer

## Java SE

### 包装类

#### 包装类的概念

```java
package com.itheima.d5_integer;

/**
 * ----------------------------包装类是什么？------------------------------
 * 基本数据类型对应的引用类型
 * 实现一切皆对象
 * 后期集合和泛型都不支持基本类型，只能使用包装类型
 * ---------------------包装类有哪些特殊功能------------------
 * 可以把基本类型的数据转换成字符串类型（用处不大）
 * 可以把字符串类型的数值转换成真实的数据类型（真的很好用）
 */
public class Test {
    public static void main(String[] args) {
        int a = 5;
        Integer b = a;//自动装箱
        int c = b;//自动拆箱
        System.out.println(c);
        System.out.println(b);
        //包装类的容错率更高
       // int e = null;报错
        Integer d = null;//可以
        //可以把基本类型转换成字符串类型
        //调用toString方法得到字符串结果
        //调用Integer.toString(基本类型的数据)
        Integer i3 = 23;
        String s = i3.toString();
        System.out.println(s+1);//231
        String s1 = Integer.toString(i3);
        System.out.println(s1+1);
        //可以加字符串得到字符串类型
        String rs = i3+"";
        System.out.println(rs+1);
        System.out.println("---------------------------");
        //可以把字符串类型的数值转换成真实的数据类型--很好用
        //Integer.parseInt("字符串类型的整数");
       // Double.parseDouble("字符串类型的小数");
        //String number = "23aa";-----32行--数字格式化异常
        /*
        Exception in thread "main" java.lang.NumberFormatException: For input string: "23aa"
	at java.base/java.lang.NumberFormatException.forInputString(NumberFormatException.java:67)
	at java.base/java.lang.Integer.parseInt(Integer.java:668)
	at java.base/java.lang.Integer.valueOf(Integer.java:999)
	at com.itheima.d5_integer.Test.main(Test.java:32)
         */
        String number = "23";
        //转换成整数
        //int age = Integer.parseInt(number);
        //也可以用valueOf
        int age = Integer.valueOf(number);
        //double ages = Double.parseDouble(number);
        double ages = Double.valueOf(number);
        System.out.println(age+1);
        System.out.println(ages+0.1);

    }
}

```

