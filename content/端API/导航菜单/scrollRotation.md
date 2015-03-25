/*
Title: scrollRotation
Description: scrollRotation
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[show](#2)

[hide](#3)

[close](#4)
</div>

#**概述**

scrollRotation是一个图片旋转联播器，实现了类似扑克牌效果的图片转动联播。开发者可自定义图片的数量，点击中间图片时会有回调，让开发者自定义点击跳转连接

![图片说明](/img/docImage/scrollRotation.jpg)

#**open**<div id="1"></div>

打开滚动旋转器

open({params}, callback(ret, err))

##params

x：

- 类型：数字
- 默认值：0
- 描述：视图左上角点坐标，可为空

y：

- 类型：数字
- 默认值：导航条下边缘位置
- 描述：图左上角点坐标，可为空

w：

- 类型：数字
- 默认值：当前设备屏幕宽
- 描述：视图的宽，可为空

h：

- 类型：数字
- 默认值：视图的宽减20
- 描述：视图的高，可为空

items：

- 类型：数组
- 默认值：#008B00纯色板
- 描述：每条目的信息成的数组，可为空

内部字段：

```js
[{
	imgPath : 		//字符串，图片路径，支持各种本地协议,可为空,默认#008B00纯色板
	title:          //字符串，说明文字，可为空，为空时不显示文字
	fontColor:      //字符串，字体颜色，可为空，默认白色
	fontSize:       //数字，字体大小，可为空，默认13
}]
```

cornerRadius：

- 类型：数字
- 默认值：0
- 描述：每条目图片的圆角大小（圆角的半径），可为空

intervalTime：

- 类型：数字
- 默认值：无
- 描述：自动连播时间间隔，可为空，若为空则不自动连播

pageControl：

- 类型：json对象
- 默认值：无
- 描述：页面控制器参数，可为空，若为空则不显示页面控制器

内部字段：

```js
{
	normalColor： 		//字符串类型，可为空，常色值，默认#FFFFFF
	selectedColor：     //字符串类型，可为空，选中值，默认#DA70D6
	heightPercent：     //数字类型，可为空，Y轴高度百分比，默认50.0
}
```

fixedOn：

- 类型：字符串
- 默认值：当前视图的名字
- 描述：要添加到某个视图上，可为空，若为空则默认当前视图

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
    click:          //是否是点击事件，布尔值类型
	index：			//滚动后中间图片及其点击事件的下标
}
```

##示例代码

```js
var obj = api.require('scrollRotation');
obj.open(function(ret,err){
	if(ret.click){
		api.alert({msg:ret.index});
    }
	ret.index
});
```

##补充说明

打开视图

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**show**<div id="2"></div>

显示视图

show()

##示例代码

	var obj = api.require('scrollRotation');
	obj.show();

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**hide**<div id="3"></div>

隐藏视图

hide()

##示例代码

	var obj = api.require('scrollRotation');
	obj.hide();

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**close**<div id="4"></div>

关闭视图

close()

##示例代码

	var obj = api.require('scrollRotation');
	obj.close();

##补充说明

关闭视图

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



