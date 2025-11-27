📚 Day 02 学习内容复盘：数据与运算
第一模块：计算机底层的秘密 (视频 01-03)
这部分主要是理论，让你理解计算机“脑子”里是怎么想的。
 * 核心概念： 计算机只认识 0 和 1 (二进制)。
 * 进制转换： 虽然平时用十进制，但程序员要了解二进制（0b开头）、八进制（0开头）、十六进制（0x开头）。
 * 存储原理： 文本（字符）在计算机里存的其实是数字（查ASCII码表或Unicode表），图片和视频本质上也是二进制数据。
> 💡 简单理解： 你敲入代码 int a = 10;，计算机底层其实存的是 0000...1010。
> 
第二模块：数据类型与转换 (视频 04-07) ✨ 重点
Java是强类型语言，数据必须分类存放。
1. 数据类型
 * 基本数据类型 (4类8种)：
   * 整数：byte, short, int (默认), long (后面加L)
   * 浮点数：float (后面加F), double (默认)
   * 字符：char (单引号)
   * 布尔：boolean (true/false)
2. 类型转换
 * 自动类型转换 (小变大)： 代码不需要处理，自动完成。例如 double d = 10; (10变成了10.0)。
 * 强制类型转换 (大变小)： 可能会丢数据，需要手动写格式。
💻 代码示例：
```java
public class TypeDemo {
    public static void main(String[] args) {
        // 1. 自动类型转换 (隐式)
        int a = 10;
        double b = a; // int -> double，安全
        System.out.println(b); // 输出 10.0

        // 2. 表达式类型的自动提升 (视频06内容)
        // byte, short, char 在运算时会自动提升为 int
        byte b1 = 10;
        byte b2 = 20;
        // byte b3 = b1 + b2; // ❌ 报错！因为结果已经是int了
        int result = b1 + b2; // ✅ 正确

        // 3. 强制类型转换 (显式)
        double d = 88.88;
        int i = (int) d; // 强制把double切掉小数部分变成int
        System.out.println(i); // 输出 88 (精度丢失)
    }
}
```
第三模块：运算符大礼包 (视频 08-15) 🔥 核心难点
这是今天内容最多、最需要练习的部分。
1. 算术运算符与数值拆分
 * +, -, *, / (整除), % (取余数)。
 * 视频09 拆分数字： 这是经典算法题，提取个位、十位、百位。
2. 自增自减 (++, --)
 * 单独使用： i++ 和 ++i 没区别。
 * 参与运算：
   * int b = i++; -> 先把i的值给b，i再自增（先用后加）。
   * int b = ++i; -> i先自增，再把新值给b（先加后用）。
3. 逻辑与三元运算符
 * && (短路与)：左边为false，右边不执行。
 * || (短路或)：左边为true，右边不执行。
 * 三元运算符： 关系表达式 ? 结果1 : 结果2 (简化的if-else)。
💻 代码示例：
```java
public class OperatorDemo {
    public static void main(String[] args) {
        // --- 1. 拆分数字 (视频09经典案例) ---
        int num = 153;
        int ge  = num % 10;        // 个位：3
        int shi = num / 10 % 10;   // 十位：5
        int bai = num / 100;       // 百位：1
        System.out.println("百位:" + bai + ", 十位:" + shi + ", 个位:" + ge);

        // --- 2. 自增的坑 (视频11) ---
        int x = 10;
        int y = x++; // y是10，x变成了11
        int z = ++x; // x变成了12，z是12
        System.out.println("y=" + y + ", z=" + z);

        // --- 3. 扩展赋值运算符 (视频12) ---
        int a = 5;
        a += 10; // 等同于 a = (int)(a + 10); 自带强转功能
        
        // --- 4. 三元运算符 (视频15) ---
        // 求两个数的最大值
        int m = 10;
        int n = 20;
        int max = (m > n) ? m : n;
        System.out.println("最大值是：" + max);
    }
}
```
第四模块：人机交互 Scanner (视频 16)
这是你写的程序第一次能“动”起来，不仅仅是输出死数据。
 * 步骤： 导包 (import) -> 创建对象 (new) -> 接收数据 (nextInt).
💻 代码示例：
```java
// 1. 导包
import java.util.Scanner;

public class ScannerDemo {
    public static void main(String[] args) {
        // 2. 创建对象
        Scanner sc = new Scanner(System.in);
        
        System.out.println("请输入一个整数：");
        // 3. 接收数据
        int number = sc.nextInt();
        
        System.out.println("你输入的数字是：" + number);
    }
}
```
🚀 今天的练习建议
题目：老虎体重比拼
> 需求：使用 Scanner 录入两只老虎的体重（整数），使用三元运算符判断两只老虎的体重是否相同，如果不相同，输出较重的那只老虎的体重。
> 
这个练习会用到：Scanner、变量定义、关系运算符 ==、三元运算符 ? :。
你要不要试着写一下这个代码？如果写不出来，我可以把答案给你参考。
