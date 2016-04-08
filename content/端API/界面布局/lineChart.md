/*
Title: lineChart
Description: lineChart
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[close](#2)
</div>

#**概述**

lineChart模块封装了k线图的绘制方法，开发者可自定义图表的样式，只需传入相应的数据，即可在图表上显示多条折线。亦可自定义结点点击事件。本模块已停止更新，建议使用优化升级版模块[UILineChart](http://docs.apicloud.com/端API/界面布局/UILineChart)

![图片说明](/img/docImage/lineChart.jpg)

#**open**<div id="1"></div>

打开K线图视图

open({params}, callback(ret, err))

##params

x：

- 类型：数字
- 默认值：0
- 描述：视图左上角点坐标，可为空

y：

- 类型：数字
- 默认值：100
- 描述：视图左上角点坐标，可为空

w：

- 类型：数字
- 默认值：当前设备屏幕的宽
- 描述：视图的宽，可为空

h：

- 类型：数字
- 默认值：w-2
- 描述：视图的高，可为空

yAxis：

- 类型：JSON对象
- 默认值：无
- 描述：K线图坐标系y轴配置参数，不可为空

 内部字段：
 
 ```js
 {
      max          //y轴最大值,数字类型，不可为空
      step         //Y轴步幅，数字类型，不可为空
 }
 ```


xAxis：

- 类型：JSON对象
- 默认值：无
- 描述：K线图坐标系x轴配置参数，不可为空
 
 内部字段：
 
 ```js
 {
        indexs:['一月’,’二月’,’三月'] //x轴标注（本字段是个数组对象），不可为空
        screenXcount:               //每屏显示纵轴个数，数字类型，不可为空
 }
 ```

lines：

- 类型：数组
- 默认值：无
- 描述：K线配置参数，不可为空
 
 内部字段：
 
 ```js
 {
       color:                               //十六进制颜色字符串,不可为空
       datas:[ 200,400,-300,500,-400]       //K线的数据组成的数组,不可为空
       id:                                  //k线的id,不可为空
 }
 ```

 bgColor：

- 类型：字符串
- 默认值：#FFFFFF
- 描述：K线图背景颜色，支持rgb，rgba，#，可为空

coorLineColor：

- 类型：字符串
- 默认值：#000000
- 描述：K线图折线的颜色，支持rgb，rgba，#，不可为空

markColor：

- 类型：字符串
- 默认值：#000000
- 描述：K线图xy轴标记字体颜色，支持rgb，rgba，#，不可为空

fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window

fixed:
- 类型：布尔
- 默认值：true
- 描述：是否将模块视图固定到窗口上，不跟随窗口上下滚动，可为空

callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:              //状态值
	index:               //点击的k线的结点的下标，数字
	id: （deprecated）   //点击的K线的id ，数字（将要废弃此参数）
	chartId:         //模块视图的id，数字类型
    lineId:          //点击的K线的id，数字类型

}
```

err:

- 类型：json对象

内部字段：

```js
{
	msg：	//打开失败信息
}
```

##示例代码

```js
var lineChart = api.require('lineChart');
lineChart.open({
	x: 0,
	y: 64,
	w: 320,
	h: 300,
	yAxis: {
	    "max": 1000,
	    "step": 200
	},
	xAxis: {
	    "indexs": ['一月','二月','三月','四月','五月','六月','七月','八月','九月','十月','十一月','十二月','一月'],
	    "screenXcount": 7
	},
	lines: [{
	    'color': '#800080', 
	    'datas': [ 200,400,-300,500,-400,600,400,0,500,-100,800,100],
	     id: 1
	},{
	    'color': '#7FFFAA', 
	    'datas': [ -200,-400,300,-500,400,-600,-400,0,-500,100,-800,-100],
	    id: 2
	}],
	bgColor: '#F0FFFF',
	coorLineColor: '#C0C0C0',
	markColor: '#051353'
},function( ret, err) {
    if( ret ){
         alert( JSON.stringify( ret ) );
    }else{
         alert( JSON.stringify( err ) );
    }
});
```

##补充说明

打开K线图视图

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**hide**<div id="2"></div>

隐藏K线图视图

hide(params)

##param

id：

- 类型：数字
- 默认值：无
- 描述：要隐藏的K线图id，不可为空

##示例代码

```js
var lineChart = api.require('lineChart');
lineChart.hide({
    id: 1
});
```

##补充说明

隐藏K线图视图，并没有从内存清空

##可用性

IOS系统，安卓系统

可提供的1.0.1及更高版本

#**show**<div id="2"></div>

显示K线图视图

show(params)

##params

id：

- 类型：数字
- 默认值：无
- 描述：要显示的K线图id，不可为空

##示例代码

```js
var lineChart = api.require('lineChart');
lineChart.show();
```

##补充说明

显示已隐藏的K线图视图

##可用性

IOS系统，安卓系统

可提供的1.0.1及更高版本

#**close**<div id="2"></div>

关闭K线图

close()

##params

id：

- 类型：数字
- 默认值：无
- 描述：K线图id，不可为

##示例代码

```js
var lineChart = api.require('lineChart');
lineChart.close({
	id:1
});
```
##补充说明

关闭K线图

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
