/*
Title: UIButton
Description: UIButton
*/
<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">
<div class="outline">
[open](#1)

[setTitle](#2)

[getRect](#3)

[setRect](#4)

[getState](#5)

[setState](#6)

[close](#7)

[hide](#8)

[show](#9)
</div>

#**概述**

UIButton 是 button 模块的优化升级版，用原生代码实现了一个可自定义的按钮，开发者使用此模块可以实现在一个模块视图上添加自定义按钮的功能，本模块支持手指拖动改变按钮位置功能。


#**open**<div id="1"></div>

打开一个按钮模块

open({params}, callback(ret, err))

##params

rect：

- 类型：JSON对象
- 描述：（可选项）模块的位置及尺寸
- 内部字段：

```js
{
    x: 0,   //（可选项）数字类型；模块左上角的 x 坐标（相对于所属的 Window 或 Frame）；默认值：0
    y: 0,   //（可选项）数字类型；模块左上角的 y 坐标（相对于所属的 Window 或 Frame）；默认值：0
    w: 80,  //（可选项）数字类型；模块的宽度；默认值：80
    h: 50   //（可选项）数字类型；模块的高度；默认值：50
}
```

corner：

- 类型：数字
- 描述：（可选项）按钮视图顶角圆角大小
- 默认值：0

bg:

- 类型：JSON对象
- 描述：（可选项）按钮视图背景设置
- 默认值：见内部字段
- 内部字段：

```js
{
        normal: '',    //（可选项）字符串类型；按钮常态下的背景，支持rgb、rgba、#、img；默认：'#000'
        highlight: '', //（可选项）字符串类型；按钮高亮下的背景，支持rgb、rgba、#、img；默认：normal 
        active: ''     //（可选项）字符串类型；按钮选中后的背景，支持rgb、rgba、#、img；默认：normal 
}
```

title:

- 类型：
- 描述：（可选项）按钮标题设置
- 默认值：见内部字段
- 内部字段：

```js
{
      size: 13,         //（可选项）数字类型；标题字体大小；默认：13
      normal: '',       //（可选项）字符串类型；按钮常态下的标题
      highlight: '',    //（可选项）字符串类型；按钮高亮下的标题；默认：normal
      active: '',       //（可选项）字符串类型；按钮选中后的标题；默认：normal
      normalColor: '',  //（可选项）字符串类型；标题常态颜色，支持rgb、rgba、#；默认：#fff
      highlightColor:'',//（可选项）字符串类型；标题按下颜色，支持rgb、rgba、#；默认：normalColor
      activeColor:'',   //（可选项）字符串类型；标题点击后颜色，支持rgb、rgba、#；默认：normalColor
      alignment: ''     //（可选项）字符串类型；标题位置，取值范围：left、right、center；默认：center
}
```

fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window

fixed:
- 类型：布尔
- 描述：（可选项）是否将模块视图固定到窗口上（不跟随窗口上下滚动）
- 默认值：true


move:
- 类型：布尔
- 描述：（可选项）是否为可拖动的按钮，仅当 fixedOn 为空且 fixed 为 false 时有效
- 默认值：false


##callBack(ret,err)

ret：

- 类型：JOSN 对象
- 内部字段：
  
```js
{
     eventType:      //字符串类型；回调事件类型；取值范围如下：
                     //show：打开成功并显示在UI上
                     //click：用户点击事件
                     //moveBegin：开始移动
                     //moving：移动中
                     //moveEnd：移动结束
     id:             //数字类型；打开按钮模块的 id
}
```

##示例代码

```js
var button = api.require('UIButton');
button.open({
    rect:{
       x: 100,
       y: 100,
       w: 80,
       h: 50
    },
    corner: 5,
    bg: {
        normal: "#000000",
        highlight: '#ff0000',
        active: '#adf000'
    },
    title:{
        size: 14,
        highlight: '高亮状态标题',
        active: '选中后标题',
        normal: "常态标题",
        highlightColor: '#000000',
        activeColor: '#000adf',
        normalColor: "#ff0000",
        alignment: 'center'
    },
    fixedOn: api.frameName,
    fixed: true,
    move: true
},function( ret ){		
    if( ret.eventType != 'moving' ){
        alert( JSON.stringify( ret ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setTitle**<div id="2"></div>

重设指定按钮的标题

setTitle({params})

##params

id ：

- 类型：数字
- 描述：所操作按钮模块的id

title:

- 类型：
- 描述：（可选项）按钮标题设置
- 默认值：见内部字段
- 内部字段：

```js
{
      size: 13,         //（可选项）数字类型；标题字体大小；默认：13
      normal: '',       //（可选项）字符串类型；按钮常态下的标题
      highlight: '',    //（可选项）字符串类型；按钮高亮下的标题；默认：normal
      active: '',       //（可选项）字符串类型；按钮选中后的标题；默认：normal
      normalColor: '',  //（可选项）字符串类型；标题常态颜色，支持rgb、rgba、#；默认：#fff
      highlightColor:'',//（可选项）字符串类型；标题按下颜色，支持rgb、rgba、#；默认：normalColor
      activeColor:'',   //（可选项）字符串类型；标题点击后颜色，支持rgb、rgba、#；默认：normalColor
      alignment: ''     //（可选项）字符串类型；标题位置，取值范围：left、right、center；默认：center
}
```

##示例代码
```js
var button = api.require('UIButton');
button.setTitle({
    id: 1,
    title:{
        size: 14,
        highlight: '高亮状态标题',
        active: '选中后标题',
        normal: "常态标题",
        highlightColor: '#oo0000',
        activeColor: '#adf000',
        normalColor: "#ff0000",
        alignment: 'center'
    }
},function( ret ){		
    if( ret ){
        alert( JSON.stringify( ret ) );
    }
});
```
##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**getRect**<div id="3"></div>

获取指定按钮模块的位置及大小

getRect(params, callback(ret))

##params

id ：

- 类型：数字
- 描述：操作按钮模块的id

##callBack(ret)

ret：

- 类型：JOSN 对象
- 内部字段：
  
```js
{
    x: 0,   //数字类型；模块左上角的 x 坐标（相对于所属的 Window 或 Frame）
    y: 0,   //数字类型；模块左上角的 y 坐标（相对于所属的 Window 或 Frame）
    w: 80,  //数字类型；模块的宽度
    h: 50   //数字类型；模块的高度
}
```

##示例代码
```js
var button = api.require('UIButton');
button.getRect({
    id: 1
},function( ret ){		
    if( ret ){
        alert( JSON.stringify( ret ) );
    }
});

```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setRect**<div id="4"></div>

重设指定按钮模块的位置及大小

setRect({params})

##params

id ：

- 类型：数字
- 描述：操作按钮模块的id

rect：

- 类型：JSON对象
- 描述：（可选项）模块的位置及尺寸
- 内部字段：

```js
{
    x: 0,   //（可选项）数字类型；模块左上角的 x 坐标（相对于所属的 Window 或 Frame）；默认值：按钮模块原 x 值
    y: 0,   //（可选项）数字类型；模块左上角的 y 坐标（相对于所属的 Window 或 Frame）；默认值：按钮模块原 y 值
    w: 80,  //（可选项）数字类型；模块的宽度；默认值：按钮模块原 w 值
    h: 50   //（可选项）数字类型；模块的高度；默认值：按钮模块原 h 值
}
```

anim ：

- 类型：布尔
- 描述：改变模块视图大小时是否添加变化过程的动画， android 暂不支持此参数
- 默认值：false

##示例代码
```js
var button = api.require('UIButton');
button.setRect({
    id:1,
    rect: {
	    x: 80,
	    y: 100,
	    h: 60,
	    w: 90
    },
    anim: true
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**getState**<div id="5"></div>

获取指定按钮模块的状态

getState(params, callback(ret))

##params

id ：

- 类型：数字
- 描述：操作按钮模块的id

##callBack(ret)

ret：

- 类型：JOSN 对象
- 内部字段：
  
```js
{
    state: 'active'   //字符串类型；按钮的状态，取值范围：normal、active
}
```

##示例代码
```js
var button = api.require('UIButton');
button.getState({
    id: 1
},function( ret ){		
    if( ret ){
        alert( JSON.stringify( ret ) );
    }
});

```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setState**<div id="6"></div>

设置指定按钮的状态

setState({params})

##params

id ：

- 类型：数字
- 描述：操作按钮模块的id

state：

- 类型：字符串
- 描述：（可选项）按钮的状态
- 默认：active
- 取值范围：
	- normal：常态
	- active：选中状态

##示例代码
```js
var button = api.require('UIButton');
button.setState({
    id: 1,
    state: 'active'
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**close**<div id="7"></div>

关闭指定按钮模块

close(params)

##params

id ：

- 类型：数字
- 描述：操作按钮模块的 id

##示例代码
```js
var button = api.require('UIButton');
button.close({
    id: 1
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**hide**<div id="8"></div>

隐藏指定按钮模块

hide(params)

##params

id ：

- 类型：数字
- 描述：操作按钮模块的 id

##示例代码
```js
var button = api.require('UIButton');
button.hide({
    id: 1
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**show**<div id="9"></div>

显示指定按钮模块

show(params)

##params

id ：

- 类型：数字
- 描述：操作按钮模块的 id

##示例代码
```js
var button = api.require('UIButton');
button.show({
    id: 1
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本