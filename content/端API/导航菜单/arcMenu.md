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
</div>

#**概述**

arcMenu是一个弧形菜单，子菜单按钮成弧形排列，展开和缩放菜单都有炫酷的动画。开发者可以配置子按钮的样式和数量以及子按钮排列方式

![图片说明](/img/docImage/arcMenu.jpg)

#**open**<div id="1"></div>

打开弹动菜单

open({params}, callback(ret, err))

##params

type：

- 类型：数字
- 默认值：0
- 描述：弹出的子菜单的类型。0为弧形菜单，1为直线型菜单，可为空

mainMenu：

- 类型：JSON
- 默认值：无
- 描述：主菜单的位置大小和背景图

内部字段：

```js
{
    x:0,                 //起点x坐标，数字，不能为空
    y:0,                 //起点y坐标，数字，不能为空
    w:50,                //宽度，数字，不能为空
    h:50,                //高度，数字，不能为空
    img:’’               //背景图片路径，字符串，不能为空
    imgLight:’’          //高亮状态下背景图片路径，字符串，不能为空
}
```

items：

- 类型：数组对象
- 默认值：无
- 描述：子菜单集合，不能为空

内部字段：

```js
[{
    w:40,                //宽度，数字，不能为空
    h:40,                //高度，数字，不能为空
    img:’’               //背景图片路径，字符串，不能为空
    imgLight:’’          //高亮状态下背景图片路径，字符串，不能为空
}]
```

startAngle：

- 类型：数字
- 默认值：无
- 描述：起点角度（12点钟方向为0度，顺时针方向计数），不能为空

wholeAngle：

- 类型：数字
- 默认值：无
- 描述：弧形菜单的角度大小，当type为0时不能为空，当type为1时可为空

radius：

- 类型：数字
- 默认值：无
- 描述：弧形子菜单距离主菜单的半径，若是直线型子菜单，则为最远的子菜单距离主菜单的距离，不能为空

fixedOn：

- 类型：字符串
- 默认值：当前主窗口的名字
- 描述：将此模块视图添加到指定窗口的名字，可为空

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
    id:         //打开后返回id
    index:      //点击子菜单返回其下标
}
```

##示例代码

```js
var obj = api.require('arcMenu');
obj.open({
	type:1,
	mainMenu:{
		x:140,
		y:360,
		w:50,
		h:30,
		img: 'widget://res/arcMenue_centerImg.png',
		imgLight: 'widget://res/arcMenue_centerImgLight.png'
	},
	items:[{ w:40,h:40,img:'widget://res/item1.png',imgLight:'widget://res/item1Light.png'},
		{w:40,h:40,img:'widget://res/item2.png',imgLight:'widget://res/item2Light.png'},
		{w:40,h:40,img:'widget://res/item3.png',imgLight:'widget://res/item3Light.png'},
		{w:40,h:40,img:'widget://res/item4.png',imgLight:'widget://res/item4Light.png'},
		{w:40,h:40,img:'widget://res/item5.png',imgLight:'widget://res/item5Light.png'},
		{w:40,h:40,img:'widget://res/item6.png',imgLight:'widget://res/item6Light.png'}],
	startAngle:0,
	wholeAngle:180,
	radius:100
},function(ret,err){
	api.alert({msg:ret.id+'*'+ret.index});
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
- 描述：要关闭的菜单的id，为空则关闭所有，可为空

##示例代码

    var obj = api.require('arcMenu');
    obj.close({id:1});

##补充说明

关闭菜单

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
