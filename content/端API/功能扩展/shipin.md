/*
Title: shipin
Description: shipin
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">方法</a></li>
</ul>
<div id="method-content">

<div class="outline">

[play](#play)
[stop](#stop)

</div>

# 概述 #

本模块是一款实现手机自定义大小和位置的简单视频模块。有
视频的打开和关闭的相关接口

## play(params)<div id="play"></div>
初始并打开播放器

## params ##
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

### 示例代码 ###

```js
var shipin = api.require("shipin");
var param = {
	url:"/sdcard/hd.mp4,http://forum.ea3w.com/coll_ea3w/attach/2008_10/12237832415.3gp,http://pm.803.com.cn/mp4.mp4",
	x:0,
	y:0,
	w:300,
	h:500
};
shipin.play(param);
```

### 补充说明 ###
初始并打开播放器


### 可用性 ###

Android 系统

可提供的 1.0.0 及更高版本


## stop() <div id="stop"></div>
停止并销毁播放器

### 示例代码 ###

```js
var shipin = api.require("shipin");
    
shipin.Stop();
```

### 可用性 ###

Android系统

可提供的 1.0.0 及更高版本