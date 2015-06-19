/*
Title: circularMenu
Description: circularMenu
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#a1)

[close](#a2)

[hide](#a3)

[show](#a4)
</div>

#**概述**

circularMenu是一个转盘菜单，类似建行手机客户端首页的转盘菜单。本模块是原生实现的，动画非常流畅，开发者可自定义菜单上按钮的个数和样式。简单几行代码即可开发出转盘效果的炫酷UI

![图片说明](/img/docImage/circularMenu.jpg)

#**open**<div id="a1"></div>

打开转盘菜单

open({params}, callback(ret, err))

##params

centerX：

- 类型：数字
- 默认值：当前屏幕的中间
- 描述：环形菜单的圆心坐标，可为空

centerY：

- 类型：数字
- 默认值：导航条下边缘加模块半径的位置
- 描述：环形菜单的圆心坐标，可为空

radius：

- 类型：数字
- 默认值：150
- 描述：环形菜单的圆半径，可为空

centerBtnRadius：

- 类型：数字
- 默认值：radius/3.0
- 描述：环形菜单中间圆形按钮的半径，可为空

bgImg：

- 类型：字符串
- 默认值：无
- 描述：环形菜单的背景图片，可为空，为空则背景透明

centerBtnImg：

- 类型：字符串
- 默认值：无
- 描述：环形菜单的中间按钮的背景图片，可为空，为空则没有中间按钮

indicatorPosition：

- 类型：字符串
- 默认值：left
- 描述：环形菜单的指针位置，取值范围见常量指针位置，可为空

fixedOn：

- 类型：字符串
- 默认值：无
- 描述：视图添加到目标窗口的名字，可为空，为空则添加到当前window

items：

- 类型：数组
- 默认值：无
- 描述：子菜单信息组成的数组，不可为空

内部字段：

```js
[{
	normal:             //按钮常态背景图片，不可为空
	highlight:          //按钮高亮背景图片，可为空
	title:              //标题，可为空
	titleColor:         //标题颜色，可为空，默认#919191
}]
```

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    click：				//布尔值，判断是否是点击事件的callBack
	index:    			//用户点击按钮的下标，中间按钮的下标为最大
	indicatorIndex: 	//旋转停止后指针所指位置下的按钮的下标
}
```

##示例代码

```js
var obj = api.require('circularMenu');
var arrayItems = [];
for (var i=0;i<5;i++){
	arrayItems[i]={
		normal:"widget://res/circularMenu2.png",
		highlight:"widget://res/circularMenu2light.png",
		title:"按钮二",
		titleColor:"#FF0000"
	};
}
obj.open({
	items: arrayItems
}, function(ret, err){
	var index = ret.index;
	var pointerIndex = ret.pointerIndex;
});
```

##补充说明

打开环形菜单

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**close**<div id="a2"></div>

关闭环形菜单

close()

##示例代码

	var obj = api.require('circularMenu');
	obj.close();

##补充说明

关闭环形菜单

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**hide**<div id="a3"></div>

隐藏环形菜单

hide()

##示例代码

	var obj = api.require('circularMenu');
	obj.hide();

##补充说明

隐藏环形菜单，并没有从内存清除

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

#**show**<div id="a4"></div>

显示已隐藏的环形菜单

show()

##示例代码

	var obj = api.require('circularMenu');
	obj.show();

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本
</div>



<div id="const-content">
#**指针位置**

菜单指针位置。字符串类型

##取值范围：

- left		//左边
- right		//右边
- up		//上边
- down		//下边
