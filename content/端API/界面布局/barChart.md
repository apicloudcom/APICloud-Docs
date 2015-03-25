/*
Title: barChart
Description: barChart
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

barChart是一个柱状图模块，非常形象的显示出数据走势。开发者只需简单的配置相应的参数，即可实现一个立体的柱状图。极大的简化了前端实现柱状图开发的代码。开发者可自定义x，y轴以及柱子的个数和颜色

![图片说明](/img/docImage/barChart.jpg)

#**open**<div id="1"></div>

打开柱状图视图

open({params}, callback(ret, err))

##params

x ：

- 类型：数字
- 默认值：无
- 描述：视图左上角点坐标，不可为空

y ：

- 类型：数字
- 默认值：无
- 描述：视图左上角点坐标，不可为空

<del>width ：</del>

-<del> 类型：数字</del>
- <del>默认值：无</del>
- <del>描述：视图的宽，可为空</del>

<del>height ：</del>

- <del>类型：数字</del>
- <del>默认值：无</del>
- <del>描述：视图的高，可为空</del>

w ：

- 类型：数字
- 默认值：当前设备屏幕的宽
- 描述：视图的宽，可为空

h ：

- 类型：数字
- 默认值：w-20
- 描述：视图的高，可为空

yAxisMax：

- 类型：数字
- 默认值：50
- 描述：坐标系y轴配置参数，y轴上的最大值，可为空

yAxisStep：

- 类型：数字
- 默认值：10
- 描述：坐标系y轴配置参数，Y轴上数据的步幅，可为空

xAxisMarks：

- 类型：数组对象
- 默认值：无
- 描述：x轴上各个标注所组成的数组，数组元素类型为字符串，不可为空

datas：

- 类型：数组对象
- 默认值：无
- 描述：各个柱图的数据大小组成的数组，数组元素类型为数字，不可为空

fixedOn：

- 类型：字符串
- 默认值：当前主窗口的名字
- 描述：将此模块视图添加到指定窗口的名字，可为空

fixed:
- 类型：布尔
- 默认值：true
- 描述：是否将模块视图固定到窗口上，不跟随窗口上下滚动，可为空

##callBack(ret,err)

ret：

- 类型：json对象
- 内部字段：
  
  {
       id:  //打开视图的id
       index: //点击柱状图柱子的下标 
  }

##示例代码
```js
var obj = api.require('barChart');
obj.open({
	x:0,
	y:64,
	width:320,
	height:300,
	yAxisMax:50,
	yAxisStep:10,
	xAxisMarks:[1,2,3,4,5,6,7,8,9],
	datas:[10,30,40,5,3,49,55,23],
	id:1
},function(ret,err){
	api.alert({msg:ret.index+ret.id});
});
```
##补充说明

打开柱状图

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**close**<div id="2"></div>

关闭柱状图

close(params)

##params

id ：

- 类型：数字
- 默认值：无
- 描述：操作视图的id，不可为空

##示例代码
```js
var obj = api.require('barChart');
obj.close({
    id:1
});
```
##补充说明

关闭柱状图

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**hide**<div id="3"></div>

隐藏柱状图视图

hide(params)

##params

id ：

- 类型：数字
- 默认值：无
- 描述：操作视图的id，不可为空

##示例代码
```js
var obj = api.require('barChart');
obj.hide({
    id:1
});
```
##补充说明

隐藏已显示的柱状图视图，并没有从内存里清除

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

#**show**<div id="4"></div>

显示柱状图

show(params)

##params

id ：

- 类型：数字
- 默认值：无
- 描述：操作视图的id，不可为空

##示例代码
```js
var obj = api.require('barChart');
obj.show({
    id:1
});
```
##补充说明

显示已隐藏的柱状图视图

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本