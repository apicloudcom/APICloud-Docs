/*
Title: tuberBar
Description: tuberBar
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[setSelected](#2)

[setBadge](#3)

[hide](#4)

[show](#5)

[close](#6)

[bringToFront](#7)
</div>

#**概述**

tuberBar是一个底部导航条模块，开发者可自定义其样式，与tabBar不同的是中间按钮可以定义出突出显示的效果，开发者可自定义其突出高度，以及分割线颜色。


#**open**<div id="1"></div>

打开

open({params}, callback(ret, err))

##params

bg：

- 类型：字符串
- 默认值：#ffffff
- 描述：（可选项）tuberBar的背景设置，支持rgb、rgba、#、img

h：

- 类型：数字
- 默认值：60
- 描述：（可选项）tuberBar的高度最大值-----突起部分的高度

buttons：

- 类型：数组
- 默认值：无
- 描述：tuberBar按钮设置
- 备注：按钮个数为奇数
- 内部字段：

```js
[{
    frame:         //（可选项）按钮图标的坐标和宽高，json对象，默认值见内部字段
                     内部字段：{
                       w:  //（可选项）按钮图标的宽度，数字类型，默认20
                       h:  //（可选项）按钮图标的高度，数字类型，默认20
                     } 
	normal:        //按钮常态下的背景图片路径，支持widget，fs等本地路径
    highlight：     //（可选项）按钮高亮态下的背景图片路径，支持widget，fs等本地路径，若不传或传空则显示normal
    selected：     //（可选项）按钮选中后的背景图片路径，支持widget，fs等本地路径，若不传或传空则显示normal
    title：         //（可选项）按钮下面的标题文字，字符串类型，若不传或传空则不显示标题
    titleColor：    //（可选项）按钮下面的标题文字的颜色，支持rgb、rgba、#，字符串类型，默认#696969
    titleSize：     //（可选项）按钮下面的标题文字大小，默认12，数字类型
    titleNormal：   //（可选项）按钮下面的标题文字常态颜色，支持rgb、rgba、#，字符串类型，默认#696969
    titleLight：    //（可选项）按钮下面的标题文字高亮颜色，支持rgb、rgba、#，字符串类型，默认#696969
    titleSelected： //（可选项）按钮下面的标题文字选中后颜色，支持rgb、rgba、#，字符串类型,默认#ff0000
}]
```

selectedIndex：

- 类型：数字
- 默认值：无
- 描述：（可选项）默认选中按钮的索引
- 备注：若不传则没有选择项


##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    index:		//点击某个按钮返回其下标
}
```

##示例代码

```js
       var obj = api.require('tuberBar');
       obj.open({
		   bg:'widget://res/tuberBar_bg.png',
		   selectedIndex:3,
		   buttons:[{title:'buttons1',normal:"widget://image/tabBar_bg.png"},
		          {title:'buttons2',normal:"widget://image/tabBar_bg.png"},
		          {title:'buttons3',normal:"widget://image/tabBar_bg.png"},
		          {title:'buttons4',normal:"widget://image/tabBar_bg.png"},
		          {title:'buttons5',normal:"widget://image/tabBar_bg.png"},
		          {title:'buttons6',normal:"widget://image/tabBar_bg.png"},
		          {title:'buttons7',normal:"widget://image/tabBar_bg.png"},
		          {title:'buttons8',normal:"widget://image/tabBar_bg.png"},
		          {title:'buttons9',normal:"widget://image/tabBar_bg.png"},
		          {title:'buttons10',normal:"widget://image/tabBar_bg.png"},
		          {title:'buttons11',normal:"widget://image/tabBar_bg.png"}]
	},function(ret,err){
         alert(JSON.stringify(ret) + JSON.stringify(err));
	});
```

##补充说明

打开tuberBar

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setSelected**<div id=“2”></div>

设置选中按钮

setSelected({params})
 
##params
 
index：
- 类型：数字
- 默认值：0
- 描述：（可选项）要设置的按钮的索引

selected：
- 类型：布尔
- 默认值：true
- 描述：（可选项）要设置的按钮的状态

##示例代码

    var obj = api.require('tuberBar');
    obj.setSelected({index:1});

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setBadge**<div id="3"></div>

设置按钮左上角的徽章

setBadge(params)

##params

index:

- 类型：数字
- 默认值：0
- 说明：（可选项）要设置的按钮的下标

badge：

- 类型：字符串
- 默认值：无
- 说明：（可选项）要设置的徽章
- 备注：若不传则表示清除已显示的徽章，若传空字符串则显示小红点

##示例代码

```js
var obj = api.require('tuberBar');
obj.setBadge({
	index:3,
    badge:'说明'
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**hide**<div id="4"></div>

隐藏tuberBar

hide();

##示例代码

    var obj = api.require('tuberBar');
    obj.hide();

##补充说明

将打开的tuberBar以移动动画的形式移出到屏幕下方</del>

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**show**<div id="5"></div>

显示隐藏的tuberBar

show();

##示例代码

    var obj = api.require('tuberBar');
    obj.show();

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**close**<div id="6"></div>

关闭tuberBar

close()

##示例代码

    var obj = api.require('tuberBar');
    obj.close();

##补充说明

将打开的tuberBar从内存清除

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**bringToFront**<div id="7"></div>

将已经打开的模块置为最上层显示

bringToFront()

##示例代码

    var obj = api.require('tuberBar');
    obj.bringToFront();

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
