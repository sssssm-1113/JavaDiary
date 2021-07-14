#### String与基本数据类型、包装类之间的转换

[Click here](C:\Users\krato\Desktop\JavaSE\1\19.包装类.md)



***

#### String与字符数组之间的转换

```java
 /*
    String与char[]之间的转换
    String --> char[]:调用toCharArray()
    char[] --> String:调用String的构造器
     */
    @Test
    public void test(){
        String str1 = "abc123";
        char[] charArray = str1.toCharArray();

        for (char c :charArray){
            System.out.println(c);
        }

        char[] arr = new char[]{'h','e','l','l','o'};
        String str2 = new String(arr);
        System.out.println(str2);

    }
    /*
    String与byte[]之间的转换
    String --> byte[]:调用String的getBytes()
    byte[] --> String:调用String的构造器
     */
    @Test
    public void test1() throws UnsupportedEncodingException {
        String str2 = "abc123";
        //使用默认的字符集，进行编码
        byte[] bytes = str2.getBytes();
        //使用gbk编码集进行编码
        byte[] gbks = str2.getBytes("gbk");

        System.out.println(Arrays.toString(bytes));
        //解码时需要使用相同的字符集
        String str3 = new String(bytes);
        System.out.println(str3);

        String str4 = new String(gbks,"gbk");
        System.out.println(str4);


    }

```



