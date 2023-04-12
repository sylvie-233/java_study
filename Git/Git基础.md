# Git基础

> Author: Sylvie233
>
> Date: 23/1/16
>
> Point: 

[TOC]

## 基础介绍



### git

```
git:
	
```



## 核心内容

### Hooks













## 第三方工具

### GitLab



提交后自动触发项目流水线



基础流水线、DAG流水线、父子流水线





#### gitlab-runner

流水线任务执行器







#### .gitlab-ci.yml

```yaml
image: node:alpine			# 环境镜像

cache:						# 文件缓存
	key: xxx缓存标志
	key:
		files:
			- package-lock.json
	paths:
		- node_modules
		
variables:					# 变量定义($XXX 使用)
	CI:
	CI_BUILD_NAME:
	CI_COMMIT_BRANCH:
	CI_COMMIT_MESSAGE:
	CI_COMMIT_TAG:
	CI_DEPLOY_FREEZE:
	XXX: "XXX"

stages: 					# 定义流水线阶段
	- .pre
	- build
	- test
	- deploy
	- .post
	
myJob:						# 定义任务
	image: docker			# 指定任务依赖镜像
	stage: build			# 指定任务所处阶段
	environment:
		xxx: "xxx"
	variables:				# 定义变量
		XXX: "XXX"
	before_script:
		- xxx命令
	script:
		- export
		- shell命令
		
	resource_group: prod
	
	needs:					# 构建依赖关系
		- myJob_2
	
	trigger:				# 触发执行当前项目的子流水线
		include: a/.gitlab-ci.yml
		
		project: xxx/子项目  # 执行其他项目的流水线	
		branch: master
		strategy: depend
	rules:					# 定义触发规则
		- changes:
			- a/*
		- if: 条件判断
		
		
	retry: 2				# 重试次数
	retry:
		max: 2
		when: 
			- always
			- runner_system_failure
			- script_failure
			- stuck_or_timeout_failure
			- unknown_failure
	interruptible: true		# 可中断
	
	
	tags:
		- xxxRunner			# 指定执行的runner
	
	release:				# 创建发布
		tag_name: "xxx"
		description: "xxx"
	
	
	
	when:					# 条件执行任务
		- manual			# 手动执行
		- on_success
		- on_failure
		- delayed
		- always
		- never
	only:					
		- release			# 指定分支
		- merge_request
		- tags
	except:					# 排除分支
		- release
		
	timeout: 2h				# 任务超时时间	
		
	artifacts:				# 输出文件集(可在任务之间传递)
		paths:
			- dist/
```































