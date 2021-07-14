1. 提供File类的对象，指明写出到的文件
2. 提供FileWriter的对象，用于数据的写出
3. 写出的操作
4. 流资源的关闭

```Java
@Test
public void Duplicate(){
    FileReader fileReader = null;
    FileWriter fileWriter = null;
    try {
        File srcfile = new File("hello.txt");
        File destfile = new File("hello2.txt");

        fileReader = new FileReader(srcfile);
        fileWriter = new FileWriter(destfile);
        char[] chars = new char[5];
        int len;
        while ((len = fileReader.read(chars)) != -1){
            fileWriter.write(chars,0,len);
        }
    } catch (IOException e) {
        e.printStackTrace();
    } finally {
        try {
            fileReader.close();
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            try {
                fileWriter.close();
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
}
```