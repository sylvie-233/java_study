# SpringBoot3

> Author: Sylvie233
>
> Date: 23/7/28
>
> Point:
>
> ​	SpringBoot3教程：P3


## 基础介绍

### 自动装配

自动配置的Selector在**解析@Configuration注解时执行**

![c4625778890d4c988aff59409b4afedd](SpringBoot3.assets/c4625778890d4c988aff59409b4afedd.png)





#### starter

`spring-boot-starter`、`spring-boot-autoconfigure`

条件注解开启starter功能







#### 构造

![image-20230730165604490](SpringBoot3.assets/image-20230730165604490.png)

![image-20230730165813484](SpringBoot3.assets/image-20230730165813484.png)

添加Bean来源、在初始化器中扩展Application、初始化Application监听器











#### run()

![image-20230730180625814](SpringBoot3.assets/image-20230730180625814.png)

![image-20230730180721672](SpringBoot3.assets/image-20230730180721672.png)

![image-20230730181948573](SpringBoot3.assets/image-20230730181948573.png)









##### ApplicationEvent

Application事件发布（7个事件）

![image-20230730173057520](SpringBoot3.assets/image-20230730173057520.png)

![image-20230730173604535](SpringBoot3.assets/image-20230730173604535.png)

##### ApplicationListener









##### ApplicationEnvironment

准备Application环境配置













![](SpringBoot3.assets/09b4bf16ecc54f128a73e09e99beca52.png)

![img](SpringBoot3.assets/1242355-20220420144442818-645855383.png)





















##### SpringMVC

![](SpringBoot3.assets/1255094-20190418171910471-271294354.png)

![](SpringBoot3.assets/6f75367ab6e8165e950686cf8774f705.png)



##### Runner

Application启动后执行自定义任务









## 核心内容
API
```
jakarta:
	persistence:
		Column: 数据库字段映射
		Entity: JPA实体类
		GeneratedValue: key自增
		Id: 
		Table: 映射数据库表
	validation:
		ConstraintViolationException:
org.springframework
	boot:
		autoconfigure:
			web:
				servlet:
					
			SpringBootApplication:
		SpringApplication:
	data:
		jpa:
			repository:
				JpaRepository:
	securiry:
		core:
			context:
				SecurityContextHolder:
			userdetails:
				User:
	validation:
		annotaion:
			Validated:
	web:
		bind:
			annotation:
				ControllerAdvice:
				ExceptionHandler:
				ResponseBody:
```

配置
```yaml
spring:
	datasource:
		url:
		username:
		password:
		driver-class-name:
	jpa:
		hibernate: 
			ddl-auto: update|validate|
		show-sql: true
	mvc:
		throw-exception-if-no-handler-found: true
	security:
		user:
			name:
			password:
			roles:
	web:
		resources:
			add-mappings: false
			static-locations: classpath:/xxx

server:
	port:
```



### 拦截器



### 异常处理



### 模板引擎



### Runner


### Listener








## 第三方库


### SpringSecurity

认证授权框架




### spring-boot-starter-validation

接口数据校验框架



@Validated标注控制器、@Valid标注实体类参数



### springdoc

接口文档生成Swagger

依赖
```yaml
org.springdoc:
	springdoc-openapi-starter-webmvc-ui:
		2.1.0
```

API
```yaml
 io.swagger.v3.oas:
	 annotaions:
		 media:
			 Schema: 标注实体类
		 responses:
			 ApiResponse:
			 ApiResponses: 标注控制器返回参数信息
		 tags:
			 Tag: 标注控制器信息
		 Operation: 标注控制器方法
		 Parameter: 标注控制器方法参数	
```

自定义OpenAPI填写相关配置信息


### spring-boot-starter-actuator

项目运行监控




### spring-boot-starter-jdbc



### spring-boot-starter-data-jpa

持久层ORM框架


JpaRepository<Entity,ID>

条件判断函数：Repository接口方法名称自动生成

关联查询：对象依赖
```
:
	@OneToOne: 一对一
	@OneToMany: 一对多
	@ManyToOne: 多对一
	@ManyToMany: 多对多
		@JoinColumn: 关联字段外键
		@JoinTable: 中间关联表
```


自定义SQL语句
Repository注解接口方法
```
:
	@Modifying:
	@Param: 设置SQL参数
	@Query:
	
```



### mybatis-plus-boot-starter

依赖
```yaml
com.baomidou:
	mybatis-plus-boot-starter:
		3.5.3
```


注解标注
```
:
	@TableName:
	@TableField:
```


BaseMapper<Entity>
Wrapper条件拼接
分页查询

IService、ServiceImpl



代码生成器
