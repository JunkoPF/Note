# CS 144 Note #6

## Circuit Switching

早期的电话线路，每两台电话之间的通信都有一条专用的物理连接。

现代有线电话，使用虚拟线路，即两台电话通信时会建立一条虚拟连接，同一条物理线路可以用于多个通信。

### 为什么计算机网络不使用 Circuit Switching

- 互联网之间的数据传输是突发性的，可能会在短时间内需要传输大量数据而在之后一段时间内空闲，如果每次通信都占用一个连接，那么会造成大量浪费。
- 互联网中存在很多种应用，传输数据的速度也各不相同，固定传输速度的 circuit 并不适合用于此。
- Circuit Switching 需要维护每次通信的状态，以保证 circuit 不被其他通信占用且正确工作，而互联网中存在大量的连接，这种需要维护 state 的方案会造成大量开销。

## Packet Switching

数据通信不建立专用的 circuit，而是通过各个节点的转发来传输数据。

### buffer

Packet Switching 的节点需要 buffer，因为当同时有来自不同线路的多个 packet 发送到同一个节点，但节点的出口带宽不能将其全部转发出去时，需要先将一部分 packet 放入 buffer 中。

![image-20210423111650796](C:\Users\polyethylene\AppData\Roaming\Typora\typora-user-images\image-20210423111650796.png)

### 为什么计算机网络使用 Packet Switching

- 每个 packet 的路径都是独立的，只根据节点的 forwarding table 决定。
- 所有的 packets 共享链路的总容量，充分利用资源。
- 节点只需要维护 forwarding table，不需要维护连接的状态。