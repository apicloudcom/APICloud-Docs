/*
Title: tabBar
Description: tabBar
*/

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

tabBar是一个底部导航条模块，开发者可自定义其样式，当子按钮个数超出屏幕时，用户可左右拖动查看

![图片说明](/img/docImage/tabBar.jpg)

#**open**<div id="1"></div>

打开

open({params}, callback(ret, err))

##params

bgImg：

- 类型：字符串
- 默认值：无
- 描述：tabBar的背景图片路径，不能为空

selectImg：

- 类型：字符串
- 默认值：无
- 描述：选中按钮后的按钮背景效果图片路径，可为空

perScreenBtn：

- 类型：数字
- 默认值：5
- 描述：每屏显示按钮的个数，可为空

items：

- 类型：数组
- 默认值：无
- 描述：多个按钮的信息组成的数组，不能为空

内部字段：

```js
[{
	 img:                //按钮图片路径，字符串，不可为空
    highlight：          //按钮按下时的背景图片，字符串，可为空
    selected:            //按钮选中后的图片，字符串，可为空
    title:               //按钮的标题，字符串，不可为空
    color：              //标题的颜色，字符串，可为空，默认白色
    selectedTitleColor:  //选中后的按钮标题颜色，默认白色，支持rgb,rgba,#,可为空
    badge：			     //按钮左上角的badge，字符串类型，可为空，为空时不显示badge
}]
```

fixedOn：

- 类型：字符串
- 默认值：当前主窗口的名字
- 描述：将此模块视图添加到指定窗口的名字，可为空

selecteIndex：

- 类型：数字
- 默认值：无
- 描述：默认选中按钮的下标，可为空，若为空则都不选中

h：

- 类型：数字
- 默认值：50
- 描述：模块视图的高，可为空

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
var obj = api.require('tabBar');
obj.open({
	bgImg:'widget://res/tabBar_bg.png',
	selectImg:'widget://res/selecte_tabBar.png',
	items:[{title:'item1',img:'widget://res/tabBar_item1.png',badge:'1'},
          {title:'item2',img:'widget://res/tabBar_item1.png'},
          {title:'item3',img:'widget://res/tabBar_item1.png',badge:'2'},
          {title:'item4',img:'widget://res/tabBar_item1.png'},
          {title:'item5',img:'widget://res/tabBar_item1.png',badge:'2'},
          {title:'item6',img:'widget://res/tabBar_item1.png',badge:'200000'},
          {title:'item7',img:'widget://res/tabBar_item1.png',badge:'2'},
          {title:'item8',img:'widget://res/tabBar_item1.png',badge:'2'},
          {title:'item9',img:'widget://res/tabBar_item1.png',badge:'2'},
          {title:'item10',img:'widget://res/tabBar_item1.png',badge:'2'},
          {title:'item11',img:'widget://res/tabBar_item1.png',badge:'2'}]
},function(ret,err){
	api.alert({msg:ret.index});
});
```

##补充说明

打开tabBar

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**setBadge**<div id="2"></div>

设置按钮左上角的badge标注

setBadge(params)

##params

index:

- 类型：数字
- 默认值：无
- 说明：要设置的按钮的下标，不可为空

badge：

- 类型：字符串
- 默认值：无
- 说明：要设置的标注，可为空

##示例代码

```js
var obj = api.require('tabBar');
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

#**<del>hidden</del>**<div id="3"></div>

<del>隐藏tabBar</del>

<del>hidden();</del>

##<del>示例代码</del>

    var obj = api.require('tabBar');
    obj.hidden();

##<del>补充说明</del>

<del>将打开的tabBar以移动动画的形式移出到屏幕下方</del>

##<del>可用性</del>

<del>iOS系统，Android系统</del>

<del>可提供的1.0.1及更高版本</del>


#**hide**<div id="3"></div>

隐藏tabBar

hide();

##示例代码

    var obj = api.require('tabBar');
    obj.hide();

##补充说明

将打开的tabBar以移动动画的形式移出到屏幕下方</del>

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**show**<div id="4"></div>

显示隐藏的tabBar

show();

##示例代码

    var obj = api.require('tabBar');
    obj.show();

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**close**<div id="5"></div>

关闭tabBar

close()

##示例代码

    var obj = api.require('tabBar');
    obj.close();

##补充说明

将打开的tabBar从内存清除

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setSelect**<div id=“6”></div>

设置选中按钮

setSelect({params})
 
##params
 
index：
- 类型：数字
- 默认值：0
- 描述：要设置的按钮的下标，可为空

##示例代码

    var obj = api.require('tabBar');
    obj.setSelect({index:1});

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
