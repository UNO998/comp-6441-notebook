# Akka Streams
> 摘抄自 ：Reactive Web Application - chapter 9 - Reactive Streams
## 目录：
  - Reasons for defining a Reactive Streams standard
  - The building blocks of the Akka Streams library that implements Reactive Streams
  - Using Akka Streams in combination with iteratees and building a simple flow graph
  - Observing reactive back pressure in action
  
## Reacitve Streams
见文档[Reactive Streams](https://github.com/UNO998/comp-6441-notebook/blob/master/Java9-reactive%20stream.md)

## Akka Streams
### Core Principles
- There are four major building blocks (Processing Stages) in Akka Terms
  - Source
    - No Input
    - One Output
    - Producing Streaming data
  - Sink
    - One Input
    - No Output
    - Consuming Streaming data
  - Flow
    - Exactly One Input
    - Exactly One Output
    - Transform Streaming data in one way to another
  - Junction
    - Multiple Inputs
    - Multiple Outputs
- When We need to use Junctions, it's a flow graph.
### 专有名词
- Runnable flow
  - 一个flow graph中，所有不见的输入输出都完备则可以run了。
- Materialization（实体化）
  -  The process of running a flow
