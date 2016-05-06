/*
Title: actionButton
Description: actionButton
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[close](#2)

[hide](#3)

[show](#4)
</div>

#**概述**

actionButton 是一个仿照新浪微博快捷菜单而定制的一个模块，使用该模块可弹出一个由多个按钮组成的菜单，点击按钮，菜单消失。此模块最大的特点是弹出和消失都有相应的动画，开发者可自定义按钮的样式和个数（超过单屏显示的可以左右拖动）。本模块已停止更新，建议使用优化升级版模块 [MNActionButton](http://docs.apicloud.com/端API/导航菜单/MNActionButton)

![图片说明](/img/docImage/actionButton.jpg)

#**open**<div id="1"></div>

打开弹动按钮菜单

open({params}, callback(ret, err))

##params

bg：

- 类型：字符串
- 默认值：无
- 描述：（可选项）背景遮罩层设置，支持 rgb，rgba，#，img
- 备注：若不传或传空则背景透明

size：

- 类型：数字
- 默认值：80
- 描述：（可选项）按钮大小设置

items：

- 类型：数组
- 默认值：无
- 描述：弹出的子菜单按钮的信息，该数组有多少个元素，则有多少个菜单按钮
- 内部字段：

```js
[{
    bgColor:       //按钮背景色值，deprecated
    image：		//图片路径，deprecated
    normal         //（可选项）按钮背景色设置，支持 rgb，rgba，#，img，默认#ff0000
    highlight：    //（可选项）按钮高亮背景设置，支持 rgb,rgba,#,默认和normal一样
	title：        //（可选项）标题，字符串类型，无默认值，可为空，为空则不显示
    titleSize :   // （可选项）标题字体的大小，默认15
	titleColor :  // （可选项）标题字体的颜色，支持 rgb，rgba，#，默认#000000 

}]
```

pageControl：

- 类型：JSON 对象
- 默认值：无
- 描述：（可选项）配置页面控制器的显示
- 备注：若不传则表示不显示页面控制器
- 内部字段：

```js
{
    activeColor:0,          //（可选项）当前页颜色值，默认为红色，支持 rgb,rgba,#
    inactiveColor:0,        //（可选项）非当前页颜色值，默认为灰色，支持 rgb,rgba,#
}
```

<del>topHeight：</del>

- <del>类型：数字</del>
- <del>默认值：屏幕的一半</del>
- <del>描述：上边一排按钮距离屏幕顶部的高度，可为空</del>

fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window

clickDisappear：

- 类型：布尔
- 默认值：true
- 描述：（可选项）点击子菜单按钮后是否关闭菜单

matrix：

- 类型：JSON 对象
- 默认值：见内部字段
- 描述：（可选项）菜单按钮布局配置
- 内部字段：

```js
{
   row:         //（可选项）每屏幕显示的按钮行数，数字类型，默认2
   column:      //（可选项）每屏幕显示的按钮列数，数字类型，默认3
   bottomMargin://（可选项）底排按钮下边缘距离模块视图底端高度占h的百分比,数字类型,默认40 	   取值范围 0 ~ 100

}
```

shake：

- 类型：布尔
- 默认值：true
- 描述：（可选项）打开时是否添加抖动动画

blowUp：

- 类型：布尔
- 默认值：true
- 描述：（可选项）点击按钮是否添加放大效果

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	index:       //点击子菜单返回其下标
}
```

##示例代码

```js
var actionButton = api.require('actionButton');
actionButton.open({
	items: [{
		bgColor: '#00CED1',
		title: '标题一'
	},{
		bgColor: '#00CED1',
		title: '标题三'
	}],
	topHeight: 20,
	pageControl: {
		activeColor: '#778899',
		inactiveColor: '#DDA0DD'
	},
    fixedOn: api.frameName
}, function(ret, err){		
	if( ret ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```

##补充说明

打开弹动菜单按钮

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**close**<div id="2"></div>

关闭菜单

close()

##示例代码

```js
var actionButton = api.require('actionButton');
actionButton.close();
```

##补充说明

关闭菜单

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**hide**<div id="3"></div>

隐藏菜单

hide()

##示例代码

```js
var actionButton = api.require('actionButton');
actionButton.hide();
```

##补充说明

隐藏菜单，并没有从内存里清除

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**show**<div id="3"></div>

显示已隐藏的菜单

show()

##示例代码

```js
var actionButton = api.require('actionButton');
actionButton.show();
```

##补充说明

显示已隐藏的菜单

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本