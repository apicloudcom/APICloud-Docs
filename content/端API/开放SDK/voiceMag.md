/*
Title: voiceMag
Description: voiceMag
*/

<p style="color: #ccc;margin-bottom: 30px;">来自于：开发者</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[onCall](#a1)

[onNormal](#a2)

[startPlay](#a3)

[stopPlay](#a4)

</div>

#**概述**

voiceMag是用来控制手机的声音在听筒播放还是在扩音器播放；由于IOS版本的用apicloud的startPlay播放时，不能进行控制，所以将startPlay和stopPlay一并来封装了。使用时，将api.startPlay和api.stopPlay改为voiceMag.startPlay和voiceMag.stopPlay即可。
使用场景：类似微信播放语音时靠近听筒时使用听筒播放，远离时使用扩音器播放。下面有相应的例子。


#**onCall**<div id="a1"></div>

使声音在听筒播放

onCall()


##示例代码

```js
var voiceMag = api.require('voiceMag');
voiceMag.onCall();//改为听筒播放
```

##补充说明


##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**onNormal**<div id="a2"></div>

正常播放声音

onNormal()

##示例代码

```js
var voiceMag = api.require('voiceMag');
voiceMag.onCall();//改为听筒播放
```

##补充说明

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**startPlay**<div id="a3"></div>

播放音频文件

startPlay(function(ret,err))

播放错误时会提醒

##示例代码

```js
var voiceMag = api.require('voiceMag');
voiceMag.startPlay({path:"fs://test.mp3"}); //播放语音
```

##补充说明

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**stopPlay**<div id="a4"></div>

停止播放

stopPlay()

##示例代码

```js
var voiceMag = api.require('voiceMag');
voiceMag.stopPlay();
```

##补充说明

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
