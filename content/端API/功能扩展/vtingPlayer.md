/*
Title: vtingPlayer
Description: vtingPlayer封装了网络音频播放功能
*/

<p style="color: #ccc;margin-bottom: 30px;">来自于：开发者</p>

<div class="outline">
[play](#a1)

[pause](#a2)

[stop](#a3)

[setProgress](#a4)

[nowPlaying](#a5)

</div>

#**概述**

vtingPlayer 封装了网络音频播放功能，可播放纯音频 m3u8，在线 FM 首选格式，实现对音频资源的播放、暂停、继续、停止、设置播放位置等相关操作。在 ios 上如需支持后台播放功能请参看下例配置。

- 配置后台运行示例:

```xml
   <preference name="backgroundMode' value="audio'/>
```
- 描述:

    用于配置iOS后台运行，配置后可以实现后台播放音乐等功能。云编译有效。
    
<div id="a1"></div>
#**play**

播放网络音频，支持m3u8纯音频播放

play({params}, callback(ret, err))

##params

url:

- 类型：字符串
- 描述：音频资源地址

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    duration:       //数字类型；音频总时长，单位为s
    position:	    //数字类型；当前播放位置，单位为s
}
```

##示例代码

```js
var vtingPlayer = api.require('vtingPlayer');
vtingPlayer.play({
    url: 'widget://test.wav'
}, function(ret, err){		
	if( ret ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```

##特别说明

当播放源为m3u8时，请确保m3u8的ts切片不包含视频信息，若包含视频信息，IOS将不能支持后台播放，安卓部分机型（小米、魅族等）将无法播放或者缓冲时间明显加长等问题。

##可用性

iOS系统，Android系统（Android系统监听来去电，实现自动暂停播放和自动恢复播放）

可提供的1.0.0及更高版本

<div id="a2"></div>
#**pause**

暂停播放

pause()

##示例代码

```js
var vtingPlayer = api.require('vtingPlayer');
vtingPlayer.pause();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="a3"></div>
#**stop**

停止播放

stop()

##示例代码

```js
var vtingPlayer = api.require('vtingPlayer');
vtingPlayer.stop();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="a4"></div>
#**setProgress**

设置播放位置

setProgress({params})

##params

progress：

- 类型：数字
- 描述：播放位置百分比，取值范围：0-100

##示例代码

```js
var vtingPlayer = api.require('vtingPlayer');
vtingPlayer.setProgress({
    progress: 50
});
```

##可用性

仅支持IOS

可提供的1.0.0及更高版本

<div id="a5"></div>
#**nowPlaying**

设置当前播放内容锁屏显示信息

nowPlaying({params})

##params

title：

- 类型：字符串
- 描述：（可选项）显示标题。

artist：

- 类型：字符串
- 描述：（可选项）显示作者。

zhuanji：

- 类型：字符串
- 描述：（可选项）显示专辑名。

##示例代码

```js
var vtingPlayer = api.require('vtingPlayer');
vtingPlayer.nowPlaying({
	title: '歌曲名',
	artist: '作者',
	zhuanji: '专辑'
});
```

##可用性

仅支持 IOS

可提供的1.0.0及更高版本
