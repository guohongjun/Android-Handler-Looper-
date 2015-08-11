# Android 消息处理机制
android的消息处理机制是消息驱动的，要是实现消息驱动需要以下几个元素：

- 消息 Message
- 消息队列  MessageQueue
- 消息循环  Looper，用于循环MessageQueue中消息。
- 消息处理  Handler，用于处理Looper取出的Message。

android的消息处理有三个核心类：Looper,Handler和Message。其实还有一个Message Queue（消息队列），但是MQ被封装到Looper里面了，我们不会直接与MQ打交道，因此我没将其作为核心类。下面一一介绍下：
### Message###


### MessageQueue ###

### Looper ###

### Handler ###
> 定义：






