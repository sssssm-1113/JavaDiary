### Map

##### Map：双列数据，存储key-value对的数据 

* HashMap：作为Map的主要实现类；线程不安全，效率高
  * LinkedHashMap：在遍历Map元素时，可以按添加顺序实现遍历
* TreeMap：按照添加的Key-value对进行排序，此时考虑key的自然或定制排序
* Hashtable：线程安全，效率低；不能存储null的key和value
  * Properties：常用来处理配置文件。key和value都是String型



HashMap底层：数组 + 链表					（jdk 7及之前）

​							数组 + 链表 + 红黑树	（jdk 8 ）

***

##### Map结构的理解：

Map中的Key：无序的、不可重复的，使用Set存储所有的key

> ​	key所在类要重写equals()  HashCode()    -----HashMap为例

Map中的Value：无序的、可重复的，使用Collection存储所有的value

> ​	value所在类要重写equals()

一个键值对：key-value 构成了一个Entry对象

Map中的entry：无序的、不可重复的，使用Set存储所有的entry

***

##### HashMap的底层实现原理:

***以 JDK 7 为例：***
HashMap map  = new HashMap();

实例化后，底层创建一个长度是16的一维数组Entry[] table。

map.put(key1,value1);

首先调用key1所在类的HashCode()计算key1哈希值，此哈希值经过算法计算后，得到Entry数组中的存放位置。

如果此位置上数据为空，添加成功
如果此位置上数据不为空，比较key1和已经存在的一个或多个数据的哈希值：

* 如果和已存在数据的哈希值都不同，添加成功
* 如果和已存在的数据(key2,value2)的哈希值相同，调用key1类所在的equals()方法，比较：
  * 返回false，添加成功
  * 返回true，使用value1替换value2

在不断添加过程中，涉及到扩容问题，当超出临界值（且要存放的位置非空），扩容，默认的扩容方式：扩容为原来的两倍，并将原有的数据复制过来

***以 JDK 8 为例***

1. new HashMap()  ：底层未创建一个长度为16的数组
2. jdk 8 底层数组是：Node[]
3. 首次调用put，底层创建一个长度是16的数组
4. jdk 8 底层结构：数组 + 链表 + 红黑树：当数组的某一个索引位置上的元素以链表形式存在的数据 > 8 且当前数组的长度 > 64时，此索引位置上的所有数据改为使用红黑树存储。

* 重要常量

  DEFAULT_INITIAL_CAPACITY : HashMap的默认容量，**16** 

  MAXIMUM_CAPACITY ： HashMap的最大支持容量，**2^30 **

  DEFAULT_LOAD_FACTOR：HashMap的默认加载因子 ，**0.75**

  TREEIFY_THRESHOLD：Bucket中链表长度大于该默认值，转化为红黑树,**8**

  UNTREEIFY_THRESHOLD：Bucket中红黑树存储的Node小于该默认值，转化为链表 

  MIN_TREEIFY_CAPACITY：桶中的Node被树化时最小的hash表容量。**64**（当桶中Node的 数量大到需要变红黑树时，若hash表容量小于MIN_TREEIFY_CAPACITY时，此时应执行 resize扩容操作这个MIN_TREEIFY_CAPACITY的值至少是TREEIFY_THRESHOLD的4 倍。） 

  table：存储元素的数组，总是2的n次幂 

  entrySet：存储具体元素的集 size：HashMap中存储的键值对的数量 

  modCount：HashMap扩容和结构改变的次数。 

  threshold：扩容的临界值，= 容量*填充因子 loadFactor：填充因子

***









##### HashMap和Hashtable的异同







##### CurrentHashMap与Hashtable的异同





