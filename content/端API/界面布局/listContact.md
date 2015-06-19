/*
Title: listContact
Description: listContact
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[close](#2)

[reloadData](#3)

[setRefreshHeader](#4)

[hide](#5)

[show](#6)

[deleteItem](#7)

[refreshItem](#8)

[insertItem](#9)
</div>

#**概述**

listContact定义了一个类似微信联系人界面的模板，开发者可自定义数据源，ui界面里的各种元素的样式等

![图片说明](/img/docImage/listContact.jpg)

#**open**<div id="1"></div>

打开

open({params}, callback(ret, err))

##params

x：

- 类型：数字
- 默认值：0
- 描述：（可选项）列表视图的左上角点的坐标

y：

- 类型：数字
- 默认值：0
- 描述：（可选项）列表视图的左上角点的坐标

w：

- 类型：数字
- 默认值：当前屏幕宽度
- 描述：（可选项）列表视图的宽

h：

- 类型：数字
- 默认值：当前屏幕的高
- 描述：（可选项）列表视图的高

bgColor：

- 类型：字符串
- 默认值：#FFFFFF
- 描述：（可选项）当前屏幕宽度列表的背景色，支持rgb，rgba，#

groupTitle:

- 类型：json对象
- 默认值：见内部字段
- 描述：（可选项）配置组标题的字体颜色和大小

内部字段：

```js
{
    color:          //（可选项）字符串类型，默认#949494,支持rgb，rgba，#
    size:           //（可选项）数字类型，默认13
	 bgColor:        //（可选项）标题背景色，默认#DBDBDB,支持rgb，rgba，#
}
```

leftBtn：

- 类型：数组对象
- 默认值：无
- 描述：（可选项）往右滑动cell露出的按钮组成的数字
- 备注：若不传则表示cell不可向右滑动

内部字段：

```js
[{
    color:         	//按钮背景色，支持rgb，rgba，#
    title:          //按钮名字
	selectColor		//按钮选中时候的颜色值，支持rgb，rgba，#
}]
```

leftBg：

- 类型：字符串
- 默认值：#5cacee
- 描述：（可选项）往右滑动cell露出的视图的背景色，支持rgb，rgba，#

rightBtn：

- 类型：数组对象
- 默认值：无
- 描述：（可选项）往左滑动cell露出的按钮组成的数组
- 备注：若不传则表示cell不可向左滑动

内部字段：

```js
[{
    color:        		//按钮背景色，支持rgb，rgba，#
    title:           	//按钮名字，支持rgb，rgba，#
	 selectColor			//按钮选中时候的颜色值，支持rgb，rgba，#
}]
```

rightBg：

- 类型：字符串
- 默认值：#6c7b8b
- 描述：（可选项）往左滑动cell露出的视图的背景色，支持rgb，rgba，#

borderColor：

- 类型：字符串
- 默认值：#696969
- 描述：（可选项）每个cell之间分割线的颜色，支持rgb，rgba，#

cellBgColor：

- 类型：字符串
- 默认值:#AFEEEE
- 描述：（可选项）cell的背景色，支持rgb，rgba，#

cellSelectColor：

- 类型：字符串
- 默认值：#F5F5F5
- 描述：（可选项）选中cell时的颜色，支持rgb，rgba，#

cellHeight：

- 类型：数字
- 默认值：55
- 描述：（可选项）每个cell的高度

imgHeight：

- 类型：数字
- 默认值：cellHeight-10
- 描述：（可选项）头像的高

imgWidth：

- 类型：数字
- 默认值：imgHeight
- 描述：（可选项）头像的宽

data：

- 类型：json对象
- 默认值：无
- 描述：列表数据源，必传项
- 内部字段：

```js
{
	common: [{                 //区域标题，字符串类型
		img:               		//（可选项）cell的头像，，支持http、https、widget、fs等网络和本地图片路径协议，网络图片会被缓存到本地
		placeholderImg:         //（可选项）头像,本地路径,加载网络图片时显示界面上的图，可为空
		title:               	//（可选项）cell的标题，若subtitle为空时，title上下居中位置
		subTitle:           	//（可选项）cell的子标题，为空时title上下居中显示
		titleLocation 			//（可选项）标题在水平线上的位置center,left,right，默认left
		titleSize				//（可选项）标题字体的大小，默认12
		titleColor				//（可选项）标题字体的颜色值，默认黑色，支持rgb，rgba，#
		subTitleLocation 		//（可选项）子标题在水平线上的位置center,left,right默认left
		subTitleSize			//（可选项）子标题字体的大小，默认12
		subTitleColor			//（可选项）子标题字体的颜色值,默认黑色,支持rgb，rgba，#
}],
A:[{}],
B:[{}],,,,,,
}
```

indicator:

- 类型：json对象
- 默认值：无
- 描述：（可选项）是否添加右边索引导航条
- 备注：若不传则不显示右边索引导航条
- 内部字段：

```js
{
	bgColor:       	//（可选项）背景色，字符串，默认透明，支持rgb，rgba，#
	color：			//（可选项）索引指器颜色,字符串类型，默认#A1A1A1,支持rgb，rgba，#
}
```

fixedOn:

- 类型：字符串
- 默认值：当前主窗口名
- 描述：（可选项）将模块视图添加在某个窗口上的名字

searchBar:

- 类型：json对象
- 默认值：无
- 描述：（可选项）搜索条设置
- 备注：若不传则不显示搜索条
- 内部字段：

```js
{
	bgColor:       	//（可选项）搜索条背景色，字符串，默认透明，支持rgb，rgba，#
	cancelColor:    //（可选项）取消文字的颜色，字符串类型，默认#A1A1A1,支持rgb，rgba，#
	placeholder:    //（可选项）搜索条提示文字，字符串类型，默认空，不传则不显示提示文字
	h:              //（可选项）搜索框的高度，数字类型，默认44
}
```

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    index:          	//点击某个cell所在区域内的cell的下标
	section:            //被点击的cell所在的区域的下标 
	key：               //被点击的cell的区域的key
	clickType:        	//点击类型，0-cell；1-右边按钮；2-左边的按钮
	btnIndex:       	//点击按钮时返回其下标
}
```

##示例代码

```js
var obj = api.require('listContact');
obj.open({
    h: 300,
    rightBtn: [{
        color: '#8B0000',
        title: '备注'
    }],
    data: {
        common: [{
            placeholderImg: 'widget://res/listContact.png',
            img: 'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
            title: '标题'
        }],
        A: [{
            placeholderImg: 'widget://res/listContact.png',
            img: 'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
            title: '标题'
        }, {
            placeholderImg: 'widget://res/listContact.png',
            title: '标题'
        }, {
            placeholderImg: 'widget://res/listContact.png',
            title: '标题'
        }, {
            placeholderImg: 'widget://res/listContact.png',
            title: '标题'
        }, {
            placeholderImg: 'widget://res/listContact.png',
            title: '标题'
        }, {
            placeholderImg: 'widget://res/listContact.png',
            title: '标题'
        }, {
            placeholderImg: 'widget://res/listContact.png',
            title: '标题'
        }, {
            placeholderImg: 'widget://res/listContact.png',
            title: '标题'
        }, {
            placeholderImg: 'widget://res/listContact.png',
            title: '标题'
        }, {
            placeholderImg: 'widget://res/listContact.png',
            title: '标题'
        }]
    }
}, function(ret, err) {
    api.alert({
        msg: ret.section + "*" + ret.index
    });
});
```

##补充说明

打开列表视图

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**close**<div id="2"></div>

关闭listContact

close()

##示例代码

	var obj = api.require('listContact');
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

data：

- 类型：JSON对象
- 默认值：无
- 描述：（可选项）刷新的数据源，若不传则仅停止下拉刷新状态

内部字段：

```js
{
	common: [{                 //区域标题，字符串类型
		img:               		//（可选项）cell的头像，，支持http、https、widget、fs等网络和本地图片路径协议，网络图片会被缓存到本地
		placeholderImg:         //（可选项）头像,本地路径,加载网络图片时显示界面上的图，可为空
		title:               	//（可选项）cell的标题，若subtitle为空时，title上下居中位置
		subTitle:           	//（可选项）cell的子标题，为空时title上下居中显示
		titleLocation 			//（可选项）标题在水平线上的位置center,left,right，默认left
		titleSize				//（可选项）标题字体的大小，默认12
		titleColor				//（可选项）标题字体的颜色值，默认黑色，支持rgb，rgba，#
		subTitleLocation 		//（可选项）子标题在水平线上的位置center,left,right默认left
		subTitleSize			//（可选项）子标题字体的大小，默认12
		subTitleColor			//（可选项）子标题字体的颜色值,默认黑色,支持rgb，rgba，#
}],
A:[{}],
B:[{}],,,,,,
}
```

##示例代码

```js
var obj = api.require('listContact');
obj.reloadData({
	data:{
		common:[{
			placeholderImg:'widget://res/listContact.png',
			img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
       		title:'标题'
      	}],
		A:[{
			placeholderImg:'widget://res/listContact.png',
			img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
       		title:'标题'
     	},{
			placeholderImg: 'widget://res/listContact.png',title:'标题'
     	},{
			placeholderImg: 'widget://res/listContact.png',title:'标题' 
     	},{
			placeholderImg:'widget://res/listContact.png',title:'标题'
     	},{
			placeholderImg:'widget://res/listContact.png',title:'标题'
     	},{
			placeholderImg: 'widget://res/listContact.png',title:'标题'
     	},{
			placeholderImg: 'widget://res/listContact.png',title:'标题' 
     	},{
			placeholderImg: 'widget://res/listContact.png',title:'标题'
     	},{
			placeholderImg: 'widget://res/listContact.png',title:'标题'
     	},{
			placeholderImg:'widget://res/listContact.png' ,title:'标题'
     	}]}
},function(ret,err){
				api.alert({msg:ret.section+"*"+ret.index});
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**setRefreshHeader**<div id="4"></div>

设置下拉刷新样式

setRefreshHeader({params} ,callback(ret,err))

##params

loadingImg：

- 类型：字符串
- 默认值：无
- 描述：下拉刷新的小箭头本地图片的路径

bgColor:

- 类型：字符串
- 默认值：#f5f5f5
- 描述：（可选项）下拉刷新视图的背景色

textColor：

- 类型：字符串
- 默认值：#8e8e8e
- 描述：（可选项）提示文字颜色

textDown：

- 类型：字符串
- 默认值：下拉可以刷新…
- 描述：（可选项）提示文字

textUp：

- 类型：字符串
- 默认值：松开开始刷新…
- 描述：（可选项）提示文字

showTime：

- 类型：布尔值
- 默认值：true
- 描述：（可选项）是否显示刷新时间

##callback

返回触发刷新事件

##示例代码

```js
var loadingImgae = 'widget://res/listContact_arrow.png';		//刷新的小箭头，不可为空
var bgColor = '#F5F5F5';									//下拉刷新的背景颜色，有默认值，可为空
var textColor= '#8E8E8E';									//提示语颜色，有默认值，可为空
var textDown= '下拉可以刷新...';								//尚未触发刷新时间的提示语，有默认值，可为空
var textUp= '松开开始刷新...';								//触发刷新事件的提示语，有默认值，可为空
var showTime= true;											//是否显示时间，有默认值，可为空

var obj = api.require('listContact');
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

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**hide**<div id="5"></div>

隐藏listContact列表视图

hide()

##示例代码

	var obj = api.require('listContact');
	obj.hide();

##补充说明

隐藏列表视图，并没有从内存里清除

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

#**show**<div id="6"></div>

显示列表视图

show()

##示例代码

	var obj = api.require('listContact');
	obj.show();

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

#**deleteItem**<div id="7"></div>

删除指定索引的数据

deleteItem({params})

##params

index：

- 类型：数字
- 默认值：列表最后一条数据的索引
- 描述：（可选项）要删除的数据的索引

key：

- 类型：字符串
- 默认值：无
- 描述：要删除的数据所在的区域的key

##示例代码

```js
var obj = api.require('listContact');
 obj.deleteItem({
      index:2,
      key:A
 });
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.2及更高版本
 
#**refreshItem**<div id="8"></div>

刷新指定index条目的数据

refreshItem({params})

##params

index：

- 类型：数字
- 默认值：0
- 描述：（可选项）要刷新数据的item索引下标

key：

- 类型：字符串
- 默认值：无
- 描述：要刷新的数据所在的区域的key


data：

- 类型：json对象
- 默认值：无
- 描述：要刷新的item的数据源

内部字段：

```js
{
    img:                  //（可选项）cell的头像图片路径，支持http、https、widget、fs等网络和本地图片路径协议，网络图片会被缓存到本地
    placeholderImg:       //（可选项）头像,本地路径,加载网络图片时显示界面上的图
    title:                //（可选项）cell的标题，若subtitle为空时，title上下居中位置
    subTitle:             //（可选项）cell的子标题，可为空，为空时title上下居中显示
    titleLocation         //（可选项）标题在水平线上的位置center,left,right，默认left
    titleSize             //（可选项）标题字体的大小，默认12
    titleColor            //（可选项）标题字体的颜色值，默认黑色，支持rgb，rgba，#
    subTitleLocation      //（可选项）子标题在水平线上的位置center,left,right默认left
    subTitleSize          //（可选项）子标题字体的大小，默认12
    subTitleColor         //（可选项）子标题字体的颜色值,默认黑色, 支持rgb，rgba，#
}
```
##示例代码

```js
var obj = api.require('listContact');
obj.refreshItem({
      index:2,
      data: {title:'刷新指定下标的标题', subTitle:'刷新指定下标的子标题'}
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本
 
#**insertItemItem**<div id="9"></div>

插入指定索引的数据

insertItemItem({params})

##params

index：

- 类型：数字
- 默认值：列表最后一条数据的索引
- 描述：（可选项）要插入的item索引下标

key：

- 类型：字符串
- 默认值：无
- 描述：要插入的数据所在的区域的key


data：

- 类型：json对象
- 默认值：无
- 描述：要插入的item的数据源

内部字段：

```js
{
    img:                  //（可选项）cell的头像图片路径，支持http、https、widget、fs等网络和本地图片路径协议，网络图片会被缓存到本地
    placeholderImg:       //（可选项）头像,本地路径,加载网络图片时显示界面上的图
    title:                //（可选项）cell的标题，若subtitle为空时，title上下居中位置
    subTitle:             //（可选项）cell的子标题，可为空，为空时title上下居中显示
    titleLocation         //（可选项）标题在水平线上的位置center,left,right，默认left
    titleSize             //（可选项）标题字体的大小，默认12
    titleColor            //（可选项）标题字体的颜色值，默认黑色，支持rgb，rgba，#
    subTitleLocation      //（可选项）子标题在水平线上的位置center,left,right默认left
    subTitleSize          //（可选项）子标题字体的大小，默认12
    subTitleColor         //（可选项）子标题字体的颜色值,默认黑色, 支持rgb，rgba，#
}
```
##示例代码

```js
var obj = api.require('listContact');
 obj.insertItem({
    index:2,
data:{
   img:' http://d.hiphotos.baidu.com/image/pic/item/4d086e061d950a7b29a788c209d162d9f2d3c922.jpg ',
    title:'12:00',
    subTitle:'APICloud粉丝互动会',
        remark:'完成'
      }
 });
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.2及更高版本