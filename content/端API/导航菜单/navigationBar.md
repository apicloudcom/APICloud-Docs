/*
Title: navigationBar
Description: navigationBar
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[close](#2)

[hide](#3)

[show](#4)

[config](#5)
</div>

#**概述**

本模块用来以原生方式实现应用中常用的导航条功能. 配合 apicloud 平台的 frameGroup 功能( api.openFrameGroup )与 tabBar 模块可实现复杂内容的优雅导航和展示

![图片说明](/img/docImage/navigationBar.jpg)

#**open**<div id="1"></div>

打开

open({params}, callback(ret, err))

##params

x：

- 类型：数字
- 描述：（可选项）导航条横坐标
- 默认值：0

y：

- 类型：数字
- 描述：（可选项）导航条纵坐标
- 默认值：0

w：

- 类型：数字
- 描述：（可选项）导航条宽度
- 默认值：当前frame宽度.默认值,仅在style参数为'left_to_right'时有效

h：

- 类型：数字
- 描述：（可选项）导航条高度
- 默认值：当前frame高度.默认值,仅在style参数为'up_to_down '时有效

style：

- 类型：字符串
- 描述：（可选项）导航条风格
- 默认值：'left_to_right'
- 取值范围：
	- left_to_right	：item从左到右排列
	- up_to_down   ：item从上到下排列

items：

- 类型：数组
- 描述：按钮项
- 内部字段:

```js
[{
	title:			// 标题.字符串类型.不可为空
	titleSelected: 	// 选中后的标题.字符串.默认与title相同.可为空.
	bg:				// 背景,支持 rgb,rgba,# , img. 字符串，默认#696969，可为空
	bgSelected:   	//  选中后背景,支持 rgb,rgba,# , img.字符串.默认与bg相同.可为空.
	alpha: 		    // 背景透明度. 数字.取值范围0-1，默认1，可为空
}]
```

selectedIndex：

- 类型：数字
- 描述：（可选项）被选中的导航项的下标，不传表示不选中任何item

font：

- 类型：JSON 对象
- 默认值：与系统设置相同
- 描述：导航项字体的大小和颜色
- 内部字段:

```js
{
	size:   		//导航项字体大小.数字.默认系统字号，可为空
	sizeSelected:	// 选中时,导航项字体大小.默认size大小，可为空
	color:			// 导航条字体颜色.字符串.默认#FFFFFF,可为空
	colorSelected:  // 导航条字体颜色.字符串.默认与 color 相同.可为空
	alpha: 			// 背景透明度. 数字.取值范围0-1，默认1，可为空
}
```

bg：

- 类型：字符串
- 描述：（可选项）导航条背景，支持 rgb、rgba、#、img
- 默认值：#6b6b6b

alpha：

- 类型：数字
- 描述：背景透明度.取值范围0-1
- 默认值：1.0.


itemSize：

- 类型：JSON 对象
- 描述：（可选项）单个导航项的宽度和高度
- 内部字段:

```js
{
	w:// 单个导航项的宽度.数字.默认为导航条宽度/导航项个数. 可不传.仅在导航条style参数为 'left_to_right'时有效.
	h:// 单个导航项的高度.数字.默认为导航条高度/导航项个数.可不传.仅在导航条style参数为 'up_to_down'时有效.
}
```

fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window

fixed:

- 类型：布尔
- 描述：是否将模块视图固定到窗口上，不跟随窗口上下滚动
- 默认值：true

##callback(ret, err)

ret：

- 类型：JSON 对象
- 描述：包含被点击的导航项的相关信息
- 内部字段：

```js
{
    eventType: 'show', //字符串类型；交互事件类型，取值范围如下：
                       //show：模块打开成功并显示
                       //click：用户点击按钮事件
                       //config：调用config触发点击按钮事件
	id:		,   		//数字类型；导航条对象唯一标识
	index:             //数字类型；导航项下标，当点击 pop按钮时,此值为-1.
}
```

err:

- 类型：JSON 对象
- 描述：发生错误时,返回此对象
- 内部字段：

```js
{
	msg:			// 错误信息.
}
```

##示例代码

```js
var navigationBar = api.require('navigationBar');
navigationBar.open({
    y: 0,
    w: api.frameWidth,
    h: 42,
    itemSize : {
		w : 150
	},
    items: [{
        title: '标题一',
        bg: '#ffff00',
        bgSelected: '#ff00000'
	},{
        title: '标题二',
        bg: '#ffff00',
        bgSelected: '#ff00000'
	},{
        title: '标题三',
        bg: '#ffff00',
        bgSelected: '#ff00000'
	},{
        title: '标题四',
        bg: '#ffff00',
        bgSelected: '#ff00000'
	},{
        title: '标题五',
        bg: '#ffff00',
        bgSelected: '#ff00000'
	}],
    font: {
        color: '#333'
    },
    fixedOn: api.frameName
}, function(ret, err){		
	if( ret ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```

##补充说明

- 当导航项过多时,每次点击或模拟导航项,都会使被选中的导航项,居中显示在导航条中.
- 可以在同一页面操作多个导航条对象.
- open方法的回调会在以下三种情况下触发：

```js
a.模块第一次打开.
b.用户点击了导航条的按钮.
c.selectedIndex参数发生变化.如通过config方法设置selectedIndex参数的值.
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**close**<div id="2"></div>

关闭

close({params})

##params

id：

- 类型：数字
- 默认值：无
- 描述：如果当前页面存在且仅存在一个导航条对象,则默认操作此对象.此时参数可为空

##示例代码

```js
var navigationBar = api.require('navigationBar');
navigationBar.close();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**hide**<div id="3"></div>

隐藏

hide({params})

##params

id：

- 类型：数字
- 描述：操作对象的id

##示例代码

```js
var navigationBar = api.require('navigationBar');
navigationBar.hide();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**show**<div id="4"></div>

显示

show({params})

##params

id：

类型：数字
描述：操作对象的id

##示例代码

```js
var navigationBar = api.require('navigationBar');
navigationBar.show();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**config**<div id="5"></div>

设置或获取模块配置的值

config({params}, callback(ret, err))

##params

id：

- 类型：数字
- 描述：操作对象的id

key：

- 类型：字符串
- 描述：要配置的参数名称.可选范围: open方法中传入的 params 的某一字段.可选字段: x, y, w, h, selectedIndex,bg, alpha

value：

- 类型：混合类型.应与key期望的类型一致
- 描述：要配置的模块的值.不传此参数,则可以直接获取当前配置的值

##callback(ret, err)

ret：

- 类型：JSON 对象
- 描述：设置属性成功时返回
- 内部字段：

```js
{
	key: 		// 字符串. 参数名称.
	oldValue:	// 混合类型,与参数期望的值类型一致. 配置的原值.
	newValue: 	// 混合类型. 配置的新值.当为获取配置的操作时,与oldValue相同.
}
```

err:

- 类型：JSON 对象
- 描述：配置模块参数失败时返回的错误信息
- 内部字段:

```js
{
	msg:		// 错误信息
}
```

##示例代码

```js
var navigationBar = api.require('navigationBar');
navigationBar.config({
	key: 'y'
}, function(ret, err){		
	if( ret ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```

##补充说明

- 此函数传入的回调方法,默认只在设置或获取到参数值时,执行且仅执行一次.
- 当key 为selectedIndex时,会执行两个回调:一个是由config传入的回调,一个是在open方法中传入的回调.

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本