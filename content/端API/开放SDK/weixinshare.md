/*
Title: weixinshare
Description: weixinshare
*/
<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">方法</a></li>
</ul>
<div id="method-content">

<div class="outline">

[share](#share)

</div>
# 概述 #

本模块是一款打开微信分享功能模块,可分享文字和多张图片。

## share(params) <div id="share"></div>
打开微信分享功能

## params ##
shareImages：

- 类型：字符串
- 默认值：无
- 描述：需要分享的网络图片路径或者本地sd路径

content：

- 类型：字符串
- 默认值：无
- 描述：分享微信的内容

shareTip：

- 类型：字符串
- 默认值：无
- 描述：在网络下载时，对话框的提示语言 


savePath：

- 类型：字符串
- 默认值：无
- 描述：下载路径 


### 示例代码 ###
 
```js
var weixinshare = api.require('weixinshare');
var params = {
    shareImages:'http://a.hiphotos.baidu.com/image/pic/item/5243fbf2b2119313684741d767380cd791238d55.jpg,http://h.hiphotos.baidu.com/image/pic/item/0d338744ebf81a4cee5a52aed52a6059252da669.jpg',
    content:document.getElementById("content").value,
    shareTip:'我是一个下载提示,下载中....',
    savePath:'/sdcard/download'
};
weixinshare.share(params);
```

### 补充说明 ###
打开微信分享功能


### 可用性 ###

Android系统

可提供的 1.0.0 及更高版本