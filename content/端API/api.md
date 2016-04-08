/*
Title: API对象
Description: API对象
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#attr-content">Attribute</a></li>
	<li><a href="#const-content">Constant</a></li>
	<li><a href="#evt-content">Event</a></li>
	<li><a href="#method-content">Method</a></li>
</ul>
<div id="attr-content">

<div class="outline">
[appId](#a27)

[appName](#a1)

[appVersion](#a3)

[systemType](#a13)

[systemVersion](#a14)

[version](#a15)

[deviceId](#a5)

[deviceToken](#a23)

[deviceModel](#a6)

[deviceName](#a7)

[operator](#a24)

[connectionType](#a4)

[fullScreen](#a11)

[screenWidth](#a25)

[screenHeight](#a26)

[winName](#a19)

[winWidth](#a20)

[winHeight](#a18)

[frameName](#a9)

[frameWidth](#a10)

[frameHeight](#a8)

[pageParam](#a12)

[wgtParam](#a16)

[appParam](#a2)

[wgtRootDir](#a17)

[fsDir](#a21)

[cacheDir](#a22)
</div>

#**概述**
api对象是您入门APICloud必须了解和熟练掌握的一个基础对象。api对象提供了构建应用程序所需要的一些基本的方法（method），如窗口操作、相册和网络数据访问等；以及一些常见的属性（Attrbute），如屏幕宽度（screenWidth），系统类型（systemType）等；还有一些常用事件，如电量低（batterylow）事件、应用进入后台（pause）事件。api对象不需要require引用，可以直接在js中使用。

#**appId**<div id="a27"></div>

应用的ID，可以在网站控制台概览里面查看，字符串类型

##示例代码

	var appId = api.appId; //比如: A6980386445546

##可用性

iOS系统，Android系统

可提供的1.1.0及更高版本

#**appName**<div id="a1"></div>

应用在桌面显示名称，字符串类型

##示例代码

	var appName = api.appName; //比如: AppLoader

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**appVersion**<div id="a3"></div>

应用版本号，字符串类型

##示例代码

	var appVersion = api.appVersion; // 比如: 1.0.0

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**systemType**<div id="a13"></div>

系统类型，如ios、android，取值范围详见[系统类型](!Constant#b18)常量，字符串类型

##示例代码

	var systemType = api.systemType;  // 比如: ios

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**systemVersion**<div id="a14"></div>

手机平台的系统版本，字符串类型

##示例代码

	var systemVersion = api.systemVersion;  // 比如: 8.0

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**version**<div id="a15"></div>

引擎版本信息，字符串类型

##示例代码

	var version = api.version;  //比如: 1.0.0

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**deviceId**<div id="a5"></div>

设备唯一标识，字符串类型

##示例代码

	var deviceId = api.deviceId;  //比如: FC408F8B-9598-48B6-A740-B9037ADCXXXE

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**deviceToken**<div id="a23"></div>

iOS中用于推送的Token，若未从系统获取到则返回空字符串，字符串类型

##示例代码

	var deviceToken = api.deviceToken;  //比如: a22241adab6c68b3687a9f0f086c540341f4b3f010546d4af4834ada32281615

##可用性

iOS系统

可提供的1.1.0及更高版本


#**deviceModel**<div id="a6"></div>

设备型号，字符串类型

##示例代码

	var deviceModel = api.deviceModel;  // 比如: iPhone 5

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**deviceName**<div id="a7"></div>

设备名称，字符串类型

##示例代码

	var deviceName = api.deviceName;  // 比如:“柚子”的 iPhone

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**operator**<div id="a24"></div>

运营商名称，若未获取到则返回none，字符串类型

##示例代码

	var operator = api.operator;  // 比如:中国移动

##可用性

iOS系统，Android系统

可提供的1.1.0及更高版本


#**connectionType**<div id="a4"></div>

当前网络连接类型，如2g、3g、4g、wifi等，取值范围详见[网络类型](!Constant#b16)常量，字符串类型

##示例代码

	var connectionType = api.connectionType;  //比如: wifi

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**fullScreen**<div id="a11"></div>

应用是否全屏，布尔类型，只支持iOS

##示例代码

	var fullScreen = api.fullScreen;  // 比如: true

##可用性

iOS系统

可提供的1.0.0及更高版本

#**screenWidth**<div id="a25"></div>

屏幕分辨率宽，数字类型

##示例代码

	var screenWidth = api.screenWidth;  // 比如: 640

##可用性

iOS系统，Android系统

可提供的1.1.0及更高版本

#**screenHeight**<div id="a26"></div>

屏幕分辨率高，数字类型

##示例代码

	var screenHeight = api.screenHeight;  // 比如: 960

##可用性

iOS系统，Android系统

可提供的1.1.0及更高版本


#**winName**<div id="a19"></div>

当前window名称，字符串类型

该属性值为openWin()时传递的name参数值，注意首页的名称为root

##示例代码

	var winName = api.winName;  //比如: root

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**winWidth**<div id="a20"></div>

当前window宽度，数字类型

此属性值不同于屏幕的分辨率，比如iPhone 5的分辨率为640*1136，但是其winWidth为320，因此前端需根据winWidth和winHeight来进行布局

##示例代码

	var winWidth = api.winWidth;  // 比如: 320

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**winHeight**<div id="a18"></div>

当前window高度，数字类型

此属性值不同于屏幕的分辨率，比如iPhone 5的分辨率为640*1136，但是其winHeight为568（若不使用iOS7风格则为548），因此前端需根据winWidth和winHeight来进行布局

##示例代码

	var winHeight = api.winHeight;  // 比如: 568

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**frameName**<div id="a9"></div>

frame名称，字符串类型

若当前环境为window中，则该属性值为空字符串

##示例代码

	var frameName = api.frameName;  //比如: trans-con

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**frameWidth**<div id="a10"></div>

frame宽度，数字类型

若当前环境为window中，则值和winWidth相同

##示例代码

	var frameWidth = api.frameWidth;  // 例如: 320

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**frameHeight**<div id="a8"></div>

frame高度，数字类型

若当前环境为window中，则值和winHeight相同

##示例代码

	var frameHeight = api.frameHeight;  // 比如: 504

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**pageParam**<div id="a12"></div>

页面参数，JSON对象类型

用于获取页面间传递的参数值，为openWin()、openFrame()等方法中的pageParam参数对应值

##示例代码

	var pageParam = api.pageParam; //比如: {"name" : "tans-con"}

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**wgtParam**<div id="a16"></div>

widget参数，JSON对象类型

用于获取widget间传递的参数值，为openWidget()方法中的wgtParam参数对应值

##示例代码

	var wgtParam = api.wgtParam;  //比如: {"name": "API Demo"}

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**appParam**<div id="a2"></div>

当应用被第三方应用打开时，传递过来的参数，字符串类型

##示例代码

	var appParam = api.appParam; // 比如: appLoader

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**wgtRootDir**<div id="a17"></div>

widget://协议对应的真实目录，即widget网页包的根目录，字符串类型

注意该目录为只读，不要往该目录下面写文件

##示例代码

```js
	var wgtRootDir = api.wgtRootDir;  
	/* 
	比如:  
	/private/var/mobile/Containers/Bundle/Application/56218B5B-1B59-48CD-8080-DAC54DB46446/UZApp.app/widget
	*/
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**fsDir**<div id="a21"></div>

fs://协议对应地真实目录，字符串类型

##示例代码
```js
	var fsDir = api.fsDir; 
	/* 
	例如: 
	/var/mobile/Containers/Data/Application/4E376FDE-D595-4E08-B0A4-A06561B31000/Documents/uzfs/A123456789
	*/
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**cacheDir**<div id="a22"></div>

cache://协议对应的真实目录，字符串类型

iOS平台下载的文件一般存放于该目录下，否则提交AppStore审核时可能会不通过，且此目录下的内容在手机备份时不会被备份

##示例代码
```js
	var cacheDir = api.cacheDir; 
	/* 
	例如: 
	/var/mobile/Containers/Data/Application/4E376FDE-D595-4E08-B0A4-A06561B31000/Library/Caches/APICloud/Cache/XXXXXX
	*/
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

</div>
<div id="const-content">

<div class="outline">
[toast位置](#b1)

[传感器类型](#b2)

[错误码](#b3)

[电话类型](#b4)

[定位精度](#b5)

[动画类型](#b6)

[动画曲线类型](#b7)

[动画子类型](#b8)

[进度提示框动画类型](#b9)

[进度提示框风格](#b10)

[媒体类型](#b11)

[拾取器类型](#b12)

[图片编码类型](#b13)

[图片数据格式](#b14)

[图片源类型](#b15)

[网络类型](#b16)

[文件操作错误码](#b17)

[系统类型](#b18)

[下载状态](#b19)

[异步请求错误类型](#b20)

[异步请求返回数据类型](#b21)

[异步请求方法类型](#b22)

[状态栏样式](#b23)

[屏幕旋转方向](#b24)

[上传状态](#b25)

[键盘弹出页面调整方式](#b26)

[缓存策略](#b27)
</div>

#**toast位置**<div id="b1"></div>

toast位置，字符串类型

用于toast()方法中location字段

##取值范围

```js
top			//顶部
middle		//中间
bottom		//底部
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**传感器类型**<div id="b2"></div>

传感器类型，字符串类型

用于startSensor()方法中type字段

##取值范围

```js
accelerometer		//加速计
gyroscope			//陀螺仪
magnetic_field		//地磁传感器
proximity			//近接传感器
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**错误码**<div id="b3"></div>

错误码，数字类型

##取值范围

```js
0		//错误
1		//没有指定模块
2		//没有指定方法
3		//参数不匹配
4		//没有权限
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**电话类型**<div id="b4"></div>

电话类型，字符串类型

用于call()方法中type字段

##取值范围

```js
tel				//直接拨打电话
tel_prompt		//iOS拨打电话之前会弹出提示框
facetime		//facetime通话，Android不支持
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**定位精度**<div id="b5"></div>

定位精度，字符串类型

根据需要来选择适当的精度来进行定位，用于startLocation()方法中accuracy字段

##取值范围

```js
10m		//精度在10米范围内
100m	//精度在100米范围内
1km		//精度在1千米范围内
3km		//精度在3千米范围内
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**动画类型**<div id="b6"></div>

打开window或打开widget时的动画类型，Android部分动画不支持，字符串类型

##取值范围

```js
none			//无动画效果
push			//新视图将旧视图推开
movein			//新视图移到旧视图上面
fade			//交叉淡化过渡（不支持过渡方向）
flip			//翻转效果
reveal			//将旧视图移开,显示下面的新视图
ripple			//滴水效果（不支持过渡方向）
curl			//向上翻一页
un_curl			//向下翻一页
suck			//收缩效果（不支持过渡方向）
cube			//立方体翻滚效果
```

##可用性

iOS系统，Android系统（flip，ripple，curl，un_curl，suck，cube类型不支持）

可提供的1.0.0及更高版本


#**动画曲线类型**<div id="b7"></div>

动画曲线类型，指定动画开始和结束时的快慢，字符串类型

用于animation()方法中curve字段

##取值范围

```js
ease_in_out		//开始和结束时慢
ease_in			//开始时慢
ease_out		//结束时慢
linear			//整个动画过程速率一样
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**动画子类型**<div id="b8"></div>

动画子类型，字符串类型

部分动画如fade可能没有过渡方向

##取值范围

```js
from_right		//从右边开始动画
from_left		//从左边开始动画
from_top		//从顶部开始动画
from_bottom		//从底部开始动画
```

##可用性

iOS系统，Android系统（仅限于from_right，from_left）

可提供的1.0.0及更高版本


#**进度提示框动画类型**<div id="b9"></div>

进度提示框动画类型，字符串类型

用于showProgress()方法中animationType字段

##取值范围

```js
fade		//渐隐渐现
zoom		//缩放
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**进度提示框风格**<div id="b10"></div>

进度提示框风格，字符串类型

用于showProgress()方法中style字段

##取值范围

```js
default		//默认
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**媒体类型**<div id="b11"></div>

媒体类型，字符串类型

用于getPicture()方法中mediaValue字段

##取值范围

```js
pic			//图片
video		//视频
all			//图片和视频，Android不支持
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**拾取器类型**<div id="b12"></div>

拾取器类型，字符串类型

用于openPicker()方法中type字段

##取值范围

```js
date			//日期
time			//时间
date_time		//日期和时间，Android不支持
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**图片编码类型**<div id="b13"></div>

图片编码类型，字符串类型

用于getPicture()方法中encodingType字段

##取值范围

```js
jpg		//指定图片格式为jpg
png		//指定图片格式为png
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**图片数据格式**<div id="b14"></div>

图片数据格式，字符串类型

用于getPicture()方法中destinationType字段

##取值范围

```js
base64		//指定返回数据为base64编码后内容
url			//指定返回数据为选取的图片地址
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**图片源类型**<div id="b15"></div>

图片源类型，字符串类型

用于getPicture()方法中sourceType字段

##取值范围

```js
library			//图片库
camera			//相机
album			//相册
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**网络类型**<div id="b16"></div>

网络类型，字符串类型

用于connectionType属性

##取值范围

```js
unknown			//未知
ethernet		//以太网
wifi			//wifi
2g				//2G网络
3g				//3G网络
4g				//4G网络
none			//无网络
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**文件操作错误码**<div id="b17"></div>

文件操作错误码，数字类型

指定readFile()、writeFile()方法返回错误时的错误类型

##取值范围

```js
0			//没有错误
1			//找不到文件错误
2			//不可读取错误
3			//编码格式错误
4			//无效操作错误
5			//无效修改错误
6			//磁盘溢出错误
7			//文件已存在错误
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**系统类型**<div id="b18"></div>

系统类型，字符串类型

用于systemType属性

##取值范围

```js
ios			//iOS系统
android		//Android系统
win			//Windows系统
wp			//Windows Phone系统
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**下载状态**<div id="b19"></div>

下载状态，数字类型

用于download()方法返回值中的state字段

##取值范围

```js
0			//下载中
1			//下载完成
2			//下载失败
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**异步请求错误类型**<div id="b20"></div>

异步请求错误类型，数字类型

用于ajax()方法返回错误时的code字段

##取值范围

```js
0		//连接错误
1		//超时
2		//授权错误
3		//数据类型错误
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**异步请求返回数据类型**<div id="b21"></div>

异步请求返回数据类型，字符串类型

用于ajax()方法中dataType字段

##取值范围

```js
json		//返回数据为JSON对象
text		//返回数据为字符串类型
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**异步请求方法类型**<div id="b22"></div>

异步请求方法类型，字符串类型

用于ajax()方法中method字段

##取值范围

```js
get
post
put
delete
head
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**状态栏样式**<div id="b23"></div>

状态栏样式，字符串类型

用于setStatusBarStyle()方法中style字段

##取值范围

```js
dark		//状态栏字体为黑色，适用于浅色背景
light		//状态栏字体为白色，适用于深色背景
```

##可用性

iOS系统

可提供的1.0.0及更高版本


#**屏幕旋转方向**<div id="b24"></div>

指定屏幕旋转到特定方向，或根据重力感应自动旋转，字符串类型

用于setScreenOrientation()方法中orientation字段

##取值范围

```js
portrait_up				//竖屏时，屏幕在home键的上面
portrait_down			//竖屏时，屏幕在home键的下面，部分手机不支持
landscape_left			//横屏时，屏幕在home键的左边
landscape_right			//横屏时，屏幕在home键的右边
auto					//屏幕根据重力感应在横竖屏间自动切换
auto_portrait			//屏幕根据重力感应在竖屏间自动切换
auto_landscape			//屏幕根据重力感应在横屏间自动切换
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**上传状态**<div id="b25"></div>

上传状态，数字类型

用于ajax()方法上传文件时返回值中的status字段

##取值范围

```js
0			//上传中
1			//上传完成
2			//上传失败
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**键盘弹出页面调整方式**<div id="b26"></div>

指定键盘弹出时，页面如何调整其内容，字符串类型

##取值范围

```js
resize			//若键盘盖住输入框，页面会自动上移
pan				//若键盘盖住输入框，页面不会自动上移
auto	    	//默认值，由系统决定如何处理，iOS平台该字段等同于resize
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**缓存策略**<div id="b27"></div>

缓存策略，字符串类型

用于imageCache()方法中的policy字段

##取值范围

```js
default						//默认为cache_else_network
cache_else_network			//若服务器上没有更新，则使用缓存
no_cache					//不使用缓存，始终从服务器获取
cache_only					//当缓存存在时，只从缓存中读取
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

</div>


<div id="evt-content">

<div class="outline">
[batterylow](#c1)

[batterystatus](#c2)

[keyback](#c3)

[keymenu](#c4)

[volumeup](#c21)

[volumedown](#c22)

[offline](#c5)

[online](#c6)

[pause](#c7)

[resume](#c8)

[scrolltobottom](#c9)

[shake](#c10)

[takescreenshot](#c24)

[swipedown](#c11)

[swipeleft](#c12)

[swiperight](#c13)

[swipeup](#c14)

[tap](#c15)

[longpress](#c23)

[viewappear](#c16)

[viewdisappear](#c17)

[noticeclicked](#c18)

[appintent](#c19)

[smartupdatefinish](#c20)
</div>

#**batterylow**<div id="c1"></div>

设备电池电量低事件，字符串类型

##callback(ret)

ret：

- 描述：返回电池电量和充电状态，不能为空

内部字段：

```js
{
	level:100,			//电池电量（0-100）
	isPlugged:true		//是否连接电源
}
```

##示例代码

```js
api.addEventListener({
	name:'batterylow'
},function(ret,err){
	api.alert({msg:'电池电量低'});
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**batterystatus**<div id="c2"></div>

设备电池状态改变事件，如电量变化或正在充电，字符串类型

##callback(ret)

ret:

- 描述：返回电池电量和充电状态，不能为空

内部字段：

```js
{
	level:100,			//电池电量（0-100）
	isPlugged:true		//是否连接电源
}
```

##示例代码

```js
api.addEventListener({
	name:'batterystatus'
},function(ret,err){
	var msg = '电池电量：'+ret.level;
	api.alert({msg:msg});
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**keyback**<div id="c3"></div>

设备back键被点击事件，仅Android平台有效，字符串类型

该事件必须在Window中注册才有效，Frame中注册无效，并且只在当前屏幕上的window才能收到回调。

##callback(ret)

ret:

- 描述：被点击的键值

内部字段：

```js
{
    keyCode:0				//被点击的按键
    longPress:false			//是否是长按
}
```

##示例代码

```js
api.addEventListener({
	name:'keyback'
},function(ret,err){
	//operation
});
```

##可用性

Android系统

可提供的1.0.0及更高版本


#**keymenu**<div id="c4"></div>

设备menu键被点击事件，仅Android平台有效

该事件必须在Window中注册才有效，Frame中注册无效，并且只在当前屏幕上的window才能收到回调。

##callback(ret)

ret:

- 描述：被点击的按键

内部字段：

```js
{
    keyCode:0				//被点击的按键
    longPress:false			//是否是长按
}
```

##示例代码

```js
api.addEventListener({
	name:'keymenu'
},function(ret,err){
	//operation
});
```

##可用性

Android系统

可提供的1.0.0及更高版本


#**volumeup**<div id="c21"></div>

设备音量加键被点击事件，仅Android平台有效

该事件必须在Window中注册才有效，Frame中注册无效，并且只在当前屏幕上的window才能收到回调。

##callback(ret)

ret:

- 描述：被点击的按键

内部字段：

```js
{
    keyCode:0				//被点击的按键
    longPress:false			//是否是长按
}
```

##示例代码

```js
api.addEventListener({
	name:'volumeup'
},function(ret,err){
	//operation
});
```

##可用性

Android系统

可提供的1.2.0及更高版本


#**volumedown**<div id="c22"></div>

设备音量减键被点击事件，仅Android平台有效

该事件必须在Window中注册才有效，Frame中注册无效，并且只在当前屏幕上的window才能收到回调。

##callback(ret)

ret:

- 描述：被点击的按键

内部字段：

```js
{
    keyCode:0				//被点击的按键
    longPress:false			//是否是长按
}
```

##示例代码

```js
api.addEventListener({
	name:'volumedown'
},function(ret,err){
	//operation
});
```

##可用性

Android系统

可提供的1.2.0及更高版本


#**offline**<div id="c5"></div>

监听设备断开网络的事件，字符串类型

##callback()

不能为空

##示例代码

```js
api.addEventListener({
	name:'offline'
},function(ret,err){
	//operation
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**online**<div id="c6"></div>

监听设备连接到网络的事件，字符串类型

##callback(ret, err)

ret:

- 描述：监听到网络连接时的返回数据

内部字段：

```js
{
	connectionType:''			//当前网络连接类型，如2g、3g、4g、wifi等
}
```

##示例代码

```js
api.addEventListener({
	name:'online'
},function(ret,err){
	var connectionType = ret.connectionType;
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**pause**<div id="c7"></div>

应用进入后台事件，字符串类型

##callback()

不能为空

##示例代码

```js
api.addEventListener({
	name:'pause'
},function(ret,err){
	//operation
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**resume**<div id="c8"></div>

应用从后台回到前台事件，字符串类型

##callback()

不能为空

##示例代码

```js
api.addEventListener({
	name:'resume'
},function(ret,err){
	//operation
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**scrolltobottom**<div id="c9"></div>

Window或者Frame页面滑动到底部事件，字符串类型

可用于实现滚动到底部，加载更多功能

##callback()

不能为空

##示例代码

```js
api.addEventListener({
	name:'scrolltobottom',
	extra:{
		threshold:0			//设置距离底部多少距离时触发，默认值为0，数字类型
	}
},function(ret,err){
	//operation
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**shake**<div id="c10"></div>

设备摇动事件，字符串类型。设置该监听后，当前APP将立即开启摇动检测功能。

可用于实现摇一摇功能

##callback()

不能为空

##示例代码

```js
api.addEventListener({
	name:'shake'
},function(ret,err){
	//operation
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**takescreenshot**<div id="c24"></div>

应用在前台运行期间，用户屏幕截图事件（比如同时按下了home键和电源键），只支持iOS。

##callback()

不能为空

##示例代码

```js
api.addEventListener({
	name:'takescreenshot'
},function(ret,err){
	//operation
});
```

##可用性

iOS系统

可提供的1.2.0及更高版本


#**swipedown**<div id="c11"></div>

Window或者Frame的页面全局向下轻扫事件，字符串类型

##callback()

不能为空

##示例代码

```js
api.addEventListener({
	name:'swipedown'
},function(ret,err){
	//operation
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**swipeleft**<div id="c12"></div>

Window或者Frame的页面全局向左轻扫事件，字符串类型

##callback()

不能为空

##示例代码

```js
api.addEventListener({
	name:'swipeleft'
},function(ret,err){
	//operation
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**swiperight**<div id="c13"></div>

Window或者Frame的页面全局向右轻扫事件，字符串类型

##callback()

不能为空

##示例代码

```js
api.addEventListener({
	name:'swiperight'
},function(ret,err){
	//operation
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**swipeup**<div id="c14"></div>

Window或者Frame的页面全局向上轻扫事件，字符串类型

##callback()

不能为空

##示例代码

```js
api.addEventListener({
	name:'swipeup'
},function(ret,err){
	//operation
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**tap**<div id="c15"></div>

Window或者Frame的页面全局单击事件，字符串类型。监听该事件后，点击window或者frame的任意位置，都将收到tap回调。

##callback()

不能为空

##示例代码

```js
api.addEventListener({
	name:'tap'
},function(ret,err){
	//operation
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**longpress**<div id="c23"></div>

Window或者Frame的页面全局长按事件，字符串类型。

##callback()

不能为空

##示例代码

```js
api.addEventListener({
	name:'longpress'
},function(ret,err){
	//operation
});
```

##可用性

iOS系统，Android系统

可提供的1.2.0及更高版本


#**viewappear**<div id="c16"></div>

Window显示到屏幕的事件，字符串类型。收到viewappear事件回调，即标识当前Window已经动画结束，并且完全显示到屏幕上。

该事件的作用对象为Window，Frame的显示不会收到事件

##callback()

不能为空

##示例代码

```js
api.addEventListener({
	name:'viewappear'
},function(ret,err){
	//operation
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**viewdisappear**<div id="c17"></div>

Window离开屏幕的事件，字符串类型。收到viewdisappear事件回调，即标识当前Window已经动画结束，并且完全从屏幕上移除。

该事件的作用对象为Window，Frame的隐藏不会收到事件

若是Window被关闭，此事件不会再回调

##callback()

不能为空

##示例代码

```js
api.addEventListener({
	name:'viewdisappear'
},function(ret,err){
	//operation
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**noticeclicked**<div id="c18"></div>

状态栏通知被用户点击后的回调，字符串类型

##callback(ret)

ret:

- 描述：通知被点击后的回调

内部字段：

```js
{
    type:0,			//内容来源类型。取值范围：0-APICloud收到的推送内容，1-开发者自定义的
    value:''		//内容，收到的推送内容或者由开发者发送通知时自行传入的，见notification接口中extra
}
```

##示例代码

```js
api.addEventListener({
	name:'noticeclicked'
},function(ret,err){
	var value = ret.value;
	if(ret.type == 0){
		//APICloud推送内容
	} else if(ret.type == 1){
		//开发者自定义消息
	}
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**appintent**<div id="c19"></div>

本应用被其他应用调起来时（Android平台也可以通过Activity打开），收到相关数据的回调，字符串类型

在任意页面中注册该监听后，如果本应用被其他应用调起，将触发该监听函数，同时将传给该应用的数据回调给网页

##callback(ret)

ret:

- 描述：其他应用或Activity传给本应用的数据

内部字段：

```js
{
	iosUrl:''			//其他应用打开本应用的url，只iOS有效，字符串类型
	sourceAppId:'' 		//其他应用的包名，iOS平台有可能为空字符串，字符串类型
	appParam:{}			//其他应用传递过来的参数，JSON或字符串类型
}
```

##示例代码

```js
api.addEventListener({
	name:'appintent'
},function(ret,err){
	var appParam = ret.appParam;
	if(api.systemType == 'ios'){
		var iosUrl = ret.iosUrl;
	} else {
		var sourceAppId = ret.sourceAppId;
	}
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**smartupdatefinish**<div id="c20"></div>

云修复使用静默修复时，更新完毕事件。可通过监听此事件来通知用户做是否强制重启应用等操作或者提示，以使更新生效，字符串类型

如果是提示修复，则不会触发该事件

##callback(ret)

ret：
- 类型：JSON对象

内部字段：
```js
{
    value:[{
        extra:''			//在控制台云修复里面进行静默修复时填写的附加信息，字符串类型
    }]
}
```


不能为空

##示例代码

```js
api.addEventListener({
	name:'smartupdatefinish'
},function(ret,err){
	var value = ret.value;
	var extra = value[0];
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


</div>

<div id="method-content">
<style type="text/css">
h4{clear: both; margin: 0; padding: 20px 0; font-weight: bold;}
</style>
<div class="outline">
<h4>窗口系统</h4>
<a href="#33" title="打开window">openWin</a>
<a href="#15" title="关闭window">closeWin</a>
<a href="#13" title="关闭到指定window">closeToWin</a>
<a href="#48" title="设置window属性">setWinAttr</a>
<a href="#27" title="打开frame">openFrame</a>
<a href="#10" title="关闭frame">closeFrame</a>
<a href="#41" title="设置frame属性">setFrameAttr</a>
<a href="#6" title="把frame带到前面">bringFrameToFront</a>
<a href="#40" title="把frame放到后面">sendFrameToBack</a>
<a href="#93" title="设置frame页面加载监听">setFrameClient</a>
<a href="#5" title="frame动画">animation</a>
<a href="#28" title="打开frame组">openFrameGroup</a>
<a href="#11" title="关闭frame组">closeFrameGroup</a>
<a href="#42" title="设置frame组属性">setFrameGroupAttr</a>
<a href="#43" title="设置frame组当前显示页面">setFrameGroupIndex</a>
<a href="#76" title="iPad上面打开弹出层window">openPopoverWin</a>
<a href="#77" title="关闭整个弹出层window，只iPad上面有效">closePopoverWin</a>
<a href="#30" title="打开侧滑布局">openSlidLayout</a>
<a href="#31" title="侧滑">openSlidPane</a>
<a href="#12" title="关闭侧滑">closeSlidPane</a>
<a href="#67" title="锁住SlidPane">lockSlidPane</a>
<a href="#68" title="解锁SlidPane">unlockSlidPane</a>
<a href="#89" title="打开抽屉式侧滑Window">openDrawerLayout</a>
<a href="#90" title="打开抽屉式侧滑Pane">openDrawerPane</a>
<a href="#91" title="关闭抽屉式侧滑Pane">closeDrawerPane</a>
<a href="#18" title="在指定页面执行脚本">execScript</a>
<a href="#63" title="手动移除启动页">removeLaunchView</a>
<a href="#34" title="手动移除启动页">parseTapmode</a>
<h4>应用管理</h4>
<a href="#23" title="安装应用">installApp</a>
<a href="#25" title="打开应用">openApp</a>
<a href="#75" title="判断设备是否已安装指定应用">appInstalled</a>
<a href="#92" title="重启应用">rebootApp</a>
<a href="#32" title="打开widget">openWidget</a>
<a href="#14" title="关闭widget">closeWidget</a>
<h4>网络通信</h4>
<a href="#3" title="跨域异步请求">ajax</a>
<a href="#86" title="取消异步请求">cancelAjax</a>
<a href="#17" title="开始下载">download</a>
<a href="#8" title="取消下载">cancelDownload</a>
<a href="#78" title="图片缓存">imageCache</a>
<h4>数据存储</h4>
<a href="#36" title="读文件">readFile</a>
<a href="#61" title="写文件">writeFile</a>
<a href="#45" title="设置偏好数据">setPrefs</a>
<a href="#21" title="获取偏好数据">getPrefs</a>
<a href="#39" title="删除偏好数据">removePrefs</a>
<a href="#9" title="清除缓存">clearCache</a>
<a href="#84" title="获取缓存大小">getCacheSize</a>
<a href="#85" title="获取剩余存储容量">getFreeDiskSpace</a>
<a href="#64" title="获取加密数据">loadSecureValue</a>
<h4>消息事件</h4>
<a href="#2" title="添加事件监听">addEventListener</a>
<a href="#38" title="移除事件监听">removeEventListener</a>
<a href="#72" title="发送事件">sendEvent</a>
<a href="#88" title="SuperWebView中js向原生发送消息">accessNative</a>
<a href="#65" title="弹出通知提示">notification</a>
<a href="#69" title="取消本应用弹出到状态栏的某个或所有通知">cancelNotification</a>
<h4>设备访问</h4>
<a href="#52" title="开始定位">startLocation</a>
<a href="#56" title="停止定位">stopLocation</a>
<a href="#19" title="获取位置信息">getLocation</a>
<a href="#55" title="打开传感器">startSensor</a>
<a href="#59" title="停止传感器">stopSensor</a>
<a href="#7" title="拨打电话">call</a>
<a href="#51" title="发送短信">sms</a>
<a href="#24" title="发送邮件">mail</a>
<a href="#26" title="打开系统通讯录">openContacts</a>
<a href="#44" title="是否隐藏状态栏">setFullScreen</a>
<a href="#47" title="设置状态栏样式">setStatusBarStyle</a>
<a href="#66" title="设置屏幕旋转方向">setScreenOrientation</a>
<a href="#71" title="设置是否禁止屏幕休眠">setKeepScreenOn</a>
<a href="#70" title="回到系统桌面">toLauncher</a>
<a href="#82" title="设置是否禁止截屏">setScreenSecure</a>
<a href="#83" title="设置应用图标右上角数字">setAppIconBadge</a>
<h4>UI组件</h4>
<a href="#4" title="带一个按钮的对话框">alert</a>
<a href="#16" title="带两个按钮的对话框">confirm</a>
<a href="#35" title="带两个按钮和输入框的对话框">prompt</a>
<a href="#1" title="弹出菜单">actionSheet</a>
<a href="#50" title="显示进度提示框">showProgress</a>
<a href="#22" title="隐藏进度提示框">hideProgress</a>
<a href="#60" title="自动消失的提示框">toast</a>
<a href="#29" title="时间选择器">openPicker</a>
<a href="#46" title="下拉刷新">setRefreshHeaderInfo</a>
<a href="#94" title="自定义下拉刷新">setCustomRefreshHeaderInfo</a>
<a href="#87" title="设置刷新中">refreshHeaderLoading</a>
<a href="#37" title="设置刷新完成">refreshHeaderLoadDone</a>
<a href="#49" title="显示悬浮按钮">showFloatBox</a>
<h4>多媒体</h4>
<a href="#20" title="从系统相册、相机获取图片">getPicture</a>
<a href="#81" title="保存图片和视频到系统相册">saveMediaToAlbum</a>
<a href="#54" title="开始录音">startRecord</a>
<a href="#58" title="停止录音">stopRecord</a>
<a href="#53" title="播放音频">startPlay</a>
<a href="#57" title="停止播放音频">stopPlay</a>
<a href="#62" title="播放视频">openVideo</a>
<h4>WebApp历史</h4>
<a href="#73" title="历史记录后退一页">historyBack</a>
<a href="#74" title="历史记录前进一页">historyForward</a>
<h4>其它</h4>
<a href="#79" title="页面向上滚动一页">pageUp</a>
<a href="#80" title="页面向下滚动一页">pageDown</a>

</div>

#**openWin**<div id="33"></div>

打开window

若window已存在，则会把该window显示到最前面，如果url和之前的url有变化，或者reload为true时，页面会刷新，但是该window里面已经打开的frame等不会移除

若当前正在进行openWin、closeWin等带动画过渡的window操作，调用此方法会失效

openWin({params})

##params

name：

- 类型：字符串
- 默认值：无
- 描述：window名字，不能为空字符串

url：

- 类型：字符串
- 默认值：无
- 描述：页面地址，可以为本地文件路径，支持相对路径和绝对路径，以及widget://、fs://等协议路径，也可以为远程地址

pageParam：

- 类型：JSON对象
- 默认值：无
- 描述：（可选项）页面参数，新页面中可以通过api.pageParam获取

bounces：

- 类型：布尔
- 默认值：若在config.xml里面配置了pageBounce，则默认值为配置的值，否则为false
- 描述：（可选项）页面是否弹动

bgColor：

- 类型：字符串
- 默认值：若在config.xml里面配置了windowBackground，则默认值为配置的值，否则透明
- 描述：（可选项）背景色，支持图片和颜色，格式为#fff、#ffffff、rgba(r,g,b,a)等，图片路径支持fs://、widget://等APICloud自定义文件路径协议，同时支持相对路径

scrollToTop：

- 类型：布尔
- 默认值：false
- 描述：（可选项）当点击状态栏，页面是否滚动到顶部。若当前屏幕上不止一个页面的scrollToTop属性为true，则所有的都不会起作用。只iOS有效

vScrollBarEnabled：

- 类型：布尔
- 默认值：true
- 描述：（可选项）是否显示垂直滚动条

hScrollBarEnabled：

- 类型：布尔
- 默认值：true
- 描述：（可选项）是否显示水平滚动条

scaleEnabled：

- 类型：布尔
- 默认值：false
- 描述：（可选项）页面是否可以缩放，为true时softInputMode参数无效

slidBackEnabled：

- 类型：布尔
- 默认值：true
- 描述：（可选项）是否支持滑动返回。iOS7.0及以上系统中，在新打开的页面中向右滑动，可以返回到上一个页面，该字段只iOS有效

slidBackType：

- 类型：字符串
- 默认值：full
- 描述：（可选项）当支持滑动返回时，设置手指在页面右滑的有效作用区域。取值范围（full:整个页面范围都可以右滑返回，edge:在页面左边缘右滑才可以返回），该字段只iOS有效

animation：

- 类型：JSON对象
- 默认值：无
- 描述：（可选项）动画参数，不传时使用默认动画，**type**：[动画类型](!Constant#b6)，**subType**：[动画子类型](!Constant#b8)。

内部字段：

```js
{
    type:"none",                //动画类型（详见动画类型常量）
    subType:"from_right",       //动画子类型（详见动画子类型常量）
    duration:300                //动画过渡时间，默认300毫秒
}
```

showProgress：

- 类型：布尔
- 默认值：false
- 描述：（可选项）是否显示等待框，此参数即将废弃，使用progress参数代替。若传了progress参数，此参数将忽略

progress：

- 类型：JSON对象
- 默认值：无
- 描述：（可选项）页面加载进度配置信息，若不传则无加载进度效果

内部字段：

```js
{
    type:"",            	//加载进度效果类型，默认值为default，取值范围为default|page，default等同于showProgress参数效果；为page时，进度效果为仿浏览器类型，固定在页面的顶部
    title:"",       		//type为default时显示的加载框标题
    text:"",                //type为default时显示的加载框内容
    color:""                //type为page时进度条的颜色，默认值为#45C01A，支持#FFF，#FFFFFF，rgb(255,255,255)，rgba(255,255,255,1.0)等格式
}
```

delay：

- 类型：数字
- 默认值：0
- 描述：（可选项）window显示延迟时间，适用于将被打开的window中可能需要打开有耗时操作的模块时，可延迟window展示到屏幕的时间，保持UI的整体性

reload：

- 类型：布尔
- 默认值：false
- 描述：（可选项）页面已经打开时，是否重新加载页面，重新加载页面后apiready方法将会被执行

allowEdit：

- 类型：布尔
- 默认值：false
- 描述：（可选项）是否允许长按页面时弹出选择菜单

softInputMode：

- 类型：字符串
- 默认值：auto
- 描述：（可选项）当键盘弹出时，输入框被盖住时，当前页面的调整方式，详见[键盘弹出页面调整方式](!Constant#b26)常量；只iOS有效，且当scaleEnabled参数为true时无效，Android请在config.xml里面配置并云编译使用

customRefreshHeader：

- 类型：字符串
- 默认值：无
- 描述：（可选项）设置使用自定义下拉刷新模块的名称，设置后可以使用api.setCustomRefreshHeaderInfo方法来使用自定义下拉刷新组件

##示例代码

```js
api.openWin({
	name: 'page1',
	url: './page1.html',
	pageParam: {
	    name: 'test'
	}
});
```

##补充说明

窗口操作

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**closeWin**<div id="15"></div>

关闭window

若当前正在进行openWin、closeWin等带动画过渡的window操作，调用此方法会失效

closeWin({params})

##params

name：

- 类型：字符串
- 默认值：无
- 描述：（可选项）window名字，不传时关闭当前window，为root时无效

animation：

- 类型：JSON对象
- 默认值：无
- 描述：（可选项）动画参数，不传时使用默认动画，**type**：[动画类型](!Constant#b6)，**subType**：[动画子类型](!Constant#b8)。

内部字段：
```js
{
    type:"none",                //动画类型（详见动画类型常量）
    subType:"from_right",       //动画子类型（详见动画子类型常量）
    duration:300                //动画过渡时间，默认300毫秒
}
```

##示例代码

```js
//关闭当前window，使用默认动画
api.closeWin();

//关闭指定window，使用指定动画，若待关闭的window不在最上面，则动画无效
api.closeWin({
    name: 'page1',
    animation: {
    	type: 'flip',
		subType: 'from_bottom',
		duration: 500
	}
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**closeToWin**<div id="13"></div>

关闭到指定window，最上面显示的window到指定name的window间的所有window都会被关闭

若当前正在进行openWin、closeWin等带动画过渡的window操作，调用此方法会失效

closeToWin({params})

##params

name：

- 类型：字符串
- 默认值：无
- 描述：window名字

animation：

- 类型：JSON对象
- 默认值：无
- 描述：（可选项）动画参数，不传时使用默认动画，**type**：[动画类型](!Constant#b6)，**subType**：[动画子类型](!Constant#b8)。

内部字段：

```js
{
    type:"none",                //动画类型（详见动画类型常量）
    subType:"from_right",       //动画子类型（详见动画子类型常量）
    duration:300                //动画过渡时间，默认300毫秒
}
```

##示例代码

```js
api.closeToWin({
	name: 'win1',
	animation: {
		type: 'flip',
		subType: 'from_bottom',
		duration: 500
	}
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**setWinAttr**<div id="48"></div>

设置window属性

setWinAttr({params})

##params

bounces：

- 类型：布尔
- 默认值：无
- 描述：（可选项）页面是否弹动

bgColor：

- 类型：字符串
- 默认值：无
- 描述：（可选项）背景色，支持图片和颜色，格式为#fff、#ffffff、rgba(r,g,b,a)等，图片路径支持fs://、widget://等APICloud自定义文件路径协议，同时支持相对路径

scrollToTop：

- 类型：布尔
- 默认值：无
- 描述：（可选项）当点击状态栏，页面是否滚动到顶部。若当前屏幕上不止一个页面的scrollToTop属性为true，则所有的都不会起作用。只iOS有效

vScrollBarEnabled：

- 类型：布尔
- 默认值：无
- 描述：（可选项）是否显示垂直滚动条

hScrollBarEnabled：

- 类型：布尔
- 默认值：无
- 描述：（可选项）是否显示水平滚动条

scaleEnabled：

- 类型：布尔
- 默认值：无
- 描述：（可选项）页面是否可以缩放，为true时softInputMode参数无效

slidBackEnabled：

- 类型：布尔
- 默认值：无
- 描述：（可选项）是否支持滑动返回。iOS7.0及以上系统中，在新打开的页面中向右滑动，可以返回到上一个页面，该字段只iOS有效

softInputMode：

- 类型：字符串
- 默认值：无
- 描述：（可选项）当键盘弹出时，输入框被盖住时，当前页面的调整方式，详见[键盘弹出页面调整方式](!Constant#b26)常量；只iOS有效，且当scaleEnabled参数为true时无效，Android请在config.xml里面配置并云编译使用

##示例代码

```js
api.setWinAttr({
	bounces: true,
	bgColor: '#fff',
	vScrollBarEnabled: true,
	hScrollBarEnabled: true,
	scaleEnabled: true,
	slidBackEnabled: true
});
```
 
##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**openFrame**<div id="27"></div>

打开frame

若frame已存在，则会把该窗口显示到最前面并显示，如果url和之前的url有变化，或者reload为true时，页面会刷新

此方法对frameGroup里面的frame不起作用

openFrame({params})

##params

name：

- 类型：字符串
- 默认值：无
- 描述：frame名字

url：

- 类型：字符串
- 默认值：无
- 描述：页面地址，可以为本地文件路径，支持相对路径和绝对路径，以及widget://、fs://等协议路径，也可以为远程地址

pageParam：

- 类型：JSON对象
- 默认值：无
- 描述：（可选项）页面参数，在新页面通过api.pageParam获取

bounces：

- 类型：布尔
- 默认值：若在config.xml里面配置了pageBounce，则默认值为配置的值，否则为true
- 描述：（可选项）页面是否弹动

bgColor：

- 类型：字符串
- 默认值：若在config.xml里面配置了frameBackgroundColor，则默认值为配置的值，否则透明
- 描述：（可选项）背景色，支持图片和颜色，格式为#fff、#ffffff、rgba(r,g,b,a)等，图片路径支持fs://、widget://等APICloud自定义文件路径协议，同时支持相对路径

scrollToTop：

- 类型：布尔
- 默认值：true
- 描述：（可选项）当点击状态栏，页面是否滚动到顶部。若当前屏幕上不止一个页面的scrollToTop属性为true，则所有的都不会起作用。只iOS有效

vScrollBarEnabled：

- 类型：布尔
- 默认值：true
- 描述：（可选项）是否显示垂直滚动条

hScrollBarEnabled：

- 类型：布尔
- 默认值：true
- 描述：（可选项）是否显示水平滚动条

scaleEnabled：

- 类型：布尔
- 默认值：false
- 描述：（可选项）页面是否可以缩放，为true时softInputMode参数无效

rect：

- 类型：JSON对象
- 默认值：充满整个父页面
- 描述：（可选项）frame的位置和大小，设置margin后，在不同手机上面会保持与父页面的各方向边距一致，而中间区域会自动扩充。

内部字段：

```js
{
    x:0,             //左上角x坐标
    y:0,             //左上角y坐标
    w:320,           //宽度，若传'auto'，页面从x位置开始自动充满父页面宽度
    h:480            //高度，若传'auto'，页面从y位置开始自动充满父页面高度
    
    marginLeft:0,	//相对父window左外边距的距离
    
    marginTop:0,	//相对父window上外边距的距离
    
    marginBottom:0,	//相对父window下外边距的距离
    
    marginRight:0	//相对父window右外边距的距离
}
```

showProgress：

- 类型：布尔
- 默认值：false
- 描述：（可选项）是否显示等待框，此参数即将废弃，使用progress参数代替。若传了progress参数，此参数将忽略

progress：

- 类型：JSON对象
- 默认值：无
- 描述：（可选项）页面加载进度配置信息，若不传则无加载进度效果

内部字段：

```js
{
    type:"",            	//加载进度效果类型，默认值为default，取值范围为default|page，default等同于showProgress参数效果；为page时，进度效果为仿浏览器类型，固定在页面的顶部
    title:"",       		//type为default时显示的加载框标题
    text:"",                //type为default时显示的加载框内容
    color:""                //type为page时进度条的颜色，默认值为#45C01A，支持#FFF，#FFFFFF，rgb(255,255,255)，rgba(255,255,255,1.0)等格式
}
```

reload：

- 类型：布尔
- 默认值：false
- 描述：（可选项）页面已经打开时，是否重新加载页面

allowEdit：

- 类型：布尔
- 默认值：false
- 描述：（可选项）是否允许长按页面时弹出选择菜单

softInputMode：

- 类型：字符串
- 默认值：auto
- 描述：（可选项）当键盘弹出时，输入框被盖住时，当前页面的调整方式，详见[键盘弹出页面调整方式](!Constant#b26)常量；只iOS有效，且当scaleEnabled参数为true时无效，Android请在config.xml里面配置并云编译使用

animation：

- 类型：JSON对象
- 默认值：无
- 描述：（可选项）动画参数，不传时无动画，**type**：[动画类型](!Constant#b6)，**subType**：[动画子类型](!Constant#b8)。

内部字段：

```js
{
    type:"none",                //动画类型（详见动画类型常量）
    subType:"from_right",       //动画子类型（详见动画子类型常量）
    duration:300                //动画过渡时间，默认300毫秒
}
```

customRefreshHeader：

- 类型：字符串
- 默认值：无
- 描述：（可选项）设置使用自定义下拉刷新模块的名称，设置后可以使用api.setCustomRefreshHeaderInfo方法来使用自定义下拉刷新组件

##示例代码

```js
api.openFrame({
	name: 'page2',
	url: './page2.html',
	rect: {
		x: 0,
		y: 0,
		w: 320,
		h: 480
	},
	pageParam: {
	    name: 'test'
	},
	bounces: true,
	bgColor: 'rgba(0,0,0,0)',
	vScrollBarEnabled: true,
	hScrollBarEnabled: true
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**closeFrame**<div id="10"></div>

关闭frame

closeFrame({params})

##params

name：

- 类型：字符串
- 默认值：无
- 描述：（可选项）frame名字，不传时关闭当前frame

##示例代码

```js
api.closeFrame({
	name: 'page2'
});
```
##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**setFrameAttr**<div id="41"></div>

设置frame属性

setFrameAttr({params})

##params

name：

- 类型：字符串
- 默认值：无
- 描述：frame名称

bounces：

- 类型：布尔
- 默认值：无
- 描述：（可选项）页面是否弹动

hidden：

- 类型：布尔
- 默认值：无
- 描述：（可选项）本frame是否隐藏（隐藏即从屏幕上移除，但不销毁）

bgColor：

- 类型：字符串
- 默认值：无
- 描述：（可选项）背景色，支持图片和颜色，格式为#fff、#ffffff、rgba(r,g,b,a)等，图片路径支持fs://、widget://等APICloud自定义文件路径协议，同时支持相对路径

scrollToTop：

- 类型：布尔
- 默认值：无
- 描述：（可选项）当点击状态栏，页面是否滚动到顶部。若当前屏幕上不止一个页面的scrollToTop属性为true，则所有的都不会起作用。只iOS有效

vScrollBarEnabled：

- 类型：布尔
- 默认值：无
- 描述：（可选项）是否显示垂直滚动条

hScrollBarEnabled：

- 类型：布尔
- 默认值：无
- 描述：（可选项）是否显示水平滚动条

scaleEnabled：

- 类型：布尔
- 默认值：无
- 描述：（可选项）页面是否可以缩放，为true时softInputMode参数无效

rect：

- 类型：JSON对象
- 默认值：无
- 描述：（可选项）窗口区域

内部字段：
```js
{
    x:0,                 //左上角x坐标
    y:0,                 //左上角y坐标
    w:320,               //宽度，若传'auto'，页面从x位置开始自动充满父页面宽度
    h:480                //高度，若传'auto'，页面从y位置开始自动充满父页面高度
}
```

softInputMode：

- 类型：字符串
- 默认值：无
- 描述：（可选项）当键盘弹出时，输入框被盖住时，当前页面的调整方式，详见[键盘弹出页面调整方式](!Constant#b26)常量；只iOS有效，且当scaleEnabled参数为true时无效，Android请在config.xml里面配置并云编译使用

##示例代码

```js
api.setFrameAttr({
	name: 'page2',
	rect: {
		x: 0,
		y: 0,
		w: 320,
		h: 480
	},
	bounces: true,
	bgColor: '#fff',
	vScrollBarEnabled: true,
	hScrollBarEnabled: true
});
```

##补充说明

设置frame属性

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**bringFrameToFront**<div id="6"></div>

调整frame到前面

bringFrameToFront({params})

##params

from：

- 类型：字符串
- 默认值：无
- 描述：待调整显示顺序的frame名字

to：

- 类型：字符串
- 默认值：无
- 描述：（可选项）frame名字，不传时调整from对应frame到最前面，否则调整from对应frame到此frame前面

##示例代码

```js
api.bringFrameToFront({
	from: 'page1',
	to: 'page2'
});
```

##补充说明

调整frame到前面

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**sendFrameToBack**<div id="40"></div>

调整frame到后面

sendFrameToBack({params})

##params

from：

- 类型：字符串
- 默认值：无
- 描述：frame名字

to：

- 类型：字符串
- 默认值：无
- 描述：（可选项）frame名字，不传时调整from对应frame到最后面，否则调整from对应frame到此frame后面

##示例代码

```js
api.sendFrameToBack ({
	from: 'page1',
	to: 'page2'
});
```

##补充说明

调整frame到后面

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**setFrameClient**<div id="93"></div>

设置指定frame的页面加载监听，仅在window中调用生效，可以对多个frame进行监听。

setFrameClient({params}, callback(ret, err))

##params

frameName：

- 类型：字符串
- 默认值：无
- 描述：frame名字

##callback(ret, err)

ret：

- 类型：JSON对象
- 描述：frame加载状态、加载进度等发生变化时的回调

内部字段：

```js
{
	state:0,			//加载状态，数字类型，取值范围：0-开始加载；1-加载进度发生变化；2-结束加载；3-title发生变化；4-url发生变化
	progress:0,			//state为1时，页面的加载进度，数字类型，取值范围0-100
	title:'',			//state为3时，页面当前的title，字符串类型
	url:''				//state为0|2|4时，页面当前的url，字符串类型
}
```

##示例代码

```js
api.setFrameClient({
	frameName:'webpage'
}, function(ret, err){
	switch (ret.state) {
		case 0:
			break;
		case 1:
			break;
		case 2:
			break;
		case 3:
			break;
		case 4:
			break;
		default:
			break;
	}
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.2.0及更高版本


#**animation**<div id="5"></div>

frame动画，支持平移，缩放，旋转和透明度变化

仅支持frame，不支持window以及frameGroup里面的frame

animation({params}, callback())

##params

name：

- 类型：字符串
- 默认值：当前frame
- 描述：frame名字

delay：

- 类型：数字
- 默认值：0
- 描述：（可选项）动画延迟时间，单位毫秒，默认立即开始

duration：

- 类型：数字
- 默认值：0
- 描述：（可选项）动画过渡时间，单位毫秒

curve：

- 类型：字符串
- 默认值：ease_in_out
- 描述：（可选项）动画曲线类型，指定动画开始和结束时的快慢，详见动画曲线类型

repeatCount：

- 类型：数字
- 默认值：0
- 描述：（可选项）动画次数，默认不重复，为-1时无限重复

autoreverse：

- 类型：布尔
- 默认值：false
- 描述：（可选项）一次动画结束后是否自动反转动画

alpha：

- 类型：数字
- 默认值：无
- 描述：（可选项）整个页面的透明度，介于0 1之间，Android不支持

translation：

- 类型：JSON
- 默认值：无
- 描述：（可选项）位置平移参数

内部字段：

```js
{
    x: 0,         //x轴方向上的平移距离，默认为0
    y: 0,         //y轴方向上的平移距离，默认为0
    z: 0          //z轴方向上的平移距离，默认为0，Android不支持
}
```

scale：

- 类型：JSON
- 默认值：无
- 描述：（可选项）页面缩放参数，Android不支持

内部字段：

```js
{
    x: 1,         //x轴方向上的放大倍率，默认为1
    y: 1,         //y轴方向上的放大倍率，默认为1
    z: 1          //z轴方向上的放大倍率，默认为1
}
```

rotation：

- 类型：JSON
- 默认值：无
- 描述：（可选项）页面旋转参数，Android不支持

内部字段：

```js
{
    degree:0,     //旋转角度，默认0
    x: 0,         //绕x轴旋转，默认为0
    y: 0,         //绕y轴旋转，默认为0
    z: 1          //绕z轴旋转，默认为1
}
```

##callback(ret, err)

动画结束后的回调

##示例代码

```js
api.animation ({
	name: 'page1',
	delay: 1000,
	duration: 3000,
	curve: 'ease_in',
	repeatCount: 2,
	autoreverse: true,
	alpha: 0.6,
	translation: {
	    x: 0,
	    y: 100,
	    z: 0
	}, 
	scale: {
	    x: 1.2,
	    y: 1,
	    z: 1
	},
	rotation: {
	    degree: 45,
	    x: 0,
	    y: 0,
	    z: 1
	}
}, function( ret, err ) {
	api.alert({msg: '动画结束'});
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**openFrameGroup**<div id="28"></div>

打开frame组

frame组打开后，当前页面加载完成后，页面会预加载后面指定个数页面

openFrameGroup({params}, callback(ret, err))

##params

name：

- 类型：字符串
- 默认值：无
- 描述：frame组名字

background：

- 类型：字符串
- 默认值：无
- 描述：（可选项）frame组背景，颜色（#fff,#ffffff,rgba(r,g,b,a)）或图片（支持文件路径协议和相对路径）

scrollEnabled：

- 类型：布尔
- 默认值：true
- 描述：（可选项）frame组是否能够左右滚动

rect：

- 类型：JSON对象
- 默认值：充满整个父页面
- 描述：（可选项）frameGroup的位置和大小，设置margin后，在不同手机上面会保持与父页面的各方向边距一致，而中间区域会自动扩充。

内部字段：

```js
{
    x:0,             //左上角x坐标
    y:0,             //左上角y坐标
    w:320,           //宽度，若传'auto'，页面从x位置开始自动充满父页面宽度
    h:480，          //高度，若传'auto'，页面从y位置开始自动充满父页面高度
    
    marginLeft:0,	//相对父window左外边距的距离
    marginTop:0,	//相对父window上外边距的距离
    marginBottom:0,	//相对父window下外边距的距离
    marginRight:0	//相对父window右外边距的距离
}
```

index：

- 类型：数字
- 默认值：0
- 描述：（可选项）默认显示的页面索引

preload：

- 类型：数字
- 默认值：1
- 描述：（可选项）预加载的frame个数，默认加载当前页后面一个

frames：

- 类型：数组
- 默认值：无
- 描述：frame数组

内部字段：

```js
[{
	name:'',                                //frame名字，字符串类型，不能为空字符串
	url:'',                                 //页面地址，可以为本地文件路径，支持相对路径和绝对路径，以及widget://、fs://等协议路径，也可以为远程地址，字符串类型
	pageParam:{},                           //（可选项）页面参数，页面中可以通过api.pageParam获取，JSON对象
	bounces:true,                           //（可选项）是否弹动，布尔型，默认值：若在config.xml里面配置了pageBounce，则默认值为配置的值，否则为false
	bgColor:'#fff',                         //（可选项）背景色，支持图片和颜色，格式为#fff、#ffffff、rgba(r,g,b,a)等，图片路径支持fs://、widget://等APICloud自定义文件路径协议，同时支持相对路径
	scrollToTop:true						//（可选项）当点击状态栏，页面是否滚动到顶部。若当前屏幕上不止一个页面的scrollToTop属性为true，则所有的都不会起作用。默认值：true。只iOS有效
	vScrollBarEnabled:true,                 //（可选项）是否显示垂直滚动条，布尔型，默认值：true
	hScrollBarEnabled:false,                //（可选项）是否显示水平滚动条，布尔型，默认值：false
	scaleEnabled:true,                      //（可选项）页面是否可以缩放，为true时softInputMode参数无效，布尔型，默认值：false
	allowEdit:false,						//（可选项）是否允许长按页面时弹出选择菜单
	softInputMode:'auto'		            //（可选项）当键盘弹出时，输入框被盖住时，当前页面的调整方式，参考键盘弹出页面调整方式常量，只iOS有效，且当scaleEnabled参数为true时无效
	customRefreshHeader:''					//（可选项）设置使用自定义下拉刷新模块的名称，设置后可以使用api.setCustomRefreshHeaderInfo方法来使用自定义下拉刷新组件
}]
```

##callback(ret, err)

ret：

- 类型：JSON对象
- 描述：当前显示在屏幕上的frame变化时会回调

内部字段：

```js
{
    name:'',         //当前frame名称
    index:0          //当前frame索引
}
```

##示例代码

```js
api.openFrameGroup ({
	name: 'group1',
	background: '#fff',
	scrollEnabled: false,
	rect: {
	     x: 0, 
	     y: 0, 
	     w: 'auto', 
	     h: 'auto'
	},
	index: 1,
	frames: [{
		name: 'frame1', 
		url: 'frame1.html',
		bgColor: '#fff'
    },{
        name: 'frame2', 
		url: 'frame2.html', 
		bgColor: '#fff'
    }]
}, function( ret, err ){
    if( ret ){
         alert( JSON.stringify( ret ) );
    }else{
         alert( JSON.stringify( err ) );
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**closeFrameGroup**<div id="11"></div>

关闭frame组

closeFrameGroup({params})

##params

name：

- 类型：字符串
- 默认值：无
- 描述：frame组名字

##示例代码

```js
api.closeFrameGroup({
	name: 'group1'
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**setFrameGroupAttr**<div id="42"></div>

设置frame组属性

setFrameGroupAttr({params})

##params

name：

- 类型：字符串
- 默认值：无
- 描述：frame组名字

hidden：

- 类型：布尔
- 默认值：无
- 描述：（可选项）frame组是否隐藏

scrollEnabled：

- 类型：布尔
- 默认值：无
- 描述：（可选项）frame组是否能够左右滚动

rect：

- 类型：JSON对象
- 默认值：无
- 描述：（可选项）frame组区域

内部字段：

```js
{
    x:0,             //左上角x坐标
    y:0,             //左上角y坐标
    w:320,           //宽度，若传'auto'，frame组从x位置开始自动充满父页面宽度
    h:240            //高度，若传'auto'，frame组从y位置开始自动充满父页面高度
}
```

##示例代码

```js
api.setFrameGroupAttr({
    name: 'group1',
    hidden: true
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**setFrameGroupIndex**<div id="43"></div>

设置frame组当前可见frame

setFrameGroupIndex({params})

##params

name：

- 类型：字符串
- 默认值：无
- 描述：frame组名字

index：

- 类型：数字
- 默认值：无
- 描述：frame索引

scroll：

- 类型：布尔
- 默认值：false
- 描述：（可选项）是否平滑滚动至目标窗口，即是否带有动画

reload：

- 类型：布尔
- 默认值：false
- 描述：（可选项）是否刷新frame

##示例代码

```js
api.setFrameGroupIndex({
    name: 'group1',
    index: 2,
    scroll: true
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**openPopoverWin**<div id="76"></div>

iPad上面打开弹出层窗口，弹出层从底部往上弹出，然后显示在屏幕中间一片指定区域，周围为黑色半透明，只iPad上面有效

弹出层是模态的，弹出层后面的界面将不可操作，在弹出层窗口里面不能再打开弹出窗口

弹出层里面页面可以使用所有的window和frame相关操作，如openWin、openFrame等

使用execScript()方法时，引擎只会在整个弹出层里面的窗口中去寻找要执行脚本的窗口，如果要和弹出层下面的窗口间进行通信，可以使用sendEvent()方法代替实现

openPopoverWin({params})

##params

width：

- 类型：数字
- 默认值：540
- 描述：（可选项）弹出窗口在屏幕中间显示的宽度

height：

- 类型：数字
- 默认值：620
- 描述：（可选项）弹出窗口在屏幕中间显示的高度

name：

- 类型：字符串
- 默认值：无
- 描述：弹出层的第一个window的名字，不能为空字符串

url：

- 类型：字符串
- 默认值：无
- 描述：弹出层的第一个window页面地址，可以为本地文件路径，支持相对路径和绝对路径，以及widget://、fs://等协议路径，也可以为远程地址，不能为空字符串

pageParam：

- 类型：JSON对象
- 默认值：无
- 描述：（可选项）页面参数，新页面中可以通过api.pageParam获取

bounces：

- 类型：布尔
- 默认值：若在config.xml里面配置了pageBounce，则默认值为配置的值，否则为false
- 描述：（可选项）页面是否弹动

bgColor：

- 类型：字符串
- 默认值：若在config.xml里面配置了windowBackground，则默认值为配置的值，否则透明
- 描述：（可选项）背景色，支持图片和颜色，格式为#fff、#ffffff、rgba(r,g,b,a)等，图片路径支持fs://、widget://等APICloud自定义文件路径协议，同时支持相对路径

scrollToTop：

- 类型：布尔
- 默认值：false
- 描述：（可选项）当点击状态栏，页面是否滚动到顶部。若当前屏幕上不止一个页面的scrollToTop属性为true，则所有的都不会起作用。只iOS有效

vScrollBarEnabled：

- 类型：布尔
- 默认值：true
- 描述：（可选项）是否显示垂直滚动条

hScrollBarEnabled：

- 类型：布尔
- 默认值：true
- 描述：（可选项）是否显示水平滚动条

scaleEnabled：

- 类型：布尔
- 默认值：false
- 描述：（可选项）页面是否可以缩放，为true时softInputMode参数无效

showProgress：

- 类型：布尔
- 默认值：false
- 描述：（可选项）是否显示等待框，此参数即将废弃，使用progress参数代替。若传了progress参数，此参数将忽略

progress：

- 类型：JSON对象
- 默认值：无
- 描述：（可选项）页面加载进度配置信息，若不传则无加载进度效果

内部字段：

```js
{
    type:"",            	//加载进度效果类型，默认值为default，取值范围为default|page，default等同于showProgress参数效果；为page时，进度效果为仿浏览器类型，固定在页面的顶部
    title:"",       		//type为default时显示的加载框标题
    text:"",                //type为default时显示的加载框内容
    color:""                //type为page时进度条的颜色，默认值为#45C01A，支持#FFF，#FFFFFF，rgb(255,255,255)，rgba(255,255,255,1.0)等格式
}
```

allowEdit：

- 类型：布尔
- 默认值：false
- 描述：（可选项）是否允许长按页面时弹出选择菜单

softInputMode：

- 类型：字符串
- 默认值：auto
- 描述：（可选项）当键盘弹出时，输入框被盖住时，当前页面的调整方式，详见[键盘弹出页面调整方式](!Constant#b26)常量；只iOS有效，且当scaleEnabled参数为true时无效，Android请在config.xml里面配置并云编译使用

customRefreshHeader：

- 类型：字符串
- 默认值：无
- 描述：（可选项）设置使用自定义下拉刷新模块的名称，设置后可以使用api.setCustomRefreshHeaderInfo方法来使用自定义下拉刷新组件

##示例代码

```js
api.openPopoverWin({
	width: 480,
	height: 400,
	name: 'page1',
	url: './page1.html'
});
```

##补充说明

无

##可用性

iOS系统

可提供的1.0.0及更高版本


#**closePopoverWin**<div id="77"></div>

关闭整个弹出层窗口，只iPad上面有效

在当前弹出层里面的任意页面里面调用都会关闭整个弹出层

closePopoverWin()

##示例代码

```js
api.closePopoverWin();
```

##补充说明

无

##可用性

iOS系统

可提供的1.0.0及更高版本


#**openSlidLayout**<div id="30"></div>

打开侧滑式布局

打开后，其所在window的name默认为slidLayout，所以关闭整个侧滑布局可以通过api.closeWin({name:'slidLayout'})实现，同时可以通过api.openWin({name:'slidLayout'})来把整个侧滑显示到最前面

openSlidLayout({params}, callback(ret, err))

##params

type：

- 类型：字符串
- 默认值：all
- 描述：（可选项）侧滑类型（left：左侧滑、right：右侧滑、all：左右侧滑）。安卓暂只支持left。

leftEdge：

- 类型：数字
- 默认值：60
- 描述：（可选项）左侧滑时，侧滑window停留时露出的宽度。即将废弃，用slidPaneStyle中leftEdge参数代替

rightEdge：

- 类型：数字
- 默认值：60
- 描述：（可选项）右侧滑时，侧滑window停留时露出的宽度。即将废弃，用slidPaneStyle中rightEdge参数代替

slidPaneStyle：

- 类型：JSON对象
- 默认值：无
- 描述：侧滑层window样式

内部字段：

```js
{
	leftEdge:				//（可选项）左侧滑时，侧滑window停留时露出的宽度，默认60，数字类型
	rightEdge:				//（可选项）右侧滑时，侧滑window停留时露出的宽度，默认60，数字类型
	leftScale:				//（可选项）左侧滑时，侧滑window移动时能缩放的最小倍数，0-1.0，默认1.0，数字类型，只支持iOS
	rightScale:				//（可选项）右侧滑时，侧滑window移动时能缩放的最小倍数，0-1.0，默认1.0，数字类型，只支持iOS
}
```

fixedPaneStyle：

- 类型：JSON对象
- 默认值：无
- 描述：底部固定层window样式

内部字段：

```js
{
	leftEdge:				//（可选项）左侧滑时，固定window能向左移动的最大宽度，默认0，数字类型，只支持iOS
	rightEdge:				//（可选项）右侧滑时，固定window能向右移动的最大宽度，默认0，数字类型，只支持iOS
	leftScale:				//（可选项）左侧滑时，固定window向左移动时能缩放的最小倍数，0-1.0，默认1.0，数字类型，只支持iOS
	rightScale:				//（可选项）右侧滑时，固定window向右移动时能缩放的最小倍数，0-1.0，默认1.0，数字类型，只支持iOS
	leftMaskBg:				//（可选项）左侧滑时，固定window上面的遮罩层背景，支持颜色和图片，默认rgba(0,0,0,0)，字符串类型，只支持iOS
	rightMaskBg:			//（可选项）右侧滑时，固定window上面的遮罩层背景，支持颜色和图片，默认rgba(0,0,0,0)，字符串类型，只支持iOS
	leftBg:					//（可选项）左侧滑时，固定window后面的背景，缩放过程中后面的背景将会显示出来，支持颜色和图片，默认rgba(0,0,0,0)，字符串类型，只支持iOS
	rightBg:				//（可选项）右侧滑时，固定window后面的背景，缩放过程中后面的背景将会显示出来，支持颜色和图片，默认rgba(0,0,0,0)，字符串类型，只支持iOS
}
```

fixedPane：

- 类型：JSON对象
- 默认值：无
- 描述：底部固定层window

内部字段：

```js
{
    name:'',                            // window名字（字符串类型）
    url:'',                             // 页面地址，可以为本地文件路径，支持相对路径和绝对路径，以及widget://、fs://等协议路径，也可以为远程地址
    pageParam:{},                       //（可选项）页面参数，页面中可以通过api.pageParam获取，JSON对象
    bgColor:'',                         //（可选项）背景色，支持图片和颜色，格式为#fff、#ffffff、rgba(r,g,b,a)等，图片路径支持fs://、widget://等APICloud自定义文件路径协议，同时支持相对路径
    bounces:false,                      //（可选项）是否弹动，默认值：若在config.xml里面配置了pageBounce，则默认值为配置的值，否则为false
	scrollToTop:false					//（可选项）当点击状态栏，页面是否滚动到顶部。若当前屏幕上不止一个页面的scrollToTop属性为true，则所有的都不会起作用。默认值：true。只iOS有效
    vScrollBarEnabled:true,             //（可选项）是否显示垂直滚动条，默认true 
    hScrollBarEnabled:true,             //（可选项）是否显示水平滚动条，默认true
	scaleEnabled:true,                  //（可选项）页面是否可以缩放，为true时softInputMode参数无效，布尔型，默认值：false
    allowEdit:false,					//（可选项）是否允许长按页面时弹出选择菜单
    softInputMode:'auto'		        //（可选项）当键盘弹出时，输入框被盖住时，当前页面的调整方式，参考键盘弹出页面调整方式常量，只iOS有效，且当scaleEnabled参数为true时无效
    customRefreshHeader:''				//（可选项）设置使用自定义下拉刷新模块的名称，设置后可以使用api.setCustomRefreshHeaderInfo方法来使用自定义下拉刷新组件
}
```

slidPane：

- 类型：JSON对象
- 默认值：无
- 描述：侧滑层window

内部字段：

```js
{
    name:'',                            // window名字（字符串类型）
    url:'',                             // 页面地址，可以为本地文件路径，支持相对路径和绝对路径，以及widget://、fs://等协议路径，也可以为远程地址
    pageParam:{},                       //（可选项）页面参数，页面中可以通过api.pageParam获取，JSON对象
    bgColor:'',                         //（可选项）背景色，支持图片和颜色，格式为#fff、#ffffff、rgba(r,g,b,a)等，图片路径支持fs://、widget://等APICloud自定义文件路径协议，同时支持相对路径
    bounces:false,                      //（可选项）是否弹动，默认值：若在config.xml里面配置了pageBounce，则默认值为配置的值，否则为false
	scrollToTop:false					//（可选项）当点击状态栏，页面是否滚动到顶部。若当前屏幕上不止一个页面的scrollToTop属性为true，则所有的都不会起作用。默认值：true。只iOS有效
    vScrollBarEnabled:true,             //（可选项）是否显示垂直滚动条，默认true 
    hScrollBarEnabled:true,             //（可选项）是否显示水平滚动条，默认true
	scaleEnabled:true,                  //（可选项）页面是否可以缩放，为true时softInputMode参数无效，布尔型，默认值：false
    allowEdit:false,					//（可选项）是否允许长按页面时弹出选择菜单
    softInputMode:'auto'		        //（可选项）当键盘弹出时，输入框被盖住时，当前页面的调整方式，参考键盘弹出页面调整方式常量，只iOS有效，且当scaleEnabled参数为true时无效
    customRefreshHeader:''				//（可选项）设置使用自定义下拉刷新模块的名称，设置后可以使用api.setCustomRefreshHeaderInfo方法来使用自定义下拉刷新组件
}
```

##callback(ret, err)

ret：

- 类型：JSON对象
- 描述：手指头触摸屏幕，引起开始侧滑时的回调，左右侧滑时应该在这里面判断显示左边页面还是右边页面

内部字段：

```js
{
	type: 'left'		//侧滑方向，left或right
	event: 'slide'		//侧滑事件，（slide-当前处于滑动状态、open-侧滑打开状态、close-侧滑关闭状态
}
```

##示例代码

```js
api.openSlidLayout ({
	type: 'all',
	leftEdge: 80,
	rightEdge: 60,
	fixedPane: {
        name: 'win1', 
		url: 'win1.html', 
		bgColor: '#fff', 
		bounces: true,
		vScrollBarEnabled: true,
		hScrollBarEnabled: false
	},
	slidPane: {
        name: 'win2', 
		url: 'win2.html', 
		bgColor: '#fff', 
		bounces: true,
		vScrollBarEnabled: true,
		hScrollBarEnabled: false
    }
},function( ret, err ){
	if( ret ) {
        alert( JSON.stringify( ret ) );
	}else{
        alert( JSON.stringify( err ) );
	}
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**openSlidPane**<div id="31"></div>

向左或右进行侧滑

openSlidPane(params)

##params

type：

- 类型：字符串
- 默认值：无
- 描述：侧滑类型，left或right

##示例代码

```js
api.openSlidPane({
    type: 'left'
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**closeSlidPane**<div id="12"></div>

当SlidPane处于左或右侧滑状态时，将其收起

closeSlidPane()

##示例代码

```js
api.closeSlidPane();
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**lockSlidPane**<div id="67"></div>

锁住SlidPane，使其不能跟随手指滑动而移动

lockSlidPane()

##示例代码

```js
api.lockSlidPane();
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**unlockSlidPane**<div id="68"></div>

解锁SlidPane，使其能跟随手指滑动而移动

unlockSlidPane()

##示例代码

```js
api.unlockSlidPane();
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**openDrawerLayout**<div id="89"></div>

打开一个抽屉式侧滑window，可以从当前window的左右边缘滑动拉出侧滑window。

此方法在openWin方法的基础上增加了leftPane、rightPane参数，所以可以通过api.closeWin()方法来关闭整个抽屉式侧滑。

openDrawerLayout({params})

##params

name：

- 类型：字符串
- 默认值：无
- 描述：window名字，不能为空字符串

url：

- 类型：字符串
- 默认值：无
- 描述：页面地址，可以为本地文件路径，支持相对路径和绝对路径，以及widget://、fs://等协议路径，也可以为远程地址

pageParam：

- 类型：JSON对象
- 默认值：无
- 描述：（可选项）页面参数，新页面中可以通过api.pageParam获取

bounces：

- 类型：布尔
- 默认值：若在config.xml里面配置了pageBounce，则默认值为配置的值，否则为false
- 描述：（可选项）页面是否弹动

bgColor：

- 类型：字符串
- 默认值：若在config.xml里面配置了windowBackground，则默认值为配置的值，否则透明
- 描述：（可选项）背景色，支持图片和颜色，格式为#fff、#ffffff、rgba(r,g,b,a)等，图片路径支持fs://、widget://等APICloud自定义文件路径协议，同时支持相对路径

scrollToTop：

- 类型：布尔
- 默认值：false
- 描述：（可选项）当点击状态栏，页面是否滚动到顶部。若当前屏幕上不止一个页面的scrollToTop属性为true，则所有的都不会起作用。只iOS有效

vScrollBarEnabled：

- 类型：布尔
- 默认值：true
- 描述：（可选项）是否显示垂直滚动条

hScrollBarEnabled：

- 类型：布尔
- 默认值：true
- 描述：（可选项）是否显示水平滚动条

scaleEnabled：

- 类型：布尔
- 默认值：false
- 描述：（可选项）页面是否可以缩放，为true时softInputMode参数无效

slidBackEnabled：

- 类型：布尔
- 默认值：true
- 描述：（可选项）是否支持滑动返回。iOS7.0及以上系统中，在新打开的页面中向右滑动，可以返回到上一个页面，该字段只iOS有效

slidBackType：

- 类型：字符串
- 默认值：full
- 描述：（可选项）当支持滑动返回时，设置手指在页面右滑的有效作用区域。取值范围（full:整个页面范围都可以右滑返回，edge:在页面左边缘右滑才可以返回），该字段只iOS有效

animation：

- 类型：JSON对象
- 默认值：无
- 描述：（可选项）动画参数，不传时使用默认动画，**type**：[动画类型](!Constant#b6)，**subType**：[动画子类型](!Constant#b8)。

内部字段：

```js
{
    type:"none",                //动画类型（详见动画类型常量）
    subType:"from_right",       //动画子类型（详见动画子类型常量）
    duration:300                //动画过渡时间，默认300毫秒
}
```

showProgress：

- 类型：布尔
- 默认值：false
- 描述：（可选项）是否显示等待框，此参数即将废弃，使用progress参数代替。若传了progress参数，此参数将忽略

progress：

- 类型：JSON对象
- 默认值：无
- 描述：（可选项）页面加载进度配置信息，若不传则无加载进度效果

内部字段：

```js
{
    type:"",            	//加载进度效果类型，默认值为default，取值范围为default|page，default等同于showProgress参数效果；为page时，进度效果为仿浏览器类型，固定在页面的顶部
    title:"",       		//type为default时显示的加载框标题
    text:"",                //type为default时显示的加载框内容
    color:""                //type为page时进度条的颜色，默认值为#45C01A，支持#FFF，#FFFFFF，rgb(255,255,255)，rgba(255,255,255,1.0)等格式
}
```

delay：

- 类型：数字
- 默认值：0
- 描述：（可选项）window显示延迟时间，适用于将被打开的window中可能需要打开有耗时操作的模块时，可延迟window展示到屏幕的时间，保持UI的整体性

reload：

- 类型：布尔
- 默认值：false
- 描述：（可选项）页面已经打开时，是否重新加载页面，重新加载页面后apiready方法将会被执行

allowEdit：

- 类型：布尔
- 默认值：false
- 描述：（可选项）是否允许长按页面时弹出选择菜单

softInputMode：

- 类型：字符串
- 默认值：auto
- 描述：（可选项）当键盘弹出时，输入框被盖住时，当前页面的调整方式，详见[键盘弹出页面调整方式](!Constant#b26)常量；只iOS有效，且当scaleEnabled参数为true时无效，Android请在config.xml里面配置并云编译使用

customRefreshHeader：

- 类型：字符串
- 默认值：无
- 描述：（可选项）设置使用自定义下拉刷新模块的名称，设置后可以使用api.setCustomRefreshHeaderInfo方法来使用自定义下拉刷新组件

leftPane：

- 类型：JSON对象
- 默认值：无
- 描述：左边侧滑window

内部字段：

```js
{
    edge:60,							// 左边侧滑打开后，漏出的半透明区域宽度，默认值为60。此时左边侧滑window的宽度为屏幕宽度减去edge
    name:'',                            // window名字（字符串类型）
    url:'',                             // 页面地址，可以为本地文件路径，支持相对路径和绝对路径，以及widget://、fs://等协议路径，也可以为远程地址
    pageParam:{},                       //（可选项）页面参数，页面中可以通过api.pageParam获取，JSON对象
    bgColor:'',                         //（可选项）背景色，支持图片和颜色，格式为#fff、#ffffff、rgba(r,g,b,a)等，图片路径支持fs://、widget://等APICloud自定义文件路径协议，同时支持相对路径
    bounces:false,                      //（可选项）是否弹动，默认值：若在config.xml里面配置了pageBounce，则默认值为配置的值，否则为false
	scrollToTop:false					//（可选项）当点击状态栏，页面是否滚动到顶部。若当前屏幕上不止一个页面的scrollToTop属性为true，则所有的都不会起作用。默认值：true。只iOS有效
    vScrollBarEnabled:true,             //（可选项）是否显示垂直滚动条，默认true 
    hScrollBarEnabled:true,             //（可选项）是否显示水平滚动条，默认true
	scaleEnabled:true,                  //（可选项）页面是否可以缩放，为true时softInputMode参数无效，布尔型，默认值：false
    allowEdit:false,					//（可选项）是否允许长按页面时弹出选择菜单
    softInputMode:'auto'		        //（可选项）当键盘弹出时，输入框被盖住时，当前页面的调整方式，参考键盘弹出页面调整方式常量，只iOS有效，且当scaleEnabled参数为true时无效
    customRefreshHeader:''				//（可选项）设置使用自定义下拉刷新模块的名称，设置后可以使用api.setCustomRefreshHeaderInfo方法来使用自定义下拉刷新组件
}
```

rightPane：

- 类型：JSON对象
- 默认值：无
- 描述：右边侧滑window

内部字段：

```js
{
    edge:60,							// 右边侧滑打开后，漏出的半透明区域宽度，默认值为60。此时右边侧滑window的宽度为屏幕宽度减去edge
    name:'',                            // window名字（字符串类型）
    url:'',                             // 页面地址，可以为本地文件路径，支持相对路径和绝对路径，以及widget://、fs://等协议路径，也可以为远程地址
    pageParam:{},                       //（可选项）页面参数，页面中可以通过api.pageParam获取，JSON对象
    bgColor:'',                         //（可选项）背景色，支持图片和颜色，格式为#fff、#ffffff、rgba(r,g,b,a)等，图片路径支持fs://、widget://等APICloud自定义文件路径协议，同时支持相对路径
    bounces:false,                      //（可选项）是否弹动，默认值：若在config.xml里面配置了pageBounce，则默认值为配置的值，否则为false
	scrollToTop:false					//（可选项）当点击状态栏，页面是否滚动到顶部。若当前屏幕上不止一个页面的scrollToTop属性为true，则所有的都不会起作用。默认值：true。只iOS有效
    vScrollBarEnabled:true,             //（可选项）是否显示垂直滚动条，默认true 
    hScrollBarEnabled:true,             //（可选项）是否显示水平滚动条，默认true
	scaleEnabled:true,                  //（可选项）页面是否可以缩放，为true时softInputMode参数无效，布尔型，默认值：false
    allowEdit:false,					//（可选项）是否允许长按页面时弹出选择菜单
    softInputMode:'auto'		        //（可选项）当键盘弹出时，输入框被盖住时，当前页面的调整方式，参考键盘弹出页面调整方式常量，只iOS有效，且当scaleEnabled参数为true时无效
    customRefreshHeader:''				//（可选项）设置使用自定义下拉刷新模块的名称，设置后可以使用api.setCustomRefreshHeaderInfo方法来使用自定义下拉刷新组件
}
```

##示例代码

```js
api.openDrawerLayout({
	name: 'main',
	url: './main.html',
	animation:{
		type:'none'
	},
	leftPane:{
		name: 'leftPane',
		url: 'leftPane.html'
	}
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.2.0及更高版本


#**openDrawerPane**<div id="90"></div>

打开抽屉式侧滑Pane

openDrawerPane(params)

##params

type：

- 类型：字符串
- 默认值：无
- 描述：侧滑类型，left或right

##示例代码

```js
api.openDrawerPane({
    type: 'left'
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.2.0及更高版本


#**closeDrawerPane**<div id="91"></div>

关闭抽屉式侧滑Pane

closeDrawerPane()

##示例代码

```js
api.closeDrawerPane();
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.2.0及更高版本


#**execScript**<div id="18"></div>

在指定window或者frame中执行脚本，对于frameGroup里面的frame也有效，若name和frameName都未指定，则在当前window中执行脚本，具体执行逻辑见补充说明。

execScript({params})

##params

name：

- 类型：字符串
- 默认值：无
- 描述：（可选项）window名称，若要跨window执行脚本，该字段必须指定，首页的名称为root

frameName：

- 类型：字符串
- 默认值：无
- 描述：（可选项）frame名称

script：

- 类型：字符串
- 默认值：无
- 描述：js代码

##示例代码

```js
//在名为winName的window中执行jsfun脚本
var jsfun = 'funcGoto();';
api.execScript({
    name: 'winName',
    script: jsfun
});


//在名为winName的window中找到
//名为frmName的frame，并在该frame中执行jsfun脚本
var jsfun = 'funcGoto();';
api.execScript({
    name: 'winName',
    frameName: 'frmName',
    script: jsfun
});


//在当前window中找到
//名为frmName的frame，并在该frame中执行jsfun脚本
var jsfun = 'funcGoto();';
api.execScript({
    frameName: 'frmName',
    script: jsfun
});
```

##补充说明

统一处理逻辑为：exec->window->frame
 
name参数：
当name不传值，或者传空字符串的情况下，execScript对象为调用execScript的window（该window可能位于屏幕或者后台），在该window中继续frameName的逻辑；
当name传值且非空字符串，但并未找到名为name的window，则直接返回不处理（不论frameName是否有值）。若找到了对应的window，则在该window中继续frameName的逻辑；
 
frameName参数：
当frameName不传值，或者传空字符串的情况下，execScript对象为调用execScript的window（该window可能位于屏幕或者后台），在该window中执行script；
当frameName传值且非空字符串，但并未找到名为frameName的frame，则直接返回不处理。若找到了该frame，则在该frame中执行script。

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**historyBack**<div id="73"></div>

历史记录后退一页

historyBack({params}, callback(ret, err))

##params

frameName：

- 类型：字符串
- 默认值：无
- 描述：（可选项）frame名称，若不传则表示对当前页面进行操作

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:true		//后退是否成功，失败时说明不能再后退了
}
```

##示例代码

```js
api.historyBack({
	frameName:'detail'
},function(ret,err){
	if(!ret.status){
		api.closeWin();
	}
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**historyForward**<div id="74"></div>

历史记录前进一页

historyForward({params}, callback(ret, err))

##params

frameName：

- 类型：字符串
- 默认值：无
- 描述：（可选项）frame名称，若不传则表示对当前页面进行操作

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:true		//前进是否成功，失败时说明不能再前进了
}
```

##示例代码

```js
api.historyForward({
	frameName:'detail'
},function(ret,err){
	if(!ret.status){
		
	}
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**pageUp**<div id="79"></div>

页面向上滚动一页

pageUp({params, callback(ret,err)})

##params

top：

- 类型：布尔
- 默认值：false
- 描述：（可选项）是否直接滚动到最顶部

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	scrolled:true		//是否滚动，为false时说明当前页面已经到达顶部了
}
```

##示例代码

```js
api.pageUp(function( ret, err ){
	if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }	
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.1.0及更高版本


#**pageDown**<div id="80"></div>

页面向下滚动一页

pageDown({params, callback(ret,err)})

##params

bottom：

- 类型：布尔
- 默认值：false
- 描述：（可选项）是否直接滚动到最底部

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	scrolled:true		//是否滚动，为false时说明当前页面已经到达底部了
}
```

##示例代码

```js
api.pageDown(function( ret, err ){
	if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }		
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.1.0及更高版本



#**removeLaunchView**<div id="63"></div>

移除启动图。若config.xml里面配置autoLaunch为false，则启动图不会自动消失，直到调用此方法移除。

removeLaunchView({params})

##params

animation：

- 类型：JSON对象
- 默认值：无
- 描述：（可选项）动画参数，不传时不使用动画，**type**：[动画类型](!Constant#b6)，**subType**：[动画子类型](!Constant#b8)。

内部字段：

```js
{
    type:"fade",                //动画类型（详见动画类型常量）
    subType:"from_right",       //动画子类型（详见动画子类型常量）
    duration:300                //动画过渡时间，默认300毫秒
}
```

##示例代码

```js
api.removeLaunchView({
	animation: {
		type: 'fade',
		duration: 500
	}
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**parseTapmode**<div id="34"></div>

解析元素tapmode属性，优化点击事件处理

默认页面加载完成后，引擎会对dom里面的元素进行tapmode属性解析，若是之后用代码创建的dom元素，则需要调用该方法后tapmode属性才会生效

parseTapmode()

##示例代码

```js
api.parseTapmode();
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**installApp**<div id="23"></div>

安装应用

installApp({params})

##params

appUri：

- 类型：字符串
- 默认值：无
- 描述：目标应用的资源文件标识。Android上为apk包的本地路径，如file://xxx.apk；iOS上为应用在itunes里面的地址，或者安装包对应的plist文件地址

##示例代码

```js
//Android用法：
api.installApp({
	appUri: 'file://xxx.apk'
});

//iOS用法：
api.installApp({
	appUri: 'https://itunes.apple.com/cn/app/qq/id444934666?mt=8'    //itunes地址
});

api.installApp({
	appUri: 'https://list.kuaiapp.cn/list/KuaiAppZv7.1.plist'        //安装包对应plist地址
});
```

##补充说明

安装应用

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**openApp**<div id="25"></div>

打开手机上其它应用，并且可以传递参数

openApp({params}, callback(ret, err))

##params

appParam：

- 类型：JSON对象
- 默认值：无
- 描述：（可选项）传给目标应用的参数。iOS平台会将appParam里面的值拼接到iosUrl后面，比如iosUrl为http://www.baidu.com，appParam为{"keyword":"APICloud"}，则最后传递给第三方应用的url为http://www.baidu.com?keyword=APICloud

iosUrl：

- 类型：字符串
- 默认值：无
- 描述：（可选项）目标应用的url（iOS平台使用），iOS下必传

androidPkg：

- 类型：字符串
- 默认值：无
- 描述：（可选项）目标应用的包名或action（Android平台使用），Android下必传

mimeType：

- 类型：字符串
- 默认值：无
- 描述：（可选项）指定目标应用的响应数据类型，如："text/html"（Android平台使用）

uri：

- 类型：字符串
- 默认值：无
- 描述：（可选项）指定目标应用响应的uri（Android平台使用）

##callback(ret, err)
ret：
- 类型：JSON对象
- 描述：目标应用关闭后的返回值，只支持Android

err：
- 类型：JSON对象

内部字段：
```js
{
    msg:""      //错误描述
}
```

##示例代码

```js
//iOS中的使用方法如下：

api.openApp({
	iosUrl: 'http://www.baidu.com',         //例如调用系统浏览器Safari打开百度，其中http为Safari的URL Scheme；同理，微信的URL Scheme为weixin，因此可以通过传weixin://来打开微信
	appParam: {
		appParam: 'app参数'
	}
});

//Android中的使用方法如下：

api.openApp({
	androidPkg: 'android.intent.action.VIEW',
	mimeType: 'text/html',
	uri: 'http://www.baidu.com'
},function( ret, err ){
	if( ret ){
         alert( JSON.stringify( ret ) );
    }else{
         alert( JSON.stringify( err ) );
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**appInstalled**<div id="75"></div>

判断设备上面是否已安装指定应用

appInstalled({params}, callback(ret, err))

##params

appBundle：

- 类型：字符串
- 默认值：无
- 描述：Android平台为应用包名，iOS平台为应用定义的URL Scheme。iOS中的URL Scheme与包名不一样，一个应用只有一个包名，但是可以配置多个URL Scheme

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    installed:true			//是否安装，布尔类型
}
```

##示例代码

```js
api.appInstalled({
    appBundle: appBundle
},function( ret, err ){
	if( ret ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**重启应用**<div id="92"></div>

重启应用，云修复完成后可以调用此方法来重启应用使云修复生效。

rebootApp()

##示例代码

```js
api.rebootApp();
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.2.0及更高版本


#**openWidget**<div id="32"></div>

打开Widget，若此widget已经被打开，则会把其调整到最前面显示

openWidget({params}, callback(ret, err))

##params

id：

- 类型：字符串
- 默认值：无
- 描述：widget的ID

wgtParam：

- 类型：JSON对象
- 默认值：无
- 描述：（可选项）widget参数，在新打开的widget里面的页面中通过api.wgtParam获取

animation：

- 类型：JSON对象
- 默认值：无
- 描述：（可选项）动画参数，不传时使用默认动画，**type**：[动画类型](!Constant#b6)，**subType**：[动画子类型](!Constant#b8)。

内部字段：

```js
{
    type:"none",                 //动画类型（详见动画类型常量）
    subType:"from_right",        //动画子类型（详见动画子类型常量）
    duration:300                 //动画过渡时间，默认300毫秒
}
```

##callback(ret, err)

ret：

- 类型：JSON对象
- 描述：新widget关闭时候的返回值

##示例代码

```js
api.openWidget({
	id: 'A00000001',
	animation: {
		type: 'flip',
		subType: 'from_bottom',
		duration: 500
	}
}, function( ret, err ){
	if( ret ){
         alert( JSON.stringify( ret ) );
    }else{
         alert( JSON.stringify( err ) );
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**closeWidget**<div id="14"></div>

关闭指定widget

closeWidget({params})

##params

id：

- 类型：字符串
- 默认值：无
- 描述：（可选项）widget的ID

retData：

- 类型：JSON对象
- 默认值：无
- 描述：（可选项）返回给上个widget的返回值

silent：

- 类型：布尔型
- 默认值：false
- 描述：（可选项）是否静默退出应用，只在主widget中有效。当为false时，引擎会弹出对话框询问是否退出应用

animation：

- 类型：JSON对象
- 默认值：无
- 描述：（可选项）动画参数，不传时使用默认动画，**type**：[动画类型](!Constant#b6)，**subType**：[动画子类型](!Constant#b8)。

内部字段：
```js
{
    type:"none",                //动画类型（详见动画类型常量）
    subType:"from_right",       //动画子类型（详见动画子类型常量）
    duration:300                //动画过渡时间，默认300毫秒
}
```

##示例代码

```js
api.closeWidget({
	id: 'A00000001',
	retData: {
	    name: 'closeWidget'
	},
	animation: {
		type: 'flip',
		subType: 'from_bottom',
		duration: 500
	}
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**ajax**<div id="3"></div>

跨域异步请求，支持文件上传

ajax({params}, callback(ret, err))

##params

url：

- 类型：字符串
- 默认值：无
- 描述：请求地址

tag：

- 类型：字符串
- 默认值：无
- 描述：（可选项）请求标识，可以传递此字段给cancelAjax方法来取消请求

method：

- 类型：字符串
- 默认值：get
- 描述：（可选项）异步请求方法类型（详见[异步请求方法类型](!Constant#b22)常量）

cache：

- 类型：布尔
- 默认值：false
- 描述：（可选项）是否缓存，若缓存，下次没网络时请求则会使用缓存

timeout：

- 类型：数字
- 默认值：30
- 描述：（可选项）超时时间，单位秒

dataType：

- 类型：字符串
- 默认值：json
- 描述：（可选项）返回数据类型（详见[异步请求返回数据类型](!Constant#b22)常量）

charset：

- 类型：字符串
- 默认值：utf-8
- 描述：（可选项）当响应头里面没有返回字符集编码时，使用此编码来解析数据

headers：

- 类型：JSON对象
- 默认值：无
- 描述：（可选项）请求头

report：

- 类型：布尔
- 默认值：false
- 描述：（可选项）是否实时返回上传文件进度

returnAll：

- 类型：布尔
- 默认值：false
- 描述：（可选项）是否需要返回所有response信息，为true时，返回的头信息获取方法(ret.headers)，消息体信息获取方法(ret.body)，状态码获取方法(ret.statusCode)

data：

- 类型：JSON对象
- 默认值：无
- 描述：（可选项）POST数据，method为get时不传。以下字段除了values和files可以同时使用，其它参数都不能同时使用。

内部字段：

```js
{
	stream："",		//文件路径（字符串类型）
	body："",			//请求体（字符串类型）如: JSON.stringify({"name1": "value1", "name2": "value2"}) (将JSON对像转为JSON字符串再赋值给body)
	values：{},		//以表单方式提交参数（JSON对象）, 如 {"field1": "value1", "field1": "value2"} (直接传JSON对像.)
	files：{}			//以表单方式提交文件，支持多文件上传（JSON对象）,如 {"file": "path"}，也支持同一字段对应多文件：{"file":["path1","path2"]}。路径支持绝对路径，以及fs://、widget://、cache://等文件路径协议.
}
```

certificate：

- 类型：JSON对象
- 默认值：无
- 描述：（可选项）https安全证书设置。

内部字段：

```js
{
	path:'',				//p12证书路径，支持fs://、widget://、cache://等文件路径协议，字符串类型
	password:''			//证书密码，字符串类型
}
```

##callback(ret, err)

ret：

- 类型：JSON对象或字符串
- 描述：类型依赖于传入的dataType和returnAll

返回上传进度时，原服务器返回数据会被放在body字段里面，内部字段为：

```js
{
    progress: 100,          //上传进度，0.00-100.00
    status: '',             //上传状态，详见上传状态常量
    body: ''                //上传完成时，服务器返回的数据
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    statusCode: 400,		//网络请求状态码，数字类型
    code:0,					//错误码（详见异步请求错误码常量），数字类型
    msg:''					//错误描述，字符串类型
    body:					//当请求失败如需要权限时，此时服务器返回的数据会通过该参数返回；当要求返回的数据格式为json，而返回的数据不是json格式时，数据通过该参数返回
}
```

##示例代码

```js
api.ajax({
	url: 'http://192.168.1.101:3101/upLoad',
	method: 'post',
	data: {
		values: { 
		    name: 'haha'
		},
		files: { 
		    file: 'fs://a.gif'
		}
	}
},function(ret, err){
	if (ret) {
		 alert(JSON.stringify(ret));
	} else {
		 alert(JSON.stringify(err));
	}
});
```

##补充说明

异步请求

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**cancelAjax**<div id="86"></div>

取消异步请求

cancelAjax({params})

##params

tag：

- 类型：字符串
- 默认值：无
- 描述：请求标识

##示例代码

```js
api.cancelAjax({
    tag: 'publish'
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.1.0及更高版本


#**download**<div id="17"></div>

下载文件

download({params}, callback(ret, err))

##params

url：

- 类型：字符串
- 默认值：无
- 描述：下载地址

savePath：

- 类型：字符串
- 默认值：无
- 描述：（可选项）存储路径，不传时使用自动创建的路径

report：

- 类型：布尔类型
- 默认值：false
- 描述：（可选项）下载过程是否上报

cache：

- 类型：布尔类型
- 默认值：true
- 描述：（可选项）是否使用本地缓存

allowResume：

- 类型：布尔类型
- 默认值：false
- 描述：（可选项）是否允许断点续传

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    fileSize:0,                 //文件大小，数字类型
    percent:0,                  //下载进度（0-100），数字类型
    state:0,                    //下载状态（详见下载状态常量）
    savePath:''                 //存储路径（字符串类型）
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    msg:""    //错误描述
}
```

##示例代码

```js
api.download({
	url: url,
	savePath: 'fs://test.rar',
	report: true,
	cache: true,
	allowResume: true
},function( ret, err ){
	if(ret){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify ( err ) );
	}
});
```

##补充说明

通过返回的state来判断文件是否下载完成，不要通过percent来判断

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**cancelDownload**<div id="8"></div>

取消文件下载

cancelDownload({params})

##params

url：

- 类型：字符串
- 默认值：无
- 描述：下载地址

##示例代码

```js
api.cancelDownload({
    url: url
});
```

##补充说明

取消文件下载

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**imageCache**<div id="78"></div>

图片缓存

imageCache({params}, callback(ret, err))

##params

url：

- 类型：字符串
- 默认值：无
- 描述：图片远程地址

policy：

- 类型：字符串
- 默认值：default
- 描述：（可选项）缓存策略（详见[缓存策略](!Constant#b27)常量）

thumbnail：

- 类型：布尔类型
- 默认值：true
- 描述：（可选项）使用缩略图，底层将根据当前系统及设备性能，返回最优的缩略图，有利于提高应用运行及渲染效率

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    status:true,          //是否成功，布尔类型
    url:''                //图片本地存储路径，若下载失败，则返回传入的url，字符串类型
}
```

##示例代码

```js
api.imageCache({
	url: 'http://a.hiphotos.baidu.com/image/w%3D400/sign=2abe1c77d4ca7bcb7d7bc62f8e086b3f/64380cd7912397ddf9f4bdb05a82b2b7d1a287f0.jpg'
},function( ret, err ){
	if( ret ){
		 alert( JSON.stringify( ret ) );
	}else{
         alert( JSON.stringify( err ) );
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.1.0及更高版本



#**readFile**<div id="36"></div>

读取文本文件内容，只支持utf-8编码文本类型文件

readFile({params}, callback(ret, err))

##params

path：

- 类型：字符串
- 默认值：无
- 描述：文件路径，支持绝对路径和文件路径协议如fs://、widget://等

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    status:true,        //操作成功状态值
    data:""             //文件内容，字符串类型
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    code:0,             //错误码（详见文件操作错误码常量）
    msg:""              //错误描述
}
```

##示例代码

```js
api.readFile({
	path: 'fs://a.txt'
}, function( ret, err ){
	if( ret ){
		 alert( JSON.stringify( ret ) );
	}else{
         alert( JSON.stringify( err ) );
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**writeFile**<div id="61"></div>

写入内容到文本文件

writeFile({params}, callback(ret, err))

##params

path：

- 类型：字符串
- 默认值：无
- 描述：文件路径，支持绝对路径和文件路径协议如fs://、cache://等，不支持widget://目录，该目录只读

data：

- 类型：字符串
- 默认值：无
- 描述：文件内容

append：

- 类型：布尔
- 默认值：false
- 描述：是否以追加方式写入数据，默认会清除之前文件内容

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    status:true        //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    code:0,           //错误码（详见文件操作错误码常量）
    msg:""            //错误描述
}
```

##示例代码

```js
api.writeFile({
	path: 'fs://a.txt',
	data: 'writeFile测试内容'
}, function(ret, err){
	if( ret ){
		 alert( JSON.stringify( ret ) );
	}else{
         alert( JSON.stringify( err ) );
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**setPrefs**<div id="45"></div>

设置偏好数据

setPrefs({params})

##params

key：

- 类型：字符串
- 默认值：无
- 描述：键

value：

- 类型：字符串
- 默认值：无
- 描述：值

##示例代码

```js
api.setPrefs({
    key: 'k',
    value: '1'
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**getPrefs**<div id="21"></div>

获取偏好设置值

getPrefs({params}, callback(ret, err))

##params

key：

- 类型：字符串
- 默认值：无
- 描述：键

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    value:""		//值
}
```

##示例代码

```js
api.getPrefs({
    key: 'k'
}, function( ret, err ){
    if( ret ){
		 alert( JSON.stringify( ret ) );
	}else{
         alert( JSON.stringify( err ) );
    }
});
```

##补充说明

获取偏好设置值

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**removePrefs**<div id="39"></div>

删除偏好设置值

removePrefs({params})

##params

key：

- 类型：字符串
- 默认值：无
- 描述：键

##示例代码

```js
api.removePrefs({
	key: 'k'
});
```

##补充说明

删除偏好设置值

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**clearCache**<div id="9"></div>

清除缓存，包括下载的文件、拍照临时文件、网页缓存文件等，清除时可能需要消耗一定时间。

clearCache({params}, callback(ret, err))

##params

timeThreshold：

- 类型：数字
- 默认值：0
- 描述：（可选项）清除多少天前的缓存

##callback(ret, err)

- 描述：清除完成后的回调

##示例代码

```js
api.clearCache(function( ret, err ){
	if( ret ){
		 alert( JSON.stringify( ret ) );
	}else{
         alert( JSON.stringify( err ) );
    }	
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**getCacheSize**<div id="84"></div>

获取缓存占用空间大小，缓存包括下载的缓存文件、拍照临时文件以及网页缓存文件等，计算可能需要花费一些时间

getCacheSize(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	size:		//缓存大小，单位为Byte，数字类型。（-1：无存储设备、-2：正在准备USB存储设备、-3：无法访问存储设备）
}
```

##示例代码

```js
api.getCacheSize(function( ret, err ){
	if( ret ){
		 alert( JSON.stringify( ret ) );
	}else{
         alert( JSON.stringify( err ) );
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.1.0及更高版本



#**getFreeDiskSpace**<div id="85"></div>

获取剩余存储空间大小

getFreeDiskSpace(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	size:		//剩余存储空间大小，单位为Byte，数字类型。（-1：无存储设备、-2：正在准备USB存储设备、-3：无法访问存储设备）
}
```

##示例代码

```js
api.getFreeDiskSpace(function( ret, err ){
	if( ret ){
		 alert( JSON.stringify( ret ) );
	}else{
         alert( JSON.stringify( err ) );
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.1.0及更高版本



#**loadSecureValue**<div id="64"></div>

从加密的key.xml文件中读取指定数据，key.xml文件放置于网页包里面的res目录，配置方式：

```js
<?xml version="1.0" encoding="UTF-8"?>
<security>
<item name="appKey" value="1111111"/>
</security>
```

loadSecureValue({params}, callback(ret, err))

##params

key：

- 类型：字符串
- 默认值：无
- 描述：键

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	value:""		//值
}
```

##示例代码

```js
api.loadSecureValue({
	key:'appKey'
},function( ret, err ) {
	alert(ret.value);
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**addEventListener**<div id="2"></div>

监听事件，支持系统事件和自定义事件

addEventListener({params}, callback(ret, err))

##params

name：

- 类型：字符串
- 默认值：无
- 描述：自定义事件或系统事件名称（详见[事件](!Event)）

extra：

- 类型：JSON对象
- 默认值：无
- 描述：（可选项）附加字段。一些特定事件可能需要提供额外的参数。

内部字段：

```js
{
	threshold:			//当事件为scrolltobottom时，设置距离底部多少距离时触发事件，默认值为0，数字类型
}
```

##callback(ret, err)

ret：

- 类型：JSON对象
- 描述：事件发生时传递的参数，可能为空

##示例代码

```js
//如监听网络连接事件
api.addEventListener({
	name: 'online'
}, function( ret, err ){
	if( ret ){
		 alert( JSON.stringify( ret ) );
	}else{
         alert( JSON.stringify( err ) );
    }
});
```

##补充说明

监听事件

##可用性
iOS系统，Android系统

可提供的1.0.0及更高版本


#**removeEventListener**<div id="38"></div>

移除事件监听

removeEventListener({params})

##params

name：

- 类型：字符串
- 默认值：无
- 描述：自定义事件或系统事件名称（详见[事件](!Event)）

##示例代码

```js
api.removeEventListener({
    name: 'online'
});
```

##补充说明

停止监听事件

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**sendEvent**<div id="72"></div>

将任意一个自定义事件广播出去，该事件可在任意页面通过addEventListener监听收到。

sendEvent({params})

##params

name

- 类型：字符串
- 默认值：无
- 描述：任意自定义事件的名称，比如：apprunning、appover等

extra

- 类型：字符串或JSON对象
- 默认值：无
- 描述：（可选项）附带的参数。在监听页面的回调里面通过ret.value获取。

##示例代码

```js
api.sendEvent({
	name: 'myEvent',
	extra: {
	    key1: 'value1', 
	    key2: 'value2'
	}
});

//html页面a：
api.addEventListener({
	name: 'myEvent'
}, function(ret, err){
	alert(JSON.stringify(ret.value));
});

//html页面b：
api.addEventListener({
	name: 'myEvent'
}, function( ret, err ){
	alert(JSON.stringify(ret.value));
});

//a、b页面都将收到myEvent事件
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**accessNative**<div id="88"></div>

使用SuperWebView时，js向原生发送消息。此方法只在使用SuperWebView时有效。

accessNative({params}, callback(ret,err))

##params

name

- 类型：字符串
- 默认值：无
- 描述：消息名称。

extra

- 类型：JSON对象
- 默认值：无
- 描述：（可选项）附带的参数。

##callback(ret, err)

ret：

- 类型：JSON对象

err：

- 类型：JSON对象

##示例代码

```js
api.accessNative({
	name: 'showMenu',
	extra: {
	    key: 'value'
	}
},function(ret,err){
    
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.2.0及更高版本


#**notification**<div id="65"></div>

向用户发出震动、声音提示、灯光闪烁、状态栏消息等通知，以及闹钟功能

状态栏消息点击后，页面可以通过监听noticeclicked事件得到内容

notification({params}, callback(ret, err))

##params

vibrate：

- 类型：数组
- 默认值：[500,500]
- 描述：（可选项）伴随节奏的震动，时间数组，时间单位为毫秒，iOS上面震动时间为固定值

sound：

- 类型：字符串
- 默认值：default
- 描述：（可选项）提示音，默认为系统提示音。当实现闹钟功能时，iOS只支持widget://路径协议

light：

- 类型：布尔型
- 默认值：false
- 描述：（可选项）设备提示灯是否闪烁

notify：

- 类型：JSON对象
- 默认值：无
- 描述：（可选项）弹出通知到状态栏

内部字段：

```js
{
	title:''				//标题，默认值为应用名称，只Android有效
	content:''				//内容，默认值为'有新消息'
	extra:''       			//传递给通知的数据，在通知被点击后，该数据将通过监听函数回调给网页
	updateCurrent: false    //是否覆盖更新已有的通知，取值范围true|false。只Android有效
}
```

alarm：

- 类型：JSON对象
- 默认值：无
- 描述：（可选项）如果本次通知设置了闹铃，那么该通知将在设定的闹铃时间弹出

内部字段：

```js
{
	hour:			//小时，数字类型，取值范围（0-23），默认值为当前系统时
	minutes:		//分钟，数字类型，取值范围（0-59），默认值为当前系统分
	daysOfWeek:		//通知循环时间，以周为单位，数组类型，如[1,2,3,4,5,6,7]代表周日、周一、周二、周三、周四、周五、周六。若不传则不循环，只在当天或隔天的指定时间通知一次
	time:       	//闹铃目标时间，数字类型，1970年至今的毫秒数，只在设定的时间执行一次，若设置了time，那么hour、minutes、daysOfWeek将被忽略
}
```

##callback(ret, err)
如果notification时传入了notify，那么将收到callback，返回本次状态栏通知的id，该id可用于取消状态栏通知。

ret：

- 类型：JSON对象

内部字段：

```js
{
	id:1		//弹出到状态栏通知的id，可用于取消通知
}
```

##示例代码

```js
api.notification({
	notify: {
		content: '闹钟'
	},
	alarm: {
		hour: 7,
		minutes: 30,
		daysOfWeek: [2,3,4,5,6]
	}
}, function( ret, err ){
	if( ret ){
		 alert( JSON.stringify( ret ) );
	}else{
         alert( JSON.stringify( err ) );
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**cancelNotification**<div id="69"></div>

取消本应用弹出到状态栏的某个或所有通知，也可以清除设定的闹铃

cancelNotification({params})

##params

id：

- 类型：字符串
- 默认值：0。如果传入-1，则取消本应用弹到状态栏的所有通知，iOS只支持清除所有弹到状态栏的通知。
- 描述：（可选项）调用notification方法时返回的id

##示例代码

```js
api.cancelNotification({
	id: 1
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**startLocation**<div id="52"></div>

调用系统自带定位功能，开始定位

startLocation({params}, callback(ret, err))

##params

accuracy：

- 类型：字符串
- 默认值：100m
- 描述：（可选项）定位精度（详见[定位精度](!Constant#b5)常量）

filter：

- 类型：数字
- 默认值：1.0
- 描述：（可选项）位置更新所需最小距离（单位米）

autoStop：

- 类型：布尔
- 默认值：true
- 描述：（可选项）获取到位置信息后是否自动停止定位

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	longitude:116.213,                   //经度
	latitude:39.213,                     //纬度
	timestamp:1396068155591,             //时间戳
	status: true                         //定位成功
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    msg:""    //错误描述
}
```

##示例代码

```js
api.startLocation({
	accuracy: '100m',
	filter: 1,
	autoStop: true
},function( ret, err ){
	if( ret ){
		 alert( JSON.stringify( ret ) );
	}else{
         alert( JSON.stringify( err ) );
    }
});
```

##补充说明

本API使用系统自身定位能力进行定位。
Android上使用的是Google的定位服务，因法规政策的原因，在中国基本无法提供服务，因此建议国内开发者使用百度定位模块（baiduLocation）进行定位操作。
IOS上使用的是苹果的定位服务，不受影响。

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**stopLocation**<div id="56"></div>

停止定位

stopLocation()

##示例代码

```js
api.stopLocation();
```

##补充说明

停止定位

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**getLocation**<div id="19"></div>

获取位置信息，获取成功后自动停止获取。

若之前已通过startLocation()方法进行定位，则直接返回上次定位的数据，否则使用默认设置进行定位

getLocation(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    longitude:116.213,                  //经度
    latitude:39.213,                    //纬度
    timestamp:1396068155591,            //时间戳
    status:true                         //定位成功
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    msg:""    //错误描述
}
```

##示例代码

```js
api.getLocation(function( ret, err ){
	if( ret ){
		 alert( JSON.stringify( ret ) );
	}else{
         alert( JSON.stringify( err ) );
    }
});
```

##补充说明

本API使用系统自身定位能力进行定位。
Android上使用的是Google的定位服务，因法规政策的原因，在中国基本无法提供服务，因此建议国内开发者使用百度定位模块（baiduLocation）进行定位操作。
IOS上使用的是苹果的定位服务，不受影响。

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**startSensor**<div id="55"></div>

开启传感器

startSensor({params}, callback(ret, err))

##params

type：

- 类型：字符串
- 默认值：无
- 描述：传感器类型（详见[传感器类型](!Constant#b2)常量）

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	x:0,                    //x轴分量值
	y:0,                    //y轴分量值
	z:0,                    //z轴分量值
	proximity:true,         //是否接近设备
	status:true             //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    msg:""		//错误描述
}
```

##示例代码

```js
api.startSensor({
	type: 'accelerometer'
}, function( ret, err ){
	if( ret ){
		 alert( JSON.stringify( ret ) );
	}else{
         alert( JSON.stringify( err ) );
    }
});
```

##补充说明

开启传感器

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**stopSensor**<div id="59"></div>

停止传感器

stopSensor({params})

##params

type：

- 类型：字符串
- 默认值：无
- 描述：传感器类型（详见[传感器类型](!Constant#b2)常量）

##示例代码

```js
api.stopSensor({
    type: 'accelerometer'
});
```

##补充说明

停止传感器

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**call**<div id="7"></div>

拨打电话或进行faceTime

call({params})

##params

type：

- 类型：字符串
- 默认值：tel_prompt
- 描述：（可选项）打电话类型（详见[电话类型](!Constant#b4)常量）

number：

- 类型：字符串
- 默认值：无
- 描述：电话号码

##示例代码

```js
api.call({
	type: 'tel_prompt',
	number: '10086'
});
```

##补充说明

拨打电话，需要设备有电话功能

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**sms**<div id="51"></div>

调用系统短信界面发送短信，或者后台直接发送短信

sms({params}, callback(ret, err))

##params

numbers：

- 类型：字符串数组
- 默认值：无
- 描述：电话号码
- 备注：当调用系统短信界面进行短信发送时，仅支持传入一个号码，且发送是否成功的状态值依赖于系统短信界面的返回值

text：

- 类型：字符串
- 默认值：无
- 描述：文本内容

silent：

- 类型：布尔型
- 默认值：false
- 描述：（可选项）是否后台发送，iOS不支持
- 备注：后台发送时，numbers支持多个，可同时将一条信息发送给多个号码

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    status:true		//发送状态
}
```

##示例代码

```js
api.sms({
	numbers: ['10086'],
	text: '测试短信'
},function( ret, err ){
	if( ret ){
		 alert( JSON.stringify( ret ) );
	}else{
         alert( JSON.stringify( err ) );
    }
});
```

##补充说明

发送短信，需要设备有短信功能

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**mail**<div id="24"></div>

发送邮件

mail({params}, callback(ret, err))

##params

recipients：

- 类型：字符串数组
- 默认值：无
- 描述：收件人

subject：

- 类型：字符串
- 默认值：无
- 描述：邮件主题

body：

- 类型：字符串
- 默认值：无
- 描述：（可选项）邮件内容

attachments：

- 类型：数组
- 默认值：无
- 描述：（可选项）附件地址

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    status:true           //发送状态
}
```

##示例代码

```js
api.mail({
	recipients: ['test@163.com'],
	subject: '邮件测试',
	body: '这是一封测试用的邮件',
	attachments: ['widget://a.txt']
}, function( ret, err ){
	if( ret ){
		 alert( JSON.stringify( ret ) );
	}else{
         alert( JSON.stringify( err ) );
    }
});
```

##补充说明

需要在手机上面已经配置好邮件账户

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**openContacts**<div id="26"></div>

在应用内打开系统通讯录界面选择联系人

openContacts(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js

{
    status:true,             //操作成功状态值
    name:"",                 //姓名
    phone:""                 //电话号码
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    msg:""    //错误描述
}
```

##示例代码

```js
api.openContacts(function( ret, err ){
	if( ret ){
		 alert( JSON.stringify( ret ) );
	}else{
         alert( JSON.stringify( err ) );
    } 
});
```

##补充说明

打开通讯录界面

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**setFullScreen**<div id="44"></div>

设置是否全屏

setFullScreen({params})

##params

fullScreen：

- 类型：布尔
- 默认值：无
- 描述：是否全屏

##示例代码

```js
api.setFullScreen({
	fullScreen: true
});
```

##补充说明

设置是否全屏

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**setStatusBarStyle**<div id="47"></div>

设置状态栏样式为白色（适用于深色背景）或黑色（适用于浅色背景），以及设置状态栏背景颜色

setStatusBarStyle({params})

##params

style：

- 类型：字符串
- 默认值：无
- 描述：（可选项）状态栏样式（详见[状态栏样式](!Constant#b23)常量），只支持iOS

color：

- 类型：字符串
- 默认值：#000
- 描述：（可选项）状态栏背景颜色，只Android 5.0及以上有效

##示例代码

```js
api.setStatusBarStyle({
    style: 'light'
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**setScreenOrientation**<div id="66"></div>

设置屏幕旋转方向

setScreenOrientation({params})

##params

orientation：

- 类型：字符串
- 默认值：无
- 描述：旋转屏幕到指定方向，或根据重力感应自动旋转；当前为横屏时，若想只在横屏间根据重力切换，则可以传auto_landscape，竖屏间切换则传auto_portrait。详见[屏幕旋转方向](!Constant#b24)常量

##示例代码

```js
api.setScreenOrientation({
	orientation: 'landscape_left'
});
```
##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**setKeepScreenOn**<div id="71"></div>

设置是否禁止屏幕休眠

setKeepScreenOn({params})

##params

keepOn

- 类型：布尔
- 默认值：无
- 描述：是否禁止屏幕休眠

##示例代码

```js
api.setKeepScreenOn({
	keepOn: true
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**toLauncher**<div id="70"></div>

回到系统桌面

toLauncher()

##示例代码

```js
api.toLauncher();
```

##补充说明

该接口仅Android平台支持。

##可用性

Android系统

可提供的1.0.0及更高版本


#**setScreenSecure**<div id="82"></div>

设置是否禁止截屏，只支持Android

setScreenSecure({params})

##params

secure

- 类型：布尔
- 默认值：无
- 描述：是否禁止截屏

##示例代码

```js
api.setScreenSecure({
	secure: true
});
```

##补充说明

无

##可用性

Android系统

可提供的1.1.0及更高版本


#**setAppIconBadge**<div id="83"></div>

设置应用图标右上角数字，支持所有iOS手机，以及部分Android手机，如小米和三星的某些型号，不支持的设备，表现结果为调用该接口无任何效果

setAppIconBadge({params})

##params

badge

- 类型：数字
- 默认值：无
- 描述：显示在应用图标右上角的数字。为0时表示清除应用图标上显示的数字

##示例代码

```js
api.setAppIconBadge({
	badge: 1
});
```

##补充说明

无

##可用性

iOS系统

可提供的1.1.0及更高版本


#**alert**<div id="4"></div>

弹出带一个按钮的对话框，更多按钮的对话框请使用confirm方法

alert({params}, callback(ret, err))

##params

title：

- 类型：字符串
- 默认值：无
- 描述：（可选项）标题

msg：

- 类型：字符串
- 默认值：无
- 描述：（可选项）内容

buttons：

- 类型：数组
- 默认值：["确定"]
- 描述：（可选项）按钮

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	buttonIndex:1   //按钮点击序号，从1开始
}
```

##示例代码

```js
api.alert({
	title: 'testtitle',
	msg: 'testmsg',
	buttons: ['确定']
},function( ret, err ){
	if( ret ){
		 alert( JSON.stringify( ret ) );
	}else{
         alert( JSON.stringify( err ) );
    }
});
```

##补充说明

对话框

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**confirm**<div id="16"></div>

弹出带两个或三个按钮的confirm对话框

confirm({params}, callback(ret, err))

##params

title：

- 类型：字符串
- 默认值：无
- 描述：（可选项）标题

msg：

- 类型：字符串
- 默认值：无
- 描述：（可选项）内容

buttons：

- 类型：数组
- 默认值：["取消","确定"]
- 描述：（可选项）按钮标题，若小于两个按钮，会补齐两个按钮；若大于三个按钮，则使用前三个按钮

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：
```js
{
    buttonIndex:1   //按钮点击序号，从1开始
}
```
##示例代码

```js
api.confirm({
	title: 'testtitle',
	msg: 'testmsg',
	buttons: ['确定', '取消']
},function( ret, err ){
	if( ret ){
		 alert( JSON.stringify( ret ) );
	}else{
         alert( JSON.stringify( err ) );
    }
});
```

##补充说明

多个按钮的对话框

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**prompt**<div id="35"></div>

弹出带两个或三个按钮和输入框的对话框

prompt({params}, callback(ret, err))

##params

title：

- 类型：字符串
- 默认值：无
- 描述：（可选项）标题

msg：

- 类型：字符串
- 默认值：无
- 描述：（可选项）内容

text：

- 类型：字符串
- 默认值：无
- 描述：（可选项）输入框里面的默认内容

type：

- 类型：字符串
- 默认值：text
- 描述：（可选项）输入类型，不同输入类型弹出键盘类型不同，取值范围（text、password、number、email、url）

buttons：

- 类型：数组
- 默认值：["取消","确定"]
- 描述：（可选项）按钮标题，若小于两个按钮，会补齐两个按钮；若大于三个按钮，则使用前三个按钮

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    buttonIndex:1,              //按钮点击序号，从1开始
    text:""                     //输入文字
}
```

##示例代码

```js
api.prompt({
	buttons: ['确定', '取消']
},function( ret, err ){
	if( ret ){
		 alert( JSON.stringify( ret ) );
	}else{
         alert( JSON.stringify( err ) );
    }
});
```

##补充说明

带输入框的对话框

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**actionSheet**<div id="1"></div>

底部弹出框

```js
actionSheet({params}, callback(ret, err))
```

##params

title：

- 类型：字符串
- 默认值：无
- 描述：（可选项）标题

cancelTitle：

- 类型：字符串
- 默认值：取消
- 描述：（可选项）取消按钮标题

destructiveTitle：

- 类型：字符串
- 默认值：无
- 描述：（可选项）红色警示按钮标题，一般用于做一些删除之类操作

buttons：

- 类型：数组
- 默认值：无
- 描述：（可选项）其它按钮

style：

- 类型：JSON对象
- 默认值：无
- 描述：（可选项）样式设置，不传时使用默认样式

内部字段：

```js
{
	layerColor:'',         //遮蔽层颜色，仅支持rgba颜色，默认值：rgba（0, 0, 0, 0.4）
	itemNormalColor:'',    //选项按钮正常状态背景颜色，支持#000、#000000、rgb、rgba，默认值：#F1F1F1
	itemPressColor:'',     //选项按钮按下时背景颜色，支持#000、#000000、rgb、rgba，默认值：#E6E6E6
	fontNormalColor:'',    //选项按钮正常状态文字颜色，支持#000、#000000、rgb、rgba，默认值：#007AFF
	fontPressColor:'',     //选项按钮按下时文字颜色，支持#000、#000000、rgb、rgba，默认值：#0060F0
	titleFontColor:''      //标题文字颜色，支持#000、#000000、rgb、rgba，默认值：#8F8F8F
}
```

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	buttonIndex:1		//按钮点击序号，从1开始
}
```

##示例代码

```js
api.actionSheet({
    title: '底部弹出框测试',
    cancelTitle: '这里是取消按钮',
    destructiveTitle: '红色警告按钮',
	buttons: ['1','2','3']
},function( ret, err ){
	if( ret ){
		 alert( JSON.stringify( ret ) );
	}else{
         alert( JSON.stringify( err ) );
    }
});
```

##补充说明

底部弹出框

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**showProgress**<div id="50"></div>

显示进度提示框

showProgress({params})

##params

style：

- 类型：字符串
- 默认值：default
- 描述：（可选项）进度提示框风格（详见[进度提示框风格](!Constant#b10)常量）

animationType：

- 类型：字符串
- 默认值：fade
- 描述：（可选项）进度提示框动画类型（详见[进度提示框动画类型](!Constant#b9)常量）

title：

- 类型：字符串
- 默认值：加载中
- 描述：（可选项）标题

text：

- 类型：字符串
- 默认值：请稍后...
- 描述：（可选项）内容

modal：

- 类型：布尔
- 默认值：true
- 描述：（可选项）是否模态，模态时整个页面将不可交互

##示例代码

```js
api.showProgress({
    style: 'default',
    animationType: 'fade',
    title: '努力加载中...',
    text: '先喝杯茶...',
    modal: false
});
```

##补充说明

显示进度提示框

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**hideProgress**<div id="22"></div>

隐藏进度提示框

hideProgress()

##示例代码

```js
api.hideProgress();
```

##补充说明

隐藏进度提示框

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**toast**<div id="60"></div>

弹出一个定时自动关闭的提示框

toast({params})

##params

msg：

- 类型：字符串
- 默认值：无
- 描述：提示消息

duration：

- 类型：字符串
- 默认值：2000
- 描述：（可选项）持续时长，单位：毫秒

location：

- 类型：字符串
- 默认值：bottom
- 描述：（可选项）弹出位置，顶部、中间或底部（详见[toast位置](!Constant#b1)常量）

##示例代码

```js
api.toast({
    msg: '网络错误',
    duration: 2000,
    location: 'bottom'
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**openPicker**<div id="29"></div>

打开时间选择器

openPicker({params}, callback(ret, err))

##params

type：

- 类型：字符串
- 默认值：无
- 描述：拾取器类型（详见[拾取器类型](!Constant#b12)常量）

date：

- 类型：字符串
- 默认值：当前时间
- 描述：（可选项）时间格式化字符串，格式yyyy-MM-dd HH:mm

title：

- 类型：字符串
- 默认值：无
- 描述：（可选项）显示在拾取器上面的标题

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	year:2000,                  //年
	month:1,                    //月
	day:1,                      //日
	hour:12,                    //时
	minute:00                   //分
}
```

##示例代码

```js
api.openPicker({
	type: 'date_time',
	date: '2014-05-01 12:30',
	title: '选择时间'
},function( ret, err ){
	if( ret ){
		 alert( JSON.stringify( ret ) );
	}else{
         alert( JSON.stringify( err ) );
    }
});
```

##补充说明

时间选择器

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**setRefreshHeaderInfo**<div id="46"></div>

显示顶部下拉刷新组件，页面必须设置为弹动。

setRefreshHeaderInfo({params}, callback(ret, err))

##params

visible：

- 类型：布尔
- 默认值：true
- 描述：（可选项）是否可见

loadingImg：

- 类型：字符串
- 默认值：旋转箭头图片
- 描述：（可选项）上拉下拉时的图片地址

bgColor：

- 类型：字符串
- 默认值：rgba(187, 236, 153, 1.0)
- 描述：（可选项）背景颜色

textColor：

- 类型：字符串
- 默认值：rgba(109, 128, 153, 1.0)
- 描述：（可选项）文本颜色

textDown：

- 类型：字符串
- 默认值：下拉可以刷新...
- 描述：（可选项）下拉文字描述

textUp：

- 类型：字符串
- 默认值：松开可以刷新...
- 描述：（可选项）松开时文字描述

textLoading：

- 类型：字符串
- 默认值：加载中...
- 描述：（可选项）加载状态文字描述

textTime：

- 类型：字符串
- 默认值：最后更新加日期时间
- 描述：（可选项）更新时间文字描述

showTime：

- 类型：布尔
- 默认值：true
- 描述：（可选项）是否显示更新时间

##callback(ret, err)

ret：

- 描述：可以为空

err：

- 描述：可以为空

##示例代码

```js
api.setRefreshHeaderInfo({
    visible: true,
    loadingImg: 'widget://image/refresh.png',
    bgColor: '#ccc',
    textColor: '#fff',
    textDown: '下拉刷新...',
    textUp: '松开刷新...',
    showTime: true
}, function( ret, err ){
    //在这里从服务器加载数据，加载完成后调用api.refreshHeaderLoadDone()方法恢复组件到默认状态
    
});
```

##补充说明

下拉刷新

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**setCustomRefreshHeaderInfo**<div id="94"></div>

显示顶部自定义下拉刷新组件，页面必须设置为弹动。

可以在config.xml里面配置要使用的自定义下拉刷新模块名称，如：

```js
<preference name="customRefreshHeader" value="UIPullRefresh"/>
```

或者在使用openWin、openFrame等方法打开页面时传入customRefreshHeader参数来指定。

setCustomRefreshHeaderInfo({params}, callback(ret, err))

##params

由对应的自定义下拉刷新模块提供

##callback(ret, err)

由对应的自定义下拉刷新模块提供

##示例代码

```js
api.setCustomRefreshHeaderInfo({
    bgColor: '#C0C0C0',
    images: {
        pull: 'widget://image/refresh/pulling.png', 
        transform: [
            'widget://image/refresh/transform0.png', 
            'widget://image/refresh/transform1.png',
            'widget://image/refresh/transform2.png',
            'widget://image/refresh/transform3.png',
            'widget://image/refresh/transform4.png',
            'widget://image/refresh/transform5.png',
            'widget://image/refresh/transform6.png'
        ],
        load: [ 
            'widget://image/refresh/loading0.png', 
            'widget://image/refresh/loading1.png',
            'widget://image/refresh/loading2.png', 
            'widget://image/refresh/loading3.png',
            'widget://image/refresh/loading4.png',
        ]
    }
}, function( ret, err ){
    //在这里从服务器加载数据，加载完成后调用api.refreshHeaderLoadDone()方法恢复组件到默认状态
    
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.2.0及更高版本


#**refreshHeaderLoading**<div id="87"></div>

设置下拉刷新组件为刷新中状态

refreshHeaderLoading()

##示例代码

```js
api.refreshHeaderLoading();
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.1.0及更高版本


#**refreshHeaderLoadDone**<div id="37"></div>

通知顶部下拉刷新数据加载完毕，组件会恢复到默认状态

refreshHeaderLoadDone()

##示例代码

```js
api.refreshHeaderLoadDone();
```

##补充说明

通知顶部刷新数据加载完毕

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**showFloatBox**<div id="49"></div>

展示一个悬浮框，浮动在屏幕上，点击时关闭当前widget

showFloatBox({params})

##params

iconPath：

- 类型：字符串
- 默认值：应用图标
- 描述：（可选项）展示在悬浮框中的图片地址

duration：

- 类型：字符串
- 默认值：5000毫秒
- 描述：（可选项）自动消隐时长。在该时长内不发生触摸悬浮框行为，悬浮框自动消隐至半透状态

##示例代码

```js
api.showFloatBox({
	iconPath: 'widget://image/icon.png',
	duration: 3000
});
```

##补充说明

对主widget无效

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**getPicture**<div id="20"></div>

通过系统相册或拍照获取图片和视频

getPicture({params}, callback(ret, err))

##params

sourceType：

- 类型：字符串
- 默认值：library
- 描述：（可选项）图片源类型，从相册、图片库或相机获取图片（详见[图片源类型](!Constant#b15)常量）

encodingType：

- 类型：字符串
- 默认值：png
- 描述：（可选项）返回图片类型，jpg或png（详见[图片编码类型](!Constant#b13)常量）

mediaValue：

- 类型：字符串
- 默认值：pic
- 描述：（可选项）媒体类型，图片或视频（详见[媒体类型](!Constant#b11)常量）

destinationType：

- 类型：字符串
- 默认值：url
- 描述：（可选项）返回数据类型，指定返回图片地址或图片经过base64编码后的字符串（详见[图片数据格式](!Constant#b14)常量）

allowEdit：

- 类型：布尔
- 默认值：false
- 描述：（可选项）是否可以选择图片后进行编辑，支持iOS及部分安卓手机

quality：

- 类型：数字
- 默认值：50
- 描述：（可选项）图片质量，只针对jpg格式图片（0-100整数）

videoQuality：

- 类型：字符串
- 默认值：medium
- 描述：（可选项）视频质量，取值范围(low、medium、high)，只支持iOS

targetWidth：

- 类型：数字
- 默认值：原图宽度
- 描述：（可选项）压缩后的图片宽度，图片会按比例适配此宽度

targetHeight：

- 类型：数字
- 默认值：原图高度
- 描述：（可选项）压缩后的图片高度，图片会按比例适配此高度

saveToPhotoAlbum：

- 类型：布尔
- 默认值：false
- 描述：（可选项）拍照或录制视频后是否保存到相册

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	data:"",                //图片路径
	base64Data:"",          //base64数据，destinationType为base64时返回
	duration:0              //视频时长（数字类型）
}
```
err：

- 类型：JSON对象

内部字段：

```js
{
    msg:""    //错误描述
}
```

##示例代码

```js
api.getPicture({
	sourceType: 'camera',
	encodingType: 'jpg',
	mediaValue: 'pic',
	destinationType: 'url',
	allowEdit: true,
	quality: 50,
	targetWidth: 100,
	targetHeight: 100,
	saveToPhotoAlbum: false
}, function( ret, err ){ 
	if( ret ){
		 alert( JSON.stringify( ret ) );
	}else{
         alert( JSON.stringify( err ) );
    }
});
```

##补充说明

获取图片

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**saveMediaToAlbum**<div id="81"></div>

保存图片和视频到系统相册

saveMediaToAlbum({params}, callback(ret, err))

##params

path：

- 类型：字符串
- 默认值：无
- 描述：本地文件路径，支持fs://、widget://等文件路径协议，必须带有扩展名

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:true     //是否保存成功
}
```
err：

- 类型：JSON对象

内部字段：

```js
{
    msg:""    //错误描述
}
```

##示例代码

```js
api.saveMediaToAlbum({
	path: 'fs://1.png'
}, function( ret, err ){ 
	if( ret ){
		 alert( JSON.stringify( ret ) );
	}else{
         alert( JSON.stringify( err ) );
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.1.0及更高版本


#**startRecord**<div id="54"></div>

录制amr格式音频

startRecord({params})

##params

path：

- 类型：字符串
- 默认值：无
- 描述：（可选项）文件路径，不传时自动创建路径

##示例代码

```js
api.startRecord({
    path: 'fs://a.amr'
});
```

##补充说明

录音格式为amr

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**stopRecord**<div id="58"></div>

停止录音

stopRecord(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	path:'',              //字符串，返回的音频地址
	duration:0            //数字类型，音频的时长
}
```

##示例代码

```js
api.stopRecord(function( ret, err ){
    if( ret ){
		 alert( JSON.stringify( ret ) );
	}else{
         alert( JSON.stringify( err ) );
    }	
});
```

##补充说明

停止录音

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**startPlay**<div id="53"></div>

开始播放音频

startPlay({params}, callback())

##params

path：

- 类型：字符串
- 默认值：无
- 描述：文件路径，支持fs://、widget://等文件路径协议

##callback()

播放完成的回调

##示例代码

```js
api.startPlay({
    path: 'widget://res/1.mp3'
},function( ret, err ){
    if( ret ){
		 alert( JSON.stringify( ret ) );
	}else{
         alert( JSON.stringify( err ) );
    }
});
```

##补充说明

播放音频

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**stopPlay**<div id="57"></div>

停止播放音频

stopPlay()

##示例代码

```js
api.stopPlay();
```

##补充说明

停止播放音频

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**openVideo**<div id="62"></div>

打开系统视频播放器

openVideo({params})

##params

url：

- 类型：字符串
- 默认值：无
- 描述：本地文件路径（支持fs://、widget://等文件路径协议）或者网络资源地址

##示例代码

```js
api.openVideo({
	url: 'widget://res/1.mp4'
});
```

##补充说明

打开系统视频播放器

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



</div>