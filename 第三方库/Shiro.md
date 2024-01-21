# Shiro

> Author: Sylvie233
>
> Date: 23/12/31
>
> Point: 


## 基础介绍

![[Pasted image 20231231144726.png]]




三大核心组件：Subject、SecurityManager、Realm



自定义：ShiroFilterFactoryBean、SecurityManager、Realm


![[Pasted image 20231231151729.png]]



### 认证过滤器

```
:
	anon:
	authc:
	authBase:
	user:
```

### 授权过滤器

```
:
	perms:
	roles:
	port:
	rest:
	ssl:
```




## 核心内容

```

```

### Subject


### SecurityManager




### Realm

相当于一个DAO：从应用配置的Realm中查找用户以及其权限信息，内部执行认证和授权





### UsernamePasswordToken




### AuthenticationInfo


### AuthorizationInfo


### ShiroFilterFactoryBean


