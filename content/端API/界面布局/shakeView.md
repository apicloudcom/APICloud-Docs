/*
Title: shakeView
Description: shakeView
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[shake](#2)

[hide](#3)

[show](#4)

[close](#5)
</div>

#**概述**

shakeView封装了一个可供开发者自定义的摇一摇界面，包括动画方向，震动，声音等摇一摇时特定的效果，都可自定义。使用此模块有效的解决了前端实现摇一摇动画不流畅问题

![图片说明](/img/docImage/shakeView.jpg)

#**open**<div id="1"></div>

打开摇一摇视图

open({params})

##params

x：

- 类型：数字
- 默认值：0
- 描述：视图左上角点坐标，可为空

y：

- 类型：数字
- 默认值：0
- 描述：视图左上角点坐标，可为空

w：

- 类型：数字
- 默认值：当前设备屏幕宽
- 描述：视图的宽度，可为空

h：

- 类型：数字
- 默认值：w
- 描述：视图高度，可为空

type：

- 类型：字符串
- 默认值：up_down
- 描述：摇一摇视图类型，取值范围见[摇一摇类型常量](!Constant)，可为空

anim：

- 类型：json对象
- 默认值：无
- 描述：视图动画的参数配置，可为空

内部字段：

```js
{
	time:           //动画持续时间，数字，默认3.0秒，可为空
	sound:          //摇动后的音效文件路径，字符串，可为空
	isShake:        //是否添加手机震动效果，布尔值，默认false，可为空   
	percent：        //裂开距离占摇动视图的百分比，数字类型，默认50，可为空  
}
```

img：

- 类型：json对象
- 默认值：无
- 描述：视图界面图片配置，可为空

内部字段：

```js
{
	leftUp:           //左边（上面）的图片路径，字符串类型，默认灰色界面可为空
	rightDown:        //右边（下面）的图片路径，字符串类型，默认灰色界面可为空
	bg:               //背景图片路径，字符串类型，默认绿色面板，可为空
	shake：           //摇动效果动画时摇动的图片，可为空。当type为up_down或left_right时，忽略此参数
}
```

fixedOn：

- 类型：字符串
- 默认值：当前窗口名
- 描述：将模块视图添加到指定窗口名，可为空

fixed:
- 类型：布尔
- 默认值：true
- 描述：是否将模块视图固定到窗口上，不跟随窗口上下滚动，可为空

##示例代码

	var obj = api.require('shakeView');
	obj.open();

##补充说明

打开摇一摇视图

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**shake**<div id="2"></div>

触发摇一摇事件

shake({params},callback(ret,err))

##params

anim：

- 类型：json对象
- 默认值：无
- 描述：视图动画的参数配置，可为空

内部字段：

```js
{
	time:           //动画持续时间，数字，默认3.0秒，可为空
	sound:          //摇动后的音效文件路径，字符串，可为空
	isShake:        //是否添加手机震动效果，布尔值，默认false，可为空
	percent：        //裂开距离占摇动视图的百分比，数字类型，默认50，可为空
}
```

##callback(ret,err)

回调摇一摇动画结束事件

##示例代码

	var obj = api.require('shakeView');
	obj.shake();

##补充说明

触发摇一摇事件

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**hide**<div id="3"></div>

隐藏视图

hidd()

##示例代码

	var obj = api.require('shakeView');
	obj.hide();

##补充说明

隐藏视图，只是移除到屏幕之外，还在内存里没有清除

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**show**<div id="4"></div>

显示视图

show()

##示例代码
```js
var obj = api.require('shakeView');
obj.open({
     type:'up_down',
     x:0,
     y:64,
     w:320,
     h:300,
     anim:{
         time:3,
         isShake:"true"
     },
     img:{
         leftUp:"widget://image/ak2.png",
         rightDown:"widget://image/ak5.png",
         bg:"widget://image/ak6.png"
     }
});
```

##补充说明

显示视图，从屏幕外移动到屏幕内

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**close**<div id="5"></div>

关闭视图

close()

##示例代码

```js
	var obj = api.require('shakeView');
	obj.close();
```

##补充说明

关闭视图，意味着从内存里清除

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
</div>


<div id="const-content">

#**视图类型**

摇一摇界面类型。字符串类型

##取值范围：	

- up_down		//触动摇动动画后视图上下裂开
- left_right	//触动摇动动画后视图左右裂开
- shake			//触动摇动动画后视图左右晃动

