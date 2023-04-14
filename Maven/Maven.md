# Mavan

> Point: 

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
	
	<profiles>: 环境配置项
		<profile>
			<id>: profile标识
			<activation>: 定义激活方式
				<activeByDefault>
				<jdk>
				<os>
					<name>
					<family>
					<arch>
					<version>
			<properties>
			<file>
				<exists>
				<missing>
	
	<pluginGroups>
		<pluginGroup>
	
	<servers>
		<server>
			<id>
			<username>
			<password>
			
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
	-P: 指定profile环境
	archetypee:
		:generate:
	clean:
	dependency:
		:list:
		:tree:	
	deploy:
	enforcer:
		:enforcer:
    help:
    	:active-profiles:
    	:all-profiles:
    	:describe:
    	:effective-pom:
    	:evaluate:
    	:system:
	install:
		install-file:
	resources:
		:resources:
	
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
		maven-plugin:

	<properties>: （内置java系统属性Properties、env系统环境变量、project项目属性、settings Maven配置、）
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
            <optional>: 可选依赖
            <scope>
            	import: 导入一个版本集合依赖
            	system:
            	runtime:
            <type>
            	pom
            <systemPath>: 手动导入jar包
            <exclusions>
                <exclusion>
                    <groupId>
                    <artiractId>
                    <version>
	
	<distributionManagement>: 包发布管理
		<snapshotRepository>
			<id>
			<name>
			<url>
	
	<repositories>
		<repository>
			<id>
			<name>
			<url>
			<layout>
			<snapshots>
				<enabled>
	
	<pluginRepositories>
		<pluginRepository>
			<id>
			<name>
			<url>
			<layout>
			<snapshots>
				<enabled>
	
	<build>: 构建配置
		<directory>
		<outputDirectory>
		<testOutputDirectory>
		<sourceDirectory>
		<finalName>
		<scriptSourceDirectory>
		<testSourceDirectory>
		
		<resources>
			<resource>
				<directory>
		<testResources>
		
		<pluginManagement>
			<plugin>
		
		<plugins>
			<plugin>
				<groupId>
                <artifactId>
                <version>
                
                <executions>
                	<execution>
                		<id>
                		<phase>: 绑定生命周期
                		<goals>: 定义需要执行的插件目标
                			<goal>
                		<configuration>
                
                <dependencies>
                	<groupId>
                    <artifactId>
                    <version>
     
     <profiles>: 环境配置项（可覆盖原有配置）
		<profile>
			<id>: profile标识
			<activation>: 定义激活方式
				<activeByDefault>
				<jdk>
				<os>
					<name>
					<family>
					<arch>
					<version>
			<properties>
			<file>
				<exists>
				<missing>    
            <build>
            	<resources>
            		<resource>
            			<directory>
            			<filtering>
            			<includes>
            			<excludes>
```



### 依赖

超级POM、



版本仲裁：最短路径优先、路径相同时先声明者优先



体系外jar包导入

```
mvn install:install-file -Dfile -DgroupId -DartifactId -Dversion -Dpackage=jar
```















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



#### 自定义插件

`maven-plugin-api`、



Mojo类

文档注释注解

```
:
	@goal: 定义插件目标（命令行中使用）
```





### 私服

Nexus

































