/*
Title: UIListView
Description: UIListView
*/
<div class="outline">
[open](#m1)

[close](#m6)

[show](#m15)

[hide](#m14)

[setAttr](#m2)

[getIndex](#m3)

[getDataByIndex](#m4)

[setSwipeBtns](#m5)

[reloadData](#m7)
 
[deleteItem](#m8)
 
[updateItem](#m9)

[insertItem](#m10)
 
[appendData](#m11)
 
[setRefreshHeader](#m12)
 
[setRefreshFooter](#m13)
</div>

#**概述**

UIListView 模块封装了一个数据列表控件，列表项水平侧滑可出现控制按钮；开发者可自定义列表的数据源，及列表的样式，支持列表项的增、删、改、查，支持批量更新、追加数据，支持下拉刷新和上拉加载事件。**UIListView 模块是 listView 模块的优化版。**

![图片说明](/img/docImage/listView.jpg)

<div id="m1"></div>
#**open**

打开 UIListView 模块

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
    w: 320, //（可选项）数字类型；模块的宽度；默认值：所属的 Window 或 Frame 的宽度
    h: 480  //（可选项）数字类型；模块的高度；默认值：所属的 Window 或 Frame 的高度
}
```

data：

- 类型：数组
- 描述：列表的数据源，**开发者可以自定义唯一的键值对信息（如：uid: '1001'），供 getIndex 使用**
- 内部字段：

```js
[{
    imgPath: '',            //（可选项）字符串类型；列表项的配图路径，支持http://、https://、widget://、fs://等协议，网络图片会被缓存到本地，若不传则标题和子标题靠最左侧显示
    title: '',              //（可选项）字符串类型；标题，若不传或为空则 subTitle 上下位置居中显示
    subTitle: '',           //（可选项）字符串类型；子标题，若不传或为空则 title 上下位置居中显示
    remark: '',             //（可选项）字符串类型；右边备注文字
    icon: '',               //（可选项）字符串类型；右侧备注的图标路径（本地路径，支持fs://，widget://）
    rightBtns: []           //（可选项）数组类型；列表项向左滑动露出的按钮组，配置某一项的特定按钮组，若不传则显示通用按钮，内部字段同下方 rightBtns 参数
}]
```

rightBtns：

- 类型：数组
- 描述：（可选项）列表项向左滑动露出的按钮组，**建议：配置列表每项的通用按钮，用此参数；配置某一项的特定按钮，可在 `data` 数组的指定项传入 `rightBtns` 参数**
- 内部字段：

```js
[{
    bgColor: '#388e8e', //（可选项）字符串类型；按钮背景色，支持rgb、rgba、#；默认：'#388e8e'
    activeBgColor: '',  //（可选项）字符串类型；按钮按下时的背景色，支持rgb、rgba、#
    width: 70,          //（可选项）数字类型；按钮的宽度；默认：w / 4       
    title: '',          //（可选项）字符串类型；按钮标题，水平、垂直居中
    titleSize: 12,      //（可选项）数字类型；按钮标题文字大小；默认：12
    titleColor: '#fff', //（可选项）字符串类型；按钮标题文字颜色，支持rgb、rgba、#；默认：'#ffffff'
    icon: '',           //（可选项）字符串类型；按钮标题前的图标路径（本地路径，支持fs://，widget://），水平、垂直居中，图标为正方形
    iconWidth: 20       //（可选项）数字类型；按钮标题前的图标宽度，图标为正方形；默认：20
}]
```

styles:

- 类型：JSON对象
- 描述：（可选项）模块各部分的样式
- 内部字段：

```js
{
    borderColor: '#696969',             //（可选项）字符串类型；列表分割线的颜色，支持rgb、rgba、#；默认：'#696969'
    item: {                             //（可选项）JSON对象；列表项的样式
        bgColor: '#AFEEEE',             //（可选项）字符串类型；列表项的背景色，支持rgb、rgba、#；默认：'#AFEEEE'
        activeBgColor: '#F5F5F5',       //（可选项）字符串类型；列表项按下时的背景色，支持rgb、rgba、#；默认：'#F5F5F5'
        height: 55,                     //（可选项）数字类型；列表项的高度；默认：55
        imgWidth: 40,                   //（可选项）数字类型；列表项配图的宽度；默认：列表项的高度减去10px
        imgHeight: 40,                  //（可选项）数字类型；列表项配图的高度；默认：列表项的高度减去10px
        placeholderImg: '',             //（可选项）字符串类型；列表项配图的占位图路径（本地路径，fs://，widget://），默认：APICloud 图标
        titleSize: 12,                  //（可选项）数字类型；列表项标题文字大小；默认：12
        titleColor: '#000',             //（可选项）字符串类型；列表项标题文字颜色，支持rgb，rgba，#；默认：'#000000'
        subTitleSize: 12,               //（可选项）数字类型；列表项子标题文字大小；默认：12
        subTitleColor: '#000',          //（可选项）字符串类型：列表项子标题文字颜色，支持rgb、rgba、#；默认：'#000000' 
        remarkColor: '#000',            //（可选项）字符串类型；备注的文字颜色，支持rgb、rgba、#；默认：'#000000'
        remarkSize: 16,                 //（可选项）数字类型；备注的文字大小；默认：16
        remarkIconWidth: 30              //（可选项）数字类型；当备注是图片时，图片的宽度，图片为正方形；默认：30
    }
}
```

fixedOn:

- 类型：字符串
- 描述：（可选项）模块所属 Frame 的名字，若不传则模块归属于当前 Window

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    eventType: 'show',  //字符串类型；交互事件类型
                        //取值范围如下：
	                    //show（模块加载成功）
                        //clickRightBtn（点击侧滑出现的右侧按钮）
                        //clickContent（点击列表项的内容，除了配图和备注以外的区域）
                        //clickImg（点击列表项的配图）
                        //clickRemark（点击列表项右侧备注）
	index: 0,           //数字类型；列表项的索引
	btnIndex: 0         //数字类型；列表项侧滑出现的按钮的索引
}
```

##示例代码

```js
var obj = api.require('UIListView');
obj.open({
    rect: {
        x: 0,
        y: 0,
        w: 320,
        h: 480
    },
    data: [{
        uid: '1001',    //开发者自定义的唯一标识
        imgPath: 'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
        title: '标题',
        subTitle: '子标题，说明文字',
        remark: '备注',
        icon: ''
    },{
        imgPath: 'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
        title: '标题',
        subTitle: '子标题，说明文字',
        remark: '备注',
        icon: ''
    }],
    rightBtns: [{
        bgColor: '#388e8e',
        activeBgColor: '',
        width: 70,
        title: '按钮',
        titleSize: 12,
        titleColor: '#fff',
        icon: '',
        iconWidth: 20
    }],
    styles: {
        borderColor: '#696969',
        item: {
            bgColor: '#AFEEEE',
            activeBgColor: '#F5F5F5',
            height: 55.0,
            imgWidth: 40,
            imgHeight: 40,
            placeholderImg: '',
            titleSize: 12.0,
            titleColor: '#000',
            subTitleSize: 12.0,
            subTitleColor: '#000', 
            remarkColor: '#000',
            remarkSize: 16,
            remarkIconWidth: 30
        }
    },
    fixedOn: ''
}, function(ret){
    alert(JSON.stringify(ret));
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m6"></div>
#**close**

关闭数据列表模块

close()

##示例代码

```js
var obj = api.require('UIListView');
obj.close();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m15"></div>
#**show**
 
显示 UIListView 模块
 
show()
 
##示例代码
 
```js    
var obj = api.require('UIListView');
obj.show();
```
 
##可用性
 
iOS系统，Android系统
 
可提供的1.0.0及更高版本

<div id="m14"></div>
#**hide**
 
隐藏 UIListView 模块

hide()
 
##示例代码
 
```js
var obj = api.require('UIListView');
obj.hide();
```
 
##可用性
 
iOS系统，Android系统
 
可提供的1.0.0及更高版本

<div id="m2"></div>
#**setAttr**

设置列表的纵坐标和高度

setAttr({params}, callback(ret, err))

##params

y：

- 类型：数字
- 描述：（可选项）模块的纵坐标
- 默认值：原 y 值

h：

- 类型：数字
- 描述：（可选项）模块的高度
- 默认值：原 h 值

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true       //布尔型；true||false
}
```

##示例代码

```js
var obj = api.require('UIListView');
obj.setAttr({
    y: 40,
    h: 200
}, function(ret){
    alert('设置成功');
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m3"></div>
#**getIndex**

根据开发者自定义的唯一标识（open 接口的 data 参数中自定义的唯一标识）查找列表项对应的数据

getIndex({params}, callback(ret,err))

##params

key：

- 类型：字符串
- 描述：调用 open 接口时，data 参数传入的开发者自定义的唯一标识的 key

value：

- 类型：字符串
- 描述：调用 open 接口时，data 参数传入的开发者自定义的唯一标识的 value

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    index: 0,   //数字类型；当前列表项的索引
    data: []    //数组类型；当前列表项的数据，内部字段与 open 时的 data 参数一致
}
```

##示例代码

```js
var obj = api.require('UIListView');
obj.getIndex({
    key: "uid",
    value: "1001"
}, function(ret){
    alert(JSON.stringify(ret));
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m4"></div>
#**getDataByIndex**

根据列表项的索引获取对应的数据

getDataByIndex({params}, callback(ret,err))

##params

index：

- 类型：数字
- 描述：（可选项）列表项的索引
- 默认值：0

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	data: []    //数组类型；当前列表项的数据，内部字段与 open 时的 data 参数一致
}
```

##示例代码

```js
var obj = api.require('UIListView');
obj.getDataByIndex({
	index: 0
},function(ret){
	alert(JSON.stringify(ret.data));
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m5"></div>
#**setSwipeBtns**

设置侧滑显示出来的按钮

setSwipeBtns({params}, callback(ret,err))

##params

index：

- 类型：数字
- 描述：（可选项）列表项的索引
- 默认值：0

btns：

- 类型：数组
- 描述：（可选项）列表项侧滑露出的按钮组
- 内部字段：

```js
[{
    bgColor: '#388e8e', //（可选项）字符串类型；按钮背景色，支持rgb、rgba、#；默认：'#388e8e'
    activeBgColor: '',  //（可选项）字符串类型；按钮按下时的背景色，支持rgb、rgba、#
    width: 70,          //（可选项）数字类型；按钮的宽度；默认：w / 4       
    title: '',          //（可选项）字符串类型；按钮标题，水平、垂直居中
    titleSize: 12,      //（可选项）数字类型；按钮标题文字大小；默认：12
    titleColor: '#fff', //（可选项）字符串类型；按钮标题文字颜色，支持rgb、rgba、#；默认：'#ffffff'
    icon: '',           //（可选项）字符串类型；按钮标题前的图标路径（本地路径，支持fs://，widget://），水平、垂直居中，图标为正方形
    iconWidth: 20       //（可选项）数字类型；按钮标题前的图标宽度，图标为正方形；默认：20
}]
```

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true       //布尔型；true||false
}
```

##示例代码

```js
var obj = api.require('UIListView');
obj.setSwipeBtns({
    index: 0,
    btns: [{
        bgColor: '#388e8e',
        activeBgColor: '',
        width: 70,
        title: '',
        titleSize: 12,
        titleColor: '#fff',
        icon: '',
        iconWidth: 20
    }]
}, function(ret){
    alert('设置成功');
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m7"></div>
#**reloadData**

刷新列表数据

reloadData({params}, callback(ret,err))

##params

data：

- 类型：数组
- 描述：（可选项）列表的数据源，**若不传或传空，仅收起下拉刷新组件**
- 内部字段：

```js
[{
    imgPath: '',            //（可选项）字符串类型；列表项的配图路径，支持http://、https://、widget://、fs://等协议，网络图片会被缓存到本地，若不传则标题和子标题靠最左侧显示
    title: '',              //（可选项）字符串类型；标题，若不传或为空则 subTitle 上下位置居中显示
    subTitle: '',           //（可选项）字符串类型；子标题，若不传或为空则 title 上下位置居中显示
    remark: '',             //（可选项）字符串类型；右边备注文字
    icon: '',               //（可选项）字符串类型；右侧备注的图标路径（本地路径，支持fs://，widget://）
    rightBtns: []           //（可选项）数组类型；列表项向左滑动露出的按钮组，配置某一项的特定按钮组，若不传则显示通用按钮，内部字段同 rightBtns 参数
}]
```

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true        //布尔型；true||false     
}
```

##示例代码

```js
var obj = api.require('UIListView');
obj.reloadData({
	 data:[{
        imgPath: 'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
        title: '新标题',
        subTitle: '新子标题',
        remark: '新备注',
        icon: ""
    }]
},function(ret){
    if(ret.status){
        alert('刷新数据成功');
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
 
<div id="m8"></div>
#**deleteItem**

根据索引删除某一条列表的数据

deleteItem({params}, callback(ret, err))

##params

index：

- 类型：数字
- 描述：（可选项）数据列表的索引
- 默认值：0

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true       //布尔型；true||false
}
```

##示例代码

```js
var obj = api.require('UIListView');
obj.deleteItem({
    index: 2
},function(ret){
    if(ret.status){
        alert('删除成功');
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
 
<div id="m9"></div>
#**updateItem**

根据索引更新某一条列表的数据

updateItem({params}, callback(ret, err))

##params

index：

- 类型：数字
- 描述：（可选项）数据列表的索引
- 默认值：0

data：

- 类型：JSON对象
- 描述：列表的数据源
- 内部字段：

```js
{
	imgPath: '',            //（可选项）字符串类型；列表项的配图路径，支持http://、https://、widget://、fs://等协议，网络图片会被缓存到本地，若不传则标题和子标题靠最左侧显示
    title: '',              //（可选项）字符串类型；标题，若不传或为空则 subTitle 上下位置居中显示
    subTitle: '',           //（可选项）字符串类型；子标题，若不传或为空则 title 上下位置居中显示
    remark: '',             //（可选项）字符串类型；右边备注文字
    icon: '',               //（可选项）字符串类型；右侧备注的图标路径（本地路径，支持fs://，widget://）
    rightBtns: []           //（可选项）数组类型；列表项向左滑动露出的按钮组，配置某一项的特定按钮组，若不传则显示通用按钮，内部字段同 rightBtns 参数
}
```

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true     //布尔型；true||false
}
```

##示例代码

```js
var obj = api.require('UIListView');
obj.updateItem({
    index: 2,
    data: {
        imgPath: 'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
        title: '刷新标题', 
        subTitle: '刷新子标题',
        remark: '刷新备注'
    }
}, function(ret){
    if(ret.status){
        alert('刷新列表数据成功');
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
 
<div id="m10"></div>
#**insertItem**

根据索引向某一条列表插入数据

insertItem({params}, callback(ret, err))

##params

index：

- 类型：数字
- 描述：（可选项）数据列表的索引
- 默认值：列表最后一条数据的索引

data：

- 类型：JSON对象
- 描述：列表的数据源
- 内部字段：

```js
{
    imgPath: '',            //（可选项）字符串类型；列表项的附图路径，支持http://、https://、widget://、fs://等协议，网络图片会被缓存到本地，若不传则标题和子标题靠最左侧显示
    title: '',              //（可选项）字符串类型；标题，若不传或为空则 subTitle 上下位置居中显示
    subTitle: '',           //（可选项）字符串类型；子标题，若不传或为空则 title 上下位置居中显示
    remark: '',             //（可选项）字符串类型；右边备注文字
    icon: '',               //（可选项）字符串类型；右侧备注的图标路径（本地路径，支持fs://，widget://）
    rightBtns: []           //（可选项）数组类型；列表项向左滑动露出的按钮组，配置某一项的特定按钮组，内部字段同 open 接口的 rightBtns 参数
}
```

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true          //布尔型；true||false
}
```

##示例代码

```js
var obj = api.require('UIListView');
obj.insertItem({
    index: 2,
    data: {
        imgPath: 'http://d.hiphotos.baidu.com/image/pic/item/4d086e061d950a7b29a788c209d162d9f2d3c922.jpg',
        title: '12:00',
        subTitle: 'APICloud粉丝互动会',
        remark: '完成'
    }
},function(ret){
    if(ret.status){
        alert('插入数据成功');
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
 
<div id="m11"></div>
#**appendData**
 
向列表末端追加数据
 
appendData({params}, callback(ret, err))
 
##params
 
data：

- 类型：数组对象
- 描述：列表的数据源，**若不传或传空，仅收起上拉加载组件**
- 内部字段：

```js
[{
    imgPath: '',            //（可选项）字符串类型；列表项的附图路径，支持http://、https://、widget://、fs://等协议，网络图片会被缓存到本地，若不传则标题和子标题靠最左侧显示
    title: '',              //（可选项）字符串类型；标题，若不传或为空则 subTitle 上下位置居中显示
    subTitle: '',           //（可选项）字符串类型；子标题，若不传或为空则 title 上下位置居中显示
    remark: '',             //（可选项）字符串类型；右边备注文字
    icon: '',               //（可选项）字符串类型；右侧备注的图标路径（本地路径，支持fs://，widget://）
    rightBtns: []           //（可选项）数组类型；列表项向左滑动露出的按钮组，配置某一项的特定按钮组，内部字段同 open 接口的 rightBtns 参数
}]
```
 
##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true        //布尔型；true||false
}
```

##示例代码
 
```js
var obj = api.require('UIListView');
obj.appendData({
    data: [{
        imgPath: 'http://d.hiphotos.baidu.com/image/pic/item/4d086e061d950a7b29a788c209d162d9f2d3c922.jpg',
        title: '新增标题',
        subTitle: '新增子标题',
        remark: '新增备注'
    }]
},function(ret){
    if(ret.status){
        alert('追加数据成功');
    }
});
```
 
##可用性
 
iOS系统，Android系统
 
可提供的1.0.0及更高版本

<div id="m12"></div>
#**setRefreshHeader**
 
设置下拉刷新，**通过 reloadData 收起下拉刷新组件**
 
setRefreshHeader({params}, callback(ret, err))
 
##params
 
loadingImg：
 
- 类型：字符串
- 描述：下拉刷新时显示的小箭头图标的本地路径，要求本地路径（fs://，widget://）
 
bgColor：
 
- 类型：字符串
- 描述：（可选项）下拉刷新区域的背景色，支持rgb、rgba、#
- 默认值：'#f5f5f5'
 
textColor：
 
- 类型：字符串
- 描述：（可选项）提示文字颜色，支持rgb、rgba、#
- 默认值：'#8e8e8e'
 
textDown：
 
- 类型：字符串
- 描述：（可选项）下拉提示文字
- 默认值：下拉可以刷新...
 
textUp：
 
- 类型：字符串
- 描述：（可选项）松开提示文字
- 默认值：松开开始刷新...
 
 
showTime：
 
- 类型：布尔值
- 描述：（可选项）是否显示刷新时间
- 默认值：true
 
 
##callback(ret, err)
 
下拉刷新的事件回调
 
##示例代码
 
```js
var obj = api.require('UIListView');
obj.setRefreshHeader({
    loadingImg: 'widget://res/UIListView_arrow.png',
    bgColor: '#F5F5F5',
    textColor: '#8E8E8E',
    textDown: '下拉可以刷新...',
    textUp: '松开开始刷新...',
    showTime: true
},function(ret, err){
    
});
```
 
##可用性
 
iOS系统，Android系统
 
可提供的1.0.0及更高版本

<div id="m13"></div>
#**setRefreshFooter**
 
设置上拉加载，**通过 appendData 收起上拉加载组件**
 
setRefreshFooter({params}, callback(ret, err))
 
##params
 
loadingImg：
 
- 类型：字符串
- 描述：上拉加载时显示的小箭头图标的本地路径，要求本地路径（fs://，widget://）
 
bgColor：
 
- 类型：字符串
- 描述：（可选项）上拉加载区域的背景色，支持rgb、rgba、#
- 默认值：'#f5f5f5'
 
textColor：
 
- 类型：字符串
- 描述：（可选项）提示文字颜色，支持rgb、rgba、#
- 默认值：'#8e8e8e'
 
textUp：
 
- 类型：字符串
- 描述：（可选项）上拉提示文字
- 默认值：'上拉加载更多...'
 
textDown：
 
- 类型：字符串
- 描述：（可选项）松开提示文字
- 默认值：'松开开始加载...'

showTime：
 
- 类型：布尔值
- 描述：（可选项）是否显示刷新时间
- 默认值：true
 
##callback(ret, err)
 
上拉加载的事件回调
 
##示例代码
 
```js      
var obj = api.require('UIListView');
obj.setRefreshFooter({
    loadingImg: 'widget://res/UIListView_arrow.png',
    bgColor: '#F5F5F5',
    textColor: '#8E8E8E',
    textUp: '上拉加载更多...',
    textDown: '松开开始加载...',
    showTime: true
},function(ret, err){
    
});
 
```
 
##可用性
 
iOS系统，Android系统
 
可提供的1.0.0及更高版本

