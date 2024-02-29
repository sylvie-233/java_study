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

```java
// 简单单例模式（饿汉式）
public class Singleton {
	private final static Singleton INSTANCE = new Singleton();
	private Singleton() {}
	public static Singleton getInstance() {
		return INSTANCE;
	}
}

// 简单单例模式（懒汉式）
public class Singleton {
	private final static Singleton INSTANCE = new Singleton();
	private Singleton() {}
	public static Singleton getInstance() {
		if (INSTANCE == null) {
			INSTANCE = new Singleton();
		}
		return INSTANCE;
	}
}

// 多线程优化
public class Singleton {
	private final static volatile Singleton INSTANCE = new Singleton();
	private Singleton() {}
	public static Singleton getInstance() {
		if (INSTANCE == null) {
			synchronized(Singleton.class) {\
				if (INSTANCE == null) {
					INSTANCE = new Singleton();
				}
			}
		}
		return INSTANCE;
	}
}

```


##### 原型模式
对象拷贝clone,（深拷贝、浅拷贝）

```java
//原型模式

```



#### 结构型设计模式(7)

##### 适配器模式
中间接口转换适配

![[Pasted image 20240221190638.png]]


```java
// 类适配器（继承实现）
public class TestSupplier { // 初始类
	public String doSupply() {
		return "iPhone 14 pro";
	}
}

public interface Target { // 目标接口
	String supply();
}

public void test(Target target) { // *******使用目标接口的方法******
	System.out.println(target.supply());
}

public class TestAdapter extends TestSupplier implements Target { // 适配实现
	@Override
	public String supply() {
		return super.doSupply();
	}
}

// 对象适配器（组合实现）
public class TestAdapter implements Target { // 适配实现
	TestSupplier supplier;

	public TestAdaper(TestSupplier supplier) {
		this.supplier = supplier;
	}

	@Override
	public String supply() {
		return supplier.doSupply();
	}
}
```

##### 桥接模式
和组合模式挺像的

```java
// 桥接模式（继承扩展）
public abstract class AbstractTea {
	protected Size size; // 尺寸作为桥接属性存放在类中

	protected AbstractTea(Size size) { // 在构造时需要知道尺寸属性
		this.size = size;
	}

	public abstract String getType(); // 具体类型依然是由子类决定
}

public abstract class RefinedAbstractTea extends AbstractTea { // 继承扩展属性维度
	protected RefinedAbstractTea(Size size) {
		super(size);
	}
	public abstract String getSize();
}
```

##### 组合模式

```java
// 就是组合
```

##### 装饰模式
通过组合的方式实现，不改变一个对象本身功能的继承上，给对象添加额外的行为
和代理模式很像

```java
public abstract class Base { // 目标功能
	public abstract void test();
}

public class Decorator extends Base { // 组合实现目标功能
	protected Base base;
	public Decorator(Base base) {
		this.base = base;
	}

	@Override
	public void test() {
		base.test();
	}
}

public classd DecoratorImpl extends Decorator { // 装饰实现
	public DecoratorImpl(Base base) {
		super(base);
	}

	@Override
	public void test() {
		// 前置处理
		super.test(); // 实际调用
		// 后置处理
	}
}

public void main() { // 装饰使用
	Base base = new BaseImpl();
	Decorator decorator = new DecoratorImpl(base);
}

```


##### 代理模式
当无法直接访问某个对象或访问某个对象存在困难时，可以通过一个代理对象来间接访问
```java
public abstract class Subject {
	public abstract void test();
}

public class Proxy extends Subject {
	Subject target;
	public Proxy(Subject subject) {
		this.target = subject;
	}
	@Override 
	public void test() {
		// 前置处理
		target.test(); // 实际调用
		// 后置处理
	}
}
```


JDK动态代理基于接口
```java
 public interface Subject {
	 public void test();
 }

public class SubjectImpl implements Subject {
	@Override
	public void test() {
		// 具体实现
	}
}

public class TestProxy implements InvocationHandler { // 代理封装
	private final Object object;
	public TestProxy(Object object) {
		this.object = object;
	}
	@Override
	public Object invoke(Object proxy, Method method, Object[] args) {
		// proxy为生成的代理对象，实现了目标Subject接口
		Object res = method.invoke(object, args); // 在被代理对象身上调用
		return res;
	}
}

public void main() { // 使用代理
	SubjectImpl subject = new SubjectImpl(); // 被代理对象(实际调用对象)
	InvocationHandler handler = new TestProxy(subject); // 代理封装
	Subject proxy = (Subject) Proxy.newProxyInstance( // 生成代理对象
		subject.getClass().getClassLoader(),
		subject.getClass().getInterface(),
		handler
	);
	proxy.test();

}
```

CGLib动态代理基于ASM框架实现










##### 外观模式
Facade门面
![[Pasted image 20240221202301.png]]
多个子系统设置一个统一的门面，当子系统需要修改时，只需要修改门面中的逻辑



```java
public class Facade {
	SubSystemA a = new SubSystemA(); // 门面组合
	SubSystemA b = new SubSystemB();
	SubSystemA c = new SubSystemC();

	public void marry() {
		a.test1();
		b.test2();
		c.test3();
	}
}
```


##### 享元模式
FlyWeight
将重复出现的内容作为共享部分取出，公共部分只有一个

```java
public class DBUtilFactory {
	private static final DBUtil UTIL = new DBUtil(); // 享元对象存放在工厂中
	public static DBUtil getFlyweight() {
		return UTIL;
	}
}
```

#### 行为型设计模式(11)

##### 解释器模式


```java

```

##### 模板方法模式

程序中某些操作是固定的，可以直接在类中对应的方法进行编写，但可能某些操作需要视情况而定，由不同的子类实现来决定

```java
public abstract class Test {
	public void test() {
		// 前置操作
		process(); // 调用抽象方法
		// 后置操作
	}
	abstract void process();
}
```

##### 责任链模式

![[Pasted image 20240221205544.png]]


```java
public abstract class Handler {
	protected Handler successor;
	public Handler connect(Handler successor) { // 组链
		this.successor = successor;
		return successor; // 方便链式调用
	}
	
	public void handle() {
		this.doHandle();
		Optional.ofNullable(successor).ifPresent(Handler::handle); // 责任链调用
	}
	public abstract void doHandle(); // 每个Handler实际操作
}
```

##### 命令模式

调用者 -> 命令 -> 接收者（功能实现）

```java
public interface Receiver {
	void action();
}

public abstract class Command {
	private final Receiver receiver;
	protected Command(Receiver receiver) {
		this.receiver = receiver;
	}
	public void execute() {
		receiver.action();
	}
}

public class Controller {
	public static void call(Command cmd) {
		cmd.execute();
	}
}


public void main() {
	Controller.call(new CommandImpl(new ReceiverImpl));
}
```

##### 迭代器模式

```java
public class MyArray<T> implements Iterable<T> {
	private final T[] array;

	@Override
	public Iterator<T> iterator() {
		return new MyIterator();
	}
	public class MyIterator implements Iterator<T> {
		private int cur = 0;
		@Override
		public boolean hasNext() {
			return cur < arr.length;
		}
		@Override
		public T next() {
			return array[cur++];
		}
	}
}
```

##### 中介者模式
中间商提供群体对话的平台（优化了原有的复杂多对多关系，简化成一对多关系）
```java
public class Mediator {
	private final Map<String, User> userMap = new HashMap<>();
	public void register(String address, User user) {
		userMap.put(address, user);
	}
	public User find(String address) {
		return userMap.get(address);
	}
}

public class User {
	public void find(String address, Mediator mediator) {
		// 前置操作
		User user = mediator.find(address);
		// 后置操作
	}
}
```

##### 备忘录模式
可回溯的时间节点，状态State保存和恢复

```java
// 状态保存类
public class State { // 对象中有哪些值需要保存的，State中就有哪些字段
	final String currentWork;
	final int percentage;
}


public State save();
public void restore(State);
```

##### 观察者模式

```java
public interface Observer {
	void action();
}

public class Subject {
	private final Set<Observer> set = new HashSet<>();
	public void observe(Observer observer) {
		set.add(observer);
	}
	public void modify() { // 调用观察者
		set.forEach(Observer::action);
	}
}
```


JDK实现
```

```


##### 状态模式
不同状态下有不同的行为
```java
public class Subject {
	private State state; // 状态枚举
	public void setState(State state) {
		this.state = state;
	}
	public void process() {
		switch (state) {
			case A:
				// A行为
				break;
			case B:
				// B行为
				break;
		}
	}
}
```

##### 策略模式
类似状态模式，主动指定执行的策略（策略中保存了具体的执行方法）

- 策略接口
- 策略接口的实现类
- 策略标识枚举类
- 策略工厂
- 实际业务


```java
public interface Strategy {  // 策略接口
	Object handle(Object arg);
}

public enum StrategyEnum { // 策略枚举标识
	STRATEGY_A("A"),
	STRATEGY_B("B"),
	private String name;
	StrategyEnum(String name) {
		this.name = name;
	}
	public static StrategyEnum getStrategyName(String name);
}

public class StrategyFactory { // 策略工厂
	private Map<String, Strategy> ctxStrategy = new HashMap<>();
	public StrategyFactory(Map<String, Strategy> map) {
		this.ctxStrategy = map;
	} 
	public Strategy getStrategy(String name) {
		return ctxStrategy.get(name);
	}
}

public void main() {
	strategy = StrategyFactory.getStrategy(strategyName);
	res = strategy.handle(arg);
}
```

##### 访问者模式

```java
public class Subject {}

public interface Visitor {
	void visit(Subject obj);
}
```




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


