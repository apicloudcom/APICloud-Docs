/*
Title: coverFlow
Description: coverFlow
*/

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

coverFlow底层封装了openGL实现的3D图片流效果和逼真的倒影。开发者可自定义图片及其数量。只需一个open接口就能打开一个超炫酷的coverFlow效果导航菜单

![图片说明](/img/docImage/coverFlow.jpg)

#**open**<div id="1"></div>

打开coverFlow

open({params}, callback(ret, err))

##params

x ：

- 类型：数字
- 默认值：0
- 描述：视图左上角点坐标，可为空

y：

- 类型：数字
- 默认值：100
- 描述：视图左上角点坐标，可为空

<del>width：<del>

- <del>类型：数字<del>
- <del>默认值：无<del>
- <del>描述：视图的宽，可为空<del>

<del>height：<del>

- <del>类型：数字<del>
- <del>默认值：无<del>
- <del>描述：视图的高，可为空</del>

w：

- 类型：数字
- 默认值：当前设备屏幕的宽
- 描述：视图的宽，可为空

h：

- 类型：数字
- 默认值：w-20
- 描述：视图的高，可为空

<del>backGroundColor：</del>

- <del>类型：字符串</del>
- <del>默认值：无</del>
- <del>描述：背景颜色十六进制值</del>

bgColor：

- 类型：字符串
- 默认值：rgba(0,0,0,0)
- 描述：背景颜色十六进制值,支持rgb，rgba，#，可为空

paths：

- 类型：数组
- 默认值：无
- 描述：图片路径组成的数组，不可为空

fixedOn：

- 类型：字符串
- 默认值：当前主窗口的名字
- 描述：将此模块视图添加到指定窗口的名字，可为空

reflect：

- 类型：布尔值
- 默认值：true
- 描述：是否显示倒影，可为空

fixed:
- 类型：布尔
- 默认值：true
- 描述：是否将模块视图固定到窗口上，不跟随窗口上下滚动，可为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	index:           //返回用户选择的图片的下标
}
```

##示例代码

```js
var obj = api.require('coverFlow');
obj.open({
	x:0,
	y:64,
	w:320,
	h:300,
	bgColor:'#ADD8E6',
	paths:['widget://res/a1.png','widget://res/a2.png','widget://res/a3.png',
		'widget://res/a4.png','widget://res/a5.png','widget://res/a6.png',
		'widget://res/a7.png','widget://res/a8.png','widget://res/a9.png',
		'widget://res/a10.png']
},function(ret,err) {
	var index = ret.index;
});
```

##补充说明

打开coverFlow模块视图

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**close**<div id="2"></div>

关闭coverFlow

close()

##示例代码

    var obj = api.require('coverFlow');
    obj.close();

##补充说明

关闭coverFlow

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**hide**<div id="2"></div>

隐藏显示的coverFlow视图

hide()

##示例代码

    var obj = api.require('coverFlow');
    obj.hide();

##补充说明

只是隐藏模块视图，并没有从内存里清除

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

#**show**<div id="4"></div>

显示已隐藏的coverFlow视图

show()

##示例代码

    var obj = api.require('coverFlow');
    obj.show();

##补充说明

显示模块视图

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本