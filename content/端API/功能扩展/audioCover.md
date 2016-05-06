/*
Title: audioCover
Description: audioCover
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[set](#1)

[update](#2)

[cancel](#3)

</div>

#**概述**

audioCover 封装了设置音乐播放锁屏界面的相关接口。当音乐播放时切换到后台（音频后台播放功能需要在 config.xml 文件里进行相关配置，详情参考 config 文件配置文档）锁屏后，再次点击开屏键，当前屏幕会显示一个音乐播放器页面，该界面中有播放器的控制按钮，可点击按钮和用户播放器进行交互。通过本模块可以对该页面进行相关功能的自定义设置。**在 iOS 平台上，必须保证有音频在后台播放，本模块设置的锁屏界面才会显示**


#**set**<div id="1"></div>

设置锁屏音乐播放页面

set({params}, callback(ret, err))

##params

totalTime:

- 类型： 数字
- 描述： 播放的音频的总时长

progress:

- 类型： 数字
- 描述： 音频播放位置，当前播放位置占整个音频长度的百分比

cover:

- 类型： 字符串
- 描述：（可选项）专辑图片路径，要求本地路径（fs://、widget://）

defaultCover:

- 类型： 字符串
- 描述：（可选项）默认专辑图片路径，要求本地路径（fs://、widget://）

volume：

- 类型： 数字
- 描述：（可选项）音量大小，取值范围：0-100
- 默认值：当前系统音量

audio:

- 类型： 字符串
- 描述： （可选项）音频名称
- 默认值：未知

author:

- 类型： 字符串
- 描述：（可选项）音频作者名称
- 默认值：未知

lyrics:

- 类型： JSON 对象
- 描述：（可选项）显示歌词设置
- 内部字段：

```js
{
	path: 'widget://res/firework.lrc', //（可选项）字符串类型；歌词文件路径，要求本地文件（fs://、widget://），不传则不显示歌词
	size: 14,                          //（可选项）数字类型；歌词字体大小；默认：14
	color: '#fff'                      //（可选项）字符串类型；歌词颜色，支持#，rgb，rgba；默认："#fff"
}
```

fixedOn:

- 类型： 字符串
- 描述：本模块所依附的 window 或 frame 的名字，在 iOS 平台上，该 window 或 frame 必须始终在可视区域的最上层，否则锁屏效果将会失效
- 默认值：当前主 window

##callBack(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：
  
```js
{
	eventType: 'play',     //字符串类型；交互事件类型，取值范围如下：
							//play(播放)
							//pause（暂停）                            
							//next（下一首）
							//previous（上一首）
}
```
 
##示例代码

```js
var audioCover = api.require('audioCover');
audioCover.set({
    audio: '歌曲名',
    author: '作者'
}, function(ret, err){		
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

#**update**<div id="2"></div>

更新锁屏播放界面播放进度条

update({params})

##params

progress:

- 类型： 数字
- 描述： 音频播放位置，当前播放位置占整个音频长度的百分比

##示例代码

```js
var audioCover = api.require('audioCover');
audioCover.update({
    progress : 60
}); 
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**cancel**<div id="3"></div>

取消锁屏音乐播放页面

cancel(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status: true  //布尔类型；
}
```
##示例代码

```js
var audioCover = api.require('audioCover');
audioCover.cancel(function( ret, err ){		
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
