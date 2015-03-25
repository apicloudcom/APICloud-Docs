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

bgColor：

- 类型：字符串
- 默认值：#FFFFFF
- 描述：列表的背景色，支持rgb，rgba，#，可为空

groupTitle:

- 类型：json对象
- 默认值：无
- 描述：配置组标题的字体颜色和大小，可为空，为空时显示字段里默认值

内部字段：

```js
{
    color:          //字符串类型，默认#949494,支持rgb，rgba，#，可为空
    size:           //数字类型，默认13，可为空
	bgColor:        //标题背景色，默认#DBDBDB,支持rgb，rgba，#，可为空
}
```

leftBtn：

- 类型：数组对象
- 默认值：无
- 描述：往右滑动cell露出的按钮组成的数字，可为空，为空时则表示cell不可向右滑动

内部字段：

```js
[{
    color:         	//按钮背景色，支持rgb，rgba，#，不可为空
    title:          //按钮名字，不可为空
	selectColor		//按钮选中时候的颜色值，支持rgb，rgba，#，不可为空
}]
```

leftBg：

- 类型：字符串
- 默认值：#5cacee
- 描述：往右滑动cell露出的视图的背景色，支持rgb，rgba，#，可为空

rightBtn：

- 类型：数组对象
- 默认值：无
- 描述：往左滑动cell露出的按钮组成的数字，可为空，为空时则表示cell不可向左滑动

内部字段：

```js
[{
    color:        		//按钮背景色，支持rgb，rgba，#，不可为空
    title:           	//按钮名字，支持rgb，rgba，#，不可为空
	selectColor			//按钮选中时候的颜色值，支持rgb，rgba，#，不可为空
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
- 描述：每个cell的高度，可为空

imgHeight：

- 类型：数字
- 默认值：自适应cell的高度
- 描述：头像的高，可为空

imgWidth：

- 类型：数字
- 默认值：自适应cell的高度
- 描述：头像的宽，可为空

data：

- 类型：json对象
- 默认值：无
- 描述：数据库名称，不能为空

内部字段：

```js
{
	common: [{                  //索引值
		img:               		//cell的头像，一个网络路径，此图片会被缓存到本地，可为空
		placeholderImg:         //头像,本地路径,加载网络图片时显示界面上的图，不可为空
		title:               	//cell的标题，若subtitle为空时，title上下居中位置，不可为空
		subTitle:           	//cell的子标题，可为空，为空时title上下居中显示
		titleLocation 			//标题在水平线上的位置center,left,right
		titleSize				//标题字体的大小默认12，可维空
		titleColor				//标题字体的颜色值，默认黑色，支持rgb，rgba，#，可为空
		subTitleLocation 		//子标题在水平线上的位置center,left,right默认left，可为空
		subTitleSize			//子标题字体的大小默认12，可为空
		subTitleColor			//子标题字体的颜色值,默认黑色,支持rgb，rgba，#，可为空
}],
A:[{}],
B:[{}],,,,,,
}
```

indicator:

- 类型：json对象
- 默认值：无
- 描述：是否添加右边索引导航条，可为空，若为空则不添加

内部字段：

```js
{
	bgColor:       	//背景色，字符串，默认透明，支持rgb，rgba，#，可为空
	color：			//索引指器颜色,字符串类型，默认#A1A1A1,支持rgb，rgba，#，可为空
}
```

fixedOn:

- 类型：字符串
- 默认值：无
- 描述：将模块视图添加在某个窗口上的名字，若为空则默认当前视图

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
    index:          	//点击某个cell所在区域内的cell的下标
	section:            //被点击的cell所在的区域的下标
	clickType:        	//点击类型，0-cell；1-右边按钮；2-左边的按钮
	btnIndex:       	   //点击按钮时返回其下标
}
```

##示例代码

```js
var obj = api.require('listContact');
obj.open({
	h:300,
	rightBtn:[{color:'#8B0000',title:'备注'}],
	data:{
		common:[{
			placeholderImg:'widget://res/listview.png',
			img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
			title:'标题'
			}],
			A:[{
				placeholderImg:'widget://res/listview.png',
				img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
				title:'标题'
			},{
				placeholderImg: 'widget://res/listview.png',title:'标题'
			},{
				placeholderImg: 'widget://res/listview.png',title:'标题' 
			},{
				placeholderImg:'widget://res/listview.png',title:'标题'
			},{
				placeholderImg:'widget://res/listview.png',title:'标题'
			},{
				placeholderImg: 'widget://res/listview.png',title:'标题'
			},{
				placeholderImg: 'widget://res/listview.png',title:'标题' 
			},{
				placeholderImg: 'widget://res/listview.png',title:'标题'
			},{
				placeholderImg: 'widget://res/listview.png',title:'标题'
			},{
				placeholderImg:'widget://res/listview.png' ,title:'标题'
			}]}
},function(ret,err){
					api.alert({msg:ret.section+"*"+ret.index});
});
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
- 描述：刷新的数据源，不能为空

内部字段：

```js
{
	comman: [{                  //索引值
		img:               		//cell的头像，一个网络路径，此图片会被缓存到本地，可为空
		placeholderImg:      	//头像,一个本地路径,加载网络图片时显示界面上的图，不可为空
		title:               	//cell的标题，若subtitle为空时，title上下居中位置，不可为空
		subTitle:            	//cell的子标题，可为空，为空时title上下居中显示
		titleLocation			//标题在水平线上的位置center,left,right
		titleSize				//标题字体的大小默认12，可维空
		titleColor				//标题字体的颜色值，默认黑色，支持rgb，rgba，#，可为空
		subTitleLocation 		//子标题在水平线上的位置center,left,right默认left，可为空
		subTitleSize			//子标题字体的大小默认12，可为空
		subTitleColor			//子标题字体的颜色值,默认黑色,支持rgb，rgba，#，可为空
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
			placeholderImg:'widget://res/listview.png',
			img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
       		title:'标题'
      	}],
		A:[{
			placeholderImg:'widget://res/listview.png',
			img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
       		title:'标题'
     	},{
			placeholderImg: 'widget://res/listview.png',title:'标题'
     	},{
			placeholderImg: 'widget://res/listview.png',title:'标题' 
     	},{
			placeholderImg:'widget://res/listview.png',title:'标题'
     	},{
			placeholderImg:'widget://res/listview.png',title:'标题'
     	},{
			placeholderImg: 'widget://res/listview.png',title:'标题'
     	},{
			placeholderImg: 'widget://res/listview.png',title:'标题' 
     	},{
			placeholderImg: 'widget://res/listview.png',title:'标题'
     	},{
			placeholderImg: 'widget://res/listview.png',title:'标题'
     	},{
			placeholderImg:'widget://res/listview.png' ,title:'标题'
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
- 描述：下拉刷新的小箭头本地图片的路径，不能为空

bgColor:

- 类型：字符串
- 默认值：#f5f5f5
- 描述：下拉刷新视图的背景色，可为空

textColor：

- 类型：字符串
- 默认值：#8e8e8e
- 描述：提示文字颜色

textDown：

- 类型：字符串
- 默认值：下拉可以刷新…
- 描述：提示文字

textUp：

- 类型：字符串
- 默认值：松开开始刷新…
- 描述：提示文字

showTime：

- 类型：布尔值
- 默认值：true
- 描述：是否显示刷新时间

##callback

返回触发刷新事件

##示例代码

```js
var loadingImgae = 'widget://res/listView_arrow.png';		//刷新的小箭头，不可为空
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

隐藏listView列表视图

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