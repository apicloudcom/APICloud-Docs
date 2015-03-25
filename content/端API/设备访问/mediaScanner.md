/*
Title: mediaScanner
Description: mediaScanner
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>
<div id="method-content">


<div class="outline">
[open](#a1)

[scann](#a2)

</div>

#**概述**

mediaScanner是一个多媒体扫描器，通过调用其相关接口可扫描系统相册内存放的图片、视频等多媒体资源，也可直接打开可自定义的模板多选界面

#**open**<div id="a1"></div>

打开系统相册资源选择器

open({params}, callback(ret, err))

##params

bgColor：

- 类型：字符串
- 默认值：#FFFFFF
- 描述：背景色，支持rgb，rgba，#，imgPath，可为空

row：

- 类型：数字
- 默认值：4
- 描述：图片显示的列数，可为空

mark：

- 类型：json对象
- 默认值：见内部字段
- 描述：选中标记图标配置，可为空

内部字段：

```js
{
	icon:  		//标记的图标，字符串，支持rgb，rgba，#，imgPath，默认#696969，可为空
	position：	//标记的位置，取值范围见标记位置，默认left_down,可为空
	size:  		//标记的大小，数字类型，默认图片宽度的三分之一
}
```

navigation：

- 类型：json对象
- 默认值：见内部字段
- 描述：导航栏设置，可为空

内部字段：

```js
{
	bg:  		//背景配置,字符串,支持rgb,rgba,#,img，默认rgba(0.5,0.5,0.5,0.8)，可为空
	state：		//状态文字配置，json对象，可为空
	内部字段：
	{
		title:   //字符串类型, 默认已选择*项，可为空
		color：  //字符串，字体颜色，默认蓝色，可为空，支持rgb，rgba，#
		size：   //数字类型，字体大小，默认18，可为空
	}
	cancel: 	 //取消按钮配置，json对象，可为空
	内部字段：
	{
		title:       //字符串类型, 默认取消，可为空
		titleColor： //字符串，字体颜色，默认蓝色，可为空，支持rgb，rgba，#
		titleSize：  //数字类型，字体大小，默认18，可为空
		bg:          //字符串,默认rgba(0,0,0,0)，可为空，支持rgb，rgba，#，img
    }
	finish: 		//完成按钮配置，json对象，可为空
	内部字段：
	{
        title:       //字符串类型, 默认完成，可为空
		titleColor： //字符串，字体颜色，默认蓝色，可为空，支持rgb，rgba，#
		titleSize：     //数字类型，字体大小，默认18，可为空
		bg:          //字符串,默认rgba(0,0,0,0)，可为空，支持rgb，rgba，#，img
	}
}
```

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	list:        //获取选中的媒体资源信息组成的数组
	内部字段:
	[{
		url:        //资源路径
		thumbUrl:  	//缩略图路径
		mimeType: 	// 资源类型
		size： 		//资源大小
   }]
}
```

##示例代码

```js
var obj = api.require('mediaScanner');
obj.open ( function(ret, err){
	api.alert({msg:ret.list});
});
```

##补充说明

打开相册资源多选器

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**scann**<div id="a2"></div>

获取系统相册所有媒体资源

scann(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	list:        	//系统相册中所有媒体资源的路径组成的数组
	内部字段[{
	url:        	//资源路径
	thumbUrl:  		//缩略图路径
	mimeType: 		//资源类型
    size：			//资源大小
   }]
}
```

##示例代码

```ja
var obj = api.require('mediaScanner');
obj.scann( function(ret, err){
	api.alert({msg:ret.list});
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


</div>

<div id="const-content">

#**标记位置**

图片选中后标记的位置。字符串类型

##取值范围：

- left_up		//左上角
- left_down		//左下角
- right_up		//右上角
- right_down	//右下角



