1. File类的实例化
2. FileReader流的实例化
3. 读入的操作
4. 资源的关闭


```java 
    /*
    说明：
    read() 返回读入的字符，如果到达文件末尾，返回-1
    异常的处理：为了保证流资源一定可以执行关闭操作，使用try-catch-finally
    读入的文件一定要存在，否则会报FileNotFoundException
     */
    @Test
    public void test() {
        FileReader fileReader = null;
        try {
            File file = new File("hello.txt");//相较于当前module
            //提供具体的流
            fileReader = new FileReader(file);
            //数据的读入:read() 返回读入的字符，如果到达文件末尾，返回-1
//        int data = fileReader.read();
//        while (data != -1) {
//            System.out.print((char) data);
//            data = fileReader.read();
//        }
            //语法二
            int data;
            while((data = fileReader.read()) != -1){
                System.out.print((char)data);
            }
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            try {
                //关闭流
                if (fileReader != null)
                    fileReader.close();
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
```

```Java
	/*
    对read()操作升级，使用read的重载方法
    read(char[] cbuf):返回每次读入cbuf数组中字符的个数
     */
    @Test
    public void test1(){
        FileReader fileReader = null;
        try {
            File file = new File("hello.txt");
            fileReader = new FileReader(file);
            char[] chars = new char[5];
            int len;
            while ((len = fileReader.read(chars)) != -1){
                //方式一
//                for (int i = 0; i < len; i++) {
//                    System.out.print(chars[i]);
//                }
                //方式二
                String str = new String(chars,0,len);
                System.out.print(str);
            }
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            try {
                fileReader.close();
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
```