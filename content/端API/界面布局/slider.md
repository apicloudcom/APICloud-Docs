/*
Title: slider
Description: slider
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[setValue](#2)

[lock](#3)

[close](#4)

[show](#5)

[hide](#6)
</div>

#**概述**

slider封装了一个滑动器，开发者可自定义最大值、最小值、当前值以及拖动滑块时的气泡提示信息等各种滑动器用到的功能。原生代码比前端实现更加流畅稳定。本模块已停止更新，建议使用 [UISlider](http://docs.apicloud.com/端API/界面布局/UISlider)

![图片说明](/img/docImage/slider.jpg)

#**open**<div id="1"></div>

打开slider

open({params}, callback(ret, err))

##params

multiOpen：

- 类型：布尔
- 默认值：false
- 描述：（可选项）同一个页面是否可以同时打开多个滑动器

showBubble：

- 类型：布尔
- 默认值：true
- 描述：（可选项）是否显示提示气泡

alwaysShowBubble：

- 类型：布尔
- 默认值：true
- 描述：（可选项）是否一直显示提示气泡，若为false则只有点击拖动时才显示气泡

x：

- 类型：数字
- 默认值：30
- 描述：（可选项）slider左边点的坐标，**在 Android 平台上需适当预留出滑块空隙**

y：

- 类型：数字
- 默认值：104
- 描述：（可选项）slider左边点的坐标，**在 Android 平台上需适当预留出滑块空隙**

w：

- 类型：数字
- 默认值：260
- 描述：（可选项）slider的宽，**在 Android 平台上需适当预留出滑块空隙**

h：

- 类型：数字
- 默认值：5
- 描述：（可选项）slider的高，**在 Android 平台上需适当预留出滑块空隙**

bgImg：

- 类型：字符串
- 默认值：无
- 描述：slider的背景图片

selectedBgImg：

- 类型：字符串
- 默认值：无
- 描述：slider滑块左边划过的区域图片

bar：

- 类型：json对象
- 默认值：见内部字段
- 描述：（可选项）气泡设置
- 备注：若不传则不显示滑块
- 内部字段：

```js
{
	barWidth：  //（可选项）滑块宽，数字，默认30
	barHeight： //（可选项）滑块的高，数字，默认18
	barImg：    //（可选项）滑块背景，字符串，默认#4f94dc，支持rgb，rgba，#，img
}
```

bubble：

- 类型：json对象
- 默认值：无
- 描述：（可选项）气泡设置
- 内部字段：

```js
{
	bubbleWidth：  //（可选项）数字类型，默认60，气泡的宽
	bubbleHeight： //（可选项）数字类型，默认40，气泡的高
	bubbleImg：    //（可选项）字符串，默认#5cacee，气泡背景，支持rgb,rgba,#,img
	titleSuffix：  //（可选项）字符串，默认℃，气泡后缀
	titleColor：   //（可选项）字符串，默认#000000，支持rgb，rgba，#
	titleSize：    //（可选项）数字类型，默认13.0，气泡上字体大小
	titlePosition：//（可选项）字符串类型，气泡标题位置，取值范围：left、right、center，默认center
}
```

minValue：

- 类型：数字
- 默认值：0
- 描述：（可选项）slider最小值

maxValue：

- 类型：数字
- 默认值：100
- 描述：（可选项）slider最大值

defValue：

- 类型：数字
- 默认值：0
- 描述：（可选项）slider开启默认值

fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window

step：

- 类型：数字
- 默认值：0.00001
- 描述：（可选项）滑块滑动最小单位

fixed:
- 类型：布尔
- 默认值：true
- 描述：（可选项）是否将模块视图固定到窗口上，不跟随窗口上下滚动

##callback(ret, err)

ret：

- 类型：JSON对象内部字段：

```js
{
	id:                  //滑动器的id
	touchCancel:         //是否是滑动结束事件
	value:               //滑动时返回滑动的值
}
```

##示例代码

```js
var slider = api.require('slider');
slider.open({
     x: 30,
     y: api.frameHeight - 60,
     width: api.frameWidth - 60,
     height: 6,
     bgImg: "widget://res/img/slider_bg.png",
     selectedBgImg: "widget://res/img/slider_selected.png",
     barW: 30,
     barH: 20,
     barImg: "widget://res/img/slider_bar.png",
     bubbleW: 60,
     bubbleH: 40,
     bubbleImg: "widget://res/img/slider_bubble.png",
     minValue: 0,
     maxValue: 100,
     defValue: 30,
     fixedOn: api.frameName
},function( ret, err ){
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


#**setValue**<div id="2"></div>

设置slider的值

setValue({params})

##params

id：

- 类型：数字
- 默认值：打开的第一个菜单的id
- 描述：（可选项）菜单id
- 备注：若open接口内multiOpen不传或传false，则本参数被忽略

value:

- 类型：数字
- 默认值：无
- 描述：要设置的滑块的值（在最大值和最小值直接的一个值）

minValue：

- 类型：数字
- 默认值：旧值
- 描述：（可选项）slider最小值

maxValue：

- 类型：数字
- 默认值：旧值
- 描述：（可选项）slider最大值

step：

- 类型：数字
- 默认值：0.00001
- 描述：（可选项）滑块滑动最小单位

##示例代码

```js
var slider = api.require('slider');
slider.setValue({
    id:1,
    value:51
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**lock**<div id="3"></div>

锁定slider的值

lock({params})

##params

id：

- 类型：数字
- 默认值：无
- 描述：操作菜单id
- 备注：若open接口内multiOpen不传或传false，则本参数被忽略

lock:

- 类型：布尔
- 默认值：true
- 描述：（可选项）是否锁定当前slider的值

##示例代码

```js
var slider = api.require('slider');
slider.lock({
	id:1,
	lock:true
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



##**close**<div id="4"></div>

关闭slider

close()

##params

id：

- 类型：数字
- 默认值：无
- 描述：（可选项）操作菜单id
- 备注：若open接口内multiOpen不传或传false，则本参数被忽略

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
   status:      //操作状态值，布尔值
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
	msg:      //错误信息，字符串
}
```

##示例代码

```js
var slider = api.require('slider');
slider.close({
   id:1
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**show**<div id="5"></div>

显示滑动器

show(callBack(ret,err))

##params

id：

- 类型：数字
- 默认值：无
- 描述：操作菜单id
- 备注：若open接口内multiOpen不传或传false，则本参数被忽略


##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	status:true           //操作成功状态值，布尔值
}
```

err：

- 类型：JSON对象
- 内部字段：

```
{
	msg:“”	//错误描述，字符串
}
```

##示例代码

```js
var slider= api.require('slider');
slider.show({
  id:1
});
```

##补充说明
无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**hide**<div id="6"></div>

隐藏滑动器

hide(callBack(ret,err))

##params

id：

- 类型：数字
- 默认值：无
- 描述：菜单id
- 备注：若open接口内multiOpen不传或传false，则本参数被忽略


##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```
{
	status:true           //操作成功状态值，布尔值
}
```

err：


- 类型：JSON对象
- 内部字段：

```js
{
	msg:“”	//错误描述，字符串
}
```

##示例代码

```js
var slider = api.require('slider');
slider.hide({
  id:1
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

