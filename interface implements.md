# interface implements

## 接口的规范

### Java SE

#### 接口的规范并使用

##### 例子

###### 接口

```Java
package d6_interface_implements;

public interface Low {
    void rule();

}

```

###### 接口

```Java
package d6_interface_implements;

/**
 * 规范
 */
public interface SportMan {
    void run();
    void competition();


}

```

###### 实现类

```Java
package d6_interface_implements;

/**
 * 实现类
 */
public class PingPongMan implements SportMan,Low{
    private String name;

    public PingPongMan(String name) {
        this.name = name;
    }

    @Override
    public void run() {
        System.out.println(name+"必须跑步训练！");
    }

    @Override
    public void competition() {
        System.out.println(name+"要参加比赛，为国争光~");
    }

    @Override
    public void rule() {
        System.out.println(name+"必须守法~");
    }
}

```

###### 测试类

```Java
package d6_interface_implements;

/**
 * 测试类
 */
public class Test {
    public static void main(String[] args) {
        //目标：理解接口的基本使用，被类实现
        PingPongMan p = new PingPongMan("麦尔旦");
        p.run();
        p.competition();
        p.rule();
    }
}

```

