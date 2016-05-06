/*
Title: scrollRotation
Description: scrollRotation
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[setIndex](#2)

[show](#3)

[hide](#4)

[close](#5)
</div>

#**概述**

scrollRotation 是一个图片旋转联播器，实现了类似扑克牌效果的图片转动联播。开发者可自定义图片的数量，点击中间图片时会有回调，让开发者自定义点击跳转连接

![图片说明](/img/docImage/scrollRotation.jpg)

#**open**<div id="1"></div>

打开滚动旋转器

open({params}, callback(ret, err))

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
- 默认值：当前设备屏幕的宽

h：

- 类型：数字
- 默认值：w-20
- 描述：（可选项）模块的高度

items：

- 类型：数组
- 描述：每项的信息成的数组
- 内部字段：

```js
[{
	imgPath : 		//字符串类型；图片路径，要求本地协议（widget://、fs://）
	title:          //字符串类型；说明文字
	fontColor:      //字符串类型；字体颜色，支持 rgba、rgb、#；默认：#fff
	fontSize:       //数字类型；字体大小；默认：13
}]
```

cornerRadius：

- 类型：数字
- 描述：（可选项）每条目图片的圆角大小（圆角的半径）
- 默认值：0

intervalTime：

- 类型：数字
- 描述：（可选项）自动连播时间间隔，若不传则不自动连播

pageControl：

- 类型：JSON 对象
- 描述：（可选项）页面控制器参数，若不传则不显示页面控制器
- 内部字段：

```js
{
	normalColor： 		//字符串类型，可为空，常色值，默认#FFFFFF
	selectedColor：     //字符串类型，可为空，选中值，默认#DA70D6
	heightPercent：     //数字类型，可为空，Y轴高度百分比，默认50.0
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

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    click:          //布尔值类型；是否是点击事件
	index:          //数字类型；滚动后中间图片及其点击事件的索引
}
```

##示例代码

```js
var scrollRotation = api.require('scrollRotation');
scrollRotation.open({
	x: 30,
	y: api.frameHeight / 2 - 170,
	w: api.frameWidth - 60,
	h: 340,
    items: [{
        imgPath : 'widget://res/img/apicloud.png',
        title: 'apicloud',
        fontColor: '#ffffff',
        fontSize: 16 
    },{
        imgPath : 'widget://res/img/apicloud-gray.png',
        title: 'apicloud',
        fontColor: '#ffffff',
        fontSize: 16 
    },{
        imgPath : 'widget://res/img/apicloud.png',
        title: 'apicloud',
        fontColor: '#ffffff',
        fontSize: 16 
    },{
        imgPath : 'widget://res/img/apicloud-gray.png',
        title: 'apicloud',
        fontColor: '#ffffff',
        fontSize: 16 
    }],
    fixedOn: api.frameName
}, function(ret, err){		
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

#**setIndex**<div id="2"></div>

滚动到指定条目

setIndex({params})

##params

index：

- 类型：数字
- 描述：滚动的指定位置索引
- 默认值：0

animation：

- 类型：布尔
- 描述：滚动时是否带动画效果（0.3s的滚动动画效果）
- 默认值：true

##示例代码

```js
var scrollRotation = api.require('scrollRotation');
scrollRotation.setIndex({
    index: 1,
    animation: false
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**show**<div id="3"></div>

显示视图

show()

##示例代码

```js
var scrollRotation = api.require('scrollRotation');
scrollRotation.show();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**hide**<div id="4"></div>

隐藏视图

hide()

##示例代码

```js
var scrollRotation = api.require('scrollRotation');
scrollRotation.hide();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**close**<div id="5"></div>

关闭视图

close()

##示例代码

```js
var scrollRotation = api.require('scrollRotation');
scrollRotation.close();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
