/*
Title: listViewPlus
Description: listViewPlus
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[setFrame](#2)

[getIndex](#3)

[getData](#4)

[setSlideButtons](#5)

[close](#6)

[reloadData](#7)
 
[deleteItem](#8)
 
[refreshItem](#9)

[insertItem](#10)
 
[appendData](#11)
 
[setRefreshHeader](#12)
 
[setRefreshFooter](#13)

[hide](#14)
 
[show](#15)
</div>

#**概述**

listViewPlus封装了一个列表控件，实现了一个可左右拖动item的列表视图。开发者可根据需求自定义列表的数据源，亦可自定义相关字段的样式。支持设置下拉刷新和上拉加载事件。本模块是listView的升级版，在listView基础上规范了接口参数，添加了若干功能，开放了更多可自定义的接口。

![图片说明](/img/docImage/listView.jpg)

#**open**<div id="1"></div>

打开

open({params}, callback(ret, err))

##params

x:

- 类型：数字
- 描述：（可选项）模块视图左上角点的X坐标
- 默认值：0，即所属的Window或Frame的左上角X坐标

y:

- 类型：数字
- 描述：（可选项）模块视图左上角点的Y坐标
- 默认值：0，即所属的Window或Frame的左上角Y坐标

w:

- 类型：数字
- 描述：（可选项）模块视图的宽度
- 默认值：所属的Window或Frame的宽度

h:

- 类型：数字
- 描述：（可选项）模块视图的高度
- 默认值：所属的Window或Frame的高度

fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window

style:

- 类型：JSON 对象
- 描述：（可选项）模块视图的样式
- 默认值：见内部字段
- 内部字段：

```js
{
	bounce:      //布尔类型；（可选项）模块视图页面是否支持弹动；默认值为true
	leftBg:      //字符串类型；（可选项）往右滑动item时，所显露出部分的背景色，支持 rgb、rgba、#；默认值为#5cacee
	rightBg:     //字符串类型；（可选项）往左滑动item时，所显露出部分的背景色，支持 rgb、rgba、#；默认值为#6c7b8b
	border:      //JSON对象；（可选项）item之间分割线的样式；默认值见内部字段
                 内部字段如下：{
					color:              //字符串类型；（可选项）分割线的颜色，支持 rgb、rgba、#；默认值为#696969
					width:              //数字类型；（可选项）分割线的宽度；默认值为1.0
				 }
	item:        //JSON对象；（可选项）item的样式；默认值见内部字段
				 内部字段如下: {
					bg:                 //字符串类型；（可选项）item的背景色，支持 rgb、rgba、#；默认#AFEEEE
					highlight:          //字符串类型；（可选项）item被按下和弹起之间的背景色，支持 rgb、rgba、#；默认#F5F5F5
					height:             //数字类型；（可选项）item的高度；默认值是55.0
					avatarW:            //数字类型；（可选项）item上头像的宽度；默认值为item的高度减去10.0个像素
					avatarH:            //数字类型；（可选项）item上头像的高度；默认值为item的高度减去10.0个像素
					placeholder:        //字符串类型；（可选项）item上头像占位图的路径，仅支持本地协议路径，如fs://、widget://等，默认值为APICloud的图标
					titleAlignment:     //字符串类型；（可选项）item上标题在水平方向的位置，取值范围center、left、right；默认值为left
					titleSize:          //数字类型；（可选项）item上标题字体大小；默认值为12.0
					titleColor:         //字符串类型；（可选项）item上标题字体颜色，支持 rgb,rgba,#；默认值为#000000
					subTitleAlignment:  //字符串类型；（可选项）item上子标题在水平方向的位置，取值范围：center、left、right；默认值为left
					subTitleSize:       //数字类型；（可选项）item上子标题字体大小；默认值为12.0
					subTitleColor:      //字符串类型：（可选项）item上子标题字体颜色，rgb、rgba、#；默认值为#000000 
					markStyle:          //字符串类型：（可选项）item右侧的备注部分的样式，默认值见内部字段
                                        内部字段如下: {
												remarkMargin://数字类型；（可选项）备注与item右侧边界的距离；默认值为10
												remarkColor: //字符串类型；（可选项）备注的字体颜色，支持 rgb、rgb、#；默认值为#000000
												remarkSize:  //数字类型；（可选项）备注的字体大小；默认值为16.0
												iconSize:    //数字类型；（可选项）当备注是图片时，图片的大小；默认值为30.0
										} 
				}        
}
``` 

data：

- 类型：数组
- 描述：列表的数据源
- 默认值：无
- 内部字段：

```js
[{
	avatarPath:             //字符串类型；（可选项）头像地址，支持http、https、widget、fs等本地和网络协议，网络图片会被缓存到本地，若不传则标题和子标题靠最左侧显示；默认值无
	title:                  //字符串类型；（可选项）标题，若subTitle不传或为空字符串则title上下位置居中显示；默认值无
	subTitle:               //字符串类型；（可选项）子标题，若不传或为空字符串则title上下位置居中显示；默认值无
	remark                  //字符串类型；（可选项）右边备注；默认值无
	icon                    //字符串类型；（可选项）右边备注图标路径，支持widget，fs等本地协议；默认值无
	leftBtn:                //JSON对象；（可选项）往右滑动item时，露出部分的按钮组成的数组，不传此参数则表示item不可向右滑动
							内部字段如下:[{
								bg:              //字符串类型；（可选项）按钮背景色，支持 rgb、rgba、#；默认值为#388e8e
								title:           //字符串类型；（可选项）按钮标题；默认值无
								titleSize:       //数字类型；（可选项）按钮标题字体大小；默认值为12.0
								titleColor:      //字符串类型；（可选项）按钮标题颜色，支持 rgb、rgba、#；默认值为#ffffff
								highlightColor:  //字符串类型；（可选项）按钮被按下和弹起之间的背景色,支持 rgb、rgba、#；默认无
								icon:            //字符串类型；（可选项）按钮标题前图标图片路径，图标大小20*20，支持本地协议路径，如widget://、fs://等；默认值无
							}]
	rightBtn:               //（可选项）往左滑动item露出的按钮组成的数组，不传此参数则表示item不可向左滑动
							内部字段如下：[{
								bg:              //字符串类型；（可选项）按钮背景色，支持 rgb、rgba、#；默认值为#388e8e
								title:           //字符串类型；（可选项）按钮标题；默认值无
								titleSize:       //数字类型；（可选项）按钮标题字体大小；默认值为12.0
								titleColor:      //字符串类型；（可选项）按钮标题颜色，支持 rgb、rgba、#；默认值为#ffffff
								highlightColor:  //字符串类型；（可选项）按钮选中时的颜色值，支持 rgb、rgba、#；默认值无
								icon:            //字符串类型；（可选项）按钮标题前图标的路径，图标大小20*20，支持本地协议路径，如widget://、fs://等；默认值无
							}]  
	leftSlipDistance:       //数字类型；（可选项）向右滑动露出左边按钮时，滑动距离占item宽的百分比，取值范围 0-100；默认值为50.0
	rightSlipDistance:      //数字类型；（可选项）向左滑动露出右边按钮时，滑动距离占item宽的百分比，取值范围 0-100；默认值为50.0
}]
```

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    eventType:  //字符串类型；回调事件的类型，取值范围如下：
	              show:      //模块视图加载成功事件
	              rightBtn:  //点击item侧滑右边按钮事件
	              leftBtn:   //点击item侧滑右边按钮事件
	              content:   //点击的item内容事件
	              avatar:    //点击的item的头像事件
	              icon:      //点击item右边备注图标事件
	index:      //数字类型；响应事件的item的索引
	btnIndex:   //数字类型；响应事件的侧滑按钮的索引
}
```

##示例代码

```js
var listViewPlus = api.require('listViewPlus');
listViewPlus.open({
    data:[{ 
        uid:"0000001",
        avatar:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
        title:'标题',
        subTitle:'子标题，说明文字。。。。。。',
        remark:"备注"
    },{ 
        uid:"0000002",
        avatar:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
        title:'标题',
        subTitle:'子标题，说明文字。。。。。。',
        remark:"备注"
    },{ 
        uid:"0000003",
        avatar:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
        title:'标题',
        subTitle:'子标题，说明文字。。。。。。',
        remark:"备注"
    },{ 
        uid:"0000004",
        avatar:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
        title:'标题',
        subTitle:'子标题，说明文字。。。。。。',
        remark:"备注"
    },{ 
        uid:"0000005",
        avatar:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
        title:'标题',
        subTitle:'子标题，说明文字。。。。。。',
        remark:"备注"
    },{ 
        uid:"0000006",
        avatar:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
        title:'标题',
        subTitle:'子标题，说明文字。。。。。。',
        remark:"备注"
    },{ 
        uid:"0000007",
        avatar:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
        title:'标题',
        subTitle:'子标题，说明文字。。。。。。',
        remark:"备注"
    },{ 
        uid:"0000008",
        avatar:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
        title:'标题',
        subTitle:'子标题，说明文字。。。。。。',
        remark:"备注"
    },{ 
        uid:"0000009",
        avatar:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
        title:'标题',
        subTitle:'子标题，说明文字。。。。。。',
        remark:"备注"
    },{ 
        uid:"0000010",
        avatar:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
        title:'标题',
        subTitle:'子标题，说明文字。。。。。。',
        remark:"备注"
    },{ 
        uid:"0000011",
        avatar:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
        title:'标题',
        subTitle:'子标题，说明文字。。。。。。',
        remark:"备注"
    }]
},function(ret,err){
    api.alert({msg:ret.eventType});
});
```

##补充说明

打开列表视图

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setFrame**<div id="2"></div>

重设列表模块视图的y，和h

setFrame({params })

##params

anim：

- 类型：布尔
- 描述：（可选项）改变模块视图的frame时，是否添加动画效果
- 默认值：false

y：

- 类型：数字
- 描述：（可选项）重设模块视图的y值
- 默认值：原值

h：

- 类型：数字
- 描述：（可选项）重设模块视图的h值
- 默认值：原值

##示例代码

	var listViewPlus = api.require('listViewPlus');
	listViewPlus.setFrame({
		anim:true ,
		y:0
	});

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**getIndex**<div id="3"></div>

根据唯一标识查找该item在列表中的下标

getIndex({params },callback(ret, err))

##params

key：

- 类型：字符串
- 描述：open时传入的data所包含的开发者自定义的唯一标识的key
- 默认值：无

value：

- 类型：字符串
- 描述：open时传入的data所包含的开发者自定义的唯一标识的value
- 默认值：无

##callBack

ret：

- 类型：JSON 对象
- 内部字段：

```js
	{
	    index: //数字类型；获取的item的索引
	    data:  //数组；当前操作的item的数据，内部字段与open里data元素一致
	}
```

##示例代码

	var listViewPlus = api.require('listViewPlus');
	listViewPlus.getIndex({
	     key:"uid",
	     value:"0000001"
	},function(ret,err){
	     api.alert({msg:ret.index})
	});

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**getData**<div id="4"></div>

根据item的索引获取item的数据

getData({params },callback(ret, err))

##params

index：

- 类型：数字
- 默认值：0
- 描述：（可选项）要获取数据的item的索引

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
	{
		data：               //操作的item的data内部字段跟传进来的data一致
	}
```
##示例代码

	var listViewPlus = api.require('listViewPlus');
	listViewPlus.getData({
	     index:0
	},function(ret,err){
	     api.alert({msg:ret.data});
	});

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setSlideButtons**<div id="5"></div>

设置侧滑item显示出来按钮

setRightButtons({params })

##params

index：

- 类型：数字
- 默认值：0
- 描述：（可选项）要设置侧滑按钮的item的索引

type：

- 类型：字符串
- 默认值：right
- 描述：（可选项）要设置的侧滑按钮，取值范围:right、left

buttons：

- 类型：数组对象
- 默认值：无
- 描述：(可选项)数组对象,往左滑动item露出的按钮信息组成的数组，
- 备注：若为不传则不可向左/右滑动
- 内部字段：

```js
   [{
        bg:           //（可选项）按钮背景色，支持 rgb、rgba、#，默认#388e8e
        title:        //（可选项）按钮标题，字符串类型，默认空字符串
        titleSize:    //（可选项）按钮标题字体大小，数字类型，默认12.0
        titleColor:   //（可选项）按钮标题颜色，支持 rgb、rgba、#，默认#ffffff
        highlightColor//（可选项）按钮选中时的颜色值,支持 rgb、rgba、#，默认无
        icon          //（可选项）按钮标题前图标图片路径，图标大小20*20，默认无，可不传，支持本地协议路径，如widget：//、fs://等。（icon的宽+title的宽居中显示）
   }]
```

##示例代码

```js
var listViewPlus = api.require('messageList');
listViewPlus.setSlideButtons({
     buttons: [{
            bg:  "#556B2F",  //按钮背景色，支持 rgb，rgba，#，默认#ee8262.
            title: "取消", //按钮名字，字符串类型，默认‘按钮’
            titleSize: 13,      //按钮标题大小，默认12
            titleColor: "#000000", // 按钮标题颜色，支持 rgb，rgba，#，默认#ffffff
            selectedColor: "#FFFFFF",  //按钮选中时候的颜色值,支持 rgb，rgba，#
            icon:"widget://image/messageList/delete.png"
        }, {
            bg:  "#4EEE94",  //按钮背景色，支持 rgb，rgba，#，默认#ee8262.
            title: "取消置顶", //按钮名字，字符串类型，默认‘按钮’
            titleSize: 13,      //按钮标题大小，默认12
            titleColor: "#000000", // 按钮标题颜色，支持 rgb，rgba，#，默认#ffffff
            selectedColor: "ffffff",  //按钮选中时候的颜色值,支持 rgb，rgba，#
            icon:"widget://image/messageList/delete.png"
        }]
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**close**<div id="6"></div>

关闭listViewPlus

close()

##示例代码

```js
    var listViewPlus = api.require('listViewPlusPlus');
    listViewPlus.close();
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**reloadData**<div id="7"></div>

刷新列表数据

reloadData({params})

##params

data：

- 类型：数组对象
- 默认值：无
- 描述：（可选项）列表的数据源，若不传或传空，则仅停止下拉刷新状态
- 内部字段：

```js
[{
	avatar:                 //（可选项）item的头像地址，支持http、https、widget、fs等本地和网络路径协议，网络图片会被缓存到本地，若不传则标题和子标题顶头显示
	title:                  //（可选项）item的标题，若subTitle不传或为空字符串则title上下位置居中显示，不传则不显示
	subTitle:               //（可选项）item的子标题，若不传或为空字符串则title上下位置居中显示
    remark                  //（可选项）item右边备注，字符串类型，不传或空字符串则不显示
    arrow                   //（可选项）item右边箭头图标路径，支持widget，fs等本地协议，不传或传空字符串则不显示
    leftBtn:  //（可选项）往右滑动item露出的按钮组成的数组，不传此参数则表示item不可向右滑动
               内部字段如下：[{
				      bg:         	  //（可选项）按钮背景色，支持 rgb、rgba、#，默认#388e8e
				      title:          //（可选项）按钮标题，字符串类型，默认空字符串
				      titleSize:      //（可选项）按钮标题字体大小，数字类型，默认12.0
				      titleColor:     //（可选项）按钮标题颜色，支持 rgb、rgba、#，默认#ffffff
				      highlightColor  //（可选项）按钮选中时的颜色值,支持 rgb、rgba、#，默认无
				      icon            //（可选项）按钮标题前图标图片路径，图标大小20*20，默认无，可不传，支持本地协议路径，如widget://、fs://等。（icon的宽+title的宽居中显示）
				 }]
	 rightBtn://（可选项）往左滑动item露出的按钮组成的数组，不传此参数则表示item不可向左滑动
	          内部字段如下：[{
				      bg:         	  //（可选项）按钮背景色，支持 rgb、rgba、#，默认#388e8e
				      title:          //（可选项）按钮标题，字符串类型，默认空字符串
				      titleSize:      //（可选项）按钮标题字体大小，数字类型，默认12.0
				      titleColor:     //（可选项）按钮标题颜色，支持 rgb、rgba、#，默认#ffffff
				      highlightColor  //（可选项）按钮选中时的颜色值,支持 rgb、rgba、#，默认无
				      icon            //（可选项）按钮标题前图标图片路径，图标大小20*20，默认无，可不传，支持本地协议路径，如widget://、fs://等。（icon的宽+title的宽居中显示）
				 }]  
	rightSlipDistance:		//（可选项）向左滑动露出右边按钮时，item的滑动距离咱item宽的百分比，默认50，取值范围 0-100
	leftSlipDistance:		//（可选项）向右滑动露出左边按钮时，item的滑动距离咱item宽的百分比，默认50，取值范围 0-100
}]
```

##示例代码

```js
var listViewPlus = api.require('listViewPlus');
listViewPlus.reloadData({
	 data:[{ 
        uid:"1000001",
        avatar:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
        title:'标题reload',
        remark:"备注"
    },{ 
        uid:"1000002",
        avatar:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
        title:'标题reload',
        remark:"备注"
    },{ 
        uid:"1000003",
        avatar:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
        title:'标题reload',
        remark:"备注"
    },{ 
        uid:"1000004",
        avatar:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
        title:'标题reload',
        remark:"备注"
    },{ 
        uid:"1000005",
        avatar:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
        title:'标题reload',
        remark:"备注"
    },{ 
        uid:"1000006",
        avatar:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
        title:'标题reload',
        remark:"备注"
    },{ 
        uid:"1000007",
        avatar:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
        title:'标题reload',
        remark:"备注"
    },{ 
        uid:"1000008",
        avatar:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
        title:'标题reload',
        remark:"备注"
    },{ 
        uid:"1000009",
        avatar:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
        title:'标题reload',
        remark:"备注"
    },{ 
        uid:"1000010",
        avatar:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
        title:'标题reload',
        remark:"备注"
    },{ 
        uid:"1000011",
        avatar:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
        title:'标题reload',
        remark:"备注"
    }]
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
 
 
#**deleteItem**<div id="8"></div>

删除指定索引的数据

deleteItem({params})

##params

index：

- 类型：数字
- 默认值：0
- 描述：（可选项）要删除的数据的索引


##示例代码

```js
var listViewPlus = api.require('listViewPlus');
 listViewPlus.deleteItem({
      index:2
 });
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
 
#**refreshItem**<div id="9"></div>

刷新指定index条目的数据

refreshItem({params})

##params

index：

- 类型：数字
- 默认值：0
- 描述：（可选项）要刷新数据的item索引下标

data：

- 类型：数组对象
- 默认值：无
- 描述：列表的数据源
- 内部字段：

```js
[{
	avatar:                 //（可选项）item的头像地址，支持http、https、widget、fs等本地和网络路径协议，网络图片会被缓存到本地，若不传则标题和子标题顶头显示
	title:                  //（可选项）item的标题，若subTitle不传或为空字符串则title上下位置居中显示，不传则不显示
	subTitle:               //（可选项）item的子标题，若不传或为空字符串则title上下位置居中显示
    remark                  //（可选项）item右边备注，字符串类型，不传或空字符串则不显示
    arrow                   //（可选项）item右边箭头图标路径，支持widget，fs等本地协议，不传或传空字符串则不显示
    leftBtn:  //（可选项）往右滑动item露出的按钮组成的数组，不传此参数则表示item不可向右滑动
               内部字段如下：[{
				      bg:         	  //（可选项）按钮背景色，支持 rgb、rgba、#，默认#388e8e
				      title:          //（可选项）按钮标题，字符串类型，默认空字符串
				      titleSize:      //（可选项）按钮标题字体大小，数字类型，默认12.0
				      titleColor:     //（可选项）按钮标题颜色，支持 rgb、rgba、#，默认#ffffff
				      highlightColor  //（可选项）按钮选中时的颜色值,支持 rgb、rgba、#，默认无
				      icon            //（可选项）按钮标题前图标图片路径，图标大小20*20，默认无，可不传，支持本地协议路径，如widget://、fs://等。（icon的宽+title的宽居中显示）
				 }]
	 rightBtn://（可选项）往左滑动item露出的按钮组成的数组，不传此参数则表示item不可向左滑动
	          内部字段如下：[{
				      bg:         	  //（可选项）按钮背景色，支持 rgb、rgba、#，默认#388e8e
				      title:          //（可选项）按钮标题，字符串类型，默认空字符串
				      titleSize:      //（可选项）按钮标题字体大小，数字类型，默认12.0
				      titleColor:     //（可选项）按钮标题颜色，支持 rgb、rgba、#，默认#ffffff
				      highlightColor  //（可选项）按钮选中时的颜色值,支持 rgb、rgba、#，默认无
				      icon            //（可选项）按钮标题前图标图片路径，图标大小20*20，默认无，可不传，支持本地协议路径，如widget://、fs://等。（icon的宽+title的宽居中显示）
				 }]  
	rightSlipDistance:		//（可选项）向左滑动露出右边按钮时，item的滑动距离咱item宽的百分比，默认50，取值范围 0-100
	leftSlipDistance:		//（可选项）向右滑动露出左边按钮时，item的滑动距离咱item宽的百分比，默认50，取值范围 0-100
}]
```


##示例代码

```js
var listViewPlus = api.require('listViewPlus');
listViewPlus.refreshItem({
      index:2,
      data: {title:'刷新指定下标的标题', subTitle:'刷新指定下标的子标题'}
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
 
#**insertItem**<div id="10"></div>

插入指定索引的数据

insertItemItem({params})

##params

index：

- 类型：数字
- 默认值：列表最后一条数据的索引
- 描述：（可选项）要插入的item索引下标

data：

- 类型：数组对象
- 默认值：无
- 描述：列表的数据源
- 内部字段：

```js
[{
	avatar:                 //（可选项）item的头像地址，支持http、https、widget、fs等本地和网络路径协议，网络图片会被缓存到本地，若不传则标题和子标题顶头显示
	title:                  //（可选项）item的标题，若subTitle不传或为空字符串则title上下位置居中显示，不传则不显示
	subTitle:               //（可选项）item的子标题，若不传或为空字符串则title上下位置居中显示
    remark                  //（可选项）item右边备注，字符串类型，不传或空字符串则不显示
    arrow                   //（可选项）item右边箭头图标路径，支持widget，fs等本地协议，不传或传空字符串则不显示
    leftBtn:  //（可选项）往右滑动item露出的按钮组成的数组，不传此参数则表示item不可向右滑动
               内部字段如下：[{
				      bg:         	  //（可选项）按钮背景色，支持 rgb、rgba、#，默认#388e8e
				      title:          //（可选项）按钮标题，字符串类型，默认空字符串
				      titleSize:      //（可选项）按钮标题字体大小，数字类型，默认12.0
				      titleColor:     //（可选项）按钮标题颜色，支持 rgb、rgba、#，默认#ffffff
				      highlightColor  //（可选项）按钮选中时的颜色值,支持 rgb、rgba、#，默认无
				      icon            //（可选项）按钮标题前图标图片路径，图标大小20*20，默认无，可不传，支持本地协议路径，如widget://、fs://等。（icon的宽+title的宽居中显示）
				 }]
	 rightBtn://（可选项）往左滑动item露出的按钮组成的数组，不传此参数则表示item不可向左滑动
	          内部字段如下：[{
				      bg:         	  //（可选项）按钮背景色，支持 rgb、rgba、#，默认#388e8e
				      title:          //（可选项）按钮标题，字符串类型，默认空字符串
				      titleSize:      //（可选项）按钮标题字体大小，数字类型，默认12.0
				      titleColor:     //（可选项）按钮标题颜色，支持 rgb、rgba、#，默认#ffffff
				      highlightColor  //（可选项）按钮选中时的颜色值,支持 rgb、rgba、#，默认无
				      icon            //（可选项）按钮标题前图标图片路径，图标大小20*20，默认无，可不传，支持本地协议路径，如widget://、fs://等。（icon的宽+title的宽居中显示）
				 }]  
	rightSlipDistance:		//（可选项）向左滑动露出右边按钮时，item的滑动距离咱item宽的百分比，默认50，取值范围 0-100
	leftSlipDistance:		//（可选项）向右滑动露出左边按钮时，item的滑动距离咱item宽的百分比，默认50，取值范围 0-100
}]
```

##示例代码

```js
var listViewPlus = api.require('listViewPlus');
listViewPlus.insertItem({
   index:2,
	data:{
	    avatar:' http://d.hiphotos.baidu.com/image/pic/item/4d086e061d950a7b29a788c209d162d9f2d3c922.jpg ',
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

可提供的1.0.0及更高版本
 
 
#**appendData**<div id="11"></div>
 
添加列表数据
 
appendData({params})
 
##params
 
data：

- 类型：数组对象
- 默认值：无
- 描述：列表的数据源，若不传或传空则仅停止上拉加载事件
- 内部字段：

```js
[{
	avatar:                 //（可选项）item的头像地址，支持http、https、widget、fs等本地和网络路径协议，网络图片会被缓存到本地，若不传则标题和子标题顶头显示
	title:                  //（可选项）item的标题，若subTitle不传或为空字符串则title上下位置居中显示，不传则不显示
	subTitle:               //（可选项）item的子标题，若不传或为空字符串则title上下位置居中显示
    remark                  //（可选项）item右边备注，字符串类型，不传或空字符串则不显示
    arrow                   //（可选项）item右边箭头图标路径，支持widget，fs等本地协议，不传或传空字符串则不显示
    leftBtn:  //（可选项）往右滑动item露出的按钮组成的数组，不传此参数则表示item不可向右滑动
               内部字段如下：[{
				      bg:         	  //（可选项）按钮背景色，支持 rgb、rgba、#，默认#388e8e
				      title:          //（可选项）按钮标题，字符串类型，默认空字符串
				      titleSize:      //（可选项）按钮标题字体大小，数字类型，默认12.0
				      titleColor:     //（可选项）按钮标题颜色，支持 rgb、rgba、#，默认#ffffff
				      highlightColor  //（可选项）按钮选中时的颜色值,支持 rgb、rgba、#，默认无
				      icon            //（可选项）按钮标题前图标图片路径，图标大小20*20，默认无，可不传，支持本地协议路径，如widget://、fs://等。（icon的宽+title的宽居中显示）
				 }]
	 rightBtn://（可选项）往左滑动item露出的按钮组成的数组，不传此参数则表示item不可向左滑动
	          内部字段如下：[{
				      bg:         	  //（可选项）按钮背景色，支持 rgb、rgba、#，默认#388e8e
				      title:          //（可选项）按钮标题，字符串类型，默认空字符串
				      titleSize:      //（可选项）按钮标题字体大小，数字类型，默认12.0
				      titleColor:     //（可选项）按钮标题颜色，支持 rgb、rgba、#，默认#ffffff
				      highlightColor  //（可选项）按钮选中时的颜色值,支持 rgb、rgba、#，默认无
				      icon            //（可选项）按钮标题前图标图片路径，图标大小20*20，默认无，可不传，支持本地协议路径，如widget://、fs://等。（icon的宽+title的宽居中显示）
				 }]  
	rightSlipDistance:		//（可选项）向左滑动露出右边按钮时，item的滑动距离咱item宽的百分比，默认50，取值范围 0-100
	leftSlipDistance:		//（可选项）向右滑动露出左边按钮时，item的滑动距离咱item宽的百分比，默认50，取值范围 0-100
}]
```
 
##示例代码
 
```js
var listViewPlus = api.require('listViewPlus');
listViewPlus.appendData({
 	data:[{title:'拼接数据标题',subTitle:'拼接数据子标题'}]
});
```
 
##补充说明
 
无
 
##可用性
 
iOS系统，Android系统
 
可提供的1.0.0及更高版本
 
#**setRefreshHeader**<div id="12"></div>
 
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
- 描述：（可选项）下拉刷新视图的背景色，支持 rgb、rgba、#
 
textColor：
 
- 类型：字符串
- 默认值：#8e8e8e
- 描述：（可选项）提示文字颜色，支持 rgb、rgba、#
 
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
var loadingImgae = 'widget://res/listViewPlus_arrow.png';     //刷新的小箭头，不可为空
var bgColor = '#F5F5F5';                                  //下拉刷新的背景颜色 ，有默认值，可为空
var textColor= '#8E8E8E';                                 //提示语颜色，有默认值，可为空
var textDown= '下拉可以刷新...';                             //尚未触发刷新时间的提示语，有默认值，可为空
var textUp= '松开开始刷新...';                               //触发刷新事件的提示语，有默认值，可为空
var showTime= true;                                       //是否显示时间，有默认值，可为空
 
var listViewPlus = api.require('listViewPlus');
listViewPlus.setRefreshHeader({
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
 
#**setRefreshFooter**<div id="13"></div>
 
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
- 描述：（可选项）上拉加载更多视图的背景色，支持 rgb、rgba、#
 
textColor：
 
- 类型：字符串
- 默认值：#8e8e8e
- 描述：（可选项）提示文字颜色，支持 rgb、rgba、#
 
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
var loadingImgae = 'widget://res/listViewPlus_arrow.png';       //刷新的小箭头，不可为空
var bgColor = '#F5F5F5';                                    //下拉刷新的背景颜色 ，有默认值，可为空
var textColor= '#8E8E8E';                                   //提示语颜色，有默认值，可为空
var textDown= '下拉可加载更多...';                             //尚未触发刷新时间的提示语，有默认值，可为空
var textUp= '松开开始加载...';                                 //触发刷新事件的提示语，有默认值，可为空
var showTime= true;                                         //是否显示时间，有默认值，可为空        
var listViewPlus = api.require('listViewPlus');
listViewPlus.setRefreshFooter({
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

#**hide**<div id="14"></div>
 
隐藏listViewPlus
 
hide()
 
##示例代码
 
```js    
var listViewPlus = api.require('listViewPlus');
listViewPlus.hide();
 
```
 
##补充说明
 
隐藏listViewPlus，并没有从内存里清除
 
##可用性
 
iOS系统，Android系统
 
可提供的1.0.0及更高版本


#**show**<div id="15"></div>
 
显示listViewPlus
 
show()
 
##示例代码
 
```js    
var listViewPlus = api.require('listViewPlus');
listViewPlus.show();
 
```
 
##补充说明
 
显示已隐藏的列表视图
 
##可用性
 
iOS系统，Android系统
 
可提供的1.0.0及更高版本