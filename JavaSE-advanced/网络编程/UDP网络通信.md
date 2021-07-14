 UDP数据报通过数据报套接字 DatagramSocket 发送和接收，系统不保证UDP数据报一定能够安全送到目的地，也不能确定什么时候可以抵达。

```Java

//发送端
@Test
public void send() throws IOException {
    DatagramSocket socket = new DatagramSocket();

    String str = "I'm UDP rocket!";
    byte[] bytes = str.getBytes();
    InetAddress localHost = InetAddress.getLocalHost();
    DatagramPacket packet = new DatagramPacket(bytes, 0, bytes.length,localHost,8888);

    socket.send(packet);

    socket.close();


}

//接收端
@Test
public void receive() throws IOException {
    DatagramSocket socket = new DatagramSocket(8888);
    byte[] bytes = new byte[100];
    DatagramPacket packet = new DatagramPacket(bytes,0,bytes.length);

    socket.receive(packet);

    System.out.println(new String(packet.getData(),0,packet.getLength()));

    socket.close();
}
```