# Android基础

> Author: Sylvie233
>
> Date: 2023/5/8
>
> Point: P22



[TOC]

## 基础介绍

Android版本

<img src="Android基础.assets/image-20230512104518844.png" alt="image-20230512104518844" style="zoom:67%;" />



**Android技术架构**

<img src="Android基础.assets/image-20230512104600383.png" alt="image-20230512104600383" style="zoom:67%;" />

<img src="Android基础.assets/image-20230512104649244.png" alt="image-20230512104649244" style="zoom:67%;" />



Android单位

<img src="Android基础.assets/image-20230516081433185.png" alt="image-20230516081433185" style="zoom:67%;" />













### **目录结构**

```
:
	/build:
		/generated:
		/intermediates:
		/outputs:
		/tmp:
	/libs:
	/src:
		/androidTest:
		/main:
			/java:
			/res:
				/animator:
				/anim:
				/color:
				/drawable: (xxxhdpi|xxhdpi|xhdpi|hdpi|mdpi)
                /layout:
                	activity_main.xml:
                /menu:
                /mipmap: (xxxhdpi|xxhdpi|xhdpi|hdpi|mdpi)
                	/ic_launcher:
                /raw:
                /values:
                    colors.xml:
                    strings.xml:
                    styles.xml: 样式定义文件
                /xml:
			AndroidManifest.xml:
		/test:
	build.gradle:
```



`AndroidManifest.xml`

```
<manifest>
	<supports-screens>
	<applicatioin
		allowBackup:
		icon:
		label:
		roundIcon:
		supportsRtl:
		theme: @style/xxx应用样式
	>
		<activity
			name
		>
			<intent-filter>
				<action
					name:
				>
				<category
					name:
						LAUNCH:
						DEFAULT:
				>
```



`layout/activity_main.xml`

```
<Root>
	<include
		layout: 复用layout布局
	>
	
	<fragment
		id:
		name: 全类名
	>
```



`values/colors.xml`

```
<resources>
	<color
		name:
	>
```



`values/strings.xml`

```
<resources>
	<string
		name:
	>
```



`values/styles.xml`

```
<resources>
	<style
		name:
		parent:
	>
		<item
			name:
		>
			@color/xxx
			@style/xxx
```









## 核心内容

### Activity

#### 生命周期

<img src="Android基础.assets/image-20230515212223905.png" alt="image-20230515212223905" style="zoom:67%;" />



状态转换

<img src="Android基础.assets/image-20230515212729735.png" alt="image-20230515212729735" style="zoom:67%;" />



2个Activity的生命周期

<img src="Android基础.assets/image-20230515212911885.png" alt="image-20230515212911885" style="zoom:67%;" />





#### Intent





#### Fragment

##### 生命周期

<img src="Android基础.assets/image-20230516092736671.png" alt="image-20230516092736671" style="zoom:67%;" />

<img src="Android基础.assets/image-20230516092907532.png" alt="image-20230516092907532" style="zoom:67%;" />

















### View

#### FrameLayout



#### GridLayout



#### RelativeLayout



#### TableLayout



##### TableRow



#### EditText



#### ImageView





#### TextView





### Resource









## API

```
androidx:
	constraintlayout:
		widget:
			ConstraintLayout:
    fragment:
    	app:
    		Fragment:




AppCompatActivity:
	findViewById():
	onCreate():
	setContentView():
	startActivity():
Bundle:
Button:
	id:
	text:
ComponentName:
EditText:
	hint:
	getText():
EventActivity:
	this:
FrameLayout:
GridLayout:
ImageView:
	src:
Intent:
	---
	setAction():
	setClassName():
	setComponent():
LinearLayout:
	layout_gravity:
	layout_height:
		wrap_content:
	layout_width:
		match_parent:
	orientation:
Log:
	d():
	e():
	i():
	w():
R:
	id:
	layout:
RelativeLayout:
Space:
TableLayout:
TextView:
	
View:
ViewGroup:
```





