# abstract_test

## 抽象类的简单使用

### Java SE

#### 模拟做卡片

###### 抽象类

```java
package d2_abstract_test;

public abstract class Card {
    private String userName;
    private double money;
    /**
     *定义一个支付方法
     */
    public abstract void pay(double money);
    public String getUserName() {
        return userName;
    }

    public void setUserName(String userName) {
        this.userName = userName;
    }

    public double getMoney() {
        return money;
    }

    public void setMoney(double money) {
        this.money = money;
    }
}

```

###### 实现类

```java
package d2_abstract_test;

public class GoldCard extends Card{
    @Override
    public void pay(double money) {
        System.out.println(getUserName());
        System.out.println("您当前消费："+money);
        System.out.println("您卡片当前余额："+getMoney());
        double rs = money*0.8;
        System.out.println("您实际支付金额："+rs);
        //更新账户余额
        setMoney(getMoney()-rs);
    }
}

```

###### 测试类

```java
package d2_abstract_test;

public class Test {
    public static void main(String[] args) {
        //目标，学习以下抽象类的基本使用，做父类，被继承，重写抽象方法
        GoldCard g = new GoldCard();
        g.setMoney(100000);
        g.setUserName("麦尔旦");
        g.pay(3000);
        System.out.println("余额："+g.getMoney());
    }
}

```

