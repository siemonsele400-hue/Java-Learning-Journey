Day 1 的复盘总结：
1. Java 的“铁三角”关系 (对应视频 02, 07, 08)
这是面试中最喜欢问的基础题，必须分清三者的从属关系：
 * JVM (Java Virtual Machine): 核心。它是 Java 跨平台的关键（翻译官）。Windows 有 Windows 版的 JVM，Mac 有 Mac 版的 JVM，但它们都能跑同一份 .class 文件。
 * JRE (Java Runtime Environment): 运行环境。如果你只运行 Java 程序，装这个就够了。
   * 公式： JRE = JVM + 核心类库
 * JDK (Java Development Kit): 开发工具包。你要写代码，必须装这个。
   * 公式： JDK = JRE + 开发工具 (javac, java, javadoc 等)
> 深度思考： 为什么装了 JDK 就不用装 JRE 了？因为 JDK 里包含了一个 JRE。
> 
2. 程序运行的“幕后黑手” (对应视频 03, 04, 06)
你学会了写 HelloWorld，但不仅要会写，还要懂它是怎么跑起来的：
 * 编写 (Coding): 生成 .java 文件（源文件，人看得懂）。
 * 编译 (Compile): 使用 javac.exe 命令。
   * 产物： 生成 .class 文件（字节码文件，机器看得懂，这是 Java 跨平台的载体）。
 * 运行 (Run): 使用 java.exe 命令。启动 JVM，加载字节码并执行。
> 深度思考： 为什么视频 03 要教你用 CMD (命令行)？
> 其实 IDEA 点击“运行”按钮时，底层就是在自动帮你执行 javac 和 java 命令。懂命令行，你才懂 IDE 到底为你做了什么。
> 
3. 环境变量的意义 (对应视频 09)
 * 现象： 不配环境变量，必须进入 JDK 的 bin 目录才能运行 java 命令。
 * 原理： 配置 JAVA_HOME 和 Path，是为了告诉操作系统：“如果在当前文件夹找不到命令，就去 Path 指定的路径里找”。
 * 现状： 虽然现在的 JDK 安装包会自动配置，但作为开发者，必须会手动配，因为以后配 Tomcat、Maven 都要用到这个原理。
4. 项目结构规范 (对应视频 10, 11)
在 IDEA 中，层级结构非常严格，不要乱建文件：
 * Project (项目) -> Module (模块) -> Package (包) -> Class (类)
 * 注意： 包名（Package）通常是公司域名倒写（例如 com.itheima.demo），这是为了防止类名冲突。
5. 变量与标识符 (对应视频 17-21)
 * 变量的三要素： 数据类型、变量名、值。
   * 代码： int age = 18;
   * 内存原理： 相当于在内存中开辟了一块小空间，起名叫 age，里面放了 18，且这就空间只能放整数。
 * 标识符命名规范 (大厂红线)：
   * 类名： 大驼峰命名 (BigCamelCase)，如 HelloWorld, StudentName。
   * 变量名/方法名： 小驼峰命名 (littleCamelCase)，如 age, studentName, getAge。
   * 切记： 严禁使用拼音（特别是拼音首字母，如 xsxm - 学生姓名），这是非常不专业的表现。
