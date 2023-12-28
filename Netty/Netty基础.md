# Netty基础

Sylvie233的Java基础学习~~~

> Author: Sylvie233
>
> Date: 2023/1/3
>
> Point: 



[TOC]

## 基础介绍

![aa73567d6b1c4d2e8d358e37d8ceac01](Netty基础.assets/aa73567d6b1c4d2e8d358e37d8ceac01.png)

![netty-jiangjie-1](Netty基础.assets/netty-jiangjie-1.png)

![18694455-a3c9ef5cb186f425](Netty基础.assets/18694455-a3c9ef5cb186f425.webp)













### EventLoopGroup

selector+thread+任务队列

单线程执行器，维护了一个Selector



eventloop->channel->pipiline->handle

<img src="Netty基础.assets/image-20230103174824886.png" alt="image-20230103174824886" style="zoom:67%;" />





accept事件、读写事件



### Channel

![image-20230729135448697](Netty基础.assets/image-20230729135448697.png)











### Future&Promise



### Handler&Pipeline

入站处理器、出站处理器



<img src="Netty基础.assets/image-20230103191824273.png" alt="image-20230103191824273" style="zoom:67%;" />



Head handle、Tail handle

![image-20230729135633156](Netty基础.assets/image-20230729135633156.png)











### ByteBuf

读指针、写指针

<img src="Netty基础.assets/image-20230103193147499.png" alt="image-20230103193147499" style="zoom:67%;" />





池化



bytebuf的释放











## 核心内容















## API

```

```



### bootstrap

#### ServerBootstrap



### buffer

#### ByteBuf

#### ByteBufAllocator



### channel

#### nio

##### NioEventLoopGroup

io事件、普通任务、定时任务



#### socket

##### nio

###### NioServerSocketChannel

###### NioSocketChannel



#### ChannelHandlerContext

#### ChannelInboundHandlerAdapter

#### ChannelInitializer

#### EventLoopGroup



### util

#### NettyRuntime