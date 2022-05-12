# enum

## ConstantDemo2

### JavaSE

###### 枚举类

```java
package constant;
enum Orientation {
    UP,DOWN,LEFT,RIGHT
}

```

###### 测试类

```java
package constant;
import javax.swing.*;
import java.awt.event.ActionEvent;

public class ConstantDemo2 {
    public static void main(String[] args) {
        //创建一个窗口对象(桌子)
        JFrame win = new JFrame();
        //创建一个面板对象（桌布）
        JPanel panel = new JPanel();
        //把桌布垫在桌子上
        win.add(panel);
        //创建四个按钮对象
        JButton button1 = new JButton("上");
        JButton button2 = new JButton("下");
        JButton button3 = new JButton("左");
        JButton button4 = new JButton("右");
        //把按钮对象添加到桌布上
        panel.add(button1);
        panel.add(button2);
        panel.add(button3);
        panel.add(button4);
        //显示窗口
        win.setLocationRelativeTo(null);
        win.setSize(300,400);
        win.setVisible(true);
        button1.addActionListener(new AbstractAction() {
            @Override
            public void actionPerformed(ActionEvent e) {
                move(Orientation.UP);
            }
        });
        button2.addActionListener(new AbstractAction() {
            @Override
            public void actionPerformed(ActionEvent e) {
                move(Orientation.DOWN);
            }
        });
        button3.addActionListener(new AbstractAction() {
            @Override
            public void actionPerformed(ActionEvent e) {
                move(Orientation.LEFT);
            }
        });
        button4.addActionListener(new AbstractAction() {
            @Override
            public void actionPerformed(ActionEvent e) {
                move(Orientation.RIGHT);
            }
        });
    }
    public static void move(Orientation orientation){
        switch (orientation) {
            case UP -> System.out.println("玛丽往上飞了一下~~");
            case DOWN -> System.out.println("玛丽往下蹲了一下~~");
            case LEFT -> System.out.println("玛丽往左跑了一下~~");
            case RIGHT -> System.out.println("玛丽往右跑了一下~~");
        }
    }
}

```

