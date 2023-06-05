# JetPack

> Author: Sylvie233
>
> Date: 23/6/1
>
> Point: Compose教程P3

[TOC]

## JetPack

### AppCompatActivity

```
AppCompatActivity:
	layoutInflater:
	lifecycle:
	onCreate():
	---
	setContentView():
```





### ViewModel

```
ViewModel:
	onCleared():
	---
	clear():
```





#### 生命周期

<img src="JetPack.assets/image-20230605160810958.png" alt="image-20230605160810958" style="zoom:67%;" />





### LiveData

```

MutableLiveData:
	---
	observe():
	postValue():
	setValue():
```



### ViewBinding

```
ActivityMainBinding:
	xxx:
	root:
	bind()
	inflate():
	---
```



自动为每个XML文件生成`XXXBinding`类,简化了为每个控件`findViewById()`来获取



### DataBinding

```
ViewDataBinding:
	inflate():
	---
	
DataBindingUtil:
	bind():
	setContentView():
	---
```



为layout生成`XXXbinding`类





#### layout

```
<layout>
	<data>
		<import
			type:
		>
		<variable
			name:
			type:
		>
		
使用：
	@{xxx变量}
	@={xxx}: 双向数据绑定
```



#### BaseObservable

```
BaseObservable:
	@Bindable:
	---	
	notifyPropertyChanged():
```



双向数据绑定









### Lifecycle

```
Lifecycle:
	currentState:
		isAtLeast():
	---
	addObserver():

LifecycleOwner:

LifecycleObserver:
	@OnLifecycleEvent:
		
```



![image-20230605202904442](JetPack.assets/image-20230605202904442.png)















## JetPack Compose

### ComponentActivity

```
ComponentActivity:
	onCreate():
	---
	setContent():
	

```



### 内置注解

```
@Composable:


@DrawableRes:

@Preview:
```





### 内置组件

```
内置组件:
	Column:
	Icon:
	Row:
	Text:
```



### 常用类

```
常用函数:
	painterResource():

常用类:
	Alignment:
		CenterHorizontally:
	Color:
		Black:
		Green:
	CompositionLocal:
	Modifier:
		background():
		padding():
		size():
		weight():
```







## API

```
android:
	os:
		Bundle:
	view:
		LayoutInflater:
		View:
		ViewGroup:
	
androidx:
	databinding:
		BaseObservable:
		Bindable:
		ViewBinding:
	fragment:
		app:
			activityViewModels:
			Fragment:
				onCreateView():
				onActivityCreated():
				---
	lifecycle:
		LifecycleObserver:
			
		LifecycleOwner:
			getLifecycle():
		MutableLiveData:
			---
			observe():
		Observer:
			onChanged():
		ViewModeL:
```



