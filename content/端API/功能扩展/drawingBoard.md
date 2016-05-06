/*
Title: drawinBoard
Description: drawinBoard
*/

<ul id="tab" class="clearfix">
    <li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)
[save](#2)
[close](#3)
[hide](#4)
[show](#5)
[revoke](#6)
[restore](#7)
[clear](#8)
[resetBrush](#9)
</div>

#**概述**

drawinBoard 模块是一个手写签名模块。开发者可自定义个固定宽高（w、h）的 “frame”，该 “frame” 即是可手写签名的背景透明的画板，可将此画板固定在指定的 frame 或 window 上，从而自定义出符合自己需求的各种 UI 效果的签名功能。

#**open**<div id="1"></div>

打开签名画板

open({params})

##params

rect：

- 类型：JSON 对象
- 描述：（可选项）签名画板的位置及尺寸
- 默认值：见内部字段
- 内部字段：

```js
{
    x: 0,                              //（可选项）数字类型；签名画板左上角的 X 坐标（相对于所属的 Window 或 Frame）；默认：0
    y: 0,                              //（可选项）数字类型；签名画板左上角的 Y 坐标（相对于所属的 Window 或 Frame）；默认：0
    w: 320,                            //（可选项）数字类型；签名画板的宽度；默认：所属的 Window 或 Frame 的宽度
    h: 300                             //（可选项）数字类型；签名画板的高度；默认：w-20
}
```
styles：

- 类型：JSON 对象
- 描述：画板画笔样式配置
- 默认值：见内部字段
- 内部字段：

```js
{
    brush: {                  //（可选项）JSON对象；画笔配置
       color:'#ff0000',       //（可选项）字符串类型；画笔颜色，支持#、rgb、rgba；默认：#000
       width:6                //（可选项）数字类型；画笔粗细；默认：6.0；
    },
    bgColor: ''               //（可选项）字符串类型；画板背景色，支持#、rgb、rgba；默认：#fff
}
```

fixedOn：

- 类型：字符串类型
- 描述：（可选项）签名画板添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window
 
##示例代码

```js
var drawinBoard = api.require('drawinBoard');
drawinBoard.open({
    rect: {
        x: 0,
        y: 0,
        w: 320,
        h: 300
    },
    styles{
	    brush: {
	        color: '#ff0000',
	        width: 6
	    },
	    bgColor: '#ff0'
    },
    fixedOn: api.frameName
});
```

##可用性

IOS系统，Android系统

可提供的1.0.0及更高版本

#**save**<div id="a2"></div>

保存签名画板截图，**截图大小（宽高：w、h）同 open 时传入的 rect 大小（宽高：w、h）**

save({params}, callback(ret, err))

##params

savePath：

- 类型：字符串类型
- 描述：保存图片路径，要求本地路径（fs://），**IOS 平台不支持 widget 路径**

copyToAlbum：

- 类型：布尔类型
- 描述：（可选项）是否将结果同时保存到系统相册
- 默认：false

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	absolutePath:       //字符串类型；图片保存到指定路径后的绝对路径，若保存失败则为该参数为 undefined
	albumPath:          //字符串类型；图片保存到相册后的绝对路径，若保存失败则该参数为 undefined
}
```

##示例代码

```js
var drawinBoard = api.require('drawinBoard');
drawinBoard.save({
    savePath: 'fs://drawinBoard/result.png',
    copyToAlbum: false
}, function(ret){	
    alert(JSON.stringify(ret));
});
```

##可用性

IOS系统，Android系统

可提供的1.0.0及更高版本

#**close**<div id="3"></div>

关闭签名画板

close()

##示例代码

```js
var drawinBoard = api.require('drawinBoard');
drawinBoard.close();
```

##可用性

IOS系统，Android系统

可提供的1.0.0及更高版本

#**hide**<div id="4"></div>

隐藏签名画板

hide()

##示例代码

```js
var drawinBoard = api.require('drawinBoard');
drawinBoard.hide();
```
##补充说明

隐藏已显示的签名画板，并没有从内存里清除

##可用性

IOS系统，Android系统

可提供的1.0.0及更高版本

#**show**<div id="5"></div>

显示已隐藏的签名画板

show()

##示例代码

```js
var drawinBoard = api.require('drawinBoard');
drawinBoard.show();
```

##可用性

IOS系统，Android系统

可提供的1.0.0及更高版本

#**revoke**<div id="6"></div>

撤销最新画出的笔画线条

revoke()

##示例代码

```js
var drawinBoard = api.require('drawinBoard');
drawinBoard.revoke();
```

##可用性

IOS系统，Android系统

可提供的1.0.0及更高版本

#**restore**<div id="7"></div>

恢复刚撤销的笔画线条

restore()

##示例代码

```js
var drawinBoard = api.require('drawinBoard');
drawinBoard.restore();
```

##可用性

IOS系统，Android系统

可提供的1.0.0及更高版本

#**clear**<div id="8"></div>

清空画板上的所有笔画线条

clear()

##示例代码

```js
var drawinBoard = api.require('drawinBoard');
drawinBoard.clear();
```

##可用性

IOS系统，Android系统

可提供的1.0.0及更高版本

#**resetBrush**<div id="9"></div>

重设画笔样式

resetBrush({params})

##params

color：

- 类型：字符串
- 描述：（可选项）画笔颜色，支持#、rgb、rgba
- 默认值：原值

width：

- 类型：数字
- 描述：画笔粗细
- 默认值：原值

##示例代码

```js
var drawinBoard = api.require('singature');
drawinBoard.resetBrush({
   color: '#696969',
   width: 10
});
```

##可用性

IOS系统，Android系统

可提供的1.0.0及更高版本