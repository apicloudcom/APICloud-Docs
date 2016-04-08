/*
Title: qCloudVODPlayer
Description: qCloudVODPlayer
*/
<div class="outline">
[playInNewWin](#a1)
[playInCurWin](#a2)
</div>

#**概述**

qCloudVODPlayer封装了腾讯云点播(VOD) android 端播放器SDK。可用于播放腾讯云视频，兼容防盗链，黑白名单，使用本模块后，用户无需考虑腾讯云后台是否开启了防盗链，是否设置了黑白名单。用户只需向本模块接口提供视频的播放链接即可播放视屏。集成与接口调用十分简单。
    
<div id="a1"></div>
#**playInNewWin**

打开新窗口全屏播放视频

playInNewWin({params})

##params

videoUrl：

- 类型：string字符串
- 描述：视频链接。必传。视频链接可通过腾讯云后台查看，查看腾讯云视频链接步骤【视频管理-点击某个视频-视频发布-显示源地址】。或者可调用腾讯云相关API查询。由于腾讯云只支持转码为MP4与HLS格式，此处调用请尽量使用这两种格式。

##示例代码

```js
var qCloudVODPlayer = api.require('qCloudVODPlayer');
var param = {
	videoUrl : "http://200000365.vod.myqcloud.com/200000365_b0986b3c984e11e598b435610f6d541b.f20.mp4"
};
qCloudVODPlayer.playInNewWin(param);
```

##可用性

Android系统 IOS系统

可提供的1.0.0及更高版本

<div id="a2"></div>
#**playInCurWin**

指定播放器的位置和大小，播放视频

playInCurWin({params})

##params
x：

- 类型：integer,数字
- 描述：播放器在x轴上的放置位置，从屏幕左上角为计为0开始

y：

- 类型：integer,数字
- 描述：播放器在y轴上的放置位置，从屏幕左上角为计为0开始

w：

- 类型：integer,数字
- 描述：播放器宽度

h：

- 类型：integer,数字
- 描述：播放器高度

videoUrl：

- 类型：string字符串
- 描述：视频链接。必传。视频链接可通过腾讯云后台查看，查看腾讯云视频链接步骤【视频管理-点击某个视频-视频发布-显示源地址】。或者可调用腾讯云相关API查询。由于腾讯云只支持转码为MP4与HLS格式，此处调用请尽量使用这两种格式。

##示例代码

```js
var qCloudVODPlayer = api.require('qCloudVODPlayer');
var param = {
	x : 30,
	y : 50,
	w : 300,
	h : 180,
	videoUrl : "http://200000365.vod.myqcloud.com/200000365_b0986b3c984e11e598b435610f6d541b.f20.mp4"
};
qCloudVODPlayer.playInCurWin(param);
```

##可用性

Android系统 IOS系统

可提供的1.0.0及更高版本