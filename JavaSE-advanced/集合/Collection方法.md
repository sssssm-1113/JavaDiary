### Collection接口的方法



向Collection接口的实现类的对象中添加数据obj时，要求obj所在类要重写equals()

```java
@Test
public void test1() {
    Collection coll = new ArrayList();
    //1.add(Object obj)
    coll.add("aa");
    coll.add("bb");
    coll.add(123);
    coll.add(new Date());

    //2.size()
    System.out.println(coll.size());

    //3.addAll()
    Collection coll1 = new ArrayList();
    coll1.add(123);
    coll1.add("cc");
    coll.addAll(coll1);

    //4.isEmpty()
}
```

```java
public void test2(){
    Collection coll = new ArrayList();
    coll.add("aa");
    coll.add("bb");
    coll.add(123);
    coll.add(new Date());
    coll.add(false);
    coll.add(new Person("tom",11));


    //5.contains(Object obj)  判断集合中是否包含obj,
    //判断时会调用obj对象所在类的equals()
    boolean contains = coll.contains(new Person("tom",11));
    System.out.println(contains);

    //6.containsAll(Collections coll1)
    //判断形参coll1中所有元素是否都存在于当前集合中
    Collection coll1 = Arrays.asList(123,"bb");
    System.out.println(coll.containsAll(coll1));

    //7.remove(obj)
    coll.remove(123);
    
    //8.removeAll(Collection coll2)  差集
    Collection coll2 = Arrays.asList("aa","bb");
    coll.removeAll(coll2);
    System.out.println(coll);

}
```

```java
public void test3(){
    Collection coll = new ArrayList();
    coll.add("aa");
    coll.add("bb");
    coll.add(123);
    coll.add(new Date());
    coll.add(false);
    coll.add(new Person("tom",11));

    //9.retainAll(Collection coll1) （交）
    Collection coll1 = Arrays.asList(123,"bb","aa");
    coll.retainAll(coll1);
    System.out.println(coll);

    //10.equals（obj)判断当前集合和形参集合相同
    
	//11.hashCode()
    
    //12.toArray()集合 --->数组
    Object[] objects = coll.toArray();
        for (int i = 0; i < objects.length; i++) {
            System.out.println(objects[i]);
        }
    
    //数组--->集合:调用Arrays类的静态方法
    List<String> list = Arrays.asList(new String[]{"aa","bb","cc"});
    
    
}
```