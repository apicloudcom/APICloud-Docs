/*
Title: MNRotationMenu
Description: MNRotationMenu
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[setIndex](#2)

[show](#3)

[hide](#4)

[close](#5)

[clearCache](#6)
</div>

#**概述**

MNRotationMenu 是一个图片旋转轮播控件，实现了类似扑克牌效果的图片轮播展示。开发者可自定义图片的数量，点击图片时会有回调，比如开发者可以自定义点击跳转连接

![图片说明](/img/docImage/MNRotationMenu.jpg)

#**open**<div id="1"></div>

打开图片旋转轮播控件

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
    h: 180                             //（可选项）数字类型；模块的高度；默认值：180
}

```

items：

- 类型：数组类型
- 描述：设置图片旋转轮播控件的图片项
- 内部字段：

```js
[{
    url: 'fs://rotation/0.png'   //字符串类型；图片路径，支持：fs://、widget://、http://等
}]

```

styles：

- 类型：JSON 对象
- 描述：图片旋转轮播控件的样式设置
- 内部字段：

```js
{
    bg: '#fff',                        //（可选项）字符串类型；控件的背景，支持 rgb、rgba、#、img；默认：#fff
    r: 190,                //（可选项）数字类型；控件所在圆的半径，即图片下边到圆心的距离；默认值：190
    image:{                            //JSON 类型；图片的样式设置
		h:108,                          //（可选项）数字类型；图片的显示高度；默认:108
        w:80,                          //（可选项）数字类型；图片的显示宽度；默认:80
        corner: 2,                     //（可选项）数字类型；图片圆角半径；默认：2.0
        placeholder: 'fs://ph.png',    //（可选项）字符串类型；图片的占位图，支持 widget://、fs://；默认：未设置时不显示占位图
    },
    indicator: {                       //（可选项）JSON 类型；指示器的样式设置，若为空则不显示指示器 
        bg: '#eee',                    //（可选项）字符串类型；指示器未激活时的背景，支持 rgb、rgba、#；默认：#eee
        active: '#f00',                //（可选项）字符串类型；指示器激活时的背景，支持 rgb、rgba、#；默认：#eee
    }
}
```

index：

- 类型：数字类型
- 描述：（可选项）初始选中的图片索引值
- 默认：items数组长度 / 2（向下取整）

auto：

- 类型：布尔类型
- 描述：（可选项）图片是否自动播放
- 默认：false

interval：

- 类型：数字类型
- 描述：（可选项）图片每次切换的停留间隔，单位 ms（毫秒）；仅当 auto 为 true 时有效
- 默认：3000

fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window

fixed:

- 类型：布尔
- 描述：（可选项）模块是否随所属 window 或 frame 滚动
- 默认值：true（不随之滚动）

##callback(ret, err)

ret：

- 类型：JSON 对象
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
var MNRotationMenu = api.require('MNRotationMenu');
MNRotationMenu.open({
        rect: {
           	y:api.winHeight-180,
    		w:api.winWidth,
    		h:180
        },
        items: [{
            url: 'fs://rotation/0.png'
        }, {
            url: 'fs://rotation/1.png'
        }, {
            url: 'fs://rotation/2.png'
        }, {
            url: 'fs://rotation/3.png'
        }, {
            url: 'fs://rotation/4.png'
        }, {
            url: 'fs://rotation/5.png'
        }, {
            url: 'fs://rotation/6.png'
        }],
        styles: {
            bg: '#fff',
            r:190,
            image: {
                w: 80,
		        h: 108,
                corner: 2,
                placeholder: 'widget://placeholder.png'
            },
            indicator: {
                bg: '#eee',
                active: '#f00'
            }
        },
        index: 1
    },
    function(ret, err) {
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

#**setIndex**<div id="2"></div>

滚动到指定条目

setIndex({params})

##params

index：

- 类型：数字
- 描述：滚动的指定位置索引

##示例代码

```js
var MNRotationMenu = api.require('MNRotationMenu');
MNRotationMenu.setIndex({
    index: 2
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**show**<div id="3"></div>

显示已经隐藏的模块

show()

##示例代码

```js
var MNRotationMenu = api.require('MNRotationMenu');
MNRotationMenu.show();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**hide**<div id="4"></div>

隐藏模块（并没有从内存清除）

hide()

##示例代码

```js
var MNRotationMenu = api.require('MNRotationMenu');
MNRotationMenu.hide();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**close**<div id="5"></div>

关闭模块（从内存清除）

close()

##示例代码

```js
var MNRotationMenu = api.require('MNRotationMenu');
MNRotationMenu.close();
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
var MNRotationMenu = api.require('MNRotationMenu');
MNRotationMenu.clearCache();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本