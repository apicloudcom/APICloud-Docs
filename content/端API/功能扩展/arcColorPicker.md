/*
Title: arcColorPicker
Description: arcColorPicker
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[getColor](#2)

[setColor](#3)

[hide](#4)

[show](#5)

[close](#6)
</div>

#**概述**

arcColorPicker模块封装了一个环形取色器，开发者可自定义样式，设置当前色值，获取拖动指示十六进制色值

![图片说明](/img/docImage/arcColorPicker.jpg)

#**open**<div id="1"></div>

打开环形取值器

open({params}, callback(ret, err))

##params

x：

- 类型：数字
- 默认值：当前设备屏幕宽除以二
- 描述：取色器视图的中心点坐标，可为空

y：

- 类型：数字
- 默认值：200
- 描述：取色器视图中心点的坐标，可为空

r：

- 类型：数字
- 默认值：128
- 描述：环形取色器外环半径，可为空

gradients：

- 类型：数组
- 默认值：['#000000','#fff']
- 描述：顺时针渐变色值组成的数组，可为空

slider：

- 类型：字符串
- 默认值：#fff
- 描述：滑块背景，支持rgb,rgba,#,img,可为空，为空时滑块背景透明

style：

- 类型：json对象
- 默认值：内部字段
- 描述：环形选值器样式配置，可为空

内部字段：

```js
{
	innerR：//预览区半径占r的百分比，数字类型，默认25，取值范围0-100可为空
	innerRwidth://预览区灰色环宽占innerR的百分比，数字类型，默认3，取值范围0-100，可为空
	ringWidth：//环形取色器环宽占r的百分比，数字类型，默认25，取值范围0-100，可为空
	intervalAngle://环形取值器下环缺口弧度大小，数字类型，默认20,可为空，取值范围0-180
}
```

currentColor：

- 类型：字符串
- 默认值：gradients的第一个元素
- 描述：环形取色器当前颜色值，仅支持#，可为空

fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window


fixed：

- 类型：布尔
- 默认值：true
- 描述：是否将模块视图固定到窗口上，不跟随窗口上下滚动，可为空


##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	touchCancel:      //是否是滑动结束事件，布尔类型，若为true则表示手指离开事件
	color：//色值的十六进制表示，字符串类型
}
```

##示例代码

```js
var arcColorPicker = api.require('arcColorPicker');
arcColorPicker.open({
    gradients : [ 
		'#FF0005',
		'#FF00F0'
	],
	fixedOn: api.frameName
},function( ret, err ){		
    if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**getColor**<div id="2"></div>

获取取色器当前的值

getColor(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	color：//色值的十六进制表示，字符串类型
}
```

##示例代码

```js
var arcColorPicker = api.require('arcColorPicker');
arcColorPicker.getColor(function( ret, err ){		
    if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setColor**<div id="3"></div>

设置取色器的色值

setColor({params})

##params

color：

- 类型：字符串
- 默认值：无
- 描述：要设置的色值，可为空

##示例代码

```js
var arcColorPicker = api.require('arcColorPicker');
arcColorPicker.setColor({
    color: '#6757dj'
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**hide**<div id="4"></div>

隐藏取色器模块视图

hide(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:      //操作是否成功，布尔类型
}
```

##示例代码

```js
var arcColorPicker = api.require('arcColorPicker');
arcColorPicker.hide();
```

##补充说明

隐藏显示的模块视图，并没有从内存清除

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**show**<div id="5"></div>

显示已隐藏的取色器模块视图

show(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:      //操作是否成功，布尔类型
}
```

##示例代码

```js
var arcColorPicker = api.require('arcColorPicker');
arcColorPicker.show();
```

##补充说明

显示已隐藏的模块视图

可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**close**<div id="6"></div>

关闭取色器

close(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:      //操作是否成功，布尔类型
}
```

##示例代码

```js
var arcColorPicker = api.require('arcColorPicker');
arcColorPicker.close();
```

##补充说明

从内存里清除

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
