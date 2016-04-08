/*
Title: graphHaier
Description: graphHaier
*/
<div class="outline">
[open](#m1)

[close](#m3)

[show](#m4)

[hide](#m5)

[reloadData](#m2)
</div>

#**概述**

graphHaier是一个贝塞尔曲线模块。开发者可自定义背景、线条、坐标系等UI样式和数据源，可监听用户点击结点事件。用于实现数据可视化的功能。

![图片说明](/img/docImage/graphHaier.jpg)

<div id="m1"></div>

#**open**

打开贝塞尔曲线模块

open({params}, callback(ret, err))

##params

rect：

- 类型：JSON对象
- 描述：（可选项）模块的位置及尺寸
- 内部字段：

```js
{
    x: 0,       //（可选项）数字类型；模块左上角的 x 坐标（相对于所属的 Window 或 Frame）；默认：15
    y: 0,       //（可选项）数字类型；模块左上角的 y 坐标（相对于所属的 Window 或 Frame）；默认：64
    w: 320,     //（可选项）数字类型；模块的宽度；默认：所属 Window 或 Frame 的宽度
    h: 220      //（可选项）数字类型；模块的高度；默认：w - 100
}
```

yAxis：

- 类型：JSON对象
- 描述：曲线图的y轴信息
- 内部字段：

```js
{
    max: 80,            //数字类型；y轴最大值
    min: 0,             //数字类型；y轴最小值
    step: 20,           //数字类型；y轴刻度间隔
    unit: '%'          //字符串类型；y轴数据单位
}
```

data：

- 类型：数组
- 描述：曲线关键结点的数据
- 内部字段：

```js
[{
    xAxis: '一月',                //字符串类型；关键结点的x轴数据
    yAxis: [80, 81, 56, 55]      //数组类型；关键结点的y轴数据
},{
    xAxis: '二月',                //字符串类型；关键结点的x轴数据
    yAxis: [70, 81, 56, 55]      //数组类型；关键结点的y轴数据，
}]
```

styles：

- 类型：JSON对象
- 描述：（可选项）模块各部分的样式
- 内部字段：

```js
{
    bg: '#fff',                   //（可选项）字符串类型；曲线图的背景，支持rgb，rgba，#，图片路径（本地路径，fs://，widget://）；默认：'#fff'
    axisColor: '#A9A9A9',         //（可选项）字符串类型；曲线图的坐标轴颜色，支持rgb，rgba，#；默认：'#A9A9A9'
    nodeColor: '#000',            //（可选项）字符串类型；曲线图的结点颜色，支持rgb，rgba，#；默认：'#000'
    nodeSize: 2,                  //（可选项）数字类型；曲线图的结点处小圆圈的半径；默认：2
    lineColor: '#1E90FF',         //（可选项）字符串类型；曲线的颜色，支持rgb，rgba，#；默认：'#1E90FF'
    lineWidth: 1,                 //（可选项）数字类型；曲线条的宽；默认：1
    makeColor: '#000',            //（可选项）字符串类型；标注的字体颜色，支持rgb，rgba，#；默认：'#000'
    makeSize:  16,                //（可选项）数字类型；标注的字体大小，；默认：16
    bubble: {                     //（可选项）JSON对象；点击结点弹出气泡的样式
        bgImg: 'widget://'        //（可选项）字符串类型；点击结点弹出气泡的背景图
        size:  14,                //（可选项）数字类型；点击结点弹出气泡的字体大小，；默认：14
    }
}
```

showNode：

- 类型：布尔
- 描述：（可选项）是否默认显示结点
- 默认值：true

minInterval：

- 类型：数字类型
- 描述：（可选项）坐标系纵线最小间距
- 默认值：(rect -> w)/7.0

maxInterval：

- 类型：数字类型
- 描述：（可选项）坐标系纵线最大间距
- 默认值：minInterval*2.0

fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window

fixed:

- 类型：布尔
- 描述：（可选项）模块是否随所属 Window 或 Frame 滚动
- 默认值：true（不随之滚动）

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    id: 1,                          //数字类型；模块的 id，用于区分模块的多个实例
	eventType: 'reachLeftmost',     //字符串类型；交互事件类型
                                    //取值范围：
                                    //reachLeftmost（拖动曲线图至左边缘）
                                    //reachRightmost（拖动曲线图至右边缘）
                                    //zoomIn（放大曲线图）
                                    //zoomOut（缩小曲线图）
                                    //narrow（缩小曲线图小于模块宽）
    index: 6                        //数字类型；缩放曲线图时，返回缩放中心结点的数据在 data 数组中的索引
}
```

##示例代码

```js
var obj = api.require('graphHaier');
obj.open({
    rect: {
        x: 0,
        y: 0,
        w: 320,
        h: 200
    },
    yAxis: {
        max: 80,
        min: 0,
        step: 20,
        unit: '℃'
    },
    data: [{
        xAxis: '一月',
        yAxis: 15
    },{
        xAxis: '二月',
        yAxis: [65, 59, 80, 81]
    },{
        xAxis: '三月',
        yAxis: 55
    },{
        xAxis: '四月',
        yAxis: 0
    }],
    styles: {
        bg: '#fff',
        axisColor: '#A9A9A9',
        nodeColor: '#000',
        lineColor: '#1E90FF',
        bubble: {
            bgImg: ''
        }
    },
    showNode: true,
    fixedOn: api.frameName,
    fixed: true
}, function(ret, err){
    if(ret){
        alert(JSON.stringify(ret));
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m3"></div>

#**close**

关闭曲线图模块

close({params})

##params

id：

- 类型：数字
- 描述：模块的 id，用于区分模块的多个实例

##示例代码

```js
var obj = api.require('graphHaier');
obj.close({id: 1});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m4"></div>

#**show**

显示曲线图模块

show({params})

##params

id：

- 类型：数字
- 描述：模块的 id，用于区分模块的多个实例

##示例代码

```js
var obj = api.require('graphHaier');
obj.show({id: 1});
```

##可用性

IOS系统，安卓系统

可提供的1.0.1及更高版本

<div id="m5"></div>

#**hide**

隐藏曲线图模块

hide({params})

##params

id：

- 类型：数字
- 描述：模块的 id，用于区分模块的多个实例

##示例代码

```js
var obj = api.require('graphHaier');
obj.hide({id: 1});
```

##可用性

IOS系统，安卓系统

可提供的1.0.1及更高版本

<div id="m2"></div>

#**reloadData**

更新曲线图的数据

reloadData({params})

##params

id：

- 类型：数字
- 描述：模块 id，用于区分多个模块实例

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
    xAxis: '一月',                //字符串类型；关键结点的x轴数据
    yAxis: [80, 81, 56, 55]      //数组类型；关键结点的y轴数据
},{
    xAxis: '二月',                //字符串类型；关键结点的x轴数据
    yAxis: [70, 81, 56, 55]      //数组类型；关键结点的y轴数据，
}]
```

##示例代码

```js
var obj = api.require('graphHaier');
obj.reloadData({
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
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



