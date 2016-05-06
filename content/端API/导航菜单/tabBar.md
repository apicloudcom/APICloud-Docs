/*
Title: tabBar
Description: tabBar
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[setBadge](#2)

[hidden](#3)

[show](#4)

[close](#5)

[setSelect](#6)
</div>

#**概述**

tabBar是一个底部导航条模块，开发者可自定义每个按钮样式及其显示的徽章（badge），当子按钮个数超出屏幕时，用户可左右拖动查看

![图片说明](/img/docImage/tabBar.jpg)

#**open**<div id="1"></div>

打开

open({params}, callback(ret, err))

##params

bgImg：

- 类型：字符串
- 描述：tabBar的背景图片路径，要求本地路径（fs://、widget://）

selectImg：

- 类型：字符串
- 描述：选中按钮后的按钮背景效果图片路径

perScreenBtn：

- 类型：数字
- 默认值：5
- 描述：（可选项）每屏显示按钮的个数

items：

- 类型：数组
- 描述：多个按钮的信息组成的数组
- 内部字段：

```js
[{
	img:                 //字符串类型；按钮图片路径，要求本地路径（fs://、widget://）
    highlight:           //字符串类型；按钮按下时的背景图片，要求本地路径（fs://、widget://）
    selected:            //字符串类型；按钮选中后的图片，要求本地路径（fs://、widget://）
    title:               //字符串类型；按钮的标题
    color:               //（可选项）字符串类型；标题的颜色，支持 rgba、rgb、#；默认：#fff
    selectedTitleColor:  //（可选项）字符串类型；选中后的按钮标题颜色，支持 rgb、rgba、#；默认：#fff
    badge:               //（可选项）字符串类型；按钮左上角的badge，不传时不显示badge
}]
```

selecteIndex：

- 类型：数字
- 描述：（可选项）默认选中按钮的下标，不传则都不选中

h：

- 类型：数字
- 描述：（可选项）模块视图的高
- 默认值：50

fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window


badgeAlignment：

- 类型：字符串
- 描述：（可选项）徽章位置
- 默认值：left
- 取值范围：
   - left：中间偏左（相对于所在 item）显示
   - right：中间偏右（相对于所在 item）显示 

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    index:		    //数字类型；点击某个按钮返回其索引值
}
```

##示例代码

```js
var tabBar = api.require('tabBar');
tabBar.open({
    bgImg: 'widget://res/img/bg.png',
	items: [{
        title: '标题一',
        img: 'widget://res/img/ic/item.png',
        badge: '1'
    },{
        title: '标题二',
        img: 'widget://res/img/ic/item.png',
        badge: '2'
    },{
        title: '标题三',
        img: 'widget://res/img/ic/item.png',
        badge: '1'
    },{
        title: '标题四',
        img: 'widget://res/img/ic/item.png',
        badge: '2'
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


#**setBadge**<div id="2"></div>

设置按钮左上角的badge标注

setBadge({params})

##params

index:

- 类型：数字
- 说明：要设置的按钮的下标

badge：

- 类型：字符串
- 说明：（可选项）要设置的标注，不传则设置为不显示徽章

##示例代码

```js
var tabBar = api.require('tabBar');
tabBar.setBadge({
	index: 3,
    badge: '说明'
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**hide**<div id="3"></div>

隐藏tabBar

hide();

##示例代码

```js
var tabBar = api.require('tabBar');
tabBar.hide();
```

##补充说明

将已打开的tabBar以移动动画的形式移出到屏幕下方

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**show**<div id="4"></div>

显示隐藏的tabBar

show();

##示例代码

```js
var tabBar = api.require('tabBar');
tabBar.show();
```

##补充说明

将已打开的tabBar以移动动画的形式弹出

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**close**<div id="5"></div>

关闭tabBar

close()

##示例代码

```js
var tabBar = api.require('tabBar');
tabBar.close();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setSelect**<div id=“6”></div>

设置选中按钮

setSelect({params})
 
##params
 
index：
- 类型：数字
- 描述：（可选项）要设置的按钮的下标
- 默认值：0

##示例代码

```js
var tabBar = api.require('tabBar');
tabBar.setSelect({
    index: 1
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
