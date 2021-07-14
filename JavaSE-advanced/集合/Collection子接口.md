#### List接口

* ArrayList   LinkedList   Vector三者的异同
  * 同：存储有序的、可重复的数据
  * 异：
    * ArrayList：作为List接口的主要实现类；线程不安全，效率高；底层使用Object[] elementData存储
    * LinkedList：对于频繁地插入、删除操作，此类效率比ArrayList 高；底层使用双向链表存储
    * Vector：古老实现类；线程安全，效率低；底层使用Object[] elementData存储

* ArrayList：
  * JDK1.7：ArrayList像饿汉式，直接创建一个初始容量为10的数组 
  * JDK1.8：ArrayList像懒汉式，一开始创建一个长度为0的数组，当添加第一个元素时再创建一个始容量为10的数组
  * Arrays.asList(…) 方法返回的 List 集合，既不是 ArrayList 实例，也不是 Vector 实例。 Arrays.asList(…) 返回值是一个固定长度的 List 集合
* LinkedList:
  * 双向链表，内部没有声明数组，而是定义了Node类型的first和last， 用于记录首末元素。同时，定义内部类Node，作为LinkedList中保存数据的基 本结构。Node除了保存数据，还定义了两个变量：
    * prev变量记录前一个元素的位置
    * next变量记录下一个元素的位置



##### List接口的常用方法

void *add*(int index, Object ele):在index位置插入ele元素 

boolean *addAll*(int index, Collection eles):从index位置开始将eles中 的所有元素添加进来 

Object *get*(int index):获取指定index位置的元素 

int *indexOf*(Object obj):返回obj在集合中首次出现的位置 

int *lastIndexOf*(Object obj):返回obj在当前集合中末次出现的位置 

Object *remove*(int index):移除指定index位置的元素，并返回此元素 

Object *set*(int index, Object ele):设置指定index位置的元素为ele 

List *subList*(int fromIndex, int toIndex):返回从fromIndex到toIndex 位置的子集合

***

#### Set接口

* Set接口是Collection的子接口，set接口没有提供额外的方法
* Set 集合不允许包含相同的元素，如果试把两个相同的元素加入同一个 Set 集合中，则添加操作失败。
* Set 判断两个对象是否相同不是使用 == 运算符，而是根据 equals() 方法
* Set中没有额外定义新的方法，使用的都是Collection中声明过的方法



##### HashSet

* HashSet：作为Set接口的主要实现类；线程不安全；可以存储Null值
  * LinkedHashSet：作为HashSet的子类；遍历内部数据时，可以按照添加的顺序遍历
* TreeSet：可以按照添加对象的指定属性，进行排序
* HashSet底层采用数组+链表的方式存储



一、Set：存储无序的、不可重复的数据

1. 无序性：不等于随机性；存储的数据在底层数组中并非按照数组索引的顺序添加，而是
   根据数据的哈希值确定
2. 不可重复性：保证添加的元素按照equals()判断时，不能返回true

二、添加元素的过程：以HashSet为例

​	向HashSet中添加元素a，首先调用元素a所在类的HashCode()方法，计算a的哈希值，此哈希值通过某种算法计算出在HashSet底层数组中的存放位置，判断数组此位置上是否已有元素：

​	如果没有，a添加成功；

​	如果有其他元素b(或以链表形式存在的多个元素)，则比较元素a与元素b的hash值 ：

​			如果hash值不同，a添加成功，

​			如果hash值相同，进而调用a所在类的equals()方法：

​					equals()返回true，添加失败

​					equals()返回false，添加成功	

***对于添加成功的后两个情况而言：元素a与已存在索引位置上的数据以链表方式存储***

***jdk 7：a放入数组，指向原元素***

***jdk 8：原元素在数组中，指向元素a***																													

要求：

1. 对于存放在Set容器中的对象，对应的类一定要重写equals()和hashCode(Object obj)方法，以实现对象相等规则。
2. 重写的hashCode()和equals()尽可能保持一致性。即：“相等的对象必须具有相等的散列码”。



##### LinkedHashSet

LinkedHashSet作为HashSet的子类，在添加数据的同时，每个数据还维护了两个引用，记录此数据前后的数据

* 优点：对于频繁的遍历，效率高一些



##### TreeSet

1. 向TreeSet中添加的数据，要求是相同类的对象
2. 两种排序方式：自然排序(实现Comparable)、定义排序(Comparator)
3. 自然排序中，比较两个对象是否相同的标准为：compareTo() 返回0，不再是equals()
4. 定制排序中，比较两个对象是否相同的标准为：compare() 返回0，不再是equals()

```java
@Test
public void test1(){
    //定制排序
    Comparator com = new Comparator() {
        @Override
        //按年龄从小到大,然后按姓名首字母排序
        public int compare(Object o1, Object o2) {
            if (o1 instanceof Person && o2 instanceof Person) {
                Person p1 = (Person) o1;
                Person p2 = (Person) o2;
                int compare = Integer.compare(p1.getAge(), p2.getAge());
                if (compare != 0){
                    return compare;
                }else {
                    return  p1.getName().compareTo(p2.getName());
                }

            }else {
                throw new RuntimeException("---");
            }
        }

    };
    TreeSet set = new TreeSet(com);//此时按照定制排序的方法进行排序
    set.add(new Person("tom",12));
    set.add(new Person("ham",21));
    set.add(new Person("mike",50));
    set.add(new Person("jack",21));
    set.add(new Person("jack",7));

    for (Object obj :
            set) {
        System.out.println(obj);
    }
}
```

