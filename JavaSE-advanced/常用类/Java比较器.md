####Comparable接口的使用：自然排序

1. String、包装类等实现了Comparable接口，重写了compareTo()方法，给出了比较两个对象大小的方法
2. 重写compareTo(obj)的规则：
   1. 如果当前对象this大于形参对象obj，则返回正整数，
   2. 如果当前对象this小于形参对象obj，则返回负整数，
   3. 如果当前对象this等于形参对象obj，则返回零。
3. 对于自定义类来说，如果需要排序，我们可以让自定义类实现Comparable接口，重写compareTo(obj)，在方法中指明如何排序

```Java
public class Goods implements Comparable{
    private String name;
    private double price;

    //指明商品比较大小的方式:按价格从低到高排序
    @Override
    public int compareTo(Object o) {
        if (o instanceof Goods) {
            //方式一
            Goods goods = (Goods) o;
            if (this.price > goods.price) {
                return 1;
            } else if (this.price < goods.price) {
                return -1;
            } else {
                return 0;
                //再按商品名称从低到高排
                //return  this.name.compareTo(goods.name);
            }
            //方式二
            //return Double.compare(this.price,goods.price);
        }
        throw new RuntimeException("数据类型不一致");

    }
```



####Comparator接口的使用：定制排序

1. 当元素的类型没有实现java.lang.Comparable接口而又不方便修改代码，或者实现了java.lang.Comparable接口的排序规则不适合当前的操作，那么可以考虑使用Comparator的对象来排序

2. 重写compare(Object o1,Object o2)方法，比较o1和o2的大小：

   如果方法返回正整数，则表示o1大于o2；

   如果返回0，表示相等；

   返回负整数，表示 o1小于o2。

```Java
@Test
public void test4(){
    Goods[] arr = new Goods[5];
    arr[0] = new Goods("lenovo",500);
    arr[1] = new Goods("dell",1000);
    arr[2] = new Goods("alienware",10000);
    arr[3] = new Goods("asus",500);
    arr[4] = new Goods("asus",600);

    Arrays.sort(arr, new Comparator<Goods>() {
        //按产品名称从低到高排序，再按价格从低到高排序
        @Override
        public int compare(Goods o1, Goods o2) {
            if(o1.getName().equals(o2.getName())){
                return Double.compare(o1.getPrice(),o2.getPrice());

            }else {
                return o1.getName().compareTo(o2.getName());
            }
        }
    });
    System.out.println(Arrays.toString(arr));
}
```



***

##### Comparable接口与Comparator接口的对比

* Comparable接口的方式一旦确定，保证Comparable接口实现类的对象在任何位置都可以比较大小
* Comparator接口属于临时性的比较