* String、StringBuffer、StringBuilder的异同：

String：不可变的字符序列；底层使用char[]存储

StringBuffer：可变的字符序列；线程安全的，效率偏低；底层使用char[]存储

StringBuilder：可变的字符序列；线程不安全的，效率高；底层使用char[]存储



```java
//new char[16]底层创建了一个长度为16的数组
StringBuffer sb1 = new StringBuffer();
```



* 扩容问题：如果要添加的数据底层数组放不下了，那就需要扩容底层的数组。默认情况下，扩容为原来容量的2倍 + 2，同时将原有数组的元素复制到新的数组中。

  开发中，建议使用*StringBuffer(int capacity)、StringBuilderr(int capacity)*



####StringBuffer常用方法

**StringBuffer** append(xxx)：提供了很多的append()方法，用于进行字符串拼接 

**StringBuffer** delete(int start,int end)：删除指定位置的内容 

**StringBuffer** replace(int start, int end, String str)：把[start,end)位置替换为str 

**StringBuffer** insert(int offset, xxx)：在指定位置插入xxx 

**StringBuffer** reverse() ：把当前字符序列逆转

**int**indexOf(String str) 

**String** substring(int start,int end) :返回一个从Start开始到End结束的左闭右开区间的子字符串

**int** length() 

**char** charAt(int n ) 

**void** setCharAt(int n ,char ch)