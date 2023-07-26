# Java基础

Sylvie233的Java基础学习~~~

> Author: Sylvie233
>
> Date: 2022/10/21
>
> Point: 
>
> ​	JUC教程P34

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





#### 队列同步器AQS

锁机制底层

双向链表

![image-20230726114815625](Java基础.assets/image-20230726114815625.png)

CAS算法、Unsafe操作

![image-20230726121827759](Java基础.assets/image-20230726121827759.png)





#### Condition

条件队列

![image-20230726122553947](Java基础.assets/image-20230726122553947.png)

![image-20230726123558159](Java基础.assets/image-20230726123558159.png)

![image-20230726124001354](Java基础.assets/image-20230726124001354.png)



#### 原子类

CAS算法

Atomic

ABA问题：带版本号的原子类解决（默认CAS自旋仅进行值比较）







#### 并发容器

##### CopyOnWriteArrayList

可重入锁







##### ConcurrrentHashMap

![image-20230726183532434](Java基础.assets/image-20230726183532434.png)

红黑树



##### BlockingQueue

阻塞队列









#### 线程池

##### ThreadPoolExecutor

拒绝策略

线程创建工程

![image-20230726194132958](Java基础.assets/image-20230726194132958.png)















#### CountDownLatch



#### CyclicBarrier



#### Semaphore



#### Exchanger



#### Fork/Join











## API

```
java:
	io:
		Serializable:
	lang:
		reflect:
			Field:
		Class:
			forName():
			getDeclaredConstructor():
			newInstance():
		Object:
        System:
            err:
            in:
            out:
            currentTimeMillis():
        Thread:
            currentThread():
	nio:
	text:
		SimpleDateFormat:
			format():
	util:
		concurrent: 并发
			atomic:
				AtomicInteger:
					compareAndSet():
					getAndAdd():
					getAndIncrement():
				AtomicBoolean:
				AtomicIntegerArray:
				AtomicIntegerFieldUPdater: 字段原子更新器
					newUpdater():
					---
					incrementAndGet():
				AtomicLong:
				AtomicReference: 引用原子
					compareAndSet():
					get():
				AtomicStampedReference: 带版本号
				LongAdder:
					add():
			locks:
				AbstractQueuedSynchronizer: AQS队列
                Condition:
                	await():
                	signal():
                Lock:
                	newCondition():
                LockSupport:
                	park(): 线程挂起
                	unpark():
                ReadWriteLock:
                	readLock():
                	writeLock():
                ReentranLock:
                	getHoldCount():
                	getQueueLength():
                	hasQueuedThread():
                	isLocked():
                ReentranReadWriteLock:
            ArrayBlockingQueue: 有界带缓冲队列
            BlockingQueue:
            	put():
            	take():
            ConcurrentHashMap:
            CopyOnWriteArrayList:
            Delayd:
            DelayQueue:
            Executors:
            	newFixedThreadPool():
            	newSingleThreadExecutor():
            ExecutorService:
            	shutdown():
            	submit():
           	Future:
           		cancel():
           		get():
           		isCancelled():
           		isDone():
           	FutureTask:
           		get():
           		
            LinkedTransferQueue: 无界带缓冲阻塞队列
            PriorityBlockingQueue:
            ScheduledFuture:
            	
            ScheduledThreadPoolExecutor:
            	schedule():
            	scheduleAtFixedRate():	
            	scheduleWithFiexedDelay():
            SynchronousQueue: 无缓冲阻塞队列
            ThreadFactory:
            ThreadPoolExecutor: 线程池
            	execute():
            	getPoolSize():
            	shutdown():
            	shutdownNow():
            TimeUnit:
            	SECONDS: 秒
            		sleep():
            		timeWait():
            	convert():
		ArrayList:
		HashMap:
		HashSet:
			remove():
		List:
			size():
		Map:
			put():
			size():
		PriorityQueue:
	

sum:
	misc:
		Unsafe:
			allocateInstance():
			getUnsafe():
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

