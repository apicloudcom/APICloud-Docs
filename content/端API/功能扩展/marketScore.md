/*
Title: marketScore
Description: marketScore
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">方法</a></li>
</ul>
<div id="method-content">

<div class="outline">

[myScore](#myScore)

</div>

#**概述**

marketScore是调用已安装市场，进行app评分的功能实现

#**myScore**<div id="myScore"></div>

打开市场

myScore({params})

##params

appname：

- 类型：字符串
- 默认值：无
- 描述：被评分的app的包名，不能为空

##示例代码

```js
if (api.systemType =="android"){
	smarket = api.require('marketScore');
	var param = {appname:"com.tencent.mm"};
	smarket.myScore(param);
}else{
	api.openApp({
		iosUrl: 'https://itunes.apple.com/cn/app/wei-xin/id414478124?mt=8'
	},function(ret,err){
	});
}
```

##补充说明

iOS不需要使用模块，直接打开app对应的地址就可以

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本