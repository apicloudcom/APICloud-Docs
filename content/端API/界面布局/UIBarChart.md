/*
Title: UIBarChart
Description: UIBarChart
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[reloadData](#2)

[close](#3)

[hide](#4)

[show](#5)
</div>

#**概述**

UIBarChart 是一个柱状图模块，可自定义 X、Y 轴样式以及柱子的个数和颜色。本模块可监听左右拖动到头的事件，可向当前数据拼接加载、刷新等操作。同一个页面可以打开多个模块实例，以模块 id 区分。**本模块是 barChart 的优化版**

![图片说明](/img/docImage/barChart.jpg)

#**open**<div id="1"></div>

打开柱状图视图

open({params}, callback(ret, err))

##params

rect：

- 类型：JSON 对象
- 描述：（可选项）模块的位置及尺寸
- 内部字段：

```js
{
    x: 0,   //（可选项）数字类型；模块左上角的 x 坐标（相对于所属的 Window 或 Frame）；默认：0
    y: 0,   //（可选项）数字类型；模块左上角的 y 坐标（相对于所属的 Window 或 Frame）；默认：0
    w: 320, //（可选项）数字类型；模块的宽度；默认：所属的 Window 或 Frame 的宽度
    h: 200  //（可选项）数字类型；模块的高度；默认：w * 2.0/3.0
}
```
yAxis：

- 类型：JSON 对象
- 描述：曲线图的y轴信息
- 内部字段：

```js
{
    max: 50,            //数字类型；y轴最大值
    min: 0,             //数字类型；y轴最小值
    step: 20,           //数字类型；y轴刻度间隔
}
```

data：

- 类型：数组
- 描述：曲线关键结点的数据
- 内部字段：

```js
[{
    xAxis: '一月',                //字符串类型；关键结点的x轴数据
    yAxis: 80                     //数字类型；关键结点的y轴数据
},{
    xAxis: '二月',                //字符串类型；关键结点的x轴数据
    yAxis: 56                     //数字类型；关键结点的y轴数据
}]
```

styles:

- 类型：
- 描述：（可选项）模块视图内元素样式设置
- 默认值：见内部字段
- 内部字段：

```js
{
      yAxis: {              //（可选项）JSON 对象；Y轴样式
          width:30,         //（可选项）数字类型；Y轴宽度，默认：20
          bg: '#B2DFEE',    //（可选项）字符串类型；Y轴背景，支持 rgb、rgba、#、img，默认:'#B2DFEE'
          markColor: '#fff',//（可选项）字符串类型；Y轴标注字体颜色，支持 rgb、rgba、#，默认:'#fff'
          markSize: 12      //（可选项）数字类型；Y轴标注字体大小，默认：12
      },   
      xAxis: {              //（可选项）JSON 对象；X轴样式
          height:30,        //（可选项）数字类型；X轴高度，默认：20
          bg: '#B2DFEE',    //（可选项）字符串类型；X轴背景，支持 rgb、rgba、#、img，默认:'#B2DFEE'
          markColor: '#fff',//（可选项）字符串类型；X轴标注字体颜色，支持 rgb、rgba、#，默认:'#fff'
          markSize: 12      //（可选项）数字类型；X轴标注字体大小，默认：12
      },   
      coordinate: {         //（可选项）JSON 对象；坐标系样式
          bg: '#FCFCFC',    //（可选项）字符串类型；坐标系背景，支持 rgb、rgba、#、img，默认:'#FCFCFC'
      },    
      bar: {                //（可选项）JSON 对象；柱子样式
          width:30,         //（可选项）数字类型；柱子的宽度，默认：20
          bg: '#696969',    //（可选项）字符串类型；柱子的背景色，支持 rgb、rgba、#、img，默认:'#696969'
          tint: '#8DB6CD',  //（可选项）字符串类型；柱子的数据展示色，支持 rgb、rgba、#，默认:'#8DB6CD'
          interval: 16      //（可选项）数字类型；柱子间隔大小，默认：16
      }    
}
```

fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window

fixed:

- 类型：布尔
- 描述：（可选项）模块是否随所属 window 或 frame 滚动
- 默认值：true（不随之滚动）

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：
  
```js
{
 id: 1,                 //数字类型；模块的 id，用于区分模块的多个实例
  eventType: 'show',     //字符串类型；交互事件类型
                        //取值范围：
                        //show（打开模块成功）
                        //click（点击柱状图的柱子的点击事件）
                         //reachLeftmost（拖动柱图至左边缘）
                         //reachRightmost（拖动柱图至右边缘）
  index:                //数字类型；点击柱状图柱子的索引，当 eventType 为 click 时有效
  value:                //数字类型；所点击柱子的值，当 eventType 为 click 时有效
}
```
 
##示例代码

```js
var UIBarChart = api.require('UIBarChart');
UIBarChart.open({
	rect: {
		x: 30,
		y: api.frameHeight / 2 - 170,
		w: api.frameWidth - 60,
		h: 340
	},
	yAxis: {
	    max: 50,            //数字类型；y轴最大值
	    min: 0,             //数字类型；y轴最小值
	    step: 10            //数字类型；y轴刻度间隔
	},
	data: [{
	    xAxis: '一月',                //字符串类型；关键结点的x轴数据
	    yAxis: 80                     //数字类型；关键结点的y轴数据
	},{
	    xAxis: '二月',                //字符串类型；关键结点的x轴数据
	    yAxis: 0                     //数字类型；关键结点的y轴数据
	},{
	    xAxis: '三月',                //字符串类型；关键结点的x轴数据
	    yAxis: 16                     //数字类型；关键结点的y轴数据
	},{
	    xAxis: '四月',                //字符串类型；关键结点的x轴数据
	    yAxis: 36                     //数字类型；关键结点的y轴数据
	},{
	    xAxis: '五月',                //字符串类型；关键结点的x轴数据
	    yAxis: 26                     //数字类型；关键结点的y轴数据
	},{
	    xAxis: '六月',                //字符串类型；关键结点的x轴数据
	    yAxis: 46                     //数字类型；关键结点的y轴数据
	},{
	    xAxis: '七月',                //字符串类型；关键结点的x轴数据
	    yAxis: 66                     //数字类型；关键结点的y轴数据
	},{
	    xAxis: '八月',                //字符串类型；关键结点的x轴数据
	    yAxis: 11                     //数字类型；关键结点的y轴数据
	},{
	    xAxis: '九月',                //字符串类型；关键结点的x轴数据
	    yAxis: 8                     //数字类型；关键结点的y轴数据
	},{
	    xAxis: '十月',                //字符串类型；关键结点的x轴数据
	    yAxis: 56                     //数字类型；关键结点的y轴数据
	},{
	    xAxis: '十一月',                //字符串类型；关键结点的x轴数据
	    yAxis: 61                     //数字类型；关键结点的y轴数据
	},{
	    xAxis: '十二月',                //字符串类型；关键结点的x轴数据
	    yAxis: 35                     //数字类型；关键结点的y轴数据
	}],
	styles: {
	      yAxis: {              //（可选项）JSON 对象；Y轴样式
	          width:30,         //（可选项）数字类型；Y轴宽度，默认：20
	          bg: '#B2DFEE',    //（可选项）字符串类型；Y轴背景，支持 rgb、rgba、#、img，默认:'#B2DFEE'
	          markColor: '#fff',//（可选项）字符串类型；Y轴标注字体颜色，支持 rgb、rgba、#，默认:'#fff'
	          markSize: 12      //（可选项）数字类型；Y轴标注字体大小，默认：12
	      },   
	      xAxis: {              //（可选项）JSON 对象；X轴样式
	          height:30,        //（可选项）数字类型；X轴高度，默认：20
	          bg: '#B2DFEE',    //（可选项）字符串类型；X轴背景，支持 rgb、rgba、#、img，默认:'#B2DFEE'
	          markColor: '#fff',//（可选项）字符串类型；X轴标注字体颜色，支持 rgb、rgba、#，默认:'#fff'
	          markSize: 12      //（可选项）数字类型；X轴标注字体大小，默认：12
	      },   
	      coordinate: {         //（可选项）JSON 对象；坐标系样式
	          bg: '#FCFCFC',    //（可选项）字符串类型；坐标系背景，支持 rgb、rgba、#、img，默认:'#FCFCFC'
	      },    
	      bar: {                //（可选项）JSON 对象；柱子样式
	          width:30,         //（可选项）数字类型；柱子的宽度，默认：20
	          bg: '#696969',    //（可选项）字符串类型；柱子的背景色，支持 rgb、rgba、#、img，默认:'#696969'
	          tint: '#8DB6CD',  //（可选项）字符串类型；柱子的数据展示色，支持 rgb、rgba、#，默认:'#8DB6CD'
	          interval: 16      //（可选项）数字类型；柱子间隔大小，默认：16
	      }    
	},
	fixedOn: api.frameName,
	fixed: false
}, function(ret, err){
    if( ret ){
         alert( JSON.stringify( ret ) );
    }else{
         alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**reloadData**<div id="2"></div>

重新加载数据

reloadData({params}, callback(ret, err))

##params

id：

- 类型：数字
- 描述：模块的 id，用于区分模块的多个实例

type：

- 类型：字符串
- 描述：更新数据的方式
- 默认值：'updateAll'
- 取值范围：
    - prepend（往数据源头部追加数据）
    - append（往数据源尾部追加数据）
    - updateAll（更新所有数据）

data：

- 类型：数组
- 描述：要更新的数据
- 内部字段：

```js
[{
    xAxis: '一月',            //字符串类型；关键结点的x轴数据
    yAxis: 80                //数字类型；关键结点的y轴数据
},{
    xAxis: '二月',            //字符串类型；关键结点的x轴数据
    yAxis: 56                //数字类型；关键结点的y轴数据，
}]
```
##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：
  
  ```js
  {
       status: true,        //布尔类型；数据源是否刷新成功， true|false
       count: 20            //数字类型；刷新数据后总数据量数 
  }
 ```

##示例代码
```js
var UIBarChart = api.require('UIBarChart');
UIBarChart.reloadData({
    id: 1,
    type: 'prepend',
	data: [{
        xAxis: '五月',
        yAxis: 45
    },{
        xAxis: '六月',
        yAxis: 70
    },{
        xAxis: '七月',
        yAxis: 20
    },{
        xAxis: '八月',
        yAxis: 85
    }]
}, function(ret, err){
    if( ret ){
         alert( JSON.stringify( ret ) );
    }else{
         alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**close**<div id="3"></div>

关闭柱状图

close({params})

##params

id：

- 类型：数字
- 描述：模块的 id，用于区分模块的多个实例

##示例代码
```js
var UIBarChart = api.require('UIBarChart');
UIBarChart.close({
    id:1
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**hide**<div id="4"></div>

隐藏柱状图视图

hide({params})

##params

id：

- 类型：数字
- 描述：模块的 id，用于区分模块的多个实例

##示例代码
```js
var UIBarChart = api.require('UIBarChart');
UIBarChart.hide({
    id:1
});
```
##补充说明

隐藏已显示的柱状图视图，并没有从内存里清除

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**show**<div id="5"></div>

显示已隐藏的柱状图视图

show({params})

##params

id：

- 类型：数字
- 描述：模块的 id，用于区分模块的多个实例

##示例代码
```js
var UIBarChart = api.require('UIBarChart');
UIBarChart.show({
    id:1
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本