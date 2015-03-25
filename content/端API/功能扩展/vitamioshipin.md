/*
Title: vitamioshipin
Description: vitamioshipin
*/
<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">方法</a></li>
</ul>
<div id="method-content">

<div class="outline">

[init](#init)

[initPlayer](#initPlayer)

[setSpeed](#setSpeed)

[setVolume](#setVolume)

[seekTo](#seekTo)

[playNext](#playNext)

[playPre](#playPre)

[pause](#pause)

[play](#play)

[stop](#stop)

[stopPlay](#stopPlay)

[getDuration](#getDuration)

[getCurrentPosition](#getCurrentPosition)

[setFullScreen](#setFullScreen)

</div>

#**概述**

本模块是一款多功能播放器，可以播放本地和网络视频，并可以自定义屏幕位置和大小，同时可以控制播放，声音,速度等。

#**init**<div id="init"></div>

初次化操作,只使用一次,建议放在应用程序入口

##示例代码

```js
var uzmoduledemo = null;
apiready = function(){
    uzmoduledemo = api.require('vitamioshipin');
    uzmoduledemo.Init();
}
```

##补充说明

建议放在应用程序入口

##可用性

android系统

可提供的1.0.0及更高版本


#**initPlayer**<div id="initPlayer"></div>

初始并打开播放器

initPlayer ({params})

##params

url：

- 类型：字符串
- 默认值：无
- 描述：视频的路径可以为本地或者网络路径

x：

- 类型：字符串
- 默认值：0
- 描述：x坐标

y：

- 类型：字符串
- 默认值：0
- 描述：Y坐标

w：

- 类型：字符串
- 默认值：0
- 描述：组件宽带

h：

- 类型：字符串
- 默认值：0
- 描述：组件高度

logoColor：

- 类型：字符串 
- 默认值：#fffff
- 描述：logo的颜色

logoPos：

- 类型：字符串 
- 默认值：“TOP_LEFT”
- 描述：logo位置,取4个值"TOP_LEFT","TOP_RIGHT","BUTTOM_LEFT","BUTTOM_RIGHT"

qualtity：

- 类型：字符串 
- 默认值：HIGH
- 描述：视频的质量,取三个值LOW,MEDIUM,HIGH

logoSize：

- 类型：字符串 
- 默认值：20
- 描述：logo的字体大小

logoText：

- 类型：字符串 
- 默认值：“”
- 描述：要显示的log

defaultController：

- 类型：boolean
- 默认值：false
- 描述：是否显示默认的播放控制器,控制器上有进度条,时间等信息

autoPlayNext：

- 类型：boolean 
- 默认值：false
- 描述：当前视频播放完后,是否自动播放下一首,当到最后一首时,又回到第一首播放


##示例代码

```js
var param = {
	url:"/sdcard/hd.mp4,http://forum.ea3w.com/coll_ea3w/attach/2008_10/12237832415.3gp,http://pm.803.com.cn/mp4.mp4",
	x:0,
	y:0,
	w:300,
	h:500,
	logoColor:”#000000”,
	logoPos:”TOP_LEFT”,
	qualtity:”HIGH”,
	logoSize:20,
	logoText:”logo”,
	defaultController : true,
	autoPlayNext : true
};
uzmoduledemo.initPlayer(param);
```

##补充说明

初始并打开播放器

##可用性

android系统

可提供的1.0.0及更高版本


#**setSpeed**<div id="setSpeed"></div>

设置播放速度,取值 在0.5-2.0之间

SetSpeed({params})

##params

speed：

- 类型：float
- 默认值：1.0
- 描述：设置的播放速度


##示例代码

```js
var param = {
    speed:2.0
};
uzmoduledemo.setSpeed(param);
```

##补充说明

无

##可用性

android系统

可提供的1.0.0及更高版本


#**setVolume**<div id="setVolume"></div>

设置音量,取值 在0-100之间

setVolume({params})

##params

volume：

- 类型：float
- 默认值：100
- 描述：设置音量取值0-100

##示例代码

```js
var param = {
	volume:50
};
uzmoduledemo.setVolume(param);
```

##补充说明

无

##可用性

android系统

可提供的1.0.0及更高版本


#**seekTo**<div id="seekTo"></div>

设置播放位置

seekTo({params})

##params

msec：

- 类型：int
- 默认值：0
- 描述：设置播放位置

##示例代码

    var param = {
    		msec:5000
    };
    uzmoduledemo.seekTo(param);

##补充说明
无

##可用性

android系统

可提供的1.0.0及更高版本


#**playNext**<div id="playNext"></div>

播放下一首

##示例代码
    
    uzmoduledemo.playNext();

##补充说明

无

##可用性

android系统

可提供的1.0.0及更高版本


#**playPre**<div id="playPre"></div>

播放上一首

##示例代码
    
    uzmoduledemo.playPre();

##补充说明

无

##可用性

android系统

可提供的1.0.0及更高版本

#**pause**<div id="pause"></div>

暂停

##示例代码
    
    uzmoduledemo.pause();

##补充说明

暂停

##可用性

android系统

可提供的1.0.0及更高版本

#**play**<div id="play"></div>

播放

##示例代码
    
    uzmoduledemo.play();

##补充说明

无

##可用性

android系统

可提供的1.0.0及更高版本


#**stop**<div id="stop"></div>

停止

##示例代码
    
    uzmoduledemo.stop();

##补充说明

无

##可用性

android系统

可提供的1.0.0及更高版本

#**stopPlay**<div id="stopPlay"></div>

停止并销毁播放器

##示例代码
    
    uzmoduledemo.stopPlay();

##补充说明

无

##可用性

android系统

可提供的1.0.0及更高版本

#**getDuration**<div id="getDuration"></div>

获得当前总时间

getDuration(callback(ret, err))

##示例代码
    
    var resultCallback = function(ret, err){
		alert(“当前总时间为”+ret);
    }
    uzmoduledemo.getDuration(resultCallback);

##补充说明

无

##可用性

android系统

可提供的1.0.0及更高版本

#**getCurrentPosition**<div id="getCurrentPosition"></div>

获得当前总时间

getCurrentPosition(callback(ret, err))

##示例代码
    
    var resultCallback = function(ret, err){
      alert(“当前播放的时间为”+ret);
    }
    uzmoduledemo.getCurrentPosition(resultCallback);

##补充说明

无

##可用性

android系统

可提供的1.0.0及更高版本


#**setFullScreen**<div id="setFullScreen"></div>

全屏

setFullScreen()

##示例代码
    
    uzmoduledemo.setFullScreen();

##补充说明

无

##可用性

android系统

可提供的1.0.0及更高版本