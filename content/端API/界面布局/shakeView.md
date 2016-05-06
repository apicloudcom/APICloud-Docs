/*
Title: shakeView
Description: shakeView
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

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

shakeView 封装了一个可供开发者自定义的摇一摇界面，包括动画方向，震动，声音等摇一摇时特定的效果，都可自定义。使用此模块有效的解决了前端实现摇一摇动画不流畅问题

![图片说明](/img/docImage/shakeView.jpg)

#**open**<div id="1"></div>

打开摇一摇视图

open({params})

##params

x：

- 类型：数字
- 描述：（可选项）模块左上角的 x 坐标（相对于所属的 Window 或 Frame）
- 默认值：0

y：

- 类型：数字
- 描述：（可选项）模块左上角的 y 坐标（相对于所属的 Window 或 Frame）
- 默认值：0

w：

- 类型：数字
- 描述：（可选项）模块的宽度
- 默认值：当前设备屏幕宽

h：

- 类型：数字
- 描述：（可选项）模块的高度
- 默认值：w

type：

- 类型：字符串
- 描述：（可选项）摇一摇视图类型，取值范围见[摇一摇类型常量](!Constant)
- 默认值：up_down

anim：

- 类型：JSON 对象
- 描述：（可选项）视图动画的参数配置
- 内部字段：

```js
{
	time:          //（可选项）数字类型；动画持续时间；默认：3.0秒
	sound:         //（可选项）字符串类型；摇动后的音效文件路径，要求本地路径（fs://），Android 平台不支持 wdget 协议，若不传则无声音提示
	isShake:       //（可选项）布尔类型；是否添加手机震动效果；默认：false   
	percent:       //（可选项）数字类型；裂开距离占摇动视图的百分比；默认：50
}
```

img：

- 类型：JSON 对象
- 描述：视图界面图片配置
- 内部字段：

```js
{
	leftUp:           //字符串类型；左边（上面）的图片路径，要求本地路径（widget://、fs://）；默认：灰色视图
	rightDown:        //字符串类型；右边（下面）的图片路径，要求本地路径（widget://、fs://）；默认：灰色视图
	bg:               //（可选项）字符串类型；背景图片路径，要求本地路径（widget://、fs://）；默认：绿色视图
	shake：           //（可选项）字符串类型；震动效果动画时震动（抖动）的图片路径，要求本地路径（widget://、fs://），当type为up_down或left_right时忽略此参数
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

##示例代码

```js
var shakeView = api.require('shakeView');
shakeView.open({
	x: 0,
	y: 300,
	w: api.winWidth,
	h: 300,
	type: 'left_right',
	img: {
		leftUp: 'widget://res/1.png',
		rightDown: 'widget://res/2.png',
		bg: 'widget://res/3.png'
		
	},
	anim: {
		time: '2',
		sound: '',
		isShake: true, 
		percent: 50
	}
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**shake**<div id="2"></div>

触发摇一摇事件

shake({params}, callback(ret, err))

##params

anim：

- 类型：JSON 对象
- 描述：（可选项）视图动画的参数配置
- 内部字段：

```js
{
	time:          //（可选项）数字类型；动画持续时间；默认：3.0秒
	sound:         //（可选项）字符串类型；摇动后的音效文件路径，要求本地路径（fs://），Android 平台不支持 wdget 协议，若不传则无声音提示
	isShake:       //（可选项）布尔类型；是否添加手机震动效果；默认：false   
	percent:       //（可选项）数字类型；裂开距离占摇动视图的百分比；默认：50
}
```

##callback(ret, err)

回调摇一摇动画结束事件

##示例代码

```js
var shakeView = api.require('shakeView');
shakeView.shake(function( ret, err ){
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


#**hide**<div id="3"></div>

隐藏视图

hidd()

##示例代码

```js
var shakeView = api.require('shakeView');
shakeView.hide();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**show**<div id="4"></div>

显示视图

show()

##示例代码
```js
var shakeView = api.require('shakeView');
shakeView.show();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**close**<div id="5"></div>

关闭视图

close()

##示例代码

```js
var shakeView = api.require('shakeView');
shakeView.close();
```

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

