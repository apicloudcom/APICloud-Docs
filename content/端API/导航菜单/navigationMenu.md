/*
Title: navigationMenu
Description: navigationMenu
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[hidden](#2)

[hidden](#5)

[show](#3)

[close](#4)
</div>

#**概述**

navigationMenu 是一个导航栏菜单，可以实现在导航栏上弹出一个菜单，然后子菜单左右铺展开来的动画效果，开发者可自定义其中的样式和按钮个数，超出屏幕部分可左右拖动查看。本模块已停止更新，建议使用优化升级版模块 [MNNavigationMenu](http://docs.apicloud.com/端API/导航菜单/MNNavigationMenu)

![图片说明](/img/docImage/navigationMenu.jpg)

#**open**<div id="1"></div>

打开导航菜单

open({params}, callback(ret, err))

##params

color：

- 类型：字符串
- 默认值：#FFFFFF
- 描述：按钮文字颜色，支持 rgb，rgba，#，可为空

highlight：

- 类型：字符串
- 默认值：#d36bff
- 描述：按钮文字选中后的颜色，支持 rgb，rgba，#，可为空

btnInfo：

- 类型：数组
- 默认值：无
- 描述：菜单里按钮的参数配置，不可为空

内部字段：

```js
[{
	normal:           //按钮背景图片路径，字符串，不可为空
	highlight:        //按钮点击时背景图片路径，字符串，可为空
	selected:         //按钮选中后背景图片路径，字符串，可为空
	title:            //按钮的标题文字，字符串，可为空
}]
```

fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	index：		//用户点击按钮的下标
}
```

##示例代码

```js
var navigationMenu = api.require('navigationMenu');
navigationMenu.open({
	btnInfo: [{
		normal: 'widget://res/img/ic/small-bell.png',
		highlight: 'widget://res/img/ic/small-bell.png',
		selected: 'widget://res/img/ic/small-bell.png',
		title: '按钮一'
	},{
		normal: 'widget://res/img/ic/small-bell.png',
		highlight: 'widget://res/img/ic/small-bell.png',
		selected: 'widget://res/img/ic/small-bell.png',
		title: '按钮一'
	}]
}, function(ret, err){		
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
var navigationMenu = api.require('navigationMenu');
navigationMenu.hidden();
```

##<del>补充说明</del>

<del>隐藏菜单，只是移除到屏幕之外，还在内存里没有清除</del>

##<del>可用性</del>

<del>iOS系统，Android系统</del>
<del>可提供的1.0.0及更高版本</del>


#**hide**<div id="5"></div>

隐藏菜单

hide()

##示例代码

```js
var navigationMenu = api.require('navigationMenu');
navigationMenu.hide();
```

##补充说明

隐藏菜单，只是移除到屏幕之外，还在内存里没有清除

##可用性

iOS系统，Android系统
可提供的1.0.1及更高版本

#**show**<div id="3"></div>

显示菜单

show()

##示例代码

```js
var navigationMenu = api.require('navigationMenu');
navigationMenu.show();
```

##补充说明

显示菜单，从屏幕外移动到屏幕内

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**close**<div id="4"></div>

关闭菜单

close()

##示例代码

```js
var navigationMenu = api.require('navigationMenu');
navigationMenu.close();
```

##补充说明

关闭菜单，意味着从内存里清除

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本