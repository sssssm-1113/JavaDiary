#### 流的分类

* 按操作数据单位不同 分为：字节流(8 bit)，字符流(16 bit)
* 按数据流的流向不同分为：输入流，输出流
* 按流的角色的不同分为：节点流，处理流



#### 流的体系结构

| 抽象基类 | 字节流       | 字符流 |
| -------- | ------------ | ------ |
| 输入流   | InputStream  | Reader |
| 输出流   | OutputStream | Writer |



| 抽象基类     | 节点流（文件流） | 缓冲流（处理流的一种） |
| ------------ | ---------------- | ---------------------- |
| InputStream  | FileInputStream  | BufferedInputStream    |
| OutputStream | FileOutputStream | BufferedOutputStream   |
| Reader       | FileReader       | BufferedReader         |
| Writer       | FileWriter       | BufferedWriter         |













