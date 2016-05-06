/*
Title: calendar
Description: calendar
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[close](#2)
</div>

#**概述**

calendar是一个简单的日历模块，原生实现了公历历法列表，开发者可添加特殊日期标注，只需简单配置参数即可实现一个复杂的日历效果界面。**UICalendar 模块是 calendar 模块的优化版，建议使用  [UICalendar](http://docs.apicloud.com/端API/界面布局/UICalendar) 模块，此模块已停止更新。**

![图片说明](/img/docImage/calendar.jpg)

#**open**<div id="1"></div>

打开日历

open({params}, callback(ret, err))

##params
x:

- 类型：数字
- 默认值：0
- 描述：日历视图左上角点的x坐标，可为空

y:

- 类型：数字
- 默认值：100
- 描述：日历视图左上角点的y坐标，可为空

w:

- 类型：数字
- 默认值：当前设备屏幕的宽
- 描述：日历视图宽，可为空

h:

- 类型：数字
- 默认值：w-40
- 描述：日历视图高，可为空

specialDate:

- 类型：数组
- 默认值：无
- 描述：需要标记的特殊日期组成的数组，数组元素类型为字符串，格式为yyyy-MM-dd，可为空

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
    date:’’           //用户点击的日期，格式为yyyy-MM-dd
}
```

##示例代码

```js
var calendar = api.require('calendar');
calendar.open({
	x: 100,
	y:100,
	width:300,
	height:300,
    specialDate:['2014-05-01','2014-05-11','2014-05-20','2014-05-25','2014-05-31']
},function(ret,err) {
    var date = ret.date;
});
```

##补充说明

打开日历

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**close**<div id="2"></div>

关闭日历

close()

##示例代码

    var calendar = api.require('calendar');
    calendar.close();

##补充说明

关闭日历

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**hide**<div id="3"></div>

隐藏日历

hide()

##示例代码

    var calendar = api.require('calendar');
    calendar.hide();

##补充说明

隐藏日历视图，并没有从内存清空

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

#**show**<div id="4"></div>

显示已隐藏日历

show()

##示例代码

    var calendar = api.require('calendar');
    calendar.show();

##补充说明

显示已隐藏日历视图

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本
