/*
Title: UILineChart
Description: UILineChart
*/

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

UILineChart 模块可用于生成折线图(K线图)视图，并支持多条折线。开发者可自定义 X、Y 轴样式以及折线的个数和颜色。本模块还可监听左右拖动到头的事件，可向当前数据拼接加载、刷新等操作。同一个页面可以打开多个模块实例，以模块 id 区分。**本模块是 lineChart 的优化版**

![图片说明](/img/docImage/lineChart.jpg)

#**open**<div id="1"></div>

打开折线图视图

open({params}, callback(ret, err))

##params

rect：

- 类型：JSON 对象
- 描述：（可选项）模块的位置及尺寸
- 默认值：见内部字段
- 内部字段：

```js
{
    x: 0,                              //（可选项）数字类型；模块左上角的 X 坐标（相对于所属的 Window 或 Frame）；默认：0
    y: 0,                              //（可选项）数字类型；模块左上角的 Y 坐标（相对于所属的 Window 或 Frame）；默认：0
    w: 320,                            //（可选项）数字类型；模块的宽度；默认：所属的 Window 或 Frame 的宽度
    h: 300                             //（可选项）数字类型；模块的高度；默认：w-20
}
```
xAxis：

- 类型：JSON 对象
- 描述：折线图的 X 轴信息
- 默认值：见内部字段
- 内部字段：

```js
{
    indexs:['一月','二月','三月'],      //字符串数组类型；X 轴标注
    screenXcount:7                    //（可选项）数字类型；X 轴标注在每屏内的显示个数；默认：7
}
```
yAxis：

- 类型：JSON 对象
- 描述：折线图的 Y 轴信息
- 默认值：见内部字段
- 内部字段：

```js
{
    max: 1000,                         //数字类型；Y 轴最大值；可为负值，需要大于 min
    min: -200,                         //数字类型；Y 轴最小值；可为负值，需要小于 max
    step: 200,                         //数字类型；Y 轴刻度间隔
    base: 300                          //数字类型；基准线对应的 Y 轴坐标，当值大于 max 或小于 min 时不显示
}
```

datas：

- 类型：数组类型
- 描述：多条折线关键结点数据的数组
- 默认值：见内部字段
- 内部字段：

```js
[
    [200,-100,100,0,50],               //数字数组；一条折线的结点数据数组
                                       //数组的值在绘图时会对应到 Y 轴
                                       //数据项按顺序对应 X 轴的每个结点

    [-200,100,-100,0,-50]              //（可选项）数字数组；这是另一条折线的结点数据数组
]
```

styles:

- 类型：JSON 对象
- 描述：模块视图内元素样式设置
- 默认值：见内部字段
- 内部字段：

```js
{
    xAxis: {                           //（可选项）JSON 对象；X 轴样式
        bg: '#B2DFEE',                 //（可选项）字符串类型；X 轴背景，支持 rgb、rgba、#；默认:'#B2DFEE'
        markColor: '#888',             //（可选项）字符串类型；X 轴标注字体颜色，支持 rgb、rgba、#；默认:'#848484'
        markSize: 12                   //（可选项）数字类型；X 轴标注字体大小；默认：12
    },
    yAxis: {                           //（可选项）JSON 对象；Y 轴样式
        bg: '#B2DFEE',                 //（可选项）字符串类型；Y 轴背景，支持 rgb、rgba、#；默认:'#B2DFEE'
        markColor: '#888',             //（可选项）字符串类型；Y 轴标注字体颜色，支持 rgb、rgba、#；默认:'#848484'
        markSize: 12                   //（可选项）数字类型；Y 轴标注字体大小；默认：12
    },
    coordinate: {                      //（可选项）JSON 对象；坐标系样式
        bg: '#fcfcfc',                 //（可选项）字符串类型；坐标系背景，支持 rgb、rgba、#、img；默认:'#fcfcfc'
        color:'#cacaca',               //（可选项）字符串类型；坐标系网格线颜色，支持 rgb、rgba、#；默认:'#cacaca'
        baseColor:'#bbb',            //（可选项）字符串类型；坐标系基准线颜色，支持 rgb、rgba、#；默认:'#bbb'
    },
    colors:['#800080','#7FFFAA']       //（可选项）字符串类型数组；多条折线的颜色，支持 rgb、rgba、#；默认:['#cb3d1b','#f6a800','#fff100','#00a13f','#007db0','#142a8c','#a51466']
                                       //显示时将按照 datas 内对应的顺序设置颜色
}
```

fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window

fixed:

- 类型：布尔
- 描述：（可选项）模块是否随所属 Window 或 Frame 滚动
- 默认值：true（不随之滚动）

##callBack(ret)

ret：

- 类型：json对象
- 内部字段：
  
```js
{
    id: 1,                             //数字类型；模块的 id，用于区分模块的多个实例
    eventType: 'show',                 //字符串类型；交互事件类型
                                       //取值范围：
                                       //show（打开模块成功）
                                       //click（折线图结点的点击事件）

    lineIndex: 0,                      //数字类型；所点击结点所在折线在 datas 中的索引；当 eventType 为 click 时有效
    nodeIndex: 0,                      //数字类型；所点击结点所在折线数据数组中的索引；当 eventType 为 click 时有效
    value: 100                         //数字类型；所点击结点对应的 Y 轴的值；当 eventType 为 click 时有效
}
```
 
##示例代码

```js
var UILineChart = api.require('UILineChart');
UILineChart.open({
    rect: {
        x: 0,
        y: 64,
        w: 320,
        h: 300
    },
    xAxis: {
        indexs: ['一月', '二月', '三月', '四月', '五月', '六月', '七月', '八月', '九月', '十月', '十一月', '十二月', '一月'], //字符串数组类型；X 轴标注
        screenXcount: 7                //（可选项）数字类型；X 轴标注在每屏内的显示个数；默认：7
    },
    yAxis: {
        max: 1000,                     //数字类型；Y 轴最大值；可为负值，需要大于 min
        min: -1000,                    //数字类型；Y 轴最小值；可为负值，需要小于 max
        step: 200,                     //数字类型；Y 轴刻度间隔
        base: 0                        //数字类型；基准线对应的 Y 轴坐标，当值大于 max 或小于 min 时不显示
    },
    datas: [
        [200,-100,100,0,50],           //数字数组；一条折线的结点数据数组
                                       //数组的值在绘图时会对应到 Y 轴
                                       //数据项按顺序对应 X 轴的每个结点

        [-200,100,-100,0,-50]          //数字数组；这是另一条折线的结点数据数组
    ],
    styles: {
        xAxis: {                       //（可选项）JSON 对象；X 轴样式
            bg: '#b2dfee',             //（可选项）字符串类型；X 轴背景，支持 rgb、rgba、#；默认:'#b2dfee'
            markColor: '#888',         //（可选项）字符串类型；X 轴标注字体颜色，支持 rgb、rgba、#；默认:'#848484'
            markSize: 12               //（可选项）数字类型；X 轴标注字体大小；默认：12
        },
        yAxis: {                       //（可选项）JSON 对象；Y 轴样式
            bg: '#b2dfee',             //（可选项）字符串类型；Y 轴背景，支持 rgb、rgba、#；默认:'#b2dfee'
            markColor: '#888',         //（可选项）字符串类型；Y 轴标注字体颜色，支持 rgb、rgba、#；默认:'#848484'
            markSize: 12               //（可选项）数字类型；Y 轴标注字体大小；默认：12
        },
        coordinate: {                  //（可选项）JSON 对象；坐标系样式
            bg: '#fcfcfc',             //（可选项）字符串类型；坐标系背景，支持 rgb、rgba、#、img；默认:'#fcfcfc'
            color: '#cacaca',          //（可选项）字符串类型；坐标系网格线颜色，支持 rgb、rgba、#；默认:'#cacaca'
            baseColor: 'bbb',       //（可选项）字符串类型；坐标系基准线颜色，支持 rgb、rgba、#；默认:'#bbb'
        },
        colors: ['#800080','#7FFFAA']  //（可选项）字符串类型数组；多条折线的颜色，支持 rgb、rgba、#；默认:['#cb3d1b','#f6a800','#fff100','#00a13f','#007db0','#142a8c','#a51466']
                                       //显示时将按照 datas 内对应的顺序设置颜色
    },
    fixedOn: api.frameName,
    fixed: false
},function( ret, err ){
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

reloadData({params},callback(ret))

##params

id：

- 类型：数字
- 描述：模块的 id，用于区分模块的多个实例

lineIndexs：

- 类型：数字数组
- 描述：需要更新的折线索引数组，索引对应 open 函数中设置的参数 datas 的索引值
- 默认值：从 0 到 datas.length 的整数数组

datas：

- 类型：数字数组
- 描述：要更新的数据数组
- 内部字段：

```js
[
    [200,-100,100,0,50],               //数字数组；一条折线的结点数据数组
                                       //数组的值在绘图时会对应到 Y 轴
                                       //数据项按顺序对应 X 轴的每个结点

    [-200,100,-100,0,-50]              //数字数组；这是另一条折线的结点数据数组
]
```
##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：
  
```js
{
    status: true                       //布尔类型；数据源是否刷新成功， true|false
}
```

##示例代码
```js
var UILineChart = api.require('UILineChart');
UILineChart.reloadData({
    id: 1,
    lineIndexs: [0, 1],                //（可选项）数字数组；需要更新的折线索引数组，索引对应 open 函数中设置的参数 datas 的索引值；默认：从 0 到 datas.length 的整数数组
    datas:[
        [200,-100,100,0,50],           //数字数组；一条折线的结点数据数组
                                       //数组的值在绘图时会对应到 Y 轴
                                       //数据项按顺序对应 X 轴的每个结点

        [-200,100,-100,0,-50]          //数字数组；这是另一条折线的结点数据数组
    ]
},function(ret){
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

关闭折线图

close(params)

##params

id：

- 类型：数字
- 描述：模块的 id，用于区分模块的多个实例

##示例代码
```js
var UILineChart = api.require('UILineChart');
UILineChart.close({
    id:1
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**hide**<div id="4"></div>

隐藏折线图视图

hide(params)

##params

id：

- 类型：数字
- 描述：模块的 id，用于区分模块的多个实例

##示例代码
```js
var UILineChart = api.require('UILineChart');
UILineChart.hide({
    id:1
});
```
##补充说明

隐藏已显示的折线图视图，并没有从内存里清除

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**show**<div id="5"></div>

显示已隐藏的折线图视图

show(params)

##params

id：

- 类型：数字
- 描述：模块的 id，用于区分模块的多个实例

##示例代码
```js
var UILineChart = api.require('UILineChart');
UILineChart.show({
    id:1
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本