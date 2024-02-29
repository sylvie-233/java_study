# Android逆向

> Author: Sylvie233
>
> Date: 2023/12/31
>
> Point:  


## 基础介绍



JVM、Dalvik、ART虚拟机




## 核心内容

### smali

```
---关键字
	.class:
	.field:
	.line:
	.method:
		.end method
	.parameter:
	.prologue:
	.registers:
		v0/v1/v2: 本地寄存器
		p0/p1/p2: 参数寄存器
	.source:
	.super:
	private:
	protected:
	public:

---数据类型
	B: byte
	C: char
	D: double
	F: float
	I: int
	J: long
	L_XXX/XXX: 自定义对象
	S: Short
	V: void
	Z: boolean 
	string: String

---常用指令
	const: 寄存器赋值
		const-string:
		const-wide:
	goto:
	if-eq: 条件跳转
	iget: 获取寄存器数据
	invoke: 调用函数
			invoke-direct:
		invoke-static:
		invoke_virtual:
	move-result:
		move-result-object:
	return: 方法返回值
	switch:
```



Dalvik的寄存器语言、由dex反编译而来的