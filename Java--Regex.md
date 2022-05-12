# Java--Regex

## Java SE

### 正规表达式

#### Demo 1

###### 创建测试类

```java
package com.itheima.d6_regex;

/**
 * -----------------------------正规表达式----------------------------
 *
 */
public class RegexDemo1 {
    public static void main(String[] args) {
        //需求：校验QQ号，必须全部是数字，6~20位
        System.out.println(checkQQ("234566742"));
        System.out.println(checkQQ("66742"));
        System.out.println(checkQQ("23456a742"));
        System.out.println(checkQQ(null));
        System.out.println("----------------------------");
        System.out.println(checkQQ1("234566742"));
        System.out.println(checkQQ1("66742"));
        System.out.println(checkQQ1("23456a742"));
        System.out.println(checkQQ1(null));
    }
    public static boolean checkQQ1(String qq){
        // /d 表示数字，这里//d的第一个杠意义是告诉第二个杠它只是一个杠
        return qq != null && qq.matches("\\d{6,20}");
    }
    public static boolean checkQQ(String qq){
        //判断QQ号码长度是否满足要求
        if (qq == null || qq.length() < 6 || qq.length() > 20){
            return false;
        }
        //判断是否全部是数字,不是返回false
        for (int i = 0; i < qq.length(); i++) {
            char c = qq.charAt(i);
            //判断这个数字是否不是数字，如果不是返回false
            if(c<'0' || c >'9'){
                return false;
            }
        }
        return true;//到这里肯定是合规的
    }
}

```

#### Demo 2

###### 创建测试类

```

```

