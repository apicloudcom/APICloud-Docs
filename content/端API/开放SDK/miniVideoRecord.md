/*
Title: miniVideoRecord
Description: miniVideoRecord
*/

<p style="color: #ccc;margin-bottom: 30px;">来自于：开发者</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[init](#1)

[open](#2)
</div>

#**概述**

miniVideoRecord封装了秒拍的视频拍摄功能（去掉后期编辑功能，大大缩小编译后apk的大小），使用此模块可实现录制自定义时长的小视频，开发者可以自行设置最小和最大时长（最小1秒到最大5分钟），暂时仅支持Android系统（需Android4.0及以上系统版本）。

#**init**<div id="1"></div>

初始化SDK

init({params}, callback(ret, err))

##params

savePath：

- 类型：字符串
- 描述：视频存储路径，会建立在DIMC文件夹下。
- 默认值："/VCamera/"

timeMin：

- 类型：数字
- 描述：视频录制最小时间，单位：毫秒。
- 默认值：3000

timeMax：

- 类型：数字
- 描述：视频录制最大时间，单位：毫秒。
- 默认值：10000

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	success:1			 //数字类型，1为初始化成功，0为初始化失败
}
```

##示例代码

```js
var mvr = null;
apiready = function() {
    mvr = api.require('miniVideoRecord');
}
function initsdk(){
	mvr.init({
	    savePath:'/VCamera/',
		timeMin:3000,
		timeMax:10000
	},function(ret){
		if (ret.success == 1) {
        	alert('初始化 miniVideoRecord 成功');
	    } else {
        	alert('初始化 miniVideoRecord 失败');
  		}
	});
}

```

##补充说明

初始化SDK 建议在apiready方法中初始化

##可用性

Android系统

可提供的1.0.0及更高版本



#**open**<div id="2"></div>

打开录制窗口

open(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	success:		//数字类型，1为成功，0为失败
	path:			//字符串类型，保存到内存卡的视频地址 如果操作失败则为""
}
```

##示例代码

```js
mvr.open(function(ret){		
	if (ret.success == 1) {
    	alert('拍摄视频成功:' + ret.path);
    } else {
    	alert('拍摄取消');
		}
});
```

##可用性

Android系统

可提供的1.0.0及更高版本

