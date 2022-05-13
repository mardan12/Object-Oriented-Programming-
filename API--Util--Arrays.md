# API--Util--Arrays

## Java SE

### API

#### 工具类Arrays的简单的使用

### Demo1

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

### Demo 2

##### Arrays.toString(arr)-- Arrays.sort(arr)--Arrays.binarySearch(arr,要搜的元素)

###### 创建对象类

```java
package com.itheima.d7_arrays;

import java.util.Arrays;

public class ArraysDemo1 {
    public static void main(String[] args) {
        //目标：学会arrays类的常用api,并理解其原理。
        int[]arr = {10,4,45,6,7,87,8};
        //直接输出是地址
        System.out.println(arr);//[I@776ec8df
        //1.用arrays类的toString方法数组内容以字符串形式返回
        //String s = Arrays.toString(arr);
        //System.out.println(s);
        System.out.println(Arrays.toString(arr));//[10, 4, 45, 6, 7, 87, 8]
        //2.排序的API(它默认对数组元素进行升序排序)
        Arrays.sort(arr);
        System.out.println(Arrays.toString(arr));//[4, 6, 7, 8, 10, 45, 87]
        //3.二分搜索技术（前提数组必须排好序才支持，否则出bug）
        int i = Arrays.binarySearch(arr, 87);
        System.out.println(i);//6---返回索引·
        //返回不存在元素规律： -（应该插入的位置索引+1）
        int j = Arrays.binarySearch(arr, 244);
        System.out.println(j);//-8
        //注意：如果没有排好序，可能会找不到存在的元素，从而出现bug.
        int[] arr2 = {12,65,43,98,12,23};
        int i1 = Arrays.binarySearch(arr2, 98);
        System.out.println(i1);//-7
    }
}

```

### Demo 3

###### 创建对象类

```java
package com.itheima.d7_arrays;

public class Student {
    private String name;
    private int age;
    private double height;

    public Student() {
    }

    public Student(String name, int age, double height) {
        this.name = name;
        this.age = age;
        this.height = height;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public double getHeight() {
        return height;
    }

    public void setHeight(double height) {
        this.height = height;
    }

    @Override
    public String toString() {
        return "Student{" +
                "name='" + name + '\'' +
                ", age=" + age +
                ", height=" + height +
                '}';
    }
}

```

##### Arrays.sort(ages1, new Comparator<Integer>()

参数一：被排序的数组，必须是引用类型的元素
参数二：匿名内部类对象，代表了一个比较器对象

###### 创建测试类

```java
package com.itheima.d7_arrays;
import java.util.Arrays;
import java.util.Comparator;
public class ArraysDemo2 {
    public static void main(String[] args) {
        //目标：自定义数组的排序规则，comparator比较器对象
        //1.Arrays的sort方法对有值特性的数组是默认升序排序的。
        int[]ages = {34,12,54,23,22,43,66};
        Arrays.sort(ages);
        System.out.println(Arrays.toString(ages));
        //2.需求：我想降序排序（自定义比较器对象，只能支持引用类型的排序）
        Integer[]ages1 = {34,12,54,23,22,43,66};
        /*
        参数一：被排序的数组，必须是引用类型的元素
        参数二：匿名内部类对象，代表了一个比较器对象
         */
        Arrays.sort(ages1, new Comparator<Integer>() {
            @Override
            public int compare(Integer o1, Integer o2) {
                //开始指定比较规则
//                if (o1 > o2){
//                    return 1;
//                }else if (o1 < o2){
//                    return -1;
//                }
//                return 0;默认排序
//                return o1-o2;//默认排序
                return -(o1-o2);//降序排序
            }
        });
        System.out.println(Arrays.toString(ages1));
        System.out.println("-------------------------------");
        Student[]students = new Student[3];
        students[0] = new Student("麦尔旦",22,174.5);
        students[1] = new Student("小李",21,179.7);
        students[2] = new Student("小明",23,163.3);
        System.out.println(Arrays.toString(students));
       // Arrays.sort(students);//报错，它说我怎么排啊，我按照年龄还是什么啊，你会不会啊！？
        Arrays.sort(students, new Comparator<Student>() {
            @Override
            public int compare(Student o1, Student o2) {
                //自己指定比较规则
                //return o1.getAge()- o2.getAge();//按照升序排序根据年龄大小去排序
                //return o2.getAge() - o1.getAge();//降序排序
                //return -(o1.getAge()- o2.getAge());//也可以这样
                //比较小数
                //return o1.getHeight()- o2.getHeight();不行这方法是要返回int类型的
                //return (int) (o1.getHeight()- o2.getHeight());//这样也是不正确的，结果不精确
                //对于这个问题官方已经给我们解决做好API了我们直接去用就行了
                //return Double.compare(o1.getHeight(),o2.getHeight());//升序排序
                //return Double.compare(o2.getHeight(), o1.getHeight());//降序排序
                return -Double.compare(o1.getHeight(),o2.getHeight());//降序排序
            }
        });
        System.out.println(Arrays.toString(students));

    }
}

```

