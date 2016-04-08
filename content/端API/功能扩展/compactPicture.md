/*
Title: compactPicture
Description: compactPicture
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">
<div class="outline">
[HittingPic](#a1)
</div>


#**概述**

compactPicture为批量压缩图片，用户可自己控制压缩图片的质量参数，此模块为等比例压缩图片。
使用之前确保用户手机内存存在且充足


#**HittingPic**<div id="a1"></div>

按用户定义尺寸批量等比例处理图片

HittingPic(params, callback(ret))

##params

picpatharray：

- 类型：数组
- 描述：开发者需要处理的图片地址组成的数组 ，要求本地路径（widget://、fs://）

size：

- 类型：整形
- 描述：图片压缩的质量 ,参数范围 1 － 10 , 例如当传递为5时，则会将图片压缩至原质量的百分之50，尺寸不变，个人建议为4或者5.

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	states:["pic1","pic2","pic3",....]       //数组类型；处理好的图片的地址（绝对路径）组成的数组
}
```

##示例代码

```js
var hittingpic = api.require('compactPicture');
var paramshare1 = {
	picpatharray : "需要处理的图片地址数组",
	size:10
};
hittingpic.HittingPic(paramshare1, function(ret) {
	alert(JSON.stringify(ret));
});
```

##补充说明

批量处理图片，如有好的建议也可发送建议到zd_9022952@163.com

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
