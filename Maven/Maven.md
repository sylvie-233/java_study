# Mavan

> Point: P146

[TOC]



## 基础介绍

安装目录

```
Maven:
	
```



`settigs.xml`

```
<settings>
	<localRepository>
	
	<mirrors>
		<mirror>
			<id>
			<mirrorOf>
				central:
			<name>
			<url>
```





### mvn

```
mvn:
	-D: 指定参数
	archetypee:
		:generate:
	clean:
	dependency:
		:list:
		:tree:			
	install:
	
	
---
maven参数:
maven:
	test:
		skip:
```







## 核心内容

`pom.xml`

```
<project>
	<modelVersion>

	<groupId>
    <artifactId>
    <version>

	<name>
	<url>
	
	<packaging>:
		pom:
		war:

	<properties>
		<project.build.sourceEncoding>
		<自定义属性>:

	<modules>: 子模块配置（聚合	）
		<module>: 子模块工程
		
	<parent>: 父工程配置
		<groupId>
		<artifactId>
		<version>
		
	<dependencyManagement>
		<dependencies>
			<dependency>
                <groupId>
                <artifactId>
                <version>
			
    <dependencies>
        <dependency>
            <groupId>
            <artifactId>
            <version>
            <scope>
            <exclusions>
                <exclusion>
                    <groupId>
                    <artiractId>
                    <version>
	
	<build>: 构建配置
		<finalName>
		
		<plugins>
			<plugin>
				<groupId>
                <artifactId>
                <version>
                
                <dependencies>
                	<groupId>
                    <artifactId>
                    <version>
                
```



### 依赖



### 继承





### 聚合



### 生命周期

#### clean

- pre-clean
- clean
- post-clean



#### site

- pre-site
- site
- post-site
- deploy-site



#### default

- **validate**
- generate-sources
- process-sources
- generate-resources
- process-resources
- **compile**
- process-classes
- generate-test-sources
- process-test-sources
- generate-test-resources
- process-test-resources

- **test-comppile**
- process-test-classes
- **test**
- prepare-package
- **package**
- pre-integration-test
- integration-test
- post-integration-test
- **verify**
- **install**
- **deploy**



### 插件

一个插件可以对应多个目标，而每一个目标都和生命周期中的某一个环节对应

插件实现了maven的生命周期













