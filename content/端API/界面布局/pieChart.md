/*
Title: pieChart
Description: pieChart
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[reloadData](#2)

[setFrame](#3)

[close](#4)

[hide](#5)

[show](#6)
</div>

#**概述**

pieChart是一个饼图数据展示控件，可识别手势转动该饼图，旋转动画结束返回特定位置的数据库的下标。支持开发者自定义数据块样式

![图片说明](/img/docImage/pieChart.jpg)

#**open**<div id="1"></div>

打开饼图视图

open({params},callback)

##params

<del>id：</del>

- <del>类型：数字</del>
- <del>默认值：无</del>
- <del>描述：视图的id，根据此id删除此视图，可为空</del>

x：

- 类型：数字
- 默认值：0
- 描述：（可选项）圆心坐标

y：

- 类型：数字
- 默认值：100
- 描述：（可选项）圆心坐标

radius：

- 类型：数字
- 默认值：当前屏幕宽的1/4
- 描述：（可选项）圆半径

<del>title：</del>

- <del>类型：字符串</del>
- <del>默认值：中标题</del>
- <del>描述：（可选项）饼图中间的说明文字</del>

<del>subTitle：</del>

- <del>类型：字符串</del>
- <del>默认值：子标题</del>
- <del>描述：（可选项）饼图中间的说明文</del>

center：

- 类型：json对象
- 默认值：见内部字段
- 描述：（可选项）饼形图中间标题样式设置
- 内部字段：

```js
{
    r:’’,           //（可选项）中间圆圈的半径，数字类型 ，默认radius/3.0    bg:’’           //（可选项）中间圆背景颜色 ，支持rgb，rgba，# ，默认#ffffff    title：         //（可选项）饼图中间的说明文字，字符串类型，默认：标题     titleColor:     //（可选项）标题的颜色，支持rgb、rgba、#，默认#000000    titleSize       //（可选项）标题的字体大小，数字类型，默认12    subTitle：      //（可选项）饼图中间的说明文字，字符串类型，默认：子标题    subTitleColor   //（可选项）子标题的颜色，支持rgb、rgba、#，默认#696969    subTitleSize    //（可选项）子标题的字体大小，数字类型，默认12
}
```

elements：

- 类型：数组
- 默认值：无
- 描述：模块字典对象组成的数组
- 内部字段：

```js
[{
    value:     //本部分的大小，数字类型     color:     //颜色值 ，支持rgb，rgba，#     title：    //（可选项）单元格显示的标题，字符串类型，若不传则显示百分比，若传空字符串则显示空字符串    titleColor//（可选项）标题的颜色，支持rgb、rgba、#，默认#ffffff    titleSize //（可选项）标题的字体大小，数字类型，默认12
}]
```

fixedOn：

- 类型：字符串
- 默认值：当前主窗口的名字
- 描述：（可选项）将此模块视图添加到指定窗口的名字

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    eventType:       //回调事件类型，字符串类型，取值范围如下：
                        rotation//拖动旋转事件
                        click   //点击旋转事件，点击色块，该色块旋转到0度
                        open    //打开事件
    index:           //返回饼图0度（圆形最下端）位置的模块的index
    percent:         //返回饼图0度（圆形最下端）位置的模块的百分比
    id:              //返回饼图视图的id
}
```

##示例代码

```js
var array = new Array();
array[0] = {value: 15, color: '#FF6600'};
array[1] = {value: 15, color: '#660099'};
array[2] = {value: 15, color: '#FF33FF'};
array[3] = {value: 15, color: '#66CCFF'};
array[4] = {value: 15, color: '#00CCFF'};
var obj = api.require('pieChart');
obj.open({
      x: 200,
      y: 250,
      radius: 100,
      title: '标题',
      subTitle: '子标题',
      elements: array
}, function(ret, err) {
      api.alert({
            msg:ret.index+ret.percent
      });
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**reloadData**<div id="2"></div>

刷新展示数据

close({params})

##params

id：

- 类型：数字
- 默认值：无
- 描述：操作的视图的id

elements：

- 类型：数组
- 默认值：无
- 描述：（可选项）模块字典对象组成的数组，可为空，为空则不刷新数据
- 内部字段：

```js
[{
    value:       //组成部分的大小    color:       //组成部分的颜色值 ，支持rgb，rgba，#     title：      //（可选项）单元格显示的标题，字符串类型，可为空，若为空则显示百分比
}]
```
##示例代码

```js
var obj = api.require('barChart');obj.reloadData({     parts:[{value:'2',color:'#FF6600'},     {value:'2',color:'#660099'},     {value:'2',color:'#FF33FF'},     {value:'2',color:'#66CCFF'},     {value:'2',color:'#00CCFF'}]},function(ret,err){   api.alert({msg:ret.index+ret.id});});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

#**serFrame**<div id="3"></div>

重设模块视图的位置大小

serFrame({params})

##params

id：

- 类型：数字
- 默认值：无
- 描述：操作的视图的id

x：

- 类型：数字
- 默认值：原值
- 描述：（可选项）圆心坐标

y：

- 类型：数字
- 默认值：原值
- 描述：（可选项）圆心坐标

radius：

- 类型：数字
- 默认值：原值
- 描述：（可选项）圆半径

anim：

- 类型：布尔
- 默认值：false
- 描述：（可选项）改变模块视图大小时是否添加变化过程的动画

##示例代码

```js
var obj = api.require('barChart');obj.setFrame({x:10,w:300});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

#**close**<div id="4"></div>

关闭饼图

close({params})

##params

id：

- 类型：数字
- 默认值：无
- 描述：要关闭的饼图的id

##示例代码

```js
var obj = api.require('pieChart');
obj.close({
    id:1
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**hide**<div id="5"></div>

隐藏饼图

hide({params})

##params

id：

- 类型：数字
- 默认值：无
- 描述：要隐藏的饼图的id

##示例代码

```js
var obj = api.require('pieChart');
obj.hide({
    id:1
});
```

##补充说明

隐藏饼形图，并没有从内存里清除

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

#**show**<div id="6"></div>

显示饼图

show({params})

##params

id：

- 类型：数字
- 默认值：无
- 描述：要显示的饼图的id

##示例代码

```js
var obj = api.require('pieChart');
obj.show({
    id:1
});
```

##补充说明

显示已隐藏的饼形图

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本