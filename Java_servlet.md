# servlet
## abstract
- servlet 主要功能用于交互式浏览或者修改数据，生成动态Web内容
- 理论上可以响应任何类型的请求，但是绝大多数情况Servlet只用来扩展基于HTTP协议的Web服务器

## 和CGI（Common Gateway Interface）的区别
- CGI：
  - 请求被服务后需要卸载，高内存开销，CPU开销大，同一个进程不能服务多个客户
- Servlet
  - 开销小，每个请求生成一个新的线程。
  
## 生命周期
1. 客户端请求该Servlet
2. 还在Servlet类到内存
3. 实力化并调用init（）方法初始化Servlet
4. service（）（根据请求方法不同，调用doGet（）， doPost（）， doHead(), doPut(), doTrace(), doDelete(),doOptions(),destory()）
5. 加载和实力化Servlet。动态执行。类似于web.xml

### 具体步骤
- Server创建一个Servlet实例
- 第一个客户端请求到达Server
  - Server 调用Servlet 的init() 方法（配置为Server创建Servlet实例时调用，在web.xml中<servlet>标签下配置<load-on-startup>标签，
  配置的值为整数， 值越小Servlet的启动优先级越高)
- 一个客户端请求到达Server
  - Server创建一个请求对象，处理客户端请求
  - Server创建一个响应对象，响应客户端请求
  - Server激活Servlet的service（）方法， 传递请求和响应对象作为参数
  - service（）方法活的请求对象的信息，处理请求，访问其他资源，获取相关的信息
  - service（）方法使用响应对象的方法，将响应传回Server，最终到达客户端。
- 更多的客户端请求，Server创建新的请求和响应对象，仍然激活这个Servlet的service（）方法，将这两个对象作为参数传递给它。
  - 不需要再次调用init（）方法。
  - servlet只初始化一次（只有一个对象）
- Server不需要Servlet时候（Server关闭），Server调用Servlet的destroy（）方法
  
  ![Servlet生命周期](https://baike.baidu.com/pic/servlet/477555/0/2cf5e0fe9925bc31930cf45c55df8db1ca1370a5?fr=lemma&ct=single)
### 与Applet比较

