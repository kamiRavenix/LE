# 网络协议
## 协议复现
### TCP
**三次握手**
<img width="1422" height="68" alt="image" src="https://github.com/user-attachments/assets/af1ab1c0-d4ff-4d49-95be-5edb836758dd" />

*三次握手（Three-Way Handshake）是指建立一个TCP连接时，需要客户端和服务端总共发送3个包以确认连接的建立。

第一次握手客户端将标志位 SYN 置为1，随机产生一个值 seq=s ，并将该数据包发送给服务端，客户端进入 SYN_SENT 状态，等待服务端确认。

第二次握手服务端收到数据包后由标志位 SYN=1 知道客户端请求建立连接，服务端将标志位 SYN 和 ACK 都置为1，ack=s+1，随机产生一个值 seq=k ，并将该数据包发送给客户端以确认连接请求，服务端进入 SYN_RCVD 状态。

第三次握手客户端收到确认后，检查ack值是否为s+1，ACK标志位是否为1，如果正确则将标志位 ACK 置为1，ack=k+1，并将该数据包发送给服务端，服务端检查ack值是否为k+1，ACK标志位是否为1，如果正确则连接建立成功，客户端和服务端进入 ESTABLISHED 状态，完成三次握手。*

**四次挥手**
<img width="1340" height="102" alt="image" src="https://github.com/user-attachments/assets/3768049e-4e31-4219-a720-eecad067c97d" />

*四次挥手（Four-Way Wavehand）指断开一个TCP连接时，需要客户端和服务端总共发送4个包以确认连接的断开。

第一次挥手客户端发送一个 FIN ，用来关闭客户端到服务端的数据传送，客户端进入 FIN_WAIT_1 状态。

第二次挥手服务端收到 FIN 后，发送一个 ACK 给客户端，确认序号为收到序号+1，服务端进入 CLOSE_WAIT 状态。

第三次挥手服务端发送一个 FIN ，用来关闭服务端到客户端的数据传送，服务端进入 LAST_ACK 状态。

第四次挥手客户端收到 FIN 后，客户端进入 TIME_WAIT 状态，接着发送一个 ACK 给服务端，确认序号为收到序号+1，服务端进入 CLOSED 状态，完成四次挥手。*




### UDP

*UDP 是一种「无连接、不可靠、面向报文」的传输层协议 —— 它把应用层的数据打包成一个个「数据报」直接扔给 IP 层发出去，不管对方收没收到。*

**主要特点**

*协议开销小、效率高。

UDP是无连接的，即发送数据之前不需要建立连接。

UDP使用尽最大努力交付，即不保证可靠交付。

UDP没有拥塞控制。

UDP支持一对一、一对多、多对一和多对多交互通信。

UDP的首部开销小，只有8个字节。*
<img width="2556" height="1050" alt="image" src="https://github.com/user-attachments/assets/16da2a85-9cfe-4c59-bc00-88c44d056c0f" />

### DNS

*DNS是一个简单的请求-响应协议，是将域名和IP地址相互映射的一个分布式数据库，能够使人更方便地访问互联网。DNS使用TCP和UDP协议的53端口。*

