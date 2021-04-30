# CS 144 Note #3

## Note

Internet 规定数据以大端方式存储，所以对于小端方式的处理器（Intel/AMD），需要进行转换。

使用 C 中的函数 htons 与 ntohs 进行 host 与 net 之间的数据转换（short 类型，同样也有 htonl 与 ntohl