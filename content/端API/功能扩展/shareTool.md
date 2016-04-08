/*
Title: shareTool
Description: shareTool
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[shareText](#a1)

[sharePicture](#a2)
</div>

#**概述**

shareTool封装了android的原生分享功能，使用此模块可轻松实现对文字和图片分享的功能。暂仅支持Android。


#**shareText**<div id="a1"></div>

分享文本

shareText({params}, callback(ret, err))

##params

title：

- 类型：字符串
- 默认值：无
- 描述：不能为空，分享的弹出的窗口标题

text：

- 类型：字符串
- 默认值：无
- 描述：不能为空，分享的文本


##示例代码

```js
var shareTool = api.require('shareTool');
shareTool.shareText({
    text: '这个游戏真好玩！',
    title: '我爱分享'
});
```

##补充说明

无

##可用性

Android系统

可提供的1.0.0及更高版本

#**sharePicture**<div id="a2"></div>

分享图片


sharePicture({params}, callback(ret, err))

##params

title：

- 类型：字符串
- 默认值：无
- 描述：不能为空，分享的弹出的窗口标题

url：

- 类型：字符串
- 默认值：无
- 描述：不能为空，图片保存地址url(可为imageTool返回的图片路径)


##示例代码

```js
var shareTool = api.require('shareTool');
shareTool.sharePicture({
    url: 'widget://.png',
    title: '分享'
});
```

##补充说明

无

##可用性

Android系统

可提供的1.0.0及更高版本


