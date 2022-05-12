# Geme_Mardan

## Java SE

### oop

#### 自己模拟做的一个模拟小游戏

###### 用户类

```java
package java_Mardan;

public class Users {
    private String name;
    private String gander;
    private String id;
    private String passWord;
    private double money;

    public double getMoney() {
        return money;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getGander() {
        return gander;
    }

    public void setGander(String gander) {
        this.gander = gander;
    }

    public String getId() {
        return id;
    }

    public void setId(String id) {
        this.id = id;
    }

    public String getPassWord() {
        return passWord;
    }

    public void setPassWord(String passWord) {
        this.passWord = passWord;
    }

    public void setMoney(double money) {
        this.money = money;
    }
}

```

###### 工具类

```java
package java_Mardan;
import java.util.Random;
import java.util.ArrayList;
import java.util.Scanner;
public final class GamesUtil {
    private static final Scanner sc = new Scanner(System.in);
    private static final Random r = new Random();
    static  int randomNumber = r.nextInt(99)+1;
    static char random = (char) (r.nextInt(26)+65);
    public static ArrayList<Users>users = new ArrayList<>();
    public static final ArrayList<String> Cards = new ArrayList<>();
    private GamesUtil() {
    }
    static {
        String[] number = {"2", "3", "4", "5", "6", "7", "8", "9", "10", "J", "Q", "K", "A"};
        String[] color = {"♠","♥","♦","♣"};
        for (String s : number) {
            for (String value : color) {
                String card = (s + value);
                Cards.add(card);
            }
        }
                Cards.add("大🃏");
        Cards.add("小🃏");
    }
    private static void marDan(){
        //用for语句四个牌一组的输出
        System.out.println("==========本游戏由麦尔旦独自开发==========");
        for (int i = 0; i < Cards.size(); i++) {
            if (i%4==0){
                System.out.println(i==0?"\n"+"新牌：":"\n");
                System.out.print(Cards.get(i));
            }else {
                System.out.print(Cards.get(i));
            }
        }
    }
    private static void NiuNiu(){
        System.out.println("==========本游戏由麦尔旦独自开发==========");
        while (true) {
        System.out.println("\t"+"\t"+"麦尔平台"+"\t"+"\t");
        System.out.println("------欢迎进入斗牛游戏------");
        System.out.println("请选择模式:");
        System.out.println("《1.单人模式》");
        System.out.println("《2.双人模式》");
        int type = sc.nextInt();
            switch (type){
                case 1:
                    for (int i = 0; i < 5; i++) {
                        int index = r.nextInt(Cards.size()-2);
                        System.out.print(i==0?"您的牌是："+Cards.get(index)+"\t":Cards.get(index)+"\t");
                    }
                    System.out.println();
                    break;
                case 2:
                    for (int j = 0; j < 2; j++) {
                        if (j==0){
                            System.out.println("第一位赌神：");
                        }else {
                            System.out.println("第二位赌神：");
                        }
                        for (int i = 0; i < 5; i++) {
                            int index = r.nextInt(Cards.size());
                            System.out.print(i==0?"您的牌是："+Cards.get(index)+"\t":Cards.get(index)+"\t");
                        }
                        System.out.println();
                    }
                    break;
                case 121:
                    return;
                default:
                    System.out.println("输入有误！请重新输入！");
            }
        }
    }
    private static void ZhaJinHua(){
        System.out.println("==========本游戏由麦尔旦独自开发==========");
        while (true) {
            System.out.println("\t"+"\t"+"麦尔平台"+"\t"+"\t");
            System.out.println("------欢迎进入砸金花游戏------");
            System.out.println("请选择模式:");
            System.out.println("《1.单人模式》");
            System.out.println("《2.双人模式》");
            int type = sc.nextInt();
            switch (type){
                case 1:
                    for (int i = 0; i < 3; i++) {
                        int index = r.nextInt(Cards.size());
                        System.out.print(i==0?"您的牌是："+Cards.get(index)+"\t":Cards.get(index)+"\t");
                    }
                    System.out.println();
                    break;
                case 2:
                    for (int j = 0; j < 2; j++) {
                        if (j==0){
                            System.out.println("第一位赌神：");
                        }else {
                            System.out.println("第二位赌神：");
                        }
                        for (int i = 0; i < 3; i++) {
                            int index = r.nextInt(Cards.size());
                            System.out.print(i==0?"您的牌是："+Cards.get(index)+"\t":Cards.get(index)+"\t");
                        }
                        System.out.println();
                    }
                    break;
                case 121:
                    return;
                default:
                    System.out.println("输入有误！请重新输入！");
            }
        }

    }
    private static void RandomNumbers(){
        System.out.println("====麦尔猜数字游戏====");
        System.out.println("请选择模式：");
        System.out.println("1.《单人模式》");
        System.out.println("2.《双人模式》");
        int type = sc.nextInt();
        switch (type){
            case 1:
                System.out.println("====麦尔猜数字游戏====");
                System.out.println("你要猜的数字已准备好！");
                for (int i = 0; i < 6; i++) {
                    System.out.println("请开始猜测吧（范围1——99）：");
                    int UserNumber = sc.nextInt();
                    if (randomNumber > UserNumber){
                        System.out.println("您猜小了哟~~，继续加油！你还有"+(5-i)+"次机会！");
                    }else if (randomNumber < UserNumber){
                        System.out.println("您猜大了哟~~，继续加油！你还有"+(5-i)+"次机会！");
                    }else if (randomNumber + 3 == UserNumber || randomNumber - 3 ==UserNumber){
                        System.out.println("哇哦，很接近了哟~~，离胜利就差一步！你还有"+(5-i)+"次机会！");
                    }else if (randomNumber == UserNumber){
                        System.out.println("哇噢！太帅了~~恭喜您猜中啦！");
                        break;
                    }
                }
                break;
            case 2:
                System.out.println("====麦尔猜数字游戏====");
                System.out.println("你要猜的数字已准备好！");
                while (true) {
                    for (;;) {
                        System.out.println("请开始猜测吧（范围1——99）：");
                        System.out.println("第一位：");
                        int UserNumber = sc.nextInt();
                        if (randomNumber > UserNumber){
                            System.out.println("您猜小了哟~~，继续加油！");
                            break;
                        }else if (randomNumber < UserNumber){
                            System.out.println("您猜大了哟~~，继续加油！");
                            break;
                        }else if (randomNumber + 3 == UserNumber || randomNumber - 3 ==UserNumber){
                            System.out.println("哇哦，很接近了哟~~，离胜利就差一步！");
                            break;
                        }else if (randomNumber == UserNumber){
                            System.out.println("哇噢！太帅了~~恭喜您猜中啦！");
                            System.out.println("第一位选手赢了~~");
                            return;
                        }
                    }
                    for (;;) {
                        System.out.println("请开始猜测吧（范围1——99）：");
                        System.out.println("第二位：");
                        int UserNumber1 = sc.nextInt();
                        if (randomNumber > UserNumber1){
                            System.out.println("您猜小了哟~~，继续加油！");
                            break;
                        }else if (randomNumber < UserNumber1){
                            System.out.println("您猜大了哟~~，继续加油！");
                            break;
                        }else if (randomNumber + 3 == UserNumber1 || randomNumber - 3 ==UserNumber1){
                            System.out.println("哇哦，很接近了哟~~，离胜利就差一步！");
                            break;
                        }else if (randomNumber == UserNumber1){
                            System.out.println("哇噢！太帅了~~恭喜您猜中啦！");
                            System.out.println("第二位选手赢了~~");
                            return;
                        }
                    }
                }
            case 3:
                return;
            default:
                System.out.println("输入有误！");
        }
    }
    private static void RandomAbc(){
        while (true) {
            System.out.println("====麦尔猜字母游戏====");
            System.out.println("请选择模式：");
            System.out.println("1.《单人模式》");
            System.out.println("2.《双人模式》");
            int type = sc.nextInt();
            switch (type){
                case 1:
                    System.out.println("====麦尔猜英文字母游戏====");
                    System.out.println("字母已准备好~~，请开始猜测...");
                    for (int i = 0; i < 10; i++) {
                        System.out.println("请输入范围在A~Z的字母猜测（不分大小写）：");
                        String UserRandom = sc.next();
                        if (UserRandom.equalsIgnoreCase(String.valueOf(random))){
                            System.out.println("哇哦，恭喜您猜中啦！真聪明！");
                            break;
                        }else {
                            System.out.println("没猜中哦！继续加油！您还有"+(9-i)+"次机会");
                        }
                    }
                    break;
                case 2:
                    while (true) {
                        for (;;) {
                            System.out.println("请输入范围在A~Z的字母猜测（不分大小写）");
                            System.out.println("第一位：");
                            String UserRandom = sc.next();
                            if (UserRandom.equalsIgnoreCase(String.valueOf(random))){
                                System.out.println("哇哦，恭喜您猜中啦！真聪明！");
                                return;
                            }else {
                                System.out.println("没猜中哦！继续加油！");
                                break;
                            }
                        }
                        for (;;) {
                            System.out.println("请输入范围在A~Z的字母猜测（不分大小写）");
                            System.out.println("第二位：");
                            String UserRandom1 = sc.next();
                            if (UserRandom1.equalsIgnoreCase(String.valueOf(random))){
                                System.out.println("哇哦，恭喜您猜中啦！真聪明！");
                                return;
                            }else {
                                System.out.println("没猜中哦！继续加油！");
                                break;
                            }
                        }
                    }
                case 3:
                    return;
                default:
                    System.out.println("输入有误！");
            }
        }

    }
    private static void RandomGames(){
        System.out.println("==========本游戏由麦尔旦独自开发==========");
        while (true) {
            System.out.println("请选择游戏模式：");
            System.out.println("1.《麦尔数字猜测游戏》");
            System.out.println("2.《麦尔字母猜测游戏》");
            System.out.println("3.《退出游戏》");
            int type = sc.nextInt();
            switch (type){
                case 1:
                    RandomNumbers();
                    break;
                case 2:
                    RandomAbc();
                    break;
                case 3:
                    return;
                default:
                    System.out.println("输入有误！请重新输入！");
            }
        }
    }
    private static void userRegister(){
        Users user = new Users();
        System.out.println("请输入您的用户名：");
        user.setName(sc.next());
        System.out.println("请输入您的性别：1.《男》2.《女》");
        gander(user);
        while (true) {
            System.out.println("请输入您的密码：");
            String OkPassWord = sc.next();
            System.out.println("请再次输入确认密码（两次输入要一致！）");
            String passWord = sc.next();
            if (passWord.equals(OkPassWord)){
                user.setPassWord(OkPassWord);
                break;
            }else {
                System.out.println("两次输入不一致，请重新输入！");
            }
        }
        System.out.println();
        user.setId(generateCardNumber(users));
        System.out.print(user.getGander().equals("男")?user.getName()+"先生"+",":user.getName()+"女士"+",");
        System.out.println("恭喜你成为了麦尔集团的用户！注册成功！");
        System.out.print("您的卡号是：");
        System.out.println("您的卡号为："+user.getId()+",请保管好！");
        users.add(user);
    }
    private static String generateCardNumber(ArrayList<Users>users) {
        StringBuilder CardId = new StringBuilder();//用累加生成的随机数
        while (true) {
            //生成八位数
            for (int i = 0; i < 8; i++) {
                int userid = r.nextInt(10);
                CardId.append(userid);
            }
            //如果一样说明此卡号已注册的，继续生成直到不一样为止
            Users acc = getUsersByCardId(CardId.toString(),users);
            if (acc == null){
                return CardId.toString();
            }
        }
    }
    private static Users getUsersByCardId(String cardId , ArrayList<Users>users) {
        /*
        这里因为我们不知道集合的长度是多少，可能是很多，更适合用while循环来遍历
        也可以用for循环，我是用了while可以参考一下！
         for (int i = 0; i < accounts.size(); i++) {
        Account acc = accounts.get(i);
        if (acc.getCardId().equals(cardId)) {
        return acc;
        }
        }
               */
        int i = 0;
        while (i < users.size()) {
            Users acc = users.get(i);
            if (acc.getId().equals(cardId)) {
                return acc;
            }
            i++;
        }
        return null;
    }
    private static void gander(Users u){
        while (true) {
            int gander = sc.nextInt();
            switch (gander) {
                case 1 -> {
                    u.setGander("男");
                    return;
                }
                case 2 -> {
                    u.setGander("女");
                    return;
                }
                default -> System.out.println("输入有误！请重新输入！");
            }
        }
    }
    private static void userLogin() {
        String codes = codes();
        System.out.println("====================麦尔集团====================");
        //1.判断账户集合中是否存在账户，如果不存在账户登录功能不能进行
        if (users.size() == 0){
            System.out.println("对不起，当前系统中无任何账户，请先注册账户，再进行登录操作！");
            return;//卫语言风格，结束方法的执行！
        }
        //2.正式进入登录操作
        while (true) {
            System.out.println("请输入登录卡号：");
            String cardId = sc.next();
            //3.查询集合是否有此账户，如果有返回账户对象，如果没有返回null
            Users acc = getUsersByCardId(cardId,users);
            if (acc != null){
                //存在此账户
                //4.让用户输入密码，然后认证密码
                for (int i=0;i<3;i++){
                    System.out.println("请您输入登录密码：");
                    String passWord = sc.next();
                    if (acc.getPassWord().equals(passWord)){
                        System.out.print("您的验证码为："+"\t");
                        System.out.println(codes);
                        System.out.println("请输入您的验证码：");
                        String UserCodes = sc.next();
                        if (codes.equalsIgnoreCase(UserCodes)) {
                            //登录成功了
                            System.out.print(acc.getGander().equals("男")?acc.getName()+"先生"+",":acc.getName()+"女士"+",");
                            System.out.println("登录成功！，你的卡号为："+acc.getId());
                            // ...转账，查询，存款...
                            //展示登录后的操作页
                            showUserCommand(acc,users);
                            return;
                        }else {
                            System.out.println("对不起，你输入的验证码有误！您还有"+(2-i)+"次输入机会");
                        }
                    }
                    else{
                        System.out.println("对不起，你输入的密码有误！您还有"+(2-i)+"次输入机会");
                    }
                }
                return;
            }else{
                System.out.println("对不起，系统中查无此号！请重新输入呢？！");
            }
        }
    }
    private static void showUserCommand(Users acc, ArrayList<Users> users) {
        while (true) {
            System.out.println("====================麦尔集团用户操作页====================");
            System.out.println("1.查看麦尔扑克牌");
            System.out.println("2·查询账户");
            System.out.println("3·麦尔斗牛游戏");
            System.out.println("4·麦尔炸金花游戏");
            System.out.println("5.麦尔猜测游戏");
            System.out.println("6·修改密码");
            System.out.println("7·退出");
            System.out.println("8·注销账户");
            System.out.println("9.存钱");
            System.out.println("请选择：");
            int command = sc.nextInt();
            switch (command){
                case 1:
                    //查询账户，展示当前登录的账户
                    marDan();
                    break;
                case 2:
                    showUsers(acc);
                    break;
                case 3:
                    NiuNiu();
                    break;
                case 4:
                    ZhaJinHua();
                    break;
                case 5:
                    RandomGames();
                    break;
                case 6:
                    updatePassWord(acc);
                case 7:
                    //退出
                    System.out.println("退出成功！欢迎下次光临！");
                    return;//停止当前方法执行，跳出去！
                case 8:
                    //注销账户
                    //从当前账户集合中，删掉当前账户对象。
                    if(deleteUsers(acc,users)){
                        return;//返回值为true，删除当前对象并且退出此方法
                    }
                    else {
                        break;//返回值为false,结束switch，用户可以继续在此方法内选择相应的操作；、
                    }
                case 9:
                    setMoney(acc);
                    break;
                default:
                    System.out.println("你输入的操作命令不正确！请重新输入！");
            }
        }
    }
    private static void showUsers(Users acc) {
        System.out.println("====================麦尔集团登录账户信息如下====================");
        System.out.println("卡号："+acc.getId());
        System.out.println("姓名："+acc.getName());
        System.out.println("性别："+acc.getGander());
        System.out.println("余额："+acc.getMoney()+"元人民币");
    }
    private static void updatePassWord(Users acc) {
        System.out.println("====================用户密码修改操作====================");
        System.out.println("请您输入原密码：");
        String passWord = sc.next();
        while (true) {
            if (acc.getPassWord().equals(passWord)){
                //输入正确
                //输入新的密码
                while (true) {
                    System.out.println("请您输入新密码：");
                    String newPassWord = sc.next();
                    System.out.println("请您再输入一次确认密码：");
                    String okPassWord = sc.next();
                    //判断两次输入的密码是否一致
                    if (newPassWord.equals(okPassWord)){
                        System.out.println("恭喜你！密码修改成功！");
                        acc.setPassWord(newPassWord);
                        return;//修改成功，停掉此方法
                    }else{
                        System.out.println("你输入的两次密码不一致！请重新输入！");
                    }
                }
            }else{
                System.out.println("您输入的原密码不正确,请重新输入！");
            }
        }
    }
    private static boolean deleteUsers(Users acc, ArrayList<Users> users) {
        //注销账户
        //从当前账户集合中，删掉当前账户对象。
        System.out.println("您确定要注销吗老铁！are you sure!?");
        System.out.println("注销请输入”y“ ，不注销请输入”n“");
        String rs = sc.next();
        switch (rs){
            case "y":
                //真正注销
                if (acc.getMoney() > 0){
                    System.out.println("对不起，您账户里还有金额没取走，是不可以注销的哦！");
                }else {
                    //已经确定没有余额了，直接注销
                    users.remove(acc);//删除集合内的对象
                    System.out.println("好的，已经给您注销了次账户！");
                    return true;//删除成功
                }
            case "Y":
                //真正注销
                if (acc.getMoney() > 0){
                    System.out.println("对不起，您账户里还有金额没取走，是不可以注销的哦！");
                }else {
                    //已经确定没有余额了，直接注销
                    users.remove(acc);//删除集合内的对象
                    System.out.println("好的，已经给您注销了次账户！");
                    return true;//删除成功
                }
            case "n":
                System.out.println("好的，此账户已经给您保留了哦！感谢您的使用！");
                return false;//用户取消注销
            case "N":
                System.out.println("好的，此账户已经给您保留了哦！感谢您的使用！");
                return false;//用户取消注销
            default:
                System.out.println("您输入的命令有误哦！");
        }
        return false;//取消注销
    }
    public static void MeirGroup(){
        System.out.println("      ==========本平台由麦尔旦独自开发==========");
        while (true) {
            System.out.println("=*==*==*==*==*==*=欢迎您来到麦尔平台=*==*==*==*==*==*=");
            System.out.println("请选择：");
            System.out.println("1.《登录账户》");
            System.out.println("2.《注册账户》");
            int type = sc.nextInt();
            switch (type){
                case 1:
                    userLogin();
                    break;
                case 2:
                    userRegister();
                    break;
                case 121:
                    return;
                case 666:
                    NiuNiu();
                default:
                    System.out.println("输入有误！");
            }
        }
    }
    private static String codes(){
        StringBuilder code = new StringBuilder();
        String data = "1234567890ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz";
        for (int i = 0; i < 4; i++) {
            int index = r.nextInt(data.length());
            code.append(data.charAt(index));
        }
        return code.toString();
    }
    private static void setMoney (Users acc){
        System.out.println("请输入您要存储的金额~");
        double money = sc.nextDouble();
        acc.setMoney(acc.getMoney()+money);
        System.out.println("亲爱的，"+acc.getName()+acc.getGander()+"恭喜你存储成功~");
        System.out.println("现有余额为："+acc.getMoney()+"元人民币");
    }
}

```

###### 测试类

###### 跨包导包运行的，也可以本包内运行

```java
package java_;
import java_Mardan.GamesUtil;
public class Test {
    public static void main(String[] args) {
        GamesUtil.MeirGroup();
    }
}



```

