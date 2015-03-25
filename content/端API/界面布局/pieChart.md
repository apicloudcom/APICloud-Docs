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

[close](#2)

[hide](#3)

[show](#4)
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
- 描述：圆心坐标，可为空

y：

- 类型：数字
- 默认值：100
- 描述：圆心坐标，可为空

radius：

- 类型：数字
- 默认值：当前屏幕宽的1/4
- 描述：圆半径，可为空

title：

- 类型：字符串
- 默认值：中间标题
- 描述：饼图中间的说明文字，可为空

subTitle：

- 类型：字符串
- 默认值：中间子标题
- 描述：饼图中间的说明文，可为空

elements：

- 类型：数组
- 默认值：无
- 描述：模块字典对象组成的数组，不能为空

内部字段：

```js
[{
    value:’’,		//大小，不能为空
    color:’’		//颜色值，支持rgb，rgba，#，不能为空
}]
```

fixedOn：

- 类型：字符串
- 默认值：当前主窗口的名字
- 描述：将此模块视图添加到指定窗口的名字，可为空

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

##callback(ret, err)
ret：

- 类型：JSON对象

内部字段：

```js
{
    index:           //返回饼图0度位置的模块的index
    percent:         //返回饼图0度位置的模块的百分比
    id:              //返回饼图视图的id
}
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**close**<div id="2"></div>

关闭饼图

close({params})

##params

id：

- 类型：数字
- 默认值：无
- 描述：要关闭的饼图的id，不能为空

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

#**hide**<div id="3"></div>

隐藏饼图

hide({params})

##params

id：

- 类型：数字
- 默认值：无
- 描述：要隐藏的饼图的id，不能为空

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

#**show**<div id="4"></div>

显示饼图

show({params})

##params

id：

- 类型：数字
- 默认值：无
- 描述：要显示的饼图的id，不能为空

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