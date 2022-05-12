# API--StringBuilder

## Java SE

### object oriented programming

#### API

##### StringBuilder 方法的使用并解释

###### 创建测试类

```java
package com.itheima.d11_api_stringbuilder;

/**
 * ---目标：-学会使用StringBuilder操作字符串。最终还需要知道它性能好的原因
 */

/**
 * -------------为什么建议使用StringBuilder?---------------
 * String：内容是不可变的，拼接字符串性能差。每次拼接都会产生很多个对象浪费内存
 * StringBuilder：内容可变的，拼接字符串性能好，代码优雅~只产生一个对象，在一个对象里完成拼接，反转等一系列操作。
 * ---但是，StringBuilder只是拼接反转修改等操作字符串的手段---最终还是要返回String类型使用。
 * 定义字符串还是要拿String来定义。
 */
public class StringBuilderDemo1 {
    public static void main(String[] args) {
        StringBuilder sb = new StringBuilder();
        sb.append("a");
        System.out.println(sb);
        System.out.println("-------------------");
        sb.append("b");
        sb.append(3);
        sb.append(false);
        sb.append(3.3);
        sb.append("abc");
        System.out.println(sb);
        StringBuilder sb2 = new StringBuilder();
        //支持链式编程~
        /*
        这是源代码，每次都return.this-----
        public StringBuilder append(String str) {
                  super.append(str);
                  return this;
              }
         */
        sb2.append("3").append("abc").append("我爱你中国").append(true);
        System.out.println(sb2);
        //反转内容，并且还可以反转拼接，很灵活~
        System.out.println("----------------------");
        System.out.println(sb2.reverse().append("mardan"));
        //获取长度
        System.out.println(sb2.length());
        //注意：StringBuilder 只是拼接字符串的手段：效率好
        //最终的结果还是要恢复成String类型
        StringBuilder sb3 = new StringBuilder();
        sb3.append("123").append("456");
        //因为它现在是StringBuilder 类型直接赋值是不支持的，因为最终目地还是返回String类型来用
        //官方提供了toString方法！
        //String rs = sb3;报错~类型不兼容
        String str = sb3.toString();//是这样用toString方法来接
        System.out.println(str);

    }
}

```

## 例题来更深入了解

###### 创建测试类

```java
package com.itheima.d11_api_stringbuilder;

public class StringBuilderTest {
    public static void main(String[] args) {
        int[]arr = {};
        System.out.println(getArrays(arr));
    }

    /**
     * 定义方法
     * @param arr 接收任意一个整型数组
     * @return 返回数组内容格式
     */
    public static String getArrays(int[]arr){
        if (arr != null) {
            //拼接内容
            StringBuilder stringBuilder = new StringBuilder("[");
            for (int i = 0; i < arr.length; i++) {
                //这样也可以但是有加号会再创建对象占用内存~
                //stringBuilder.append(i==arr.length-1?arr[i]:arr[i]+",")
                //如下写法最优雅~
                stringBuilder.append(arr[i]).append(i == arr.length-1? "" : ",");
            }
            /*有说法是--stringBuilder.append("]");--这行代码是多余的
            可以在上面这样定义省一行代码--stringBuilder.append(arr[i]).append(i==arr.length-1? "]" : ",");--
            这样也是对的，但是它忽略了数组为空的情况，这样的情况下输出结果会缺一个].输出结果为：[
            在这里拼接“]”的原因是这样没有隐患，这是考虑了数组为空的情况
             */
            //这是最优雅的方法,就算是空的这样写输出的结果为：[]
            //                                              ----优雅----
            stringBuilder.append("]");
            return stringBuilder.toString();
        } else {
            return null;
        }
    }

}

```

# -------例子-------

###### 创建测试类

```java
package com.itheima.d14_BigDecimal;
import java.util.Random;
public class aa {
    public static void main(String[] args) {
        StringBuilder stringBuilder = new StringBuilder();
        Random random = new Random();
        String date = "abcdefghijklmnopqrstuvwxyz1234567890ABCDEFGHIJKLMNOPQRSTUVWXYZ";
        for (int i = 0; i < 10; i++) {
            int index = random.nextInt(date.length());
            stringBuilder.append(date.charAt(index));
        }
        System.out.println(stringBuilder);
    }
}

```

