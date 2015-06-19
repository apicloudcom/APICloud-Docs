/*
Title: sideMenu
Description: sideMenu
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

sideMenu是一个从边框弹出的菜单，允许开发者自定义子按钮的样式和个数。打开时会有从边框弹出的动画

![图片说明](/img/docImage/sideMenu.jpg)

#**open**<div id="1"></div>

打开菜单

open({params}, callback(ret, err))

##params

type：

- 类型：数字
- 默认值：0
- 描述：菜单类型，0代表从左往右弹出，非0代表从右往左弹出，可为空

startPosition：

- 类型：数字
- 默认值：紧贴导航条下边缘
- 描述：菜单最上边的第一个按钮的起始位置，可为空

btnHeight：

- 类型：数字
- 默认值：60
- 描述：菜单里单个按钮的高度，可为空

interval：

- 类型：数字
- 默认值：10
- 描述：菜单里两个相邻按钮间的距离，可为空

trajectoryColor：

- 类型：字符串
- 默认值：无
- 描述：弹出的按钮的弹道的颜色，可为空，若为空则不显示弹道

btnArray：

- 类型：数组
- 默认值：无
- 描述：弹出的按钮的信息，不可为空

内部字段：

```js
[{
	icon:                      //字符串，按钮的图标，支持本地协议，不可为空
	bgImg:                     //字符串，按钮背景图标，支持本地协议，不可为空
}]
```
fixedOn：

- 类型：字符串
- 默认值：当前主窗口的名字
- 描述：将此模块视图添加到指定窗口的名字，可为空

clickHide：

- 类型：布尔值
- 默认值：true
- 描述：点击子按钮后是否隐藏菜单，可为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	id:             //菜单的id
	index：			//用户点击按钮的下标
}
```

##示例代码

```js
var obj = api.require('sideMenu');
var arrayPath = new Array();
arrayPath[0]={icon:'widget://res/sideMemu_icon.png',bgImg:'widget://res/sideMenu_bg.png' };
arrayPath[1]={icon: 'widget://res/sideMemu_icon.png',bgImg: 'widget://res/sideMenu_bg1.png' };
arrayPath[2]={icon: 'widget://res/sideMemu_icon.png',bgImg: 'widget://res/sideMenu_bg.png' };
arrayPath[3]={icon: 'widget://res/sideMemu_icon.png',bgImg: 'widget://res/sideMenu_bg1.png' };

obj.open({
	btnArray:arrayPath
},function(ret,err){
	api.alert({msg:'点击了菜单id为'+ret.id+'的第'+ret.index+'个按钮'});
});
```

##补充说明

打开菜单

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**hidden**

隐藏菜单

hidden({params})

##params

id：

- 类型：数字
- 默认值：无
- 描述：要操作的菜单的id，不可为空

##示例代码

```js
var obj = api.require('sideMenu');
obj.hidden({
	id:1
});
```

##补充说明

隐藏菜单，只是移除到屏幕之外，还在内存里没有清除

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**show**

显示菜单

show({parmas})

##params

id：

- 类型：数字
- 默认值：无
- 描述：要操作的菜单的id，不可为空

##示例代码

```js
var obj = api.require('sideMenu');
obj.show({
	id:1
});
```

##补充说明

显示菜单，从屏幕外移动到屏幕内

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**close**

关闭菜单

close({parmas})

##params

id：

- 类型：数字
- 默认值：无
- 描述：要操作的菜单的id，不可为空

##示例代码

```js
var obj = api.require('sideMenu');
obj.close({
	id:1
});
```

##补充说明

关闭菜单，意味着从内存里清除

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
