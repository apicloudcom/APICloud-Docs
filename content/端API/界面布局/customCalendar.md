/*
Title: customCalendar
Description: customCalendar
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[showNextMonth](#2)

[showPreviousMonth](#3)

[close](#4)

[hide](#5)

[show](#6)
</div>

#**概述**

customCalendar是一个简单的日历模块，原生实现了公历历法列表，开发者可添加特殊日期标注，只需简单配置参数即可实现一个复杂的日历效果界面

#**open**<div id="1"></div>

打开日历

open({params}, callback(ret, err))

##params
x:

- 类型：数字
- 默认值：0
- 描述：（可选项）日历视图左上角点的x坐标

y:

- 类型：数字
- 默认值：0
- 描述：（可选项）日历视图左上角点的y坐标

w:

- 类型：数字
- 默认值：屏幕宽度
- 描述：（可选项）日历视图宽

h:

- 类型：数字
- 默认值：220
- 描述：（可选项）日历视图高

bg:

- 类型：字符串
- 默认值：rgba(0,0,0,0)
- 描述：（可选项）日历背景，默认透明，支持颜色（#、rgb、rgba格式）和图片（支持widget://、fs://等路径协议）

weekSize:

- 类型：字符串
- 默认值：12
- 描述：（可选项）顶部的星期文字大小

weekColor:

- 类型：字符串
- 默认值：#000
- 描述：（可选项）顶部的星期文字颜色，支持#、rgb、rgba格式

dateSize:

- 类型：字符串
- 默认值：12
- 描述：（可选项）日期文字大小

commonDateColor:

- 类型：字符串
- 默认值：#000
- 描述：（可选项）普通日期文字颜色，支持#、rgb、rgba格式

commonDateSelectedColor:

- 类型：字符串
- 默认值：#fff
- 描述：（可选项）普通日期选中后的文字颜色，支持#、rgb、rgba格式

commonDateSelectedBg:

- 类型：字符串
- 默认值：#000
- 描述：（可选项）普通日期点击选中后的背景，当为颜色时，背景为一个实心圆
，支持颜色（#、rgb、rgba格式）和图片（支持widget://、fs://等路径协议）

currentDateColor:

- 类型：字符串
- 默认值：rgb(230,46,37)
- 描述：（可选项）当前日期文字颜色，支持#、rgb、rgba格式

currentDateSelectedColor:

- 类型：字符串
- 默认值：#fff
- 描述：（可选项）当前日期选中后的文字颜色，支持#、rgb、rgba格式

currentDateSelectedBg:

- 类型：字符串
- 默认值：rgb(230,46,37)
- 描述：（可选项）当前日期点击选中后的背景，当为颜色时，背景为一个实心圆
，支持颜色（#、rgb、rgba格式）和图片（支持widget://、fs://等路径协议）

specialDateList:

- 类型：JSON数组
- 默认值：无
- 描述：（可选项）需要标记的特殊日期数组
- 内部字段：

	```js
	[{
		date:				//日期格式化字符串，格式为yyyy-MM-dd，字符串类型
		color:				//（可选项）文字颜色，默认为commonDateColor的值，支持#、rgb、rgba格式，字符串类型
		selectedColor:		//（可选项）选中后文字颜色，默认为commonDateSelectedColor的值，支持#、rgb、rgba格式，字符串类型
		bg:					//（可选项）背景，默认为commonDateSelectedBg的值，当为颜色时，背景为一个实心圆
，支持颜色（#、rgb、rgba格式）和图片（支持widget://、fs://等路径协议），字符串类型
	}]
	```

showDisabledDate:

- 类型：布尔
- 默认值：true
- 描述：（可选项）是否显示不在该月的日期

disabledDateColor:

- 类型：字符串
- 默认值：rgb(145,145,145)
- 描述：（可选项）不在该月的日期文字颜色，支持#、rgb、rgba格式

fixedOn：

- 类型：字符串
- 默认值：当前主窗口的名字
- 描述：（可选项）将此模块视图添加到指定窗口的名字

fixed：

- 类型：布尔
- 默认值：true
- 描述：（可选项）是否固定住不随页面滚动而移动

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	year:					//当前显示的年份，数字类型
	month:					//当前显示的月份，数字类型
	selectedDate:			//用户点击选择的日期，格式为yyyy-MM-dd，字符串类型
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    msg:           //错误描述
}
```

##示例代码

```js
var obj = api.require('customCalendar');
obj.open({
	x:0,
	y:100,
	w:api.winWidth,
	h:300,
	specialDate:[{
		date:'2015-06-01',
		color:'#ff0',
		bg:'widget://image/specialDateBg.png'
	}]
},function(ret,err) {
	if(ret){
		var date = ret.date;
	}else{
		var msg = err.msg;
	}
});
```

##补充说明

打开日历

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**showNextMonth**<div id="2"></div>

显示下个月日历

showNextMonth(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	year:					//当前显示的年份，数字类型
	month:					//当前显示的月份，数字类型
}
```

##示例代码

```js
var obj = api.require('customCalendar');
obj.showNextMonth(
    function(ret,err){
        var year = ret.year;
        var month = ret.month;
    }
);
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**showPreviousMonth**<div id="3"></div>

显示上个月日历

showPreviousMonth(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	year:					//当前显示的年份，数字类型
	month:					//当前显示的月份，数字类型
}
```

##示例代码

```js
var obj = api.require('customCalendar');
obj.showPreviousMonth(
    function(ret,err){
        var year = ret.year;
        var month = ret.month;
    }
);
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**close**<div id="4"></div>

关闭日历

close()

##示例代码

    var obj = api.require('customCalendar');
    obj.close();

##补充说明

关闭日历

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**hide**<div id="5"></div>

隐藏日历

hide()

##示例代码

    var obj = api.require('customCalendar');
    obj.hide();

##补充说明

隐藏日历视图，并没有从内存清空

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

#**show**<div id="6"></div>

显示已隐藏日历

show()

##示例代码

    var obj = api.require('customCalendar');
    obj.show();

##补充说明

显示已隐藏日历视图

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本
