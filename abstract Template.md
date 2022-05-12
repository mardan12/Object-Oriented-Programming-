# abstract Template

## 抽象类模板

### Java SE

#### abstract

##### 一个小例子

###### 抽象类

```java
package d4_abstract_template;
public abstract class Student {
    //正式：声明了模板方法
    public final void write() {
        System.out.println("\t\t\t\t《我的爸爸》");
        System.out.println("你的爸爸是啥样，来说说。");
        //正文部分：每个人都要写，
        // 但是写的情况不一样，
        // 因此模板方法把正文部分定义成抽象方法交给具体的子类完成！
        System.out.println(writeMain());

        System.out.println("我的爸爸简直太好了~~");
    }
    public abstract String writeMain();
}
```

###### 实现类

```java
package d4_abstract_template;

public class StudentChild extends Student{

    @Override
    public String writeMain() {
        return "我爸爸太牛逼了，天天买好吃的给我吃";
    }
}


```

###### 实现类

```Java
package d4_abstract_template;

public class StudentMiddle extends Student{
    @Override
    public String writeMain() {
        return "我爸爸太牛逼了，开车红黄绿等都不带看一下的~，下辈子还要做他儿子";
    }
}

```

###### 测试类

```Java
package d4_abstract_template;

public class Test {
    public static void main(String[] args) {
        //目标：模板方法模式的思想和使用步骤。
            StudentMiddle s = new StudentMiddle();
                s.write();
                StudentChild s2 = new StudentChild();
                s2.write();
    }
}

```

