/*
Title: marketScore
Description: marketScore
*/

<p style="color: #ccc;margin-bottom: 30px;">来自于：开发者</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">方法</a></li>
</ul>
<div id="method-content">

<div class="outline">

[myScore](#myScore)

</div>

#**概述**

marketScore 是在已安装的应用市场中，打开指定 app 对应的页面，提示用户评分的功能实现。是提高 app 排名的利器。用法包括但不限于：在适当页面放5星好评支持我们的按钮、用户第 N 次打开 app 的时候直接跳出，提示用户评分。现在主流的 app 基本都有这个功能。

#**myScore**<div id="myScore"></div>

打开市场

myScore({params})

##params

appname：

- 类型：字符串
- 默认值：无
- 描述：被评分的 app 的包名，不能为空

##示例代码

```js
if ( api.systemType =="android' ){
	var smarket = api.require('marketScore');
	smarket.myScore({
        appname:'com.tencent.mm'
    });
}else{
	api.openApp({
		iosUrl: 'https://itunes.apple.com/cn/app/wei-xin/id414478124?mt=8'
	});
}
```

##补充说明

iOS不需要使用模块，直接打开app对应的地址就可以

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本