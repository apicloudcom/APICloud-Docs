/*
Title: audioPlayer
Description: audioPlayer
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[initPlayer](#1)

[play](#2)

[pause](#3)

[stop](#4)

[setVolume](#5)

[getVolume](#6)

[setProgress](#7)

[getProgress](#8)

[getState](#9)

[getBufferPercent](#10)

[addEventListener](#11)

[removeEventListener](#12)

[clearCache](#13)

[scanAudioLibrary](#14)
</div>

#*模块概述*

audioPlayer 是一个音频播放器，支持对本地、网络音频资源的播放。当播放网络音频时模块会把网络音频资源缓存到本地，并将缓存到本地的音频绝对路径返回给开发者。开发者可以通过 clearCache 接口，手动清除缓存在本地的音频资源，也可以通过 [fs](http://docs.apicloud.com/端API/功能扩展/fs) 模块的相关接口对单个缓存在本地的音频进行移动、删除等操作。开发者调用 api.clearCache 接口时也会清除所有本模块已缓存的音频文件。

对于缓冲音频文件的进度，开发者可通过 addEventListener 接口监听，也可通过 getBufferPercent 接口获取缓冲进度的百分比。当开发者调用 initPlayer 接口时模块底层会初始化一个播放器的实例对象，并判断是否是需要加载缓冲的资源（网络资源、在iOS上的音乐库资源），若是则进一步判断此音频资源是否已缓存到本地，若已缓存（未缓冲完整也按已缓存处理）则直接播，若未缓存则开始缓冲。

本模块可通过 scanAudioLibrary 接口扫描本地音频资源库 （在 iOS 上仅扫描系统音乐库），获取其标题、歌手、专辑、路径等信息。在 iOS 平台上，存在三种音频资源：1，网络音频；2，APP 沙箱（每个 APP 在系统内相当于一个文件夹，APP 只能访问本文件夹内的文件）内的音频；3，音乐库（系统音乐 APP，可通过 iTunes 同步的音频库）音频；本模块播放第三种音频资源时也会把音频文件缓存到 当前 APP 的沙箱内。

如需支持后台播放功能请参考 config.xml 配置说明文档里关于 [BackgroundMode](http://docs.apicloud.com/APICloud/技术专题/app-config-manual) 的配置

配置实例如下：

```js
<preference name="backgroundMode" value="audio"/>
```

在 iOS 平台上，当音频在后台播放时，若启动其它播放音频的 APP，则后台播放事件会被挂起。当有电话呼入、呼出或其它占用喇叭的事件发生时，也会打断后台播放音频。被打断播放的事件可通过 addEventListener 接口监听。

#*模块接口*

#**initPlayer**<div id="1"></div>

初始化音频播放器，若是网络音频资源则同时开始缓冲音频文件到本地

initPlayer({params}, callback(ret))

##params

path：

- 类型：字符串
- 描述：音频资源地址，支持本地和网络路径（fs://、widget://、http://、ipod-library:// 等）

cache：

- 类型：布尔类型
- 描述：（可选项）是否对网络音频资源进行缓存，仅当音频资源为网络音频时有效（在 iOS 上对 ipod 音乐库音频也有效）
- 默认值：false

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	status: true,        //布尔类型；操作成功状态值，true|false
	duration: 289,       //数字类型；音频总时长，单位为s（当status为true时有值）
	path: ''		        //字符串类型；所播放的音频资源在本地的绝对路径，仅当 cache 为 true 时有值
}
```

##示例代码

```js
var audioPlayer = api.require('audioPlayer');
audioPlayer.initPlayer({
	path: 'http://7xisq1.com1.z0.glb.clouddn.com/apicloud/0d0b81b8bd5ab81bda9ca54267eb9b98.mp3',
	cache: true
},function( ret ){		
	if( ret.status ){
		api.alert({ msg:JSON.stringify(ret) });
	}
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**play**<div id="2"></div>

播放音频，只有当前播放器为暂停、播放完成状态时有效

play()

##示例代码

```js
var audioPlayer = api.require('audioPlayer');
audioPlayer.play();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**pause**<div id="3"></div>

暂停播放

pause()

##示例代码

```js
var audioPlayer = api.require('audioPlayer');
audioPlayer.pause();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**stop**<div id="4"></div>

停止播放

stop()

##示例代码

```js
var audioPlayer = api.require('audioPlayer');
audioPlayer.stop();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setVolume**<div id="5"></div>

设置音量

setVolume({params})

##params

volume：

- 类型：数字
- 描述：（可选项）音量大小（0-1）
- 默认值：0

##示例代码

```js
var audioPlayer = api.require('audioPlayer');
audioPlayer.setVolume({
	volume: 0.6
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**getVolume**<div id="6"></div>

设置音量

getVolume(callback(ret))

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	volume: 0.5       //数字类型；当前音频播放器的音量，取值范围：0-1
}
```

##示例代码

```js
var audioPlayer = api.require('audioPlayer');
audioPlayer.getVolume(function(ret){
    api.alert({msg:ret.volume});
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setProgress**<div id="7"></div>

设置播放位置

setProgress({params})

##params

progress：

- 类型：数字
- 描述：（可选项）播放位置在总时上的百分比，取值范围：0-100
- 默认值：0

##示例代码

```js
var audioPlayer = api.require('audioPlayer');
audioPlayer.setProgress({
	progress: 50
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**getProgress**<div id="8"></div>

获取当前播放的位置在总时长的百分比

getProgress(callback(ret))

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	progress: 50       //数字类型；当前播放位置占总时长的百分比，取值范围：0-100
}
```

##示例代码

```js
var audioPlayer = api.require('audioPlayer');
audioPlayer.getProgress(function(ret){
    api.alert({msg:ret.progress});
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**getState**<div id="9"></div>

获取当前播放器的状态

getState(callback(ret))

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	state: 'playing'   //字符串类型；当前播放器的状态，取值范围如下：
						   //playing：正在播放
						   //paused：暂停
						   //idle：闲置
						   //finished：播放完成
						   //buffering：正在缓冲
						   //error：出现错误
}
```

##示例代码

```js
var audioPlayer = api.require('audioPlayer');
audioPlayer. getState(function(ret){
    api.alert({msg:ret.state});
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**getBufferPercent**<div id="10"></div>

获取已缓冲的音频文件占音频文件的百分比

getBufferPercent(callback(ret))

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	percent: 50       //数字类型；获取的已缓冲的音频文件占音频文件的百分比，取值范围：0-100
}
```

##示例代码

```js
var audioPlayer = api.require('audioPlayer');
audioPlayer.getBufferPercent(function(ret){
    api.alert({msg:ret.percent});
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**addEventListener**<div id="11"></div>

监听事件

addEventListener({params}, callback(ret))

##params

name：

- 类型：字符串
- 描述：（可选项）监听的事件类型
- 默认：playing
- 取值范围：
   - playing：播放进度，每有播放进度改变事件则触发此回调（频率为每秒3次）
   - complete：播放结束事件
   - pause：被其他占用喇叭事件打断时，本模块播放暂停（仅支持ios）
   - buffering：网络音频缓冲事件，每有缓冲进度变化时触发此回调（频率为每秒3次）
   - state：播放器状态改变事件

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	progress: 30       //数字类型；当前播放位置，单位为s，仅当 name 为 playing 时有值
	received: 100,     //数字类型；缓冲到本地的数据大小，单位为 byte，仅当 name 为 buffering 时有值 
	expected: 100,     //数字类型；尚未缓冲的数据大小，单位为 byte，仅当 name 为 buffering 时有值 
	speed: 100         //数字类型；缓冲速度大小，单位为 byte，  仅当 name 为 buffering 时有值
	state: 'playing'   //字符串类型；当前播放器的状态，取值范围如下：
						   //playing：正在播放
						   //paused：暂停
						   //idle：闲置
						   //finished：播放完成
						   //buffering：正在缓冲
						   //error：出现错误
}
```

##示例代码

```js
var audio = api.require('audioPlayer');
audio.addEventListener({
   name: "complete"
},function(ret){
	alert( '播放完成！' );
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**removeEventListener**<div id="12"></div>

监听事件

removeEventListener({params})

##params

name：

- 类型：字符串
- 描述：（可选项）要移除的监听事件类型
- 默认：playing
- 取值范围：
   - playing：播放进度，每有播放进度改变事件则触发此的回调
   - complete：播放结束事件
   - pause：当前播放被其他占用喇叭的事件打断时（仅支持iOS）
   - buffering：网络音频缓冲事件，每有缓冲进度变化时触发的回调
   - state：播放器状态改变事件

##示例代码

```js
var audio = api.require('audioPlayer');
audio.removeEventListener({
   name: "complete"
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**clearCache**<div id="13"></div>

清除缓存到本地的音频文件，**本接口只清除本模块缓存的数据，若要清除本 app 缓存的所有数据则调用api.clearCache**

clearCache()

##示例代码

```js
var audioPlayer = api.require('audioPlayer');
audioPlayer.clearCache();
```

##可用性

IOS系统，Android系统

可提供的1.0.0及更高版本

#**scanAudioLibrary**<div id="14"></div>

扫描本地音频资源，在 iOS 上仅扫描系统音乐库资源

scanAudioLibrary(callback(ret))

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	audios:[{            //数组类型；获取的音频资源信息组成的数组
	   artist: '',       //字符串类型；音频作者
	   title: '',        //字符串类型；音频标题
	   url: '',          //字符串类型；音频地址
	   albumTitle: ''    //字符串类型；音频专辑
	}]
}
```

##示例代码

```js
var audioPlayer = api.require('audioPlayer');
audioPlayer.scanAudioLibrary(function(ret){
    api.alert({msg:JSON.stringify(ret)});
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本