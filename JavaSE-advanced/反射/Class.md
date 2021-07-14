#### 关于java.lang.Class

1. 类的加载过程：

   经过javac.exe命令后，会生成一个或多个字节码文件（.class结尾），接着我们使用java.exe命令对某个字节码文件进行解释运行，相当于将某个字节码文件加载到内存中，此过程称为类的加载。

2. 加载到内存中的类，我们就称为运行时类，此运行时类就称为Class的一个实例

3. 加载到内存中的运行时类，会缓存一段时间，在此时间之内，可以通过不同方式来获取此运行时类

```Java
/*
获取Class实例的方式（掌握前三种）
 */
@Test
public void test() throws ClassNotFoundException {
    //1.调用运行时类的属性：.class
    Class<Person> clazz = Person.class;
    System.out.println(clazz);
    //2.通过运行时类的对象，调用getClass()
    Person person = new Person();
    Class<? extends Person> clazz2 = person.getClass();
    System.out.println(clazz2);
    //3.调用Class的静态方法：forName(String classPath)
    Class<?> clazz3 = Class.forName("TestClass.Person");
    System.out.println(clazz3);
	//4.使用类的加载器（了解）
    ClassLoader classLoader = ClassTest.class.getClassLoader();
    Class<?> clazz4 = classLoader.loadClass("TestClass.Person");
    System.out.println(clazz4);

    System.out.println(clazz == clazz2);//true
    System.out.println(clazz == clazz3);//true

}
```

4. Class实例可以是如下结构:

   （1）class： 外部类，成员(成员内部类，静态内部类)，局部内部类，匿名内部类 

   （2）interface：接口 

   （3）[]：数组 (只要数组的元素类型和维度一样，就是同一个Class)

   （4）enum：枚举 

   （5）annotation：注解@interface 

   （6）primitive type：基本数据类型 

   （7）void

   ```java
   Class c1 = Object.class;
   Class c2 = Comparable.class;
   Class c3 = String[].class;
   Class c4 = int[][].class;
   Class c5 = ElementType.class;
   Class c6 = Override.class;
   Class c7 = int.class;
   Class c8 = void.class;
   Class c9 = Class.class;
   
   ```

   