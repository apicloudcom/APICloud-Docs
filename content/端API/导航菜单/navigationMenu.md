/*
Title: navigationMenu
Description: navigationMenu
*/

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

navigationMenu是一个导航栏菜单，可以实现在导航栏上弹出一个菜单，然后子菜单左右铺展开来的动画效果，开发者可自定义其中的样式和按钮个数，超出屏幕部分可左右拖动查看

![图片说明](/img/docImage/navigationMenu.jpg)

#**open**<div id="1"></div>

打开导航菜单

open({params}, callback(ret, err))

##params

color：

- 类型：字符串
- 默认值：#FFFFFF
- 描述：按钮文字颜色，支持rgb，rgba，#，可为空

highlight：

- 类型：字符串
- 默认值：#d36bff
- 描述：按钮文字选中后的颜色，支持rgb，rgba，#，可为空

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

- 类型：字符串
- 默认值：当前主窗口的名字
- 描述：将此模块视图添加到指定窗口的名字，可为空

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
var obj = api.require('navigationMenu');
var arrayPath = new Array();
for(var i=0;i<17;i++){
	arrayPath[i] = {
		normal: 'widget://res/navigationMenu_normal.png',
		highlight: 'widget://res/ navigationMenu_highlight.png',
		selected: 'widget://res/navigationMenu_selected.png',
		title: '收藏'
	};
}
obj.open({
	btnInfo: arrayPath
},function(ret,err){
     api.alert({msg:ret.index});
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

    var obj = api.require('navigationMenu');
    obj.hidden();

##<del>补充说明</del>

<del>隐藏菜单，只是移除到屏幕之外，还在内存里没有清除</del>

##<del>可用性</del>

<del>iOS系统，Android系统</del>
<del>可提供的1.0.0及更高版本</del>


#**hide**<div id="5"></div>

隐藏菜单

hide()

##示例代码

    var obj = api.require('navigationMenu');
    obj.hide();

##补充说明

隐藏菜单，只是移除到屏幕之外，还在内存里没有清除

##可用性

iOS系统，Android系统
可提供的1.0.1及更高版本

#**show**<div id="3"></div>

显示菜单

show()

##示例代码

    var obj = api.require('navigationMenu');
    obj.show();

##补充说明

显示菜单，从屏幕外移动到屏幕内

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**close**<div id="4"></div>

关闭菜单

close()

##示例代码

    var obj = api.require('navigationMenu');
    obj.close();

##补充说明

关闭菜单，意味着从内存里清除

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
