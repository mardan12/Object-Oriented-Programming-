# API--Util--System

## Java SE

### API

#### System 的简单使用

##### Demo 1

###### 创建测试类

```java
package com.itheima.d13_System;

/**
 *System 的简单使用
 */
public class SystemDemo {
    public static void main(String[] args) {
        System.out.println("开始....");
        System.exit(0);//JVM终止
        //后面不会跑Java虚拟机被干掉了，数字是后台记录日志用，不用管，填个0就好
        //一般不会用的，不要去用，了解一下就行了，干掉jvm干什么~~~
        System.out.println("结束了....");
    }
}

```

##### Demo 2

###### 创建测试类

```java
package com.itheima.d13_System;

public class SystemDemo1 {
    public static void main(String[] args) {
        //2.计算机认为时间有起源：返回1970-1-1 00 ：00 ： 00 走到此刻的总的毫秒值 ：时间毫秒值
        //1970-1-1 是c语言的生日
        //这个主要用于记录时间
        long time = System.currentTimeMillis();
        System.out.println(time);
        System.out.println("---------------------------------");
        long forTimes = System.currentTimeMillis();
        for (int i = 0; i < 10000000; i++) System.out.print(i);
        long forTimesEnd = System.currentTimeMillis();
        System.out.println("---------------------------------");
        long whileTimeStart = System.currentTimeMillis();
        int i = 0;
        while ( i < 10000000 ){
            System.out.print(i);
            i++;
        }
        System.out.println();
        long whileTimeEnd = System.currentTimeMillis();
        System.out.println("for语句的速度："+(forTimesEnd - forTimes)/1000.0+"s");
        System.out.println("================================");
        System.out.println("while语句的速度："+(whileTimeEnd - whileTimeStart)/1000.0+"s");
    }
}

```



