/*
Title: arcProgress
Description: arcProgress
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[close](#2)

[setValue](#3)
</div>

#**概述**

arcProgress是一个弧形进度条，包括环形、扇形、类月牙形三种样式，开发者可以自定义进度色和背景色。此模块动画流畅，原生实现效果炫酷，有效的解决了网页画圆会有锯齿的问题

![图片说明](/img/docImage/arcProgress.jpg)

#**open**<div id="1"></div>

打开圆形进度条

open({params}, callback(ret, err))

##params

type：

- 类型：字符串类型
- 默认值：annular
- 描述：进度视图类型，取值范围[进度条类型](!Constant),可为空

centerX：

- 类型：数字
- 默认值：100
- 描述：视图中心点坐标，可为空

centerY：

- 类型：数字
- 默认值：100
- 描述：视图中心点坐标，可为空

radius：

- 类型：数字
- 默认值：60
- 描述：视图圆半径，可为空

bgColor：

- 类型：字符串
- 默认值：#C0C0C0
- 描述：进度背景色，可为空

pgColor：

- 类型：字符串
- 默认值：#2e8b57
- 描述：进度色，可为空

loopWidth：

- 类型：数字
- 默认值：3
- 描述：当类型为环形进度条时，此参数表上环的宽度。若为其它类型，则此参数无用可为空

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

- 类型：JSON对象

内部字段：

```js
{
	id:           //打开圆形进度条的id
}
```

##示例代码

```js
var arcProgress = api.require('arcProgress');
arcProgress.open({
    type: 1,
    centerX: api.frameWidth / 6 * (2 * 1  + 1),
    centerY: api.frameHeight / 2,
    radius: api.frameWidth / 6,
    bgColor: '#87c0ed',
    pgColor: '#325570',
    fixedOn: api.frameName
},function(ret,err){
	setValue( { id: ret.id, value: 0 } )
});
function setValue( obj ){
	if( obj.value == 100 ){ obj.value = 0; } 
	setTimeout(function(){
		arcProgress.setValue({
			id: obj.id,
			value: ++obj.value
		});
		setValue( obj )
	},100);
}
```
##补充说明

打开圆形进度视图

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**close**<div id="2"></div>

关闭圆形进度视图

close({params})

##params

id：

- 类型：数字
- 默认值：无
- 描述：要关闭的视图的id，若为空，则关闭全部

##示例代码

```js
    var arcProgress = api.require('arcProgress');
    arcProgress.close({
        id:1
    });
```

##补充说明

关闭视图

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setValue**<div id="3"></div>

设置进度值

setValue({params})

##params

id：

- 类型：数字
- 默认值：无
- 描述：要设置视图的id，不可为空

value：

- 类型：数字
- 默认值：0
- 描述：设置的值，可为空

##示例代码

```js
var arcProgress = api.require('arcProgress');
arcProgress.setValue({
    id: 1,
    value: 50
});
```

##补充说明

设置指定id的视图的进度值

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

</div>
<div id="const-content">

<div class="outline">
[进度条类型](#1)
</div>

#**进度条类型**<div id="1"></div>

进度条类型，字符串类型

##取值范围：

- annular		//环形
- sector		//扇形
- crescent		//月牙形

</div>