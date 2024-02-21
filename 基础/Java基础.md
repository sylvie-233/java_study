# Java基础

Sylvie233的Java基础学习~~~

> Author: Sylvie233
>
> Date: 2022/10/21
>
> Point: 
>	Java 设计模式：P12
>		
> ​

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

### 集合







### 注解

#### 反射






### 设计模式



- 单一职责原则：一个对象应该
- 开闭原则：对扩展开放，对修改关闭
- 里氏替换原则：子类型的特别定义
- 依赖倒转原则：高层模块不应直接依赖底层模块，应该依赖抽象
- 接口隔离原则：
- 合成复用原则：优先使用对象组合，而不是通过继承来达到复用的目的
- 迪米特法则：最小知识原则


#### 创建型设计模式(5)


##### 工厂方法模式

避免直接new对象，使用工厂方法创建对象

```java

// 简单工厂模式
public class FruitFactory {
	public static Fruit getFruit(String type) {
		switch (type) {
			case "苹果":
				return new Apple();
			case "橘子":
				return new Orange();
			default:
				return null; 
		}
	}
}

// 工厂方法模式
public abstract class FruitFactory<T extends Fruit> {
	public abstract T getFruit();
}


public class AppleFactory extends FruitFactory<Apple> { // 专门生产苹果的工厂
	@Override
	public Apple getFruit() {
		return new Apple;
	}
}

```


##### 抽象工厂模式
工厂方法模式只适用于简单对象，当需要生产多个产品族时，使用抽象工厂模式

```java
// 抽象工厂模式
public abstract class AbstractFactory {
	public abstract Phone getPhone();
	public abstract Table getTable();
	public abstract Router getRouter();
}
```


##### 建造者模式
Builder

```java
// 建造者模式
public class Student {
	private Student(int id, int age, String name) {}

	public static StudnetBuilder builder() {
		return new StudentBuilder();
	}
	public static class StudentBuilder {
		int id; // 可以设置默认值
		int age;
		String name;
		public StudentBuilder id(int id) {
			this.id = id;
			return this;
		}
		public StudentBuilder age(int age) {
			this.age = age;
			return this;
		}
		public StudentBuilder name(String name) {
			this.name = name;
			return this;
		}
		public Studnet build() {
			return new Student(id, age, name);
		}
	}
}
```




##### 单例模式


##### 原型模式


#### 结构型设计模式(7)

##### 适配器模式

##### 桥接模式

##### 组合模式

##### 装饰模式

##### 代理模式

##### 外观模式

##### 享元模式


#### 行为型设计模式(11)

##### 解释器模式

##### 模板方法模式

##### 责任链模式

##### 命令模式

##### 迭代器模式

##### 中介者模式

##### 备忘录模式

##### 观察者模式

##### 状态模式

##### 策略模式

##### 访问者模式




### JVM





### NIO

Selector、Channel、Buffer



### JUC

Callable和Runnable类似，但可带返回值







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

##### Executors


##### ThreadPoolExecutor

拒绝策略

线程创建工程

![image-20230726194132958](Java基础.assets/image-20230726194132958.png)















#### CountDownLatch



#### CyclicBarrier
 类似CountDownLatch


#### Semaphore
信号量抢占、释放


#### Exchanger



#### Fork/Join











## API

```
java:
	io:
		Serializable:
	lang:
		annotation:
			ElementType:
			Retention:
			RetentionPolicy:
			Target:
		reflect:
			Field:
			Proxy:
				newProxyInstance():
		Class:
			forName():
			getDeclaredConstructor():
			newInstance():
		Integer:
		Object:
		String:
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
	
javax:
	annotaion:
		PostConstruct:
		Resource:
	validation:
		constraints: 模型注解
			NotNull:
			Pattern:
			Size:
				min
		Valid:

sum:
	misc:
		Unsafe:
			allocateInstance():
			getUnsafe():
```


