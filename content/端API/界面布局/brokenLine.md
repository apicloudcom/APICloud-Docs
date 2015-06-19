/*
Title: brokenLine
Description: brokenLine
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[reloadData](#2)

[appendData](#3)

[close](#4)

[hide](#5)

[show](#6)
</div>

#**概述**

brokenLine模块封装了一个折线图视图，开发者可自定义其样式，可刷新数据，左右拖动查看不同的数据，并且能响应用户点击结点的事件。目前暂仅支持绘制单条折线，由于本模块是有第三方模块开发者提供，使用本模块需在线云编译安装包。如下图：

![图片说明](/img/docImage/brokenLine.jpg)

#**open**<div id="1"></div>

打开折线图视图

open({params}, callback(ret, err))

##params

x：

- 类型：数字	
- 默认值： 0
- 描述：模块视图左上角点的坐标，可为空

y：

- 类型：数字	
- 默认值：0
- 描述：模块视图左上角点的坐标，可为空

w：

- 类型：数字	
- 默认值：当前设备屏幕的宽
- 描述：模块视图左上角点的宽，可为空

h：

- 类型：数字	
- 默认值：w-60
- 描述：模块视图左上角点的高，可为空

bg：

- 类型：字符串	
- 默认值：#BFEFFF
- 描述：背景色，支持grb，rgba，img，#，可为空

shadowColor：

- 类型：字符串	
- 默认值：#CAE1FF
- 描述：折线覆盖的阴影区域的颜色，支持grb，rgba，#，可为空

xAxisGap：

- 类型：数字类型
- 默认值：w/7
- 描述：x轴标记间隔距离，可为空

yAxis：

- 类型：JSON对象
- 默认值：无
- 描述：K线图坐标系y轴配置参数，可为空

内部字段：

```js
{
	max：			//y轴最大值，数字类型，默认10000，可为空
	min：			//y轴最小值，数字类型,不可小于0，默认2000，可为空
	step：          //Y轴步幅，数字类型，默认2000，可为空
}
```

mark：

- 类型：json对象	
- 默认值：见内部字段
- 描述：标注的配置，可为空

内部字段：
```js
{
	colorX: 	//X轴标注的字体颜色，支持rgb，rgba，#，默认696969，可为空
	sizeX： 		//X轴标注的字体大小，数字类型，默认13，可为空
	colorY: 	//Y轴标注的字体颜色，支持rgb，rgba，#，默认696969，可为空
	sizeY： 		//Y轴标注的字体大小，数字类型，默认13，可为空
	dot:    	//josn对象，圆点标注配置，可为空

	内部字段：

	{
	markX:     //圆点x轴标注，字符串，默认日期，可为空
	markY:     //圆点y轴标注，字符串，默认字数，可为空
	colorX:    //圆点x标注颜色，支持rgb，rgba，#，默认696969，可为空
	colorY:    //圆点y标注颜色，支持rgb，rgba，#，默认696969，可为空
	sizeX:     //圆点x标注大小，，默认11，可为空
	sizeY:     //圆点x标注大小，默认11，可为空
    }
}
```

coordLine：

- 类型：字符串	
- 默认值：见内部字段
- 描述：坐标线的配置，可为空

内部字段:

```js
{
	color://坐标线颜色,字符串类型，支持rgb，rgba，#，默认#696969，可为空
	width: //坐标线粗细，数字类型，默认1.0，可为空
	style：    //坐标线类型，dash，solid，默认dash，可为空
}
```

brokenLine：

- 类型：json对象	
- 默认值：见内部字段
- 描述：折线的配置，可为空

内部字段：

```js
{
	color://折线颜色,字符串类型，支持rgb，rgba，#，默认#436eee，可为空
	width: //折线粗细，数字类型，默认2.0，可为空
}
```
node：

- 类型：json对象	
- 默认值：见内部字段
- 描述：结点的配置，可为空

内部字段:

```js
{
	size:  //结点大小，数字类型，默认5.0，可为空
	color：//结点颜色，字符串类型，支持rgb，rgba，#，默认#436eee，可为空
	showBubble: //布尔类型，是否显示点击结点时候的气泡，默认true，可为空
	bubbleBg://气泡背景,字符串类型,支持rgb，rgba，#，img，默认#436eee，可为空
	textColor://气泡字体颜色,字符串类型，支持rgb，rgba，#，默认#436eee，可为空
	textSize://气泡文字大小，数字类型，默认13.0，可为空
	hollow：  //布尔类型，是否为空心圆，默认true，可为空
}
```

datas：

- 类型：数组对象	
- 默认值：无
- 描述：折线的数据信息，可为空

内部字段：

```js
[{	
	mark:     //x轴标注，字符串类型，不可为空
	value:    //标注对应的值，数字类型，在min和max之间，不可为空
}]
```

fixedOn：

- 类型：字符串
- 默认值：当前主窗口的名字
- 描述：将此模块视图添加到指定窗口的名字，可为空

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
    id:         //打开的折线图视图的id
	eventType:  //事件类型，取值范围，nodeClick，scrollLeft，scrollRight
	index：		//点击结点的下标，仅当eventType为nodeClick时有值
}
```

##示例代码

```js
var obj = api.require('brokenLine');
obj.open({
	datas: [{mark:1,value:2500},
			{mark:2,value:3500},
			{mark:3,value:4500},
			{mark:4,value:3500},
			{mark:5,value:7500},
			{mark:6,value:6500},
			{mark:7,value:4500},
			{mark:8,value:5500},
			{mark:9,value:3500},
			{mark:10,value:3000}]
}, function(ret, err){
	if(ret.eventType){
		api.alert({msg:ret.eventType});
    }
});
```

##补充说明

打开线图列表并显示数据

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**reloadData**<div id="2"></div>

刷新指定title的折线数据

reloadData({params}, callback(ret, err))

##params

datas：

- 类型：数组对象	
- 默认值：无
- 描述：折线的数据信息，可为空

内部字段：

```js
[{	
	mark:     //x轴标注，字符串类型，不可为空
	value:    //标注对应的值，数字类型，在min和max之间，不可为空
}]
```

id：

- 类型：数字	
- 默认值：无
- 描述：操作视图的id，不可为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```
{
	status:true           //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:””//错误描述
}
```

##示例代码

```js
var obj = api.require('brokenLine');
obj.reloadData({
	id:1,
	datas: [{mark:1,value:3500},
			{mark:2,value:2500},
			{mark:3,value:5500},
			{mark:4,value:3500},
			{mark:5,value:6500},
			{mark:6,value:4500},
			{mark:7,value:8500},
			{mark:8,value:7500},
			{mark:9,value:9500},
			{mark:10,value:5000}]
}, function(ret, err){
	if(ret.status){
		api.alert({msg:'刷新数据成功'});
    }else{
		api.alert({msg:err.msg});
    }
});
```

##补充说明

刷新指定title的折线的数据

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**appendData**<div id="3"></div>

往现有数据拼接新数据

reloadData({params}, callback(ret, err))

##params

orientation：

- 类型：字符串	
- 默认值：right
- 描述：拼接数据的方向，取值范围right，left，可为空

datas：

- 类型：数组对象	
- 默认值：无
- 描述：折线的数据信息，可为空

内部字段：

```js
[{	
	mark:     //x轴标注，字符串类型，不可为空
	value:    //标注对应的值，数字类型，在min和max之间，不可为空
}]
```

id：

- 类型：数字	
- 默认值：无
- 描述：操作视图的id，不可为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:true           //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:””//错误描述
}
```

##示例代码

```js
var obj = api.require('brokenLine');
obj.appendData({
	id:1,
	datas: [{mark:11,value:3500},
			{mark:12,value:2500},
			{mark:13,value:5500},
			{mark:14,value:3500},
			{mark:15,value:6500},
			{mark:16,value:4500},
			{mark:17,value:8500},
			{mark:18,value:7500},
			{mark:19,value:9500}]
}, function(ret, err){
	if(ret.status){
		api.alert({msg:'拼接数据成功'});
    }else{
		api.alert({msg:err.msg});
    }
});
```

##补充说明

刷新指定title的折线的数据

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**close**<div id="4"></div>

关闭折线图视图

close({params},callback(ret, err))

##params

id：

- 类型：数字	
- 默认值：无
- 描述：操作视图的id，可为空，若为空则关闭所有

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:true           //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```
{
	msg:“”//错误描述
}
```

##示例代码

```js
var obj = api.require('brokenLine');
obj.close(function(ret, err){
	if(ret.status){
		api.alert({msg:'关闭成功'});
    }else{
		api.alert({msg:'error'});
    }
});
```

##补充说明

关闭折线图视图，并从内存里清空

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**hide**<div id="5"></div>

隐藏折线图视图

hide ({params}callback(ret, err))

##params

id：

- 类型：数字	
- 默认值：无
- 描述：操作视图的id，可为空，若为空则隐藏所有

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:true           //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:“”             //错误描述
}
```

##示例代码

```js
var obj = api.require('brokenLine');
obj.hide (function(ret, err){
	if(ret.status){
			api.alert({msg:'隐藏成功'});
	    }else{
			api.alert({msg:'error'});
	    }
});
```

##补充说明

隐藏折线图视图，并没有从内存里清空

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**show**<div id="6"></div>

显示折线图视图

show ({params}callback(ret, err))

##params

id：

- 类型：数字	
- 默认值：无
- 描述：操作视图的id，可为空，若为空则显示所有

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:true           //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:“”             //错误描述
}
```

##示例代码

```js
var obj = api.require('brokenLine');
obj.show (function(ret, err){
		if(ret.status){
			api.alert({msg:'隐藏成功'});
	    }else{
			api.alert({msg:'error'});
	    }
});
```

##补充说明

显示已隐藏的折线图视图

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
