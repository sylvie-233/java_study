# Gradle基础

> Author: Sylvie233
>
> Date: 23/6/1
>
> Point: 



## 基础介绍



![image-20230605230652264](Gradle.assets/image-20230605230652264.png)



`project`->`task`、其余的均为`extensions`



必备配置：plugins、repositories、dependencies


### 安装目录

```
gradle-8.4:
	/android:
	/bin:
	/caches:
		/modules-2:
	/daemon:
	/docs:
	/init.d:
	/jdks:
	/kotlin-profile:
	/lib:
	/native:
	/notifications:
	/src:
	/wrapper:
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
apply plugin: 'java'


plugins {
	id ‘xxx.xxx’ version "x.x.x"
}




group = "xxx"
version = "xxx"
sourceCompatibility = "1.8"
targetCompatibility = "1.8"

ext {
	
}


buildscript {
	repositories {
		mavenLocal()
		maven {
			url 'https://maven.aliyun.com/repository/public'
		}
		mavenCentral()
	}
	dependencies {
		classpath "xxx.xxx:xxx:x.x.x"
	}
}

configurations {
	xxx
	xxx.extendsFrom testImplementation
}

allprojects {
	apply plugin: "idea"
	
	dependencyManagement {
		imports {
			mavenBom
		}
	}
	repositories {}
	dependencies {}
}


repositories {
	mavenLocal()
	mavenCentral()
	maven {
		name
		url
		credentials {
			username
			password
		}
	}
	repositories {
		flatDir(
			dirs:
			name:
		)
	}
}

dependencies {
	annotationProcessor
	developmentOnly
	implementation 'xxx:xxx'
	testImplementation 'xxx:xxx'
	implementation("xxx.xxx") {
		exclude "xxx"
		isForce
		transitiveD
	}
}



sourceSets {
	main {
		java {
			srcDirs
		}
		resources {
			srcDirs
			srcDir
			exclude
		}
	}
	xxx {
		compileClasspath += sourceSets.main.output
		runtimeClasspath += sourceSets.main.output
	}
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




task xxx(
	type:
) {
	description()
	group()
	
	testClassesDirs
	classpath
	shouldRunAfter test
	mustRunAfter
	
	
	doFirst {
		
	}
	doLast {
	
	}
}



task myJar(
	type: Jar
) {
	baseName "xxx"
	from compileJava.outpus, "sr/main/resources"
	manifest {
		attributes(
			"Manifest-Version": 1.0,
			"Main-Class": "xxx.xxx"
		)
	}
	desinationDir(file("xxx"))
}
artifacts {
	archives myJar
}
```



#### settings.gradle

```
rootProject
	.name = 'xxx '

include 'xxx子项目'

findProject()


gradle.beforeSettings {}
gradle.settingsEvaluated {}
gradle.projectsLoaded {}


```



### 生命周期

- 初始化阶段
- 配置阶段
- 执行阶段



![image-20230606191355110](Gradle.assets/image-20230606191355110.png)

![image-20230606191602672](Gradle.assets/image-20230606191602672.png)

![image-20230606191937063](Gradle.assets/image-20230606191937063.png)















### gradle

```
gradle指令:
	-b: 指定文件运行
	-d:
	-i:
	-q: 静默模式
	-x: 排除任务
	_taskName: 运行指定任务
	build:
	buildEnvironment: 
	dependencies:
	help: 帮助
	init:
	projects: 列出所有project项目
	properties:
	tasks: 列出所有task任务
```











## 核心内容

### gradle

```yaml
gradle:
	taskGraph:
	addListener():
```

### project

```
project:
	allprojects:
	buildDir:
	buildFileName: build.gradle名称
	convention:
	ext: 扩展属性（全局def）
	group: 包名分组
	logger:
	name: 包名
	parent:
	path:
	project:
	projectDir:
		absolutePath:
	rootDir:
	rootProject:
	subprojects:
	tasks:
		addRule():
		create():
		findByPath():
		getByPath():
			path:
		register():
		with():
		withType():
	version: 版本
	_taskName: 	
	property():
	---
	extensions: 项目扩展
		create():
	apply(): 应用插件
		from: 
		plugin:
	getConvention():
		getPlugins():
			put():
	getExtensions():
		add():
		create():
	getPluginManager():
	task(): 创建任务
			
 
---
常用方法:
	copy():
		from:
		into:
	defaultTasks()
	fileTree():	
	flatDir():
	println():
	project():
```

![image-20230606131921449](Gradle.assets/image-20230606131921449.png)





### plugins

```
plugins:
	id: 
		apply:
		version:
	---
	apply():
	getPlugin():
```







### buildscript

```
buildscript:
	repositories:
		maven:
			url:
	dependencies:
		classpath:
```


声明gradle脚本自身的依赖



### configurations

```
configurations:
	xxx:
		asPath:
		files:
			first():
			last():
```

![image-20230606133056129](Gradle.assets/image-20230606133056129.png)

![image-20230606133339429](Gradle.assets/image-20230606133339429.png)





### repositories

```
repositories:
	maven:
		url:
	mavenCentral:
	gradlePluginPortal:
	---
```





### denpendencies

```
denpendencies:
	compile:
	testCompile:
	testImplementation:
	testRuntimeOnly:
		group:
		name:
		version:
	xxxImplementation: 指定源集添加依赖
```

![image-20230606135214357](Gradle.assets/image-20230606135214357.png)



### allprojects

```
allprojects:
	
```

所有项目都生效的配置



### subprojects

```
subprojects:
	
```

子项目生效的配置







### sourceSets

```
sourceSets:
	xxx项目: 自定义源代码集（java、test）
		java:
			srcDirs:
			outputDir:
		output:
			resourcesDir:
		resources:
			srcDirs:
			
```


定义源代码目录


### test

```
test:
	enabled:
	exclude:
	include:
	useJUnitPlatform():
	useTestNG():
```

使用测试框架




### artifacts

```
artifacts:
	
```


### tasks
```yaml
tasks:
	[]: 索引task
	---
	register():
	withType(): 修改任务配置
```


### task

```
task:
	dependsOn:
	description:
	enabled:
	group:
	mustRunAfter: 指定任务执行顺序
	name: 任务名称	
	overwrite:
	type: 预定义任务调用
		Copy:
			from:
			into:
			rename:
		Jar: 封装Jar包
			archiveBaseName:
			archiveVersion:
			destinationDirectory:
			from:
		Zip:
			from:
			into:
			
	with: 使用闭包
	---
	dependsOn():
	doFirst {}:
	doLast {}: 
```

task抛出异常则会跳过执行






#### DefaultTask





#### TaskAction

```
:
	@Input:
	@TaskAction:
```





#### Rule


### uploadArchives

```yaml
uploadArchives: 发布文件
	repositories:
		mavenDeployer:
			repository:
				url:
```

发布包

### publishing
```
publishing:
	publications:
		maven:
			from:
	repositories:
		maven:
			url:
```


### 插件


脚本插件(.gradle文件)、二进制插件(jar包)

#### 自定义插件

##### Plugin

```
Plugin:
	apply():
		Project:
```

实现Plugin接口


### jar

```
jar: 生成可执行jar包的配置
	manifest:
		attributes:
			Manifest-Version:
			Main-Class:
	
```






## Android

`build.gradle`

```
apply plugin: 'com.android.application'
apply plugin: 'kotlin-android'
apply plugin: 'kotlin-android-extensions'
apply plugin: 'kotlin-kapt'

android {
	compileSdkVersion 29
	
	defaultConfig {
		applicationId "xxx.xxx"
		minSdkVersion 23
		targetSdkVersion 29
		versionCode 1
		versionName "1.0"
		multiDexEnabled
		testInstrumentationRunner "androidx.test.runner.AndroidJUnitRunner"
		dataBinding {
			enabled true
		}
	}
	
	buildTypes {
		release {
			minifyEnabled false
			shrinkResources false
			proguardFiles
		}
	}
	
	compileOptions {
		sourceCompatibility JavaVersion.VERSION_1_8
		targetCompatibility JavaVersion.VERSION_1_8
	}
	
	buildToolsVersion '29.0.3'
}

dependencies {
	
}
```







