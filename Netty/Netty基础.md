# Netty基础

Sylvie233的Java基础学习~~~

> Author: Sylvie233
>
> Date: 2023/1/3
>
> Point: 



[TOC]

## Netty介绍

### EventLoopGroup

selector+thread+任务队列

单线程执行器，维护了一个Selector



eventloop->channel->pipiline->handle

<img src="Netty基础.assets/image-20230103174824886.png" alt="image-20230103174824886" style="zoom:67%;" />





accept事件、读写事件



### Channel



### Future&Promise



### Handler&Pipeline

入站处理器、出站处理器



<img src="Netty基础.assets/image-20230103191824273.png" alt="image-20230103191824273" style="zoom:67%;" />



Head handle、Tail handle









### ByteBuf

读指针、写指针

<img src="Netty基础.assets/image-20230103193147499.png" alt="image-20230103193147499" style="zoom:67%;" />





池化



bytebuf的释放







## Netty库(io.netty)

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