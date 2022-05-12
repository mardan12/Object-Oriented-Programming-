# abstract

## 抽象类

### 抽象类的简单使用

#### JavaSE

###### 抽象类

```Java
package d1_abstract;

public abstract class Animal {
    abstract void run();
}

```

###### 实现类

```java
package d1_abstract;

public class Dog extends Animal {
    @Override
    void run() {
        System.out.println("狗跑的贼快~~");
    }
}

```

###### 测试类

```java
	package d1_abstract;

public class Test {
    public static void main(String[] args) {
        Dog d = new Dog();
       d.run();
    }
}

```

