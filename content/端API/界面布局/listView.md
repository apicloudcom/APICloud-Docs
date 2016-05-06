/*
Title: listView
Description: listView
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[setFrame](#b0)

[getIndex](#b1)

[setRightButtons](#b3)

[close](#2)

[reloadData](#3)
 
[deleteItem](#30)
 
[refreshItem](#31)

[insertItem](#32)
 
[appendData](#4)
 
[setRefreshHeader](#5)
 
[setRefreshFooter](#6)

[hide](#7)
 
[show](#8)
</div>

#**概述**

listView 封装了一个列表控件，可实现一个可左右拖动item的列表视图。开发者可根据需求自定义列表的数据源，亦可自定义相关字段的样式。支持设置下拉刷新和上拉加载更多事件。**UIListView 模块是 listView 模块的优化版，建议使用 [UIListView](http://docs.apicloud.com/端API/界面布局/UIListView) 模块，此模块已停止更新。**

![图片说明](/img/docImage/listView.jpg)

#**open**<div id="1"></div>

打开

open({params}, callback(ret, err))

##params

x：

- 类型：数字
- 默认值：0
- 描述：（可选项）列表视图的左上角点的X坐标

y：

- 类型：数字
- 默认值：0
- 描述：（可选项）列表视图的左上角点的Y坐标

w：

- 类型：数字
- 默认值：父窗口视图的宽
- 描述：（可选项）列表视图的宽

h：

- 类型：数字
- 默认值：父窗口视图的高
- 描述：（可选项）列表视图的高

leftBtn：

- 类型：数组对象
- 默认值：无
- 描述：（可选项）往右滑动item露出的按钮组成的数组
- 备注：不传此参数则表示item不可向右滑动
- 内部字段：

```js
[{
	color:                  //按钮背景色，支持 rgb，rgba，#
	title:                  //（可选项）按钮名字，不传则不显示
    selectedColor    	    //按钮选中时候的颜色值，支持 rgb，rgba，#
}]
```

leftBg：

- 类型：字符串
- 默认值：#5cacee
- 描述：（可选项）往右滑动item露出的视图的背景色

rightBtn：

- 类型：数组对象
- 默认值：无
- 描述：（可选项）往左滑动item露出的按钮组成的数字
- 备注：不传则表示item不可向左滑动
- 内部字段：

```js
  [{
      bg:         	  //（可选项）按钮背景色，支持 rgb，rgba，#，默认#388e8e
      title:          //（可选项）按钮标题，字符串类型，默认空字符串
      titleSize:      //（可选项）按钮标题字体大小，数字类型，默认12
      titleColor:      //（可选项）按钮标题颜色，支持 rgb，rgba，#，默认#ffffff，可为空
      highlightColor  //（可选项）按钮选中时的颜色值,支持 rgb，rgba，#，默认无
      icon            //（可选项）按钮标题前图标图片路径，图标大小20*20，默认无，可不传，支持本地协议路径，如widget：//、fs://等
   }]
```

rightBg：

- 类型：字符串
- 默认值：#6c7b8b
- 描述：（可选项）往左滑动item露出的视图的背景色，支持 rgb，rgba，#

borderColor：

- 类型：字符串
- 默认值：#696969
- 描述：（可选项）每个item之间分割线的颜色，支持 rgb，rgba，#

cellBgColor：

- 类型：字符串
- 默认值:#AFEEEE
- 描述：（可选项）item的背景色，支持 rgb，rgba，#

cellSelectColor：

- 类型：字符串
- 默认值：#F5F5F5
- 描述：（可选项）选中item时的颜色，支持 rgb，rgba，#

cellHeight：

- 类型：数字
- 默认值：55
- 描述：（可选项）每个item的高度

imgHeight：

- 类型：数字
- 默认值：(itemHeight-10)
- 描述：（可选项）头像的高

imgWidth：

- 类型：数字
- 默认值：imgHeight
- 描述：（可选项）头像的宽

placeholderImg：

- 类型：字符串
- 默认值：无
- 描述：（可选项）头像占位图，本地图的地址，支持widget，fs等本地协议
- 备注：不传则不显示头像，标题和子标题顶头显示

fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window

data：

- 类型：数组对象
- 默认值：无
- 描述：列表的数据源
- 内部字段：

```js
[{
    placeholderImg:        //（可选项）头像,一个本地路径,加载网络图片时显示界面上的图
	img:                    //（可选项）item的头像，支持http,https,widget,fs等本地和网络路径协议，网络图片会被缓存到本地
	title:                  //（可选项）item的标题，若subtitle不传或为空字符串则title上下位置居中显示
	subTitle:               //（可选项）item的子标题，若不传或为空字符串则title上下位置居中显示
	titleLocation           //（可选项）标题在水平线上的位置，取值范围：center,left,right，默认left
	titleSize               //（可选项）标题字体的大小，默认12
	titleColor              //（可选项）标题字体的颜色值，默认#000000，支持 rgb,rgba,#
	subTitleLocation        //（可选项）子标题在水平线上的位置，取值范围：center,left,right默认left
	subTitleSize            //（可选项）子标题字体的大小，默认12
	subTitleColor           //（可选项）子标题字体的颜色值,默认黑色,rgb,rgba,#
    remark                  //（可选项）item右边备注，字符串类型，不传或空字符串则不显示
    arrow                   //（可选项）item右边箭头图标路径，支持widget，fs等本地协议，不传或空字符串则不显示
    rightBtn:   //(可选项)数组对象,往左滑动item露出的按钮信息组成的数组，无默认值，若为空则以open接口内data参数外的rightBtn参数为准，若open接口内data参数外的rightBtn参数和本参数都不传，则不可向左滑动
	            内部字段：
	            [{
		           bg:         	  //（可选项）按钮背景色，支持 rgb，rgba，#，默认#388e8e
		           title:        //（可选项）按钮标题，字符串类型，默认空字符串
		           titleSize:    //（可选项）按钮标题字体大小，数字类型，默认12
		           titleColor:    //（可选项）按钮标题颜色，支持 rgb，rgba，#，默认#ffffff，可为空
		           highlightColor//（可选项）按钮选中时的颜色值,支持 rgb，rgba，#，默认无
		           icon          //（可选项）按钮标题前图标图片路径，图标大小20*20，默认无，可不传，支持本地协议路径，如widget：//、fs://等
	             }]
	rightSlipDistance:		//（可选项）向左滑动露出右边按钮时，item的滑动距离占item宽的百分比，默认50，取值范围30-100
	leftSlipDistance:		//（可选项）向右滑动露出左边按钮时，item的滑动距离占item宽的百分比，默认50，取值范围30-100
}]
```

rightSlipDistance：

- 类型：数字
- 默认值：50
- 描述：（可选项）向左滑动露出右边按钮时，item的滑动距离咱item宽的百分比，取值范围30-100

leftSlipDistance：

- 类型：数字
- 默认值：50
- 描述：（可选项）向右滑动露出左边按钮时，item的滑动距离咱item宽的百分比，取值范围30-100

markStyle：

- 类型：JSON 对象
- 默认值：见内部字段
- 描述：（可选项）item右边的arrow，remark样式配置
- 内部字段：

```js
{
     remarkMargin:   //（可选项）备注距离右边的边距，数字类型，默认10
     remarkColor:    //（可选项）备注距字体颜色，支持 rgb，rgba，#，默认#000000
     remarkSize:     //（可选项）备注字体大小，数字类型，默认16
     arrowSize:      //（可选项）右边图标大小，数字类型，默认30
}
```

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
    eventType:      	//事件类型，取值范围如下：
	                       rightBtn:       //点击右边按钮
	                       leftBtn:        //点击右边按钮
	                       content:        //点击的item内容
	                       avatar:         //点击的item的头像
	                       arrow:          //点击item右边箭头图标事件
	                       open:           //打开列表视图渲染加载成功
	index:              //点击某个item或其内部按钮返回其索引
	clickType:          //（deprecated）点击类型，取值范围：0-item；1-右边按钮；2-左边的按钮
	btnIndex:           //点击按钮时返回其索引
}
```

##示例代码

```js
var listView = api.require('listView');
listView.open({
    h:300,
    leftBtn:[{color:'#8B0000',title:'左按钮1'},{color:'#228B22',title:'左按钮2'}],
    rightBtn:[{color:'#8B0000',title:'右按钮1'},{color:'#228B22',title:'右按钮2'}],
    placeholderImg: 'widget://res/listview.png',
    data:[{ img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',title:'标题',subTitle:'子标题，说明文字。。。。。。'},{ title:'标题',subTitle:'子标题'},{title:'标题',subTitle:'子标题'},{ title:'标题',subTitle:'子标题'},{ title:'标题',subTitle:'子标题'},{ title:'标题',subTitle:'子标题'},{ title:'标题',subTitle:'子标题'},{ title:'标题',subTitle:'子标题 '},{title:'标题',subTitle:'子标题'},{ title:'标题',subTitle:'子标题 '},{ title:'标题',subTitle:'子标题'}]
}, function(ret, err){		
    if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##补充说明

打开列表视图

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setFrame**<div id="b0"></div>

重设模块视图的y，和h

setFrame({params})

##params

anim：

- 类型：布尔
- 默认值：false
- 描述：改变模块视图的frame时是否添加动画效果,可为空

y：

- 类型：数字类型
- 默认值：无
- 描述：（可选项）重设模块视图的y值
- 备注：若不传则保持原值不变

h：

- 类型：数字类型
- 默认值：无
- 描述：（可选项）重设模块视图的h值
- 备注：若不传则保持原值不变

##示例代码

```js
var listView = api.require('listView');
listView.setFrame({
	anim:true ,
	y:0
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**getIndex**<div id="b1"></div>

根据唯一标识查找该item在列表中的下标

getIndex({params}, callBack(ret, err))

##params

key：

- 类型：字符串
- 默认值：无
- 描述：唯一标识的key

value：

- 类型：字符串
- 默认值：无
- 描述：每条item数据的唯一标识

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

	{
	    index:          	//获取的item的索引
	    data：              //当前操作的item的数据，内部字段与open里datas元素一致
	}

##示例代码

```js
var listView = api.require('listView');
listView.getIndex({
	key: 'uid',
	value: '00000001'
}, function(ret, err){		
    if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setRightButtons**<div id="b3"></div>

设置侧滑item显示出来按钮

setRightButtons({params})

##params

index：

- 类型：数字
- 默认值：0
- 描述：要设置侧滑按钮的item的索引,可为空

rightBtn：

- 类型：数组对象
- 默认值：无
- 描述：(可选项)数组对象,往左滑动item露出的按钮信息组成的数组，
- 备注：若为不传则以open接口内data参数外的rightBtn参数为准，若open接口内data参数外的rightBtn参数和本参数都不传，则不可向左滑动
- 内部字段：

```js
   [{
        bg:         	  //（可选项）按钮背景色，支持 rgb，rgba，#，默认#388e8e
        title:        //（可选项）按钮标题，字符串类型，默认空字符串
        titleSize:    //（可选项）按钮标题字体大小，数字类型，默认12
        titleColor:    //（可选项）按钮标题颜色，支持 rgb，rgba，#，默认#ffffff，可为空
        highlightColor//（可选项）按钮选中时的颜色值,支持 rgb，rgba，#，默认无
        icon          //（可选项）按钮标题前图标图片路径，图标大小20*20，默认无，可不传，支持本地协议路径，如widget：//、fs://等
   }]
```

##示例代码

```js
var listView = api.require('messageList');
listView.setRightButtons({
     index:0,
     rightBtn: [{
            bg:  '#556B2F',  			//按钮背景色，支持 rgb，rgba，#，默认#ee8262.
            title: '取消', 				//按钮名字，字符串类型，默认‘按钮’
            titleSize: 13,      		//按钮标题大小，默认12
            titleColor: '#000000',  	// 按钮标题颜色，支持 rgb，rgba，#，默认#ffffff
            selectedColor: '#FFFFFF',   //按钮选中时候的颜色值,支持 rgb，rgba，#
            icon:'widget://image/messageList/delete.png'
        }, {
            bg:  '#4EEE94',  			//按钮背景色，支持 rgb，rgba，#，默认#ee8262.
            title: '取消置顶', 			//按钮名字，字符串类型，默认‘按钮’
            titleSize: 13,      		//按钮标题大小，默认12
            titleColor: '#000000', 		// 按钮标题颜色，支持 rgb，rgba，#，默认#ffffff
            selectedColor: 'ffffff',  	//按钮选中时候的颜色值,支持 rgb，rgba，#
            icon:'widget://image/messageList/delete.png'
        }]
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**close**<div id="2"></div>

关闭listView

close()

##示例代码

```js
var listView = api.require('listView');
listView.close();
```

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
- 描述：（可选项）列表数据源，若不传则仅停止下拉刷新状态
- 内部字段：

```js
[{
    placeholderImg:        //（可选项）头像,一个本地路径,加载网络图片时显示界面上的图
	img:                    //（可选项）item的头像，支持http,https,widget,fs等本地和网络路径协议，网络图片会被缓存到本地
	title:                  //（可选项）item的标题，若subtitle不传或为空字符串则title上下位置居中显示
	subTitle:               //（可选项）item的子标题，若不传或为空字符串则title上下位置居中显示
	titleLocation           //（可选项）标题在水平线上的位置，取值范围：center,left,right，默认left
	titleSize               //（可选项）标题字体的大小，默认12
	titleColor              //（可选项）标题字体的颜色值，默认#000000，支持 rgb,rgba,#
	subTitleLocation        //（可选项）子标题在水平线上的位置，取值范围：center,left,right默认left
	subTitleSize            //（可选项）子标题字体的大小，默认12
	subTitleColor           //（可选项）子标题字体的颜色值,默认黑色,rgb,rgba,#
    remark                  //（可选项）item右边备注，字符串类型，不传或空字符串则不显示
    arrow                   //（可选项）item右边箭头图标路径，支持widget，fs等本地协议，不传或空字符串则不显示
    rightBtn:   //(可选项)数组对象,往左滑动item露出的按钮信息组成的数组，无默认值，若为空则以open接口内data参数外的rightBtn参数为准，若open接口内data参数外的rightBtn参数和本参数都不传，则不可向左滑动
                  内部字段：
                  [{
	                  bg:         	  //（可选项）按钮背景色，支持 rgb，rgba，#，默认#388e8e
	                  title:        //（可选项）按钮标题，字符串类型，默认空字符串
	                  titleSize:    //（可选项）按钮标题字体大小，数字类型，默认12
	                  titleColor:    //（可选项）按钮标题颜色，支持 rgb，rgba，#，默认#ffffff，可为空
	                  highlightColor//（可选项）按钮选中时的颜色值,支持 rgb，rgba，#，默认无
	                  icon          //（可选项）按钮标题前图标图片路径，图标大小20*20，默认无，可不传，支持本地协议路径，如widget：//、fs://等
                  }]
}]
```

##示例代码

```js
var listView = api.require('listView');
listView.reloadData({
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
- 默认值：列表最后一条数据的索引
- 描述：（可选项）要删除的数据的索引


##示例代码

```js
var listView = api.require('listView');
listView.deleteItem({
	index: 2
});
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
- 默认值：0
- 描述：（可选项）要刷新数据的item索引下标

data：

- 类型：JSON 对象
- 默认值：见内部字段
- 描述：（可选项）要刷新的item的数据源
- 内部字段：

```js
{
    placeholderImg:         //（可选项）头像,一个本地路径,加载网络图片时显示界面上的图
	img:                    //（可选项）item的头像，支持http,https,widget,fs等本地和网络路径协议，网络图片会被缓存到本地
	title:                  //（可选项）item的标题，若subtitle不传或为空字符串则title上下位置居中显示
	subTitle:               //（可选项）item的子标题，若不传或为空字符串则title上下位置居中显示
	titleLocation           //（可选项）标题在水平线上的位置，取值范围：center,left,right，默认left
	titleSize               //（可选项）标题字体的大小，默认12
	titleColor              //（可选项）标题字体的颜色值，默认#000000，支持 rgb,rgba,#
	subTitleLocation        //（可选项）子标题在水平线上的位置，取值范围：center,left,right默认left
	subTitleSize            //（可选项）子标题字体的大小，默认12
	subTitleColor           //（可选项）子标题字体的颜色值,默认黑色,rgb,rgba,#
    remark                  //（可选项）item右边备注，字符串类型，不传或空字符串则不显示
    arrow                   //（可选项）item右边箭头图标路径，支持widget，fs等本地协议，不传或空字符串则不显示
    rightBtn:   //(可选项)数组对象,往左滑动item露出的按钮信息组成的数组，无默认值，若为空则以open接口内data参数外的rightBtn参数为准，若open接口内data参数外的rightBtn参数和本参数都不传，则不可向左滑动
                  内部字段：
                  [{
	                  bg:         	  //（可选项）按钮背景色，支持 rgb，rgba，#，默认#388e8e
	                  title:        //（可选项）按钮标题，字符串类型，默认空字符串
	                  titleSize:    //（可选项）按钮标题字体大小，数字类型，默认12
	                  titleColor:    //（可选项）按钮标题颜色，支持 rgb，rgba，#，默认#ffffff，可为空
	                  highlightColor//（可选项）按钮选中时的颜色值,支持 rgb，rgba，#，默认无
	                  icon          //（可选项）按钮标题前图标图片路径，图标大小20*20，默认无，可不传，支持本地协议路径，如widget：//、fs://等
                  }]
}
```
##示例代码

```js
var listView = api.require('listView');
listView.refreshItem({
	index:2,
	data: {
		title:'刷新指定下标的标题', 
		subTitle:'刷新指定下标的子标题'
	}
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本
 
#**insertItemItem**<div id="32"></div>

插入指定索引的数据

insertItemItem({params})

##params

index：

- 类型：数字
- 默认值：列表最后一条数据的索引
- 描述：（可选项）要插入的item索引下标

data：

- 类型：JSON 对象
- 默认值：见内部字段
- 描述：数据源
- 内部字段：

```js
{
    placeholderImg:         //（可选项）头像,一个本地路径,加载网络图片时显示界面上的图
	img:                    //（可选项）item的头像，支持http,https,widget,fs等本地和网络路径协议，网络图片会被缓存到本地
	title:                  //（可选项）item的标题，若subtitle不传或为空字符串则title上下位置居中显示
	subTitle:               //（可选项）item的子标题，若不传或为空字符串则title上下位置居中显示
	titleLocation           //（可选项）标题在水平线上的位置，取值范围：center,left,right，默认left
	titleSize               //（可选项）标题字体的大小，默认12
	titleColor              //（可选项）标题字体的颜色值，默认#000000，支持 rgb,rgba,#
	subTitleLocation        //（可选项）子标题在水平线上的位置，取值范围：center,left,right默认left
	subTitleSize            //（可选项）子标题字体的大小，默认12
	subTitleColor           //（可选项）子标题字体的颜色值,默认黑色,rgb,rgba,#
    remark                  //（可选项）item右边备注，字符串类型，不传或空字符串则不显示
    arrow                   //（可选项）item右边箭头图标路径，支持widget，fs等本地协议，不传或空字符串则不显示
    rightBtn:   //(可选项)数组对象,往左滑动item露出的按钮信息组成的数组，无默认值，若为空则以open接口内data参数外的rightBtn参数为准，若open接口内data参数外的rightBtn参数和本参数都不传，则不可向左滑动
                  内部字段：
                  [{
	                  bg:         	  //（可选项）按钮背景色，支持 rgb，rgba，#，默认#388e8e
	                  title:        //（可选项）按钮标题，字符串类型，默认空字符串
	                  titleSize:    //（可选项）按钮标题字体大小，数字类型，默认12
	                  titleColor:    //（可选项）按钮标题颜色，支持 rgb，rgba，#，默认#ffffff，可为空
	                  highlightColor//（可选项）按钮选中时的颜色值,支持 rgb，rgba，#，默认无
	                  icon          //（可选项）按钮标题前图标图片路径，图标大小20*20，默认无，可不传，支持本地协议路径，如widget：//、fs://等
                  }]
}
```
##示例代码

```js
var listView = api.require('listView');
listView.insertItem({
	index: 2,
	data: {
		img: 'http://d.hiphotos.baidu.com/image/pic/item/4d086e061d950a7b29a788c209d162d9f2d3c922.jpg ',
		title: '12:00',
		subTitle: 'APICloud粉丝互动会',
		remark: '完成'
	}
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.2及更高版本
 
 
#**appendData**<div id="4"></div>
 
添加列表数据
 
appendData({params})
 
##params
 
data：
 
- 类型：数组对象
- 默认值：无
- 描述：（可选项）要拼接到列表的数据源，若不传则仅停止上拉加载更多状态
- 内部字段：
 
```js
[{
    placeholderImg:         //（可选项）头像,一个本地路径,加载网络图片时显示界面上的图
	img:                    //（可选项）item的头像，支持http,https,widget,fs等本地和网络路径协议，网络图片会被缓存到本地
	title:                  //（可选项）item的标题，若subtitle不传或为空字符串则title上下位置居中显示
	subTitle:               //（可选项）item的子标题，若不传或为空字符串则title上下位置居中显示
	titleLocation           //（可选项）标题在水平线上的位置，取值范围：center,left,right，默认left
	titleSize               //（可选项）标题字体的大小，默认12
	titleColor              //（可选项）标题字体的颜色值，默认#000000，支持 rgb,rgba,#
	subTitleLocation        //（可选项）子标题在水平线上的位置，取值范围：center,left,right默认left
	subTitleSize            //（可选项）子标题字体的大小，默认12
	subTitleColor           //（可选项）子标题字体的颜色值,默认黑色,rgb,rgba,#
    remark                  //（可选项）item右边备注，字符串类型，不传或空字符串则不显示
    arrow                   //（可选项）item右边箭头图标路径，支持widget，fs等本地协议，不传或空字符串则不显示
    rightBtn:   //(可选项)数组对象,往左滑动item露出的按钮信息组成的数组，无默认值，若为空则以open接口内data参数外的rightBtn参数为准，若open接口内data参数外的rightBtn参数和本参数都不传，则不可向左滑动
                  内部字段：
                  [{
	                  bg:         	  //（可选项）按钮背景色，支持 rgb，rgba，#，默认#388e8e
	                  title:        //（可选项）按钮标题，字符串类型，默认空字符串
	                  titleSize:    //（可选项）按钮标题字体大小，数字类型，默认12
	                  titleColor:    //（可选项）按钮标题颜色，支持 rgb，rgba，#，默认#ffffff，可为空
	                  highlightColor//（可选项）按钮选中时的颜色值,支持 rgb，rgba，#，默认无
	                  icon          //（可选项）按钮标题前图标图片路径，图标大小20*20，默认无，可不传，支持本地协议路径，如widget：//、fs://等
                  }]
}]
```
 
##示例代码
 
```js
var listView = api.require('listView');
listView.appendData({
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
- 描述：下拉刷新时显示的小箭头的本地图片路径
 
bgColor：
 
- 类型：字符串
- 默认值：#f5f5f5
- 描述：（可选项）下拉刷新视图的背景色，支持 rgb，rgba，#
 
textColor：
 
- 类型：字符串
- 默认值：#8e8e8e
- 描述：（可选项）提示文字颜色，支持 rgb，rgba，#
 
textDown：
 
- 类型：字符串
- 默认值：下拉可以刷新...
- 描述：（可选项）提示文字
 
textUp：
 
- 类型：字符串
- 默认值：松开开始刷新...
- 描述：（可选项）提示文字
 
 
showTime：
 
- 类型：布尔值
- 默认值：true
- 描述：（可选项）是否显示刷新时间
 
 
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
 
var listView = api.require('listView');
listView.setRefreshHeader({
    loadingImg : loadingImgae,
    bgColor:bgColor,
    textColor:textColor,
    textDown:textDown,
    textUp:textUp,
    showTime : showTime
}, function(ret, err){		
    if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
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
- 描述：上拉加载更多时显示的小箭头的本地图片路径
 
bgColor：
 
- 类型：字符串
- 默认值：#f5f5f5
- 描述：（可选项）上拉加载更多视图的背景色，支持 rgb，rgba，#
 
textColor：
 
- 类型：字符串
- 默认值：#8e8e8e
- 描述：（可选项）提示文字颜色，支持 rgb，rgba，#
 
textDown：
 
- 类型：字符串
- 默认值：上拉可以加载更多...
- 描述：（可选项）提示文字
 
textUp：
 
- 类型：字符串
- 默认值：松开开始加载...
- 描述：（可选项）提示文字
 
 
showTime：
 
- 类型：布尔值
- 默认值：true
- 描述：（可选项）是否显示刷新时间
 
 
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
var listView = api.require('listView');
listView.setRefreshFooter({
    loadingImg:loadingImgae,
    bgColor:bgColor,
    textColor:textColor,
    textDown:textDown,
    textUp:textUp,
    showTime:showTime
}, function(ret, err){		
    if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
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
var listView = api.require('listView');
listView.hide();
 
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
var listView = api.require('listView');
listView.show();
```
 
##补充说明
 
显示已隐藏的列表视图
 
##可用性
 
iOS系统，Android系统
 
可提供的1.0.1及更高版本