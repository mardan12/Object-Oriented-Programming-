# inner class

## Java SE

### object oriented programming

#### 无static修饰的成员内部类

##### 简单的例子

# Demo1

###### 创建实现类

```java
package com.itheima.d6_innerclass;
/**
 * ---外部类
 */
public class Outer {
    /**
     *-----成员内部类：不能加static修士，局于外部类对象的
     */
    public static int num = 111;
    private String hobby;

    public Outer(String hobby) {
        this.hobby = hobby;
    }

    public Outer() {
    }

    class Inner{
        private String name;
        private int age;
        public static int a = 100;//JDK16 开始支持静态成员
    public static void test(){
        System.out.println(a);
    }
    public void show(){
        System.out.println("名称："+name);
        System.out.println("数量："+num);
        System.out.println("爱好"+hobby);
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
package com.itheima.d6_innerclass;

public class Test {
    public static void main(String[] args) {
        Outer.Inner inner = new Outer().new Inner();
        inner.setName("麦尔旦");
        inner.show();
        Outer.Inner.test();
        System.out.println("----------------------");
        Outer.Inner inner1 = new Outer("爱听课").new Inner();
        inner1.show();

    }
}

```

# Demo2

###### 创建测试类

```java
package com.itheima.d6_innerclass;

public class Test2 {
    public static void main(String[] args) {
        People.Heart p = new People().new Heart();
        p.show();
    }
}
class People{
    private int heartbeat = 150;
    public class Heart{
        private int heartbeat = 100;
        public void show(){
            int heartbeat = 78;
            System.out.println(heartbeat);
            System.out.println(this.heartbeat);
            System.out.println(People.this.heartbeat);
        }
    }
}

```

# Demo3

## 局部内部类

### 局部内部类的语法

###### 创建测试类

```java
package com.itheima.d7_innerclass;

/**
 * 了解局部内部类的语法
 */
public class Test {
    static{
        class Dog{

        }
        abstract class Animal{

        }
        interface SuperMan{

        }
    }
    public static void main(String[] args) {
        class Cat {
            private String name;
            public static int onlineNumber = 100;


            public String getName() {
                return name;
            }

            public void setName(String name) {
                this.name = name;
            }
        }
        Cat c = new Cat();
        c.setName("麦尔旦");
    }
}
```

