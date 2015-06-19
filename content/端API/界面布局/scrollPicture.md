/*
Title: scrollPicture
Description: scrollPicture
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[close](#2)

[turnPage](#3)

[refresh](#4)

[hide](#5)

[show](#6)
</div>

#**概述**

scrollPicture是一个图片自动滚动联播器，开发者自需传入一组图片地址，即可实现图片滚动联播的效果。图片地址支持网络路径，网络图片会被缓存到本地

![图片说明](/img/docImage/scrollPicture.jpg)

#**open**<div id="1"></div>

打开图片滚动界面

open({params}, callback(ret, err))

##params

x：

- 类型：数字
- 默认值：0
- 描述：（可选项）视图左上角点坐标

y：

- 类型：数字
- 默认值：导航条下边缘位置
- 描述：（可选项）图左上角点坐标

<del>width:

- <del>类型：数字
- <del>默认值：当前设备屏幕宽 
- <del>描述：视图的宽，可为空

<del>height：
- <del>类型：数字
- <del>默认值：视图的宽减120
- <del>描述：视图的高，可为空

w：

- 类型：数字
- 默认值：当前设备屏幕宽
- 描述：（可选项）视图的宽

h：

- 类型：数字
- 默认值：视图的宽减120
- 描述：（可选项）视图的高

intervalTime：

- 类型：数字
- 默认值：3
- 描述：（可选项）图片变换间隔，单位是s

paths：

- 类型：数组
- 默认值：无
- 描述：图片路径组成的数组，支持http，https，widget，fs各种协议

<del>placeHoldImg：

- <del>类型：字符串
- <del>默认值：无
- <del>描述：当加载网络图片时，屏幕上显示的占位图片，不可为空，paths都是本地路径，该参数可为空

placeholderImg：

- 类型：字符串
- 默认值：无
- 描述：（可选项）当加载网络图片时，屏幕上显示的占位图片
- 备注：若paths都是本地路径，该参数可不传，否则为必传

<del>subtitle：

- <del>类型：json对象
- <del>默认值：无
- <del>描述：图片的说明文字，可为空，若为空则不显示说明文字

subTitle：

- 类型：json对象
- 默认值：无
- 描述：（可选项）图片的说明文字
- 备注：若不传则不显示说明文字
- 内部字段：

```js
{
	height：     //（可选项）数字类型，说明文字的视图的高，默认35.0
	titles：     //数组类型，说明的文字组成的数组，与paths一一对应
	color：      //（可选项）字符串类型，说明文字的颜色，默认#E0FFFF
	size：       //（可选项）数字类型，说明文字的字体大小，默认13.0
	bgColor：    //（可选项）说明文字视图的背景颜色，支持rgb、rgba、#，默认#696969
	fixed：      //（可选项）布尔值，是否将标题视图固定到主视图内部，默认false 
}
```

control：

- 类型：json对象
- 默认值：无
- 描述：（可选项）页面控制器
- 备注：若不传则不显示页面控制器
- 内部字段：

```js
{
	position:             //(deprecated)页面控制器位置，0-中间；1-左边；2-右边，默认0
	alignment:            //(可选项)页面控制器位置，center(居中),left(靠左), right(靠右),默认center
	activeColor:          //(可选项)当前圆点颜色，支持rgb、rgba、#，默认:DA70D6
	inactiveColor:        //(可选项)圆点颜色 ，支持rgb、rgba、#，默认：#FFFFFF
}
```

fixedOn：

- 类型：字符串
- 默认值：当前主窗口的名字
- 描述：（可选项）将模块视图添加到指定窗口的名字

adaptive：

- 类型：布尔
- 默认值：false
- 描述：（可选项）是否使图片大小自适应传入的宽高值

fixed:
- 类型：布尔
- 默认值：true
- 描述：（可选项）是否将模块视图固定到窗口上，不跟随窗口上下滚动

circulation:
- 类型：布尔
- 默认值：true
- 描述：（可选项）图片是否循环播放

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	status:   		//是否是click图片的事件
	index：			//图片滚动的下标
	click：			//点击图片的下标
}
```

##示例代码

```js
var obj = api.require('scrollPicture');
 var arrayPath = new Array();
 arrayPath[0] = 'widget://res/scrollPicture_01.jpg';
 arrayPath[1] = 'widget://res/scrollPicture_02.jpg';
 arrayPath[2] =  'http://f.hiphotos.baidu.com/image/pic/item/4e4a20a4462309f7bdca9423710e0cf3d7cad65d.jpg';
 arrayPath[3] = 'widget://res/scrollPicture_04.jpg';
 arrayPath[4] = 'widget://res/scrollPicture_05.jpg';
 var arrayTitle = new Array();
 arrayTitle[0] = 'widget://res/scrollPicture_01.jpg';
 arrayTitle[1] = 'widget://res/scrollPicture_02.jpg';
 arrayTitle[2] = 'http://f.hiphotos.baidu.com/image/pic/item/4e4a20a4462309f7bdca9423710e0cf3d7cad65d.jpg';
 arrayTitle[3] = 'widget://res/scrollPicture_04.jpg';
 arrayTitle[4] = 'widget://res/scrollPicture_05.jpg';
    
 obj.open({
     placeholderImg:'widget://res/scrollPicture_placeholder.png',
     paths: arrayPath,
     subtitle:{
         titles:arrayTitle
     },
     control:{
         position:0
     }
 },function(ret,err){
     if(ret.status){
        ret.click;
     }else{
        ret.index;
     }
 });
```

##补充说明

打开视图

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**close**<div id="2"></div>

关闭页面

close(callBack(ret,err))

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	status:true		//操作是否成功
}
```

##示例代码

    var obj = api.require('scrollPicture');
    obj.close();

##补充说明

关闭视图

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**turnPage**<div id="3"></div>

转到指定页面

turnPage(params)

##params

index：

- 类型：数字
- 默认值：0
- 描述：（可选项）指定跳转到某一页的索引值

##示例代码

```js
var scrollPicture = api.require('scrollPicture');

scrollPicture.turnPage({
	index:0
});
```

##补充说明

跳转到指定图片.

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

#**refresh**<div id="4"></div>

刷新页面

refresh(params)

##params

paths：

- 类型：数组
- 默认值：旧值
- 描述：（可选项）图片路径组成的数组，支持网络和本地路径

titles：

- 类型：数组
- 默认值：旧值
- 描述：（可选项）说明的文字组成的数组

##示例代码

```js
var scrollPicture = api.require('scrollPicture');
scrollPicture.refresh();
```

##补充说明

刷新视图内图片

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

#**hide**<div id="5"></div>

隐藏模块视图

hide(callBack(ret,err))

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	status:true		//操作是否成功
}
```

##示例代码

	var obj = api.require('scrollPicture');
	obj.hide();

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

#**show**<div id="6"></div>

显示模块视图

show(callBack(ret,err))

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	status:true		//操作是否成功
}
```

##示例代码

	var obj = api.require('scrollPicture');
	obj.show();

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

</div>
<div id="const-content">

<div class="outline">
[控制器位置](#1)
</div>

#**控制器位置**<div id="1"></div>

页面控制器的位置。字符串类型

##取值范围：

- center   	中间
- left		 	靠左
- right		靠右

</div>