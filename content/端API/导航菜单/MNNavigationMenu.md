/*
Title: MNNavigationMenu
Description: MNNavigationMenu
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[setIndex](#6)

[close](#3)

[show](#4)

[hide](#5)
</div>

#**概述**

MNNavigationMenu 是一个导航栏菜单，可以实现在导航栏上弹出一个菜单，然后子菜单左右铺展开来的动画效果，开发者可自定义其中的样式和按钮个数，超出屏幕部分可左右拖动查看。**本模块是 navigationMenu 的优化版**

![图片说明](/img/docImage/navigationMenu.jpg)

#**open**<div id="1"></div>

打开导航菜单

open({params}, callback(ret, err))

##params

rect：

- 类型：JSON 类型
- 描述：（可选项）模块的位置及尺寸
- 内部字段：

```js
{
    x: 0,                              //（可选项）数字类型；模块左上角的 x 坐标（相对于所属的 Window 或 Frame）；默认值：0
    y: 0,                              //（可选项）数字类型；模块左上角的 y 坐标（相对于所属的 Window 或 Frame）；默认值：0
    w: api.winWidth,                   //（可选项）数字类型；模块的宽度；默认值：所属的 Window 或 Frame 的宽度
    h: 44                              //（可选项）数字类型；模块的高度；默认值：所属的 Window 或 Frame 的高度
}
```

animation：

- 类型：布尔类型
- 描述：是否显示弹出动画（从 y 位置由上而下弹出的动画）
- 默认：true

index：

- 类型：数字类型
- 描述：默认选中菜单项的下标
- 默认：0

styles：

- 类型：JSON 类型
- 描述：模块整体样式
- 内部字段： 

```js
{
	column: 4,                         //（可选项）数字类型；一屏显示的菜单项个数；默认：4
    bg: '#eee',                        //（可选项）字符串类型；菜单显示区域背景，支持rgb、rgba、#、img；默认：'rgba(0,0,0,0)'
    item: {                            //（可选项）JSON 对象类型，菜单项的通用样式
    	bg: '#fff',                    //（可选项）字符串类型；菜单项的背景，支持rgb、rgba、#、img；默认：#fff
    	active: '#eee',                //（可选项）字符串类型；菜单项选中背景，支持rgb、rgba、#、img；默认：同 bg
    	highlight: '#eee',             //（可选项）字符串类型；菜单项高亮背景，支持rgb、rgba、#、img；默认：同 active
    	title: {                       //（可选项）JSON 类型；菜单项标题样式设置
    		marginB: 6,                //（可选项）数字类型；菜单项标题底部与菜单项下边线的距离；默认：6
    		size: 14,                  //（可选项）数字类型；菜单项标题文字大小；默认：14
    		color: '#888',             //（可选项）字符串类型；标题文字颜色，支持 rgb，rgba，#；默认：#888
    		active: '#f00',            //（可选项）字符串类型；标题文字选中颜色，支持 rgb，rgba，#；默认：同 color
    		highlight: '#f00',         //（可选项）字符串类型；标题文字高亮颜色，支持 rgb，rgba，#；默认：同 active
    	},
    	icon: {                        //（可选项）JSON 类型；图标的样式设置
    		marginT: 0,                //（可选项）数字类型；图标顶部与菜单项顶部的距离；默认：0
    		width: 30,                 //（可选项）数字类型；图标的宽度；默认：30
    		height: 30,                //（可选项）数字类型；图标的高度；默认：同 width
    		corner: 2                 //（可选项）数字类型；图标的圆角半径；默认：2
    	}
    }
}
```

items：

- 类型：JSON 数组类型
- 描述：菜单项数组
- 内部字段：

```js
[{                                     //一个菜单项的设置
	title: '菜单项0',                  //（可选项）字符串类型；菜单项的标题内容；默认：未设置时不显示菜单项标题
	icon: 'fs://menu/0.png',           //（可选项）字符串类型；菜单项的图标，支持 fs://，widget://，http://；默认：未设置时不显示菜单项图标
	active: 'fs://menu/0.acitve.png',  //（可选项）字符串类型；菜单项选中时的图标，支持 fs://，widget://，http://；默认：同 icon
	highlight: 'fs://menu/0.highlight.png', //（可选项）字符串类型；菜单项高亮时的图标，支持 fs://，widget://，http://；默认：同 active
}]

```

fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window

fixed：

- 类型：布尔类型
- 描述：此模块时否在窗口中固定位置（不随窗口的滚动而改变位置）
- 默认：false

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	index：		//用户点击菜单项时的下标
}

```

##示例代码

```js
var MNNavigationMenu = api.require('MNNavigationMenu');
MNNavigationMenu.open({
    rect: {
        x: 0,
        y: 0,
        w: api.winWidth,
        h: 44
    },
    index: 0,
    animation: true,
    styles: {
        column: 4,
        bg: '#eee',
        item: {
            width: api.winWidth / 4,
            bg: '#fff',
            active: '#eee',
            highlight: '#eee',
            title: {
                marginB: 6,
                size: 14,
                height: 14,
                color: '#888',
                active: '#f00',
                highlight: '#f00'
            },
            icon: {
                marginT: 0,
                width: 30,
                height: 30,
                corner: 2
            }
        }
    },
    items: [{
        title: '菜单项0',
        icon: 'fs://menu/0.png',
        active: 'fs://menu/0.acitve.png',
        highlight: 'fs://menu/0.highlight.png'
    }, {
        title: '菜单项1',
        icon: 'fs://menu/1.png',
        active: 'fs://menu/1.acitve.png',
        highlight: 'fs://menu/1.highlight.png'
    }, {
        title: '菜单项2',
        icon: 'fs://menu/2.png',
        active: 'fs://menu/2.acitve.png',
        highlight: 'fs://menu/2.highlight.png'
    }, {
        title: '菜单项3',
        icon: 'fs://menu/3.png',
        active: 'fs://menu/3.acitve.png',
        highlight: 'fs://menu/3.highlight.png'
    }, {
        title: '菜单项4',
        icon: 'fs://menu/4.png',
        active: 'fs://menu/4.acitve.png',
        highlight: 'fs://menu/4.highlight.png'
    }],
    fixedOn: api.frameName,
    fixed: false
},
function(ret, err) {
    if (ret) {
        alert(JSON.stringify(ret));
    } else {
        alert(JSON.stringify(err));
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setIndex**<div id="6"></div>

选中某一菜单项

setIndex({params}, callback(ret, err))

##params

index：

- 类型：数字类型
- 描述：目标菜单项的下标

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	status: true                       //选中完成
}

```

##示例代码

```js
var MNNavigationMenu = api.require('MNNavigationMenu');
MNNavigationMenu.setIndex({
    index: 0
},
function(ret, err) {
    if (ret) {
        alert(JSON.stringify(ret));
    } else {
        alert(JSON.stringify(err));
    }
});

```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**close**<div id="3"></div>

关闭菜单

close()

##示例代码

```js
var MNNavigationMenu = api.require('MNNavigationMenu');
MNNavigationMenu.close();

```

##补充说明

关闭菜单，意味着从内存里清除

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**show**<div id="4"></div>

显示菜单

show()

##示例代码

```js
var MNNavigationMenu = api.require('MNNavigationMenu');
MNNavigationMenu.show();

```

##补充说明

显示菜单，若 open 此模块时带动画，则本操作也带动画

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**hide**<div id="5"></div>

隐藏菜单

hide()

##示例代码

```js
var MNNavigationMenu = api.require('MNNavigationMenu');
MNNavigationMenu.hide();

```

##补充说明

隐藏菜单，只是移除到屏幕之外，还在内存里没有清除，若 open 此模块时带动画，则本操作也带动画

##可用性

iOS系统，Android系统
可提供的1.0.0及更高版本
