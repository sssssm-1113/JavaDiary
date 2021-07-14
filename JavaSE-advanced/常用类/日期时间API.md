####1.java.lang.System类 

* System类提供的public static long currentTimeMillis()用来返回当前时 间与1970年1月1日0时0分0秒之间以毫秒为单位的时间差。
  
#### 2.java.util.Date类:

java,.util.Date(java.sql.Date:对用着数据库中的日期类型的变量)

1. 构造器

   * Date()：使用无参构造器创建的对象可以获取本地当前时间
   * Date(long date)

2. 常用方法

   * getTime():返回自 1970 年 1 月 1 日 00:00:00 GMT 以来此 Date 对象 表示的毫秒数。
   * toString():把此 Date 对象转换为以下形式的 String： dow mon dd hh:mm:ss zzz yyyy 其中： dow 是一周中的某一天 (Sun, Mon, Tue, Wed, Thu, Fri, Sat)，zzz是时间标准。

   ####3.java.sql.Date：

   ```java
   //1.如何实例化
   java.sql.Date date = new java.sql.Date(1605498263395L);
   System.out.println(date);//2020-11-16
   //2.如何将java.util.Date对象转换为java.sql.Date对象
   Date date2 = new Date();
   java.sql.Date date3 = new java.sql.Date(date2.getTime());
   ```

   

   ***

   ####4.SimpleDateFormat类

   ```java
   public class DateTimeTest {
       /*
       SimpleDateFormat的使用：对日期Date类的格式化和解析
       1.两个操作：
       1.1格式化：日期--->字符串
       1.2解析：格式化的逆过程，字符串--->日期
   
       2.SimpleDateFormat的实例化
        */
       @Test
       public void SimpleDateFormat() throws ParseException {
           //实例化SimpleDateFormat：默认的构造器
           SimpleDateFormat sdf = new SimpleDateFormat();
           //格式化：日期-->字符串
           Date date = new Date();
           System.out.println(date);
           String format = sdf.format(date);
           System.out.println(format);
           //解析：字符串--->日期
           String str = "20-12-30 上午5:22";
           Date parse = sdf.parse(str);
           System.out.println(parse);
   
           //实例化SimpleDateFormat：自定义的构造器
           SimpleDateFormat simpleDateFormat = new SimpleDateFormat("YYYY-MM-dd  hh:mm:ss");
           //格式化
           String str2 = simpleDateFormat.format(date);
           System.out.println(str2);
           //解析:字符串必须符合识别的格式（看构造器）
           Date parse1 = simpleDateFormat.parse(str2);
           System.out.println(parse1);
   
   
       }
   
   }
   ```

   ***


####3.Calendar类

```java
public class TimeTest2 {
    /*
    Calendar日历类（抽象类）的使用：
    1.使用Calendar.getInstance()方法
    2.调用它的子类GregorianCalendar的构造器
     */
    @Test
    public void testCalendar(){
        Calendar calendar = Calendar.getInstance();
        //常用方法
        //get()
        int days = calendar.get(Calendar.DAY_OF_MONTH);
        System.out.println(days);
        System.out.println(calendar.get(Calendar.DAY_OF_WEEK));
        //set()
        calendar.set(Calendar.DAY_OF_MONTH,20);
        System.out.println(calendar.get(Calendar.DAY_OF_MONTH));
        //add()
        calendar.add(Calendar.DAY_OF_MONTH,3);
        System.out.println(calendar.get(Calendar.DAY_OF_MONTH));
        //getTime()日历类--->Date
        Date time = calendar.getTime();
        System.out.println(time);
        //setTime()Date--->日历类
        Date date = new Date();
        calendar.setTime(date);
        System.out.println(calendar.get(Calendar.DAY_OF_MONTH));

    }
}
```

***

####4.LocalDate、LocalTime、LocalDateTime 类

这是其中较重要的几个类，它们的实例是不可变的对象，分别表示使用 ISO-8601日历系统的日期、时间、日期和时间。 它们提供了简单的本地日期或时间，并不包含当前的时间信息，也不包含与时区 相关的信息

* LocalDate代表IOS格式（yyyy-MM-dd）的日期,可以存储 生日、纪念日等日期。 
* LocalTime表示一个时间，而不是日期。
*  LocalDateTime是用来表示日期和时间的，这是一个最常用的类之一。

```java
public void test (){
        //now()：获取当前日期、时间
        LocalDate localDate = LocalDate.now();
        LocalTime localTime = LocalTime.now();
        LocalDateTime localDateTime = LocalDateTime.now();

        System.out.println(localDate);
        System.out.println(localTime);
        System.out.println(localDateTime);

        //of()：设置指定的时间，无偏移量
        LocalDateTime localDateTime1 = LocalDateTime.of(2020, 10, 6, 8, 0);
        System.out.println(localDateTime1);

        //getXxx()
        System.out.println(localDateTime.getDayOfMonth());
        System.out.println(localDateTime.getDayOfWeek());
        System.out.println(localDateTime.getDayOfYear());
        System.out.println(localDateTime.getMinute());

        //不可变性
        //withXxx()：设置相关属性
        LocalDateTime localDateTime2 = localDateTime.withDayOfMonth(22);
        System.out.println(localDateTime);
        System.out.println(localDateTime2);

        LocalDateTime localDateTime3 = localDateTime.withHour(4);
        System.out.println(localDateTime);
        System.out.println(localDateTime3);
        System.out.println("********************");
        //plusXxx()/minusXxx():
        LocalDate localDate1 = localDate.plusDays(8);
        System.out.println(localDate);
        System.out.println(localDate1);

        LocalDate localDate2 = localDate.minusMonths(3);
        System.out.println(localDate);
        System.out.println(localDate2);
    }
```



***

####5.Instant类



```java
public void test(){
        //now():获取格林威治时间
        Instant instant = Instant.now();
        System.out.println(instant);
        //添加时间偏移量
        OffsetDateTime offsetDateTime = instant.atOffset(ZoneOffset.ofHours(8));
        System.out.println(offsetDateTime);
        //返回1970-01-01 00:00:00到当前时间的毫秒数，即为时间戳
        long l = instant.toEpochMilli();
        System.out.println(l);
        //通过给定的毫秒数，返回Instant实例
        Instant instant1 = Instant.ofEpochMilli(1605532950411L);
        System.out.println(instant1);
    }
```
