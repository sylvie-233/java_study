# SpringBoot2基础

Sylvie233的SpringBoot2学习~~~

> Author: Sylvie233
>
> Date: 2022/10/17



>Update: 2022//19
>
>Point: 动力节点SpringBoot教程P33

[TOC]

## SpringBoot介绍

Spring容器（IOC容器）



内嵌服务器

Tomcat



starter起步依赖



Spring初始化器

https://start.spring.io

https://start.springboot.io





项目配置

application.properties/application.yml











## SpringBoot基础

### JavaConfig

Spring上下文依赖

```
org.springframework
	spring-context
		5.3.1
		
		
context包依赖：
	1.spring-aop
	2.spring-beans
	3.spring-core
	4.spring-expression
```



xml配置注入

```xml
<beans>
	<bean>
    	<property />
    </bean>
</beans>
```

读取xml配置：

实例化应用上下文

```java
ApplicationContext ctx = new ClassPathXmlApplicationContext("beans.xml")

ctx.getBean("bean_id")
```





@configuration配置注入

@Bean中的方法名为bean_id

```java
@Configuraion
public class MyConfig {
	@Bean
    public Student createStudent() {
        return new Student();
    }
}


ApplicationContext ctx = new AnnotaionConfigApplicationContext(MyConfig.class)
    
ctx.getBean("方法名")

```





### Maven配置

pom.xml

```

```



### Spring Web

依赖

```
<parent>
	org.springframework.boot
		spring-boot-starter-parent
			2.4.2
			
web依赖
	ort.springframework.boot
		spring-boot-starter-web
web依赖
	1.spring-boot-starter
		spring-boot-starter-json
	2.spring-web
		spring-core
		spring-beans
		spring-aop
		spring-context
		spring-expression
	3.spring-webmvc
	4.spring-boot-starter-tomcat
		tomcat-embed-core

测试依赖
	org.springframework.boot
		spring-boot-starter-test
			test

```



项目目录

/src

1. /main
   - /java
   - /resources
     - 
2. /test

pom.xml



多环境配置

application.properties/application.yml

application-{profile}.properties/application-{profile}.yml



应用配置

WebMvcConfigurer接口

```java
@Configuration
public class MyAppConfig implements WebMvcConfigurer {
    void addInterceptors(InterceptorRegistry registry) {
        registry.addInterceptor(myInterceptor)
            	.addPathPatterns()
            	.exlcudePathPatterns()
    }
}
```







### Runner接口

run()方法，类似钩子函数

CommandLineRunner

容器已经创建好了



ApplicationRunner





### 拦截器

拦截Controller中的请求

实现HandlerInterceptor接口

```
class MyInterceptor implements HandlerInterceptor {
	public boolean preHandler(HttpServletRequest req, HttpServletResponse resp, Object handler) {
		
	}
}
```



配置拦截器













## SpringBoot常用第三方库

### JSP集成

依赖

```
负责编译JSP
	org.apache.tomcat.embed
		tomcat-embed-jasper

servlet依赖
	javax.servlet
		javax.servlet-api
	javax.servlet.jsp
		javax.servlet.jsp-api
			2.3.1

jstl依赖
	javax.servlet
		jstl
```



jsp存放目录：/resources同级

/webapp

- 



配置视图解析器



jsp编译配置

```
<build>
	<resources>
		<resource>
			<directory>src/main/webapp
			<targetPath>META-INF/resources
			<includes>
				<include>**/*.*
			
```



































## SpringBoot常用API

### 1.SpringApplication

```
ConfigurableApplicationContext ctx = SpringApplication.run(Xxx.class, args)

ctx.getBean("id")
```



### 2.HttpServletRequest/





### 3.Model/

```
model.addAttribute(k, v)
	 .
	 
	 

```





### 4.ApplicationContext/ConfigurableApplicationContext



### 5.CommandLineRunner





### 6.ApplicationRunner





### 7.HandlerInterceptor

```
interface HandlerInterceptor {
	default
	default
	default
}
```





### 8.WebMvcConfigurer



### 9.



## SpringBoot常用注解

### 1.@Configuration



### 2.@Bean

```
@Bean(
	name,
	
)
```



### 3.@ImportResource

导入Xml配置

```
@ImportResoure(
	value = "classpath:xxx.xml"
	value = {多个值,}
)

<import resources="其他配置文件" />
```



### 4.@PropertySource

读取.properties属性配置

```
@PropertySource(
	
)

<context:property-placeholder location="" />
```



### 5.@Value

```
@Value(
	"${xxx.xxx}"
)
```



### 6.@Component

```
@Component(
	value
)
```



### 7.@ComponentScan

组件扫描注入

```
@ComponenetScan(
	basePackages = "com.xxx",
	exludeFileters = {
		@Filter(
			type,
			classes = {}
		)
	}
)

<context:component-scan base-package="" />
```





### 8.@SpringBootApplication

```
@SpringBootApplication(
	
)


嵌套(复合注解)
	1.@SpringBootConfiguraion
	2.@EnableAutoConfiguraion
	3.@ComponentScan
```







### 9.@Contoller

```

```



### 10.@RequestMapping



### 11.@ResponseBody



### 12.@SpringBootConfiguraion

```


复合注解
	1.@Configuraion
```







### 13.@EnableAutoConfiguraion

启用自动配置

```



```



### 14.@ConfigurationProperties

属性映射类

```
@ConfiguraionProperties(
	prefix = "",
	
)

getter/setter方法

```

Configuration元数据

```
依赖
	org.springframework.boot
		spring-boot-configuraion-processor
			true
			
为自定义的Properties类添加提示功能
```







### 15.@Resource



### 16.@Service





### 17.





## SpringBoot常用配置

application.properties

```properties
server.port=8088
server.servlet.context-path=/xxx

spring.profiles.active=dev

```



application.yml

```yaml
server:
	port: 8088
	servlet:
		context-path: /xxx

spring:
	profile:
		active: dev
		
	mvc:
		view:
			prefix: /
			suffix: .jsp
			
```







