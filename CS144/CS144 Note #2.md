# CS 144 Note #2

## Note

### Packet switching principle

- source routing: packet 中有从起点到终点的完成的路由路径
- statistical multiplexing: 采用单一资源以概率方式在多个用户之间共享
  - 通过将所有发送的数据都看成 packet，以 packet switch 方式传输，可以让多个用户共享同一个 Link，充分利用资源

### Layering principle

<img src="C:\Users\polyethylene\AppData\Roaming\Typora\typora-user-images\image-20210402232625494.png" alt="image-20210402232625494" style="zoom: 80%;" />

### Encapsulation principle

上层数据成为下层封装的 payload

一个 VPN 的例子

![image-20210402234835391](C:\Users\polyethylene\AppData\Roaming\Typora\typora-user-images\image-20210402234835391.png)

内层的 IP 数据报将被计算机用 TLS 协议封装后再通过 TCP，IP，网络接口层协议封装后发送