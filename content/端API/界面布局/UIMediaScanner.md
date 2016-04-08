/*
Title: UIMediaScanner
Description: UIMediaScanner
*/
<div class="outline">
[open](#a1)

[scan](#a2)

[fetch](#a3)

[transPath](#a4)
</div>

#**概述**

UIMediaScanner 是一个多媒体扫描器，可扫描系统的图片、视频等多媒体资源。用于图片、视频资源的多选功能；open 接口打开可配置样式的选择界面，scan 接口返回资源数据；**注意：Android 平台扫描整个设备的资源，IOS 仅扫描相册内的资源。UIMediaScanner 模块是 mediaScanner 模块的优化版。**

![图片说明](/img/docImage/UIMediaScanner.jpg)

<div id="a1"></div>

#**open**

打开多媒体资源选择器，打开后会全屏显示

open({params}, callback(ret))

##params

type：

- 类型：字符串
- 描述：返回的资源种类；默认：'all'
- 取值范围：
    * all（图片和视频）
    * picture（图片）
    * video（视频）

column：

- 类型：数字
- 描述：（可选项）图片显示的列数，须大于1
- 默认值：4

classify：

- 类型：布尔
- 描述：（可选项）是否将图片分类显示（为 true 时，会首先跳转到相册分类列表页面）
- 默认值：false

max：

- 类型：数字
- 描述：（可选项）最多选择几张图片
- 默认值：5

sort：

- 类型：JSON对象
- 描述：（可选项）图片排序方式
- 内部字段：

```js
{
    key: 'time',    //（可选项）字符串类型；排序方式，默认：'time'
                    //取值范围：
                    //time（按图片创建时间排序）
    order: 'desc'   //（可选项）字符串类型；默认：'desc'
                    //取值范围：
                    //asc（旧->新）
                    //desc（新->旧）
}
```

texts：

- 类型：JSON对象
- 描述：（可选项）模块各部分的文字内容
- 内部字段：

```js
{
    stateText: '已选择*项',         //（可选项）字符串类型；状态文字内容；*号会被替换为已选择个数；默认：'已选择*项'
    cancelText: '取消',             //（可选项）字符串类型；取消按钮文字内容；默认：'取消'
    finishText: '完成'              //（可选项）字符串类型；完成按钮文字内容；默认：'完成'
}
```

styles：

- 类型：JSON对象
- 描述：（可选项）模块各部分的样式
- 内部字段：

```js
{
    bg: '#FFFFFF',                      //（可选项）字符串类型；资源选择器背景，支持rgb，rgba，#；默认：'#FFFFFF'
    mark: {                             //（可选项）JSON对象；选中图标的样式
        icon: '',                       //（可选项）字符串类型；图标路径（本地路径，支持fs://，widget://）；默认：对勾图标；在 Android 上暂不支持此参数
        position: 'bottom_left',        //（可选项）字符串类型；图标的位置，默认：'bottom_left'
                                        // 取值范围：
                                        // top_left（左上角）
                                        // bottom_left（左下角）
                                        // top_right（右上角）
                                        // bottom_right（右下角）
        size: 20                        //（可选项）数字类型；图标的大小；默认：显示的缩略图的宽度的三分之一
    },
    nav: {                              //（可选项）JSON对象；导航栏样式
        bg: '#eee',                     //（可选项）字符串类型；导航栏背景，支持 rgb，rgba，#；默认：'#eee'
        stateColor: '#000',             //（可选项）字符串类型；状态文字颜色，支持rgb，rgba，#；默认：'#000'
        stateSize: 18,                  //（可选项）数字类型；状态文字大小，默认：18
        cancelBg: 'rgba(0,0,0,0)',      //（可选项）字符串类型；取消按钮背景，支持rgb，rgba，#；默认：'rgba(0,0,0,0)'
        cancelColor: '#000',            //（可选项）字符串类型；取消按钮的文字颜色；支持rgb，rgba，#；默认：'#000'
        cancelSize: 18,                 //（可选项）数字类型；取消按钮的文字大小；默认：18
        finishBg: 'rgba(0,0,0,0)',      //（可选项）字符串类型；完成按钮的背景，支持rgb，rgba，#；默认：'rgba(0,0,0,0)'
        finishColor: '#000',            //（可选项）字符串类型；完成按钮的文字颜色，支持rgb，rgba，#；默认：'#000'
        finishSize: 18                  //（可选项）数字类型；完成按钮的文字大小；默认：18
    }
}
```

scrollToBottom：

- 类型：JSON
- 默认值：见内部字段
- 描述：（可选项）打开媒体资源界面后间隔一段时间开始自动滚动到底部设置
- 内部字段：

```js
{
   intervalTime:       //（可选项）数字类型；打开媒体资源界面后间隔的时间开始自动滚动到底部，单位秒（s），小于零的数表示不滚动到底部；默认：-1
   anim:               //（可选项）布尔类型；滚动时是否添加动画，android 平台不支持动画效果；默认true
}
```

exchange：

- 类型：布尔
- 默认值：false
- 描述：是否交换‘确定’和‘取消’按钮的位置（默认‘取消’按钮在右边，‘确定’按钮在左边）

rotation：

- 类型：布尔
- 默认值：false
- 描述：是否禁止屏幕旋转（禁止横屏）

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    list: [{                         //数组类型；返回选定的资源信息数组
        path: '',                    //字符串类型；资源路径，返回资源在本地的绝对路径
        thumbPath: '',               //字符串类型；缩略图路径，返回资源在本地的绝对路径
        suffix: '',                  //字符串类型；文件后缀名，如：png，jpg, mp4
        size: 1048576,               //数字类型；资源大小，单位（Bytes）
        time: '2015-06-29 15:49'     //字符串类型；资源创建时间，格式：yyyy-MM-dd HH:mm:ss
    }]
}
```

##示例代码

```js
var UIMediaScanner = api.require('UIMediaScanner');
UIMediaScanner.open({
    type: 'picture',
    column: 4,
    classify: true,
    max: 4,
    sort: {
        key: 'time',
        order: 'desc'
    },
    texts: {
        stateText: '已选择*项',
        cancelText: '取消',
        finishText: '完成'
    },
    styles: {
        bg: '#fff',
        mark: {
            icon: '',
            position: 'bottom_left',
            size: 20
        },
        nav: {
            bg: '#eee',
            stateColor: '#000',
            stateSize: 18,
            cancelBg: 'rgba(0,0,0,0)',
            cancelColor: '#000',
            cancelSize: 18,
            finishBg: 'rgba(0,0,0,0)',
            finishColor: '#000',
            finishSize: 18
        }
    },
    scrollToBottom:{
       intervalTime: 3,
       anim: true
    },
    exchange: true
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

<div id="a2"></div>

#**scan**

扫描系统多媒体资源，可以通过 Web 代码自定义多选界面。**注意：页面展示的图片建议使用缩略图，一次显示的图片不宜过多（1至2屏）**

scan({params}, callback(ret))

##params

type：

- 类型：字符串
- 描述：返回的资源种类；默认：'all'
- 取值范围：
    * all（图片和视频）
    * picture（图片）
    * video（视频）

count：

- 类型：数字
- 描述：（可选项）每次返回的资源数量；
- 默认：全部资源数量

sort：

- 类型：JSON对象
- 描述：（可选项）图片排序方式
- 内部字段：

```js
{
    key: 'time',    //（可选项）字符串类型；排序方式；默认：'time'
                    //取值范围：
                    //time（按图片创建时间排序）
    order: 'desc'   //（可选项）字符串类型；排列顺序；默认：'desc'
                    //取值范围：
                    //asc（旧->新）
                    //desc（新->旧）
}
```

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    total: 100,                      //数字类型；媒体资源总数
	list: [{                         //数组类型；返回指定的资源信息数组
		path: '',                    //字符串类型；资源路径，返回资源在本地的绝对路径
        thumbPath: '',               //字符串类型；缩略图路径，返回资源在本地的绝对路径
        suffix: '',                  //字符串类型；文件后缀名，如：png，jpg, mp4
        size: 1048576,               //数字类型；资源大小，单位（Bytes）
        time: '2015-06-29 15:49:22   //字符串类型；资源创建时间，格式：yyyy-MM-dd HH:mm:ss
	}]
}
```

##示例代码

```js
var UIMediaScanner = api.require('UIMediaScanner');
UIMediaScanner.scan({
    type: 'all',
    count: 10,
    sort: {
        key: 'time',
        order: 'desc'
    }
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

<div id="a3"></div>
#**fetch**

获取指定数量的多媒体资源，没有更多资源则返回空数组，**必须配合 scan 接口的 count 参数一起使用**。

fetch(callback(ret))

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    list: [{                         //数组类型；返回指定的资源信息数组
        path: '',                    //字符串类型；资源路径，返回资源在本地的绝对路径
        thumbPath: '',               //字符串类型；缩略图路径，返回资源在本地的绝对路径
        suffix: '',                  //字符串类型；文件后缀名，如：png，jpg, mp4
        size: 1048576,               //数字类型；资源大小，单位（Bytes）
        time: '2015-06-29 15:49'     //字符串类型；资源创建时间，格式：yyyy-MM-dd HH:mm:ss
    }]
}
```

##示例代码

```js
var UIMediaScanner = api.require('UIMediaScanner');
UIMediaScanner.fetch(function( ret, err ){
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

<div id="a4"></div>
#**transPath**

将相册图片地址转换为可以直接使用的本地路径地址（临时文件夹的绝对路径），**相册图片会被拷贝到临时文件夹，APP重启时临时文件会被自动删除。**

transPath({params},callback(ret))

##params

path：

- 类型：字符串
- 描述：要转换的图片路径（在相册库的绝对路径）

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
   path: ''     //字符串类型；相册内图片被拷贝到临时文件夹，返回已拷贝图片的绝对路径
}
```

##示例代码

```js
var UIMediaScanner = api.require('UIMediaScanner');
UIMediaScanner.transPath({
   path: ''
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