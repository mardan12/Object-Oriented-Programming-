# generic programming

## Java SE

### object oriented programming

#### 泛型的概念及简单的理解

##### 创建测试类简单的解释用泛型的原因

###### 创建测试类

```java
package FanXing;

import java.util.ArrayList;

public class FanXing {
    /**
     * 在没有泛型之前程序员都用object类型的集合，但是这样程序员要知道存储的每个数据的类型不然会有异常。
     * @param args
     */
    public static void main(String[] args) {
//        ArrayList list = new ArrayList<>();
//        list.add("java");
//        list.add(100);
//        list.add(true);
//        for (int i = 0; i < list.size(); i++) {
//            Object o = list.get(i);
//            String str = (String) o;
//            System.out.println(str); 
//        }
        ArrayList<String>str = new ArrayList<>();
        str.add("a");
        str.add("b");
        str.add("c");
        for (int i = 0; i < str.size(); i++) {
            String a = str.get(i);
            System.out.println(a);
        }
        System.out.println("================================");
        ArrayList<Integer>intLest = new ArrayList<>();
        intLest.add(100);
        intLest.add(200);
        intLest.add(300);
        for (int i = 0; i < intLest.size(); i++) {
            int integer = intLest.get(i);
            System.out.println(integer);
        }
    }
}

```

### 通过例子更深入了解

###### 创建泛型类

```java
package FanXing;

/**
 * 泛型类的定义
 * @param <T>泛型类的标识
 */
public class Generic<T>{
    private T key;

    public Generic(T key) {
        this.key = key;
    }

    public Generic() {
    }

    public T getKey() {
        return key;
    }

    public void setKey(T key) {
        this.key = key;
    }

    @Override
    public String toString() {
        return "Generic{" +
                "key=" + key +
                '}';
    }
}

```

###### 创建测试类

```java
package FanXing;

public class Test1 {
    public static void main(String[] args) {
        //泛型类在创建对象的时候来指定操作的具体数据类型
    Generic<String>stringGeneric = new Generic<>("abc   ");
    String key = stringGeneric.getKey();
        System.out.println(key);
        System.out.println("----------------------------");
        Generic<Integer>integerGeneric = new Generic<>(100);
        int key1 = integerGeneric.getKey();
        System.out.println(key1);
        System.out.println("----------------------------");
        //泛型类在创建对象的时候，没有指定类型，将按照Object类型来操作。
        Generic generic = new Generic<>("abc");
        Object key2 = generic.getKey();
        System.out.println(key2);
        //泛型类不支持基本数据类型
       // Generic<int>generic1 = new Generic<int>(100);
        System.out.println("------------------------------");
        //同一泛型类，根据不同的数据类型创建的对象，本质上是同一类型，类类型
        System.out.println(integerGeneric.getClass());
        System.out.println(stringGeneric.getClass());
        System.out.println(integerGeneric.getClass() == stringGeneric.getClass());
    }
}

```

