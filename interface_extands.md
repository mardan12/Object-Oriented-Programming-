# interface_extands

## 接口的继承

### Java SE

#### 例子

###### 接口

```java
package d7_interface_extends;

public interface Law {
    void rule();

}

```

###### 接口

```java
package d7_interface_extends;

public interface People {
    void eat();

}

```

###### 接口

```java
package d7_interface_extends;
//接口可以多继承，一个接口可以同时继承多个接口~
public interface SportMan extends Law,People {
    void run();
    void competition();
}

```

###### 实现类

```java
package d7_interface_extends;

/**
 * 实现类
 */
public class BasketballMan implements SportMan {

    @Override
    public void rule() {
        System.out.println("rule");
    }

    @Override
    public void eat() {
        System.out.println("eat");
    }

    @Override
    public void run() {
        System.out.println("run");
    }

    @Override
    public void competition() {
        System.out.println("competition");
    }
}

```

###### 测试类

```java
package d7_interface_extends;

public class Test {
    public static void main(String[] args) {
        //目标：理解接口多继承的作用。
        BasketballMan basketballMan = new BasketballMan();
        basketballMan.competition();
        basketballMan.eat();
        basketballMan.rule();
        basketballMan.run();
    }
}

```

