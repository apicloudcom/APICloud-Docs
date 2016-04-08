/*
Title: periodSelector
Description: periodSelector
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

periodSelector是一个时段选择器，由四个非常流畅的滚轮组成。使用此模块避免了网页实现上下滚轮效果不流畅的问题

![图片说明](/img/docImage/periodSelector.jpg)

#**open**<div id="1"></div>

打开时段选择器

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

lHour：

- 类型：数字
- 默认值：0
- 描述：时段选择器开始时间-时，可为空


lMinute：

- 类型：数字
- 默认值：0
- 描述：时段选择器开始时间-分，可为空

rHour：

- 类型：数字
- 默认值：0
- 描述：时段选择器结束时间-时，可为空


rMinit：

- 类型：数字
- 默认值：0
- 描述：时段选择器结束时间-分，可为空

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
	sHour:			//选择的起始小时
	sMinit: 		//选择的起始分钟 deprecated
	eHour:          //选择的结束小时
	eMinit:         //选择的结束分钟deprecated
    eMinute:        //选择的结束分钟
    sMinute:        //选择的起始分钟


}
```

##示例代码

```js
var periodSelector = api.require('periodSelector');
periodSelector.open({
	x: 30,
	y: api.frameHeight / 2 - 170,
	w: api.frameWidth - 60,
	h: 340,
    fixedOn: api.frameName
}, function( ret, err ){
	if( ret ){
         alert( JSON.stringify( ret ) );
    }else{
         alert( JSON.stringify( err ) );
    }
});
```

##补充说明

打开时段选择器

##可用性

iOS系统、 android系统

可提供的1.0.0及更高版本



#**set**<div id="2"></div>

设置时段选择器

set({params})

##params

lHour：

- 类型：数字
- 默认值：当前时间的时
- 描述：时段选择器开始时间-时，可为空

lMinute：

- 类型：数字
- 默认值：当前时间的分
- 描述：时段选择器开始时间-分，可为空

rHour：

- 类型：数字
- 默认值：当前时间的时
- 描述：时段选择器结束时间-时，可为空


rMinute：

- 类型：数字
- 默认值：当前时间的分
- 描述：时段选择器结束时间-分，可为空

##示例代码

```js
var periodSelector = api.require('periodSelector');
periodSelector.set();
```

##补充说明

设置时段选择器

##可用性

iOS系统、 android系统

可提供的1.0.0及更高版本


#**close**<div id="3"></div>

关闭时段选择器

close()

##示例代码

```js
var periodSelector = api.require('periodSelector');
periodSelector.close();
```

##补充说明

关闭时段选择器

##可用性

iOS系统、 android系统

可提供的1.0.0及更高版本

#**hide**<div id="4"></div>

隐藏时段选择器

hide()

##示例代码

```js
var periodSelector = api.require('periodSelector');
periodSelector.hide();
```

##补充说明

隐藏时段选择器，并没有从内存里清除

##可用性

iOS系统、 android系统

可提供的1.0.1及更高版本

#**show**<div id="5"></div>

显示时段选择器

show()

##示例代码

```js
var periodSelector = api.require('periodSelector');
periodSelector.show();
```

##补充说明

显示已隐藏的时段选择器

##可用性

iOS系统、 android系统

可提供的1.0.1及更高版本

