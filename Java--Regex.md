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

```JAVA
package com.itheima.d6_regex;

/**
 * 目标：全面深入了解正规表达式的规则
 */
public class RegexDemo2 {
    public static void main(String[] args) {
        //public boolean matches(String regex),判断是否匹配正规表达式，匹配返回true，不匹配返回false
        //只能是abc
        System.out.println("a".matches("[abc]"));//true
        System.out.println("z".matches("[abc]"));//false
        System.out.println("ab".matches("[abc]"));//false
        //不能是abc
        System.out.println("a".matches("[^abc]"));//false
        System.out.println("z".matches("[^abc]"));//true
        //只出现一次abc
        System.out.println("ab".matches("[abc]+"));//true
        //数字
        System.out.println("a".matches("\\d"));//false
        System.out.println("3".matches("\\d"));//true
        System.out.println("333".matches("\\d"));//false  三个就不行的，默认值是1个
        //
        System.out.println("z".matches("\\w"));//true
        System.out.println("2".matches("\\w"));//true
        System.out.println("21".matches("\\w"));//false
        System.out.println("你".matches("\\w"));//false
        System.out.println("-------------------------------------------------");
        //以上正规匹配只能校验单个字符
        //校验密码
        //必须是数字，字母，下划线，至少6位
        System.out.println("ssds3c".matches("\\w{6,}"));//true
        System.out.println("ssdsc".matches("\\w{6,}"));//false
        System.out.println("ssds223你c".matches("\\w{6,}"));//false
        //验证必须是数字和字母，必须是4位
        System.out.println("dsd2".matches("[a-zA-Z0-9]{4}"));//true
        System.out.println("E_d2".matches("[a-zA-Z0-9]{4}"));//false
        System.out.println("A3dy".matches("[a-zA-Z0-9]{4}"));//true
        System.out.println("A3dy2".matches("[a-zA-Z0-9]{4}"));//false
        System.out.println("23dF".matches("[\\w&&[^_]]{4}"));//true
        System.out.println("23_F".matches("[\\w&&[^_]]{4}"));//false

    }
}
/*

字符类
[abc] 	a, b， 或者 c（简单类）
[^abc] 	任何字符除了 a, b， 或者 c（否定）
[a-zA-Z] 	a通过 z 或者 A通过 Z, 包括 (范围)
[a-d[m-p]] 	a通过 d, 或者 m通过 p: [a-dm-p]（联盟）
[a-z&&[def]] 	d, e， 或者 f（路口）
[a-z&&[^bc]] 	a通过 z, 除了 b和 c: [ad-z]（减法）
[a-z&&[^m-p]] 	a通过 z, 并不是 m通过 p: [a-lq-z]（减法）
预定义的字符类
. 	任何字符（可能与 行终止符 ）
\d 	一个数字： [0-9]
\D 	非数字： [^0-9]
\h 	水平空白字符： [ \t\xA0\u1680\u180e\u2000-\u200a\u202f\u205f\u3000]
\H 	非水平空白字符： [^\h]
\s 	空白字符： [ \t\n\x0B\f\r]
\S 	非空白字符： [^\s]
\v 	垂直空白字符： [\n\x0B\f\r\x85\u2028\u2029]
\V 	非垂直空白字符： [^\v]
\w 	一个字字符： [a-zA-Z_0-9]
\W 	非单词字符： [^\w]
POSIX 字符类（仅限 US-ASCII）
\p{Lower} 	小写字母字符： [a-z]
\p{Upper} 	大写字母字符： [A-Z]
\p{ASCII} 	所有ASCII： [\x00-\x7F]
\p{Alpha} 	一个字母字符： [\p{Lower}\p{Upper}]
\p{Digit} 	一个十进制数字： [0-9]
\p{Alnum} 	一个字母数字字符： [\p{Alpha}\p{Digit}]
\p{Punct} 	标点：之一 !"#$%&'()*+,-./:;<=>?@[\]^_`{|}~
\p{Graph} 	一个可见的字符： [\p{Alnum}\p{Punct}]
\p{Print} 	可打印字符： [\p{Graph}\x20]
\p{Blank} 	空格或制表符： [ \t]
\p{Cntrl} 	控制字符： [\x00-\x1F\x7F]
\p{XDigit} 	十六进制数字： [0-9a-fA-F]
\p{Space} 	空白字符： [ \t\n\x0B\f\r]
java.lang.Character 类（简单的 java 字符类型 ）
\p{javaLowerCase} 	等价于 java.lang.Character.isLowerCase()
\p{javaUpperCase} 	等价于 java.lang.Character.isUpperCase()
\p{javaWhitespace} 	等价于 java.lang.Character.isWhitespace()
\p{javaMirrored} 	等价于 java.lang.Character.isMirrored()
Unicode 脚本、块、类别和二进制属性的类
\p{IsLatin} 	一个拉丁文字字符（ script ）
\p{InGreek} 	希腊语块 ( block )
\p{Lu} 	大写字母（ 类别 ）
\p{IsAlphabetic} 	一个字母字符（ 二进制属性 ）
\p{Sc} 	货币符号
\P{InGreek} 	除希腊语块中的一个之外的任何字符（否定）
[\p{L}&&[^\p{Lu}]] 	除大写字母外的任何字母（减法）
边界匹配
^ 	一行的开头
$ 	一行的结尾
\b 	一个词的边界
\b{g} 	Unicode 扩展字素簇边界
\B 	非单词边界
\A 	输入的开始
\G 	上一场比赛结束
\Z 	输入结束但为最终 终结者 ，如果有的话
\z 	输入结束
换行符匹配器
\R 	任何 Unicode 换行序列，都等价于 \u000D\u000A|[\u000A\u000B\u000C\u000D\u0085\u2028\u2029]
Unicode 扩展字形匹配器
\X 	任何 Unicode 扩展字素簇
贪心量词
X ? 	X ，一次或一次
X * 	X , 零次或多次
X + 	X , 一次或多次
X {n } 	X , 正好 n 次
X {n ,} 	X ，至少 n 次
X {n ,米 } 	X ，至少 n 但不超过 m 次
不情愿的量词
X ?? 	X ，一次或一次
X *? 	X , 零次或多次
X +? 	X , 一次或多次
X {n }? 	X , 正好 n 次
X {n ,}? 	X ，至少 n 次
X {n ,米 }? 	X ，至少 n 但不超过 m 次
占有量词
X ?+ 	X ，一次或一次
X *+ 	X , 零次或多次
X ++ 	X , 一次或多次
X {n }+ 	X , 正好 n 次
X {n ,}+ 	X ，至少 n 次
X {n ,米 }+ 	X ，至少 n 但不超过 m 次
逻辑运算符
XY 	X 后跟 Y
X |是 	X _ 或 Y
(X ) 	X，作为 捕获组
反向引用
\n 	无论第 n 个 捕获组 匹配
\k < 名称 > 	不管是什么 命名捕获组 “名称”匹配
引述
\ 	什么都没有，但引用以下字符
\Q 	什么都没有，但引用所有字符直到 \E
\E 	什么都没有，但结束引用开始于 \Q
特殊构造（命名捕获和非捕获）
(?<name>X ) 	X ，作为一个命名捕获组
(?:X ) 	X ，作为非捕获组
(?idmsuxU-idmsuxU)  	什么都没有，但会变成匹配标志 i d m s u x U 开关
(?idmsuxU-idmsuxU:X )   	X ，作为一个 非捕获 组 给定标志 i d m s u x U on - off
(?=X ) 	X ，通过零宽度正前瞻
(?!X ) 	X ，通过零宽度负前瞻
(?<=X ) 	X ，通过零宽度正向后视
(?<!X ) 	X ，通过零宽度负向后看
(?>X ) 	X ，作为一个独立的非捕获组

 */

```

###### 创建测试类 

#### Demo3

```
package com.itheima.d6_regex;

/**
 * -------------正规表达式方法中的应用----------------
 * ---按照正规表达式匹配的内容进行分割字符串，反向一个字符串数组。
 * public String[]split(String regex)
 * ---按照正规表达式匹配的内容进行替换
 * public String replaceALL(String regex , String newStr)
 */
public class RegexDemo3 {
    public static void main(String[] args) {
        String names = "麦尔旦sfffdhfslks小路dfkfgfjhg小李";
        String[] split = names.split("\\w+");
        for (int i = 0; i < split.length; i++) {
            System.out.println(split[i]);
            /*
            麦尔旦
            小路
            小李
            */
        }
        String s = names.replaceAll("\\w+", "  ");
        System.out.println(s);//麦尔旦  小路  小李
    }
}

```

#### Demo4

###### 创建测试类

```java
package com.itheima.d6_regex;

import java.util.regex.Matcher;
import java.util.regex.Pattern;

public class RegexDemo4 {
    public static void main(String[] args) {
        String rs = "来黑马程序员学习Java，电话020-43422424，" +
                "或者联系邮箱：itcast@itcast.com,电话13064114545，0" +
                "20232323，邮箱amrdsf12@123.com,400-100-323.400535678";
        //需求从上面内容中爬取电话号码，和邮箱
        //1.定义爬取规则，字符串形式
        String regex = "(\\w{1,30}@[a-zA-Z0-9]{2,20}(\\.[a-zA-Z0-9]{2,20}){1,2})" +
            "|(1[3-9]\\d{9}|0\\d{3,6}-?\\d{5,20}|400-?\\d{3,9}-?\\d{3,9})";
        //2.把这个爬取规则编译成匹配对象
        Pattern pattern = Pattern.compile(regex);
        //3.得到一个内容匹配器
        Matcher matcher = pattern.matcher(rs);
        //开始爬了
        while (matcher.find()){
            String group = matcher.group();
            System.out.println(group);
        }
    }
}

```

#### Demo 5

###### 创建测试类

```java
package com.itheima.d6_regex;

import java.util.Scanner;

public class RegexTest {
    static Scanner sc = new Scanner(System.in);
    public static void main(String[] args) {
        //目标：校验手机号码，邮箱，电话号码
        //checkPhone();
         //checkEmail();
          //checkTel();
        //1.2 44,5666,金额
        System.out.println("0023.445".matches("(\\d+\\.?\\d+)?"));
    }

    private static void checkTel() {
        while (true) {
            System.out.println("请您输入注册电话号码：");
            String tel = sc.next();
            //判断手机号码的格式是否正确
            if (tel.matches("0\\d{3,6}-?\\d{5,20}")){
                System.out.println("电话号码格式正确！");
                return;
            }else {
                System.out.println("电话号码格式有误！");
            }
        }
    }

    private static void checkEmail() {
        while (true) {
            System.out.println("请您输入注册电子邮箱：");
            String email = sc.next();
            //判断邮箱的格式是否正确
            //234637538@qq.com
            //23435df44@163.com
            //ieg434fir@pci.com.cn
            if (email.matches("\\w{1,30}@[a-zA-Z0-9]{2,20}(\\.[a-zA-Z0-9]{2,20}){1,2}")){
                System.out.println("邮箱格式正确！");
                return;
            }else {
                System.out.println("邮箱格式有误！");
            }
        }
    }

    public static void checkPhone(){
        while (true) {
            System.out.println("请您输入注册手机号：");
            String phone = sc.next();
            //判断手机号码的格式是否正确
            if (phone.matches("1[3-9]\\d{9}")){
                System.out.println("手机号码格式正确！");
                return;
            }else {
                System.out.println("手机号码格式有误！");
            }
        }
    }
}

```

