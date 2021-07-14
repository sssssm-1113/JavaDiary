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

##### Map接口的常用方法

* 添加、删除、修改操作：
  * Object *put*(Object key,Object value)：将指定key-value添加到(或修改)当前map对象中
  * void *putAll*(Map m):将m中的所有key-value对存放到当前map中
  * Object *remove*(Object key)：移除指定key的key-value对，并返回value
  * void *clear*()：清空当前map中的所有数据
* 元素查询的操作：
  * Object *get*(Object key)：获取指定key对应的value
  * boolean *containsKey*(Object key)：是否包含指定的key 
  * boolean *containsValue*(Object value)：是否包含指定的value 
  * int *size*()：返回map中key-value对的个数 
  * boolean *isEmpty*()：判断当前map是否为空 
  * boolean *equals*(Object obj)：判断当前map和参数对象obj是否相等
* 元视图操作的方法：
  * Set *keySet*()：返回所有key构成的Set集合 
  * Collection *values*()：返回所有value构成的Collection集合 
  * Set *entrySet*()：返回所有key-value对构成的Set集合