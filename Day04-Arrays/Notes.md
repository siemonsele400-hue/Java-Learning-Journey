Day 04 数组 (Arrays)。  
数组是编程中用来存储数据的第一个复杂数据结构，也是后续学习集合（Collection）和算法的基础。  
第一板块：数组的定义与初始化  
数组是一个容器，用来存储同种数据类型的多个值。在 Java 中，数组一旦创建，长度是固定的。  
 * 静态初始化 vs 动态初始化
 * 静态初始化：知道具体要存哪些数据时使用。
 * 动态初始化：只知道要存多少个数据，不知道具体值时使用（系统会分配默认值，如 int 默认为 0，boolean 默认为 false）。  
代码案例：
```java
public class ArrayInitDemo {
    public static void main(String[] args) {
        // 1. 静态初始化 (标准格式：数据类型[] 数组名 = new 数据类型[]{元素1, 元素2...})
        // 简化写法（最常用）：
        int[] ages = {18, 25, 30, 45}; 
        
        // 2. 动态初始化 (格式：数据类型[] 数组名 = new 数据类型[长度])
        // 创建一个长度为 3 的 double 数组，默认值都是 0.0
        double[] scores = new double[3];
        
        // 赋值
        scores[0] = 99.5;
        
        System.out.println("静态数组长度：" + ages.length);
        System.out.println("动态数组第一个元素：" + scores[0]);
    }
}
```
第二板块：Java 内存分配与引用原理 (重点难点)  
这是很多初学者容易晕的地方。理解了内存，你就理解了“引用类型”。  
 * 栈内存 (Stack)：方法运行时进入栈中，变量（如 arr）在这里存储。
 * 堆内存 (Heap)：new 出来的东西（如数组实体、对象）都在这里。堆内存中的数据有内存地址。
 * 引用：数组变量 arr 存储的其实不是具体的数字，而是堆内存中的地址（例如 [I@1b6d3586）。
关键点：多个变量指向同一个数组  
如果 int[] arr2 = arr1;，那么修改 arr2 的数据，arr1 也会变，因为它们拿的是同一把“钥匙”（地址）。  
代码案例：
```java
public class ArrayMemoryDemo {
    public static void main(String[] args) {
        int[] arr1 = {10, 20};
        
        // arr2 获得了 arr1 的地址，现在两人指向同一个堆内存空间
        int[] arr2 = arr1; 
        
        // 修改 arr2
        arr2[0] = 999;
        
        // 打印 arr1，发现也被改了！
        System.out.println("arr1[0]的值是：" + arr1[0]); // 输出 999
    }
}
```
第三板块：数组的通用操作 (遍历与最值)  
这是实际开发中最常用的技能。  
 * 访问：使用索引 arr[index]，注意索引从 0 开始。
 * 遍历：使用 for 循环配合 arr.length。
 * 求最值：打擂台思想。假设第一个是擂主（最大值），后面的人依次上来比武，赢了的当新擂主。  
代码案例 (综合练习)：
```java
public class ArrayStatsDemo {
    public static void main(String[] args) {
        int[] data = {15, 90, 33, 10, 55};
        
        // --- 1. 数组遍历 ---
        System.out.println("数组中的数据有：");
        for (int i = 0; i < data.length; i++) {
            System.out.print(data[i] + " ");
        }
        System.out.println(); // 换行
        
        // --- 2. 求最大值 ---
        // 建议：参照物取数组的第一个元素，而不是 0（防止数组全是负数）
        int max = data[0]; 
        
        for (int i = 1; i < data.length; i++) { // 从第二个开始比
            if (data[i] > max) {
                max = data[i]; // 记录更大的值
            }
        }
        System.out.println("最大值是：" + max);
    }
}
```
第四板块：高级算法 (交换与随机排名)  
这两个文件涉及了数组元素的位置变动。  
 * 交换 (Swap)：通过一个临时变量 temp 实现两个位置数据的互换。（就像交换两杯水，需要第三个空杯子）。
 * 随机排名 (Shuffle)：利用 Random 类生成随机索引，将当前元素与随机位置的元素进行交换。  
代码案例 (随机打乱数组)：
```java
import java.util.Random;

public class RandomRankDemo {
    public static void main(String[] args) {
        // 假设这是 5 个员工的工号
        int[] codes = {1, 2, 3, 4, 5};
        Random r = new Random();
        
        // 遍历数组，每到一个位置，都随机找个人跟它换位置
        for (int i = 0; i < codes.length; i++) {
            // 生成一个随机索引 (范围 0 到 codes.length - 1)
            int randomIndex = r.nextInt(codes.length);
            
            // --- 核心：三方变量交换法 ---
            int temp = codes[i];        // 1. 把当前数据存入临时杯子
            codes[i] = codes[randomIndex]; // 2. 把随机位置的数据给当前位置
            codes[randomIndex] = temp;  // 3. 把临时杯子的数据给随机位置
        }
        
        // 打印结果
        System.out.print("随机排名后的顺序：");
        for (int i = 0; i < codes.length; i++) {
            System.out.print(codes[i] + " ");
        }
    }
}
```
还有一个小细节：Debug  
最后提到了 Debug。这是程序员的“听诊器”。  
 * 知识点：学会打断点（BreakPoint），一步步（Step Over）查看变量在内存中是如何变化的。
 * 建议：对于数组下标越界（ArrayIndexOutOfBoundsException）或者逻辑错误（例如最大值求错了），Debug 是最高效的排错方式。  
💡 总结与下一步  
Day 04 的课程非常关键，数组是引用的起点，也是算法的起点。下一步的重点应该是：  
 * 默写：能够熟练手写数组的静态/动态初始化。
 * 理解内存：脑海中要有一张图，分得清 Stack 里的变量和 Heap 里的数组实体。
 * 掌握套路：求最大值、数组反转（交换）的代码逻辑要烂熟于心。
