/*
Title: button
Description: button
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[setTitle](#2)

[setFrame](#3)

[close](#4)

[hide](#5)

[show](#6)
</div>

#**概述**

button是一个按钮模块，用原生代码实现了一个可自定义的按钮，开发者使用此模块可以实现在一个模块视图上添加自定义按钮的功能。本模块已停止更新，建议使用优化升级版模块 [UIButton](http://docs.apicloud.com/端API/界面布局/UIButton)


#**open**<div id="1"></div>

打开一个按钮视图

open({params}, callback(ret, err))

##params

x ：

- 类型：数字
- 默认值：100
- 描述：视图左上角点坐标，可为空

y ：

- 类型：数字
- 默认值：100
- 描述：视图左上角点坐标，可为空

w ：

- 类型：数字
- 默认值：60
- 描述：视图的宽，可为空

h ：

- 类型：数字
- 默认值：40
- 描述：视图的高，可为空

corner：

- 类型：数字
- 默认值：0
- 描述：按钮视图顶角圆角大小，可为空

fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window

fixed:
- 类型：布尔
- 默认值：true
- 描述：是否将模块视图固定到窗口上，不跟随窗口上下滚动，可为空

bg:
- 类型：JSON 对象
- 默认值：见内部字段
- 描述：按钮视图背景设置，可为空
- 内部字段：

```js
{
        normal:      //按钮常态下的背景，支持 rgb，rgba，#，img，可为空
        highlight:    //按钮高亮下的背景，支持 rgb，rgba，#，img，可为空，为空则和normal效果一致

}
```

title:
- 类型：
- 默认值：见内部字段
- 描述：按钮标题设置，可为空
- 内部字段：

```js
{
      size:            //标题字体大小，数字类型，默认13，可为空 
      normalTitle:      //按钮常态下的标题，字符串，可为空
      highlightTitle:     //按钮高亮下的标题，字符串，可为空
      normalColor:     //标题常态颜色，支持 rgb，rgba，#，默认#ffffff，可为空
      highlightColor:    //标题按下颜色，支持 rgb，rgba，#，默认#ffffff，可为空
      alignment:       //标题位置，取值范围：left，right，center，默认center，可为空

}
```

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：
  
```js
{
     eventType:      //字符串类型；回调事件类型；取值范围如下：
                     //show：打开成功并显示在UI上
                     //click：用户点击事件
     id:             //数字类型；打开模块的id
}
```

##示例代码
```js
var button = api.require('button');
button.open({
    bg: {
        normal: "#ff0000"
    },
    fixedOn: api.frameName
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

#**setTitle**<div id="2"></div>

重设按钮标题

setTitle({params})

##params

id ：

- 类型：数字
- 默认值：无
- 描述：操作的视图的id，不可为空

title:
- 类型：
- 默认值：见内部字段
- 描述：按钮标题设置，可为空,为空则保持原值不变
- 内部字段：

```js
{
      size:            //标题字体大小，数字类型，默认13，可为空 
      normalTitle:      //按钮常态下的标题，字符串，可为空
      highlightTitle:     //按钮高亮下的标题，字符串，可为空
      normalColor:     //标题常态颜色，支持 rgb，rgba，#，默认#ffffff，可为空
      highlightColor:    //标题按下颜色，支持 rgb，rgba，#，默认#ffffff，可为空
      alignment:       //标题位置，取值范围：left，right，center，默认center，可为空

}
```

##示例代码
```js
var button = api.require('button');
button.setTitle({
   id: 1,
   title:{
       normalTitle: "按钮"
    }
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

#**setFrame**<div id="3"></div>

重设模块视图的位置大小

setFrame({params})

##params

id ：

- 类型：数字
- 默认值：无
- 描述：操作的视图的id，不可为空

x ：

- 类型：数字
- 默认值：无
- 描述：视图左上角点坐标，可为空，若为空则模块视图此参数保持原值

y ：

- 类型：数字
- 默认值：无
- 描述：视图左上角点坐标，可为空，若为空则模块视图此参数保持原值

w ：

- 类型：数字
- 默认值：当前设备屏幕的宽
- 描述：视图的宽，可为空，若为空则模块视图此参数保持原值

h ：

- 类型：数字
- 默认值：w-20
- 描述：视图的高，可为空，若为空则模块视图此参数保持原值

anim ：

- 类型：布尔
- 默认值：false
- 描述：改变模块视图大小时是否添加变化过程的动画，可为空.android暂不支持此参数

##示例代码
```js
var button = api.require('button');
button.setFrame({
    x: 80,
    w: 45
});
```
##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**close**<div id="4"></div>

关闭按钮视图

close({params})

##params

id ：

- 类型：数字
- 默认值：无
- 描述：操作视图的id，可为空，为空时关闭所有的模块视图

##示例代码
```js
var button = api.require('button');
button.close({
    id: 1
});
```
##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**hide**<div id="5"></div>

隐藏按钮视图

hide({params})

##params

id ：

- 类型：数字
- 默认值：无
- 描述：操作视图的id，不可为空

##示例代码
```js
var button = api.require('button');
button.hide({
    id: 1
});
```
##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**show**<div id="6"></div>

显示按钮视图

show({params})

##params

id ：

- 类型：数字
- 默认值：无
- 描述：操作视图的id，不可为空

##示例代码
```js
var button = api.require('button');
button.show({
    id: 1
});
```
##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本