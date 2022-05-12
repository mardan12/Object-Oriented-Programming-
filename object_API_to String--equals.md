# object_API_to String--equals

## Java SE

### object oriented programming

#### Object

##### object类中的to String 方法

###### 创建对象类

```java
package com.itheima.d9_api_object;

import java.util.Objects;

public class Student {//extends Object
    private String name;
    private int age;
    private char sex;

    public Student(){
    }

    public Student(String name, int age, char sex) {
        this.name = name;
        this.age = age;
        this.sex = sex;
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

    public char getSex() {
        return sex;
    }

    public void setSex(char sex) {
        this.sex = sex;
    }
    /* @Override
    public String toString(){
        return "Student {name:"+name+",sex:"+sex+",age:"+age +"}";
    }*/

    @Override
    public String toString() {
        return "Student{" +
                "name='" + name + '\'' +
                ", age=" + age +
                ", sex=" + sex +
                '}';
    }
    @Override
    public boolean equals(Object o) {
        //1.是否是同一个对象，如果是返回true
        if (this == o) return true;
        //2.如果o是null，里面没有内容，就返回false
        //o.getClass传进来的类型，如果不是本类类型也就是说如果不是学生类型就返回false，不同类型不比较~
        if (o == null || getClass() != o.getClass()) return false;
        //这里说明它一定是学生类型且并不为null
        //把o强转成学生类型，为了比较
        Student student = (Student) o;
        //这里没用this是因为不矛盾，students.是传进来的，没有的是自己的
        //在这里用objects的equals方法是因为这个更安全，不会出现里面的某个元素是空的然后出现异常这种情况
        return age == student.age && sex == student.sex && Objects.equals(name, student.name);
    }
    /**
     * ---自己重写equals，自己定制比较规则。
     * 我都规则是两个对象内容一样就认为是对的
     * s1.equals(s2)
     * 比较者：s1==this
     * 被比较者:s2
     */

    //@Override
    public boolean equals1(Object o){
    //首先判断这个o是不是学生类型的
    //其实我在这里已经排除了为空的情况，如果是空的instanceof会认定为类型不一样
        if (o instanceof Student){
            Student student = (Student) o;
//            //判断两个对象的内容是否一样
//            if (){
//                return true;
//            }else {
//                return false;
//            }
            return this.name.equals(student.name)&&this.age==student.age&&this.sex==student.sex;
        }else {
            //学生一定和学生比较，否则一定是false
            return false;
        }
    }
    }


```



###### 创建测试类

```javascript
package com.itheima.d9_api_object;
//--------------toString的作用是什么？---------------
/**
 * ----------------如下--------------
 ----默认是打印对象的地址。
 ----真正意义是== 让子类重写，以便返回子类对象的内容。
 -------------------------------------------------
 */

/**
 * ---目标：掌握object类中的toString方法的食用。
 */
public class Test {
    public static void main(String[] args) {
    Student student = new Student("麦尔旦",22,'男');
//        String rs = student.toString();
//        System.out.println(rs);
        // 直接输出对象变量，默认它可以省略toString~~调用不写的
        System.out.println(student.toString());
        //调toString和不调其实都是一样的结果，可以省略
        System.out.println(student);
        /**
         -----实际开发中直接输出对象地址是毫无意义的，开发中更希望看到的是对象变量的内容数据并不是对象变量地址
         --父类toString()方法存在的意义是为了被子类重写，以便返回对象的内容信息，而不是地址信息！！！！
         */

    }
}

```

### object 中的equals方法

###### 创建测试类

```java
package com.itheima.d9_api_object;
//-----------------object 的 equals方法的作用是什么？？-------------------
/**
 -------------如下---------
 ---默认是与另一个对象比较地址是否一样
 ---让子类重写，以便比较两个子类对象的内容是否相同
 ----------------------------------------------
 */

/**
 * 目标：掌握object中的equals方法的使用。
 */
public class Test1 {
    public static void main(String[] args) {
        Student s1 = new Student("麦尔旦",22,'男');
        Student s2 = new Student("麦尔旦",22,'男');
        //equals默认是比较两个对象之间的地址是否相同
        System.out.println(s1.equals(s2));
        //想要比较两个对象的地址是否相同完全可以用==号来替代。结果一样
        System.out.println(s1==s2);
        /**
         --其实，equals 存在的意是为了被子类重写，以便子类自己来决定比较规则。
         */
    }
}

```

