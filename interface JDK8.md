# interface JDK8

## java SE

### interface

#### jdk8以后更新的功能

##### 小例子来解释

###### 接口，实现类，测试类

```java
package d8_interface_jdk8;

public interface SportManInter {
    /**
     -- 1.jdk8 开始：默认方法
     -- 必须defunct修饰，默认public修饰
     -- 默认方法，借口不能创建对象，这个方法只能过继给了实现类，有实现类的对象调用。
     --
     */
    default void run(){
        go();
        System.out.println("跑的很快~~");
    }
    /**
     --2.静态方法
     -- 必须使用static修饰，默认用public修饰。
     -- 接口的静态方法，必须接口名自己调用。
     */
    static void inAdd(){
        System.out.println("我们都在学习java新增方法的语法：它是java源码自己用到的~~");
    }
    /**
     -- 3.私有方法
     -- jdk9开始支持的。
     -- 必须在接口内部才能访问。
     */
    private void go(){
        System.out.println("私有方法开始跑了~~");
    }
}
class PingPongMan implements SportManInter{
}
class Test{
    public static void main(String[] args) {
        PingPongMan g = new PingPongMan();
        g.run();
        SportManInter.inAdd();
    }
}
```

###### 

