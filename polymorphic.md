# polymorphic

## Java SE

### oop-面向对象

#### 多态的基本概念

##### 例子

###### 创建抽象类

```java
 	package com.itheima.d1_polymorphic;

public abstract class Animal {
    public String name = "父类动物";
    public abstract void run();
}

```

创建子类

```java
package com.itheima.d1_polymorphic;

public class Dog extends Animal {
    public String name = "子类狗";
    @Override
    public void run() {
        System.out.println("狗跑的贼快~~");
    }
    public void lookDoor(){
        System.out.println("狗在看门");
    }
}

```

###### 创建子类

```java
package com.itheima.d1_polymorphic;

public class Tortoise extends Animal{
    public String name = "子类乌龟";
    @Override
    public void run() {
        System.out.println("乌龟跑的很慢~~");
    }
}

```

###### 创建测试类

```java
package com.itheima.d1_polymorphic;

public class Test {
    public static void main(String[] args) {
        //1.多态的形式：
//        左          右
        Animal d = new Dog();
        d.run();//编译看左边，运行看右边~
        System.out.println(d.name);//编译看左边，运行看左边~
        go(d);
        //d.lookDoor();---多态下不能使用子类独有功能
        Animal t = new Tortoise();
        t.run();//编译看左边，运行看右边~
        System.out.println(t.name);//编译看左边，运行看左边~
        go(t);
    }

    /**
     * 要求：所有动物都可以进来比赛
     */
    public static void go(Animal animal){
        System.out.println("开始~~~");
        animal.run();
        System.out.println("结束...");

    }
}

```

