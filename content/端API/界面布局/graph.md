/*
Title: graph
Description: graph
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[reload](#2)

[close](#3)

[show](#4)

[hide](#5)
</div>

#**概述**

graph 底层通过复杂的逻辑和代码实现了一个贝塞尔曲线。可接受用户点击结点事件，开发者可自定义背景、线条、坐标系等等相关 ui 元素的样式和数据源。功能全面，性能强劲。**UIGraph 模块是 graph 模块的优化版，建议使用  [UIGraph](http://docs.apicloud.com/端API/界面布局/UIGraph) 模块，此模块已停止更新。**

![图片说明](/img/docImage/graph.jpg)

#**open**<div id="1"></div>

打开曲线图视图

open({params}, callback(ret, err))

##params

x：

- 类型：数字
- 默认值：15
- 描述：曲线图左上角点坐标，可为空

y：

- 类型：数字
- 默认值：64
- 描述：曲线图左上角点坐标，可为空

w：

- 类型：数字
- 默认值：当前设备屏幕宽减 30
- 描述：曲线图视图的宽,可为空

h：

- 类型：数字
- 默认值：当前设备屏幕的宽减 170
- 描述：曲线图视图的高，可为空

bgColor：

- 类型：字符串
- 默认值：#FFFFFF
- 描述：曲线图视图的背景色，支持 rgb，rgba，#，可为空

coordColor：

- 类型：字符串
- 默认值：#A9A9A9
- 描述：曲线图视图的坐标系颜色，支持 rgb，rgba，#，可为空

markColor：

- 类型：字符串
- 默认值：#000000
- 描述：曲线图视图的坐标系标注颜色，支持 rgb，rgba，#，可为空

lineColor：

- 类型：字符串
- 默认值：#1E90FF
- 描述：曲线颜色，支持 rgb，rgba，#，可为空

bubbleUp：

- 类型：字符串
- 默认值：无
- 描述：点击结点弹出下气泡的背景图，可为空

bubbleDown：

- 类型：字符串
- 默认值：无
- 描述：点击结点弹出上气泡的背景图，可为空

data：

- 类型：数组
- 默认值：无
- 描述：曲线数据，不可为空

内部字段：

```js
[{
	time: '15：00',     //时间点
	data: '50',         // 数据
	isonline: '1'       //保留使用
}]
```

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

- 类型：JSON 对象

内部字段：

```js
{
	orient:           //用户拖动曲线到头（向左或向右或缩小曲线）返回拖动事件，其值分别为：left，right，narrow
}
```

##示例代码

```js
var graph = api.require('graph');
graph.open({
  bubbleUp: 'widget://res/graph_bubble_up.png',
  bubbleDown: 'widget://res/graph_bubble_down.png',
  data: [{
    'time': '12:05',
    'data': '15',
    'isonline': '1'
  }, {
    'time': '13:10',
    'data': '45',
    'isonline': '1'
  }, {
    'time': '14:22',
    'data': '55',
    'isonline': '1'
  }, {
    'time': '15:08',
    'data': '0',
    'isonline': '1'
  }, {
    'time': '16:19',
    'data': '70',
    'isonline': '1'
  }, {
    'time': '17:31',
    'data': '45',
    'isonline': '0'
  }, {
    'time': '12:05',
    'data': '60',
    'isonline': '1'
  }, {
    'time': '13:10',
    'data': '35',
    'isonline': '1'
  }, {
    'time': '14:22',
    'data': '85',
    'isonline': '1'
  }, {
    'time': '15:08',
    'data': '20',
    'isonline': '0'
  }, {
    'time': '16:19',
    'data': '70',
    'isonline': '1'
  }, {
    'time': '17:31',
    'data': '47',
    'isonline': '1'
  }, {
    'time': '17:31',
    'data': '45',
    'isonline': '1'
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

打开曲线图视图

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**reload**<div id="2"></div>
刷新曲线数据

reload({params})

##params

type：

- 类型：字符串类型
- 默认值：reload_all
- 描述：刷新方式：取值范围详见[刷新方式](!Constant)

data：

- 类型：数组
- 默认值：无
- 描述：要刷新的数据，不可为空

内部字段：

```js
[{
	time: '15：00',     //时间点，x轴标记，字符串，不可为空
	data: 50,         // 数据，数字类型，不可为空
	isonline: '1'       //保留使用
}]
```
##示例代码

```js
var array = ;
var graph = api.require('graph');
graph.reload({
	data: [{
    'time': '12:05',
    'data': '15',
    'isonline': '1'
  },{
    'time': '13:10',
    'data': '45',
    'isonline': '1'
  },{
    'time': '14:22',
    'data': '55',
    'isonline': '1'
  },{
    'time': '15:08',
    'data': '0',
    'isonline': '1'
  },{
    'time': '16:19',
    'data': '70',
    'isonline': '1'
  },{
    'time': '17:31',
    'data': '45',
    'isonline': '0'
  },{
    'time': '12:05',
    'data': '60',
    'isonline': '1'
  },{
    'time': '13:10',
    'data': '35',
    'isonline': '1'
  },{
    'time': '14:22',
    'data': '85',
    'isonline': '1'
  },{
    'time': '15:08',
    'data': '20',
    'isonline': '0'
  },{
    'time': '16:19',
    'data': '70',
    'isonline': '1'
  },{
    'time': '17:31',
    'data': '47',
    'isonline': '1'
  },{
    'time': '17:31',
    'data': '45',
    'isonline': '1'
  }]
});
```

##补充说明

刷新曲线数据

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**close**<div id="3"></div>

关闭曲线图视图

close()

##示例代码

```js
var graph = api.require('graph');
graph.close();
```

##补充说明

关闭曲线图视图

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**hide**<div id="4"></div>

隐藏曲线图视图

hide()

##示例代码

```js
var graph = api.require('graph');
graph.hide();
```

##补充说明

隐藏曲线图视图，并没有从内存清空

##可用性

iOS系统，安卓系统

可提供的1.0.1及更高版本

#**show**<div id="5"></div>

显示曲线图视图

show()

##示例代码

```js
var graph = api.require('graph');
graph.show();
```

##补充说明

显示已隐藏的曲线图视图

##可用性

iOS系统，安卓系统

可提供的1.0.1及更高版本

</div>

<div id="const-content">

<div class="outline">
[刷新方式](#1)
</div>

#**刷新方式**<div id="1"></div>

刷新数据的方式，字符串类型

##取值范围：

- append_left		   //往左边拼接数据
- append_right		//往右边拼接数据
- reload_all		    //刷新整条曲线的数据

</div>