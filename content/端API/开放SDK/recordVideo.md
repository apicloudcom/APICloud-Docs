/*
Title: recordVideo
Description: recordVideo
*/
<div class="outline">
[initrecordSDK](#a1)
[startRecordTV](#a2)
</div>

#**概述**

recordVideo封装了vcameraSDK，使用此模块可实现录制视频并添加特效功能。
VCamera(短视频拍摄)提供视频录制、后滤镜、炫酷 MV 主题。
由于使用安卓控件原因，支持Android4.0及以上的所有系统，不支持低版本。
个人版本会有爱拍水印，模版和滤镜固定。本模块暂仅支持安卓。


#**initrecordSDK**<div id="a1"></div>

注册SDK

initrecordSDK(callback(ret))

##callback(ret)

ret：

- 类型：JSON对象

内部字段：

```js
{
	success:1           //操作成功状态值
}
```


##示例代码

```js
var aipai = null;
apiready = function() {
	aipai = api.require('recordVideo');
}
function initsdk(){
	aipai.initrecordSDK(function(ret){
		alert(JSON.stringify(ret));
	});
}
```

##补充说明

初始化SDK 建议在apiready方法中初始化


#**startRecordTV**<div id="a1"></div>

开始录制

startRecordTV(callback(ret))

##callback(ret)

ret：

- 类型：JSON对象

内部字段：

```js
{
	code:1           //操作成功状态值1 , 操作失败状态值 2
	videoaddress:"" // 保存到内存卡的视频地址 如果操作失败则为"no"
}
```


##示例代码

```js
function record(){
	aipai.startRecordTV(function(ret){
		alert(JSON.stringify(ret));
	});
}
```

##补充说明

开始录制视频并处理

##可用性

Android系统

可提供的1.0.0及更高版本

