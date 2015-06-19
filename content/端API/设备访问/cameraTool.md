/*
Title: cameraTool
Description: cameraTool
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">
<div class="outline">
[openCamera](#a1)
</div>

#**概述**

cameraTool封装了android的系统相机，使用此模块可轻松实现拍照后获取照片路径的功能


#**openCamera**<div id="a1"></div>

打开系统相机并返回图片路径


openCamera(callback(ret, err))



##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	
	imgPath:                //图片路径
}
```


##示例代码

```js
var cameraTool = api.require('cameraTool');


cameraTool.openCamera(function(ret, err){api.prompt({title:"信息",msg:"图片路径："+ret.imgPath,buttons:["取消","确定"]});});
```

##补充说明

无

##可用性

Android系统

可提供的1.0.0及更高版本


