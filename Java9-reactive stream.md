# Java9-Reactive Streams
[原地址 - Java 9 - Reactive Streams](https://www.cnblogs.com/IcanFixIt/p/7245377.html)
## 目录
- 什么是流（stream）
- Reactive Streams 指什么，规范和Java API
- Reactive Streams的API 以及使用方法
- 使用JDK 9中的 Reactive Streams 的Java API来创建发布者，订阅者，处理者
  - Publisher<T>
  - Subscriber<T>
  - Subscription
  - Processor<T,R>
  
## 什么是Streams
### abstract
- Streams由生产者生产，一个或者多个消费者消费的item序列。
- 生产者——消费者模型（source——sink model）
- 发布者——订阅者模型（publisher——subscriber model）
### 处理机制
- pull模型
  - 订阅者找发布者拿元素
- push模型
  - 发布者推送元素给订阅者
### 实际问题
- 理想情况是publisher and Subscriber works at same speed;
- 实际
  - publisher push item too fast
  - Subscriber process too slow
- 解决方法：
  - Subscriber has an unlimited buffer to save items or discard some unhandled items
  - backpressure
    - Asking publisher to slow down push speed untill Subscriber getting ready.
    - Publisher needs unlimited buffer to handle items.
    
- 异步机制可以保持Publisher && Subscriber 高效的处理双方的工作

## Reactive Streams
- 2013年提出的标准，作为提供非阻塞背压的异步流处理标准
- 目的：
  - 规范传输标准，避免Publisher阻塞，以及Subscriber需要无限的缓冲区
- 大体规则：
  - Reactive Streams让传输方式在Push 和Pull之间轮流切换
    - Subscriber slow ： pull
    - Subscriber fast ： push
    
- 接口规范：
  ```
  Publisher<T>
  Subscriber<T>
  Subscription
  Processor<T, R>
  ```
  Processor 用来转换元素 <T> -> <R>
  ![Processor](https://upload-images.jianshu.io/upload_images/4366140-0478dfc952615288.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
  - 接口：
  ```
  public interface Publisher<T> {
    public void subscribe(Subscriber<? super T> s);
  }
  public interface Subscriber<T> {
    public void onSubscribe(Subscription s);
    public void onNext(T t);
    public void onError(Throwable t);
    public void onComplete();
  }
  public interface Subscription {
    public void request(long n);
    public void cancel();
  }
  public interface Processor<T,R> extends Subscriber<T>, Publisher<R> {
  }
  ```
  Reactive Streams接口简单，但是自己实现起来比较困难，[RxJava](https://github.com/ReactiveX/RxJava)
  是一种实现方式

## JDK9 中Reactive Streams 的API使用方法
 见原链接，当前时间不足直接学习AKKA Stream
  
  
  
  
