#### 注解（Annotation）

* Annotation 其实就是代码里的特殊标记, 这些标记可以在编译, 类加 载, 运行时被读取, 并执行相应的处理。通过使用 Annotation, 程序员可以在不改变原有逻辑的情况下, 在源文件中嵌入一些补充信息。代码分析工具、开发工具和部署工具可以通过这些补充信息进行验证 或者进行部署。
* 在JavaSE中，注解的使用目的比较简单，例如标记过时的功能， 忽略警告等。在JavaEE/Android中注解占据了更重要的角色，例如 用来配置应用程序的任何切面，代替JavaEE旧版中所遗留的繁冗 代码和XML配置等。



如何自定义注解？：参照@SuppressWarnings定义

1. 注解声明为@interface
2. 内部定义成员，通常使用value表示
3. 可以指定成员的默认值，使用default定义
4. 如果自定义注解没有成员，表明是一个标识作用

* 自定义注解必须配上注解的信息处理流程（使用反射）才有意义
* 自定义注解通常都会指明两个元注解：Retention、Target

*注：Annotation 的成员变量在 Annotation 定义中以无参数方法的形式来声明。其方法名和返回值定义了该成员的名字和类型。我们称为配置参数。类型只能是八种基本数据类型、String类型、Class类型、enum类型、Annotation类型、 以上所有类型的数组。*

***

#### JDK提供的元注解：对现有的注解进行解释说明的注解

***<font color="red">@Retention</font>***: 只能用于修饰一个 Annotation 定义, 用于指定该 Annotation 的生命周期, @Rentention 包含一个 RetentionPolicy 类型的成员变量, 使用 @Rentention 时必须为该 value 成员变量指定值: 

* RetentionPolicy.SOURCE:在源文件中有效（即源文件保留），编译器直接丢弃这种策略的注释 
* RetentionPolicy.CLASS:在class文件中有效（即class保留） ， 当运行Java 程序时, JVM 不会保留注解。 这是默认值 
* RetentionPolicy.RUNTIME:在运行时有效（即运行时保留），当运行 Java 程序时, JVM 会 保留注释。程序可以通过反射获取该注释。

***<font color="red">@Target</font>***: 用于修饰 Annotation 定义, 用于指定被修饰的 Annotation 能用于 修饰哪些程序元素。 @Target 也包含一个名为 value 的成员变量。

***

#### jdk 8 中注解的新特性：可重复注解、类型注解

