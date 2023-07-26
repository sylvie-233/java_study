# Spring

> Author: Sylvie233
>
> Date: 23/7/26
>
> Point:
>
> ​	Spring6教程P24

[TOC]

## 基础介绍

Spring Framework轻量级开源框架

IOC、AOP

非侵入式

![image-20230726220305628](Spring.assets/image-20230726220305628.png)

![image-20230726220503818](Spring.assets/image-20230726220503818.png)

![image-20230726220543953](Spring.assets/image-20230726220543953.png)

![image-20230726220622528](Spring.assets/image-20230726220622528.png)

![image-20230726220658616](Spring.assets/image-20230726220658616.png)





Spring6最低要求JDK17















## 核心内容

### Spring

#### beans.xml

```
<beans>
	<bean
		id:
        class:
	>
		<property
			name:
			value:
			ref: 引用外部Bean
		>
			<value>
				![CDATA[ ... ]]: 特殊字符
			<null>
		<constructor-arg
			name:
			index:
			value:
		>
```



#### 注解

```
:
	
```









#### IoC

DI（依赖注入）实现了IoC（控制反转）

setter注入、构造注入



bean生命周期

![image-20230727000555649](Spring.assets/image-20230727000555649.png)









#### AOP



















## API

```
org.springframework:
	beans:
		factory:
			config:
				BeanDefinition: Bean定义信息
			support:
				BeanDefinitionReader:
			xml:
            	XmlBeanDefinitionReader: Bean加载器
            BeanFactory:
	context:
		support:
			ClassPathXmlApplicationContext: 基于类路径获取xml文件
			DefaultListableBeanFactory:
		ApplicationContext: Bean上下文
			getBean():
```







