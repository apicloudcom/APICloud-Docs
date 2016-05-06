/*
Title: stackMenu
Description: stackMenu
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[close](#2)

[show](#3)

[hide](#4)
</div>

#**概述**

stackMenu 是一个栈菜单，高度模仿 mac 系统下的 dock 管理器。同时允许开发者自定义按钮样式和个数，让开发者轻松实现复杂的ui效果。本模块已停止更新，建议使用优化升级版模块 [MNStack](http://docs.apicloud.com/端API/导航菜单/MNStack)

![图片说明](/img/docImage/stackMenu.jpg)

#**open**<div id="1"></div>

打开stack菜单

open({params}, callback(ret, err))

##params

startX：

- 类型：数字
- 默认值：120
- 描述：stack菜单起点坐标，可为空

startY：

- 类型：数字
- 默认值：当前屏幕高减去70
- 描述：stack菜单起点坐标，可为空

itemSize：

- 类型：数字
- 默认值：50
- 描述：子菜单大小，可为空

direction：

- 类型：字符串
- 默认值：right_up
- 描述：弹出子菜单方向，详情参考弹出菜单方向常量，可为空

titleColor：

- 类型：字符串
- 默认值：#8b3e2f
- 描述：子菜单标题颜色，可为空

items：

- 类型：数组
- 默认值：无
- 描述：子菜单参数组成的数组，不可为空

内部字段：

```js
[{
	title：              //子按钮标题
	icon:               // 子按钮头像
}]
```

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	index:                     //选中的子菜单按钮的下标
}
```

##示例代码

```js
var stackMenu = api.require('stackMenu');
stackMenu.open({
	items:[{
        title: '标题一',
        icon: 'widget://res/img/ic/small-bell.png'
    },{
        title: '标题二',
        icon: 'widget://res/img/ic/clock.png'
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

打开 stack 菜单

##可用性

iOS系统，Android系统

可提供的0.0.1及更高版本


#**close**<div id="2"></div>

关闭菜单

close()

##示例代码

```js
var stackMenu = api.require('stackMenu');
stackMenu.close();
```

##补充说明

关闭菜单，意味着从内存里清除

##可用性

iOS系统，Android系统

可提供的0.0.1及更高版本

#**show**<div id="3"></div>

显示菜单

close()

##示例代码

```js
var stackMenu = api.require('stackMenu');
stackMenu.show();
```

##补充说明

显示菜单

##可用性

iOS系统，Android系统

可提供的0.0.1及更高版本


#**hide**<div id="4"></div>

隐藏菜单

hide()

##示例代码

```js
var stackMenu = api.require('stackMenu');
stackMenu.hide();
```

##补充说明

隐藏菜单，并没有从内存里清除

##可用性

iOS系统，Android系统

可提供的0.0.1及更高版本


<div id="const-content">
#**弹出菜单方向**

设置菜单弹出的方向。字符串类型

##取值范围

- right_up 		//往右边向上弹出
- right_down 	//向右边向下弹出
- left_up		//往左边向上弹出
- left_down		//向左边向下弹出