### 第一板块：方法的定义与基本用法


方法就是一段具有独立功能的代码块，不调用就不执行。

  * **核心格式**：
    ```java
    public static 返回值类型 方法名(参数列表) {
        方法体;
        return 返回值;
    }
    ```
  * **void 与 return**：
      * 如果方法执行完需要给调用者一个结果，定义具体的**返回值类型**（如 `int`, `boolean`），必须写 `return`。
      * 如果方法只是做个操作（比如打印一句话），返回值类型写 **`void`**，可以不写 `return`（或者只写 `return;` 表示结束）。

**代码案例 (求和与判断奇偶)：**

```java
public class MethodDemo {
    public static void main(String[] args) {
        // 调用带返回值的方法
        int sum = getSum(100); // 求 1-100 的和
        System.out.println("1-100的和是：" + sum);

        // 调用判断奇偶的方法
        checkNumber(15);
    }

    // --- 案例 1：求 1-n 的和 (带返回值) ---
    public static int getSum(int n) {
        int sum = 0;
        for (int i = 1; i <= n; i++) {
            sum += i;
        }
        return sum; // 把计算结果返回给 main 方法
    }

    // --- 案例 2：判断奇偶 (无返回值 void) ---
    public static void checkNumber(int num) {
        if (num % 2 == 0) {
            System.out.println(num + " 是偶数");
        } else {
            System.out.println(num + " 是奇数");
        }
        // 这里不需要 return 具体值，因为是 void
    }
}
```

-----

### 第二板块：方法重载 (Overload)

**对应文件：11**

这是一个高频面试题，也是 Java 灵活性的体现。

  * **概念**：在同一个类中，**方法名相同**，但**参数列表不同**（个数不同、类型不同、顺序不同），与返回值无关。
  * **作用**：比如“射击”这个动作，既可以是“单发射击”，也可以是“连发射击”，方法名都叫 `fire`，根据给的子弹数量不同自动选择逻辑。

**代码案例：**

```java
public class OverloadDemo {
    public static void main(String[] args) {
        compare(10, 20);       // 自动调用两个 int 的
        compare(10.5, 20.5);   // 自动调用两个 double 的
    }

    // 比较两个 int
    public static void compare(int a, int b) {
        System.out.println("正在比较两个整数：" + (a == b));
    }

    // 比较两个 double (方法名相同，参数类型不同 -> 重载成功)
    public static void compare(double a, double b) {
        System.out.println("正在比较两个小数：" + (a == b));
    }
    
    // public static int compare(int a, int b) { } // 报错！重载与返回值无关，只看参数
}
```

-----

### 第三板块：方法的内存原理与参数传递 (重难点)

**对应文件：06, 07, 08**

这是很多初学者容易混淆的地方：**Java 中的参数传递，永远是“值传递”**。

1.  **基本数据类型 (int, double等)**：传递的是数据的**具体数值**。方法里改了，**不影响**外面的变量。
2.  **引用数据类型 (数组, 对象)**：传递的是**内存地址**。方法里通过地址找到了堆内存中的数据并修改，外面的变量**会受影响**。

**代码案例 (基本类型 vs 引用类型)：**

```java
public class ParamPassDemo {
    public static void main(String[] args) {
        int a = 10;
        int[] arr = {10, 20};

        change(a, arr);

        System.out.println("a = " + a);       // 输出 10 (没变！)
        System.out.println("arr[1] = " + arr[1]); // 输出 200 (变了！)
    }

    public static void change(int number, int[] array) {
        // 1. 修改基本类型：只改了 change 方法栈帧里的 number，没改 main 里的 a
        number = 200; 
        
        // 2. 修改引用类型：array 存的是地址，顺着地址找到了堆内存里的数组，把它改了
        array[1] = 200; 
    }
}
```

-----

### 第四板块：方法与数组的综合应用

**对应文件：09, 10**

实际开发中，我们经常把数组作为参数传给方法。

  * **常见练习**：遍历打印数组、比较两个数组是否相同、查找数组最大值。

**代码案例 (比较两个数组内容是否一样)：**

```java
public class ArrayMethodTest {
    public static void main(String[] args) {
        int[] arr1 = {1, 2, 3};
        int[] arr2 = {1, 2, 3};
        
        boolean isSame = compareArrays(arr1, arr2);
        System.out.println("两个数组内容是否一致：" + isSame);
    }

    public static boolean compareArrays(int[] arr1, int[] arr2) {
        // 1. 先判断长度，长度不一样直接 false
        if (arr1.length != arr2.length) {
            return false;
        }

        // 2. 遍历内容，只要有一个位置不一样，直接 false
        for (int i = 0; i < arr1.length; i++) {
            if (arr1[i] != arr2[i]) {
                return false; // 发现不一样的瞬间，方法结束
            }
        }

        // 3. 全比完了还没死，说明完全一样
        return true;
    }
}
```
