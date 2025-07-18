# TCP和UDP传输协议的区别？

> 本文作者：[程序员牛肉](https://github.com/luoye6)
>
> 本站地址：[https://xbt.xiaobaitiao.top](https://xbt.xiaobaitiao.top)

1. TCP是可靠的传输协议，你知道它怎么实现的一些拥塞控制，或者说对于数据发送量的合理限制？

TCP（传输控制协议）通过拥塞控制和流量控制来实现可靠的数据传输。其中，拥塞控制是TCP用来控制网络拥塞和避免网络超载的机制，而流量控制是用来控制数据发送方与接收方之间的数据流量的机制。

拥塞控制主要通过以下几个算法来实现：

1. 慢启动（Slow Start）：在建立连接时，TCP发送方初始将拥塞窗口设置为一个较小的值，然后每收到一个确认，拥塞窗口指数式增加，以适应网络的容量。
2. 拥塞避免（Congestion Avoidance）：一旦拥塞窗口达到一个阈值（拥塞窗口大小的一半），TCP发送方就采用线性增加的方式增加拥塞窗口，以更稳定地发送数据。
3. 快速重传（Fast Retransmit）：如果TCP发送方连续接受到3个重复的确认（ACK），即表明网络中有一段丢失的数据，TCP发送方将立即重传这些数据，而不必等待超时。
4. 快速恢复（Fast Recovery）：在进行快速重传后，TCP发送方将拥塞窗口减半，并且进入快速恢复状态。在此状态下，每收到一个确认，拥塞窗口仍然线性增加，但增加的速度较慢。

对于数据发送量的合理限制，TCP使用了流量控制机制来确保接收方能够跟上发送方的发送速度。流量控制通过使用滑动窗口（Sliding Window）来限制发送方的数据发送量，确保不会使接收方无法处理大量数据。

滑动窗口的大小由接收方动态调整。每次接收方收到一定数量的数据后，会向发送方发送一个确认，确认中包含了接收方的可用窗口大小。发送方根据接收方返回的可用窗口大小来动态调整发送的数据量，以保持发送方和接收方的数据传输速度的平衡。

通过拥塞控制和流量控制的机制，TCP能够根据网络的状况和接收方的处理能力来合理地限制数据发送量，同时保证网络的稳定和可靠性。

