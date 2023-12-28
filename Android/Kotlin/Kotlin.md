# Kotlin

> Author: Sylvie233
>
> Date: 23/5/23
>
> Point:
> 	全网稀缺】2021Android从零入门到实战(Kotlin最新版)：P5

## 基础介绍


```
关键字:
	break:
	false:
	in:
	println:
	true:
	val:
	var:
	
```













### 数据类型

```
数据类型:
	Any:
	Unit:
	---
	Boolean:
	Byte:
	Double:
	Float:
	Int:
	Long:
	Short:
	String:
	Array<T>:
		IntArray:
	List<T>:
		size:
		---
		MutableList<T>:
			add():
			---
	Map<K, V>:
		---
		MutableMap<K, V>:
	Pair<A, B>:
		first:
		second:
		---
		Triple<A, B, C>:
	Range:
		---
		IntRange:
	Set:
		---
		MutableSet:
```



#### 字符串

```kotlin
"字符串"


"""
	多行字符串
"""
```





### 流程控制
```kotlin
// if ... else ...

```






#### 函数
```kotlin
fun xxx() {
	
}
```








### 面向对象

#### class

```kotlin
class Xxx(xxx: Int) {
	var xxx: Int = 1
	private get() = xxx
	set(value) {
		xxx = value
	}
	
	fun xxx() {}
	
	constructor() {}
	init {}
}
```


类



##### lateinit



##### 访问修饰符

```
:
	protected:
	internal:
```





##### **类修饰符**

```
:
	abstract:
	final:
	open:
	enum: 枚举类
	inner:
	
```





##### 对象表达式

匿名类实现

```
object : Xxx {
	fun xxx() {}
}
```







##### 继承





##### override



##### **companion object**

伴生对象、模拟静态行为

```
class Xxx {
	companion object {}
}
```



##### **委托**

by、operator



**延迟委托**

lazy



##### 泛型



##### 注解








#### interface
```kotlin


```



#### data class

数据类

```
data class:
	copy():
	hashCode():
	toString():
```



#### sealed class

密封类、多类的包装



#### object









## 核心内容

### kotlin

```


ranges:
	IntProgression:
	
reflect:
```



### kotlinx

```
coroutines:
	
```



## Android





## Jetpack








