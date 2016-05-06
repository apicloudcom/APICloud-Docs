/*
Title: coverFlow
Description: coverFlow
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
</div>

#**概述**

coverFlow底层封装了openGL实现的3D图片流效果和逼真的倒影。开发者可自定义图片及其数量。只需一个open接口就能打开一个超炫酷的coverFlow效果导航菜单

![图片说明](/img/docImage/coverFlow.jpg)

#**open**<div id="1"></div>

打开coverFlow

open({params}, callback(ret, err))

##params

x ：

- 类型：数字
- 默认值：0
- 描述：视图左上角点坐标，可为空

y：

- 类型：数字
- 默认值：100
- 描述：视图左上角点坐标，可为空

w：

- 类型：数字
- 默认值：当前设备屏幕的宽
- 描述：视图的宽，可为空

h：

- 类型：数字
- 默认值：w-20
- 描述：视图的高，可为空

bgColor：

- 类型：字符串
- 默认值：rgba(0,0,0,0)
- 描述：背景颜色十六进制值,支持 rgb，rgba，#，可为空

paths：

- 类型：数组
- 默认值：无
- 描述：图片路径组成的数组，不可为空

fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window

reflect：

- 类型：布尔值
- 默认值：true
- 描述：是否显示倒影，可为空

fixed:
- 类型：布尔
- 默认值：true
- 描述：是否将模块视图固定到窗口上，不跟随窗口上下滚动，可为空

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
    eventType：     //事件类型，取值范围如下：
                      click//点击事件
                      scroll//滚动事件
	index:           //返回用户选择的图片的下标
}
```

##示例代码

```js
var coverFlow = api.require('coverFlow');
coverFlow.open({
	x: 0,
	y: 0,
	w: api.winWidth,
	h: 300,
	bgColor:'#ADD8E6',
	paths:[
        'widget://res/a1.png',
        'widget://res/a1.png',
        'widget://res/a1.png',
        'widget://res/a1.png',
        'widget://res/a1.png',
        'widget://res/a1.png',
        'widget://res/a1.png',
        'widget://res/a1.png',
        'widget://res/a1.png'
    ],
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

打开coverFlow模块视图

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**close**<div id="2"></div>

关闭coverFlow

close()

##示例代码

```js
    var coverFlow = api.require('coverFlow');
    coverFlow.close();
```

##补充说明

关闭coverFlow

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**hide**<div id="2"></div>

隐藏显示的coverFlow视图

hide()

##示例代码

```js
var coverFlow = api.require('coverFlow');
coverFlow.hide();
```

##补充说明

只是隐藏模块视图，并没有从内存里清除

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

#**show**<div id="4"></div>

显示已隐藏的coverFlow视图

show()

##示例代码

```js
var coverFlow = api.require('coverFlow');
coverFlow.show();
```

##补充说明

显示模块视图

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本