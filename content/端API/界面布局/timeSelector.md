/*
Title: timeSelector
Description: timeSelector
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[set](#2)

[close](#3)

[hide](#4)

[show](#5)
</div>

#**概述**

timeSelector是时间选择器，由两个可上下滚动的滚轮组成。原生实现滚轮效果，流畅无卡顿

![图片说明](/img/docImage/timeSelector.jpg)

#**open**<div id="1"></div>

打开时间选择器

open({params}, callback(ret, err))

##params

x：

- 类型：数字
- 默认值：0
- 描述：选择器视图左上角点坐标，可为空

y：

- 类型：数字
- 默认值：64
- 描述：选择器视图左上角点坐标，可为空

w：

- 类型：数字
- 默认值：当前设备屏幕的宽度
- 描述：选择器视图宽，可为空

h：

- 类型：数字
- 默认值：宽度减70px
- 描述：选择器视图高，可为空

hour：

- 类型：数字
- 默认值：0
- 描述：设置时，取值范围0-23，可为空

minute：

- 类型：数字
- 默认值：0
- 描述：设置分，取值范围0-59，可为空

bgColor：

- 类型：字符串
- 默认值：#FFFFFF
- 描述：选中条目的背景色值，支持rgb，rgba，#，可为空

normalColor：

- 类型：字符串
- 默认值：#959595
- 描述：未选中条目的数字色值，支持rgb，rgba，#，可为空

selectedColor：

- 类型：字符串
- 默认值：#3685dd
- 描述：选中条目的数字色值，支持rgb，rgba，#，可为空

separateColor：

- 类型：字符串
- 默认值：#575757
- 描述：中间分割线的色值，支持rgb，rgba，#，可为空

titleColor：

- 类型：字符串
- 默认值：#3685dd
- 描述：时分文字的色值，支持rgb，rgba，#，可为空

fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window

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
    hour:	//选择的小时
	minit:  //选择的分钟 deprecated
	minute:  //选择的分钟
}
```

##示例代码

```js
var timeSelector = api.require('timeSelector');
timeSelector.open({
	x: 30,
	y: api.frameHeight / 2 - 130,
	width: api.frameWidth - 60,
	height: 260,
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

打开时间选择器

##可用性

IOS系统 ，Android系统

可提供的1.0.0及更高版本


#**set**<div id="2"></div>

设置时间选择器时间

set({params})

##params

hour：

- 类型：数字
- 默认值：当前时间
- 描述：设置小时，可为空

minute：

- 类型：数字
- 默认值：当前时间
- 描述：设置分钟，可为空

##示例代码

```js
var timeSelector = api.require('timeSelector');
timeSelector.set({
	hour: 20,
	minute: 25
});
```

##补充说明

设置时间选择器

##可用性

IOS系统 ，Android系统

可提供的1.0.0及更高版本


#**close**<div id="3"></div>

关闭时间选择器

close()

##示例代码

```js
var timeSelector = api.require('timeSelector');
timeSelector.close();
```

##补充说明

关闭时间选择器

##可用性

IOS系统 ，Android系统

可提供的1.0.0及更高版本


#**hide**<div id="4"></div>

隐藏时间选择器

hide()

##示例代码

```js
var timeSelector = api.require('timeSelector');
timeSelector.hide();
```

##补充说明

隐藏时间选择器，并没有从内存里清除

##可用性

IOS系统 ，Android系统

可提供的1.0.1及更高版本

#**show**<div id="5"></div>

显示时间选择器

show()

##示例代码

```js
var timeSelector = api.require('timeSelector');
timeSelector.show();
```

##补充说明

显示已隐藏的时间选择器

##可用性

IOS系统 ，Android系统

可提供的1.0.1及更高版本