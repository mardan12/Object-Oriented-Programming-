# inner class_anonymous

## Java SE

### object oriented programming

#### inner class

##### 匿名内部类的使用和基本概念

# Demo 1

###### 创建测试类

```java
package com.itheima.d8_innnerclass_anonymous;

public class Test {
    public static void main(String[] args) {
//        Animal a = new Tiger();-----多态思想是这样写的
//        a.run();
        /**
         *---匿名内部类是这样实现的---如下：
         * ----简化代码
         * ----匿名内部类是没有名字的内部类
         * ---匿名内部类写出类就会产生一个匿名内部类对象
         * ---他绝对不是Animal的对象，Animal是不能创建对象的，是匿名内部类对象
         * ---它整个对象类型是Animal的子类，是子类对象类型~
         * ---这也是一种多态的形式
         * --作用是方便创建子类对象，最终目的是简化代码编写
         * --它会产生class文件的，是一个类
         */
        Animal a = new Animal() {
            @Override
            public void run() {
                System.out.println("老虎跑的很快~~");
            }
        };
        a.run();
    }
}
//class Tiger extends Animal{
//---- 匿名内部类不是这样想的--它根本就不需要这个内部类~~
//    @Override
//    public void run() {
//        System.out.println("老虎跑的快~~~");
//    }
//}
abstract class Animal{
    public abstract void run();
}
```

# Demo 2

## 语法

#### 掌握匿名内部类的使用形式

```java
package com.itheima.d8_innnerclass_anonymous;

/**
* --- 目标：掌握你匿名内部类的使用形式（语法）
 */
public class test2 {
    public static void main(String[] args) {
        Swimming students = new Swimming() {
            @Override
            public void swim() {
                System.out.println("学生速度一般~~");
            }
        };
        go(students);
        System.out.println("---------------------------");
        go(new Swimming() {
            @Override
            public void swim() {
                System.out.println("老师速度比较快~~");
            }
        });
        System.out.println("---------------------------");
        Swimming SportMan = new Swimming() {
            @Override
            public void swim() {
                System.out.println("运动员速度很快~~");
            }
        };
        go(SportMan);
    }
    /**
     * ---老师，学生，运动员可以一起参加游泳比赛
     */
    public static void go(Swimming swimming){
        System.out.println("开始...");
        swimming.swim();
        System.out.println("--结束--");
    }
}
interface Swimming{
    void swim();
}
```

# Demo 3

## 深入理解

### 通过例题

###### 创建测试类

```java
package com.itheima.d8_innnerclass_anonymous;

import javax.swing.*;

/**
 * ---目标：通过GUI编程，理解匿名内部类的真实使用场景
 */
public class Test3 {
    public static void main(String[] args) {
        //创建窗口
        JFrame win = new JFrame("登录界面");
        //创建桌布
        JPanel panel = new JPanel();
        //把桌布对象添加到窗口上展示~
        win.add(panel);
        //创建一个按钮
        JButton button = new JButton("登录");
        //把按钮对象添加到桌布上展示~
        panel.add(button);
        //展示窗口
        win.setSize(300,400);
        win.setLocationRelativeTo(null);
        win.setVisible(true);
//        button.addActionListener(new ActionListener() {
//            @Override
//            public void actionPerformed(ActionEvent e) {
//                JOptionPane.showMessageDialog(win,"点一下，说明你爱我~");
//            }
//        });--------------------这就是匿名内部类的魅力！~~~~
        button.addActionListener(e ->JOptionPane.showMessageDialog(win,"别说话，吻我"));
    }
}

```

