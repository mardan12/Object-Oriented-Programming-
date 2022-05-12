# API--Util--Arrays

## Java SE

### API

#### 工具类Arrays的简单的使用

###### 创建测试类

```java
package com.itheima.d13_System;

import java.util.Arrays;

public class SystemDemo2 {
    public static void main(String[] args) {
        //数组拷贝
        int[]arr = {10,20,30,40,50,60,70};
        int[]arr1 = new int[6];
        //要求如下：
        //[0,0,0,0,0,0]==>[0,0,40,50,60,0]
        /*
        到源代码去看需要的参数：
         arraycopy(Object src,int  srcPos, Object dest,int destPos,int length);
        参数一：被拷贝的数字
        参数二：从哪个索引位置开始拷贝
        参数三：复制的目标数组
        参数四：粘贴位置
        参数五：拷贝元素的个数
         */
        System.arraycopy(arr,3,arr1,2,3);
        //Array.toString方法输出数组的方法
        System.out.println(Arrays.toString(arr1));
    }
}

```

