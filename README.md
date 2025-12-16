# 🚀 Java 基础学习路线与笔记 (Java Basic Learning Path)

## 📂 目录 (Table of Contents)

### [Day 01：Java 开发环境搭建与 Hello World]([./Day01-Env](https://github.com/siemonsele400-hue/myjavaseproject/blob/master/day01-helloword-code/src/com/itheima/hello/HelloWorld.java))
- **核心目标**：完成 Java 开发环境搭建，理解程序运行机制。
- **关键知识点**：JDK 安装、环境变量、命令行操作、HelloWorld、关键字与标识符。

### [Day 02：Java 基础语法：数据类型与运算符](./Day02)
- **核心目标**：掌握数据在计算机中的处理方式及基础运算逻辑。
- **关键知识点**：
    - 数据存储：二进制、八进制、十六进制。
    - 类型处理：8种基本数据类型、自动/强制类型转换。
    - 逻辑运算：自增自减、逻辑与/或、三元运算符。
    - 交互编程：Scanner 键盘录入。

### [Day 03: 程序流程控制 (Flow Control)](https://www.google.com/search?q=https://github.com/siemonsele400-hue/Java-Learning-Journey/tree/main/day03-flow-control)

  * **核心目标**：掌握程序的逻辑控制，能够让程序根据条件执行不同的代码块。
  * **关键知识点**：
      * **分支结构**：`if-else` 判断、`switch-case` 穿透性与新特性。
      * **循环结构**：`for` 循环（固定次数）、`while` 循环（未知次数）、`do-while` 区别。
      * **控制跳转**：`break`（跳出）、`continue`（跳过本次）、无限循环写法。
      * **随机数**：`Random` 类的使用场景（猜数字游戏）。

### [Day 04: 数组 (Arrays)](https://www.google.com/search?q=https://github.com/siemonsele400-hue/Java-Learning-Journey/tree/main/day04-array)

  * **核心目标**：掌握如何在内存中存储一组相同类型的数据，并理解引用类型的内存模型。
  * **关键知识点**：
      * **定义与初始化**：静态初始化 `int[] arr = {1,2}` vs 动态初始化 `new int[3]`。
      * **核心操作**：索引访问、数组长度 `length`、遍历数组、最大值/最小值获取。
      * **内存机制**：栈内存 (Stack) vs 堆内存 (Heap)，两个数组指向同一个空间的内存图解。
      * **常见异常**：索引越界 `ArrayIndexOutOfBoundsException`、空指针 `NullPointerException`。

### [Day 05: 方法 (Methods)](https://www.google.com/search?q=https://github.com/siemonsele400-hue/Java-Learning-Journey/tree/main/day05-method)

  * **核心目标**：学习代码的模块化设计，提高代码的复用性。
  * **关键知识点**：
      * **方法定义**：修饰符、返回值类型、方法名、参数列表。
      * **调用机制**：形参 (Parameter) 与实参 (Argument) 的关系，值传递原理。
      * **方法重载 (Overload)**：同名不同参（参数个数、类型、顺序不同）。
      * **return 关键字**：返回结果与结束方法的双重作用。

### [Day 06: 编程思维训练 (Programming Logic Case)](https://www.google.com/search?q=https://github.com/siemonsele400-hue/Java-Learning-Journey/tree/main/day06-practice)

  * **核心目标**：综合运用前五天的基础语法，解决实际算法逻辑问题。
  * **关键知识点**：
      * **数据交换**：不借助第三个变量交换数值。
      * **数组翻转**：双指针思想。
      * **经典案例**：买飞机票价格计算、找质数、开发验证码、评委打分（去掉最高/最低分）、数组拷贝。

### [Day 07: 面向对象基础 (Object-Oriented Programming - Basics)](https://www.google.com/search?q=https://github.com/siemonsele400-hue/Java-Learning-Journey/tree/main/day07-oop)

  * **核心目标**：从“面向过程”转向“面向对象”，理解类与对象的关系。
  * **关键知识点**：
      * **类与对象**：类是图纸，对象是实体。
      * **封装性 (Encapsulation)**：`private` 关键字、Getter/Setter 方法。
      * **this 关键字**：解决局部变量与成员变量重名问题。
      * **构造器 (Constructor)**：无参构造与全参构造的作用。
      * **JavaBean**：标准实体类的编写规范。

### [Day 08: String 类与 ArrayList 集合](https://www.google.com/search?q=https://github.com/siemonsele400-hue/Java-Learning-Journey/tree/main/day08-api-collection)

  * **核心目标**：掌握 Java 中最常用的字符串操作以及动态数组容器。
  * **关键知识点**：
      * **String 类**：字符串的不可变性、常量池原理、`new String` vs 直接赋值。
      * **常用 API**：`equals()` 比较内容、`substring()` 截取、`replace()` 替换、`split()` 分割。
      * **ArrayList**：集合的特点（大小可变）、泛型 `<E>` 的使用、增删改查 API。
      * **应用案例**：学生信息管理系统（基础版）。

### [Day 09: 综合项目 - ATM 系统](https://www.google.com/search?q=https://github.com/siemonsele400-hue/Java-Learning-Journey/tree/main/day09-atm-system)

  * **核心目标**：独立完成一个具备完整业务逻辑的纯 Java 控制台项目。
  * **关键知识点**：
      * **架构设计**：Account（数据类）、ATM（业务类）、Test（启动类）的分离。
      * **业务逻辑**：开户（查重）、登录（认证）、转账（逻辑判断）、取款（余额检查）。
      * **综合运用**：面向对象思想 + ArrayList 集合存储 + String 校验 + 流程控制。

-----

**小建议：**
如果你在 GitHub 上已经建好了对应的文件夹（比如 `day03-flow-control`），可以在 README 里把标题做成**超链接**（就像我上面代码里写的那样 `[标题](链接)`），这样点击目录就能直接跳转到你那一天的代码文件夹，显得非常专业！
