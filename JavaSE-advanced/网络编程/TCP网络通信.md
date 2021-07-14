```Java
//客户端
@Test
public void client() {
    Socket socket = null;
    OutputStream stream = null;
   try {
        //1.创建Socket对象，指明服务器端的ip号和端口号
        InetAddress address = InetAddress.getByName("127.0.0.1");
        socket = new Socket(address, 7788);
        //2.获取一个输出流，用于输出数据
        stream = socket.getOutputStream();
        //3.写出数据
        stream.write("hello,this is client!".getBytes());
    } catch (IOException e) {
        e.printStackTrace();
    } finally {
        //stream.close()
        //socket.close()
        ····
        }
    }
}

//服务器端
@Test
public void server(){
    ServerSocket ss = null;
    Socket accept = null;
    InputStream is = null;
    ByteArrayOutputStream baos = null;
    try {
        //1.创建服务器端的ServerSocket,指明自己端口号
        ss = new ServerSocket(7788);
        //2.调用accept()表示接收服务器端的数据
        accept = ss.accept();
        //3.获取输入流
        is = accept.getInputStream();
        //4.读取输入流
        baos = new ByteArrayOutputStream();
        byte[] bytes = new byte[5];
        int len;
        while ((len = is.read(bytes))!= -1){
             baos.write(bytes,0,len);
            }
        System.out.println(baos.toString());
    } catch (IOException e) {
        e.printStackTrace();
    } finally {
        //baos.close();
        //is.close();
        //accept.close();
        //ss.close();
        ···
    }

}
```



```java
/*
客户端发送文件给服务端，服务端将文件保存在本地
*/

@Test
    public void client() {
        Socket socket = null;
        OutputStream out = null;
        FileInputStream fis = null;
        try {
            socket = new Socket("127.0.0.1", 9999);
            out = socket.getOutputStream();
            fis = new FileInputStream("win.png");

            byte[] bytes = new byte[1024];
            int len;
            while ((len = fis.read(bytes)) != -1) {
                out.write(bytes, 0, len);
            }
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            //fis.close()
            //out.close()
            //socket.close()
            ····
        }
    }
@Test
    public void server(){
        Socket acc = null;
        InputStream is = null;
        FileOutputStream fis = null;
        try {
            ServerSocket ss = new ServerSocket(9999);
            acc = ss.accept();
            is = acc.getInputStream();

            fis = new FileOutputStream("win1.png");

            byte[] bytes = new byte[1024];
            int len;
            while ((len = is.read(bytes)) != -1){
                fis.write(bytes,0,len);
            }
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            //acc.close()
            //is.close()
            //fis.close()
            ···
        }
    }
```

