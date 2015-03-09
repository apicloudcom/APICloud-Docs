/*
Title: listView
Description: listView
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[close](#2)

[reloadData](#3)
 
[deleteItem](#30)
 
[refreshItem](#31)
 
[appendData](#4)
 
[setRefreshHeader](#5)
 
[setRefreshFooter](#6)

[hide](#7)
 
[show](#8)
</div>

#**概述**

listView封装了一个列表控件，可实现一个可左右拖动item的列表视图。开发者可根据需求自定义列表的数据源，亦可自定义相关字段的样式。支持设置下拉刷新和上拉加载更多事件

![图片说明](/img/docImage/listView.jpg)

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
- 默认值：紧贴导航条位置
- 描述：列表视图的左上角点的坐标，可为空

w：

- 类型：数字
- 默认值：当前屏幕宽度
- 描述：列表视图的宽，可为空

h：

- 类型：数字
- 默认值：全屏
- 描述：列表视图的高，可为空

leftBtn：

- 类型：数组对象
- 默认值：无
- 描述：往右滑动cell露出的按钮组成的数组，可为空，为空时则表示cell不可向右滑动

内部字段：

```js
[{
	color:                  //按钮背景色，支持rgb，rgba，#，可为空
	title:                  //按钮名字，可为空
	selecteColor            //按钮选中时候的颜色值，支持rgb，rgba，#，可为空 deprecated   selectedColor    	//按钮选中时候的颜色值，支持rgb，rgba，#，不可为空
}]
```

leftBg：

- 类型：字符串
- 默认值：#5cacee
- 描述：往右滑动cell露出的视图的背景色

rightBtn：

- 类型：数组对象
- 默认值：无
- 描述：往左滑动cell露出的按钮组成的数字，可为空，为空时则表示cell不可向左滑动

内部字段：

```js
[{
	color:                  //按钮背景色，支持rgb，rgba，#，可为空
	title:                  //按钮名字，可为空
	selecteColor            //按钮选中时候的颜色值，支持rgb，rgba，#，可为空deprecated   selectedColor    	//按钮选中时候的颜色值，支持rgb，rgba，#，不可为空
}]
```

rightBg：

- 类型：字符串
- 默认值：#6c7b8b
- 描述：往左滑动cell露出的视图的背景色，支持rgb，rgba，#，可为空

borderColor：

- 类型：字符串
- 默认值：#696969
- 描述：每个cell之间分割线的颜色，支持rgb，rgba，#，可为空

cellBgColor：

- 类型：字符串
- 默认值:#AFEEEE
- 描述：cell的背景色，支持rgb，rgba，#，可为空

cellSelectColor：

- 类型：字符串
- 默认值：#F5F5F5
- 描述：选中cell时的颜色，支持rgb，rgba，#，可为空

cellHeight：

- 类型：数字
- 默认值：55
- 描述：每个cell的高度

imgHeight：

- 类型：数字
- 默认值：自适应cell的高度
- 描述：头像的高

imgWidth：

- 类型：数字
- 默认值：自适应cell的高度
- 描述：头像的宽

placeholderImg：

- 类型：字符串
- 默认值：无
- 描述：头像占位图，本地图的地址，支持widget，fs等本地协议，可为空，为空不显示头像

data：

- 类型：数组对象
- 默认值：无
- 描述：数据库名称，不能为空

内部字段：

```js
[{
	img:                    //cell的头像，一个网络路径，此图片会被缓存到本地，可为空
	title:                  //cell的标题，若subtitle为空时，title上下居中位置
	subTitle:               //cell的子标题，可为空，为空时title上下居中显示
	titleLocation           //标题在水平线上的位置center,left,right
	titleSize               //标题字体的大小默认12，可维空
	titleColor              //标题字体的颜色值，默认黑色,rgb,rgba,#，可为空
	subTitleLocation        //子标题在水平线上的位置center,left,right默认left，可为空
	subTitleSize            //子标题字体的大小默认12，可为空
	subTitleColor           //子标题字体的颜色值,默认黑色,rgb,rgba,#，可为可空
}]
```

fixedOn：

- 类型：字符串
- 默认值：当前主窗口的名字
- 描述：将此模块视图添加到指定窗口的名字，可为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	index:                  //点击某个cell或其内部按钮返回其下标
	clickType:              //点击类型，0-cell；1-右边按钮；2-左边的按钮
	btnIndex:               //点击按钮时返回其下标
}
```

##示例代码

```js
var obj = api.require('listView');obj.open({    h:300,    leftBtn:[{color:'#8B0000',title:'左按钮1'},{color:'#228B22',title:'左按钮2'}],    rightBtn:[{color:'#8B0000',title:'右按钮1'},{color:'#228B22',title:'右按钮2'}],    placeholderImg: 'widget://res/listview.png',              data:[{ img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',title:'标题',subTitle:'子标题，说明文字。。。。。。'},{ title:'标题',subTitle:'子标题'},{title:'标题',subTitle:'子标题'},{ title:'标题',subTitle:'子标题'},{ title:'标题',subTitle:'子标题'},{ title:'标题',subTitle:'子标题'},{ title:'标题',subTitle:'子标题'},{ title:'标题',subTitle:'子标题 '},{title:'标题',subTitle:'子标题'},{ title:'标题',subTitle:'子标题 '},{ title:'标题',subTitle:'子标题'}]},function(ret,err){    api.alert({msg:ret.index});});
```

##补充说明

打开列表视图

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**close**<div id="2"></div>

关闭listView

close()

##示例代码

    var obj = api.require('listView');
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

- 类型：数组对象
- 默认值：无
- 描述：数据库名称，不能为空

内部字段：

```js
[{
	img:                 //cell的头像，一个网络路径，此图片会被缓存到本地，可为空
	title:               //cell的标题，不可为空
	subTitle:            //cell的子标题，可为空，为空时标题居中显示
}]
```

##示例代码

```js
var obj = api.require('listView');
obj.reloadData({
	data:[{title:'标题',subTitle:'子标题，说明文字'},
		{title:'标题',subTitle:'子标题'},
		{title:'标题',subTitle:'子标题，说明文字'},
		{title:'标题',subTitle:'子标题，说明文字。'},
		{title:'标题',subTitle:'子标题'},
		{title:'标题',subTitle:'子标题，说明文字'},
		{title:'标题',subTitle:'子标题，说明文字'},
		{title:'标题',subTitle:'子标题'},
		{title:'标题',subTitle:'子标题，说明文字'},
		{title:'标题',subTitle:'子标题，说明文字'},
		{title:'标题',subTitle:'子标题，说明文字'}]
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
 
 
#**deleteItem**<div id="30"></div>

删除指定索引的数据

deleteItem({params})

##params

index：

- 类型：数字
- 默认值：无
- 描述：要删除的数据的索引下标，可为空，为空则删除最后一条数据


##示例代码

```js
var obj = api.require('listView'); obj.deleteItem({      index:2 });
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本
 
#**refreshItem**<div id="31"></div>

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
- 描述：数据源，可为空，为空则不刷新

内部字段：

```js
{
	img:                 //cell的头像，一个网络路径，此图片会被缓存到本地，可为空
	title:               //cell的标题，不可为空
	subTitle:            //cell的子标题，可为空，为空时标题居中显示
}
```
##示例代码

```js
var obj = api.require('listView'); obj.refreshItem({      index:2，      data：{ title:'刷新指定下标的标题',subTitle:'刷新指定下标的子标题'} });
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本
 
 
#**appendData**<div id="4"></div>
 
添加列表数据
 
appendData({params})
 
##params
 
data：
 
- 类型：数组对象
- 默认值：无
- 描述：数据库名称，不能为空
 
内部字段：
 
```js
[{
	img:                 //cell的头像，一个网络路径，此图片会被缓存到本地，可为空
	title:               //cell的标题，不可为空
	subtitle:            //cell的子标题，可为空，为空时标题居中显示
}]
```
 
##示例代码
 
```js
var obj = api.require('listView');
obj.appendData({
 	data:[{title:'标题',subTitle:'子标题，说明文字'},
 		{title:'标题',subTitle:'子标题'},
 		{title:'标题',subTitle:'子标题，说明文字'},
 		{title:'标题',subTitle:'子标题，说明文字。'},
 		{title:'标题',subTitle:'子标题'},
 		{title:'标题',subTitle:'子标题，说明文字'},
 		{title:'标题',subTitle:'子标题，说明文字'},
 		{title:'标题',subTitle:'子标题'},
 		{title:'标题',subTitle:'子标题，说明文字'},
 		{title:'标题',subTitle:'子标题，说明文字'},
 		{title:'标题',subTitle:'子标题，说明文字'}]
});
```
 
##补充说明
 
无
 
##可用性
 
iOS系统，Android系统
 
可提供的1.0.0及更高版本
 
#**setRefreshHeader**<div id="5"></div>
 
设置下拉刷新
 
setRefreshHeader({params}, callback(ret, err))
 
##params
 
loadingImg：
 
- 类型：字符串
- 默认值：无
- 描述：下拉刷新时显示的小箭头的本地图片路径，不可为空
 
bgColor：
 
- 类型：字符串
- 默认值：#f5f5f5
- 描述：下拉刷新视图的背景色，支持rgb，rgba，#，可为空
 
textColor：
 
- 类型：字符串
- 默认值：#8e8e8e
- 描述：提示文字颜色，支持rgb，rgba，#，可为空
 
textDown：
 
- 类型：字符串
- 默认值：下拉可以刷新...
- 描述：提示文字，可为空
 
textUp：
 
- 类型：字符串
- 默认值：松开开始刷新...
- 描述：提示文字，可为空
 
 
showTime：
 
- 类型：布尔值
- 默认值：true
- 描述：是否显示刷新时间
 
 
##callback(ret, err)
 
返回触发刷新的事件
 
##示例代码
 
```js
var loadingImgae = 'widget://res/listView_arrow.png';     //刷新的小箭头，不可为空
var bgColor = '#F5F5F5';                                  //下拉刷新的背景颜色 ，有默认值，可为空
var textColor= '#8E8E8E';                                 //提示语颜色，有默认值，可为空
var textDown= '下拉可以刷新...';                             //尚未触发刷新时间的提示语，有默认值，可为空
var textUp= '松开开始刷新...';                               //触发刷新事件的提示语，有默认值，可为空
var showTime= true;                                       //是否显示时间，有默认值，可为空
 
var obj = api.require('listView');
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
 
#**setRefreshFooter**<div id="6"></div>
 
设置上拉加载更多
 
setRefreshFooter({params}, callback(ret, err))
 
##params
 
loadingImg：
 
- 类型：字符串
- 默认值：无
- 描述：上拉加载更多时显示的小箭头的本地图片路径，不可为空
 
bgColor：
 
- 类型：字符串
- 默认值：#f5f5f5
- 描述：上拉加载更多视图的背景色，支持rgb，rgba，#，可为空
 
textColor：
 
- 类型：字符串
- 默认值：#8e8e8e
- 描述：提示文字颜色，支持rgb，rgba，#，可为空
 
textDown：
 
- 类型：字符串
- 默认值：上拉可以加载更多...
- 描述：提示文字，可为空
 
textUp：
 
- 类型：字符串
- 默认值：松开开始加载...
- 描述：提示文字，可为空
 
 
showTime：
 
- 类型：布尔值
- 默认值：true
- 描述：是否显示刷新时间
 
 
##callback(ret, err)
 
返回触发加载更多的事件
 
##示例代码
 
```js
var loadingImgae = 'widget://res/listView_arrow.png';       //刷新的小箭头，不可为空
var bgColor = '#F5F5F5';                                    //下拉刷新的背景颜色 ，有默认值，可为空
var textColor= '#8E8E8E';                                   //提示语颜色，有默认值，可为空
var textDown= '下拉可加载更多...';                             //尚未触发刷新时间的提示语，有默认值，可为空
var textUp= '松开开始加载...';                                 //触发刷新事件的提示语，有默认值，可为空
var showTime= true;                                         //是否显示时间，有默认值，可为空        
var obj = api.require('listView');
obj.setRefreshFooter({
    loadingImg:loadingImgae,
    bgColor:bgColor,
    textColor:textColor,
    textDown:textDown,
    textUp:textUp,
    showTime:showTime
},function(ret,err){
    //触发加载事件
});
 
```
 
##补充说明
 
加载更多的设置
 
##可用性
 
iOS系统，Android系统
 
可提供的1.0.0及更高版本

#**hide**<div id="7"></div>
 
隐藏listView
 
hide()
 
##示例代码
 
```js    
var obj = api.require('listView');
obj.hide();
 
```
 
##补充说明
 
隐藏listView，并没有从内存里清除
 
##可用性
 
iOS系统，Android系统
 
可提供的1.0.1及更高版本


#**show**<div id="8"></div>
 
显示listView
 
show()
 
##示例代码
 
```js    
var obj = api.require('listView');
obj.show();
 
```
 
##补充说明
 
显示已隐藏的列表视图
 
##可用性
 
iOS系统，Android系统
 
可提供的1.0.1及更高版本