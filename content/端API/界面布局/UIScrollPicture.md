/*
Title: UIScrollPicture
Description: UIScrollPicture
*/
<div class="outline">
[open](#m1)

[close](#m2)

[show](#m6)

[hide](#m5)

[setCurrentIndex](#m3)

[reloadData](#m4)

[addEventListener](#m7)
</div>

#**概述**

UIScrollPicture 是一个图片轮播模块，只需传入一组图片地址，即可实现图片轮播效果，开发者可以监听滑动或点击事件；一般用于头条新闻或广告图片的轮播展示；图片地址支持本地路径或网络路径，网络图片会自动缓存到本地。**UIScrollPicture 模块是 scrollPicture 模块的优化版。**

![图片说明](/img/docImage/scrollPicture.jpg)

<div id="m1"></div>
#**open**

打开模块

open({params}, callback(ret, err))

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
    captions: []    //（可选项）数组类型；说明文字数组，与 paths 数组长度一致；不传则不显示说明文字区域
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
        color: '#FFFFFF',               //（可选项）指示器颜色 ，支持rgb、rgba、#；默认：'#FFFFFF'
        activeColor: '#DA70D6'          //（可选项）当前指示器颜色，支持rgb、rgba、#；默认：'#DA70D6'
    }
}
```

placeholderImg：

- 类型：字符串
- 描述：（可选项）网络图片未加载完毕时，模块显示的占位图片，要求本地路径（fs://，widget://）

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
- 默认值：true

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
- 描述：（可选项）模块是否随所属 Window 或 Frame 滚动
- 默认值：true（不随之滚动）

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true,                  //布尔型；true||false
	eventType: 'click'||'show',    //字符串类型；交互事件类型，
                                   //取值范围：
                                   //click（用户点击）
                                   //show（模块打开成功）
	index：0		               //数字类型；当前图片的索引
}
```

##示例代码

```js
var UIScrollPicture = api.require('UIScrollPicture');
UIScrollPicture.open({
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
        captions: ['apicloud', 'apicloud', 'apicloud', 'apicloud']
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
        }
    },
    placeholderImg: 'widget://res/slide1.jpg',
    contentMode: 'scaleToFill',
    interval: 3,
    fixedOn: api.frameName,
    loop: true,
    fixed: false
},function( ret, err ){
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

<div id="m2"></div>
#**close**

关闭模块

close()

##示例代码

```js
var UIScrollPicture = api.require('UIScrollPicture');
UIScrollPicture.close();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m6"></div>
#**show**

显示模块

show()

##示例代码

```js
var UIScrollPicture = api.require('UIScrollPicture');
UIScrollPicture.show();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m5"></div>
#**hide**

隐藏模块

hide()

##示例代码

```js
var UIScrollPicture = api.require('UIScrollPicture');
UIScrollPicture.hide();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m3"></div>
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
var UIScrollPicture = api.require('UIScrollPicture');
UIScrollPicture.setCurrentIndex({
	index: 2
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m4"></div>
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
    captions: []    //（可选项）数组类型；说明文字数组，默认：原 captions 数组
}
```

##示例代码

```js
var UIScrollPicture = api.require('UIScrollPicture');
UIScrollPicture.reloadData({
    data: {
        paths: ['widget://res/img/ic/slide1.jpg', 'widget://res/img/ic/slide2.jpg', 'widget://res/img/ic/slide5.jpg'],
        captions: ['title1', 'title2', 'title3']
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m7"></div>
#**addEventListener**

事件监听

addEventListener({params}, callback(ret, err))

##params

name：

- 类型：字符串
- 描述：监听的事件名称，取值范围：'scroll'（图片滚动事件）

##callback(ret, err)

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
var UIScrollPicture = api.require('UIScrollPicture');
UIScrollPicture.addEventListener({
    name: 'scroll'
}, function( ret, err ){
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