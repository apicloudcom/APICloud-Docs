/*
Title: arcMenu
Description: arcMenu
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

arcMenu是一个弧形菜单，子菜单按钮成弧形排列，展开和缩放菜单都有炫酷的动画。开发者可以配置子按钮的样式和数量以及子按钮排列方式

![图片说明](/img/docImage/arcMenu.jpg)

#**open**<div id="1"></div>

打开弹动菜单

open({params}, callback(ret, err))

##params

<del>type：</del>

- <del>类型：数字</del>
- <del>默认值：0</del>
- <del>描述：弹出的子菜单的类型。0为弧形菜单，1为直线型菜单，可为空</del>

type：

- 类型：字符串
- 默认值：arc
- 描述：（可选项）弹出的子菜单的类型。arc为弧形菜单，straight为直线型菜单

mainMenu：

- 类型：JSON
- 默认值：见内部字段
- 描述：主菜单的位置大小和背景图
- 内部字段：

```js
{
    x:0,			//（可选项）起点x坐标，数字，默认0 
    y:0,			//（可选项）起点y坐标，数字，默认0
    w:50,			//（可选项）宽度，数字，默认50
    h:50,			//（可选项）高度，数字，默认50
    img:’’			//背景图片路径，支持widget、fs等本地协议路径
    imgLight:’’		//高亮状态下背景图片路径，支持widget、fs等本地协议路径
}
```

items：

- 类型：数组对象
- 默认值：无
- 描述：设置子菜单信息集合

内部字段：

```js
[{
    w:40,			//（可选项）宽度，数字，默认40
    h:40,			//（可选项）高度，数字 ，默认40
    img:’’			//背景图片路径，支持widget、fs等本地协议路径
    imgLight:’’		//高亮状态下背景图片路径，支持widget、fs等本地协议路径
}]
```

startAngle：

- 类型：数字
- 默认值：0
- 描述：（可选项）起点角度（12点钟方向为0度，顺时针方向计数） 

wholeAngle：

- 类型：数字
- 默认值：180
- 描述：（可选项）弧形菜单的角度大小，当type为arc时必传，当type为straight时此参数可不传 

radius：

- 类型：数字
- 默认值：100
- 描述：（可选项）弧形子菜单距离主菜单的半径，若是直线型子菜单，则为最远的子菜单距离主菜单的距离

fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window

fixed:
- 类型：布尔
- 默认值：true
- 描述：（可选项）是否将模块视图固定到窗口上，不跟随窗口上下滚动


shieldClick:
- 类型：布尔
- 默认值：true
- 描述：（可选项）点击非菜单区域是否收缩菜单

##callback(ret, err)
ret：

- 类型：JSON对象

内部字段：

```js
{
    id:         //打开后返回id
    index:      //点击子菜单返回其下标
}
```

##示例代码

```js
var arcMenu = api.require('arcMenu');
arcMenu.open({
	type: 'arc',
	mainMenu: {
		x: api.frameWidth / 2,
		y: api.frameHeight / 2,
		w: 50,
		h: 50,
		img: 'widget://res/img/ic/color-lump-square.png',
		imgLight: 'widget://res/img/ic/color-lump-square.png'
	},
	items: [{ 
			w: 40,
			h: 40,
			img: 'widget://res/img/ic/small-bell.png',
			imgLight: 'widget://res/img/ic/small-bell.png'
		},{ 
			w: 40,
			h: 40,
			img: 'widget://res/img/ic/count.png',
			imgLight: 'widget://res/img/ic/count.png'
		},{ 
			w: 40,
			h: 40,
			img: 'widget://res/img/ic/color-lump-triangle.png',
			imgLight: 'widget://res/img/ic/color-lump-triangle.png'
		},{ 
			w: 40,
			h: 40,
			img: 'widget://res/img/ic/compass.png',
			imgLight: 'widget://res/img/ic/compass.png'
		},{ 
			w: 40,
			h: 40,
			img: 'widget://res/img/ic/message.png',
			imgLight: 'widget://res/img/ic/message.png'
		},{ 
			w: 40,
			h: 40,
			img: 'widget://res/img/ic/clock.png',
			imgLight: 'widget://res/img/ic/clock.png'
		}],
    wholeAngle: 180,
    radius: 100,
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

打开菜单

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**close**<div id="2"></div>

关闭菜单

close({params})

##params

id：
- 类型：数字
- 默认值：无
- 描述：要关闭的菜单的id，不传则关闭所有

##示例代码

```js
var arcMenu = api.require('arcMenu');
arcMenu.close({
	id: 1
});
```

##补充说明

关闭菜单

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**hide**<div id="3"></div>

隐藏已打开并显示的菜单

hide({params})

##params

id：
- 类型：数字
- 默认值：无
- 描述：要操作的菜单的id 

##示例代码

```js
var arcMenu = api.require('arcMenu');
arcMenu.hide({
	id: 1
});
```

##补充说明

隐藏菜单模块视图，并没有从内存清除

##可用性

iOS系统，Android系统
可提供的1.0.1及更高版本

#**show**<div id="4"></div>

显示已打开但被隐藏的菜单

show({params})

##params

id：
- 类型：数字
- 默认值：无
- 描述：要操作的视图id

##示例代码

```js
var arcMenu = api.require('arcMenu');
arcMenu.show({
	id: 1
});
```

##补充说明

无

##可用性

iOS系统，Android系统
可提供的1.0.0及更高版本