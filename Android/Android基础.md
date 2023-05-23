# Android基础

> Author: Sylvie233
>
> Date: 2023/5/8
>
> Point: 安卓基础 P52|Jetpack P10



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
                /navigation:
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



#### AndroidManifest.xml

`AndroidManifest.xml`

```
<manifest>
	<supports-screens>
	<uses_sdk
		minSdkVersion:
		targetSdkVersion:
	>
	<uses-permission
		name:
			CALL_PHONE:
	>
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
				<data>
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
		app:navGraph:
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

```
Intent:
	ACTION_SEND:
	EXTRA_SUBJECT:
	EXTRA_TEXT:
    FLAG_ACTIVITY_NEW_TASK:
    createChooser():
	---
	addCategory():
	putExtra():
	setAction():
	setData():
	setFlags():
	setType():
	
```



<img src="Android基础.assets/image-20230523210027518.png" alt="image-20230523210027518" style="zoom:67%;" />



##### ComponentName

```
ComponentName:
	
```



##### Action

```
Action:
	
```



<img src="Android基础.assets/image-20230523211841182.png" alt="image-20230523211841182" style="zoom:67%;" />



action常量

```
常量:
	android.media.action.IMAGE_CAPTURE:
```







##### Data

```
Data:
	
```



data uri

```
uri:
	content://contacts/people/
	geo:0,0
	http://xxx.com
	tel:17729014809
	tel://17729014809
```



##### Category

```
Category:
	
```



Category常量

```
常量:
	android.intent.category.APP_CALENDAR:
```



##### Extras



##### Flags





#### Fragment

```
Fragment:
	onCreate():
	---
	
```





##### 生命周期

<img src="Android基础.assets/image-20230516092736671.png" alt="image-20230516092736671" style="zoom:67%;" />

<img src="Android基础.assets/image-20230516092907532.png" alt="image-20230516092907532" style="zoom:67%;" />



静态调用、动态调用

FragmentManager、FragmentTrasaction、











### View

#### AppBarLayout



#### ConstraintLayout



#### DrawerLayout





#### FrameLayout



#### GridLayout



#### LinearLayout

```
LinearLayout:
	---
	addView():
```





#### RelativeLayout



#### TableLayout



##### TableRow





#### Button

```
Button:
	drawableLeft:
	text:
	---
	setOnClickListener():
```





#### CalendarView



#### CheckBox

```
CheckBox:
	text:
	---
	isChecked():
```





#### EditText

```
EditText:
	editable:
	gravity:
	hint:
	imeOptions:
		actionDone:
		actionGo:
		actionSearch:
	inputType:
		numberSigned:
		phone:
		text:
		textPassword:
	lines:
	maxLength:
	numeric:
	password:
	textColorHint:
	---
	getText():
```



#### FloatingActionButton



#### HorizontalScrollView



#### ImageButton

```
ImageButton:
	src:
```





#### ImageView

```
ImageView:
	ScaleType:
		CENTER_CROP:
	scaleType:
		center: 中间
		fitCenter:
		fitStart:
		fitXY:
		matrix:
	src:
	---
	setImageResource():
	setScaleType:
```





#### ListView



#### MapView



#### ProgressBar

```
ProgressBar:
	max:
	min:
	progress:
	progressDrawable:
	style:
	---
	setProgress():
```





#### RadioButton

```
RadioButton:
	---
	getText():
	isChecked():
```



#### RadioGroup

```
RadioGroup:
	id:
	---
	setOnCheckedChangeListener():
```





#### Spinner



#### Switch

```
Switch:
	textOff:
	textOn:
	---
```





#### TextView

```
TextView:
	autoLink:
		web:
	text:
	textSize:
	---
	setText():
	setTextColor():
```





#### Toast

```
Toast:
    makeText():
	---
	getView():
	setDuration():
	setGravity():
	setView():
	show():
```





#### ToggleButton

```
ToggleButton:
	textOff:
	textOn:
	---
	isChecked():
```





#### WebView

















### Content







### Window

#### Menu

`menu.xml`

```
<menu>
	<group
		checkableBehavior:
	>
		<item>
	<item
		id:
		title:
		icon:
		orderInCategory:
		app:actionViewClass:
		app:showAsAction:
			never:
			ifRoom:
			withText:
			collapseActionView:
		app:actionProviderClass:
	>
		<menu> // 嵌套menu
```

##### MenuItem

```
MenuItem:
	getActionView():
	setOnActionExpandListener():
		onMenuItemActionExpand():
		onMenuItemActionCollapse():
```







#### PopupMenu

```
PopupMenu:
	inflate();
	setOnMenuItemClickListener():
	show():
```



#### ContextMenu

```
ContextMenu:
	add():
```





##### ContextMenuInfo	



#### Toolbar



#### ActionMode

```
ActionMode:
	Callback:
		onActionItemClicked():
		onCreateActionMode:
		onDestroyActionMode():
		onPrepareActionMode():
```



#### ActionView

```
ActionView:
```



#### ActionProvider

```
ActionProvider:
	onCreateActionView():
	onPerformDefaultAction():
	---
	
	
ShareActionProvider:
	---
	setShareIntent():
```



#### TabLayout

```
TabLayout:
	---
	setupWithViewPager():
```



##### SectionsPagerAdapter

```
SectionsPagerAdapter:
```





##### ViewPager

```
ViewPager:
	---
	setAdapter():
```



#### BottomNavigationView

```
BottomNavigationView:
	
```



##### NavigationView

```
NavigationView:
	app:headerLayout:
	app:menu:
```





##### Navigation

```
Navigation:
	
```





##### NavController

```
NavController:
```



##### NavigationUI

```
NavigationUI:
```



##### AppBarConfiguration

```
AppBarConfiguration:
```







### Resource

#### Android内置资源

```
@android:id:
	background:
	progress:
	
@android:style:
	Widget:
		ProgressBar:
			Horizontal:
```



#### \<layer-list>

```
<layer-list>
	<item
		left:
		top:
	>
		<bitmap
			src:
			gravity:
		>
		<scale
			scaleWidth:
			drawable:
		>
		<shape>
			<solid>
			<gradient
				angle:
				startColor:
				endColor:
			>
```



#### \<navigation>

```
<navigation>
	<fragment
		
	>
```





#### \<resources>

```
<resources>
	<string>
```



#### \<selector>

```
<selector>
	<item
		state_focused:
		state_pressed:
		color:
		drawable:
	>
```



#### \<vector>

```
<vector

>
	<path
		
	>
```





### JetPack



Google推出的一套系列组件集



#### AppCompat



#### 数据绑定

##### DataBinding

```
<layout>
	<data>
		<variable
			name: _vm（通过@{_vm.xxx}使用VM属性）
			type: VM全类名
		>
```



Activety中实现Binding，并注入ViewModel（xml中声明的ViewModel）

```
class MainActivity:
	ActivityMainBinding binding
	MainViewModel mainViewModel
	
	onCreate()
		// 绑定vm数据
		binding = DataBindingUtil.setContentView(this, R.layout.activity_main)
		/*
			旧版本：
			mainViewModel = ViewModelProviders.of(this).get(MainViewModel.class)
		*/
		mainViewModel = new ViewModelProvider(this, new ViewModelProvider.AndroidViewModelFactory(getApplication()).get(MainViewModel.class))
		binding.setVm(mainViewModel)
		// 建立感应
		binding.setLifecycleowner(this)
```





##### BindingAdapter

@{}的代码扩展使用，自动被扫描进value对应的属性中

```
class XxxAdapter:
	@BindingAdapter(value={"imageUrl"})
	void loadUlr(view, url)
		view|view.getContext()
```







#### Lifecycles

观察Activity、Fragment生命周期的变化，执行观察者的代码、销毁观察者对象





#### ViewModel

存储LiveData数据，和修改LiveData的方法，ViewModelStore





#### LiveData

感应变化的数据，值变化能触发界面刷新



#### Room



#### Paging



#### Navigation



#### WorkManager





## API

```
android:
	R:
		attr:
			state_enabled:
			state_focused:
			state_pressed:
		drawable:
        id:
        layout:
		
	util:
		DisplayMetrics:
			heightPixels:
			widthPixels:
	view:
		View:
			findViewById():
	widget:
		Button:
		TextView:

androidx:
	constraintlayout:
		widget:
			ConstraintLayout:
	coordinatorlayout:
		widget:
			Coordinatorlayout:	
    fragment:
    	app:
    		Fragment:
	lifecycle:
		AndroidViewModel:
		LiveData:
			observe():
			postValue():
		MutableLiveData<T>:
		ViewModel
	viewpager:
		widget:
			ViewPager:


AppCompatActivity:
	findViewById():
	getApplicationContext():
	getLayoutInflater():
	getMenuInflater():
	getResources():
	getSupportFragmentManager():
	onAttachFragment():
	onContextItemSelected():
	onCreate():
	onCreateContextMenu():
	onCreateOptionsMenu():
	onOptionsItemSelected():
	onSupportNavigateUp():
	registerForContextMenu():
	setContentView():
	setSupportActionBar():
	startActionMode():
	startActivity():
Bundle:
Button:
	id:
	text:
ComponentName:
Drawable:
EditText:
	hint:
	getText():
EventActivity:
	this:
Fragment:
	getActivity():
	onActivityCreated():
	onCreateView():
FragmentManager:
	---
	add():
	beginTransaction():
	commit():
	commitNow():
	findFragmentById():
	remove():
FrameLayout:
GridLayout:
Handler:
	postDelayed():
ImageView:
	src:
	---
	getDrawable():
	setImageDrawable():
	setOnLongClickListener():
Intent:
	---
	setAction():
	setClassName():
	setComponent():
LayoutInflater:
	inflate():
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
RelativeLayout:
Space:
Spannable:
StateListDrawable:
StyleSpan:
TableLayout:
TextView:
	
View:
ViewGroup:
```





