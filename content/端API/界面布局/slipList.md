/*
Title: slipList
Description: slipList
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[close](#2)

[reloadData](#3)

[deleteItem](#4)

[insertItem](#5)

[refreshItem](#6)

[appendData](#7)

[setRefreshHeader](#8)

[setRefreshFooter](#9)

[show](#10)

[hide](#11)
</div>

#**概述**

slipList封装了一个列表控件，可实现一个可左右拖动item的列表视图。开发者可根据需求自定义列表的元素布局，亦可自定义相关字段的样式。支持设置下拉刷新和上拉加载更多事件。支持删除、刷新、插入指定下标（index）的item数据。本模块是有第三方模块开发者提供，使用本模块需在线云编译安装包

![图片说明](/img/docImage/slipList.jpg)

#**open**<div id="1"></div>

打开

open({params}, callback(ret, err))

##params

x：

- 类型：数字
- 默认值：0
- 描述：列表视图的左上角点的坐标，可为空

y：

- 类型：数字
- 默认值：64
- 描述：列表视图的左上角点的坐标，可为空

w：

- 类型：数字
- 默认值：当前设备屏幕宽度
- 描述：列表视图的宽，可为空

h：

- 类型：数字
- 默认值：w+100
- 描述：列表视图的高，可为空

leftBtn：

- 类型：数组对象
- 默认值：无
- 描述：往右滑动item露出的按钮组成的数组，可为空，为空时则表示item不可向右滑动

内部字段：

```js
[{
	bg:         	//按钮背景色，支持rgb，rgba，#，默认#ee8262，可为空
    title:         //按钮名字，字符串类型，默认‘按钮’，可为空
	titleSize:      //按钮标题大小，数字类型，默认13，可为空
	titleColor:     //按钮标题颜色，支持rgb，rgba，#，默认#ffffff，可为空
	selectedColor//按钮选中时候的颜色值,支持rgb，rgba，#，可为空,为空则无选中变化
}]
```

leftBg：

- 类型：字符串
- 默认值：#5cacee
- 描述：往右滑动item露出的视图的背景色，支持rgb，rgba，#，可为空

rightBtn：

- 类型：数组对象
- 默认值：无
- 描述：往左滑动item露出的按钮组成的数字，可为空，为空时则表示item不可向左滑动

内部字段：

```js
[{
	bg:         	//按钮背景色，支持rgb，rgba，#，默认#388e8e，可为空
    title:         //按钮名字，字符串类型，默认‘按钮’，可为空
	titleColor:     //按钮标题颜色，支持rgb，rgba，#，默认#ffffff，可为空
	selectedColor//按钮选中时候的颜色值,支持rgb，rgba，#，可为空,为空则无选中变化
}]
```

rightBg：

- 类型：字符串
- 默认值：#6c7b8b
- 描述：往左滑动item露出的视图的背景色，支持rgb，rgba，#，可为空

itemStyle：

- 类型：json对象
- 默认值：见内部字段
- 描述：item样式配置，可为空

内部字段：

```js
{
	borderColor:  //item间分割线颜色，支持rgb，rgba，#，默认#696969，可为空
	bgColor:     //item背景色，支持rgb，rgba，#，默认#AFEEEE，可为空
	selectedColor//item背景选中色,支持rgb，rgba，#，默认#f5f5f5可为空
    height:       //一条item的高度，数字类型，默认55，可为空
	avatarH：//头像（上下居中）的高(不可超过height)，数字类型，默认45，可为空
	avatarW:     //头像（距左边框距离和上下相等）的宽，数字类型，默认45，可为空
	placeholderImg//头像为网络资源时的占位图,仅支持本地路径协议,有默认图标，可为空
	titleSize：//标题字体大小，数字类型，默认10，可为空
	titleColor     //标题字体颜色，支持rgb,rgba,#，默认：#696969,可为空
	headlineSize：//大标题字体大小，数字类型，默认15，可为空
	headlineColor //大标题字体颜色，支持rgb,rgba,#，默认：#388e8e,可为空
	subTitleSize   //子标题字体大小，数字类型，默认13，可为空
	subTitleColor  //子标题字体颜色，支持rgb,rgba,#，默认：#000000,可为空
	remarkSize:   //备注字体的大学，数字类型，默认15，可为空
	remarkColor:  //备注字体的颜色，支持rgb,rgba,#,默认#696969，可为空
	remarkMargin //备注距离右边的边距，数字类型，默认10，可为空
}
```

datas：

- 类型：数组对象
- 默认值：无
- 描述：数据源，可为空

内部字段：

```js
[{
	img:       //头像图片路径,支持本地和网络路径资源,网络图片会被缓存到本地,可为空若为空，则item内其余内容占位(与边框距离和remarkMargin一致)显示
	title:       //标题，字符串类型，可为空，为空时不显示
	headline:   //大标题，可为空，为空时不显示,且subTitleIcon和sutTitle占位显示
	subTitle//子标题，字符串类型，可为空，为空时不显示
	remark//备注，字符串类型，可为空，为空时不显示
	titleIcon:   //标题icon图片路径,仅支持本地协议,可为空,为空则不显示且title占位显示
	subTitleIcon//小标题icon图片路径,本地路径,可为空,若空不显示且subTitle占位显示
}]
```

fixedOn：

- 类型：字符串
- 默认值：当前主窗口的名字
- 描述：将此模块视图添加到指定窗口的名字，可为空

fixed:
- 类型：布尔
- 默认值：true
- 描述：是否将模块视图固定到窗口上，不跟随窗口上下滚动，可为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	eventType:      	//事件类型，取值范围如下：
                            item：点击的item
	leftBtn:点击的左边按钮
	rightBtn点击右边按钮
    index:          	//点击item的下标
	btnIndex：//点击item下的侧滑按钮下标
}
```

##示例代码

```js
var obj = api.require('slipList');
obj.open({
	datas:[{
		img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
		title:'12:00',
		headline:'刘德华',
		subTitle:'APICloud粉丝见面会',
		titleIcon:'widget://image/slipList_watch.png',
		subTitleIcon:'widget://image/slipList_star.png',
		remark:'完成'
	},{
		img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
		title:'12:00',
		headline:'刘德华',
		subTitle:'APICloud粉丝见面会',
		titleIcon:'widget://image/slipList_watch.png',
		subTitleIcon:'widget://image/slipList_star.png',
		remark:'完成'
	},{
		img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
		title:'12:00',
		headline:'刘德华',
		subTitle:'APICloud粉丝见面会',
		titleIcon:'widget://image/slipList_watch.png',
		remark:'完成'
	},{
		img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
		title:'12:00',
		headline:'刘德华',
		subTitle:'APICloud粉丝见面会',
		titleIcon:'widget://image/slipList_watch.png',
		subTitleIcon:'widget://image/slipList_star.png',
		remark:'完成'
	},{
		img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
		title:'12:00',
		headline:'刘德华',
		subTitle:'APICloud粉丝见面会',
		titleIcon:'widget://image/slipList_watch.png',
		subTitleIcon:'widget://image/slipList_star.png',
		remark:'完成'
	},{
		img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
		title:'12:00',
		headline:'刘德华',
		subTitle:'APICloud粉丝见面会',
		titleIcon:'widget://image/slipList_watch.png',
		subTitleIcon:'widget://image/slipList_star.png',
		remark:'完成'
	},{
		img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
		title:'12:00',
		headline:'刘德华',
		subTitle:'APICloud粉丝见面会',
		titleIcon:'widget://image/slipList_watch.png',
		subTitleIcon:'widget://image/slipList_star.png',
		remark:'完成'
	},{
		img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
		title:'12:00',
		headline:'刘德华',
		subTitle:'APICloud粉丝见面会',
		titleIcon:'widget://image/slipList_watch.png',
		subTitleIcon:'widget://image/slipList_star.png',
		remark:'完成'
	},{
		img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
		title:'12:00',
		headline:'刘德华',
		subTitle:'APICloud粉丝见面会',
		titleIcon:'widget://image/slipList_watch.png',
		subTitleIcon:'widget://image/slipList_star.png',
		remark:'完成'
	},{
	img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
	title:'12:00',
	headline:'刘德华',
	subTitle:'APICloud粉丝见面会',
	titleIcon:'widget://image/slipList_watch.png',
	subTitleIcon:'widget://image/slipList_star.png',
	remark:'完成'
	},{
	img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
	title:'12:00',
	headline:'刘德华',
	subTitle:'APICloud粉丝见面会',
	titleIcon:'widget://image/slipList_watch.png',
	subTitleIcon:'widget://image/slipList_star.png',
	remark:'完成'
	}]
},function(ret,err){
	api.alert({msg:ret.index+'*'+ret.eventType});
});
```

##补充说明

打开列表视图

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**close**<div id="2"></div>

关闭slipList列表视图

close()

##示例代码

	var obj = api.require('slipList');
	obj.close();

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**reloadData**<div id="3"></div>

刷新列表数据

reloadData({params})

##params

datas：

- 类型：数组对象
- 默认值：无
- 描述：数据源，可为空，为空时仅停止下拉刷新状态

内部字段：

```js
[{
	img:       //头像图片路径,支持本地和网络路径资源,网络图片会被缓存到本地,可为空若为空，则item内其余内容占位(与边框距离和remarkMargin一致)显示
	title:       //标题，字符串类型，可为空，为空时不显示
	headline:   //大标题，可为空，为空时不显示,且subTitleIcon和sutTitle占位显示
	subTitle//子标题，字符串类型，可为空，为空时不显示
	remark     //备注，字符串类型，可为空，为空时不显示
	titleIcon:   //标题icon图片路径,仅支持本地协议,可为空,为空则不显示且title占位显示
	subTitleIcon//小标题icon图片路径,本地路径,可为空,若空不显示且subTitle占位显示
}]
```

##示例代码

```
var obj = api.require('slipList');
obj.reloadData({
	datas:[{
		img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
		title:'12:00',
		headline:'张学友',
		subTitle:'APICloud粉丝交流会',
		titleIcon:'widget://image/slipList_watch.png',
		subTitleIcon:'widget://image/slipList_star.png',
		remark:'完成'
	},{
		img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
		title:'12:00',
		headline:'张学友',
		subTitle:'APICloud粉丝交流会',
		titleIcon:'widget://image/slipList_watch.png',
		subTitleIcon:'widget://image/slipList_star.png',
		remark:'完成'
	},{
		img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
		title:'12:00',
		headline:'张学友',
		subTitle:'APICloud粉丝交流会',
		titleIcon:'widget://image/slipList_watch.png',
		subTitleIcon:'widget://image/slipList_star.png',
		remark:'完成'
	},{
		img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
		title:'12:00',
		headline:'张学友',
		subTitle:'APICloud粉丝交流会',
		titleIcon:'widget://image/slipList_watch.png',
		subTitleIcon:'widget://image/slipList_star.png',
		remark:'完成'
	},{
		img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
		title:'12:00',
		headline:'张学友',
		subTitle:'APICloud粉丝交流会',
		titleIcon:'widget://image/slipList_watch.png',
		subTitleIcon:'widget://image/slipList_star.png',
		remark:'完成'
	},{
		img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
		title:'12:00',
		headline:'张学友',
		subTitle:'APICloud粉丝交流会',
		titleIcon:'widget://image/slipList_watch.png',
		subTitleIcon:'widget://image/slipList_star.png',
		remark:'完成'
	},{
		img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
		title:'12:00',
		headline:'张学友',
		subTitle:'APICloud粉丝交流会',
		titleIcon:'widget://image/slipList_watch.png',
		subTitleIcon:'widget://image/slipList_star.png',
		remark:'完成'
	},{
		img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
		title:'12:00',
		headline:'张学友',
		subTitle:'APICloud粉丝交流会',
		titleIcon:'widget://image/slipList_watch.png',
		subTitleIcon:'widget://image/slipList_star.png',
		remark:'完成'
	},{
		img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
		title:'12:00',
		headline:'张学友',
		subTitle:'APICloud粉丝交流会',
		titleIcon:'widget://image/slipList_watch.png',
		subTitleIcon:'widget://image/slipList_star.png',
		remark:'完成'
	},{
		img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
		title:'12:00',
		headline:'张学友',
		subTitle:'APICloud粉丝交流会',
		titleIcon:'widget://image/slipList_watch.png',
		subTitleIcon:'widget://image/slipList_star.png',
		remark:'完成'
	},{
		img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
		title:'12:00',
		headline:'张学友',
		subTitle:'APICloud粉丝交流会',
		titleIcon:'widget://image/slipList_watch.png',
		subTitleIcon:'widget://image/slipList_star.png',
		remark:'完成'
	}]
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**deleteItem**<div id="4"></div>

删除指定索引的数据

deleteItem({params})

##params

index：

- 类型：数字
- 默认值：无
- 描述：要删除的数据的索引下标，可为空，为空则删除最后一条数据

##示例代码

```js
var obj = api.require('slipList');
obj.deleteItem({
	index:2
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**insertItem**<div id="5"></div>

插入指定索引的数据

insertItem({params})

##params

index：

- 类型：数字
- 默认值：无
- 描述：要插入的数据的索引下标，可为空，为空则拼接到最后一条数据

data：

- 类型：json对象
- 默认值：无
- 描述：数据源，不可为空

内部字段：

```js
{
	img:       //头像图片路径,支持本地和网络路径资源,网络图片会被缓存到本地,可为空若为空，则item内其余内容占位(与边框距离和remarkMargin一致)显示
	title:       //标题，字符串类型，可为空，为空时不显示
	headline:   //大标题，可为空，为空时不显示,且subTitleIcon和sutTitle占位显示
	subTitle//子标题，字符串类型，可为空，为空时不显示
	remark     //备注，字符串类型，可为空，为空时不显示
	titleIcon:   //标题icon图片路径,仅支持本地协议,可为空,为空则不显示且title占位显示
	subTitleIcon//小标题icon图片路径,本地路径,可为空,若空不显示且subTitle占位显示
}
```

##示例代码

```js
var obj = api.require('slipList');
obj.insertItem({
	index:2,
	data:{
		img:'http://d.hiphotos.baidu.com/image/pic/item/4d086e061d950a7b29a788c209d162d9f2d3c922.jpg ',
		title:'12:00',
		headline:'小张',
		subTitle:'APICloud粉丝互动会',
		titleIcon:'widget://image/slipList_watch.png',
		subTitleIcon:'widget://image/slipList_star.png',
		remark:'完成'
	}
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**refreshItem**<div id="6"></div>

刷新指定index条目的数据

refreshItem({params})

##params

index：

- 类型：数字
- 默认值：无
- 描述：要刷新数据的item索引下标，可为空，为空则不刷新

data：

- 类型：json对象
- 默认值：无
- 描述：数据源，不可为空

内部字段：

```js
{
	img:       //头像图片路径,支持本地和网络路径资源,网络图片会被缓存到本地,可为空若为空，则item内其余内容占位(与边框距离和remarkMargin一致)显示
	title:       //标题，字符串类型，可为空，为空时不显示
	headline:   //大标题，可为空，为空时不显示,且subTitleIcon和sutTitle占位显示
	subTitle//子标题，字符串类型，可为空，为空时不显示
	remark     //备注，字符串类型，可为空，为空时不显示
	titleIcon:   //标题icon图片路径,仅支持本地协议,可为空,为空则不显示且title占位显示
	subTitleIcon//小标题icon图片路径,本地路径,可为空,若空不显示且subTitle占位显示
}
```

##示例代码

```js
var obj = api.require('slipList');
obj.refreshItem({
	index:2,
	data:{
		img:'http://d.hiphotos.baidu.com/image/pic/item/4d086e061d950a7b29a788c209d162d9f2d3c922.jpg ',
		title:'12:00',
		headline:'小张',
		subTitle:'APICloud粉丝互动会',
		titleIcon:'widget://image/slipList_watch.png',
		subTitleIcon:'widget://image/slipList_star.png',
		remark:'完成'
	}
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**appendData**<div id="7"></div>

往列表拼接数据

appendData({params})

##params

datas：

- 类型：数组对象
- 默认值：无
- 描述：数据源，可为空，为空时仅停止上拉加载更多状态

内部字段：

```js
[{
	img:       //头像图片路径,支持本地和网络路径资源,网络图片会被缓存到本地,可为空若为空，则item内其余内容占位(与边框距离和remarkMargin一致)显示
	title:       //标题，字符串类型，可为空，为空时不显示
	headline:   //大标题，可为空，为空时不显示,且subTitleIcon和sutTitle占位显示
	subTitle//子标题，字符串类型，可为空，为空时不显示
	remark     //备注，字符串类型，可为空，为空时不显示
	titleIcon:   //标题icon图片路径,仅支持本地协议,可为空,为空则不显示且title占位显示
	subTitleIcon//小标题icon图片路径,本地路径,可为空,若空不显示且subTitle占位显示
}]
```

##示例代码

```js
var obj = api.require('slipList');
obj.appendData({
	datas:[{
		img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
		title:'12:00',
		headline:'莱昂纳多',
		subTitle:'APICloud粉丝见面会',
		titleIcon:'widget://image/slipList_watch.png',
		subTitleIcon:'widget://image/slipList_star.png',
		remark:'完成'
	},{
		img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
		title:'12:00',
		headline:'莱昂纳多',
		subTitle:'APICloud粉丝见面会',
		titleIcon:'widget://image/slipList_watch.png',
		subTitleIcon:'widget://image/slipList_star.png',
		remark:'完成'
	},{
		img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
		title:'12:00',
		headline:'莱昂纳多',
		subTitle:'APICloud粉丝见面会',
		titleIcon:'widget://image/slipList_watch.png',
		subTitleIcon:'widget://image/slipList_star.png',
		remark:'完成'
	},{
		img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
		title:'12:00',
		headline:'莱昂纳多',
		subTitle:'APICloud粉丝见面会',
		titleIcon:'widget://image/slipList_watch.png',
		subTitleIcon:'widget://image/slipList_star.png',
		remark:'完成'
	},{
		img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
		title:'12:00',
		headline:'莱昂纳多',
		subTitle:'APICloud粉丝见面会',
		titleIcon:'widget://image/slipList_watch.png',
		subTitleIcon:'widget://image/slipList_star.png',
		remark:'完成'
	},{
		img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
		title:'12:00',
		headline:'莱昂纳多',
		subTitle:'APICloud粉丝见面会',
		titleIcon:'widget://image/slipList_watch.png',
		subTitleIcon:'widget://image/slipList_star.png',
		remark:'完成'
	},{
		img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
		title:'12:00',
		headline:'莱昂纳多',
		subTitle:'APICloud粉丝见面会',
		titleIcon:'widget://image/slipList_watch.png',
		subTitleIcon:'widget://image/slipList_star.png',
		remark:'完成'
	},{
		img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
		title:'12:00',
		headline:'莱昂纳多',
		subTitle:'APICloud粉丝见面会',
		titleIcon:'widget://image/slipList_watch.png',
		subTitleIcon:'widget://image/slipList_star.png',
		remark:'完成'
	},{
		img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
		title:'12:00',
		headline:'莱昂纳多',
		subTitle:'APICloud粉丝见面会',
		titleIcon:'widget://image/slipList_watch.png',
		subTitleIcon:'widget://image/slipList_star.png',
		remark:'完成'
	},{
		img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
		title:'12:00',
		headline:'莱昂纳多',
		subTitle:'APICloud粉丝见面会',
		titleIcon:'widget://image/slipList_watch.png',
		subTitleIcon:'widget://image/slipList_star.png',
		remark:'完成'
	},{
		img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
		title:'12:00',
		headline:'莱昂纳多',
		subTitle:'APICloud粉丝见面会',
		titleIcon:'widget://image/slipList_watch.png',
		subTitleIcon:'widget://image/slipList_star.png',
		remark:'完成'
	}]
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setRefreshHeader**<div id="8"></div>

设置下拉刷新样式

setRefreshHeader({params} ,callback(ret,err))

##params

loadingImg：

- 类型：字符串
- 默认值：无
- 描述：下拉刷新的小箭头本地图片的路径，可为空，为空则不显示箭头图标

bgColor:

- 类型：字符串
- 默认值：#f5f5f5
- 描述：下拉刷新视图的背景色，支持rgb，rgba，#，可为空

textColor：

- 类型：字符串
- 默认值：#8e8e8e
- 描述：提示文字颜色，支持rgb，rgba，#，可为空

textDown：

- 类型;字符串
- 默认值：下拉可以刷新…
- 描述;提示文字，可为空

textUp：

- 类型：字符串
- 默认值:松开开始刷新…
- 描述;提示文字，可为空

showTime：

- 类型：布尔值
- 默认值：true
- 描述：是否显示刷新时间，可为空

##callback

返回触发刷新事件

##示例代码

```js
var loadingImgae = 'widget://res/slipList_arrow.png';//刷新的小箭头
var bgColor = '#F5F5F5';//下拉刷新的背景颜色，有默认值，可为空
var textColor= '#8E8E8E';//提示语颜色，有默认值，可为空
var textDown= '下拉可以刷新...';//尚未触发刷新时间的提示语，有默认值，可为空
var textUp= '松开开始刷新...';//触发刷新事件的提示语，有默认值，可为空
var showTime= true;//是否显示时间，有默认值，可为空

var obj = api.require('slipList');
obj.setRefreshHeader({
	loadingImg : loadingImgae,
	bgColor:bgColor,
	textColor:textColor,
	textDown:textDown,
	textUp:textUp,
	showTime : showTime
},function(ret,err){
//触发加载事件
});
```

#**补充说明**

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setRefreshFooter**<div id="9"></div>

设置上拉加载更多样式

setRefreshFooter({params} ,callback(ret,err))

##params

loadingImg：

- 类型：字符串
- 默认值：无
- 描述：上拉加载更多的小箭头本地图片的路径，可为空，为空则不显示该图标

bgColor:

- 类型：字符串
- 默认值：#f5f5f5
- 描述：上拉加载视图的背景色，支持rgb，rgba，#，可为空

textColor：

- 类型：字符串
- 默认值：#8e8e8e
- 描述：提示文字颜色，支持rgb，rgba，#，可为空

textDown：

- 类型;字符串
- 默认值：上拉可以加载更多…
- 描述;提示文字，可为空

textUp：

- 类型：字符串
- 默认值:松开开始加载…
- 描述;提示文字，可为空

showTime：

- 类型：布尔值
- 默认值：true
- 描述：是否显示加载时间，可为空

##示例代码

```js
var loadingImgae = 'widget://res/slipList_arrow.png';//刷新的小箭头
var bgColor = '#F5F5F5';//下拉刷新的背景颜色，有默认值，可为空
var textColor= '#8E8E8E';//提示语颜色，有默认值，可为空
var textDown= '上拉可加载更多...';//尚未触发刷新时间的提示语，有默认值，可为空
var textUp= '松开开始加载...';//触发刷新事件的提示语，有默认值，可为空
var showTime= true;//是否显示时间，有默认值，可为空
var obj = api.require('slipList');
obj.setRefreshFooter({
	loadingImg : loadingImgae,
	bgColor:bgColor,
	textColor:textColor,
	textDown:textDown,
	textUp:textUp,
	showTime : showTime
},function(ret,err){
        //触发加载事件
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**show**<div id="10"></div>

显示slipList列表视图

show()

##示例代码

	var obj = api.require('slipList');
	obj.show();

##补充说明

显示已隐藏的列表视图

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**hide**<div id="11"></div>

隐藏slipList列表视图

hide()

示例代码

	var obj = api.require('slipList');
	obj.hide();

##补充说明

隐藏slipList，并没有从内存里清除

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

