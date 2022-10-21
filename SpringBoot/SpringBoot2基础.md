# SpringBoot2基础

Sylvie233的SpringBoot2学习~~~

> Author: Sylvie233
>
> Date: 2022/10/17



>Update: 2022/10/21
>
>Point: 

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
    
    @Bean
    public ServletRegistrationBean servletRegistrationBean() {
        ServletRegistrationBean bean = new ServletRegistrationBean(new MyServlet, "/xxx")
            
            
     	bean.setServlet(new MyServlet())
            .addUrlMappings("/xxx")
            .
            
        return bean
    } 
    
    @Bean
    public FilterRegistrationBean filterRegistrationBean() {
        FilterRegistrationBean bean = new FilterRegistrationBean()
            
            
     	bean.setFilter(new MyFilter())
            .addUrlPatterns("/xxx/*")
            
        return bean
    }
}
```



Restful API

表现层状态转移

资源用url名词表示，动作用http请求方式表示

form其它类型请求方式：

过滤器转换请求方式：HiddenHttpMethodFilter

```xml
<input type="hidden" name="_method" value="put" />
```





动态路由

```
"/xxx/{id}""

""
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



### Servlet

HttpServlet

```java
public class MyServlet extends HttpServlet {
	protected void doGet()
}
```



注册Servlet



### Filter

实现Filter接口

```java
public class MyFilter implements Filter {
    public void doFilter(ServletRequest req, ServletResponse resp, FilterChain chain) {
        
    }
}
```



注册Filter



CharacterEncodingFilter

springmvc提供的类

```java
CharacterEncodingFilter filter = new CharacterEncodingFilter()

filter.setEncoding("utf-8")
      .setForceEncoding(true)
      .
```

字符编码默认ISO-8859-1







### 事务

@Transactional











## SpringBoot常用第三方库

### Thymeleaf模板集成

Java模板引擎



安装依赖

```
Thymeleaf依赖
	org.springframework.boot
		spring-boot-starter-thymeleaf

Thymeleaf依赖
	1.thymeleaf-spring5
	2.thymeleaf
```



html引入th命名空间

```html
<html xmlns:th="http://www.thymeleaf.org">
</html>
```





模板引擎可以从Request作用域中获取数据



使用Model存放数据

```
model.addAttribute("key", val)
```



表达式

\[\[$key]]

request作用域中的key

使用Request或Model设置

```html
${key}
[[${key}]]

<div th:object="${obj}">
	*{key}    
</div>

<div th:text="${key}">
    
@{url}
@{/xxx(id=${xxx},)}
    
model.addAttribute("Key", val)
    

```



Thymeleaf属性

1.th:text

2.th:style

3.th:each

```html
<div th:each="item, stat : ${items}">
    
</div>

stat变量
	1.index
	2.count
	3.size
	4.current
	5.even/odd
	6.first/last

map_item变量
	1.key
	2.value
```

4.th:if/

```

```

5.th:unless

6.th:switch/th:case

```html
<div th:switch="${xxx}">
    <div th:case="val1">
        
    </div>
</div>

th:case="*"
```

7.th:inline

```
th:inline="text"

th:inline="javascript"
```



字面量

- 字符串
- 数字
- 布尔
- null



运算符

||

```html
<div th:text="|${xxx}|">
    
</div>
```

gt、lt、ge、le、eq、ne

三元运算符：?:





内置对象

1.#request/request

HttpservletRequest



2.#session/session

HttpSession

session: 简化形式Map



3.param





4.#ctx



5.application



6.#execInfo

```java

```



7.dates

```java
#dates.format(date)
    .year(date)
    .month(date)
    .monthName(date)
    .createNow()
    .
```



8.#numbers

```java
#numbers.formatCurrency(num)
    .formatDecimal(num, 5, 2)
    .
```





9.#strings

```java
#strings.toUpperCase(str)
    .indexOf(str, pat)
    .subString(str, 2, 5)
    .concat(str1, str2)
    .length(str)
    .isEmpth(str)
    .
```





10.#lists

```java
#lists.size(list)
    .contains(list, el)
    .isEmpth(list)
    .
```



非空处理

?.



自定义模板

th:fragment

```html
<div th:fragment="name">
    
</div>
```



th:insert

```html
<div th:insert="~{ tmlName :: selector }">
    
</div>



~{templatename :: selector}
	文件名称：name

th:insert="~{ dir/name :: selector }"
```



th:include

```
<div th:include="~{ tmlName :: selector }">
    
</div>

th:include="~{ name :: html}"
th:include="~{ name }"
```





















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



War包部署

主启动类继承SpringBootServletInitializer

```java
@SpringBOotApplication
public class MyApp extends SpringBootServletInitializer {
    public static void main(String[] args) {
        
    }
    
    protected SpringApplicationBuilder configure(SpringApplicationBuilder builder) {
        builder.sources(MyApp.class)
            
         
    }
}
```













### MyBatis集成

安装依赖

```
mysql驱动依赖
	mysql
		mysql-connector-java
			runtime
		
mybatis依赖
	org.mybatis.spring.boot
		mybatis-spring-boot-starter
			2.1.4 

mybaits依赖
	1.spring-boot-starter-jdbc
		HikariCP
	2.mybatis
	3.mybattis-spring
```



Dao层

@Mappper/@MapperScan





Mapper文件

打包时引入.xml文件

```
<build>
	<resources>
		<resource>
			<directory>src/main/java
			<includes>
				<include>**/*.xml
```



事务

DataSourceTransactionManager



MyBatis逆向工程

生成model、dao、mapper





### Redis集成

安装依赖

```
redis依赖
	org.springframework.boot
		spring-boot-starter-data-redis
		
redis依赖
	1.lettuce-core
	2.
```



RedisTemplate

```java
@Resource 
public RedisTemplate redisTemplate;

redisTemplate.setKeySerializer(new StringRedisSerializer())
    .setValueSerializer(new StringRedisSerializer())
    .


```



StringRedisTemplate

对key和value使用String的序列化

```
@Resource 
public StringRedisTemplate stringRedisTemplate;

stringRedisTemplate.
```





ValueOperations

```java
ValueOperations vops = redisTemplate.opsForValue()
    
vops.set("k", "v")
   .get("k")
   .
```



序列化处理

RedisTemplate默认使用JDK的序列化机制

Json序列化：Jackson2JsonRedisSerializer



### Dubbo集成

Java RPC框架



安装依赖

```
dubbo依赖
	org.apache.dubbo
		dubbo-spring-boot-starter
			2.7.8

dubbo-zookeeper依赖
	org.apache.dubbo
		dubbo-dependencies-zookeeper
			2.7.8
			<exclusion>
				slf4j-log4j12
					org.slf4j


```



公共依赖：接口interface项目

zookeeper注册中心

提供者、消费者

排除log4j依赖





provider提供者

接口实现

@DubboService暴露接口

@EnableDubbo



consumer消费者

@DubboReference获取Service

































## SpringBoot常用API

### 1.SpringApplication

```
ConfigurableApplicationContext ctx = SpringApplication.run(Xxx.class, args)

ctx.getBean("id")
```



### 2.HttpServletRequest/HttpServletResponse

```java
req.setAttribute("key", val)
    .getAttrivute("key")
    .getRequestURL()
    .getRequestURI()
    .getServerName()
    .getQueryString()
    .getContextPath()
    .getServerPort()
    .

resp.setContentType()
    .getWriter()
    .
```







### 3.Model/ModelAndView/

```java
model.addAttribute(k, v)
	 .
	 
ModelAndView mv = new ModelAndView()
mv.setViewName("xxx")
    .addObject("k", val)
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



### 9.HttpServlet



### 10.Filter



### 11.HttpSession

```java
session.geteId()
    .
```





### 12.









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





### 17.@Transactional



### 18.@EnableTransactionManager



### 19.@PathVariable



### 20.@GetMapping/@PostMapping/@PutMapping/@DeleteMapping



### 21.@RestController

@Controller+@ResponseBody



### 22.@Repository



### 23.@Autowired



### 24.@Qualifer



### 25.@ControllerAdvice



### 26.@ExceptionHandler



























### MyBatis常用注解

### 1.@Param



### 2.@Mapper



### 3.@MapperScan

```
@MapperScan(
	basePackages = "",
)
```





### Dubbo常用注解

### 1.@DubboService

```
@DubboService(
	interfaceClass = Xxx.class,
	version = "1.0"
)
```



### 2.@EnableDubbo



### 3.@DubboReference

```
@DubboReference(
	interfaceClass = Xxx.class,
	version = "1.0"
)
```















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
		encoding:
			enabled: true
			charset: utf-8
			force: true 					# 强制req,resp使用
			

spring:
	application:
		name: xxx
	profile:
		active: dev
		
	mvc:
		view:
			prefix: /
			suffix: .jsp
        hiddenmethod:
        	filter:
        		enabled: true
	
	datsource:
		driver-class-name: com.mysql,cj.jdbc.driver
		url: jdbc:mysql://localhost:3306/mydb?useUnicode=true&characterEncoding=UTF-8&serverTimezone=
		username: root
		password: 123456
	
	redis:
    	host: localhost
    	port: 6379
    
    thymeleaf:
    	cache: false
    	encoding: utf-8
    	mode: HTML
    	prefix: classpath:/templates
    	suffix: .html
    
mybatis:
	mapper-locations: classpath:mapper/*.xml
	configuraion:
		log-impl: com.xxx.Xxx
		
dubbo:
	scan:
		base-packages: com.xxx
	protocol:
		name: dubbo
		port: 20881
	registry:
		address: zookeeper://localhost:2181
```





## SpringBoot项目部署

### jar包生成

maven插件

```
<build>
	<plugins>
		<plugin>
			org.springframework.boot
				spring-boot-maven-plugin
					1.4.2.RELEASE #有jsp时必须为此版本
					

```



运行jar包

`java -jar xxx.jar`







