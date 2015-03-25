/*
Title: navigationBar
Description: navigationBar
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
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

本模块用来以原生方式实现应用中常用的导航条功能. 配合apicloud 平台的frameGroup功能(api.openFrameGroup)与 tabBar 模块可实现复杂内容的优雅导航和展示

![图片说明](/img/docImage/navigationBar.jpg)

#**open**<div id="1"></div>

打开

open(params, callback)

##params

x：

- 类型：数字
- 默认值：0
- 描述：导航条横坐标.可为空

y：

- 类型：数字
- 默认值：0
- 描述：导航条纵坐标.可为空

w：

- 类型：数字
- 默认值：当前frame宽度.默认值,仅在style参数为"left_to_right"时有效
- 描述：导航条宽度.可为空

h：

- 类型：数字
- 默认值：当前frame高度.默认值,仅在style参数为"up_to_down "时有效
- 描述：导航条高度.可为空

style：

- 类型：字符串
- 默认值："left_to_right"
- 描述：导航条风格.取值范围见[导航条方向设置](!Constant).可为空

items：

- 类型：数组
- 默认值：无
- 描述：按钮项

内部字段:

```js
[{
	title:			// 标题.字符串类型.不可为空
	titleSelected: 	// 选中后的标题.字符串.默认与title相同.可为空.
	bg:				// 背景,支持rgb,rgba,# , img. 字符串，默认#696969，可为空
	bgSelected:   	//  选中后背景,支持rgb,rgba,# , img.字符串.默认与bg相同.可为空.
	alpha: 		// 背景透明度. 数字.取值范围0-1，默认1，可为空
}]
```

selectedIndex：

- 类型：数字
- 默认值：无
- 描述：被选中的导航项的下标.可为空.不传表示不选中任何item

font：

- 类型：JSON对象
- 默认值：与系统设置相同
- 描述：导航项字体的大小和颜色.可为空

内部字段:

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
- 默认值：#6b6b6b
- 描述：导航条背景,支持rgb,rgba,# , img.可为空

alpha：

- 类型：数字
- 默认值：1.0.
- 描述：背景透明度.取值范围0-1，默认1，可为空


itemSize：

- 类型：JSON对象.	
- 默认值：无	
- 描述：单个导航项的宽度和高度.可不传

内部字段:

```js
{
	w:// 单个导航项的宽度.数字.默认为导航条宽度/导航项个数. 可不传.仅在导航条style参数为 "left_to_right"时有效.
	h:// 单个导航项的高度.数字.默认为导航条高度/导航项个数.可不传.仅在导航条style参数为 "up_to_down"时有效.
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

##callback(ret, err)

ret：

- 类型：JSON对象
- 描述：包含被点击的导航项的相关信息

内部字段：

```js
{
	id:				// 导航条对象唯一标识.数字类型.
	index:          //导航项下标.数字类型.当点击 pop按钮时,此值为-1.
}
```

err:

- 类型：JSON 对象
- 描述：发生错误时,返回此对象

内部字段：

```js
{
	msg:			// 错误信息.
}
```

##示例代码

```js
var navigationBar = api.require("navigationBar");
var params = {
    x: 0,
    y: 64,
    w: api.frameWidth,
    h: 49,
    style: "left_to_right",
itemSize:{
		w: 100,
		h: 100
	},
    items: [
        {
          	title:"title0",
          	titleSelected:"titleSelected0",
          	bg:"#ffff00",
			alpha: 0.8,
         	bgSelected:"#ff00000"
        },
        {
          	title:"title1",
   			titleSelected:"titleSelected1",
         	bg:"#ffff00",
			alpha: 0.8,
          	bgSelected:"#ff00000"
        },
        {
          	title:"title2",
   			titleSelected:"titleSelected2",
          	bg:"#ffff00",
			alpha: 0.8,
          	bgSelected:"#ff00000"
        },
        {
          	title:"title3",
   			titleSelected:"titleSelected3",
         	bg:"#ffff00",
			alpha: 0.8,
          	bgSelected:"#ff00000"
        },
        {
          	title:"title4",
   			titleSelected:"titleSelected4",
          	bg:"#ffff00",
			alpha: 0.8,
          	bgSelected:"#ff00000"
        },
        {
          	title:"title5",
   			titleSelected:"titleSelected5",
          	bg:"#ffff00",
			alpha: 0.8,
          	bgSelected:"#ff00000"
        }
    ],
selectedIndex: 2,
    font: {
        size: 11,
        sizeSelected: 14,
        color: "#ff00000",
        colorSelected: "#ffff00"
    },
    bg: "#00ff00",
	alpha: 1.0,
    popItem: {
        position: "tail",
        title: "打开",
        titleSelected: "关闭",
        bg: "#ffff00",
        bgSelected: "#ff00000"
    }
};

function callback(ret, err){
    if(! ret){
        api.alert({title: "出错了", msg: err["msg"]});
        return;
    }

    api.alert({title: "提示", msg: "您点击了 pop 导航项!"});
}

navigationBar.open(params, callback);
```

##补充说明

- 当导航项过多时,每次点击或模拟导航项,都会使被选中的导航项,居中显示在导航条中.
- 可以在同一页面操作多个导航条对象.
- open方法的回调会在以下三种情况下触发：
```
	a.模块第一次打开.
    b.用户点击了导航条的按钮.
	c.selectedIndex参数发生变化.如通过config方法设置selectedIndex参数的值.
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**close**<div id="2"></div>

关闭

close(params)

##params

id：

- 类型：数字
- 默认值：无
- 描述：如果当前页面存在且仅存在一个导航条对象,则默认操作此对象.此时参数可为空

##示例代码

	var navigationBar = api.require("navigationBar");
	navigationBar.close();

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**hide**<div id="3"></div>

隐藏

hide(params)

##params

id：

- 类型：数字
- 默认值：无
- 描述：如果当前页面存在且仅存在一个导航栏对象,则默认操作此对象.此时参数可为空

##示例代码

	var navigationBar = api.require("navigationBar");
	navigationBar.hide();

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**show**<div id="4"></div>

显示

show(params)

##params

id：

类型：数字
默认值：无
描述：如果当前页面存在且仅存在一个导航栏对象,则默认操作此对象.此时参数可为空

##示例代码

	var navigationBar = api.require("navigationBar");
	navigationBar.show();

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**config**<div id="5"></div>

设置或获取模块配置的值

config(params, callback)

##params

id：

- 类型：数字
- 默认值：无
- 描述：如果当前页面存在且仅存在一个导航栏对象,则默认操作此对象.此时参数可为空

key：

- 类型：字符串
- 默认值：无
- 描述：要配置的参数名称.可选范围: open方法中传入的 params 的某一字段.可选字段: x, y, w, h, selectedIndex,bg, alpha

value：

- 类型：混合类型.应与key期望的类型一致.
- 默认值：无
- 描述：要配置的模块的值.不传此参数,则可以直接获取当前配置的值

##callback(ret, err)

ret：

- 类型：JSON对象
- 描述：设置属性成功时返回

内部字段：

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

内部字段:

```js
{
	msg:		// 错误信息
}
```

##示例代码

```js
var navigationBar = api.require("navigationBar");
navigationBar.config({
    key: "bgImg",
    value: "widget://imgage/navigationBar/bg2.png"},
    function(ret, err){
        if(ret){
            var msg = "属性名称: " + ret["key"] + "\n旧值: " + ret["oldValue"] + "\n新值: " + ret["newValue"];
            api.alert({"title": "提示", "msg": msg});
        }
    });
```

##补充说明

- 此函数传入的回调方法,默认只在设置或获取到参数值时,执行且仅执行一次.
- 当key 为selectedIndex时,会执行两个回调:一个是由config传入的回调,一个是在open方法中传入的回调.

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

</div>



<div id="const-content">

#**导航条方向类型**

导航条的方向设置.字符串类型

##取值范围：

- left_to_right			//item从左到右排列
- up_to_down            //item从上到下排列

