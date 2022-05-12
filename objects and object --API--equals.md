# objects and object --API--equals

## Java SE

### object oriented programming

#### API

##### object 和 objects 的 equals 方法的区别

######  创建测试类

```java
package com.itheima.d10_api_objects;

import java.util.Objects;

/**
 * 对象进行内容比较的时候建议使用Objects提供的equals方法
 * 跟object类提供的结果是一样的但是，objects提供的更安全！
 * 目标：掌握objects类的常用方法：equals
 */
public class Test {
    public static void main(String[] args) {
        String s1 = null;
        String s2 = new String("itheima");
        //System.out.println(s1.equals(s2));//留下了隐患，可能会出现空指针异常
        System.out.println(Objects.equals(s1, s2));//更安全，更准确

        /**
        objects.equals的源代码：

         public static boolean equals(Object a, Object b) {
        -它在这里先判断是否是同一个对象再比较，第一层过滤
         --不是同一个对象就判断是否是null，第二层过滤
         ---如果也不是null他就会进行内容比较！
         return (a == b) || (a != null && a.equals(b));

                }
         */
        //---------object 的 isNull方法-------------
        /**
         *-----判断变量是否为null，为null返回true，反之。
         */
        System.out.println("----------------------------");
        System.out.println(Objects.isNull(s1));//true
        System.out.println(s1 == null);//一样的
        System.out.println(Objects.isNull(s2));//false
        System.out.println(s2 == null);//一样的
        /**
         * 源代码：
         *  public static boolean isNull(Object obj) {
         *              return obj == null;
         *          }
         *---------------------------------------------
         * 其实isNull方法是跟   s2 == null  一样的
         * 用isNull方法的原因就是这样会更专业一点~~
         * --------------------------------------------
         */
    }
}

```

