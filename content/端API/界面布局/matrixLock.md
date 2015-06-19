/*
Title: matrixLock
Description: matrixLock
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[openSetView](#1)

[checkGesture](#2)

[clearGesture](#3)

[showSetView](#4)
 
[hideSetView](#5)

[closeSetView](#6)
 
[openEnterView](#7)
 
[showEnterView](#8)
 
[hideEnterView](#9)

[closeEnterView](#10)
 
</div>

#**概述**

matrixLock模块是一个矩阵锁，可加锁屏幕，让用户通过输入特定的矩阵路线来解锁屏幕。手势密码会被加密存储到本地。本模块允许开发者自定义矩阵锁屏大小，矩阵的行列数，每个矩阵的元素亦可自定义其样式。模块内接口列表可分为两部分：设置手势密码界面、验证手势密码界面，通过设置手势密码界面可让用户设置自己的手势密码，然后通过验证界面验证设置的密码。本模块属于第三方模块开发者提供，所以平台开发者不能通过IDE真机同步调试，仅支持在线云编译调试

#**openSetView**<div id="1"></div>

打开设置密码页面

openSetView ({params}, callback(ret, err))

##params

bg：

- 类型：字符串
- 默认值：rgba(0,0,0,0)
- 描述：背景设置，支持img，#，rgb，rgba，可为空

x:

- 类型：数字
- 默认值：0
- 描述：地图视图左上角点的x坐标，可为空

y:

- 类型：数字
- 默认值：100
- 描述：地图视图左上角点的y坐标，可为空

w:

- 类型：数字
- 默认值：当前设备屏幕的宽
- 描述：设置手势密码视图的宽，可为空

h:

- 类型：数字
- 默认值：w+w/3.0
- 描述：设置手势密码视图的高，可为空

tips：

- 类型：json对象
- 默认值：见内部字段
- 描述：提示文字配置，可为空

内部字段：

```js
{
	size：			//提示文字大小，数字类型，默认12，可为空
	color:       	//提示文字颜色，字符串,默认#696969,支持#,rgb,rgba，可为空
	sizeError：		//错误提示文字大小，数字类型，默认12，可为空
	colorError:  	//错误提示文字颜色，字符串,默认#FF3030,支持#,rgb,rgba，可为空
}
```

matrix：

- 类型：json对象
- 默认值：见内部字段
- 描述：矩阵配置，可为空

内部字段:

```js
{ 
	row:        //矩阵行数，数字类型，默认3，可为空
	column:     //矩阵列数，数字类型，默认3，可为空
	radius：//矩阵元素的半径，数字类型，默认80，可为空
	activeBg:   //滑动经过元素的背景，字符串，默认#8deeee圆环加圆点,支持#,rgb,rgba,img,可空
	inactiveBg：//元素常态时的背景，字符串，默认#e8e8e8圆环,支持#,rgb,rgba,img,可空
	errorBg://报错时滑动经过元素的背景，字符串，默认#FF3030圆环加圆点,支持#,rgb,rgba,img,可空
	normalLine: //常态时元素间连接线颜色,字符串,默认#9ac0cd,支持#,rgb,rgba,可空
	errorLine: //错误时元素间连接线颜色,字符串,默认#a0522d,支持#,rgb,rgba,可空
	lineWidth：//连接线线条的粗细，数字类型，默认5，可为空
	arrow：//手势走向指示箭头色值，支持rgb，rgba，#，默认#8deee，可为空
	arrowError://报错时手势走向指示箭头色值，支持rgb，rgba，#，默认#8deee，可为空
}
```

anim：

- 类型：布尔值
- 默认值：false
- 描述：打开时是否添加从下往上弹出的动画，可为空

fixedOn：

- 类型：字符串
- 默认值：当前窗口名
- 描述：将模块视图添加到指定窗口的名字，可为空

fixed：

- 类型：布尔
- 默认值：true
- 描述：是否将模块视图固定到窗口上，不跟随窗口上下滚动，可为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:       //设置手势密码成功
}
```

err：

- 类型：JSON对象

内部字段：

```js
{

	code:       //错误描述，取值范围及其错误信息如下：
	-1：//未知错误
	0：//用户连接少于四个点
	1：//用户第二次绘制与上次不一致
}
```

##示例代码

```js
var obj = api.require('matrixLock');
obj.openSetView (function(ret, err){
	if(ret.status){
		api.alert({msg:'设置成功'});
	}else{
		api.alert({msg:err.code});
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**checkGesture**<div id="2"></div>

检查是否已设置手势密码

checkGesture(callBack(ret,err))

##callBack(ret,err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	code:       //手势密码设置状态码，取值范围及其信息如下：
	-1：//未知错误
	0：//用户已设计手势密码
	1：//用户未设置手势密码
}
```

##示例代码

```js
var obj = api.require('matrixLock');
obj.checkGesture(function(ret){
	api.alert({msg:ret.code});
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**clearGesture**<div id="3"></div>

清空设置的手势密码

clearGesture(callBack(ret,err))

##callBack(ret,err)

ret：

- 类型：JSON对象

内部字段：

	{
		status:       //布尔类型，操作是否成功
	}

err：

- 类型：JSON对象

内部字段：

	{
		msg:       //字符串类型，操作失败信息
	}

##示例代码

	var obj = api.require('matrixLock');
	obj.clearGesture();

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**showSetView**<div id="4"></div>

显示矩阵锁视图

showSetView(params)

##params

anim：

- 类型：布尔值
- 默认值：false
- 描述：显示时是否添加从下往上弹出的动画，可为空

##示例代码

	var obj = api.require('matrixLock');
	obj.showSetView();

##补充说明

显示已经隐藏的矩阵锁视图

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**hideSetView**<div id="5"></div>

隐藏矩阵锁视图

hideSetView(params)

##params

anim：

- 类型：布尔值
- 默认值：false
- 描述：隐藏时是否添加从下往上弹出的动画，可为空

##示例代码

	var obj = api.require('matrixLock');
	obj.hideSetView();

##补充说明

隐藏矩阵锁视图，并没有从内存中清除

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**closeSetView**<div id="6"></div>

关闭设置密码页面

closeSetView(params)

##params

anim：

- 类型：布尔值
- 默认值：false
- 描述：打开时是否添加从下往上弹出的动画，可为空

##示例代码

	var obj = api.require('matrixLock');
	obj.closeSetView();

##补充说明

关闭视图

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**openEnterView**<div id="7"></div>

打开验证手势密码视图

openEnterView ({params}, callback(ret, err))

##params

bg：

- 类型：字符串
- 默认值：rgba(0,0,0,0)
- 描述：背景设置，支持img，#，rgb，rgba，可为空

x:

- 类型：数字
- 默认值：0
- 描述：地图视图左上角点的x坐标，可为空

y:

- 类型：数字
- 默认值：207
- 描述：地图视图左上角点的y坐标，可为空

w:

- 类型：数字
- 默认值：当前设备屏幕的宽
- 描述：设置手势密码视图的宽，可为空

h:

- 类型：数字
- 默认值：w
- 描述：设置手势密码视图的高，可为空

matrix：

- 类型：json对象
- 默认值：见内部字段
- 描述：矩阵配置，可为空

内部字段:

```js
{ 
	row:        //矩阵行数，数字类型，默认3，可为空
	column:     //矩阵列数，数字类型，默认3，可为空
	radius：//矩阵元素的半径，数字类型，默认80，可为空
	activeBg:   //滑动经过元素的背景，字符串，默认#8deeee圆环加圆点,支持#,rgb,rgba,img,可空
	inactiveBg：//元素常态时的背景，字符串，默认#e8e8e8圆环,支持#,rgb,rgba,img,可空
	errorBg://报错时滑动经过元素的背景，字符串，默认#FF3030圆环加圆点,支持#,rgb,rgba,img,可空
	normalLine: //常态时元素间连接线颜色,字符串,默认#9ac0cd,支持#,rgb,rgba,可空
	errorLine: //错误时元素间连接线颜色,字符串,默认#a0522d,支持#,rgb,rgba,可空
	lineWidth：//连接线线条的粗细，数字类型，默认5，可为空
	arrow：//手势走向指示箭头色值，支持rgb，rgba，#，默认#8deee，可为空
	arrowError://报错时手势走向指示箭头色值，支持rgb，rgba，#，默认#8deee，可为空
}
```

anim：

- 类型：布尔值
- 默认值：true
- 描述：打开时是否添加从下往上弹出的动画，可为空

fixedOn：

- 类型：字符串
- 默认值：当前窗口名
- 描述：将模块视图添加到指定窗口的名字，可为空

fixed：

- 类型：布尔
- 默认值：true
- 描述：是否将模块视图固定到窗口上，不跟随窗口上下滚动，可为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

	{
		status:       //通过手势密码验证
    }

err：

- 类型：JSON对象

内部字段：

```js
{
	code:       //验证手势密码错误码，取值范围及其错误信息如下：
	-1：//未知错误
	0：//尚未设置手势密码
	1：//用户输入手势密码错误
}
```

##示例代码

```js
var obj = api.require('matrixLock');
obj.openEnterView (function(ret, err){
	if(ret.status){
		api.alert({msg:'验证通过'});
	}else{
		api.alert({msg:err.code});
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**showEnterView**<div id="8"></div>

显示手势密码验证视图

showEnterView(params)

##params

anim：

- 类型：布尔值
- 默认值：false
- 描述：显示时是否添加从下往上弹出的动画，可为空

##示例代码

	var obj = api.require('matrixLock');
	obj.showEnterView();

##补充说明

显示已经隐藏的矩阵锁视图

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**hideEnterView**<div id="9"></div>

隐藏手势密码验证矩阵锁视图

hideEnterView(params)

##params

anim：

- 类型：布尔值
- 默认值：false
- 描述：隐藏时是否添加从下往上弹出的动画，可为空

##示例代码

	var obj = api.require('matrixLock');
	obj.hideEnterView();

##补充说明

隐藏矩阵锁视图，并没有从内存中清除

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**closeEnterView**<div id="10"></div>

关闭手势验证视图

closeEnterView(params)

##params

anim：

- 类型：布尔值
- 默认值：true
- 描述：打开时是否添加从下往上弹出的动画，可为空

##示例代码

	var obj = api.require('matrixLock');
	obj.closeEnterView();

##补充说明

关闭视图

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

