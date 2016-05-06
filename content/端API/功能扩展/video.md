/*
Title: video
Description: 兼容所有安卓手机的视频模块，可自定义，支持mp4,rtsp,hls,等
*/
<div class="outline">
[addView](#a1)
</div>

#**概述**
兼容所有安卓手机的视频模块，可自定义，支持mp4,rtsp,hls,等
video 

**使用此模块之前建议先配置  [config.xml](/APICloud/技术专题/app-config-manual) 文件，配置完毕，需通过云端编译生效，配置方法如下：**

- 名称：video
- 配置示例:

```xml
  <feature name="video"></feature>
```

<div id="a1"></div>
#**addView**

视频直播

addView({params});

##params
x：

- 类型：数值型
- 描述：设置播放器距离左边的距离。

y：

- 类型：数值型
- 描述：设置播放器距离上边的距离

w：

- 类型：数值型
- 描述：设置播放器的宽度(值为0时表示最大宽度)

h：

- 类型：数值型
- 描述：设置播放器的高度(值为0时表示最大高度)

url：

- 类型：字符串
- 描述：设置视频播放地址，支持mp4、rtsp、hls等格式

##示例代码

```js

apiready = function(){
	var uzvideo = api.require('video');
	var param = {x:0,y:60,w:0,h:200,url:'rtsp://218.204.223.237:554/live/1/66251FC11353191F/e7ooqwcfbqjoo80j.sdp'};
	uzvideo.addView(param);
}
```

##可用性

Android系统

可提供的1.0.0及更高版本
