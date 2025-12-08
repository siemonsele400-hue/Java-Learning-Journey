  ### 1\_编程案例

**【知识点文字解析】**

  * **核心概念**：这个视频是课程的引入。它强调了从“学会语法”到“解决问题”的思维转变。
  * **学习重点**：
    1.  **审题**：先搞清楚输入是什么，输出是什么。
    2.  **拆解**：把复杂问题拆成几个小步骤（例如：先判断A，再循环B，最后计算C）。
    3.  **方法封装**：为了代码复用，尽量把独立逻辑写成方法，而不是全塞在 `main` 方法里。

**【代码案例】**

```java
public class TemplateDemo {
    public static void main(String[] args) {
        // 1. 准备数据（输入）
        int inputData = 100;
        
        // 2. 调用方法处理逻辑（处理）
        int result = doSomething(inputData);
        
        // 3. 展示结果（输出）
        System.out.println("结果是：" + result);
    }

    // 独立的功能方法
    public static int doSomething(int num) {
        // 具体的算法逻辑
        return num * 2;
    }
}
```

**【代码解析】**

  * **模块化**：`main` 方法只负责指挥（输入和输出），具体的脏活累活交给下面的 `doSomething` 方法。这是编程思维的第一步。

-----

### 2\. 视频：02\_买飞机票

**【知识点文字解析】**

  * **业务逻辑**：根据月份（旺季/淡季）、舱位（头等/经济）计算折后票价。
  * **编程考点**：
      * **多重判断**：`if-else` 中嵌套 `switch-case`。
      * **逻辑分层**：先判断大前提（月份），再判断小前提（舱位）。

**【完整代码】**

```java
import java.util.Scanner;

public class TicketTest {
    public static void main(String[] args) {
        // 模拟输入：原价1000，5月，头等舱
        double price = calculate(1000, 5, "头等舱");
        System.out.println("最终票价：" + price);
    }

    public static double calculate(double price, int month, String type) {
        // 1. 判断月份（旺季：5-10月）
        if (month >= 5 && month <= 10) {
            switch (type) {
                case "头等舱":
                    price *= 0.9; // 9折
                    break;
                case "经济舱":
                    price *= 0.85; // 85折
                    break;
            }
        } else if ((month >= 1 && month <= 4) || (month >= 11 && month <= 12)) {
            // 2. 淡季（11-12月, 1-4月）
            switch (type) {
                case "头等舱":
                    price *= 0.7; // 7折
                    break;
                case "经济舱":
                    price *= 0.65; // 65折
                    break;
            }
        } else {
            System.out.println("月份输入非法");
        }
        return price;
    }
}
```

**【代码解析】**

  * `price *= 0.9`：这是 `price = price * 0.9` 的缩写，直接修改变量的值。
  * `month >= 5 && month <= 10`：利用逻辑运算符确定范围。
  * **健壮性**：代码考虑了月份输入的合法性（虽然案例简单，但 `else` 处理非法情况是好习惯）。

-----

### 3\. 视频：03\_验证码

**【知识点文字解析】**

  * **业务逻辑**：随机生成 N 位验证码，内容可能包含大小写字母和数字。
  * **编程考点**：
      * **查表法**：将所有可能的字符存入一个 `char` 数组（或者字符串）。
      * **Random类**：生成随机索引，去数组中抓取字符。
      * **字符串拼接**：使用 `+` 操作符连接字符。

**【完整代码】**

```java
import java.util.Random;

public class CodeTest {
    public static void main(String[] args) {
        String code = createCode(5); // 生成5位验证码
        System.out.println("生成的验证码：" + code);
    }

    public static String createCode(int n) {
        // 1. 定义字符库（表）
        String data = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789";
        
        String result = "";
        Random r = new Random();

        // 2. 循环n次，每次随机抓一个
        for (int i = 0; i < n; i++) {
            // 随机索引范围：0 到 data长度-1
            int index = r.nextInt(data.length());
            // charAt(index) 获取字符串该位置的字符
            result += data.charAt(index);
        }
        return result;
    }
}
```

**【代码解析】**

  * `data.length()`：动态获取字符库长度，这样如果你想增加特殊符号，只需要改 `data` 字符串，下面逻辑不用动。
  * `result += ...`：将每次抓到的字符拼接到结果后面。

-----

### 4\. 视频：04\_评委打分

**【知识点文字解析】**

  * **业务逻辑**：6个评委打分，去掉最高分，去掉最低分，求剩下分数的平均值。
  * **编程考点**：
      * **数组综合操作**：在一个循环中同时完成求和、找最大值、找最小值。
      * **精度控制**：整数相除会丢精度，计算平均值时要注意转为 `double`。

**【完整代码】**

```java
public class ScoreTest {
    public static void main(String[] args) {
        int[] scores = {80, 90, 100, 50, 70, 60}; // 模拟录入的分数
        double avg = getAvg(scores);
        System.out.println("选手最终得分：" + avg);
    }

    public static double getAvg(int[] arr) {
        int sum = 0;
        int max = arr[0]; // 假设第一个最大
        int min = arr[0]; // 假设第一个最小

        // 1. 遍历数组
        for (int i = 0; i < arr.length; i++) {
            int score = arr[i];
            sum += score; // 累加

            if (score > max) max = score; // 更新最大
            if (score < min) min = score; // 更新最小
        }

        // 2. 计算平均分
        // 核心公式：(总分 - 最大 - 最小) / (人数 - 2)
        // 注意 * 1.0 的作用是将整型转为浮点型运算
        double result = (sum - max - min) * 1.0 / (arr.length - 2);
        
        return result;
    }
}
```

**【代码解析】**

  * `max = arr[0]`：初始化最大/最小值一定要用数组里的元素，不能简单的赋值为 0（万一全是负数就错了）。
  * `* 1.0`：这是 Java 中的小技巧。`int / int` 结果是 `int`（例如 `10/3=3`）。想要得到 `3.33`，必须让除号两边至少有一个是小数，所以乘以 1.0。

-----

### 5\. 视频：05\_加密程序

**【知识点文字解析】**

  * **业务逻辑**：数字加密。规则通常是：每位数字 +5，然后对10取余，最后将所有数字反转。
  * **编程考点**：
      * **数值拆分**：如果输入是整型数字，需要拆成数组。
      * **取余运算 (%)**：用于限制数字范围（0-9）。
      * **数组反转**：经典的“首尾交换”算法。

**【完整代码】**

```java
public class EncryptTest {
    public static void main(String[] args) {
        // 假设密码是 1983，先存入数组
        int[] arr = {1, 9, 8, 3};
        
        // 1. 加密操作：+5 然后 %10
        for (int i = 0; i < arr.length; i++) {
            arr[i] = (arr[i] + 5) % 10;
        }

        // 2. 反转数组
        for (int i = 0, j = arr.length - 1; i < j; i++, j--) {
            int temp = arr[i];
            arr[i] = arr[j];
            arr[j] = temp;
        }

        // 3. 打印结果
        System.out.print("加密后的密码：");
        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i]);
        }
    }
}
```

**【代码解析】**

  * `(arr[i] + 5) % 10`：
      * 1 -\> 1+5=6 -\> 6%10=6
      * 9 -\> 9+5=14 -\> 14%10=4
  * `for (int i = 0, j = arr.length - 1; i < j; i++, j--)`：这是一个高效的双指针写法。`i` 从头往后走，`j` 从尾往前走，当 `i < j` 时交换，相遇则停止。

-----

### 6\. 视频：06\_数组拷贝

**【知识点文字解析】**

  * **业务逻辑**：将一个数组的内容复制到一个全新的数组中。
  * **编程考点**：**深拷贝 vs 浅拷贝**。
      * 错误写法：`int[] arr2 = arr1;` （这只是给了地址，是同一个数组）。
      * 正确写法：`new` 一个新数组，循环赋值。

**【完整代码】**

```java
public class CopyTest {
    public static void main(String[] args) {
        int[] arr1 = {11, 22, 33, 44};
        int[] arr2 = copyArray(arr1);

        System.out.println("原数组第一个：" + arr1[0]);
        System.out.println("新数组第一个：" + arr2[0]);
        
        // 验证：修改新数组，原数组不会变
        arr2[0] = 999;
        System.out.println("修改后新数组：" + arr2[0]);
        System.out.println("修改后原数组：" + arr1[0]); // 还是11
    }

    public static int[] copyArray(int[] arr) {
        // 1. 创建一个长度一样的空数组
        int[] newArr = new int[arr.length];

        // 2. 遍历原数组，把值搬运过去
        for (int i = 0; i < arr.length; i++) {
            newArr[i] = arr[i];
        }

        // 3. 返回新数组
        return newArr;
    }
}
```

**【代码解析】**

  * `new int[arr.length]`：这是核心。必须在堆内存中开辟一块**新**的空间。
  * `return newArr`：返回的是新数组的内存地址。

-----

### 7\. 视频：07\_抢红包

**【知识点文字解析】**

  * **业务逻辑**：有 5 个固定金额的红包（如 {2, 588, 888, 1000, 10000}），随机发给 5 个人，不能重复。
  * **编程考点**：**随机抽取不重复**。
  * **技巧**：可以利用 Day 04 学过的“数组打乱（Shuffle）”，先把红包数组的顺序打乱，然后按顺序发给 5 个人即可。

**【完整代码】**

```java
import java.util.Random;

public class RedPacketTest {
    public static void main(String[] args) {
        int[] moneys = {2, 588, 888, 1000, 10000};
        startRedPacket(moneys);
    }

    public static void startRedPacket(int[] arr) {
        Random r = new Random();
        
        // 1. 核心算法：打乱数组顺序 (洗牌)
        for (int i = 0; i < arr.length; i++) {
            int index = r.nextInt(arr.length);
            // 交换
            int temp = arr[i];
            arr[i] = arr[index];
            arr[index] = temp;
        }

        // 2. 按顺序发红包
        for (int i = 0; i < arr.length; i++) {
            System.out.println("第" + (i + 1) + "个粉丝抽中了：" + arr[i] + "元");
        }
    }
}
```

**【代码解析】**

  * 如果不打乱数组，你就需要用复杂的逻辑去记录哪个红包被抽过了（check exists）。
  * **逆向思维**：把红包打乱（洗牌），然后依次发出去，既满足了“随机”，又天然满足了“不重复”。

-----

### 8\. 视频：08\_找素数

**【知识点文字解析】**

  * **概念**：素数是只能被 1 和它本身整除的数（如 3, 5, 7, 11）。
  * **编程考点**：**假设法（Flag思想）**。
      * 假设它是素数（flag = true）。
      * 尝试从 2 到 n-1 去除它。
      * 如果能除尽，说明假设失败（flag = false）。

**【完整代码】**

```java
public class PrimeTest1 {
    public static void main(String[] args) {
        System.out.println("101是素数吗？" + isPrime(101));
        System.out.println("100是素数吗？" + isPrime(100));
    }

    public static boolean isPrime(int n) {
        // 小于2的不是素数
        if (n < 2) return false;

        // 假设是素数，尝试反证
        for (int i = 2; i < n; i++) {
            if (n % i == 0) {
                // 发现能被i整除，说明不是素数
                return false; 
            }
        }
        // 循环走完都没触发 return false，说明它是素数
        return true;
    }
}
```

**【代码解析】**

  * `n % i == 0`：这是判断整除的核心。
  * `return false`：一旦发现一个因子，立马返回，不需要再继续算了。

-----

### 9\. 视频：09\_找素数2 (进阶: 范围查找)

**【知识点文字解析】**

  * **业务逻辑**：找出 101-200 之间有多少个素数，并输出所有素数。
  * **编程考点**：**循环嵌套**。外层循环遍历 101-200 的每一个数，内层逻辑判断该数字是否为素数。
  * **优化**：可以直接调用上一个视频写的 `isPrime` 方法，让代码更清晰。

**【完整代码】**

```java
public class PrimeTest2 {
    public static void main(String[] args) {
        int count = 0; // 计数器

        // 1. 遍历区间
        for (int i = 101; i <= 200; i++) {
            
            // 2. 判断当前数字 i 是否为素数
            // (这里为了演示独立性，把判断逻辑内嵌写一遍，也可以直接调方法)
            boolean flag = true; // 标记位：默认是素数
            
            // 优化：其实只需要判断到 i的一半 甚至 开根号 即可，这里写 i/2
            for (int j = 2; j <= i / 2; j++) {
                if (i % j == 0) {
                    flag = false; // 破防了，不是素数
                    break; // 停止内层循环
                }
            }

            // 3. 根据标记位输出
            if (flag) {
                System.out.print(i + " ");
                count++;
            }
        }
        
        System.out.println("\n一共有：" + count + "个素数");
    }
}
```

**【代码解析】**

  * `for (int j = 2; j <= i / 2; j++)`：这是一个算法优化。判断 100 是否为素数，只需要试到 50 即可。如果 50 以前都除不尽，50 以后肯定也除不尽（除了它自己）。
  * `flag` 标记位：在每一轮外层循环开始时，都要重置为 `true`。

