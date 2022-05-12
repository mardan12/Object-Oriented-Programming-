# abstract attention

## 抽象类注意事项

### Java SE

#### abstract

```java
package d3_abstract_attention;

public class Test {
    //目标：抽象类的注意事项
    //1.类有的东西抽象类都有。
    //2.抽象类中可以没有抽象方法，但是有抽象方法必须是抽象类.
    //3.一个类继承了抽象类必须重写抽象类的全部抽象方法，否则这个类也必须定义成抽象类。
    //4.抽象类不能创建对象,为什么？
    //反证法：如果抽象类能创建对象
    //Animal =  new Animal();
    //Animal.run;???这个方法是空的啊，还想着让他跑？？？疯掉了吧！？！？！
    //所以抽象类不能创建对象。

    public static void main(String[] args) {
       // Animal = new Animal();
    }
}
class cat extends Animal{
    @Override
    public void run() {

    }

    @Override
    public void eat() {

    }
}
abstract class Animal{
    public abstract void run();
    public abstract void eat();
}
```

