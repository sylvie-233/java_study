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

```
org.springframework.boot:
	autoconfigure:
		web:
			servlet:
				
		SpringBootApplication:
	SpringApplication:
```







## 第三方库









