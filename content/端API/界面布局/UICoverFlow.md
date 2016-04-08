/*
Title: UICoverFlow
Description: UICoverFlow
*/

<ul id="tab" class="clearfix">
    <li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[setIndex](#5)

[close](#2)

[hide](#3)

[show](#4)

[clearCache](#6)
</div>

#**概述**

UICoverFlow 底层封装了 openGL 实现的 3D 图片流效果。开发者可自定义图片大小及其数量。只需一个 open 接口就能打开一个超炫酷效果的导航菜单。**UICoverFlow 模块是 coverFlow 模块的升级版**

![图片说明](/img/docImage/coverFlow.jpg)

#**open**<div id="1"></div>

打开 UICoverFlow

open({params}, callback(ret, err))

##params

rect：

- 类型：JSON 类型
- 描述：（可选项）模块的位置及尺寸
- 内部字段：

```js
{
    x: 0,                              //（可选项）数字类型；模块左上角的 x 坐标（相对于所属的 Window 或 Frame）；默认值：0
    y: 0,                              //（可选项）数字类型；模块左上角的 y 坐标（相对于所属的 Window 或 Frame）；默认值：0
    w: api.winWidth,                   //（可选项）数字类型；模块的宽度；默认值：所属的 Window 或 Frame 的宽度
    h: 480                             //（可选项）数字类型；模块的高度；默认值：所属的 Window 或 Frame 的高度
}
```

styles：

- 类型：JSON 类型
- 描述：图片流的整体样式设置
- 内部字段：

```js
{
    bg: '#fff',                        //（可选项）字符串类型；图片流的背景，支持 rgb，rgba，#，img；默认：#fff
    image:{     
        activeW: 300,                  //（可选项）数字类型；当前图片的显示宽度；默认：w*2.0/3.0
        activeH: 400,                  //（可选项）数字类型；当前图片的显示高度；默认：h
        corner: 2,                     //（可选项）数字类型；图片圆角半径；默认：2
        placeholder: 'widget://placeholder.png', //（可选项）字符串类型；占位图片的路径，要求本地路径（fs://、widget://），若不传则不显示占位图
    },
    indicator:{                        //（可选项）JSON 类型；指示器的样式设置；默认：未设置时不显示 
        bg: '#eee',                    //（可选项）字符串类型；指示器未激活时的背景，支持 rgb，rgba，#；默认：#eee
        active: '#f00',                //（可选项）字符串类型；指示器激活时的背景，支持 rgb，rgba，#；默认：#eee
    }
}
```

index：

- 类型：数字类型
- 描述：（可选项）初始选中的图片索引值，从 0 开始
- 默认：0

interval：

- 类型：数字类型
- 描述：（可选项）图片流每次切换的停留间隔，毫秒数；只有 auto 为 true 时有效
- 默认：3000

images：

- 类型：JSON 数组
- 描述：为图片流指定数据
- 内部字段：

```js
[{
    url: 'widget://res/coverflow/0.png' //字符串类型；对应图片的网址，支持 fs://、widget://、http://等   
}]
```

fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window

fixed:

- 类型：布尔
- 描述：（可选项）是否将模块视图固定到窗口上，不跟随窗口上下滚动
- 默认值：true（不随之滚动）

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    eventType：                         //字符串类型；交互事件类型，取值范围如下:
                                       //show: 显示事件
                                       //click: 点击事件
                                       //scroll: 滚动事件
    index:                             //数字类型；返回用户选择的图片的下标
}
```

##示例代码

```js
var UICoverFlow = api.require('UICoverFlow');
UICoverFlow.open({
    rect: {
        x: 0,
        y: 60,
        w: api.winWidth,
        h: 480
    },
    styles: {
        bg: '#fff',
        image: {
            activeW: 300,
            activeH: 400,
            corner: 2,
            placeholder: 'widget://placeholder.png'
        }
      
    },
    images: [{
        url: 'widget://res/coverflow/0.png'
    }, {
        url: 'widget://res/coverflow/1.png'
    }, {
        url: 'widget://res/coverflow/2.png'
    }, {
        url: 'widget://res/coverflow/3.png'
    }],
    index: 0,
    interval: 2000,
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


#**setIndex**<div id="5"></div>

滚动到指定条目

setIndex({params})

##params

index：

- 类型：数字
- 描述：滚动的指定位置索引

##示例代码

```js
var UICoverFlow = api.require('UICoverFlow');
UICoverFlow.setIndex({
    index: 1
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**close**<div id="2"></div>

关闭 UICoverFlow

close()

##示例代码

```js
    var UICoverFlow = api.require('UICoverFlow');
    UICoverFlow.close();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**hide**<div id="2"></div>

隐藏显示的 coverFlow

hide()

##示例代码

```js
    var UICoverFlow = api.require('UICoverFlow');
    UICoverFlow.hide();
```

##补充说明

只是隐藏模块视图，并没有从内存里清除

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**show**<div id="4"></div>

显示已隐藏的 UICoverFlow 

show()

##示例代码

```js
    var UICoverFlow = api.require('UICoverFlow');
    UICoverFlow.show();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="6"></div>
#**clearCache**

清除缓存到本地的网络图片，**本接口只清除本模块缓存的数据，若要清除本app缓存的所有数据这调用api.clearCache**

clearCache()

##示例代码

```js
var UICoverFlow = api.require('UICoverFlow');
UICoverFlow.clearCache();
```

##可用性

IOS系统，Android系统

可提供的1.0.0及更高版本