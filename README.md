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
> 消息队列MessageQueue只是存储Message的地方，真正让消息队列循环起来的是Looper，这就好比消息队列MessageQueue是个水车，那么Looper就是让水车转动起来的河水，如果没有河水，那么水车就是个静止的摆设，没有任何用处，Looper让MessageQueue动了起来，有了活力。
### Handler ###
> 定义： Handler主要接收子线程发送的数据,并用此数据配合主线程更新UI，用来跟UI主线程交互用。

- 一个Handler会允许你发送和处理Message或者Runnable对象关联到一个线程的消息队列MessageQueue中,每一个Handler的实例都会关联一个单一的线程和那个线程的消息队列中。当你创建一个一个新的Handler,它会绑定到你创建的线程和这个线程消息队列中。并且指向好它，它会让消息传递到关联好它的消息队列中，当它从消息队列出队的时候执行它。这里他们的如何关联的不是很懂！

   对于Handler来说有两种主要的方式: 1.计划好消息和Runnable将来的某一个时间点来执行它 2. 从一个不同的线程中执行Handler的入队操作。分发消息由下面的几个方法完成:
   1) post(Runnable),
   2) postAtTime(Runnable, long), 
   3) postDelayed(Runnable, long), 
   4) sendEmptyMessage(int), 
   5) sendMessage(Message), 
   6) sendMessageAtTime(Message, long), 
   7) sendMessageDelayed(Message, long)
   
   post方式的方法可以将一个Runable对象排列到消息队列中。sendMessage方式的方法可以通过 Handler的handleMessage(Message) 方法携带有bundle类型的数据的Message对象到队列中(需要你实现Handler的子类)。你可以通过上诉两种方式来出来Handler,你可以允许你的消息在消息队列中准备好就马上被处理，也可以处理之前指定一些延时让你实现超时或者基于时间的行为。
   当你的应用程序的进程被创建的时候，它的主线程专门用来处理正常运行的主线程的消息队列，(也就是说UI主线程有自己的消息队列，所以我们没必要在UI主线程中处理自己的消息)它关心的是管理顶层的应用对象(activities, broadcast receivers, etc)和他们创建的窗口。你可以创建你自己的线程，然后通过Handler与主线程沟通。就像上述说的通过post和sendMessage的方式，Runnable和Message会被计划的执行在Handler的消息队列中适时的进行处理。






