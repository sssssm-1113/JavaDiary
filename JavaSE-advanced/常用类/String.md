###String类概述

1. String声明为final的
2. String实现了
   1. Serializable接口：表明字符串支持序列化
   2. Comparable接口 ：String可以比较大小
3. 内部定义了final char value[]用于存储字符串数据
4. String：代表不可变的字符序列（不可变性）：
   1. 对字符串重新赋值时，需要重写指定内存区域的赋值
   2. 对现有的字符串进行连接操作时，也需要重新指定内存区域赋值
   3. 调用String的replace()方法修改字符，也需要重新指定内存区域赋值
5. 字符串常量池是不会储存相同内容的字符串的





* String s = new String("abc")创建了两个对象：①堆空间中的②char[]对应的常量池中的数据："abc"

```java
@Test
    public void test(){
        String s1 = "java";
        String s2 = "ee";
        String ss = "javaee";
        String s3 = "java" + "ee";
        //s4,s5相当于在堆空间中new了一个新的对象
        String s4 = s1 + "ee";
        String s5 = "java" + s2;

        System.out.println(ss == s3);//true
        System.out.println(ss == s4);//false
        System.out.println(ss == s5);//false


    }
}
```

##### 结论

1. 常量与常量的拼接结果在常量池，且常量池中不会存在相同内容的常量
2. 只要有一个是变量，结果就在堆中
3. 如果拼接的结果调用intern()方法，返回值就在常量池中