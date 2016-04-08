/*
Title: shareMorePic
Description: shareMorePic
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">
<div class="outline">
[shareMPT](#a1)
</div>

#**概述**

shareMorePic为原生自定义微信分享，可分享多图加文字到微信朋友圈。本模块暂仅支持Android。


#**shareMPT**<div id="a1"></div>

发表内容

shareMPT({params}, callback(ret))

##params

sharepic：

- 类型：数组
- 描述：为需要分享图片地址的数组 

sharetext：

- 类型：字符串
- 描述：需要分享的文字内容 ， 不能特别长

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	state:1		//启动微信成功，不是分享成功，请注意
}
```

##示例代码

```js
var sharemorePic = api.require('shareMorePic');
var mycars = new Array();
mycars.push(picaddressshare);
mycars.push(picaddressshare);
mycars.push(picaddressshare);
var paramshare = {
	sharepic : mycars,
	sharetext : "分享图片"
};
sharemorePic.shareMPT(paramshare, function(ret) {
	alert(JSON.stringify(ret));
});
```

##补充说明

picaddressshare为变量，建议不要传特别大的图片，否则启动微信会有一些延迟，如有别的需要发邮件到zd_9022952@163.com，反馈如果能做我会更新模块。
最少一张图片最多9张，多传了也不会有9张以上。

由于是原生开发，微信没有分享9张图片的SDK，所以限制要多一些，使用者传递图片参数必须是内存卡路径，不支持相对路径fs:// widget://等，如果图片传递错误会导致分享失败。分享完成之后，
没有办法返回自己的app，这也是原生的和官方的差异。

##可用性

Android系统

可提供的1.0.0及更高版本

