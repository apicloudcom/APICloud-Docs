/*
Title: MNActionButton
Description: MNActionButton
*/

<div class="outline">
[open](#m1)

[close](#m2)

[hide](#m3)

[show](#m4)
</div>

#**概述**

MNActionButton 是 actionButton 模块的优化升级版。开发者可通过本模块打开一个以 action 形式弹出的菜单，该菜单从当前屏幕底部以动画的形式弹出。所弹出的菜单依附于当前主窗口，其生命周期也痛当前主窗口。

**模块功能**

该菜单由多个菜单按钮组成，开发者可定义显示行数和列数。亦支持多屏显示，当开发者所设置的子按钮个数超过当前屏幕锁承载的个数时，子按钮会被现实在下一屏，用户左右拖动即可查看。菜单子按钮图片及其标题，都可通过相应参数自定义设置。详细功能请查看模块接口。

![图片说明](/img/docImage/actionButton.jpg)

##**模块接口**

#**open**<div id="m1"></div>

打开弹动按钮菜单

open({params}, callback(ret, err))

##params

layout：
- 类型：JSON 对象
- 描述：菜单的布局设置，包括行、行间距，列、列间距等
- 内部描述

```js
{
    row: 2,                            //（可选项）数字类型；每屏显示菜单按钮的行数；默认：2
    col: 3,                            //（可选项）数字类型；每屏显示菜单按钮的列数；默认：3
    rowSpacing: 5,                     //（可选项）数字类型；行与行之间的距离；默认：10
    colSpacing: 10,                    //（可选项）数字类型；列与列之间的距离；默认：10
    offset: 0,                         //（可选项）数字类型；整个菜单底部相对所属 window 底部的距离，只能为正整数；默认：44
}
```

animation：

- 类型：布尔类型
- 描述：弹出和隐藏菜单时是否带弹出动画效果
- 默认：true

autoHide：

- 类型：布尔类型
- 描述：点击菜单按钮后是否自动隐藏菜单
- 默认：true

styles：

- 类型：JSON 类型
- 描述：弹出菜单整体样式设置
- 内部字段： 

```js
{
    maskBg: 'rgba(0,0,0,0.2)',         //（可选项）字符串类型；遮罩层背景，支持 rgb，rgba，#，img；默认：rgba(0,0,0,0.2)
    bg: '#fff',                        //（可选项）字符串类型；菜单有效区域背景，支持 rgb，rgba，#，img；默认：#fff
    cancelButton: {                    //（可选项）JSON 对象类型，取消按钮设置
        size: 44,                      //（可选项）数字类型；底部取消按钮的高和宽；默认：44
        bg: '#fff',                    //（可选项）字符串类型；取消按钮的 100% 宽度的背景，支持rgb，rgba，#，img；默认：'#fff'
        icon: 'widget://res/icon.png', //（可选项）字符串类型：取消按钮的图标，要求本地路径（widget://、fs://）；默认：默认X型图标
    },
    item: {                            //（可选项）JSON 对象类型，菜单按钮设置
        titleColor: '#848484',         //（可选项）字符串类型；菜单按钮文字颜色，支持 rgb，rgba，#；默认：#848484
        titleHighlight: 'dd2727',      //（可选项）字符串类型；菜单按钮文字高亮颜色，支持 rgb，rgba，#；默认：同 titleColor
        titleSize: 12,                 //（可选项）数字类型；菜单按钮文字大小，同时也是文字栏所占高度，值为 0 时不显示文字栏；默认：12
    },
    indicator: {                       //（可选项）JSON 对象类型；页标指示器样式，若不传则不显示该指示器
        color: '#c4c4c4',              //（可选项）字符串类型；其它页指示器颜色；支持rgb、rgba、#；默认：'#c4c4c4'
        highlight: '#9e9e9e'           //（可选项）字符串类型；当前页指示器颜色；支持rgb、rgba、#；默认：'#9e9e9e'
    }
}
```

items：

- 类型：JSON 数组类型
- 描述：菜单按钮信息数组，该数组有多少个元素，则有多少个菜单按钮
- 内部字段：

```js
[{                                     //JSON 对象类型；一个菜单项的设置信息
	icon: 'widget://res/icon.png',     //字符串类型；一个菜单按钮的图标路径，要求本地路径（widget://、fs://）；
	highlight: 'widget://res/highlight.png', //（可选项）字符串类型；一个菜单按钮的高亮图标路径，要求本地路径（widget://、fs://）；默认：同 icon
	title: '菜单项1',                  //字符串类型；菜单按钮的文字；默认：未设置时不显示，但文字栏仍按 titleSize 设置显示高度
}]
```

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    eventType:                         //字符串类型；交互事件类型，取值范围如下：
                                       //click（表示用户点击了菜单按钮）
                                       //cancel（表示用户取消了菜单显示，包括点击取消按钮和遮罩层）
	index:0                            //数字类型；点击子菜单项时返回其索引
}
```

##示例代码

```js
var obj = api.require('MNActionButton');
obj.open({
    layout: {
        row: 2,                        //（可选项）数字类型；每屏显示菜单按钮的行数；默认：2
        col: 3,                        //（可选项）数字类型；每屏显示菜单按钮的列数；默认：3
        rowSpacing: 5,                 //（可选项）数字类型；行与行之间的距离；默认：10
        colSpacing: 10,                //（可选项）数字类型；列与列之间的距离；默认：10
        offset: 0                      //（可选项）数字类型；整个菜单底部距离所属 window 底部的距离，只能为正整数；默认：0
    },
    animation: true,                   //（可选项）布尔类型；弹出和隐藏菜单时是否带弹出动画效果，true|false；默认：true
    autoHide: true,                    //（可选项）布尔类型；点击菜单按钮后是否自动隐藏菜单，true|false；默认：true
    styles: {
        maskBg: 'rgba(0,0,0,0.2)',     //（可选项）字符串类型；遮罩层背景，支持 rgb，rgba，#，img；默认：rgba(0,0,0,0.2)
        bg: '#fff',                    //（可选项）字符串类型；菜单有效区域背景，支持 rgb，rgba，#，img；默认：#fff
        cancelButton: {                      //（可选项）JSON 对象类型，取消按钮设置
            size: 44,                  //（可选项）数字类型；底部取消按钮的高和宽；默认：44
            bg: '#fff',                //（可选项）字符串类型；取消按钮的 100% 宽度的背景，支持rgb，rgba，#，img；默认：'#fff'
            icon: 'widget://res/action-button-cancel.png'  //（可选项）字符串类型：取消按钮的图标，要求本地路径（widget://、fs://）；默认：默认X型图标
        },
        item: { //（可选项）JSON 对象类型，菜单按钮设置
            titleColor: '#888',        //（可选项）字符串类型；菜单按钮文字颜色，支持 rgb，rgba，#；默认：#848484
            titleHighlight: 'dd2727',  //（可选项）字符串类型；菜单按钮文字高亮颜色，支持 rgb，rgba，#；默认：同 titleColor
            titleSize: 12              //（可选项）数字类型；菜单按钮文字大小，同时也是文字栏所占高度，值为 0 时不显示文字栏；默认：12
        },
        indicator: {                   //（可选项）JSON 对象类型；页标指示器样式，若不传则不显示该指示器
            color: '#c4c4c4',          //（可选项）字符串类型；其它页指示器颜色；支持rgb、rgba、#；默认：'#c4c4c4'
            highlight: '#9e9e9e'       //（可选项）字符串类型；当前页指示器颜色；支持rgb、rgba、#；默认：'#9e9e9e'
        }
    },
    items:[{ //JSON 对象类型；一个菜单项的设置信息
        icon: 'widget://res/MNActionButton/0.png', //字符串类型；一个菜单按钮的图标路径，要求本地路径（widget://、fs://）；
    highlight: 'widget://res/MNActionButton/0.png', //（可选项）字符串类型；一个菜单按钮的高亮图标路径，要求本地路径（widget://、fs://）；默认：同 icon
        title: '菜单项1',               //字符串类型；菜单按钮的文字；默认：未设置时不显示，但文字栏仍按 titleSize 设置显示高度
    }, {
        icon: 'widget://res/MNActionButton/1.png',
        highlight: 'widget://res/MNActionButton/1.png',
        title: '菜单项2'
    }, {
        icon: 'widget://res/MNActionButton/2.png',
        highlight: 'widget://res/MNActionButton/2.png',
        title: '菜单项3'
    }, {
        icon: 'widget://res/MNActionButton/3.png',
        highlight: 'widget://res/MNActionButton/3.png',
        title: '菜单项4'
    }, {
        icon: 'widget://res/MNActionButton/4.png',
        highlight: 'widget://res/MNActionButton/4.png',
        title: '菜单项5'
    }, {
        icon: 'widget://res/MNActionButton/5.png',
        highlight: 'widget://res/MNActionButton/5.png',
        title: '菜单项6'
    }, {
        icon: 'widget://res/MNActionButton/6.png',
        highlight: 'widget://res/MNActionButton/6.png',
        title: '菜单项7'
    }, {
        icon: 'widget://res/MNActionButton/7.png',
        highlight: 'widget://res/MNActionButton/7.png',
        title: '菜单项8'
    }]
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

#**close**<div id="m2"></div>

关闭菜单

close()

##示例代码

    var obj = api.require('MNActionButton');
    obj.close();

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**hide**<div id="m3"></div>

隐藏菜单

hide()

##示例代码

    var obj = api.require('MNActionButton');
    obj.hide();

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**show**<div id="m4"></div>

显示已隐藏的菜单

show()

##示例代码

    var obj = api.require('MNActionButton');
    obj.show();

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
