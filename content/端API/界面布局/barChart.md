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

[reloadData](#5)

[setFrame](#6)

[close](#2)

[hide](#3)

[show](#4)
</div>

#**概述**

barChart是一个柱状图模块，非常形象的显示出数据走势。开发者只需简单的配置相应的参数，即可实现一个立体的柱状图。极大的简化了前端实现柱状图开发的代码。开发者可自定义x，y轴以及柱子的个数和颜色。本模块已停止更新，建议使用优化升级版模块[UIBarChart](http://docs.apicloud.com/端API/界面布局/UIBarChart)

![图片说明](/img/docImage/barChart.jpg)

#**open**<div id="1"></div>

打开柱状图视图

open({params}, callback(ret, err))

##params

x ：

- 类型：数字
- 默认值：0
- 描述：（可选项）视图左上角点坐标

y ：

- 类型：数字
- 默认值：100
- 描述：（可选项）视图左上角点坐标

w ：

- 类型：数字
- 默认值：当前设备屏幕的宽
- 描述：（可选项）视图的宽

h ：

- 类型：数字
- 默认值：w-20
- 描述：（可选项）视图的高

yAxisMax：

- 类型：数字
- 默认值：50
- 描述：（可选项）坐标系y轴配置参数，y轴上的最大值

yAxisStep：

- 类型：数字
- 默认值：10
- 描述：（可选项）坐标系y轴配置参数，Y轴上数据的步幅

xAxisMarks：

- 类型：数组对象
- 默认值：无
- 描述：x轴上各个标注所组成的数组，数组元素类型为字符串

datas：

- 类型：数组对象
- 默认值：无
- 描述：各个柱图的数据大小组成的数组，数组元素类型为数字

fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window

fixed:
- 类型：布尔
- 默认值：true
- 描述：（可选项）是否将模块视图固定到窗口上，不跟随窗口上下滚动

style:
- 类型：
- 默认值：见内部字段
- 描述：（可选项）模块视图内元素样式设置
- 内部字段：

```js
{
      yAxisBg:       //（可选项）y轴背景色，支持rgb，rgba，#，img，默认绿色
      yAxisMark:     //（可选项）y轴标注色，支持rgb，rgba，#，默认白色
      yAxisMarkSize: //（可选项）y轴标注字体大小，数字类型，默认12
      xAxisBg:       //（可选项）x轴背景设置，支持rgb，rgba，#，img，默认蓝色
      xAxisMark:     //（可选项）x轴标注色，支持rgb，rgba，#，默认白色
      xAxisMarkSize: //（可选项）x轴标注字体大小，数字类型，默认12
      xAxisInterval: //（可选项）x轴上边背景设置，支持rgb，rgba，#，img，默认黄
      bg:            //（可选项）模块视图背景设置，支持rgb，rgba，#，img，默认背景图
      barBg：        //（可选项）柱子背景设置，支持rgb，rgba，#，img，默认灰色
      bar:           //（可选项）柱子显示设置，支持rgb，rgba，#，img，默认蓝色
      barWidth:      //（可选项）柱子的宽度，数字类型，默认27
      interval:      //（可选项）柱子之间的间距，数字类型，默认18
}
```

##callBack(ret,err)

ret：

- 类型：json对象
- 内部字段：
  
```js
{
     id:  //打开视图的id
     index: //点击柱状图柱子的下标 
}
```
 
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

#**reloadData**<div id="5"></div>

重新加载数据

reloadData({params})

##params

id ：

- 类型：数字
- 默认值：无
- 描述：操作的视图的id

xAxisMarks ：

- 类型：数组对象
- 默认值：原值数组
- 描述：（可选项）x轴上各个标注所组成的数组，数组元素类型为字符串

datas：

- 类型：数组对象
- 默认值：原值数组
- 描述：（可选项）各个柱图的数据大小组成的数组，数组元素类型为数字

##示例代码
```js
var obj = api.require('barChart');
obj.reloadData({
   xAxisMarks:[1,2,3,4,5,6,7,8,9],
   datas:[15,30,40,5,3,49,55,23]
},function(ret,err){
   api.alert({msg:ret.index+ret.id});
});
```
##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

#**setFrame**<div id="6"></div>

重设模块视图的位置大小

setFrame({params})

##params

id ：

- 类型：数字
- 默认值：无
- 描述：操作的视图的id

x ：

- 类型：数字
- 默认值：原值
- 描述：（可选项）视图左上角点坐标

y ：

- 类型：数字
- 默认值：原值
- 描述：（可选项）视图左上角点坐标

w ：

- 类型：数字
- 默认值：原值
- 描述：（可选项）视图的宽

h ：

- 类型：数字
- 默认值：原值
- 描述：（可选项）视图的高

anim ：

- 类型：布尔
- 默认值：false
- 描述：（可选项）改变模块视图大小时是否添加变化过程的动画

##示例代码
```js
var obj = api.require('barChart');
obj.setFrame({x:10,w:300});
```
##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本


#**close**<div id="2"></div>

关闭柱状图

close(params)

##params

id ：

- 类型：数字
- 默认值：无
- 描述：操作视图的id

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
- 描述：操作视图的id

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
- 描述：操作视图的id

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