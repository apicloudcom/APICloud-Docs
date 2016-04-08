/*
Title: polyVideo
Description: polyVideo
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">
<div class="outline">
[open](#1)

[setPath](#2)

[start](#3)

[pause](#4)

[stop](#5)

[close](#6)

[show](#7)

[hide](#8)

[fullScreen](#9)

[cancelFullScreen](#10)

[forward](#11)

[rewind](#12)

[seekTo](#13)

[setBrightness](#14)

[getBrightness](#15)

[setVolume](#16)

[getVolume](#17)

[addEventListener](#18)

[removeEventListener](#19)

</div>

#**概述**

polyVideo 封装了视频、音频播放功能。如果要播放网络音视频，需要到
[保利威视官网](http://www.polyv.net)注册账号，并上传视频，获取userId，readtoken，secretkey，以及每个视频的vid。

**本模块已停止维护更新，请使用优化升级版 [polyvVideo](http://docs.apicloud.com/端API/开放SDK/polyvVideo)**


**key.xml 配置详解：**

`key.xml` 文件需要放在 `widget/res` 文件目录下，格式如下：

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<security>
  <item name="userId" value="89176f0d6c"/>
  <item name="readtoken" value="995a1691-f8e3-4a2a-8b43-c0da02e3e29b"/>
  <item name="secretkey" value="yg2KfD03qs"/>
</security> 
```
- 字段描述:

    **userId**：在保利威视官网-->系统设置-->视频接口api-->userId

    **readtoken**：在保利威视官网-->系统设置-->视频接口api-->readtoken

    **secretkey**：在保利威视官网-->系统设置-->视频接口api-->secretkey

<div id="b1"></div>

#**open**<div id="1"></div>

打开一个音/视频播放器

open({params},function(ret))

##params

rect：

- 类型：JSON对象
- 描述：（可选项）模块的位置及尺寸，（仅对视频有效）
- 内部字段：

```js
{
    x: 0,   //（可选项）数字类型；模块左上角的 x 坐标（相对于所属的 Window 或 Frame）；默认：0
    y: 0,   //（可选项）数字类型；模块左上角的 y 坐标（相对于所属的 Window 或 Frame）；默认：0
    w: 320, //（可选项）数字类型；模块的宽度；默认：所属的 Window 或 Frame 的宽度
    h: 300  //（可选项）数字类型；模块的高度；默认：w的3/4
}
```

path：

- 类型：字符串
- 描述：（可选项）文档的路径，要求本地路径（fs://），在 android 平台上不支持 widget，**若 vid 不为空，则忽略本参数**

vid：

- 类型：字符串
- 描述：（可选项）视频的vid,播放网络视频时需要，**若本参数不为空，则忽略 path 参数**

autoPlay：

- 类型：布尔
- 描述：（可选项）打开时是否自动播放
- 默认值：true（自动播放）

fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window

fixed：

- 类型：布尔
- 描述：（可选项）模块是否随所属 Window 或 Frame 滚动
- 默认值：true（不随之滚动）


##callback(ret)

ret：

- 类型：JSON对象
- 描述：本回调函数在开始播放后每秒执行四次，直至播放结束、暂停、停止
- 内部字段：

```js
{
    eventType:        //字符串类型；回调事件类型，取值范围如下：
                      //show （打开播放器成功并显示）
                      //start（开始播放）
					  //playing (正在播放)
                      //stop（停止播放）
                      //pause（暂停播放）
                      //resetPath（重设媒体资源路径）
	duration:         //数字类型；音频总时长，单位为s(当eventType为 show 或 resetPath 时有值，否则为undefined)
	current:          //数字类型；当前播放位置，单位为s（每秒回调四次）
	complete:         //布尔类型；是否播放完毕
}
```

##示例代码

```js
var obj = api.require('polyVideo');
obj.open({
    rect: {
      x: 0,
      y: 0,
      w: 320,
      h: 240
    },
    path:'fs://res/video.mp4',
    autoPlay: true,
    fixedOn: api.frameName,
    fixed: false
},function(ret,err){
	var duration = ret.duration;
	var current = ret.current;
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setPath**<div id="2"></div>

设置音/视频的文件路径

setPath({params})

##params

path：

- 类型：字符串
- 描述：文档的路径，要求本地路径（fs://），在 android 平台上不支持 widget

##示例代码

```js
var obj= api.require('polyVideo');
obj.setPath({
    path:'fs://res/video.mp4',
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**start**<div id="3"></div>

开始播放

start()

##示例代码

	var obj= api.require('polyVideo');
	obj.start();

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**pause**<div id="4"></div>

暂停播放

pause()

##示例代码

	var obj= api.require('polyVideo');
	obj.pause();

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**stop**<div id="5"></div>

停止播放

stop()

##示例代码

	var obj= api.require('polyVideo');
	obj.stop();

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**close**<div id="6"></div>

关闭播放器

close()

##示例代码

	var obj= api.require('polyVideo');
	obj.close();

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**show**<div id="7"></div>

显示视频播放视图

show()

##示例代码

	var obj= api.require('polyVideo');
	obj.show();

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**hide**<div id="8"></div>

隐藏视频播放视图

hide()

##示例代码

	var obj= api.require('polyVideo');
	obj.hide();

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**fullScreen**<div id="9"></div>

全屏播放（横屏模式）

fullScreen()

##示例代码

	var obj= api.require('polyVideo');
	obj.fullScreen();

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**cancelFullScreen**<div id="10"></div>

取消全屏播放

cancelFullScreen()

##示例代码

	var obj= api.require('polyVideo');
	obj.cancelFullScreen();

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**forward**<div id="11"></div>

快进

forward(params)

##params

seconds：

- 类型：数字
- 描述：快进的秒数

##示例代码

	var obj= api.require('polyVideo');
	obj.forward({
		seconds:5
	});

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**rewind**<div id="12"></div>

快退

rewind(params)

##params

seconds：

- 类型：数字
- 描述：快退的秒数

##示例代码

	var obj= api.require('polyVideo');
	obj.rewind({
		seconds:5
	});

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**seekTo**<div id="13"></div>

跳转

seekTo(params)

##params

seconds：

- 类型：数字
- 描述：跳转到音视频播放的秒数

##示例代码

	var obj= api.require('polyVideo');
	obj.seekTo({
		seconds:20
	});

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setBrightness**<div id="14"></div>

设置屏幕亮度

setBrightness(params)

##params

brightness：

- 类型：数字
- 描述：（可选项）设置的屏幕的亮度，取值范围：0-100，**在 IOS 平台上设置的是系统屏幕亮度。Android 平台上设置的本应用内的屏幕亮度**
- 默认值：80


##示例代码

	var obj = api.require('polyVideo');
	obj.setBrightness({
		brightness:50
	});


##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本




#**getBrightness**<div id="15"></div>

获取当前屏幕亮度值

getBrightness(callBack(ret))


##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	brightness:            //数字类型；当前屏幕亮度值
}
```

##示例代码

	var obj = api.require('polyVideo');
	obj.getBrightness(function(ret,err){
			alert(ret.brightness);
		}
	);


##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**setVolume**<div id="16"></div>

设置音量

setVolume({params})

##params

volume：

- 类型：数字
- 描述：（可选项）音量大小，取值范围：0-1
- 默认值：0

##示例代码

```js
var obj = api.require('polyVideo');
obj.setVolume({
	volume:0.6
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**getVolume**<div id="17"></div>

获取当前播放音量

getVolume(callBack(ret,err))

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	volume:            //数字类型；当前音量值
}
```

##示例代码

```js
var obj = api.require('polyVideo');
obj.getVolume(function(ret){
		alert(ret.volume)
	}
);
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**addEventListener**<div id="18"></div>

添加动作监听(当全屏或者fixed为true且页面不能被左右滑动时有效)

addEventListener({params}，callBack(ret,err))

##params

name：

- 类型：字符串
- 描述：所要监听的动作名称
- 取值范围：
   - 'leftUp'：播放器靠左的二分之一内的上滑事件，每滑动5（百分比）回调执行一次
   - 'leftDown'：播放器靠左的二分之一内的下滑事件，每滑动5（百分比）回调执行一次
   - 'rightUp'：播放器靠右的二分之一内的上滑事件，每滑动5（百分比）回调执行一次
   - 'rightDown'：播放器靠右的二分之一内的下滑事件，每滑动5（百分比）回调执行一次
   - 'swipeLeft'：播放器上的左滑事件，每滑动5（百分比）回调执行一次
   - 'swipeRight'：播放器上的右滑事件，每滑动5（百分比）回调执行一次
   - 'click'：点击播放器事件（单击手势）

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
  
   start:                 //布尔类型；事件是否开始，true|false
   end:                   //布尔类型；事件是否结束，true|false
						  //手指处于滑动屏幕状态时，start、end 均为false
   
}
```

##示例代码

```js
var obj = api.require('polyVideo');
obj.addEventListener({
	name:'leftUp'
},function(ret){
	alert('leftUp');
}
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**removeEventListener**<div id="19"></div>

移除动作监听

removeEventListener({params})

##params

name：

- 类型：字符串
- 描述：所要移除的监听的动作名称
- 取值范围：
   - 'leftUp'：播放器靠左的二分之一内的上滑事件，每滑动5（百分比）回调执行一次
   - 'leftDown'：播放器靠左的二分之一内的下滑事件，每滑动5（百分比）回调执行一次
   - 'rightUp'：播放器靠右的二分之一内的上滑事件，每滑动5（百分比）回调执行一次
   - 'rightDown'：播放器靠右的二分之一内的下滑事件，每滑动5（百分比）回调执行一次
   - 'swipeLeft'：播放器上的左滑事件，每滑动5（百分比）回调执行一次
   - 'swipeRight'：播放器上的右滑事件，每滑动5（百分比）回调执行一次
   - 'click'：点击播放器事件（单击手势）

##示例代码

```js
var obj = api.require('polyVideo');
obj.removeEventListener({
		name:'leftUp'
	}
);
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

