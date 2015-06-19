/*
Title: pullMenu
Description: pullMenu
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[hidden](#2)

[hide](#5)

[show](#3)

[close](#4)
</div>

#**概述**

pullMenu是一个可上下拖动的菜单，可随手指上下滑动。其子菜单按钮都可自定义样式，超过部分可拖动查看。性能强，流畅度高

![图片说明](/img/docImage/pullMenu.jpg)

#**open**<div id="1"></div>

打开拖拉菜单

open({params}, callback(ret, err))

##params

type：

- 类型：字符串
- 默认值：up
- 描述：（可选项）菜单类型，<del>0代表从上往下弹出，1代表从下往上弹出</del>，取值范围up--从上往下、down--从下往上

h：

- 类型：数字
- 默认值：当前设备屏幕高度的三分之二
- 描述：（可选项）菜单视图的高

btnWidth：

- 类型：数字
- 默认值：60
- 描述：（可选项）菜单里每个按钮的（正方形）边长

alpha:

- 类型：数字
- 默认值：0.8
- 描述：（可选项）菜单背景透明度，取值范围为0-1

bgColor：

- 类型：字符串
- 默认值：#FFFFFF
- 描述：（可选项）菜单背景色，支持rgb，rgba，#

btnArray：

- 类型：数组
- 默认值：无
- 描述：（可选项）菜单里每个按钮的背景图片、选中图片路径组成的数组
- 内部字段：

```js
[{
      normal:          //按钮常态下的图标，字符串，支持fs、widget等本地路径协议
      selected:        //按钮选中后的图标，字符串，支持fs、widget等本地路径协议
}]
```

selectedIndex：

- 类型：数字
- 默认值：0
- 描述：（可选项）设置默认选中按钮的索引

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	index：		//用户点击按钮的下标
}
```

##示例代码

```js
var obj = api.require('pullMenu');
var arrayPath = new Array();
for(var i=0;i<17;i++){
	arrayPath[i]={
		normal: 'widget://res/pullMenu_btn1light.png',
		highlight: 'widget://res/pullMenu_btn1.png'
	};
}
obj.open({
	btnArray:arrayPath
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

    var obj = api.require('pullMenu');
    obj.hidden();

##<del>补充说明</del>

<del>隐藏菜单，只是移除到屏幕之外，还在内存里没有清除</del>

##<del>可用性</del>

<del>iOS系统，Android系统</del>

<del>可提供的1.0.0及更高版本</del>

#**setSelected**<div id="5"></div>

设置按钮选中/取消状态

setSelected({params})

##params

index：

 - 类型：数字
 - 默认值：0
 - 描述：(可选项)要设置的按钮的索引

 selected：

 - 类型：布尔
 - 默认值：true
 - 描述：(可选项)是否要将指定索引的按钮设置为选中状态

##示例代码

    var obj = api.require('pullMenu');
    obj.setSelected({
       index:2,
       selected:true
    });

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

#**hide**<div id="5"></div>

隐藏菜单

hide()

##示例代码

    var obj = api.require('pullMenu');
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

    var obj = api.require('pullMenu');
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

	var obj = api.require('pullMenu');
	obj.close();

##补充说明

关闭菜单，意味着从内存里清除

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
