#### File类的使用

1. File类的一个对象，代表一个文件或一个文件目录
2. File类声明在java.io包下
3. File类中涉及到关于文件或文件目录的操作，并未涉及到写入或读取文件内容的操作，若需要读取或写入文件内容，必须使用IO流来完成
4. File类的对象常会作为参数传递到流的构造器中，指明读取或写入的”终点“

```Java
@Test
public void test(){
    //构造器一
    File file1 = new File("hello.txt");//相对路径
    File file2 = new File("D:\\Downloads\\The Boys");//绝对路径

    System.out.println(file1);
    System.out.println(file2);

    //构造器二
    File file3 = new File("D:\\Drivers","AMDGFX");

    //构造器三
    File file4 = new File(file3,"hi.txt");


}
```



常用方法：

* File类的获取功能

public String *getAbsolutePath*()：获取绝对路径 

public String *getPath*() ：获取路径 

public String *getName*() ：获取名称 

public String *getParent*()：获取上层文件目录路径。若无，返回null 

public long *length*() ：获取文件长度（即：字节数）。不能获取目录的长度。 

public long *lastModified*() ：获取最后一次的修改时间，毫秒值 

public String[] *list*() ：获取指定目录下的所有文件或者文件目录的名称数组 

public File[] *listFiles*() ：获取指定目录下的所有文件或者文件目录的File数组

* 重命名功能

public boolean *renameTo*(File dest):把文件重命名为指定的文件路径
	说明：file1.renameTo(file二)	要想返回true，需要file1在硬盘中存在，file2在硬盘中不存在

* 判断功能

public boolean *isDirectory*()：判断是否是文件目录 

public boolean *isFile*() ：判断是否是文件 

public boolean *exists*() ：判断是否存在 

public boolean *canRead*() ：判断是否可读 

public boolean *canWrite*() ：判断是否可写 

public boolean *isHidden*() ：判断是否隐藏



* 创建方法

public boolean *createNewFile*() ：创建文件。若文件存在，则不创建，返回false 

public boolean *mkdir*() ：创建文件目录。如果此文件目录存在，就不创建了。 如果此文件目录的上层目录不存在，也不创建。 

public boolean *mkdirs*() ：创建文件目录。如果上层文件目录不存在，一并创建