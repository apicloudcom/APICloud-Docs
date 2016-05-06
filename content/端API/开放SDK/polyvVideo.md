/*
Title: polyvVideo
Description: polyvVideo
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：保利威视</p>

<ul id="tab" class="clearfix">
  <li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">
<div class="outline">
[setConfig](#0)

[open](#1)

[setPath](#2)

[setVid](#3)

[start](#4)

[pause](#5)

[stop](#6)

[close](#7)

[show](#8)

[hide](#9)

[fullScreen](#10)

[cancelFullScreen](#11)

[getDuration](#12)

[getCurrentPosition](#13)

[getBufferPercentage](#14)

[isPlaying](#15)

[forward](#16)

[rewind](#17)

[seekTo](#18)

[setBrightness](#19)

[getBrightness](#20)

[setVolume](#21)

[getVolume](#22)

[addEventListener](#23)

[removeEventListener](#24)

</div>


## 保利威视简介

保利威视（商标名“POLYV”）是一个第三方视频技术服务商，提供视频云计算服务平台，为教育行业等提供视频解决方案，隶属于广州易方信息科技有限公司，实现网络视频跨终端播放，是一家拥有自主知识产权的高新技术企业。



## 保利威视特色功能

* 无广告，不用再为视频播放前、暂停时的广告而烦扰和等待，向视频广告说NO！
* 极速加载，全网络覆盖，包含电信、联通、移动、教育网等运营商，通过智能CDN技术，为用户带来极速播放体验。
* 安全可靠，多副本的分布式存储系统保障数据安全性，三套CDN系统同时保障分发传输系统可靠性。
* 金牌服务，提供7*24小时的技术支持服务，且可由开发者直接面对开发者，以最快速度解决用户问题，打造行业服务标杆。



## 模块概述

polyvVideo 模块封装了保利威视 Android 与 iOS 原生 SDK，集成了保利威视常用的基本接口。使用本模块可以轻松把保利威视 Android 与 iOS SDK 集成到自己的 app 中，实现保利威视视频播放、下载、上传等功能。目前本模块仅包含保利威视视频播放功能，其他功能及其文档将持续更新，并以子模块形式添加到本模块中，敬请期待。

### 注意事项

* 使用本模块需要配置保利威视用户信息，即 app sdk 加密串（需配置到 *widget/res/key.xml* 中），开发者通过调用配置子模块中的 `setConfig` 方法进行配置。



# 配置子模块

polyvConfigModule 封装了对本模块用户配置的功能。

开发者要播放保利威视视频，需要到 [保利威视官网](http://www.polyv.net/) 注册账号，并上传视频，获取 `app sdk 加密串`，并将其配置到 `key.xml` 文件中，`key.xml` 文件需要放在 *widget/res* 文件目录下。

**key.xml 配置详解：**

配置格式如下：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<security>
	<item name="config" value="Q8T911eMCDjuRv/QjEF6KDovkjJx/w+ysCHa63lI8rccLuZ04GziWqjb24jUZMLRjBs1ceEo0zhHd6XXOrvO4fjqd5sdEIW/mBFqII3gszi4P8MuNYmyR7sJudbdgU91JXtby30a+M6EI7gCnPWdwQ=="/>
</security>
```

- 字段描述:

  - **config**：（必须配置）保利威视账号下的 app sdk 加密串（登录账号后，进入 *系统设置 \ 接口 API* 页面）




## **setConfig**<div id="0"></div>

配置本模块来自保利威视注册账号的用户信息，本方法只需调用**一次**。

setConfig()

### 示例代码

```javascript
var polyvConfig = api.require('polyvConfigModule');
polyvConfig.setConfig();
```

### 可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



# 视频播放子模块

polyvVideoModule 封装了保利威视视频播放功能。

## **open**<div id="1"></div>

打开一个视频播放器，通过回调返回播放状态

open({params},function(ret))

### params

`rect`：

- 类型：JSON 对象
- 描述：（可选项）模块的位置及尺寸，（仅对视频有效）
- 内部字段：

```json
{
    x: 0,   //（可选项）数字类型；模块左上角的 x 坐标（相对于所属的 Window 或 Frame）；默认：0
    y: 0,   //（可选项）数字类型；模块左上角的 y 坐标（相对于所属的 Window 或 Frame）；默认：0
    w: 320, //（可选项）数字类型；模块的宽度；默认：所属的 Window 或 Frame 的宽度
    h: 300  //（可选项）数字类型；模块的高度；默认：w的3/4
}
```

`path`：

- 类型：字符串
- 描述：（可选项）文档的路径，要求本地路径（fs://），在 android 平台上不支持 widget，**若 vid 不为空，则忽略本参数**

`vid`：

- 类型：字符串
- 描述：（可选项）视频的vid,播放网络视频时需要，**若本参数不为空，则忽略 path 参数**

`autoPlay`：

- 类型：布尔
- 描述：（可选项）打开时是否自动播放
- 默认值：true（自动播放）

`fixedOn`：

- 类型：字符串
- 描述：（可选项）模块所属 Frame 的名字，若不传则模块归属于当前 Window

`fixed`：

- 类型：布尔
- 描述：（可选项）模块是否随所属 window 或 frame 滚动
- 默认值：true（不随之滚动）

### callback

#### ret：

- 类型：JSON 对象
- 描述：本回调函数在播放状态改变时执行
- 内部字段：

```json
{
    eventType:        //字符串类型；回调事件类型，取值范围如下：
                      //show （打开播放器成功并显示）
                      //start（开始播放）
                      //stop（停止播放）
                      //pause（暂停播放）
                      //resetPath（重设媒体资源路径）
                      //complete(播放完毕)
}
```

#### err：

- 类型：JSON 对象
- 描述：本回调函数在播放错误时执行
- 内部字段：

```json
{
    msg:        //字符串类型；错误信息
}
```



### 示例代码

```javascript
var obj = api.require('polyvVideoModule');
obj.open({
    rect: {
      x: 0,
      y: 0,
      w: 320,
      h: 240
    },
    path:'fs://res/intro.mp4', // 传递本地路径
  	// vid:'sl8da4jjbx1c8baed8a48212d735d905_s', // 传递 vid
    autoPlay: true,
    fixedOn: api.frameName,
    fixed: false
},function(ret,err){
    var duration = ret.duration;
    var current = ret.current;
});
```

### 可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



## **setPath**<div id="2"></div>

设置视频的文件路径

setPath({params})

### params

`path`：

- 类型：字符串
- 描述：文档的路径或 HTTP 协议视频 URL，要求本地路径（fs://），在 android 平台上不支持 widget

### 示例代码

```javascript
var obj= api.require('polyvVideoModule');
obj.setPath({
    path:'fs://res/video.mp4',
});
```

### 可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



## **setVid**<div id="3"></div>

设置播放视频的 vid

setVid({params})

### params

`vid`：

- 类型：字符串
- 描述：视频 vid

### 示例代码

```javascript
var obj= api.require('polyvVideoModule');
obj.setVid({
    vid:'sl8da4jjbxc5565c46961a6f88ca52e5_s',
});
```

### 可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



## **start**<div id="4"></div>

开始播放

start()

### 示例代码

```javascript
var obj= api.require('polyvVideoModule');
obj.start();
```

### 可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



## **pause**<div id="5"></div>

暂停播放

pause()

### 示例代码

```javascript
var obj= api.require('polyvVideoModule');
obj.pause();
```

### 可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



## **stop**<div id="6"></div>

停止播放

stop()

### 示例代码

```javascript
var obj= api.require('polyvVideoModule');
obj.stop();
```

### 可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



## **close**<div id="7"></div>

关闭播放器

close()

### 示例代码

```javascript
var obj= api.require('polyvVideoModule');
obj.close();
```

### 可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



## **show**<div id="8"></div>

显示视频播放视图

show()

### 示例代码

```javascript
var obj= api.require('polyvVideoModule');
obj.show();
```

### 可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



## **hide**<div id="9"></div>

隐藏视频播放视图

hide()

### 示例代码

```java
var obj= api.require('polyvVideoModule');
obj.hide();
```

### 可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



## **fullScreen**<div id="10"></div>

全屏播放（横屏模式）

fullScreen()

### 示例代码

```javascript
var obj= api.require('polyvVideoModule');
obj.fullScreen();
```

### 可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



## **cancelFullScreen**<div id="11"></div>

取消全屏播放

cancelFullScreen()

### 示例代码

```javascript
var obj= api.require('polyvVideoModule');
obj.cancelFullScreen();
```

### 可用性

iOS系统，Android系统

可提供的1.0.0及更高版本




## **getDuration**<div id="12"></div>

获得当前视频时长

getDuration(callback(ret, err))

### callback(ret, err)

#### ret：

- 类型：JSON 对象
- 内部字段：

```json
{
    duration:            // 数字类型；当前视频时长
}
```

### 示例代码

```javascript
var obj = api.require('polyvVideoModule');
obj.getDuration(function(ret,err){
        alert(ret.duration);
    }
);
```

### 可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



## **getCurrentPosition**<div id="13"></div>

获取视频当前播放位置（时间）

getCurrentPosition(callback(ret, err))

### callback(ret, err)

#### ret：

- 类型：JSON 对象
- 内部字段：

```json
{
    currentPosition:            // 数字类型；视频当前播放进度（时间）
}
```

### 示例代码

```javascript
var obj = api.require('polyvVideoModule');
obj.getCurrentPosition(function(ret,err){
        alert(ret.currentPosition);
    }
);
```

### 可用性

iOS系统，Android系统

可提供的1.0.0及更高版本




## **getBufferPercentage**<div id="14"></div>

获取视频当前缓存进度

getBufferPercentage(callback(ret, err))

### callback(ret, err)

#### ret：

- 类型：JSON 对象
- 内部字段：

```json
{
    bufferPercentage:            // 数字类型，取值：0~100；当前缓存进度
}

```

### 示例代码

```javascript
var obj = api.require('polyvVideoModule');
obj.getBufferPercentage(function(ret,err){
        alert(ret.bufferPercentage);
    }
);
```

### 可用性

iOS系统，Android系统

可提供的1.0.0及更高版本




## **isPlaying**<div id="15"></div>

当前视频是否正在播放

isPlaying(callback(ret, err))

### callback(ret, err)

#### ret：

- 类型：JSON 对象
- 内部字段：

```json
{
    isPlaying:            // bool 类型；视频是否正在播放
}

```

### 示例代码

```javascript
var obj = api.require('polyvVideoModule');
obj.isPlaying(function(ret,err){
        alert(ret.isPlaying);
    }
);
```

### 可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



## **forward**<div id="16"></div>

快进

forward({params})

### params

`seconds`：

- 类型：数字
- 描述：快进的秒数

### 示例代码

```javascript
var obj= api.require('polyvVideoModule');
obj.forward({
    seconds:5
});
```

### 可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



## **rewind**<div id="17"></div>

快退

rewind({params})

### params

`seconds`：

- 类型：数字
- 描述：快退的秒数

### 示例代码

```javascript
var obj= api.require('polyvVideoModule');
obj.rewind({
    seconds:5
});
```

### 可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



## **seekTo**<div id="18"></div>

跳转

seekTo({params})

### params

`seconds`：

- 类型：数字
- 描述：跳转到音视频播放的秒数

### 示例代码

```javascript
var obj= api.require('polyvVideoModule');
obj.seekTo({
    seconds:20
});
```

### 可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



## **setBrightness**<div id="19"></div>

设置屏幕亮度

setBrightness({params})

### params

`brightness`：

- 类型：数字
- 描述：（可选项）设置的屏幕的亮度，取值范围：0-100，**在 iOS 平台上设置的是系统屏幕亮度。Android 平台上设置的本应用内的屏幕亮度**
- 默认值：80

### 示例代码

```javascript
var obj = api.require('polyvVideoModule');
obj.setBrightness({
    brightness:50
});
```

### 可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



## **getBrightness**<div id="20"></div>

获取当前屏幕亮度值

getBrightness(callback(ret, err))

### callback(ret, err)

`ret`：

- 类型：JSON 对象
- 内部字段：

```json
{
    brightness:            //数字类型；当前屏幕亮度值
}
```

### 示例代码

```javascript
var obj = api.require('polyvVideoModule');
obj.getBrightness(function(ret,err){
        alert(ret.brightness);
    }
);
```

### 可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



## **setVolume**<div id="21"></div>

设置音量

setVolume({params})

### params

`volume`：

- 类型：数字
- 描述：（可选项）音量大小，取值范围：0-1
- 默认值：0

### 示例代码

```javascript
var obj = api.require('polyvVideoModule');
obj.setVolume({
    volume:0.6
});
```

### 可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



## **getVolume**<div id="22"></div>

获取当前音量

getVolume(callback(ret, err))

### callback(ret, err)

#### ret：

- 类型：JSON 对象
- 内部字段：

```json
{
    volume:            //数字类型；当前音量值
}
```

### 示例代码

```javascript
var obj = api.require('polyvVideoModule');
obj.getVolume(function(ret){
        alert(ret.volume)
    }
);
```

### 可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



## **addEventListener**<div id="23"></div>

添加手势监听(当全屏或者 fixed 为 true 且页面不能被左右滑动时有效)

addEventListener({params}，callback(ret, err))

### params

`name`：

- 类型：字符串
- 描述：所要监听的手势名称
- 取值范围：
  - `leftUp`：播放器靠左的二分之一内的上滑事件，每滑动5（百分比）回调执行一次
  - `leftDown`：播放器靠左的二分之一内的下滑事件，每滑动5（百分比）回调执行一次
  - `rightUp`：播放器靠右的二分之一内的上滑事件，每滑动5（百分比）回调执行一次
  - `rightDown`：播放器靠右的二分之一内的下滑事件，每滑动5（百分比）回调执行一次
  - `swipeLeft`：播放器上的左滑事件，每滑动5（百分比）回调执行一次
  - `swipeRight`：播放器上的右滑事件，每滑动5（百分比）回调执行一次
  - `click`：点击播放器事件（单击手势）

### callback(ret, err)

#### ret：

- 类型：JSON 对象
- 内部字段：

```json
{

   start:                 //布尔类型；事件是否开始，true|false
   end:                   //布尔类型；事件是否结束，true|false
                          //手指处于滑动屏幕状态时，start、end 均为false

}
```

### 示例代码

```javascript
var obj = api.require('polyvVideoModule');
obj.addEventListener({
    name:'leftUp'
},function(ret){
    alert('leftUp');
}
```

### 可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



## **removeEventListener**<div id="24"></div>

移除手势监听

removeEventListener({params})

### params

`name`：

- 类型：字符串
- 描述：所要移除的监听的手势名称
- 取值范围：
  - `leftUp`：播放器靠左的二分之一内的上滑事件，每滑动5（百分比）回调执行一次
  - `leftDown`：播放器靠左的二分之一内的下滑事件，每滑动5（百分比）回调执行一次
  - `rightUp`：播放器靠右的二分之一内的上滑事件，每滑动5（百分比）回调执行一次
  - `rightDown`：播放器靠右的二分之一内的下滑事件，每滑动5（百分比）回调执行一次
  - `swipeLeft`：播放器上的左滑事件，每滑动5（百分比）回调执行一次
  - `swipeRight`：播放器上的右滑事件，每滑动5（百分比）回调执行一次
  - `click`：点击播放器事件（单击手势）

### 示例代码

```javascript
var obj = api.require('polyvVideoModule');
obj.removeEventListener({
        name:'leftUp'
    }
);
```

### 可用性

iOS系统，Android系统

可提供的1.0.0及更高版本