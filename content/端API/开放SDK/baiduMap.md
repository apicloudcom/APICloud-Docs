/*
Title: baiduMap
Description: baiduMap
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[close](#2)

[setType](#3)

[startLocation](#4)

[stopLocation](#5)

[getLocation](#6)

[getBaiduFromGoogle](#7)

[setCenter](#8)

[setZoomLevel](#9)

[setZoomEnable](#10)

[setScroolEnable](#11)

[setRotation](#b1)

[setOverlook](#b2)

[setHidden](#12)

[showUserLocation](#13)

[zoomOut](#14)

[zoomIn](#15)

[addAnnotations](#16)

[setBubbleStyle](#17)

[setThreeTitleBubble](#B17)

[addMarks](#18)

[setMarkStyle](#19)

[removeAnnotations](#20)

[addLine](#21)

[addPolygon](#22)

[addCircle](#23)

[addOverMark](#24)

[removeOverlay](#25)

[addRoute](#26)

[setRoutePlan](#260)

[removeRoute](#27)

[searchInCity](#28)

[searchNearBy](#29)

[searchInBounds](#30)

[getLocationFromName](#31)

[getNameFromLocation](#32)

[getBusRouteFromLineNum](#33)

[removeBusRoute](#34)

[longPressGesture](#35)

[setMapListener](#b3)

[setMapTapListener](#b4)
</div>

#**概述**

baiduMap封装了百度地图的SDK，对百度地图的相关接口做了一层严格准确的封装 把相对复杂的调用接口简单化，极大的简化了手机app集成百度地图的流程 该模块的接口含盖了百度地图几乎所有的接口，功能详情可参考目录。**[bMap 模块](/端API/开放SDK/bMap)是 baiduMap 模块的优化版。建议使用  bMap 模块，此模块已停止更新。**

**在集成此模块之前需先配置config文件,在config里添加如下字段：**
名称：baiduMap

参数：android_api_key、ios_api_key

描述：百度开放平台的安全码获取需要区分移动平台，意味着如果你的同一个App需要同时支持IOS和Android平台，那么，您必须为这两个平台单独申请apiKey，即同一个App申请两个apiKey，并将这两个apiKey同时配置在config文件中。	

配置示例:

```js
  <feature name="baiduMap">
		<param name="android_api_key" value="f7Is0dWLom2q6rV3ZfFPZ1aa" />
		<param name="ios_api_key" value="81qz3dBYB5q2nGji4IYrawr1" />
  </feature>
```
字段描述：
1. android_api_key：android版本的apiKey
1. ios_api_key：Ios版本的apiKey

#**open**<div id="1"></div>

打开百度地图

open({params}, callback(ret, err))

##params
x:

- 类型：数字
- 默认值：0
- 描述：（可选项）地图视图左上角点的x坐标

y:

- 类型：数字
- 默认值：0
- 描述：（可选项）地图视图左上角点的y坐标

<del>width:</del>

- <del>类型：数字</del>
- <del>默认值：无</del>
- <del>描述：地图视图的宽，可为空</del>

w:

- 类型：数字
- 默认值：当前设备屏幕的宽
- 描述：（可选项）地图视图的宽
 
 <del>height:</del>

- <del>类型：数字</del>
- <del>默认值：无</del>
- <del>描述：地图视图的高，可为空</del>
 
 h:

- 类型：数字
- 默认值：w-20
- 描述：（可选项）地图视图的高
 
lon:

- 类型：数字
- 默认值：无
- 描述：（可选项）开启地图时设置的中心点的经度
 
lat:

- 类型：数字
- 默认值：无
- 描述：（可选项）开启地图时设置的中心点的经度

fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window

fixed:

- 类型：布尔
- 默认值：true
- 描述：（可选项）是否将模块视图固定到窗口上，不跟随窗口上下滚动

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status: 1	 //操作成功状态值
}
```

##示例代码

```js
var baiduMap = api.require('baiduMap');
baiduMap.open({
	x: 0,
	y: 64,
	w: 320,
	h: 400
}, function(ret, err){		
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**close**<div id="2"></div>

关闭百度地图

close()

##示例代码

```js
var baiduMap = api.require('baiduMap');
baiduMap.close();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**setType**<div id="3"></div>

设置百度地图类型

setType({params})

##params

<del>mapType</del>:

- <del>类型：字符串</del>
- <del>默认值：无</del>
- <del>描述：地图类型（详见[地图类型](!Constant)常量），不能为空</del>

type:

- 类型：字符串
- 默认值：standard
- 描述：（可选项）地图类型（详见[地图类型](!Constant)常量）

##示例代码

```js
var baiduMap = api.require('baiduMap');
baiduMap.setType({
	type: 'standard'
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**startLocation**<div id="4"></div>

开始定位

startLocation({params}, callback(ret, err))

##params

accuracy：

- 类型：字符串
- 默认值：无
- 描述：精度（详见[精度](!Constant)常量）

filter：

- 类型：数字
- 默认值：1.0
- 描述：（可选项）位置更新所需最小距离（单位米）

autoStop：

- 类型：布尔
- 默认值：true
- 描述：（可选项）获取到位置信息后是否自动停止定位

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
    longitude:116.213                      //经度 deprecated
    latitude:39.213                        //纬度 deprecated
    lon:116.213                            //经度
    lat:39.213                             //纬度
    timestamp:1396068155591                //时间戳
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
	msg:”” 		//错误描述
}
```

##示例代码

```js
var baiduMap = api.require('baiduMap');
baiduMap.startLocation({
	accuracy: '100m',
	filter:1,
	autoStop: true
}, function(ret, err){		
    if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##补充说明

开始定位

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**stopLocation**<div id="5"></div>

停止定位

stopLocation()

##补充说明

停止定位

##示例代码

```js
var baiduMap = api.require('baiduMap');
baiduMap.stopLocation();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**getLocation**<div id="6"></div>

获取位置信息

getLocation(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    longitude:116.213                      //经度 deprecated
    latitude:39.213                        //纬度 deprecated
    lon:116.213                            //经度
    lat:39.213                             //纬度
    timestamp:1396068155591                //时间戳
}
```
err：

- 类型：JSON 对象
- 内部字段：

```js
{
	msg:””		//错误描述
}
```

##补充说明

获取位置信息

##示例代码

```js
var baiduMap = api.require('baiduMap');
baiduMap.getLocation(function( ret, err ){		
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

#**getBaiduFromGoogle**<div id="7"></div>

将谷歌坐标转换为百度坐标

getBaiduFromGoogle({params}, callback(ret, err))

##params

lon：

- 类型：数字
- 默认值：无
- 描述：经度

lat：

- 类型：数字
- 默认值：无
- 描述：纬度

mcode：

- 类型：字符串
- 默认值：无
- 描述：安全码(到http://lbsyun.baidu.com/apiconsole/key，点击应用的设置按钮，进入应用设置界面，其中安全码便是：（数字签名+;+包名)

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：
```js
{
    lon:116.213           //经度
    lat:39.213            //纬度
}
```
err：

- 类型：JSON 对象
- 内部字段：

````js
{
	msg:  		//错误描述
}
```
##补充说明

转换坐标

##示例代码

```js
var baiduMap = api.require('baiduMap');
baiduMap.getBaiduFromGoogle ({
	lon: 116.351,
	lat: 39.283,	
	mcode: '0B:13:25:D7:85:46:0A:67:12:F3:29:88:64:56:63:10:7A:9C:C4:59;com.apicloud.A6985734480360'
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

#**setCenter**<div id="8"></div>

设置百度地图中心点

setCenter({params})

##params

lon：

- 类型：数字
- 默认值：无
- 描述：经度

lat：

- 类型：数字
- 默认值：无
- 描述：纬度

##示例代码
```js
var baiduMap = api.require('baiduMap');
baiduMap.setCenter({
	lon: 116.351,
	lat: 39.283
});
```
##可用性
iOS系统，Android系统

可提供的1.0.0及更高版本

#**setZoomLevel**<div id="9"></div>

设置百度地图缩放等级

setZoomLevel({params})

##params

level：

- 类型：数字
- 默认值：10
- 描述：（可选项）地图比例尺级别，在手机上当前可使用的级别为3-18级

##示例代码

```js
var baiduMap = api.require('baiduMap');
baiduMap.setZoomLevel({
	level: 3
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**setZoomEnable**<div id="10"></div>

设置百度地图是否能放大缩小

setZoomEnable({params})

##params

enable：

- 类型：布尔
- 默认值：true
- 描述：（可选项）捏合手势可否缩放地图

##示例代码

```js
var baiduMap = api.require('baiduMap');
baiduMap.setZoomEnable({
	enable: false
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**setScrollEnable**<div id="11"></div>

设置百度地图是否能滚动

setScrollEnable({params})

##params

enable：

- 类型：布尔
- 默认值：ture
- 描述：（可选项）拖动手势可否移动地图

示例代码
```js
var baiduMap = api.require('baiduMap');
baiduMap.setScrollEnable({
    enable: false
});
```
##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setRotation**<div id="b1"></div>

设置百度地图旋转角度

setRotation({params})

##params

rotation：

- 类型：数字
- 默认值：0
- 描述：（可选项）地图旋转角度，可使用的范围为-180-180级

##示例代码
```js
var baiduMap = api.require('baiduMap');
baiduMap.setRotation({
   rotation: 10
});
```
##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

#**setOverlook**<div id="b2"></div>

设置百度地图俯视角度

setOverlook({params})

##params

overlook：

- 类型：数字
- 默认值：0
- 描述：（可选项）地图俯视角度，可使用的范围为-45-0级

##示例代码
```js
var baiduMap = api.require('baiduMap');
baiduMap.setOverlook({
   overlook: -10
});
```
##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

#**setHidden**<div id="12"></div>

设置是否隐藏地图，此功能只是隐藏地图，不影响地图上的标注气泡等覆盖物

setHidden({params})

##params

hidden：

- 类型：布尔
- 默认值：true
- 描述：（可选项）是否隐藏地图视图

##示例代码
```js
var baiduMap = api.require('baiduMap');
baiduMap.setHidden({
    hidden: false
});
```
##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**showUserLocation**<div id="13"></div>

设置是否在地图上显示用户位置

showUserLocation({params})

##params

isShow：

- 类型：布尔
- 默认值：true
- 描述：（可选项）是否显示用户位置

trackingMode：

- 类型：字符串
- 默认值：none
- 描述：（可选项）用户当前位置显示形式，详细参数见[跟踪类型](!Constant)

##示例代码

```js
var baiduMap = api.require('baiduMap');
baiduMap.showUserLocation({
	isShow: true,
	trackingMode: 'none'
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**zoomOut**<div id="14"></div>

放大地图，缩小视角

zoomOut()

##示例代码

```js
var baiduMap = api.require('baiduMap');
baiduMap.zoomOut();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**zoomIn**<div id="15"></div>

缩小地图，放大视角

zoomIn()

##示例代码

```js
var baiduMap = api.require('baiduMap');
baiduMap.zoomIn();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**addAnnotations**<div id="16"></div>

在地图上添加大头针

addAnnotations({params})

##params

annoArray：

- 类型：数组
- 默认值：无
- 描述：添加的大头针的信息组成的数组
- 内部字段：

```js
[{
        id:1                          //数字类型；大头针的id
        lon:116.233                   //数字类型；大头针所在位置的经度
        lat:39.134                    //数字类型；大头针所在位置的维度
        title: 'title'                //字符串类型；点击大头针时弹出的气泡的大标题；无默认值
        subTitle: 'subtitle'          //字符串类型；点击大头针时弹出的气泡的小标题；无默认值
        img:                          //（可选项）字符串类型；自定义大头针图片路径，若不传则显示pinImg 
        showBubble:                   //（可选项）布尔类型；点击大头针是否显示气泡，布尔类型，默认true
}]
```

pinImg：

- 类型：字符串
- 默认值：无
- 描述：（可选项）自定义的大头针图片，若不传则显示默认红色大头针


##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
    pinId:                  //用户点击大头针气泡时返回其id
    eventType：             //事件类型，字符串，取值范围如下： 
                               pin   //用户点击大头针事件
                               bubble//用户点击气泡的事件
}
```

##示例代码

```js
var baiduMap = api.require('baiduMap');
baiduMap.addAnnotations({
	annoArray:[{id:1,lon:116.297,lat:40.109,title:'第一个',subTitle:'子标题'},
			{id:2,lon:116.29,lat:40.109,title:'第二个',subTitle:'子标题'},
			{id:3,lon:116.298,lat:40.11,title:'第三个',subTitle:'子标题'}]
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


#**setBubbleStyle**<div id="17"></div>

设置大头针上气泡的类型

setBubbleStyle({params})

##params

type：

- 类型：字符串
- 默认值：normal
- 描述：（可选项）气泡布局类型，保留使用

bubbleBgimg：

- 类型：字符串
- 默认值：无
- 描述：气泡的背景图片路径

imgPath：

- 类型：字符串
- 默认值：无
- 描述：自定义类型的气泡上的头像图片路径

id：

- 类型：数字
- 默认值：无
- 描述：所要设置的大头针的id

##示例代码

```js
var baiduMap = api.require('baiduMap');
baiduMap.setBubbleStyle({
	bubbleBgimg: 'widget://res/bubble_bg.png',
	imgPath: 'widget://res/bubble_head.png',
	id: 2
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#** setThreeTitleBubble**<div id="B17"></div>

设置大头针上的气泡为一个头像加三个标题的类型

setThreeTitleBubble({params})

##params

id：

- 类型：数字
- 默认值：无
- 描述：所要设置的大头针的id

style:

- 类型：JSON 对象
- 默认值：见内部字段
- 描述：（可选项）气泡的样式
- 内部字段：

```js
{
    titleSize:       //（可选项）数字类型；标题的颜色，支持 rgb、rgba、#；默认值为：14.0
    titleColor:      //（可选项）字符串类型；标题的字体大小；默认值为：#000000
    preSize:         //（可选项）数字类型；子标题后缀的字体大小；默认值为：12.0
    preColor:        //（可选项）字符串类型；子标题后缀的颜色，支持 rgb、rgba、#；默认值为：#969696
    subTitleSize:    //（可选项）数字类型；子标题的字体大小；默认值为：14.0
    subTitleColor:   //（可选项）字符串类型；子标题的颜色，支持 rgb、rgba、#；默认值为：#8B6508
    descriptionSize: //（可选项）数字类型；描述文字的字体大小；默认值为：12.0
    descriptionColor://（可选项）字符串类型；描述文字的颜色，支持 rgb、rgba、#；默认值为：#698B22
    avatarSize:      //（可选项）数字类型；头像图片显示区域的大小；默认值为：40.0
    avatarMarginLeft://（可选项）数字类型；头像图片显示区域左边距；默认值为：5.0
    avatarMarginUp:  //（可选项）数字类型；头像图片显示区域上边距；默认值为：5.0
    arrowSize:       //（可选项）数字类型；右边箭头图标的大小；默认值为：20.0
    arrowMarginRight://（可选项）数字类型；右边箭头图标的右边距；默认值为：5.0
    placeholderImg:  //（可选项）字符串类型；头像占位图片，仅支持本地路径；无默认值
}
```

image:

- 类型：JSON 对象
- 默认值：见内部字段
- 描述：气泡的图片
- 内部字段：

```js
{
    bg:      //字符串类型；气泡的背景图片路径，暂仅支持本地路径协议（widget://、fs://....），160*60大小；无默认值
    avatar:  //字符串类型；自定义气泡上的头像图片路径，支持本地和网络路径（http://、widget://、fs://....），不传则不显示；无默认值
    icon:    //字符串类型；描述文字前的图标路径，暂仅支持本地路径协议（widget://、fs://....），不传则不显示；无默认值
    arrow:   //字符串类型；气泡右边小箭头图标路径，暂仅支持本地路径协议（widget://、fs://....），不传则不显示；无默认值
}
```

text:

- 类型：JSON 对象
- 默认值：见内部字段
- 描述：气泡上的文字
- 内部字段：

```js
{
    title:      //字符串类型；气泡上的标题文字，不传则不显示；无默认值
    subTitle:   //字符串类型；气泡上的子标题文字，不传则不显示；无默认值
    pre:        //字符串类型；气泡上的子标题的后缀文字，不传则不显示；无默认值
    description://字符串类型；气泡上的描述文字，不传则不显示；无默认值
}
```

##示例代码

```js
var baiduMap = api.require('baiduMap');
baiduMap.setThreeTitleBubble({
	id:1,
	image:{
		bg:'widget://image/baidu_bubble_bg.png',
		avatar:'widget://image/baidu_bubble_head.png',
		icon:'widget://image/baidu_bubble_icon.png',
		arrow:'widget://image/baidu_bubble_arrow.png'
	},
	text:{
	   title:'龙城假日皇冠大酒店',
	   pre:'/天',
	   subTitle:'$100',
	   description:'不支持团购'
	},
	style:{
	   placeholderImg:'widget://image/baidu_bubble_place.png'
	}
});
```

##可用性

iOS系统，Android系统

可提供的1.0.3及更高版本

#**addMarks**<div id="18"></div>

在地图上添加布告牌

addMarks({params})

##params

marks：

- 类型：数组
- 默认值：无
- 描述：添加的布告牌的信息组成的数组

内部字段：

```js
    [{
        id:1,                           //布告牌的id，数字
        lon:116.233,                    //布告牌所在位置的经度，数字
        lat:39.134,                     //布告牌所在位置的维度，数字
        title: 'title',                 //布告牌的大标题，字符串，
        subTitle: 'subtitle'            //布告牌的小标题，字符串
    }]
```

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    markID:""  //用户点击布告牌时返回该布告牌的id deprecated
    markId:""  //用户点击布告牌时返回该布告牌的id
 }
```
##示例代码

```js
var baiduMap = api.require('baiduMap');
baiduMap.addMarks ({
	marks:[{id:1,lon:116.297,lat:40.109,title:'第一个',subTitle:'子标题'},
		{id:2,lon:116.298,lat:40.109,title:'第二个',subTitle:'子标题'},
		{id:3,lon:116.298,lat:40.111,title:'第三个',subTitle:'子标题'}]
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


#**setMarkStyle**<div id="19"></div>

设置布告牌的类型

setMarkStyle({params});

##params

headImg：

- 类型：字符串
- 默认值：无
- 描述：自定义类型的布告牌上的头像图片路径

bgImg：

- 类型：字符串
- 默认值：无
- 描述：自定义的布告牌的背景图片的路径

id：

- 类型：数字
- 默认值：无
- 描述：所要设置的布告牌的id

##示例代码

```js
var baiduMap = api.require('baiduMap');
baiduMap.setMarkStyle ({
	bgImg:'widget://res/mark_bg_test.png',
	headImg:'widget://res/mark_test.png',
	id:6
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**removeAnnotations**<div id="20"></div>

移除指定id的大头针或布告牌

removeAnnotations({params})

##params

idArray：

- 类型：数组
- 默认值：无
- 描述：所要移除的大头针或布告牌id（数字）

##示例代码

```js
var baiduMap = api.require('baiduMap');
baiduMap.removeAnnotations({
	idArray:[1,3,5,7]
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**addLine**<div id="21"></div>

在地图上添加线

addLine({params})

##params

style：

- 类型：JSON 对象
- 默认值：无
- 描述：画线的类型

内部字段：
```js
{
    id:100                         //线的id，数字
    fillColor:'#FF0000'            //画线的填充色，字符串
    strokeColor:'#990033'          //画线的边框色，字符串
    lineWidth:3                    //画线的宽度，默认为2.0，数字
}
```
pointArray：

- 类型：数组
- 默认值：无
- 描述：确定画线的各个点组成的数组
- 内部字段：

```js
[
	{
	    lon:116.297,   	 //经度，数字
	    lat:40.109		 //纬度，数字
	}
]
```

##示例代码

```js
var baiduMap = api.require('baiduMap');
baiduMap.addLine({
	style:{
		id:100,
		fillColor:'#FF0000',
		strokeColor:'#990033',
		lineWidth:3
	},
	pointArray:[{lon:116.297,lat:40.109},
			{lon:116.298,lat:40.109}]
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**addPolygon**<div id="22"></div>

在地图上添加多边形

addPolygon({params})

##params

style：

- 类型：JSON 对象
- 默认值：无
- 描述：画线的类型

内部字段：

```js
{
    id:100                             //线的id，数字
    fillColor:'#FF0000'                //画线的填充色，字符串
    strokeColor:'#990033'              //画线的边框色，字符串
    lineWidth:3                        //画线的宽度，默认为2.0，数字
}
```

pointArray：

- 类型：数组
- 默认值：无
- 描述：确定画线的各个点组成的数组
- 内部字段：

```js
[
    {
        lon:116.297               //经度，数字
        lat:40.109                //纬度，数字
    }
]
```

##示例代码

```js
var baiduMap = api.require('baiduMap');
baiduMap.addPolygon ({
    style:{
	    id:100,
	    fillColor:'#FF0000',
	    strokeColor:'#990033',
	    lineWidth:3
    },
    pointArray:[{lon:116.297,lat:40.109},
    		{lon:116.298,lat:40.109},
    		{lon:116.298,lat:40.11}]
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**addCircle**<div id="23"></div>

在地图上添加圆圈

addCircle({params})

##params

id：

- 类型：数字
- 默认值：无
- 描述：圆圈的id

fillColor：

- 类型：字符串
- 默认值：无
- 描述：圆圈的填充色

strokeColor：

- 类型：字符串
- 默认值：无
- 描述：圆圈的边框色

lineWidth：

- 类型：数字
- 默认值：2
- 描述：（可选项）画线的宽度

lon：

- 类型：数字
- 默认值：无
- 描述：经度

lat：

- 类型：数字
- 默认值：无
- 描述：纬度

radius：

- 类型：数字
- 默认值：无
- 描述：圆的半径

##示例代码

```js
var baiduMap = api.require('baiduMap');
baiduMap.addCircle({
	id:101,
	lon:116.298,
	lat:40.11,
	radius:500,
	fillColor:'#FF0000',
	strokeColor:'#990033',
	lineWidth:3
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**addOverMark**<div id="24"></div>

在地图上添加图片

addOverMark({params})

#**params**

id：

- 类型：数字
- 默认值：无
- 描述：id号

imgPath：

- 类型：字符串
- 默认值：无
- 描述：图片的路径

lbLon：

- 类型：数字
- 默认值：无
- 描述：左下角点的经度

lbLat：

- 类型：数字
- 默认值：无
- 描述：左下角点的纬度

rtLon：

- 类型：数字
- 默认值：无
- 描述：右上角点的经度

rtLat：

- 类型：数字
- 默认值：无
- 描述：右上角点的纬度

##示例代码

```js
var baiduMap = api.require('baiduMap');
baiduMap.addOverMark({
	id:200,
	lbLon:116.297,
	lbLat:40.109,
	rtLon:116.298,
	rtLat:40.11,
	imgPath:'widget://res/over_img.png'
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**removeOverlay**<div id="25"></div>

移除指定id的覆盖物

removeOverlay({params})

##params

idArray：

- 类型：数组
- 默认值：无
- 描述：所要移除的id（数字）组成的数组

##示例代码
```js
var baiduMap = api.require('baiduMap');
baiduMap.removeOverlay({
    idArray:[1,3,5,7]
});
```
##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**addRoute**<div id="26"></div>

添加路线

addRoute({params}, callback(ret, err))

##params

id：

- 类型：数字
- 默认值：无
- 描述：id号

type：

- 类型：字符串
- 默认值：无
- 描述：路线类型（drive开车，transit公交，walk步行）

policy：

- 类型：字符串
- 默认值：ecar_dis_first\ ebus_transfer_first
- 描述：（可选项）路线策略,取值范围详情见[路线策略](!Constant)

startPoint：

- 类型：JSON 对象
- 默认值：无
- 描述：起点信息
- 内部字段：

```js
{
    city:'北京'                 //起点城市
    name:'史各庄'               //起点名-----和经纬度配合使用，有经纬度时，此参数可不传
    lon:116.213                //起点经度-----和起点名配合使用，有起点名时，此参数可不传
    lat:39.213                 //起点纬度-----和起点名配合使用，有起点名时，此参数可不传
}
```
endPoint：

- 类型：JSON 对象
- 默认值：无
- 描述：终点信息
- 内部字段：

```js
{
    city:'北京'                 //终点城市
    name:'龙翔路'               //终点名-----和起点名配合使用，有经纬度时，此参数可不传
    lon:116.213                //终点经度-----和终点名配合使用，有终点名时，此参数可不传
    lat:39.213                 //终点纬度-----和终点名配合使用，有终点名时，此参数可不传
}
```
##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status:""      //操作成功状态值
    steps:""       //路线方案，数组对象，路线每个结点的信息
    plans：        //建议路线方案组成的数组
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
    msg:""      //错误描述
    code:””   //错误码，取值范围如下：
               0：检索结果正常
               1：检索词有歧义
               2：检索地址有歧义
               3：该城市不支持公交搜索
               4：不支持跨城市公交
               5：没有找到检索结果
               6：起终点太近
    suggestStarts： //建议起点信息组成的数组，若非传入起点信息模糊则为空
       内部字段：[{
            name：  //地点名
            city:   //地点所在城市
            lon:    //地点经度
            lat:    // 地点纬度
       }]
    suggestEnds：  //建议终点信息组成的数组，若非传入终点信息模糊则为空
       内部字段：[{
            name：   //地点名
            city:   //地点所在城市
            lon:    //地点经度	
            lat:    // 地点纬度
    }]
}
```

##示例代码

```js
var baiduMap = api.require('baiduMap');
baiduMap.addRoute({
	id:300,
	type:'drive',
	startPoint:{
		city:'北京',
		name:'史各庄南',
		lon:116.213,
		lat:39.213
	},
	endPoint:{
		city:'北京',
		name:'龙翔路',
		lon:116.384,
		lat:39.989
	}
}, function(ret, err){		
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#** setRoutePlan**<div id="260"></div>

设置已添加路线的方案

setRoutePlan({params}, callback(ret, err))

##params

type：

- 类型：字符串
- 默认值：transit
- 描述：（可选项）路线类型（取值范围：transit公交）保留使用

planIndex：

- 类型：数字
- 默认值：0
- 描述：（可选项）从添加路线时返回的所有方案中选中的路线方案下标

##示例代码

```js
var baiduMap = api.require('baiduMap');
baiduMap.setRoutePlan({
	planIndex: 1
});
```
##补充说明

此接口必须在调用addRoute接口之后才可调用，暂仅支持android

##可用性

Android系统

可提供的1.0.1及更高版本


#**removeRoute**<div id="27"></div>

移除指定id的路线

removeRoute({params})

##params

idArray：

- 类型：数组
- 默认值：无
- 描述：所要移除的id（数字）组成的数组

内部字段：

```js
[
    1,
    2
]
```

##示例代码
```js
var baiduMap = api.require('baiduMap');
baiduMap.removeRoute({
	idArray: [300,301,302]
});
```
##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**searchInCity**<div id="28"></div>

根据关键字搜索兴趣点

searchInCity({params}, callback(ret, err))

##params

city：

- 类型：字符串
- 默认值：无
- 描述：指定的城市内搜索

key：

- 类型：字符串
- 默认值：无
- 描述：指定的要搜索的关键字

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status:                 //是否查找成功
	totalNum:               //本次搜索的总结果数
	currNum:                 //当前页的结果数
	totalPage:              //本次搜索的总页数
	pageIndex:              //当前页的索引
	resultArray:            //返回搜索结果列表，是一个数组
	                        内部字段：
	                        [{
										lon:                    //当前内容的经度
										lat:                    //当前内容的纬度
										name:                   //名称
										uid:                    //id
										add:                    //地址
										city:                   //所在城市
										phone:                  //电话号码
										postCode:               //邮编
										poiType:                //POI类型，0:普通点 1:公交站 2:公交线路 3:地铁站 4:地铁线路
								}]
}
```
err：

- 类型：JSON 对象
- 内部字段：

```js
{
	msg: 	//返回报错信息
}
```

##示例代码

```js
var city="北京';
var key="学校';
var index= 0;
var baiduMap = api.require('baiduMap');
baiduMap.searchInCity({
	city:city,
	key:key
}, function(ret, err){		
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**searchNearBy**<div id="29"></div>

根据单个关键字在指定圆圈区域内搜索兴趣点

searchNearBy({params}, callback(ret, err))

##params

key：

- 类型：字符串
- 默认值：无
- 描述：指定的要搜索的关键字

lon：

- 类型：数字
- 默认值：无
- 描述：指定的区域中心点经度

lat：

- 类型：数字
- 默认值：无
- 描述：指定的区域中心点纬度

radius：

- 类型：数字
- 默认值：无
- 描述：指定的区域半径，单位为m

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status:                 //是否查找成功
	totalNum:               //本次搜索的总结果数
	currNum:                 //当前页的结果数
	totalPage:              //本次搜索的总页数
	pageIndex:              //当前页的索引
	resultArray:            //返回搜索结果列表，是一个数组
	                         内部字段：
	                         [{
										lon:                    //当前内容的经度
										lat:                    //当前内容的纬度
										name:                   //名称
										uid:                    //id
										add:                   //地址
										city:                   //所在城市
										phone:                  //电话号码
										postCode:               //邮编
										poiType:                //POI类型，0:普通点 1:公交站 2:公交线路 3:地铁站 4:地铁线路
								  }]
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
	msg: 	//返回报错信息
}
```
##示例代码

```js
var baiduMap = api.require('baiduMap');
baiduMap.searchNearBy({
	key:'KTV',
	lon:116.384767,
	lat:39.989539,
	radius:2000
}, function(ret, err){		
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##补充说明

在指定圆圈区域内搜索兴趣点

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**searchInBounds**<div id="30"></div>

根据单个关键字在指定方形区域内搜索兴趣点

searchInBounds({params}, callback(ret, err))

##params

key：

- 类型：字符串
- 默认值：无
- 描述：指定的要搜索的关键字

lbLon：

- 类型：数字
- 默认值：无
- 描述：区域左下角经度

lbLat：

- 类型：数字
- 默认值：无
- 描述：指定的区域左下角纬度

rtLon：

- 类型：数字
- 默认值：无
- 描述：指定的区域右上角经度

rtLat：

- 类型：数字
- 默认值：无
- 描述：指定的区域右上角纬度

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status:                 //是否查找成功
    totalNum:               //本次搜索的总结果数
    currNum:                 //当前页的结果数
    totalPage:              //本次搜索的总页数
    pageIndex:              //当前页的索引
    resultArray:            //返回搜索结果列表，是一个数组
                           内部字段：
                           [{
									lon:                //当前内容的经度
									lat:                //当前内容的纬度
									name:               //名称
									uid:                //id
									add:                //地址
									city:               //所在城市
									phone:              //电话号码
									postCode:           //邮编
									poiType:            //POI类型，0:普通点 1:公交站 2:公交线路 3:地铁站 4:地铁线路
								}]
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
	msg: 	//返回报错信息
}
```

##示例代码

```js
var baiduMap = api.require('baiduMap');

baiduMap.searchInBounds({
    key: '图书馆', // 要搜索的关键字.
    lbLon: 112.47723797622677, // 左下角经度.
    lbLat: 34.556480000000015, // 左下角纬度.
    rtLon: 109.77539000000002, // 右上角经度.
    rtLat: 33.43144 // 右上角纬度.
}, function(ret, err){		
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##补充说明

在指定方形区域内搜索单个兴趣点

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**getLocationFromName**<div id="31"></div>

根据地址查找经纬度

getLocationFromName({params}, callback(ret, err))

##params

city：

- 类型：字符串
- 默认值：无
- 描述：所要搜索的地址所在的城市

address：

- 类型：字符串
- 默认值：无
- 描述：所要获得的经纬度的地址信息

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status:         //是否查找成功
	lon:            //返回经度
	lat:            //返回纬度
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
	msg: 	//返回报错信息
}
```

##示例代码

```js
var baiduMap = api.require('baiduMap');
baiduMap.getLocationFromName({
	city:'北京',
	address:'泰翔商务楼'
}, function(ret, err){		
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##补充说明

根据地址信息查找经纬度

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**getNameFromLocation**<div id="32"></div>

根据经纬度查找地址信息

getNameFromLocation({params}, callback(ret, err))

##params

lon：

- 类型：数字
- 默认值：无
- 描述：经度

lat：

- 类型：数字
- 默认值：无
- 描述：纬度

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status:                 //是否查找成功
	lon:                    //返回经度
	lat:                    //返回纬度
	add                     //地址
	province:               //所在省份
	city:                   //所在城市
	district:               //所在县区
	streetName:             //街道名
	streetNumber:           //街道号
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
	msg: 	//返回报错信息
}
```

##示例代码

```js
var baiduMap = api.require('baiduMap');
baiduMap.getNameFromLocation({
	lon:116.384767,
	lat:39.989539
}, function(ret, err){		
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##补充说明

根据经纬度查找地址信息

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**getBusRouteFromLineNum**<div id="33"></div>

根据公交线路号查询详情并在地图上显示

getBusRouteFromLineNum({params}, callback(ret, err))

##params

city：

- 类型：字符串
- 默认值：无
- 描述：公交所在城市

line：

- 类型：字符串
- 默认值：无
- 描述：公交编号

callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status:                 //是否查找成功
	busName:                //公交名字
	company:                //公交公司
	startTime:              //最早发车时间
	endTime:                //最晚班车时间
	stepInfo:               //是一个数组包含了站点信息
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
	msg: 	//返回报错信息
}
```
##示例代码

```js
var baiduMap = api.require('baiduMap');
baiduMap.getBusRouteFromLineNum({
	city:'北京',
	line:'345'
}, function(ret, err){		
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##补充说明

根据公交线路号查公交详情

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**removeBusRoute**<div id="34"></div>

移除地图上查询的公交线路

removeBusRoute()

##示例代码

```js
var baiduMap = api.require('baiduMap');
baiduMap.removeBusRoute();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**longPressGesture**<div id="35"></div>

在地图上添加长按手势，返回该点经纬度

longPressGesture({params}, callBack(ret, err))

##params

add:

- 类型：布尔
- 默认值：true
- 描述：（可选项）是否添加长按手势，若false则移除之前添加的长按手势

##callBack(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    lon:             //长按的地点的经度
    lat:              //长按的地点的纬度
}
```

##示例代码

```js
var baiduMap = api.require('baiduMap');
baiduMap.longPressGesture(function( ret, err ){		
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

#**setMapListener**<div id="b3"></div>

在地图上添加视角改变监听，返回当前地图中心坐标，视角倾斜度，地图旋转角度，地图缩放度

setMapListener({params}, callBack(ret, err))

##params

add:

- 类型：布尔
- 默认值：true
- 描述：（可选项）是否添加监听，若false则移除之前添加的监听

##callBack(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
        lon:              //当前地图中心的经度
        lat:              //当前地图中心的纬度
		zoom：			    //地图缩放角度
		rotate：			//地图旋转角度
		overlook：		    //视角倾斜度
}
```

##示例代码

```js
var baiduMap = api.require('baiduMap');
baiduMap.setMapListener(function( ret, err ){		
    if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统
可提供的1.0.2及更高版本

#**setMapTapListener**<div id="b4"></div>

在地图上添加单击监听

setMapTapListener({params}, callBack(ret, err))

##params

add:

- 类型：布尔
- 默认值：true
- 描述：（可选项）是否添加监听，若false则移除之前添加的监听

##callBack(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
   eventType:      //点击事件类型，取值范围：single--单击、double--双击  
   lon:            //点击点的经度
   lat:            //点击点的纬度
   zoom:           //地图缩放角度
   rotate:         //地图旋转角度
   overlook:       //视角倾斜度
}
```

##示例代码

```js
var baiduMap = api.require("baiduMap");
baiduMap.setMapTapListener(function( ret, err ){		
    if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统
可提供的1.0.2及更高版本

</div>


<div id="const-content">

<div class="outline">
[地图类型](#a1)

[跟踪类型](#a2)

[精度](#a3)

[路线策略](#a4)
</div>

#**地图类型**<div id="a1"></div>

设置地图的类型，字符串类型

##取值范围：

- standard         //标准地图
- trafficOn        //打开实时路况，**ios 暂不支持**
- trafAndsate      //实时路况和卫星地图，**ios 暂不支持**
- satellite        //卫星地图

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**跟踪类型**<div id="a2"></div>

设置当前位置的类型,字符串类型

##取值范围：

- none             //标准模式
- follow           //跟踪模式
- compass          //罗盘模式

注:Android系统如果为follow和compass模式,此时往地图中添加图层(大头针,布告牌等…)地图会自动移到定位信息那里。模式为none没有这种情况

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**精度**<div id="a3"></div>

定位精度，定位时只返回精度范围内的坐标。字符串类型

##取值范围：

- 10m
- 100m
- 1km
- 3km

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**路线策略**<div id="a4"></div>

设置添加路线的策略。字符串类型

##取值范围：

- ecar_fee_first		    //驾乘检索策略常量：较少费用
- ecar_dis_first		    //驾乘检索策略常量：最短距离
- ecar_time_first		//驾乘检索策略常量：时间优先
- ecar_avoid_jam		    //驾车策略： 躲避拥堵
- ebus_no_subway		    //公交检索策略常量：不含地铁
- ebus_time_first		//公交检索策略常量：时间优先
- ebus_transfer_first	//公交检索策略常量：最少换乘
- ebus_walk_first		//公交检索策略常量：最少步行距离


##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本