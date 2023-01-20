# SpringSecurity基础

> Author: Sylvie233
>
> Date: 23/1/17
>
> Point: P72

[TOC]

## 基础介绍

<img src="SpringSecurity.assets/image-20230117134704969.png" alt="image-20230117134704969" style="zoom:67%;" />

依赖：

```
org.springframework.boot
	spring-boot-starter-security
```



Filters实现：

<img src="SpringSecurity.assets/image-20230117141509143.png" alt="image-20230117141509143" style="zoom:67%;" />

默认filters

```
filters:
	WebAsyncManagerIntegrationFilter
	SecurityContextPersitenceFilter
	HeaderWriterFilter
	CsrfFilter
	LogoutFilter
	UsernamePasswordAuthenticationFilter
	DefaultLoginPageGenerationFilter
	DefaultLogoutPageGeneratingFilter
	BasicAuthenticationFilter
	RequestCacheAwareFilter
	SecurityContextHolderAwareRequestFilter
	AnonymousAuthenticationFilter
	SessionManagementFilter
	ExceptionTransiationFilter
	FilterSecurityInterceptor
```



默认登录页面生成：

<img src="SpringSecurity.assets/image-20230117143723450.png" alt="image-20230117143723450" style="zoom:67%;" />



认证管理器：（责任链模式）

<img src="SpringSecurity.assets/image-20230117145557407.png" alt="image-20230117145557407" style="zoom:67%;" />





### RememberMe

AbstractAuthenticationProcessingFilter

RememberMeAuthenticationFilter

RememberMeServices的autoLogin()方法、onLoginSuccess()、

TokenBasedRememberMeServices实现类processAutoLoginCookie()

PersistentTokenBasedRemeberMeServices实现类processAutoLoginCookie()生成令牌

<img src="SpringSecurity.assets/image-20230119182249106.png" alt="image-20230119182249106" style="zoom:67%;" />

PersistentTokenRepository根据series查询token值





cookies令牌值

<img src="SpringSecurity.assets/image-20230119180600422.png" alt="image-20230119180600422" style="zoom:67%;" />



Token令牌持久化

JdbcTokenRepositoryImpl













### 会话管理

SessionManagementFilter

SessionAuthenticationStrategy



HttpSessionEventPublisher

会话共享：SpringSession、Redis

SpringSessionBackedSessionRegistry

FindByIndexNameSessionRepository



### CSRF

csrf令牌，服务端生成

<img src="SpringSecurity.assets/image-20230120001654714.png" alt="image-20230120001654714" style="zoom:67%;" />

CsrfFilter

CookieCsrfTokenRepository实现类的loadToken()方法

请求头X-XSRF-TOKEN或请求参数\_csrf





### CORS

<img src="SpringSecurity.assets/image-20230120003716428.png" alt="image-20230120003716428" style="zoom:67%;" />

<img src="SpringSecurity.assets/image-20230120003912642.png" alt="image-20230120003912642" style="zoom:67%;" />

CorsConfigurationSource

UrlBasedCorsConfigurationSource







### 异常处理







## 核心内容

### SpringBootWebSecurityConfiguration

自动配置类

默认拦截所有请求



### AuthenticationManager

Authentication

```

```



**AuthenticationManager认证管理**

将传入的AuthenticationToken进行认证处理

ProviderManager

AuthenticationProvider

<img src="SpringSecurity.assets/image-20230118023123094.png" alt="image-20230118023123094" style="zoom:67%;" />

<img src="SpringSecurity.assets/image-20230118023159630.png" alt="image-20230118023159630" style="zoom:67%;" />![image-20230118023724668](SpringSecurity.assets/image-20230118023724668.png)![image-20230118023739796](SpringSecurity.assets/image-20230118023739796.png)

<img src="SpringSecurity.assets/image-20230118023746935.png" alt="image-20230118023746935" style="zoom:67%;" />

DaoAuthenticationProvider调用UserDetailService进行认证





认证流程：

<img src="SpringSecurity.assets/image-20230118022234256.png" alt="image-20230118022234256" style="zoom:67%;" />



前后端分离认证：

<img src="SpringSecurity.assets/image-20230119010503473.png" alt="image-20230119010503473" style="zoom:67%;" />





### UserDetailService

根据用户名获取用户信息

数据源

UserDetailServiceAutoConfiguration自动配置



**UserDetailManager用户信息管理**

InmemoryUserDetailsManager（基于内存的数据源）



UserDetail、User



### PasswordEncoder

密码比较器

DelegatingPasswordEncoder密码比较器代理







### WebSecurityConfigurerAdapter

Security项目配置

```
WebSecurityConfigurerAdapter:
	configure(HttpSecurity http):
		http.authorizeHttpRequest()
			.mvcMatchers("/xxxx").permitAll()
				.hasRole()
				.hasAuthority()
				.hasAnyAuthority()
				.hasAnyRole()
				.hasPermission()
				.antMatchers()
				.regexMatchers()
			.anyRequst.authenticated()
			.and()
			.formLogin()
			.loginPage()
				.loginProcessingUrl()
				.usernameParameter()
				.passwordParameter()
			.logout()
				.logoutUrl()
				.invalidateHttpSession()
				.logoutSuccessUrl()
				.clearAuthentication()
				.logoutRequestMatcher()
				.logoutSuccessHandler()
			.successForwardUrl()
				.defaultSuccessUrl()
				.successHandler()
			.failureUrl()
				.failureForwardUrl()
				.failureHandler()
			.csrf().disable()
				.csrfTokenRepository()
			.addFilterAt()
			.exceptionHandling()
				.authenticationEntryPoint()
				.accessDeniedHandler()
			.rememberMe()
				.key()
				.alwaysRemember()
				.rememberMeParameter()
				.rememberMeServices()
				.tokenRepository()
			.sessionManagement()
				.maximumSessions()
				.expireUrl()
				.expiredSessionStrategy()
				.maxSessionPreventsLogin()
				.sessionRegistry()
			.cors()
				.configurationSource()
			.oauth2Login()
				
    
    initialize(AuthenticationManagerBuilder, DataSource):
    configure(AuthenticationManagerBuilder):
    	builder.userDetailsService()
    		.authenticationProvider()
    		
    		
    authenticationManagerBean():
```



AuthenticationSuccessHandler认证登录成功处理

AuthenticationFailureHandler认证登录失败处理

默认错误信息存在request、session中





LogoutSuccessHandler注销成功处理







### SpringContextHolder

<img src="SpringSecurity.assets/image-20230118020542316.png" alt="image-20230118020542316" style="zoom:67%;" />

<img src="SpringSecurity.assets/image-20230118020830565.png" alt="image-20230118020830565" style="zoom:67%;" />



SpringContextHolderStrategy

策略设计模式

SpringContext





### AccessDecisionManager

FilterSecurityInterceptor过滤器实现权相比较，用户授权在Authentication认证时已完成





<img src="SpringSecurity.assets/image-20230120014802034.png" alt="image-20230120014802034" style="zoom:67%;" />









<img src="SpringSecurity.assets/image-20230120011903302.png" alt="image-20230120011903302" style="zoom: 67%;" />

GrantedAuthority

权限管理策略

<img src="SpringSecurity.assets/image-20230120012158846.png" alt="image-20230120012158846" style="zoom:67%;" />





@EnableGlobalMethodSecurity

<img src="SpringSecurity.assets/image-20230120013312465.png" alt="image-20230120013312465" style="zoom:67%;" />





<img src="SpringSecurity.assets/image-20230120014642293.png" alt="image-20230120014642293" style="zoom:67%;" />![image-20230120015041028](SpringSecurity.assets/image-20230120015041028.png)

<img src="SpringSecurity.assets/image-20230120015047100.png" alt="image-20230120015047100" style="zoom:67%;" />



### ConfigAttribute

SecurityMetadataSource



动态权限分配

自定义实现<u>FilterInvocationSecurityMetadataSource的getAttributes()方法</u>获取保存资源访问映射的权限（角色）信息

```
ApplicationContext appCtx = http.getSharedObject(ApplicationContext.class)

http.apply(new UrlAuthorizationConfigurer<>(appCtx))
	.withObjectPostProcess(new ObjectPostProcessor<FilterSecurityInterceptor>() {
		public <O extends FilterSecurityInterceptor> O postProcess(O object) {
			object.setSecurityMetadataSource(自定义SecurityMetadataSource)
			// 是否拒绝公共资源的访问
			object.setRejectPublicInvocations(false)
			return object
		}
	})
```

FilterInvocation当前请求对象

AntPathMatcher路径匹配器















## API





## OAuth2

<img src="SpringSecurity.assets/image-20230120023026343.png" alt="image-20230120023026343" style="zoom:67%;" />

四种授权模式：

<img src="SpringSecurity.assets/image-20230120023514319.png" alt="image-20230120023514319" style="zoom:67%;" />

<img src="SpringSecurity.assets/image-20230120023712510.png" alt="image-20230120023712510" style="zoom:67%;" />



一、授权码模式

<img src="SpringSecurity.assets/image-20230120155450549.png" alt="image-20230120155450549" style="zoom:67%;" />

<img src="SpringSecurity.assets/image-20230120155701931.png" alt="image-20230120155701931" style="zoom:67%;" />



<img src="SpringSecurity.assets/image-20230120160049599.png" alt="image-20230120160049599" style="zoom:67%;" />



二、简化模式

<img src="SpringSecurity.assets/image-20230120160155201.png" alt="image-20230120160155201" style="zoom:67%;" />

<img src="SpringSecurity.assets/image-20230120160303061.png" alt="image-20230120160303061" style="zoom:67%;" />



三、密码模式

<img src="SpringSecurity.assets/image-20230120160624382.png" alt="image-20230120160624382" style="zoom:67%;" />

四、客户端模式

<img src="SpringSecurity.assets/image-20230120160723001.png" alt="image-20230120160723001" style="zoom:67%;" />





标准接口：

<img src="SpringSecurity.assets/image-20230120160834555.png" alt="image-20230120160834555" style="zoom:67%;" />









github第三方登录

配置id

```
spring:
	seurity:
		oauth2:
			client:
				registraion:
					github:
						client-id:
						client-secret:
						redirect-uri: /login/oauth2/code/github
```



依赖

```
oauth2:
	org.springframework.boot
		spring-boot-starter-oauth2-client
```



DefaultOAuth2User



OAuth2LoginAuthnticationFilter处理OAuth2认证

请求默认url为`/login/oauth2/code/*`

ClientRegistrationRepository的findByRegistrationId()方法查看该第三方是否在本地注册，获取appid和密钥







OAuth2AuthorizationCodeGrantFilter处理OAuth2认证中授权码

BearerTokenAuthenticationFilter处理OAuth2认证的Access Token





### SpringSecurityOAuth2

自定义授权、资源服务器

依赖：

```
org.springframework.cloud
	spring-cloud-starter-oauth2
		2.2.5.RELEASE
```



Authentication Server配置

```
@EnableAuthorizationServer

自定义AuthorizationServerConfigurerAdapter实现

	授权服务器配置客户端
	configure(ClientDetailsServiceConfigurer clients):
		clients.inMemory()
			.withClient()
			.secret()
			.redirectUris()
			.authorizedGrantType()
			.scopes()
			
			.jdbc()
			.withClientDetails()
			
	configure(AuthorizationServerEndpointsConfigurer endpoints):
    	endpoints.userDetailsService()
    		.authenticationManager()
    		.tokenStore()
    		.tokenServices()
    		.accessTokenConverter()
    		
    	配置token服务
    	DefaultTokenServices tokenServices
    		.setTokenStore()
    		.setSupportRefreshToken()
    		.setReuseRefreshToken()
    		.setClientDetailsService()
    		.setTokenEnhancer()
    		.setAccessTokenValiditySeconds()
    		.setRefreshTokenValiditySeconds()
```



请求授权：`/oauth/authorize`

获取code授权码

根据授权码code获取Token令牌：`/oauth/token`

获取access_token令牌



认证结果告知AuthorizationManager集成进SpringSecurity



刷新Token

防止令牌过期

获取refresh_token



令牌存储（ClientDetails、Token、）

ClientDetailsService

JdbcClientDetailsService



TokenStore

JdbcTokenStore





集成JWT令牌

TokenStore

JwtTokenStore

JwtAccessTokenConverter

ClientDetailsService

JdbcClientDetailsService



资源服务器和授权服务器使用同一个TokenStore（JwtTokenStore），共享Token信息







资源服务器

依赖：

```
org.springframework.security
	spring-security-oauth2-resource-server
```



配置

```
@EnableResourceServer

ResourceServerConfigurerAdapter
	configure(ResourceServerSecurityConfigurer resources):
		resources.tokenStore()
			.
```





