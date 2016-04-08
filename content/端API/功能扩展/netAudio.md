/*
Title: netAudio
Description: netAudio
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[play](#1)

[setVolume](#2)

[setProgress](#3)

[pause](#4)

[stop](#5)

[addEventListener](#6)
</div>

#**概述**

netAudio封装了对网络音频流播放的接口，使用本模块可以实现对服务器端音频流资源的播放、暂停、继续、停止、设置播放位置等相关操作。目前暂不支持缓存到本地。在ios上如需支持后台播放功能请参考应用配置说明文档里关于[BackgroundMode的配置](http://docs.apicloud.com/APICloud/技术专题/app-config-manual)

#**play**<div id="1"></div>

播放网络音频

play({params}, callback(ret, err))

##params

path：

- 类型：字符串
- 描述：网络音频资源地址

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	duration:            //音频总时长，单位为s
	current：			  //当前播放位置，单位为s
	complete:			 //布尔类型，是否播放完毕
}
```

##示例代码

```js
var netAudio = api.require('netAudio');
netAudio.play({
	path: 'http://7xisq1.com1.z0.glb.clouddn.com/apicloud/0d0b81b8bd5ab81bda9ca54267eb9b98.mp3'
},function( ret, err ){		
	if( ret ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**setVolume**<div id="2"></div>

设置音量

setVolume({params})

##params

volume：

- 类型：数字
- 描述：（可选项）音量大小（0-1）
- 默认值：0

##示例代码

```js
var netAudio = api.require('netAudio');
netAudio.setVolume({
	volume: 0.6
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**setProgress**<div id="3"></div>

设置播放位置

setProgress({params})

##params

progress：

- 类型：数字
- 描述：（可选项）播放位置百分比，取值范围：0-100
- 默认值：0

##示例代码

```js
var netAudio = api.require('netAudio');
netAudio.setProgress({
	progress: 50
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**pause**<div id="4"></div>

暂停播放

pause()

##示例代码

```js
var netAudio = api.require('netAudio');
netAudio.pause();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**stop**<div id="5"></div>

停止播放

stop()

##示例代码

```js
var netAudio = api.require('netAudio');
netAudio.stop();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**addEventListener**<div id="6"></div>

监听被其它 app 打断事件，**暂仅支持 ios 平台**

addEventListener(callback(ret))

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	eventType:            //字符串类型；交互事件类型，取值范围如下：
	                      //pause：播放暂停
}
```

##示例代码

```js
var audio = api.require('netAudio');
audio.addEventListener(function(ret){
   alert('pause');
});
```

##可用性

IOS系统

可提供的1.0.0及更高版本
