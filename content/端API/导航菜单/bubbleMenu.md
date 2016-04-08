/*
Title: bubbleMenu
Description: bubbleMenu
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[hidden](#2)

[show](#3)

[close](#4)
</div>

#**概述**

bubbleMenu是一个原生实现的气泡按钮菜单，开发者可自定义气泡弹出位置大小以及按钮的各种样式和个数

![图片说明](/img/docImage/bubbleMenu.jpg)

#**open**<div id="1"></div>

打开菜单

open({params}, callback(ret, err))

##params

<del>bgColor：</del>

- <del>类型：字符串</del>
- <del>默认值：#000000</del>
- <del>描述：菜单背景色</del>

<del>lightColor：</del>

- <del>类型：字符串</del>
- <del>默认值：#009ACD</del>
- <del>描述：菜单按钮点击色</del>

<del>borderColor：</del>

- <del>类型：字符串</del>
- <del>默认值：#000000</del>
- <del>描述：菜单边框色</del>

<del>cutLineColor</del>

- <del>类型：字符串</del>
- <del>默认值：#636363</del>
- <del>描述：按钮间分割线颜色</del>

style：

- 类型：json对象
- 默认值：见内部字段
- 描述：气泡样式设置，可为空

 内部字段:
```js
{
     bgColor:   //菜单按钮背景色，支持rgb,rgba,#,默认#000000，可为空
     lightColor:  //菜单按钮点击色，支持rgb,rgba,#,默认#009ACD，可为空
     borderColor:// 菜单边框色，支持rgb,rgba,#,默认#000000，可为空 
     cutLineColor:// 菜单按钮分割线色，支持rgb,rgba,#,默认#636363，可为空
     titleColor:   //菜单按钮标题色，支持rgb,rgba,#,默认#ffffff，可为空
 }
 ```

centerX：

- 类型：数字
- 默认值：120
- 描述：气泡菜单箭头点的坐标，可为空

centerY：

- 类型：数字
- 默认值：120
- 描述：气泡菜单箭头点的坐标，可为空

btnArray:

- 类型：数组
- 默认值：无
- 描述：按钮的信息组成的数组，不可为空

内部字段：

```js
[{
	icon:				//按钮的图片地址，字符串，可与标题配合使用，可为空
	title:				//按钮的标题，字符串，与图片配合使用
	length:				//按钮的长度，数字类型，默认65
}]
```

fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	index：		//用户点击按钮的下标
}
```

##示例代码

```js
var bubbleMenu = api.require('bubbleMenu');
bubbleMenu.open({
	centerX: api.frameWidth / 2,
	centerY: api.frameHeight / 2,
	btnArray: [{
		title: '按钮'
	},{
		title: '按钮'
	},{
		title: '按钮'
	}],
    fixedOn: api.frameName
},function( ret, err ){		
	if( ret ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```

##补充说明

打开菜单

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**<del>hidden</del>**<div id="2"></div>

<del>隐藏菜单</del>

<del>hidden()</del>

##<del>示例代码</del>

```js
var bubbleMenu = api.require('bubbleMenu');
bubbleMenu.hidden();
```

##<del>补充说明</del>

<del>隐藏菜单，只是隐藏，还在内存里没有清除</del>

##<del>可用性</del>

<del>iOS系统，Android系统</del>

<del>可提供的1.0.0及更高版本</del>

#**hide**<div id="2"></div>

隐藏菜单

hide()

##示例代码

```js
var bubbleMenu = api.require('bubbleMenu');
bubbleMenu.hide();
```

##补充说明

隐藏菜单，只是隐藏，还在内存里没有清除

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

#**show**<div id="3"></div>

显示菜单

show()

##示例代码

```js
var bubbleMenu = api.require('bubbleMenu');
bubbleMenu.show();
```

##补充说明

显示菜单

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**close**<div id="4"></div>

关闭菜单

close()

##示例代码

```js
var bubbleMenu = api.require('bubbleMenu');
bubbleMenu.close();
```

##补充说明

关闭菜单，意味着从内存里清除

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
