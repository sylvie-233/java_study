# Jenkins基础

> Author: Sylvie233
>
> Date: 23/1/16
>
> Point: P11

[TOC]

## 基础介绍

war包安装





## 核心内容

### Pipeline

Jenkinsfile

```
pipelin {
	agent any
	
	tools {
		maven "maven3"
	}
	
	stages {
		stage("xxx") {
			steps {
				// 命令工作
				echo
				git
				sh
			}
		}
	}
	
	post {
		always {
			
		}
		
	}
}
```





































































































































































































