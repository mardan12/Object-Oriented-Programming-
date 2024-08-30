# polymorphic_Test

## Java SE

### object oriented programming_面向对象

#### polymorphic

##### 例题

###### 创建接口

```Java
package com.itheima.d4_polymorphic_Test;

/**
 * USB == 规范
 */
public interface USB {
    //接入---拔出
    void connect();
    void unConnect();
}

```

创建实现类——电脑类

```java
package com.itheima.d4_polymorphic_Test;

public class Computer {
    private String name;

    public String getName() {
        return name;
    }
    public void start(){
        System.out.println(name+"电脑开机了~~~");
    }
    /**
     -- 提供安装USB设备的入口
     */
    public void installUSB(USB usb){
        //----多态----科能是鼠标，也有可能是键盘
        usb.connect();
        //独有功能---先判断再强转
        if (usb instanceof KeyBoard){
            KeyBoard k = (KeyBoard) usb;
            k.keyDown();
        }else if (usb instanceof Mouse){
            Mouse m = (Mouse) usb;
            m.dbClick();
        }

        usb.unConnect();
    }
    public void setName(String name) {
        this.name = name;
    }

    public Computer(String name) {
        this.name = name;

    }
}

```

###### 创建实现类——键盘类

```java
package com.itheima.d4_polymorphic_Test;

public class KeyBoard implements USB {
    private String name;

    public KeyBoard(String name) {
        this.name = name;
    }

    @Override
    public void connect() {
        System.out.println(name+"键盘成功连接了电脑~~");
    }

    /**
     -- 独有功能
     */
    public void keyDown(){
        System.out.println(name+"它敲击了，来了老弟，666~~没毛病~~~");
    }
    @Override
    public void unConnect() {
        System.out.println(name+"成功从电脑中拔出了~~~");
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}

```

创建实现类——鼠标类

```java
package com.itheima.d4_polymorphic_Test;

public class Mouse implements USB {
    private String name;

    public Mouse(String name) {
        this.name = name;
    }

    @Override
    public void connect() {
        System.out.println(name+"成功连接了电脑~~");
    }

    /**
     -- 独有功能
     */
    public void dbClick(){
        System.out.println(name+"双击点亮小红心，一键三连~~");
    }
    @Override
    public void unConnect() {
        System.out.println(name+"成功从电脑中拔出了~~~");
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}

```*![xx](https://github.com/user-attachments/assets/c900e1f2-71a8-4ed1-877f-1550534fb0ef)
**

