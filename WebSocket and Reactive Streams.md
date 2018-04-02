# WebSocket
## Key point
- web protocal based on TCP
- full-duplex communication
- server could send information to client

## BackGround
### Before WebSocket protocol
- Using multiple http links
  - [links for long connection && short connection](./长链接&短链接&双工&单工.md)

## WebSocket protocol 
### 使用背景
- 实现单个TCP连接的双向通信
- 代替HTTP的双向通讯技术（HTTP技术当初设计的目的不是为了实现双向通讯，而WebSocket则是）
### 实现原理
- 握手 + 双向通讯
  - 握手：浏览器发出WebSocket连线请求，服务器发出回应。一次握手就可以形成快速通道。
### 两大好处
- header：
  - 相互沟通的header是很小的 2Bytes
- Server push：
  - 服务器不再被动接受浏览器请求返回数据，而是在有新数据时就主动推送浏览器。
### 特点：
  - 简历在TCP协议上，服务器端实现比较容易
  - HTTP兼容，默认端口80 && 443；握手阶段采用HTTP协议，握手不容易屏蔽，能通过HTTP代理
  - 数据格式轻量，开销小
  - 没有同源限制，客户端可以与任意服务器通信
  - 协议标识符是ws，如果加密的话，则是wss（ws://example.com:80/some/path）
  
### 握手协议例子
#### 浏览器请求
GET /webfin/websocket/ HTTP/1.1
Host: localhost
Upgrade: websocket
Connection: Upgrade
Sec-WebSocket-Key: xqBt3ImNzJbYqRINxEFlkg==
Origin: http://服务器地址
Sec-WebSocket-Version: 13

#### 服务器回应
HTTP/1.1 101 Switching Protocols
Upgrade: websocket
Connection: Upgrade
Sec-WebSocket-Accept: K7DJLdLooIwIG/MOpvWFB3y3FE8=
![WebSocket And HTTP](http://www.ruanyifeng.com/blogimg/asset/2017/bg2017051502.png)
