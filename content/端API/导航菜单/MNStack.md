/*
Title: MNStack
Description: MNStack
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[close](#2)
</div>

#**概述**

MNStack是一个栈菜单，可自定义按钮样式和个数及菜单背景，点击非菜单按钮区域可自动关闭菜单，**MNStack 模块是 stackMenu 的优化版**

![图片说明](/img/docImage/stackMenu.jpg)

#**open**<div id="1"></div>

打开stack菜单

open({params}, callback(ret, err))

##params

startCoords：

- 类型：数字
- 描述：（可选项）stack菜单起点坐标（第一个按钮的左上角点）
- 默认值：见内部字段
- 内部字段：

```js
{
     x: 120,       //（可选项）数字类型；起始菜单按钮左上角的 x 坐标（相对于所属的 Window 或 Frame）；默认：当前设备的屏幕宽度的二分之一
     y: 498        //（可选项）数字类型；起始菜单按钮左上角的 y 坐标（相对于所属的 Window 或 Frame）；默认：0
}
```

styles:

- 类型：JSON对象
- 描述：菜单样式配置
- 内部字段：

```js
{
   bg: '',           //（可选项）字符串类型；菜单弹出时的背景（全屏）设置，支持#、rgb、rgba、图片路径（本地路径，fs://，widget://）
   itemHeight: 50,   //（可选项）数字类型；子菜单高度，子菜单宽度随标题字符串长度自适应；默认：50
   titleColor: '',   //（可选项）字符串类型；子菜单标题字体颜色；默认：#8b3e2f
   direction: ''     //（可选项）字符串类型；弹出子菜单方向；默认：right_down，取值范围如下：
                      right_up:  //往右边向上弹出
                      right_down://向右边向下弹出
                      left_up:   //往左边向上弹出
                      right_down://向左边向下弹出
}
```



items：

- 类型：数组
- 描述：子菜单参数组成的数组，**ios 平台上 items 的宽自适应 title 的长，android 平台上为固定宽：80+itemHeight**
- 内部字段：

```js
[{
	title:          //（可选项）字符串类型；子按钮标题
	icon:           //（可选项）字符串类型；子按钮图片的路径，要求本地路径（fs://，widget://）
	bgColor:        //（可选项）字符串类型；子按钮背景色，支持rgb、rgba、#；默认：rgba(0,0,0,0);
	highlightColor: //（可选项）字符串类型；子按钮背景高亮色，支持rgb、rgba、#；默认：rgba(220,220,220,0.8)
}]
```

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	index:                     //数字类型；选中的子菜单按钮的下标
}
```

##示例代码

```js
var MNStack = api.require('MNStack');
MNStack.open({
	startCoords: {
		x: 80
	},
	styles: {
		bg: 'rgba(0,0,0,0.7)',
		itemHeight: 50,
		titleColor: '#333'
	},
	items: [{
		title: '标题一',
		bgColor: '#fff'
	},{
		title: '标题二',
		bgColor: '#fff'
	}]
},function( ret, err ){		
	if( ret ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```

##可用性

IOS系统，安卓系统

可提供的1.0.0及更高版本


#**close**<div id="2"></div>

关闭菜单

close()

##示例代码

```js
var MNStack = api.require('MNStack');
MNStack.close();
```

##可用性

IOS系统，安卓系统

可提供的0.0.1及更高版本

</div>