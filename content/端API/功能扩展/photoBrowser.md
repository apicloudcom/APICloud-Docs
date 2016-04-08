/*
Title: photoBrowser
Description: photoBrowser
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#m1)

[close](#m2)

[hide](#m3)

[show](#m4)

[setIndex](#m5)

[getIndex](#m6)

[getImage](#m7)

[setImage](#m8)

[appendImage](#m9)

[deleteImage](#m10)

[clearCache](#m11)
</div>

#**概述**

photoBrowser 是一个图片浏览器，支持单张、多张图片查看的功能，可放大缩小图片，支持本地和网络图片资源。若是网络图片资源则会被缓存到本地，缓存到本地上的资源可以通过 clearCache 接口手动清除。同时本模块支持横竖屏显示，在本app支持横竖屏的情况下，本模块底层会自动监听当前设备的位置状态，自动适配横竖屏以展示图片。使用此模块开发者看实现炫酷的图片浏览器。

**模块使用攻略**

开发者使用此模块时可以先 frame 的形式打开并添加到主窗口上，该 frame 不可设置位置和大小，其宽高默认和当前设备屏幕的宽高相同。模块打开后可再 open 一个自定义的 frame 贴在本模块上，从而实现自定义图片浏览器样式和功能。需要适配横竖屏时，开发者可通过api对象监听当前设备的位置状态，以改变自己自定义的 frame 的横竖屏展示，而图片的展示模块内部会自动适配横竖屏，最终实现了整个浏览器的横竖屏配置。在本模块的 open 接口内可以获取图片的下载状态，通过 getImage 接口获取目标图片在本地的绝对路径，以实现保存到系统相册的功能。详情请参考模块接口参数说明。

![图片说明](/img/docImage/imageBrowser.jpg)

##**模块接口**

<div id="m1"></div>
#**open**

打开图片浏览器

open({params},callback(ret))

##params

images：

- 类型：数组
- 描述：要读取的图片路径组成的数组，图片路径支持fs://、http://协议

activeIndex：

- 类型：数字
- 描述：（可选项）当前要显示的图片在图片路径数组中的索引
- 默认值：0

placeholderImg：

- 类型：字符串
- 描述：（可选项）当加载网络图片时显示的占位图路径，要求本地图片路径（widget://、fs://）

bgColor：

- 类型：字符串
- 描述：（可选项）图片浏览器背景色，支持rgb、rgba、#
- 默认：#000

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：
  
```js
{
     eventType: 'show',    //字符串类型；交互事件类型，取值范围如下：
                           //show：打开浏览器并显示
                           //change：用户切换图片
                           //click：用户单击图片浏览器
                           //loadImgSuccess：网络图片下载成功的回调事件
                           //loadImgFail：网络图片下载失败的回调事件
                           //longPress：用户长按图片事件
     index: 2              //数字类型；当前图片在图片路径数组中的索引
}
```



##示例代码

```js
var photoBrowser = api.require('photoBrowser');
photoBrowser.open({
	images: [ 
        'fs://img/image1.png', 
        'fs://img/encryption.png'
    ],
    activeIndex: 0,
    placeholderImg: 'widget://res/img/apicloud.png',
    bgColor: '#000'
}, function(ret){
    alert(JSON.stringify(ret));
});
```

##可用性

IOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m2"></div>
#**close**

关闭图片浏览器

close()

##示例代码

```js
var photoBrowser = api.require('photoBrowser');
photoBrowser.close();
```

##可用性

IOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m3"></div>
#**hide**

隐藏图片浏览器

close()

##示例代码

```js
var photoBrowser = api.require('photoBrowser');
photoBrowser.hide();
```

##可用性

IOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m4"></div>
#**show**

显示图片浏览器

show()

##示例代码

```js
var photoBrowser = api.require('photoBrowser');
photoBrowser.show();
```

##可用性

IOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m5"></div>
#**setIndex**

设置当前显示图片

setIndex({params})

##params

index：

- 类型：数字
- 描述：（可选项）当前要显示的图片在图片路径数组中的索引
- 默认值：0

##示例代码

```js
var photoBrowser = api.require('photoBrowser');
photoBrowser.setIndex({
    index: 0
});
```

##可用性

IOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m6"></div>
#**getIndex**

获取当前图片在图片路径数组内的索引

getIndex(callback(ret))

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：
  
```js
{
     index: 2        //数字类型；当前图片在图片路径数组中的索引
}
```



##示例代码

```js
var photoBrowser = api.require('photoBrowser');
photoBrowser.getIndex(function(ret){
    alert(JSON.stringfiy(ret));
});
```

##可用性

IOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m7"></div>
#**getImage**

获取指定图片在本地的绝对路径

getImage({params}, callback(ret))

##params

index：
 
- 类型：数字
- 描述：指定图片在图片数组中的索引
- 默认：当前图片在图片数组中的索引

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：
  
```js
{
     path: ‘’        //字符串类型；获取的绝对
}
```



##示例代码

```js
var photoBrowser = api.require('photoBrowser');
photoBrowser.getImage({
    index: 2
}, function(ret){
    alert(JSON.stringfiy(ret));
});
```

##可用性

IOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m8"></div>
#**setImage**

设置指定位置的图片，**若设置的是网络图片加载成功或失败会给 open 接口回调该加载事件**

setImage({params})

##params

index：
 
- 类型：数字
- 描述：（可选项）指定图片在图片数组中的索引
- 默认：当前图片在图片数组中的索引

image：
 
- 类型：字符串
- 描述：要设置的图片路径，支持本地和网络路径（fs://、http://）


##示例代码

```js
var photoBrowser = api.require('photoBrowser');
photoBrowser.setImage({
    index: 2 ,
    image: 'http://docs.apicloud.com/img/docImage/imageBrowser.jpg'
});
```

##可用性

IOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m9"></div>
#**appendImage**

往已打开的图片浏览器里添加图片（拼接在最后）

appendImage({params},callback(ret))

##params

images：

- 类型：数组
- 描述：要拼接的图片路径组成的数组，图片路径支持fs://、http://协议


##示例代码

```js
var photoBrowser = api.require('photoBrowser');
photoBrowser.appendImage({
	images: [ 
        'fs://img/image1.png', 
        'fs://img/encryption.png'
    ]
});
```

##可用性

IOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m10"></div>
#**deleteImage**

删除指定位置的图片

deleteImage({params}, callback(ret))

##params

index：
 
- 类型：数字
- 描述：（可选项）删除的指定图片在图片数组中的索引
- 默认：当前图片在图片数组中的索引

##示例代码

```js
var photoBrowser = api.require('photoBrowser');
photoBrowser.deleteImage({
    index: 2 
});
```

##可用性

IOS系统，Android系统

可提供的1.0.0及更高版本


<div id="m11"></div>
#**clearCache**

清除缓存到本地的网络图片，**本接口只清除本模块缓存的数据，若要清除本app缓存的所有数据这调用api.clearCache**

clearCache()

##示例代码

```js
var photoBrowser = api.require('photoBrowser');
photoBrowser.clearCache();
```

##可用性

IOS系统，Android系统

可提供的1.0.0及更高版本