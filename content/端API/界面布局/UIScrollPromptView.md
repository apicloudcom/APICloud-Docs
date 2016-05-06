/*
Title: UIScrollPromptView
Description: UIScrollPromptView
*/
<div class="outline">
[open](#m1)

[close](#m2)

[show](#m3)

[hide](#m4)

[setCurrentIndex](#m5)

[reloadData](#m6)

[addEventListener](#m7)

[clearCache](#m8)
</div>

#**概述**

UIScrollPromptView 是一个图片轮播模块，只需传入一组图片地址，即可实现图片轮播效果。本模块与 UIScrollPicture 模块类似，不同的是，开发者可在图片轮播区域内自定义一个按钮，用户点击该按钮弹出相应的提示框。

open 接口内的 rect 参数，可控制图片轮播区域的位置和大小。styles 参数可以设置轮播视图底部的标题文字大小及颜色，亦可设置底部页面控制器（几个小圆点）的位置和样式。

本图片轮播器是由原生代码开发，对于网络图片的展示更加人性化。模块内部会做缓存处理，第一次加载网络图片时，模块会根据其路径生成一个 md5 加密的图片名，并缓存在缓存文件夹里。当用户下次打开同路径的图片时，模块直接从缓存文件内读取该图片，从而大大节省了用户流量。开发者可以通过调用 clearCache 接口清除本地的缓存文件，亦可以通过 api.clearCache 接口清除。由于原生代码相对前端代码的高效性，本模块相对于前端实现的图片轮播功能更加流畅，内存管理更加优化。当用户需要展示多张图片时，其内存只保留三张图片的空间，然后来回切换图片内容，从而降低了整个 app 内存占用率。具体模块功能请参考模块接口。

![图片说明](/img/docImage/UIScrollPromptView.png)

#模块接口

<div id="m1"></div>

#**open**

打开模块

open({params}, callback(ret))

##params

rect：

- 类型：JSON对象
- 描述：（可选项）模块的位置及尺寸
- 内部字段：

```js
{
    x: 0,   //（可选项）数字类型；模块左上角的 x 坐标（相对于所属的 Window 或 Frame）；默认：0
    y: 0,   //（可选项）数字类型；模块左上角的 y 坐标（相对于所属的 Window 或 Frame）；默认：0
    w: 320, //（可选项）数字类型；模块的宽度；默认：所属的 Window 或 Frame 的宽度
    h: 200  //（可选项）数字类型；模块的高度；默认：w * 2.0/3.0
}
```

data：

- 类型：JSON对象
- 描述：模块的图片路径数组，及说明文字数组
- 内部字段：

```js
{
    paths: [],      //数组类型；图片路径数组，支持http://，https://，widget://，fs://协议
    captions: [] ,  //（可选项）数组类型；说明文字数组，与 paths 数组长度一致；不传则不显示说明文字区域
    prompts: []     //（可选项）数组类型；提示框图片路径组成的数组，与 paths 数组长度一致；不传则不显示提示框图片
}
```

styles：

- 类型：JSON对象
- 描述：（可选项）模块各部分的样式
- 内部字段：

```js
{
    caption: {                          //（可选项）JSON对象；说明文字区域样式
        height: 35,                     //（可选项）数字类型；说明文字区域高度；默认：35.0
        color: '#E0FFFF',               //（可选项）字符串类型；说明文字字体颜色，支持rgb、rgba、#；默认：'#E0FFFF'
        size: 13,                       //（可选项）数字类型；说明文字字体大小；默认：13.0
        bgColor: '#696969',             //（可选项）字符串类型；说明文字区域的背景色，支持rgb、rgba、#；默认：'#696969'
        position: 'bottom'              //（可选项）字符串类型；说明文字区域的显示位置；默认：'bottom'
                                        //取值范围：
                                        //overlay（悬浮在图片上方，底部与图片底部对齐）
                                        //bottom（紧跟在图片下方，顶部与图片底部对齐）
        alignment: 'center'             //（可选项）字符串类型：说明文字在水平线上的位置；默认：left
                                        //取值范围：
                                        //right（居右限时）
                                        //center（居中显示）
                                        //left（居左显示）                                  
    },
    indicator: {                        //（可选项）JSON对象；指示器样式；不传则不显示指示器
        align: 'center',                //（可选项）字符串类型；指示器位置；默认：center
                                        //取值范围：
                                        //center（居中）
                                        //left（靠左）
                                        //right（靠右）
        color: '#FFFFFF',               //（可选项）字符串类型；指示器颜色 ，支持rgb、rgba、#；默认：'#FFFFFF'
        activeColor: '#DA70D6'          //（可选项）字符串类型；当前指示器颜色，支持rgb、rgba、#；默认：'#DA70D6'
    },
    prompt: {                           // (可选项) JSON对象；提示框样式配置，若不传则不显示提示框及其触发按钮
        button: {                       //（可选项）JSON对象；提示框触发按钮样式配置
           normal: 'fs://srlBtBg.png',  // 字符串类型；触发提示框按钮的背景图片路径，支持本地图片（fs://、widget://）
           x: 0,                        //（可选项）数字类型；按钮左上角的 x 坐标（相对于图片联播区域）；默认：0
           y: 0,                        //（可选项）数字类型；按钮左上角的 y 坐标（相对于图片联播区域）；默认：按钮上下居中显示的位置
           w: 60,                       //（可选项）数字类型；按钮的宽度；默认：60 
           h: 40                        //（可选项）数字类型；按钮的高度；默认：40
        },
        x: 0,                           //（可选项）数字类型；提示框左上角的 x 坐标（相对于图片联播区域）；默认：0
        y: 0,                           //（可选项）数字类型；提示框左上角的 y 坐标（相对于图片联播区域）；默认：提示框上下居中显示的位置
        w: 160,                         //（可选项）数字类型；提示框的宽度；默认：160
        h: 90,                          //（可选项）数字类型；提示框的高度；默认：90
        contentMode: 'scaleToFill',     //（可选项）字符串类型；提示框内图片显示模式；默认值：'scaleToFill'，
                                        // 取值范围如下：
                                        // scaleToFill（填充）
                                        // scaleAspectFit（适应）
        animation: true                 //（可选项）布尔类型；弹出提示框时是否添加动画效果
    }
}
```

placeholderImg：

- 类型：字符串
- 描述：（可选项）网络图片未加载完毕时，模块显示的占位图片，要求本地路径（fs://、widget://）

contentMode：

- 类型：字符串
- 描述：（可选项）图片填充模式
- 默认值：'scaleToFill'
- 取值范围：
    * scaleToFill（填充）
    * scaleAspectFit（适应）

interval：

- 类型：数字
- 描述：（可选项）图片轮换时间间隔，单位是秒（s）
- 默认值：3

auto:

- 类型：布尔
- 描述：（可选项）图片是否自动播放
- 默认值：false

loop:

- 类型：布尔
- 描述：（可选项）图片是否循环播放
- 默认值：true

fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window

fixed:

- 类型：布尔
- 描述：（可选项）模块是否随所属 window 或 frame 滚动
- 默认值：true（不随之滚动）

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true,                  //布尔型；true||false
	 eventType: 'click'||'show',   //字符串类型；交互事件类型，
                                   //取值范围：
                                   //click（用户点击图片联播器中的单张图片）
                                   //show（模块打开成功）
	index：0		                  //数字类型；当前图片的索引
}
```

##示例代码

```js
var UIScrollPromptView = api.require('UIScrollPromptView');
UIScrollPromptView.open({
    rect: {
        x: 0,
        y: 0,
        w: api.winWidth,
        h: api.winHeight / 2
    },
    data: {
        paths: [
	        'widget://res/img/apicloud.png', 
	        'widget://res/img/apicloud-gray.png',
	        'widget://res/img/apicloud.png', 
	        'widget://res/img/apicloud-gray.png'
        ],
        captions: ['apicloud', 'apicloud', 'apicloud', 'apicloud'],
        prompts: [
	        'widget://res/img/apicloud.png', 
	        'widget://res/img/apicloud-gray.png',
	        'widget://res/img/apicloud.png', 
	        'widget://res/img/apicloud-gray.png'
        ]
    },
    styles: {
        caption: {
            height: 35,
            color: '#E0FFFF',
            size: 13,
            bgColor: '#696969',
            position: 'bottom'
        },
        indicator: {
            align: 'center',
            color: '#FFFFFF',
            activeColor: '#DA70D6'
        },
        prompt: {
           button: {
              normal: 'widget://image/btn_normal.png',
              highlight: 'widget://image/btn_highlight.png',
              x: 0,
              y: 100,
              w: 60,
              h: 40
           },
           x: 0,
           y: 50,
           w: 160,
           h: 90,
           contentMode: 'scaleToFill',
           animation: true
        }
    },
    placeholderImg: 'widget://res/slide1.jpg',
    contentMode: 'scaleToFill',
    interval: 3,
    fixedOn: api.frameName,
    loop: true,
    fixed: false
},function( ret ){
    if( ret ){
         alert( JSON.stringify( ret ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m2"></div>

#**close**

关闭模块

close()

##示例代码

```js
var UIScrollPromptView = api.require('UIScrollPromptView');
UIScrollPromptView.close();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m3"></div>

#**show**

显示模块

show()

##示例代码

```js
var UIScrollPromptView = api.require('UIScrollPromptView');
UIScrollPromptView.show();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m4"></div>

#**hide**

隐藏模块

hide()

##示例代码

```js
var UIScrollPromptView = api.require('UIScrollPromptView');
UIScrollPromptView.hide();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m5"></div>

#**setCurrentIndex**

指定当前项

setCurrentIndex({params})

##params

index：

- 类型：数字
- 描述：（可选项）索引值
- 默认值：0

##示例代码

```js
var UIScrollPromptView = api.require('UIScrollPromptView');
UIScrollPromptView.setCurrentIndex({
	index: 2
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m6"></div>

#**reloadData**

更新模块数据

reloadData({params})

##params

data：

- 类型：JSON对象
- 描述：模块的图片路径数组，及说明文字数组
- 内部字段：

```js
{
    paths: [],      //（可选项）数组类型；图片路径数组；默认：原 paths 数组
    captions: [],   //（可选项）数组类型；说明文字数组，默认：原 captions 数组
    prompts: []     //（可选项）数组类型；提示框图片路径数组，默认：原 prompts 数组
}
```

##示例代码

```js
var UIScrollPromptView = api.require('UIScrollPromptView');
UIScrollPromptView.reloadData({
    data: {
        paths: ['widget://res/img/ic/slide1.jpg', 'widget://res/img/ic/slide2.jpg', 'widget://res/img/ic/slide5.jpg'],
        captions: ['title1', 'title2', 'title3'],
        prompts: ['widget://res/img/ic/slide1.jpg', 'widget://res/img/ic/slide2.jpg', 'widget://res/img/ic/slide5.jpg']
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m7"></div>

#**addEventListener**

事件监听

addEventListener({params}, callback(ret))

##params

name：

- 类型：字符串
- 描述：监听的事件名称，取值范围：'scroll'（图片滚动事件）

##callback(ret)

ret：

- 类型：JSON对象
- 描述：事件触发时回调的参数，可能为空
- 内部字段：

```js
{
    status：true,    //布尔型；true||false
    index：0         //数字类型；当前图片的索引
}
```

##示例代码

```js
var UIScrollPromptView = api.require('UIScrollPromptView');
UIScrollPromptView.addEventListener({
    name: 'scroll'
}, function( ret ){
    if( ret ){
          alert( JSON.stringify( ret ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**clearCache**

清除缓存到本地的网络图片，**本接口只清除本模块缓存的数据，若要清除 app 缓存的所有数据则调用api.clearCache**

clearCache()

##示例代码

```js
var UIScrollPromptView = api.require('UIScrollPromptView');
UIScrollPromptView.clearCache();
```

##可用性

IOS系统，Android系统

可提供的1.0.0及更高版本