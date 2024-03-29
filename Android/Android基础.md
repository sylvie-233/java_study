# Android基础

> Author: Sylvie233
>
> Date: 2023/5/8
>
> Point:  
> 	


## 基础介绍

Android版本

![](Android基础.assets/image-20230512104518844.png)


**Android技术架构**

![](Android基础.assets/image-20230512104600383.png)
![](Android基础.assets/image-20230512104649244.png)



Android单位
![](Android基础.assets/image-20230516081433185.png)



利用View+Adapter实现列表渲染











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
                    dimens.xml:
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
			CAMERA:
			RECORD_AUDIO:
			WRITE_CONTACTS:
			WRITE_EXTERNAL_STORAGE:
	>
	
	<applicatioin
		allowBackup:
		icon:
		label:
		roundIcon:
		supportsRtl:
		theme: @style/xxx应用样式
	>
		<service
            name:
        >
            <intent-filter>
                <action>
                <category>
        <receiver
            name:
        >
            <intent-filter>
                <action>
        <provider
        	authorities:
        	name:
        >
		<activity
			name:
			screenOrientation:
				portrait:
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
				<data
					mimeType:
					schema:
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



![](Android基础.assets/image-20230529204609668.png)













### 进程

- 前台进程
- 可见进程
- 服务进程
- 后台进程
- 空进程

![](Android基础.assets/image-20230526212325916.png)

![](Android基础.assets/image-20230526212352941.png)

![](Android基础.assets/image-20230526212522776.png)

![](Android基础.assets/image-20230526212539286.png)



### SDK

```
安装目录:
	/.temp:
	/build-tools:
	/emulator:
	/extras:
	/fonts:
	/lecenses:
	/patcher:
	/platforms:
	/platform-tools:
	/skins:
	/sources:
	/system-iamges:
	/tools:
	.knownPackages:
```









### adb

```
adb:
	-d:
	-e:
	-s:
	connect: 连接设备
	devices:
	get-state:
	install: 安装APK
		-r:
	kill-server:
	logcat: (V|D|I|W|E|F|S)
		-c;
		-f:
		-v:
			color:
			time:
	pull: 下拉文件
	push: 上传文件
	shell: 进入android系统
		am: ActivityManager页面管理
			start: 切换页面
				-n:
		cat:
			
		cmd:
		date:
		dumpsys: 获取系统当前运行信息
			activitys:
			battery:
			cpuinfo:
			meminfo:
			windown
		exit: 退出安卓系统
		input: 模拟输入
			keyevent: 系统案件
				3: Home
				4: 返回键
				24: 音量+
				25:	音量-+
			press:
			roll:
			swipe: 滑动内容
			tap: 点击指定位置
			text: 输入内容
		ls:
		monkey: 性能测试工具:压测
			--bugreport:
			--ignore-crashes:
			-p: 指定包名
			--pct-touch:
			-s:
			--throttle:
			-v: 日志等级
		pm: PackageManager包管理
			clear:
			list:
				packages: 列出安装的包
					-3:
					-s:
		top:
			
	uninstall: 卸载指定package
		-k:
	version: 版本
```


android调试工具：安卓调试桥


#### aapt

```
aapt:
	dump:
```





#### emulator

```

```


### APK

```
apk目录:
	/assets: 静态资源文件
	/com:
	/lib: 动态链接库文件
	/META-INF: 签名想那些
		CERT.RSA:
		CERT.SF:
		CHANGES:
		LICENSE:
		MANIFEST.MF:
		README:
	/org:
	/res: 资源文件
	/templates:
	AndroidManifest.xml:
	classes.dex: java字节码
	classes2.dex:
	resources.arsc: 二进制资源文件（映射表）
```






## 核心内容

### Activity

```
AppCompatActivity:
	onCreate():
	onSaveInstanceState():
	---
	findViewById():
	finish(): 结束Activity
```





#### 生命周期

![](Android基础.assets/image-20230515212223905.png)



状态转换

![](Android基础.assets/image-20230515212729735.png)



2个Activity的生命周期

![](Android基础.assets/image-20230515212911885.png)




屏幕翻转会导致activity销毁重建







#### Intent

```
Intent:
	ACTION_SEND:
	ACTION_VIEW: 打开浏览器
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



![](Android基础.assets/image-20230523210027518.png)



Intent解析

![](Android基础.assets/image-20230526184908883.png)



##### Bundle

```
Bundle:
	
```





##### ComponentName

```
ComponentName:
	
```



##### Action

```
Action:
	
```



![](Android基础.assets/image-20230523211841182.png)



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

![](Android基础.assets/image-20230516092736671.png)

![](Android基础.assets/image-20230516092907532.png)



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



#### TabLayout

```
TabLayout:
	
```





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

复选框



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


#### GridView
```yaml
GridView:
	
```

网格视图



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

图片视图控件



#### ListView

```yaml
ListView:
	setAdapter(): 设置适配器
```

列表视图

Adapter适配器




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

单选按钮


#### RadioGroup

```
RadioGroup:
	id:
	---
	setOnCheckedChangeListener():
```



#### RatingBar

```
RatingBar:
	---
	setOnRatinBarChangeListener():
```



#### RecyclerView

```
RecyclerView:
	
```



#### ScrollView

```
ScrollView:
	
```

上下滑动视图



#### SearchView

```
SearchView:
	
```





#### SeekBar

```
SeekBar:

	---
	setOnSeekBarChangeListener():
		onProgressChanged():
        onStartTrackingTouch():
        onStopTrackingTouch():
```





#### Spinner



#### SurfaceView

```
SurfaceView：
	
```





#### Switch

```
Switch:
	textOff:
	textOn:
	---
	setOnCheckedChangeListener():
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



#### TextureView

```
TextureView:
	
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


弹框显示



#### ToggleButton

```
ToggleButton:
	textOff:
	textOn:
	---
	isChecked():
```



#### VideoView

```
VideoView:
	
```



#### ViewPager

```
ViewPager:
	
```

左右滑动视图






#### WebView

```
WebView:
```

















### Content

#### R

```
R:
	drawable:
	id:
	layout:		
	string:
```







#### Context

```
Context:
	---
	getResources():
	getSharedPreferences():
```



#### Localization

```
Localization:
	---
	
```











#### Broadcast

 系统广播

![](Android基础.assets/image-20230526203325112.png)



##### BroadcastReceiver

```
BroadcastReceiver:
	onReceive():
```



#### Notification

```
Notification:
	Builder:
		---
			build():
			setAutoCancel():
			setContentIntent():
			setContentText():
			setContentTitle():
			setLargeIcon():
			setSmallIcon():
			setStyle():
			setWhen():
```



<img src="Android基础.assets/image-20230526204228386.png" alt="image-20230526204228386" style="zoom:67%;" />



##### NotificationManager

```
NotificationManager:
	---
	createNotificationChannel():
	notify():
```



##### NotificationChannel

```
NotificationChannel:
	
```





#### Handler

```
Handler:
	handleMessage():
	---
	post():
	postAtTime():
	postDelayed():
	removeCallbacks():
	sendMessage():
```



常配合Thread使用





##### Message

```
Message:
	replyTo:
	what:
	---
	obtain():
```





##### Looper

```
Looper:
	
```



##### HandlerThread

```
HandlerThread:
	
```





#### ContentProvider

```
ContentProvider:
	onCreate():
	getType():
	query():
	insert():
	delete():
	update():
	---
```

![image-20230601184522337](Android基础.assets/image-20230601184522337.png)

![image-20230601184608312](Android基础.assets/image-20230601184608312.png)



![image-20230601184620059](Android基础.assets/image-20230601184620059.png)



##### ContentResolve

```---
ContentResolve:
	---
	delete():
	insert():
	query():
```



##### ContentValues

```
ContentValues:
	
```



##### ContentUris

```
ContentUris:
	
```



##### UriMatcher

```
UriMatcher:
	
```









#### AsyncTask

```
AsyncTask:
	onPreExecute():
	doInBackground():
	onPostExecute():
	onProgressUpdate():
	---
	publishProgress():
```



##### Params	

##### Progress	

##### Result









#### Service

```
Service:
	onCreate():
	onStartCommand():
	onDestory():
	onBind():
	onUnbind():
	onRebind():
	---
```



![](Android基础.assets/image-20230528194012845.png)

##### IntentService

```
IntentService:
	onHandleIntent():
	onDestory():
	---
```



##### ServiceConnection

```
ServiceConnection:
	onServiceConnected():
	onServiceDisconnected():
	---
	
```

<img src="Android基础.assets/image-20230528204837631.png" alt="image-20230528204837631" style="zoom:67%;" />







##### Binder

##### IBinder

```
IBinder:
	
```





##### Messenger

```
Messenger:
	---
	getBinder():
	send():
```





#### MediaPlayer

```
MediaPlayer:
	create():
	---
	isPlayint():
	pause():
	prepare():
	release():
	reset():
	setAudioStreamType():
	setDataSource():
	setDisplay():
	start():
```



![](Android基础.assets/image-20230530185838661.png)







##### MediaRecorder

```
MediaRecorder:
	---
	prepare():
	release():
	reset():
	setAudioEncoder():
	setAudioSource():
	setOutputFilte():
	setOutputFormat():
	start():
	stop():
```



##### MediaController

```
MediaController:
	---
```





##### SurfaceView

```
SurfaceView:
	
	
	
SurfaceHolder:
	
```



##### VideoView

```
VideoView:
	---
	setMediaController():
	setVideoPath():
	start():
```



##### TextureView

```
TextureView:
	---
	setSurfaceTextureListener():
		onSurfaceTextureAvailable():
		onSurfaceTextureSizeChanged():
		onSUrfaceTextureDestroyed():
		onSurfaceTextureUpdated():
```



##### SurfaceTexture

```
SurfaceTexture:
	
```



##### ImageReader

```
ImageReader:
	---
	acquireNextImage():
	setOnImageAvailableListener():
	
```







##### Ringtone

```
Ringtone:
	
```



##### RingtoneManager

```
RingtoneManager:
	
```





##### AudioManager

```
AudioManager:
	
```



##### AudioAttributes

```
AudioAttributes:
	Builder():
	---
	
```



##### JetPlayer

```
JetPlayer:
	
```



##### SoundPool

```
SoundPool:
	
```



##### Camera2

![image-20230530210200629](Android基础.assets/image-20230530210200629.png)

![image-20230530210235035](Android基础.assets/image-20230530210235035.png)



##### CameraManager

```
CameraManager:
	---
	getCameraIdList():
	getCameraCharacteristics():
	openCamera():
	
CameraDevice:
	StateCallback:
		onOpened():
		onDisconnected():
		onError():
    ---
    close():
    createCaptureRequest():
    createCaptureSession():
	
CaptureRequest:
	Builder:
	---
	
	
CaptureSession:
	StateCallback:
		onConfigured():
		onConfigureFailed():
    ---
    setRepeatingRequest():
	
Surface:
	---
	
CameraCharacteristics:
	
StreamConfigurationMap:
	---
	getOutputSizes():
	
Size:
	---
	
```



















#### SharedPreferences

```
SharedPreferences:
	Editor:
		---
		putString():
		commit():
	---
	edit():
	getString():
```

![](Android基础.assets/image-20230528213451402.png)

![](Android基础.assets/image-20230528213542825.png)![image-20230528213615904](Android基础.assets/image-20230528213615904.png)![image-20230528213619783](Android基础.assets/image-20230528213619783.png)

![](Android基础.assets/image-20230528213624129.png)







![image-20230611215859355](Android基础.assets/image-20230611215859355.png)









##### PreferenceScreen

```
PreferenceScreen:
	---
	getSharedPreferences():
	registerSharedPreferenceChangeListener():
	unregisterSharedPreferenceChangeListener()
```



`preferences.xml`

```
<PreferenceScreen>
	<PreferenceCategory
		key:
		title:
		app:summary:
	>
		<CheckBoxPreference
			key:
            title:
            summary:
		>
		<EditTextPreference
			key:
			title:
			summary:
		>
		<ListPreference
			key:
			title:
			summary:
			entries:
			entryValues:
			dependency:
		>
```

<img src="Android基础.assets/image-20230528214945885.png" alt="image-20230528214945885" style="zoom:67%;" />



**PreferenceFragmentCompat**

```
PreferenceFragmentCompat:
	onCreatePreferences():
	---
	setPreferencesFromResource():
	findPreference(): 
	
OnHaredPreferenceChangeListener:
	onSharedPreferenceChanged():
	---
```



##### Preference

```
Preference:
	---
	setSummary():
```









#### 内部存储器

![](Android基础.assets/image-20230528220900529.png)







#### 外部存储

```
:
	DIRECTORY_ALARMS
    DIRECTORY_AUDIOBOOKS
    DIRECTORY_DCIM
    DIRECTORY_DOCUMENTS
    DIRECTORY_DOWNLOADS
    DIRECTORY_MOVIES
    DIRECTORY_MUSIC
    DIRECTORY_NOTIFICATIONS
    DIRECTORY_PICTURES
    DIRECTORY_PODCASTS
    DIRECTORY_RECORDINGS
    DIRECTORY_RINGTONES
    DIRECTORY_SCREENSHOTS
```



![](Android基础.assets/image-20230528223253130.png)



#### SQLite

##### SQLiteOpenHelper

```
SQLiteOpenHelper:
	OnCreate():
	OnUpgrade():
	---
	getWritableDatabase():
```



##### SQLiteDatabase

```
SQLiteDatabase:
	---
	delete():
	execSQL():
	isReadOnly():
	rawQuery():
	update():
```



##### Cursor

```
Cursor:
	---
	getColumnIndex():
	getString():
	isAfterLast():
	moveToFirst():
	moveToNext():
```



##### ContentValues

```
ContentValues:
	
```





#### Canvas

```
Canvas:
	---
	drawCircle():
	drawColor():
	drawPaht():
	drawRect():
```



##### Path

```
Path:
	---
	close():
	lineTo():
	moveTo():
```



##### Paint

```
Paint:
	---
	setColor():
	setStrokeWidth()):
	setStyle():
	setAntiAlias():
```

​	

##### AttributeSet

```
AttributeSet:
	
```



























 



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



#### Animation

##### \<set>

```
<set>
	<rotate
		fromDegrees:
		toDegrees:
		pivotx:
		pivotY:
		duration:
	>
	<scale
		fromXScale:
		toXScale:
		fromYScale:
		toYScale:
		pivotX:
		pivotY:
		duration:
	>
	<translate
		fromXDelta:
		toXDelta:
		duration:
	>
```




#### \<menu>

```
<menu>:
	<group>:
		<item>:
	<item>:
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
	<dimen
		name: "属性名"
	>
	<string>
	<string-array
		name:
	>
		<item
			name:
		>
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


#### \<set>

```
<set>
	<translate>
```

动画

#### \<shape>

```
<shape>
	<corners>
	<solid>
	<stroke>
```

#### \<vector>

```
<vector

>
	<path
		
	>
```





















## JetPack



Google推出的一套系列组件集



### AppCompat



### 数据绑定

![image-20230611190400188](Android基础.assets/image-20230611190400188.png)











#### DataBinding

```
<layout>
	<data>
		<variable
			name: _vm（通过@{_vm.xxx}使用VM属性）
			type: VM全类名
		>
		
	
    
		
		
---
ActivityMainBinding: （自动生成）
	
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





#### BindingAdapter

@{}的代码扩展使用，自动被扫描进value对应的属性中

```
class XxxAdapter:
	@BindingAdapter(value={"imageUrl"})
	void loadUlr(view, url)
		view|view.getContext()
```







### Lifecycles

```
Lifecycle:
	---
	addObserver():

LifecycleOwner:
	---

LifecycleObserver:
	onCreate():
	onStart():
	onResume():
	onPause():
	onStop():
	onDestroy():
	---
```



观察Activity、Fragment生命周期的变化，执行观察者的代码、销毁观察者对象





### ViewModel

```
ViewModel:
	SavedStateHandle:
		contains():
		getLiveData():
		set():
	---

ViewModelStore:


ViewModelStoreOwner:




AndroidViewModel:
	---
	
```

![image-20230611202320229](Android基础.assets/image-20230611202320229.png)





存储LiveData数据，和修改LiveData的方法，ViewModelStore

![image-20230611185323646](Android基础.assets/image-20230611185323646.png)

![image-20230611185407430](Android基础.assets/image-20230611185407430.png)



### LiveData

```
LiveData:
	---
	observe():
		Observer:
			onchanged():
		---
	
MutableLiveData:
	---
	postValue():
	setValue():
```



感应变化的数据，值变化能触发界面刷新



### Room

```
Room:
	databaseBuilder():
	---


注解:
	@ColumnInfo:
		name:
	@Entiry:
	@PrimaryKey:
		autoGenerate:
	---
	@Dao:
	@Delete:
	@Insert:
	@Query():
	@Update:
	---
	@Database:
		entities:
		version:
		exportSchema:
```



SQLite数据库抽象





### Paging



### Navigation

```
Navigation:
	createNavigateOnClickListener():
	findNavController():
```



![image-20230611221910702](Android基础.assets/image-20230611221910702.png)



Navigation常与fragment连用

![image-20230611230403339](Android基础.assets/image-20230611230403339.png)







#### navigation

##### nav_graph.xml

```

```



##### GRAPH



##### NavHostFragment

```
NavHostFragment:
	
```



NavHostFragment为Navigation入口容器

`NavHostFrament(activity_main.xml中的fragment)`->`nav_graph.xml(定义fragment跳转关系)`->`Fragment视图定义`->`xxxfragment.xml`











#### NavController

```
NavController:
	---
	navigate():
	navigateUp():
```

![image-20230611230151363](Android基础.assets/image-20230611230151363.png)









#### NavigationUI

```
NavigationUI:
	setupActionBarWithNavController():
		onSupportNavigateUp():
	---
```







### WorkManager









## JNI

```
System.loadLibrary(): Java加载库
（）
native xxx(): c++函数声明


--- .so库文件生成
#include <jni.h>

extern "C" JNIEXPORT jstring JNICALL
Java_包名_activity名_xxx(JNIEnv* env, jobject) {
	return env->NewStringUTF();
}
```















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
	bindService():
	checkSelfPermission():
	findViewById():
	finish():
	getApplicationContext():
	getExternalCacheDir():
	getExternalFilesDir():
	getExternalCacheDirs():
	getExternalFileDirs():
	getExternalMediaDirs():
	getIntent():
	getLayoutInflater():
	getMenuInflater():
	getPreferenceManager():
	getPreferenceScreen():
	getResources():
	getSharedPreferences():
	getSupportFragmentManager():
	getSystemService():
	onActivityResult():
	onAttachFragment():
	onContextItemSelected():
	onCreate():
	onCreateContextMenu():
	onCreateOptionsMenu():
	onOptionsItemSelected():
	onRequestPermissionsResult():
	onSupportNavigateUp():
	openFileInput():
	openFileOutput():
	registerForContextMenu():
	registerReceiver():
	requestPermissions():
	sendBroadcast():
	setContentView():
	setResult():
	setSupportActionBar():
	startActionMode():
	startActivity():
	startActivityForResult():
	startService():
	unbindService():
	unregisterReceiver():
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
	onDraw():
	---
	invalidate():
ViewGroup:
```





