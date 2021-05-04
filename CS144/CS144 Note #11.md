# CS 144 Note #11

可以将 TCP 分割成以下几个问题：

- 何时发送新数据
- 何时应该重传数据
- 何时应该发送 acknowledgement

## TCP Pre-Tahoe

最早的 TCP 协议机制如下

- 在终端存在 flow control window
- 连接建立后，直接发出等于 window 总大小的 packet
- 为每个 packet 设置一个重传计时器

这个方案缺少拥塞控制，window 可能远大于网络能承载的大小

<img src="./image/TCP-1986.png" style="zoom:100%;" />

## TCP Tahoe

TCP Tahoe 在原来的 TCP 基础上

- Congestion window
- Timeout estimation
- Self-clocking

### Congestion window

congestion window 和 flow window 不同，后者只考虑 endpoint 的缓存容量，前者考虑的是网络的承载能力。

$$
    Sender \ window = min(flow \ window, congestion \ window)
$$

将 congestion control 分为两个部分

- slow start
- congestion avoidance

#### slow start

- window 初始大小为 MSS (Maximum Segment Size)
- 每次接受到 ack，window 大小增加 MSS，所以大小是指数增长的（一开始一个 MSS 一个 ack 就加一，然后两个 MSS 两个 ack 就加二，然后4 个 MSS 4 个 ack 就加四，以此类推）

#### Congestion avoidance

- 每次 ack，window 大小增加 $\dfrac{MSS^2}{congestion \  window}$
- 实际上就是每个 RTT 增加一个 MSS（实际上每个 RTT 收到 $\dfrac{congestion \ window}{MSS}$ 个 ack）

### TCP Tahoe FSM

<img src="./image/TCP-Tahoe-FSM.png" style="zoom:100%;" />

window size 变化如下图（这里 ssthread 第二次没变是因为整数四舍五入了）

<img src="./image/TCP-Tahoe-behaviour.png" style="zoom:100%;" />

> 现在可以解答 “何时发送新数据” 这个问题：当 flow control window 和 congestion window 大小允许时，TCP-Tahoe 发送新数据。congestion window 由 sender 收到 ack 或超时来动态调整。