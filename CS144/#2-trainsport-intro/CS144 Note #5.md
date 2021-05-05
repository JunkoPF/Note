# CS 144 Note #5

## Finite State Machines

![image-20210407182906724](C:\Users\polyethylene\AppData\Roaming\Typora\typora-user-images\image-20210407182906724.png)

### TCP 中的 FSM

![image-20210407182828310](C:\Users\polyethylene\AppData\Roaming\Typora\typora-user-images\image-20210407182828310.png)

### 用 FSM 表示 Stop and Wait

![image-20210407185839391](C:\Users\polyethylene\AppData\Roaming\Typora\typora-user-images\image-20210407185839391.png)

### Stop and Wait 中可能的情况

![image-20210407190343232](C:\Users\polyethylene\AppData\Roaming\Typora\typora-user-images\image-20210407190343232.png)

其中前三种都不会出现问题，第四种情况发生时，sender 不确定收到的 ACK 是对于第一个 packet 的还是第二个 packet 的。

针对第四种情况（Duplicated），停止等待协议需要用 1-bit 对 packet 进行编号。

<img src="C:\Users\polyethylene\AppData\Roaming\Typora\typora-user-images\image-20210407190604431.png" alt="image-20210407190604431" style="zoom:50%;" />

使用 1-bit 编号对于网络情况做了一些假设以保证能正常运行：

- 网络不会自己复制 packet
- packet 不会延迟多个 timeout 时间才被 receiver 收到（至多1个）