# Gradle基础

> Author: Sylvie233
>
> Date: 23/6/1
>
> Point: gradle教程P7

[TOC]



## 基础介绍



![image-20230605230652264](Gradle.assets/image-20230605230652264.png)











### 安装目录

```
:
		
```



#### 工程目录

```
工程目录:
	/.gradle:
	/gradle:
		/wrapper:
			gradle-wrapper.jar:
			gradle-wrapper.properties:
	/src:
		/main:
		/test:
	.gitignore:
	build.gradle:
	gradlew:
	gradlew.bat:
	settings.gradle:
```



`gradle-wrapper.properties`

```
distributionBase=GRADLE_USER_HOME
distributionPath=wrapper/dists
distributionUrl=https\://xxx.xxx/gradle.zip
zipStoreBase=GRADLE_USER_HOME
zipStorePath=wrapper/dists
```









#### build.gradle

```
plugins {
	id ‘xxx.xxx’ version "x.x.x"
}




group = "xxx"
version = "xxx"
sourceCompatibility = "1.8"




repositories {
	mavenCentral()
}

dependencies {
	implementation 'xxx:xxx'
	testImplementation 'xxx:xxx'
}

tasks.named("test") {
	useJUnitPlatform()
}

application {
	mainClassName = "xxx.xxx.Xxx"
}

test {
	useJUnitPlatform()
}




task xxx {
	
	doFirst {
		
	}
	doLast {
	
	}
}
```



#### settings.gradle

```

```









### gradle

```
gradle:
	-d:
	-i:
	-q:
	init:
```











## 核心内容

















## Android





