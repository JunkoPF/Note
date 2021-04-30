# CS 144 Note #1

## vocabulary

- bidirectional 双向的
- swarms 集群 （BitTorrent 中的概念）

## Note

- Bidirectional, reliable byte stream
  - 目前大部分机器之间的数据传输采用这种方式
  - 但也存在其他的传输方式
- 网络可以抽象成两个程序之间的一个传输信息的管道
- 一些网络的应用
  - World Wide Web (基于HTTP)
    - Client 与 Server 之间传输数据
  - BitTorrent
    - Client 从其他 Client 处获得数据
    - 首先 Client 从互联网中获得 Torrent file
    - Torrent file 中包含所需数据的描述信息与 Tracker 的信息，Tracker 是一个持续跟踪对应 swarm 中 Client 的节点
    - Client 通过 HTTP 从 Tracker 处获得目标 swarm 的 Clients' list，然后从这些 Clients' 中选择一些来请求文件 piece，最终得到完整的文件
    - 当一个 Client 完成了下载后，也会被 Tracker 加入到对应的 list 中，让其他 Clients 请求数据
  - Skype
    - <img src="C:\Users\polyethylene\AppData\Roaming\Typora\typora-user-images\image-20210330211338282.png" alt="image-20210330211338282" style="zoom:50%;" />
    - <img src="C:\Users\polyethylene\AppData\Roaming\Typora\typora-user-images\image-20210330211421254.png" alt="image-20210330211421254" style="zoom:50%;" />

