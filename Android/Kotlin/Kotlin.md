# Kotlin

> Author: Sylvie233
>
> Date: 23/5/23
>
> Point:

[TOC]

## 基础介绍

### 关键字

```
关键字:
	break:
	false:
	in:
	true:
	
```







### 数据类型

```
数据类型:
	Any:
	Unit:
	---
	Boolean:
	Byte:
	Int:
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
```



#### 字符串

```
"字符串"


"""
	多行字符串
"""
```





#### 范围

```
// Range
'a' .. 'c'

1 .. 10 step 2

1 until 10

10 downTo 1
```











### 变量

#### var



#### val



### 流程控制

#### if



#### when

```
when (x) {
	is Int -> {
		xxx
	}
	in 1 .. 10 -> {
		xxx
	}
	else -> {
		xxx
	}
}
```



#### while



#### for

```
for (i in arr) {
	
}
```









### 函数

```
fun main() {}
```



#### lambda

##### it



##### run



#### 泛型



#### vararg





### 面向对象

#### class

```
class Xxx(xxx: Int) {
	var xxx: Int = 1
	private get() = field
	set(value) {
		field = value
	}
	
	fun xxx() {}
	
	constructor() {}
	init {}
}
```



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





#### interface



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











