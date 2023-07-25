# Java基础

Sylvie233的Java基础学习~~~

> Author: Sylvie233
>
> Date: 2022/10/21
>
> Point: 
>
> ​	JUC教程P14



[TOC]

## 基础介绍

### java

```
java:
	
```



### javac

```
javac:
	
```











## 核心内容

### JVM





### NIO

Selector、Channel、Buffer



### JUC

重量级锁

![image-20230725223631079](Java基础.assets/image-20230725223631079.png)





自旋锁





轻量级锁

乐观锁CAS

![image-20230725224120339](Java基础.assets/image-20230725224120339.png)



偏向锁

![image-20230725224546244](Java基础.assets/image-20230725224546244.png)



JMM

java内存模型：Save、Load

指令重排序

volatile关键字：线程工作内存、主内存（还可以禁止指令重排）

内存栅栏

happens-before先行发生原则





Lock、Condition

#### 可重入锁

公平锁、非公平锁

#### 读写锁





队列同步器AQS















## API

```
java:
	io:
	nio:
	util:
		concurrent: 并发
			locks:
                Condition:
                	await():
                	signal():
                Lock:
                	newCondition():
                ReadWriteLock:
                	readLock():
                	writeLock():
                ReentranLock:
                	getHoldCount():
                	getQueueLength():
                	hasQueuedThread():
                	isLocked():
                ReentranReadWriteLock:
                	
            TimeUnit:
            	SECONDS: 秒
            		sleep():
            		timeWait():
	Object:
	Thread:
```



### java.io

#### FileInputStream



### java.nio

#### channels

##### FileChannel

```
FileChannel:
	read():
```





#### ByteBuffer

```
ByteBuffer:
	allocate():
	---
	clear():
	compact():
	flip(): 切换读写模式
	get():
	hasRemaining():
```

