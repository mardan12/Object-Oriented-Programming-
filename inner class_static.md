# inner class_static

## Java SE

### object oriented programming

#### 静态成员内部类

##### 简单的解释

###### 创建一个实现类

```java
package com.itheima.d5_innerclass_static;

/**
 * 外部类
 */
public class Outer {
    /**
     --学习静态成员内部类
     */
    public static int a = 100;
    private String hobby;
//内部类
    public static class Inner{
        private String name;
        private int age;
        public static String schoolName;
        public Inner(){}
        public Inner(String name, int age) {
            this.name = name;
            this.age = age;
        }
        public void show(){
            System.out.println("名称："+name);
            System.out.println(a);
            //System.out.println(hobby);----报错
            Outer outer = new Outer();
            System.out.println(outer.hobby);
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
    }
}

```

###### 创建测试类

```java
package com.itheima.d5_innerclass_static;

public class Test {
    public static void main(String[] args) {
        Outer.Inner in = new Outer.Inner();
        in.setName("麦尔旦");
        in.show();

    }
}

```

