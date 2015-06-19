/*
Title: epubReader
Description: epubReader
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[setValue](#2)

[getChapters](#3)

[openChapter](#4)

[getBrightness](#5)

[setBrightness](#6)

[show](#7)

[hide](#8)

[close](#9)
</div>


#**概述**

使用本模块可以实现epub电子书阅读器

#**open**<div id="1"></div>

打开阅读器

open({params}, callback(ret, err))

##params

path：

- 类型：字符串
- 默认值：无
- 描述：epub文件路径，支持widget://、fs://、cache://等协议

currentPage：

- 类型：数字
- 默认值：1
- 描述：（可选项）阅读器打开时显示的页码

bg：

- 类型：字符串	
- 默认值：#fff
- 描述：（可选项）阅读器的背景色，支持颜色（rgb，rgba，#）和图片（widget://、fs://、cache://等协议）

textColor：

- 类型：字符串
- 默认值：#000
- 描述：（可选项）文字颜色

textSize：

- 类型：数字
- 默认值：12
- 描述：（可选项）文字字体大小

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	eventType:		//事件类型，字符串，取值范围见事件类型，根据不同的事件来更新页面元素
	currentPage:		//当事件类型为翻页或分页时的当前页码
	totalPage:		//当事件类型为分页时返回，分页过程中该值会不断变化
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg：		//错误描述
}
```

##示例代码

```js
var obj = api.require('epubReader');
obj.open({
   path : "fs://test.epub"
},function(ret, err){
   if(ret){
        api.alert({msg:ret.eventType+ret.progress});
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**setValue**<div id="2"></div>

设置阅读器的参数

setValue({params})

##params

bg：

- 类型：字符串	
- 默认值：当前背景色
- 描述：（可选项）阅读器的背景色，支持颜色（rgb，rgba，#）和图片（widget://、fs://、cache://等协议）

textColor：

- 类型：字符串
- 默认值：当前文字颜色
- 描述：（可选项）文字颜色

textSize：

- 类型：数字
- 默认值：当前字体大小
- 描述：（可选项）文字字体大小。重新设置字体大小后，会重新分页，触发分页的事件

##示例代码

```js
var obj= api.require('epubReader');
obj.setValue({
	bg:"#000",
	textColor:"#fff",
	textSize:15
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**getChapter**<div id="3"></div>

获取章节列表

getChapters(callBack(ret,err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	chapters:[{			//JSON对象数组
		title:''		//章节标题，字符串类型
	}]
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:				//错误描述，字符串类型
}
```

##示例代码

```js
var obj = api.require('epubReader');
obj.getChapters(
	function(ret,err){
		if (ret){
			var chapters = ret.chapters;
		}else{
			var msg = err.msg;
		}
	}
);
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**openChapter**<div id="4"></div>

打开指定章节

openChapter({params}, callback(ret, err))

##params

index：

- 类型：数字
- 默认值：无
- 描述：章节索引，从0开始

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	currentPage:		//当前页码
	totalPage:		//总页数
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg：		//错误描述
}
```

##示例代码

```js
var obj = api.require('epubReader');
obj.openChapter({
	index:2
},function(ret, err){
	if(ret){
        var currentPage = ret.currentPage;
        var totalPage = ret.totalPage;
	}
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**getBrightness**<div id="5"></div>

获取屏幕亮度

getBrightness(callBack(ret,err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	brightness:           //返回的当前屏幕亮度，取值范围0-100，数字类型
}
```

err：

- 类型：JSON对象

内部字段：

```
{
	msg:''			//错误描述,字符串
}
```

##示例代码

```js
var obj = api.require('epubReader');
obj.getBrightness(
	function(ret, err){
		if (ret){
			var brightness = ret.brightness;
		}else{
			var msg = err.msg;
		}
	}
);
```

##补充说明

在android平台上，若当前设备屏幕亮度为自动调节，则此接口获取的是非自动调节时的亮度

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本


#**setBrightness**<div id="6"></div>

设置屏幕亮度

setBrightness({params})

##params

brightness：

- 类型：数字
- 默认值：无
- 描述：屏幕亮度，取值范围0-100

##示例代码

```js
var obj = api.require('epubReader');
obj.setBrightness();
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本


#**show**<div id="7"></div>

显示阅读器

show()

##示例代码

```js
var obj= api.require('epubReader');
obj.show();
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**hide**<div id="8"></div>

隐藏阅读器

hide()

##callback(ret, err)

##示例代码

```js
var obj= api.require('epubReader');
obj.hide();
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**close**<div id="9"></div>

关闭阅读器

close()

##示例代码

```js
var obj = api.require('epubReader');
obj.close();
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

</div>


<div id="const-content">

#**事件类型**

事件类型，字符串类型

##取值范围

```js
paginate		//分页
click			//点击
page_up			//向上翻页
page_down		//向下翻页
page_over		//在最后一页时的下翻页事件
page_begin		//在第一页时的上翻页事件
```