# CS 144 Note #4

## Note

### Transmission Control Protocol

Connection: 当两个应用程序使用 TCP 时，建立一个**双向**的通信连接

在连接的两端，TCP 都会保留一个状态机来跟踪连接的方式

### 3-way handshake

![image-20210404145909334](C:\Users\polyethylene\AppData\Roaming\Typora\typora-user-images\image-20210404145909334.png)

### connection teardown

![image-20210404150229190](C:\Users\polyethylene\AppData\Roaming\Typora\typora-user-images\image-20210404150229190.png)

### TCP 确保可靠传输的方法

#### Stream of bytes

双方数据以比特流形式传输

#### Reliable delivery

- 每次正确接收到发送方的数据都发送 ACK 来告知发送方已正确接收（一般为捎带回复）
- 通过校验和来检查数据是否损坏
- 通过序列号 sequence numbers 来检查是否有遗漏的数据
- 通过流量控制来防止 overruning receiver

#### In-sequence

TCP 通过序列号保证接收方收到的数据顺序与发送方顺序相同

#### Congestion Control

TCP 提供拥塞控制机制

### Details

- 为了保证发送方使用的端口是未被使用的，发送方每申请一个TCP连接，就将设置的端口号加一（到达最大值就循环）
  - 但这样对于一个长时间存在的 TCP 连接因为端口号循环而与一个新连接冲突
  - 冲突时两个连接发送的数据可能会混淆
  - 为防止上述情况，TCP 会使用一个随机的序列号 seq 作为发送方字节流的初始序列号（ISN）

