# interface

## 接口的概念

### Java SE

#### 接口的基本概念并使用

###### 接口

```Java
package d5_interface;
/**
 * 声明了一个接:体现了一种规范，规范一定是公开的。
 */
public interface InterfaceDemo {
        //目标：我们要理解一下接口中的成分特点，JDK 8之前接口中只能存抽象方法和常量，
        //1.常量：
        //由于接口体现规范思想，规范默认都会公开的，所以代码层面 ，public，static,final可以省略不写
    //public static final String SCHOOL_NAME = "麦尔旦";
    String SCHOOL_NAME = "麦尔旦";
    //2.抽象方法：
    //由于接口体现规范思想，规范默认都会公开的，所以代码层面 ，public，abstract,可以省略不写
    //public abstract void run();
    void run();
    //public abstract void eat();
    void eat();

}

```

