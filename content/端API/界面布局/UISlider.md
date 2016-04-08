/*
Title: UISlider
Description: UISlider
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

UISlider 封装了一个滑动器，开发者可自定义最大值、最小值、当前值以及拖动滑块时的气泡提示信息等各种滑动器用到的功能，支持同个页面打开多个模块。原生代码比前端实现更加流畅稳定。**该模块是 slider 模块的升级版**

![图片说明](/img/docImage/slider.jpg)

#**open**<div id="1"></div>

打开 UISlider

open({params}, callback(ret, err))

##params

orientation：

- 类型：字符串类型
- 描述：（可选项）滑动控件的朝向：vertical | horizontal
- 默认：horizontal

animation：

- 类型：布尔类型
- 描述：（可选项）当值发生改变时，如 click 事件，是否为滑块的移动显示动画
- 默认：true

rect：

- 类型：JSON 类型
- 描述：（可选项）模块的位置及尺寸
- 内部字段：

```js
{
    x: 0,                              //（可选项）数字类型；模块左上角的 x 坐标（相对于所属的 Window 或 Frame）；默认值：0
    y: 0,                              //（可选项）数字类型；模块左上角的 y 坐标（相对于所属的 Window 或 Frame）；默认值：0
    size: 300,                            //（可选项）数字类型；根据 orientation 的值决定模块的宽度或高度，orientation 为 vertical 时为高度，反之为宽度；默认值：所属的 Window 或 Frame 的宽度或高度
}
```

bubble：

- 类型：JSON 类型
- 描述：提示气泡设置
- 内部字段：

```js
{
    state: 'always',                  //（可选项）字符串类型；提示气泡显示状态；默认：highlight；取值范围如下：
                                      //always（一直显示）
                                      //highlight（当用户与滑动控件有交互时显示一段时间）
                                      //hide（不显示）
    direction: 'top',                  //（可选项）字符串类型；气泡弹出方向，取值范围：top（往上弹出）、bottom（往下弹出）；默认：top
    w: 80,                            //（可选项）数字类型；气泡宽度，若不传则自适应宽度；默认：自适应内容的宽度
    h: 30,                            //（可选项）数字类型；气泡高度；默认：30
    size: 14,                         //（可选项）数字类型；气泡内文字大小；默认：14
    color: '#888',                    //（可选项）字符串类型；气泡内文字颜色，支持 rgb，rgba，#；默认：#888
    bg: 'widget://res/slider/bubble.png', //（可选项）字符串类型；气泡的背景图片路径，要求本地路径（widget://、fs://）
    prefix: '温度：',                  //（可选项）字符串类型；气泡文字的前缀；默认：未设置时不显示前缀
    suffix: '摄氏度'                   //（可选项）字符串类型；气泡文字的后缀；默认：未设置时不显示后缀
}

```

handler

- 类型：JSON 类型
- 描述：滑块设置
- 内部字段：

```js
{
    w: 10,                             //（可选项）数字类型；滑块宽度；默认：10
    h:  8,                             //（可选项）数字类型；滑块高度；默认：bar.h + 4
    bg: 'widget://res/slider/handler.png', //字符串类型；滑块图片的路径，要求本地路径（widget://、fs://）
}

```

bar：

- 类型：JSON 类型
- 描述：滑动条设置
- 内部字段：

```js
{
    h: 4,                              //（可选项）数字类型；滑动条的高度；默认：4
    bg: 'widget://res/slider/background.png', //字符串类型；滑动条的背景，支持：rgb，rgba，#，img
    active: 'widget://res/slider/bar-active.png', //（可选项）字符串类型；滑动条滑块已选择区域背景，支持：rgb，rgba，#，img；默认：透明
}

```

value：

- 类型：JSON 类型
- 描述：滑动控件的值设置
- 内部字段：

```js
{
    min: 0,                            //数字类型；滑动控件的最小值
    max: 100,                          //数字类型；滑动控件的最大值
    step: 0.1,                         //数字类型；滑动时的步幅
    init: 50,                          //数字类型；初始值
}

```

fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window

fixed:

- 类型：布尔类型
- 描述：（可选项）是否将模块视图固定到窗口上，不跟随窗口上下滚动
- 默认：false

##callback(ret, err)

ret：

- 类型：JSON对象内部字段：

```js
{
	id: 1,                      //数字类型；滑动控件的唯一标识，由模块内部自动生成
	eventType: 'sliding' ,      //字符串类型；滑动控件值改变时触发；取值范围如下：
                                //show: 控件显示
	                            //sliding：滑动中
                                //end：滑动结束
                                //set：被 setValue 改变
                                //click：滑动条被点击
	value: 50                   //滑动控件的当前值，在 eventType 的所有事件中都会返回
}

```

##示例代码

```js
var uislider = api.require('UISlider');
uislider.open({
    animation: true,
    orientation: 'horizontal',
    rect: {
        x: 0,
        y: 0,
        size: 300
    },
    bubble: {
        direction: 'top',
        state: 'always',
        w: 80,
        h: 30,
        size: 14,
        color: '#888',
        bg: 'widget://res/slider/bubble.png',
        prefix: '温度：',
        suffix: '摄氏度'
    },
    handler: {
        w: 10,
        h: 8,
        bg: 'widget://res/slider/handler.png'
    },
    bar: {
        h: 4,
        bg: 'widget://res/slider/background.png',
        active: 'widget://res/slider/bar-active.png'
    },
    value: {
        min: 16,
        max: 32,
        step: 0.5,
        init: 26
    },
    fixedOn: api.frameName,
    fixed: false
}, function(ret, err) {
    if (ret) {
        alert(JSON.stringify(ret));
    } else {
        alert(JSON.stringify(err));
    }
});

```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**setValue**<div id="2"></div>

设置 UISlider 的值

setValue({params})

##params

id：

- 类型：数字类型
- 描述：指定滑动控件的唯一标识，当 open 成功后返回

value:

- 类型：JSON 类型
- 描述：要设置的值
- 内部字段：

```js
{
    min: 0,                            //（可选项）数字类型；滑动控件的最小值；默认：原值
    max: 100,                          //（可选项）数字类型；滑动控件的最大值；默认：原值
    step: 1,                           //（可选项）数字类型；滑动时的步幅；默认：原值
    value: 50                          //（可选项）数字类型；要设置的当前值；默认：原值
}

```

##示例代码

```js
var uislider = api.require('UISlider');
uislider.setValue({
    id: id,
    value: {
        min: 16,
        max: 32,
        step: 0.5,
        value: 23
    }
});

```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**lock**<div id="3"></div>

设置滑动控件是否锁定

lock({params})

##params

id：

- 类型：字符串类型
- 描述：指定滑动控件的唯一标识，当 open 成功后返回

lock:

- 类型：布尔类型
- 描述：（可选项）是否锁定指定模块
- 默认：true（锁定）

##示例代码

```js
var uislider = api.require('UISlider');
uislider.lock({
	id: id,
	lock: true
});

```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

##**close**<div id="4"></div>

关闭滑动控件

close()

##params

id：

- 类型：字符串类型
- 描述：指定滑动控件的唯一标识，当 open 成功后返回

##示例代码

```js
var uislider = api.require('UISlider');
uislider.close({
   id: id
});

```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**show**<div id="5"></div>

显示滑动器

show(callBack(ret,err))

##params

id：

- 类型：字符串类型
- 描述：指定滑动控件的唯一标识，当 open 成功后返回

##示例代码

```js
var uislider= api.require('UISlider');
uislider.show({
  id: id
});

```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**hide**<div id="6"></div>

隐藏滑动器

hide(callBack(ret,err))

##params

id：

- 类型：字符串类型
- 描述：指定滑动控件的唯一标识，当 open 成功后返回

##示例代码

```js
var uislider = api.require('UISlider');
uislider.hide({
  id: id
});

```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本