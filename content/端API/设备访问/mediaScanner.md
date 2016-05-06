/*
Title: mediaScanner
Description: mediaScanner
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>
<div id="method-content">


<div class="outline">
[open](#a1)

[scan](#a2)

</div>

#**概述**

mediaScanner是一个多媒体扫描器，通过调用其相关接口可扫描系统相册内存放的图片、视频等多媒体资源，也可直接打开可自定义的模板多选界面。**UIMediaScanner 模块是 mediaScanner 模块的优化版，建议使用  [UIMediaScanner](http://docs.apicloud.com/端API/界面布局/UIMediaScanner) 模块，此模块已停止更新。**

#**open**<div id="a1"></div>

打开系统相册资源选择器

open({params}, callback(ret, err))

##params

bgColor：

- 类型：字符串
- 默认值：#FFFFFF
- 描述：（可选项）背景色，支持 rgb，rgba，#，imgPath

row：

- 类型：数字
- 默认值：4
- 描述：（可选项）图片显示的列数

mark：

- 类型：JSON 对象
- 默认值：见内部字段
- 描述：（可选项）选中标记图标配置
- 内部字段：

```js
{
	icon:  		//（可选项）标记的图标，字符串，支持 rgb，rgba，#，imgPath，默认#696969
	position:  	//（可选项）标记的位置，取值范围见标记位置，默认left_down
	size:  		//（可选项）标记的大小，数字类型，默认图片宽度的三分之一
}
```

navigation：

- 类型：JSON 对象
- 默认值：见内部字段
- 描述：（可选项）导航栏设置
- 内部字段：

```js
{
	bg:  		   //（可选项）背景配置,字符串,支持 rgb,rgba,#,img，默认rgba(0.5,0.5,0.5,0.8)
	state：		//（可选项）状态文字配置，json对象,默认值见内部字段
					内部字段：
					{
						title:       //（可选项）字符串类型, 默认已选择*项，可为空
						color：      //（可选项）字符串，字体颜色，默认蓝色，支持 rgb，rgba，#
						size：       //（可选项）数字类型，字体大小，默认18
					}
	cancel: 	  //（可选项）取消按钮配置，json对象,默认值见内部字段
					内部字段：
					{
						title:       //（可选项）字符串类型, 默认取消
						titleColor： //（可选项）字符串，字体颜色，默认蓝色，支持 rgb，rgba，#
						titleSize：  //（可选项）数字类型，字体大小，默认18
						bg:          //（可选项）字符串,默认rgba(0,0,0,0)，支持 rgb、rgba、#、img
				    }
	finish: 	 //完成按钮配置，json对象,默认值见内部字段
					内部字段：
					{
				        title:        //（可选项）字符串类型, 默认完成
						titleColor:   //（可选项）字符串，字体颜色，默认蓝色，支持 rgb，rgba，#
						titleSize:    //（可选项）数字类型，字体大小，默认18
						bg:           //（可选项）字符串,默认rgba(0,0,0,0)，支持 rgb，rgba，#，img
					}
}
```

scrollToBottom：

- 类型：json
- 默认值：见内部字段
- 描述：（可选项）打开媒体资源界面后间隔一段时间开始自动滚动到底部设置，android 平台上不支持此功能
- 内部字段：

```js
{
   intervalTime:       //（可选项）打开媒体资源界面后间隔的时间开始自动滚动到底部，单位秒（s），小于零的数表示不滚动到底部，默认-1
   anim:               //（可选项）滚动时是否添加动画，布尔类型，默认true
}
```

sort：

- 类型：json
- 默认值：见内部字段
- 描述：（可选项）图片排序设置
- 内部字段：

```js
{
   key:       //（可选项）排序key值，取值范围：size--按图片大小排序；time：按图片创建时间（时间戳）排序 默认time
   order:     //（可选项）排序方式，取值范围：ascending--升序（小->大）；descending--降序（大->小），默认ascending
}
```

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	list:         //获取选中的媒体资源信息组成的数组
					内部字段:
					[{
						url:          //资源路径
						thumbUrl:     //缩略图路径
						mimeType:     //资源类型
						size:         //资源大小
						time:         //资源创建时间，格式为：yyyy-MM-dd HH:mm:ss
				    }]
}
```

##示例代码

```js
var mediaScanner = api.require('mediaScanner');
mediaScanner.open(function( ret, err ){
    if( ret ){
         alert( JSON.stringify( ret ) );
    }else{
         alert( JSON.stringify( err ) );
    }
});
```

##补充说明

打开相册资源多选器

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**scan**<div id="a2"></div>

获取系统相册所有媒体资源

scan(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	list:     //系统相册中所有媒体资源的路径组成的数组
				内部字段[{
				url:        	//资源路径
				thumbUrl:  		//缩略图路径
				mimeType: 		//资源类型
			    size：			 //资源大小
				time:           //资源创建时间，格式为：yyyy-MM-dd HH:mm:ss
			   }]
}
```

##示例代码

```js
var mediaScanner = api.require('mediaScanner');
mediaScanner.scan( function(ret, err){
	api.alert({msg:ret.list});
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


<div id="const-content">

#**标记位置**

图片选中后标记的位置。字符串类型

##取值范围：

- left_up		   //左上角
- left_down		//左下角
- right_up		//右上角
- right_down	   //右下角



