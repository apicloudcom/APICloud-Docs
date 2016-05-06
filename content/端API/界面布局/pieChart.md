/*
Title: pieChart
Description: pieChart
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

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

open({params}, callback(ret, err))

##params

x：

- 类型：数字
- 描述：（可选项）圆心坐标
- 默认值：0

y：

- 类型：数字
- 描述：（可选项）圆心坐标
- 默认值：100

radius：

- 类型：数字
- 描述：（可选项）圆半径
- 默认值：当前屏幕宽的1/4

center：

- 类型：JSON 对象
- 描述：（可选项）饼形图中间标题样式设置
- 默认值：见内部字段
- 内部字段：

```js
{
    r:’’,           //（可选项）数字类型；中间圆圈的半径；默认：radius/3.0
    bg:’’           //（可选项）字符串类型；中间圆背景颜色，支持 rgb、rgba、# ；默认：#fff
    title：         //（可选项）字符串类型；饼图中间的说明文字，默认：标题 
    titleColor:     //（可选项）字符串类型；标题的颜色，支持 rgb、rgba、#；默认：#000000
    titleSize       //（可选项）数字类型；标题的字体大小；默认：12
    subTitle：      //（可选项）字符串类型；饼图中间的说明文字；默认：子标题
    subTitleColor   //（可选项）字符串类型；子标题的颜色，支持 rgb、rgba、#；默认：#696969
    subTitleSize    //（可选项）数字类型；子标题的字体大小；默认：12
}
```

elements：

- 类型：数组
- 描述：模块字典对象组成的数组
- 内部字段：

```js
[{
    value:     //数字类型；本部分的数值大小
    color:     //字符串类型；本部分颜色，支持 rgb、rgba、# 
    title：    //（可选项）字符串类型；单元格显示的标题，若不传则显示百分比，若传空字符串则显示空字符串
    titleColor//（可选项）字符串类型；标题的颜色，支持 rgb、rgba、#；默认：#ffffff
    titleSize //（可选项）数字类型；标题的字体大小；默认：12
}]
```

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
    eventType:       //字符串类型；回调事件类型，取值范围如下：
                        rotation//拖动旋转事件
                        click   //点击旋转事件，点击色块，该色块旋转到0度
                        open    //打开事件
    index:           //数字类型；返回饼图0度（圆形最下端）位置的模块的索引值
    value:           //数字类型；返回饼图0度（圆形最下端）位置的模块的值
    percent:         //数字类型；返回饼图0度（圆形最下端）位置的模块的百分比值
    id:              //数字类型；返回饼图视图的id
}
```

##示例代码

```js
var pieChart = api.require('pieChart');
pieChart.open({
      x: api.frameWidth / 2,
      y:  api.frameHeight / 2,
      radius: 100,
      center:{
	      title: '标题',
	      subTitle: '子标题'
      },
      elements: [{
            value: 15, 
            color: '#FF6600'
      },{
            value: 15, 
            color: '#660099'
      },{
            value: 15, 
            color: '#FF33FF'
      },{
            value: 15, 
            color: '#66CCFF'
      },{
            value: 15, 
            color: '#00CCFF'
      }],
	fixedOn: api.frameName,
	fixed: false
}, function(ret, err) {
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

刷新展示数据

close({params}, callback(ret, err))

##params

id：

- 类型：数字
- 描述：操作的视图的id

elements：

- 类型：数组
- 描述：模块字典对象组成的数组
- 内部字段：

```js
[{
    value:       //数字类型；组成部分的大小
    color:       //字符串类型；组成部分的颜色值 ，支持 rgb，rgba，# 
    title：      //（可选项）字符串类型；单元格显示的标题，若为空则显示百分比
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
var pieChart = api.require('pieChart');
pieChart.reloadData({
     id: 1,
     elements: [{
            value: 15, 
            color: '#FF6600'
      },{
            value: 15, 
            color: '#660099'
      },{
            value: 15, 
            color: '#FF33FF'
      },{
            value: 15, 
            color: '#66CCFF'
      },{
            value: 15, 
            color: '#00CCFF'
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

可提供的1.0.1及更高版本

#**serFrame**<div id="3"></div>

重设模块视图的位置大小

serFrame({params})

##params

id：

- 类型：数字
- 描述：操作的视图的id

x：

- 类型：数字
- 描述：（可选项）圆心坐标
- 默认值：原值

y：

- 类型：数字
- 描述：（可选项）圆心坐标
- 默认值：原值

radius：

- 类型：数字
- 描述：（可选项）圆半径
- 默认值：原值

anim：

- 类型：布尔
- 默认值：false
- 描述：（可选项）改变模块视图大小时是否添加变化过程的动画

##示例代码

```js
var pieChart = api.require('pieChart');
pieChart.setFrame({
    id: 1,
  	x: 10,
  	y: 300,
  	anim: true
});
```

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

#**close**<div id="4"></div>

关闭饼图

close({params})

##params

id：

- 类型：数字
- 描述：要关闭的饼图的id

##示例代码

```js
var pieChart = api.require('pieChart');
pieChart.close({
    id: 1
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**hide**<div id="5"></div>

隐藏饼图

hide({params})

##params

id：

- 类型：数字
- 描述：要隐藏的饼图的id

##示例代码

```js
var pieChart = api.require('pieChart');
pieChart.hide({
    id: 1
});
```

##补充说明

隐藏饼形图，并没有从内存里清除

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

#**show**<div id="6"></div>

显示已隐藏的饼形图

show({params})

##params

id：

- 类型：数字
- 描述：要显示的饼图的id

##示例代码

```js
var pieChart = api.require('pieChart');
pieChart.show({
    id: 1
});
```

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本