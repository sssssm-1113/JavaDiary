集合元素的遍历操作，使用迭代器Iterator接口

1. 内部的方法：hasNext()    next()
2. 集合对象每次调用iterator()方法都得到一个全新的迭代器对象，默认游标在集合的第一个元素之前
3. 内部定义了remove()，可以在遍历时，删除集合中的元素，不同于集合直接调用remove()

```java
@Test
public void test(){
    Collection coll = new ArrayList();
    coll.add("aa");
    coll.add("bb");
    coll.add(123);
    coll.add(new Date());
    coll.add(false);
    coll.add(new Person("tom",11));
    //遍历操作
    Iterator iterator = coll.iterator();
    
    while(iterator.hasNext()){//判断是否还有下一个元素
        System.out.println(iterator.next());//指针下移并返回下移后集合位置上的元素
    }
}
```



jdk 5.0 新增了foreach循环，用于遍历集合，数组

```Java
@Test
public void test(){
    Collection coll = new ArrayList();
    coll.add("aa");
    coll.add("bb");
    coll.add(123);
    coll.add(new Date());
    coll.add(false);
    coll.add(new Person("tom",11));
    //for(集合元素的类型  局部变量 : 集合对象)
    for (Object obj : coll) {
        System.out.println(obj);
    }
```