# Spring

> Author: Sylvie233
>
> Date: 23/7/26
>
> Point:
>
> ​	Spring6教程：P32
>
> ​	SSM练手小项目：P33
>
> ​	Spring5底层教程：P89

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

ApplicationContext、BeanFactory



BeanFactory后置处理器解析注解（注入容器）：@Configuration、@Autowired、@Resource、

![image-20230728162222773](Spring.assets/image-20230728162222773.png)

![image-20230728170058282](Spring.assets/image-20230728170058282.png)

![image-20230728183335782](Spring.assets/image-20230728183335782.png)



@Lazy单例对象解决办法：使用代理创建对象

![image-20230728185717407](Spring.assets/image-20230728185717407.png)



Bean：创建、依赖注入、初始化





















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
			<bean>: 内部Bean
			<array>
				<value>
			<list>
				<ref
					bean
				>
			<map>
				<entry>
					<key>
						<value>
					<value>
					<ref bean>
		<constructor-arg
			name:
			index:
			value:
		>
	<context:>
		annotaion-config:
		conponet-scan: 组件扫描
		property-placeholder: 引入外部properties文件
			location:
	<p:>: property属性快速赋值
	<util:>
		list:
			<ref>
		map:
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

Aspect（切点、通知、切面）、Advisor切面（Pointcut、advice）、Pointcut、MethodInterceptor、

Aspect（多切点通知）->Advisor（单切点通知）->MethodInterceptor环绕通知调用链（MethodInvocation）

切点表达式：execution、@annotation、args、逻辑表达式



静态调用、动态调用

























### SpringMVC

![image-20230729055625071](Spring.assets/image-20230729055625071.png)

#### DispatcherServlet

onRefresh()初始化：

![image-20230729140624462](Spring.assets/image-20230729140624462.png)



`DispatcherServlet.properties`：默认九类组件实现







#### RequestMappingHandlerMapping

处理请求路径映射









#### RequestMappingHandlerAdapter

调用控制器方法（HandlerExecutionChain）

方法参数解析器、返回值处理器





类型转换

![image-20230729171954978](Spring.assets/image-20230729171954978.png)

Binder









#### web.xml

```
<web-app>
	<listener>
		<listener-class>
			org.springframework.web.context.ContextLoaderListener
	<context-param>
		<param-name>
			contextConfigLocation
		<param-value>
			classpath:application.xml: 加载Spring Bean核心
	<servlet>
		<servlet-name>
		<servlet-class>
			org.springframework.web.servlet.DispatcherServlet
		<init-param>
			<param-name>
				contextConfigLocation
			<param-value>
				加载MVC xml配置
		<load-on-startup>
			1
	<servlet-mapping>
		<servlet-name>
		<url-pattern>
			/
```

Tomcat的war项目启动配置文件



##### application.xml

```
<beans>
	<context:component-scan base-package />
	
	<bean id="multipartResolver" />
	
	<bean class="org.springframework.web.servlet.handler.BeanNameUrlHandlerMapping" />
	<bean class="org.springframework.web.servlet.mvc.SimpleControllerHandlerAdapter" />
	<bean class="org.springframework.web.servlet.view.InternalResourceViewResolver" id="internalResourceViewResolver">
		<property name="prefix"/>
		<property name="suffix"/>
		
	<mvc:annotaion-driven>
		<mvc:message-converters>
			<bean>: 自定义Json转换
			
	<mvc:interceptors>
		<mvc:interceptor>
			<mvc:mapping path>
			<mvc:exclude-mapping path>
			<bean>
			
	<context:annotation-config /> 添加默认BeanFactory后置处理器（5个）
	<context:property-placeholder location>
	<mybatis:scan base-package>
	<bean id="dataSource">
	<bean id="sqlSessionFactory">
	<bean id="transactionManager">
	
	<tx:advice id="txAdvice" transaction-manager="transactionManager">: 声明式事务
		<tx:attributes>
			<tx:method name propagation>
		
	<aop:aspectj-autoproxy />
```



#### 字段校验

@Validated、BindingResult（获取校验结果）



#### 拦截器











## API

```
org.springframework:
	aop:
		aspectj:
			annotation:
				AnnotationAwareAspectJAutoProxyCreator: (Bean后置处理器)
					findEligibleAdvisors(): 查找对象可用的Advisor
					wrapIfNecessary(): 创建代理
			AspectJAroundAdvice:
			AspectJExpressionPointcut:
				matches():
				setExpression():
			AspectInstanceFactory:
				
			AspectJMethodBeforeAdvice:
			InstantiationModelAwarePointcutAdvisor:
			SingletonAspectInstanceFactory:
				
		framework:
			adapter:
				AfterReturningAdviceInterceptor:
				MethodBeforeAdviceInterceptor:
				
			autoproxy:
				
			ProxyFactory:
                addAdvisor():
                getProxy():
                getInterceptorsAndDynamicInterceptionAdvice():
                setInterfaces():
                setProxyTargetClass():
				setTarget():
			ReflectiveMethodInvocation:
		interceptor:
			ExposeInvocationInterceptor:
				ADVISOR:
		support:
			AnnotationMatchingPointcut:
			ComposablePointcut:
			ControlFlowPointcut:
			DefaultPointcutAdvisor:
			ExpressionPointcut:
			StaticMethodMatcherPointcut:
		Advisor:
		Pointcut:
			getClassFilter():
			getMethodMatcher():
	asm:
		AnnotationVisitor:
		ClassWriter:
		FieldVisitor:
		MethodVisitor:
		Opcodes:
			
	beans:
		factory:
			annotatin:
				AutowiredAnnotatinBeanPostProcessor: Bean后置处理器
					getOrder(): 处理器顺序
					postProcessProperties():
					setBeanFactory():
				InjectionMetadata:
					inject(): 注入容器
				Value:
			config:
				BeanDefinition: Bean定义信息
				BeanFactoryPostProcessor: BeanFactory后置处理器(context.refresh()时执行)
					postProcessBeanFactory():
				DependencyDescriptor: 注解字段依赖封装
				DestructionAwareBeanPostProcessor:
				InstantiationAwareBeanPostProcessor:
					postProcessBeforeDestruction():
					postProcessBeforeInstantiatin():
					postProcessProperties(): 解析依赖注入注解
			support:
                BeanDefinitionBuilder:
                	addConstructorArgValue():
                	genericBeanDefinition():
                	getBeanDefinition():
                	setAutowireMode(): 自动装配模式
                	setFactoryMethodOnBean():
                	setInitMethodName():
                    setScope():
				BeanDefinitionReader:
				BeanDefinitionRegistry:
				BeanDefinitionRegisterPostProcessor:
					postProcessBeanDefinitionRegistry():
				BeanNamGenerator:
					generateBeanName():
				DefaultBeanNamGenerator:
				DefaultListableBeanFactory:
					addEmbeddedValueResolver():
					doResolveDependency(): 注入依赖解析
					registerBeanDefinition():
					registerSingleton():
					setAutowireCandidateResolver():
				DefaultSingletonBeanRegistry:
			xml:
            	XmlBeanDefinitionReader: Bean加载器
            BeanFactory:
                addBeanPostProcessor(): 添加Bean后置处理器（注解解析）
            	containsBean():
            	getBean():
            	getBeansOfType():
            	getDependencyComparator():
            	isSingleton():
            	preInstantiateSingletons(): 预生成单例Bean实例
            BeanNameAware:
            	setBeanName():
            InitializingBean:
            	afterPropertiesSet():
            ObjectFactory:
    	BeanWrapperImpl:
    		setPropertyValue():
    	DirectFieldAccessor:
    		setPropertyValue():
    	SimpleTypeConverter:
    		convertIfNecessary():
	boot:
		autoconfigure:
			web:
				format:
					WebConversionService:
				servlet:
					DispatcherServletRegistrationBean:
						setLoadOnStartup():
		context:
			properties:
				ConfigurationProperties:
				ConfigurationPropertiesBindingPostProcessor:
					register():
		convert:
			ApplicationConversionService:
				
		web:
			servlet:
				context:
					AnnotaionConfigServletWebServerApplicationContext: 基于Web注解（ServletWebServerFactory、DispatcherServlet、DispatcherServletRegistraionBean（注册到Server））
				HandlerMapping:
					
	cache:
		interceptor:
			CacheOperationSourcePointcut:
	cglib: 父子代理
		core:
			Signature:
				
		proxy:
			Enhancer:
				create():
			MethodInterceptor:
				intercept():
			MethodProxy:
				create():
				---
				invoke():
				invokeSuper():
		reflect:
			FastClass:
				
	context:
		annotation:
			AnnotationBeanNameGenerator:
			AnnotationConfigApplicationContext: 基于注解配置类
			AnnotationConfigUtils:
				registerAnnotationConfigProcessors(): 给BeanFarcory添加注解解析扩展
			Configuration: 配置类
			Bean: Bean类
			ComponentScan:
				Filter:
			ConfigurationClassPostProcessor: （@ComponentScan、@Import）
			FilterType:
			internalAutowireAnnotationProcessor: 注解解析处理器
				postProcessBeanFactory(): 为BeanFactory中的Bean解析注解
			internalCommonAnnotationProcessor:
			internalConfigurationAnnotationProcessor:
			Lazy:
			Scope: Bean作用域
				proxyMode:
				---
				request:
				session:
				application:
				
		event:
			EventListener:
			internalEventListenerFactory:
			internalEventListenerProcessor:
		support:
			
			ClassPathXmlApplicationContext: 基于类路径获取xml文件
			FileSystemXmlApplicationContext: 基于磁盘路径获取xml文件
            GenericApplicationContext:
            	close(): 销毁容器
            	getDefaultListableBeanFactory():
            	getResources():
            	registerBean(): 注册Bean
            	refresh():  初始化容器（执行BeanFactory后置处理器、添加Bean后置处理器、初始化所有单例）
            	
		ApplicationContext: Bean上下文
			getBean():
			getBeanFactory():
			getEnvironment(): 环境变量
			getMessage():
			getResources():
			publishEvent():
		ApplicationAware:
			setApplicationContext():
		ApplicationEvent:
		ApplicationEventPublisher:
			publishEvent():
		ConfigurableApplicationContext:
			getBeanDefinitionNames():
		MessageSource: 国际化信息
			getMessage():
	core:
		annotation:
			AliasFor:
			AnnotatinUtils: 注解工具类
				findAnnotation():
			AnnotationAwareOrderComparator:
			MergedAnnotations:
				from():
				isPresent():
			Order:
		env:
			EnvironmentCapable:
		io:
			PathMatchingResourcePatternResolver:
				getResources():
		type:
			classreading:
				CachingMetadataReaderFactory:
					getMetadataReader():
				
				MetadataReader:
					getClassMetadata():
						getClassName():
					getAnnotationMetadata():
						getAnnotatedMethods():
						hasAnnotation():
						hasMetaAnnotation():
			ClassMetadata:
					isInterface():
            MethodMetadata:
                getAnnotationAttributes():
        DefaultParameterNamDiscoverer:
       	GenericTypeResolver:
       		resolveTypeArgument():
       		resolveTypeArguments():
        LocalVariableTableParameterNameDiscoverer:
        	getParameterNames():
        MethodParameter:
        	getMethodAnnotation():
        	getMethodAnnotations():
        	getParameterAnnotation():
        	getParameterAnnotations():
        	getParameterIndex():
        	getParameterType():
        	initParameterNameDiscovery(): 参数名
	data:
		domain:
			Page:
			PageRequest:
	format:
		annotation:
			DateTimeFormat: 日期转换注解
				
		support:
			DefaultFormattingConversionService:
				
			FormattingConversionService:
				addFormatter():
			FormattingConversionServiceFactoryBean:
		Formatter:
			parse():
			print():
	http:
		converter:
			json:
				MappingJackson2HttpMessageConverter:
					
		ResponseEntity:
	stereotype:
		Component: 组件
	transaction:
		annotation:
			Transactional:
	util:
		AnPathMatcher:
			extractUriTemplateVariables():
	validation:
		annotation:
			Validated: 字段校验注解
		BindingResult:
			getAllErrors():
		BeanPropertyBindingResult:
		BindingResult:
		DataBinder:
			bind():
			initDirecFieldAccess():
		MutablePropertyValues:
        	add():
	web:
		bind:
			annotaion: WEB注解
				CrossOrigin: 跨域处理
				GetMapping:
				InitBinder: 初始化绑定器WebDataBinder
				RequestBody:
				ResponseBody:
				RestController:
				Validated:
			support:
				ConfigurableWebBindingInitializer:
					setConversionService():
				DefaultDataBinderFactory:
				WebDataABinderFactory:
			ServletRequestDataBinder:
				bind():
			ServletRequestParameterPropertyValues:
            WebDataBinder:
            	addCustomFormatter(): 添加自定义格式类型转换器
		client:
			RestTemplate:
				getForEntiry():
		context:
			request:
				NativeWebRequest:
					getHeader():
					getNativeResponse():
		method:
			annotation:
                RequestHeaderMethodArgumentResolver: @RequestHeader解析
				RequestHeaderMapMethodArgumentResolver:
				RequestParamMethodArgumentResolver: @RequestParam解析
					resolveArgument():
					supportsParameter():
				RequestParamMapMethodArgumentResolver:
			support:
				HandlerMethodArgumentResolver: 方法参数解析器
					resolveArgument():
					supportsParameter():
                HandlerMethodArgumentResolverComposite:
                	addResolvers():
				HandlerMethodReturnValueResolver:
					handleReturnValue():
					supportsReturnType():
				ModelAndViewContainer:
					getModel():
                	setRequestHandled():
			HandlerMethod:
				getMethodParameters():
		servlet:
			mvc:
				method:
					annotation:
						PathVariableMethodArgumentResolver: @PathVariable解析
						PathVariableMapMethodArgumentResolver:
						RequestMappingHandlerAdapter:
							getArgumentResolvers():
							getReturnValueHandlers():
							invokeHandlerMethod():
							setCustomArgumentResolvers():
						RequestMappingHandlerMapping:
							getHandler():
							getHandlerMethods():
						RequestResponseBodyMethodProcessor:
						ServletModelAttributeMethodProcessor:
						ServletRequestDataBinderFactory: 参数绑定工厂
							createBinder():
						ServletRequestMethodArgumentResolver:
						ServletReponseMethodArgumentResolver:
					RequestMappingInfo:
                    	
				Controller:
					handleRequset():
			DispatcherServlet:
				onRefresh():
			HandlerExecutionChain:
				getHandler():
			HandlerInterceptor:
				preHandle():
				postHandle():
				afterCompletion():
			HandlerMapping:
				URI_TEMPLATE_VARIABLES_ATTRIBUTE:
	

		
	
org.aopalliance:
	aop:
		Advice:
	intercept:
		MethodInterceptor:
			invoke():
		MethodInvocation:
			proceed():
org.aspectj:
	lang:
		annotation:
			After:
			Aspect: AOP注解
			Before:
			Pointcut:

com.alibaba.druid:
	pool:
		DruidDataSource:
```







