/*
Title: goodsList
Description: goodsList
*/

<p style="color: #ccc;margin-bottom: 30px;">来自于：开发者</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[setFrame](#2)

[getIndex](#3)

[getData](#4)

[setRightButtons](#5)

[close](#6)

[reloadData](#7)

[deleteItem](#8)

[insertItem](#9)

[refreshItem](#10)

[appendData](#11)

[setRefreshHeader](#12)

[setRefreshFooter](#13)

[show](#14)

[hide](#15)
</div>

#**概述**

goodsList 封装了一个列表控件，可实现一个可左右拖动 item 的列表视图。开发者可根据需求自定义列表的元素布局，亦可自定义相关字段的样式。支持设置下拉刷新和上拉加载更多事件。支持删除、刷新、插入指定下标（index）的 item 数据。可动态设置 item 侧滑按钮图标、头像。可设置头像标签。本模块是由第三方模块开发者提供，使用本模块需在线云编译安装包。

#**open**<div id="1"></div>

打开

open({params}, callback(ret, err))

##params

x：

- 类型：数字
- 默认值：0
- 描述：（可选项）列表视图的左上角点的坐标

y：

- 类型：数字
- 默认值：0
- 描述：（可选项）列表视图的左上角点的坐标

w：

- 类型：数字
- 默认值：当前设备屏幕宽度
- 描述：列表视图的宽，可为空

h：

- 类型：数字
- 默认值：w+100
- 描述：（可选项）列表视图的高

itemStyle：

- 类型：JSON 对象
- 默认值：见内部字段
- 描述：（可选项）item 样式配置
- 内部字段：

```js
{
    borderColor:   //（可选项）item间分割线颜色，支持 rgb，rgba，#，默认#696969
    bgColor:       //（可选项）item背景色，支持 rgb，rgba，#，默认#AFEEEE
    selectedColor  //（可选项）item背景选中色,支持 rgb，rgba，#，默认#f5f5f5
    height:        //（可选项）一条item的高度，数字类型，默认55
    avatarH：      //（可选项）头像（上下居中）的高(不可超过height)，数字类型，默认45
    avatarW:       //（可选项）头像（距左边框距离和上下相等）的宽，数字类型，默认45
    placeholderImg //（可选项）头像为网络资源时的占位图,仅支持本地路径协议,有默认图标
    titleSize：    //（可选项）标题字体大小，数字类型，默认16
    titleColor     //（可选项）标题字体颜色，支持 rgb,rgba,#，默认：#000000
    subTitleSize   //（可选项）子标题字体大小，数字类型，默认13
    subTitleColor  //（可选项）子标题字体颜色，支持 rgb,rgba,#，默认：#696969
    markSize：     //（可选项）小标题字体大小，数字类型，默认13
    markColor：    //（可选项）小标题字体颜色，支持 rgb,rgba,#，默认：#ff0000
    itemSlipDistance//（可选项）item侧滑距离占列表视图宽度的百分比，默认50
    tagHeight       //（可选项）item头像上的标签占头像的高度百分比，数字类型，取值范围 0-100，默认17
    tagBg           //（可选项）item头像上的标签背景设置，字符串类型，支持 rgb、rgba、#，默认rgba(69,69,69,0.5)
    tagSize        //（可选项）item头像上的标签字体大小，数字类型，默认13
    tagColor       //（可选项）item头像上的标签字体颜色，字符串类型，支持 rgb、rgba、#，默认#696969
    rightBgColor   //（可选项）往左滑动item露出的视图的背景色，支持 rgb、rgba、#，默认#696969
    interval：      //（可选项）每条item之间的间距，数据类型，默认6.0
}
```

datas：

- 类型：数组对象
- 默认值：无
- 描述：列表数据源
- 内部字段：

```js
[{
   img:       //（可选项）头像图片路径,支持本地和网络路径资源,网络图片会被缓存到本地
   title:     //（可选项）标题，字符串类型，不传或传空时不显示
   subTitle   //（可选项）子标题，字符串类型，不传或传空时不显示
   mark:      //（可选项）子标题，字符串类型，不传或传空时不显示 
   tag：      //（可选项）头像上的标签，字符串类型，不传或传空时不显示
   rightBtn：	//（可选项）数组对象,往左滑动item露出的按钮信息组成的数组，无默认值，不传或传空时表示item不可向左滑动
				内部字段：
				[{
					bg:         	//（可选项）按钮背景色，支持 rgb，rgba，#，默认#388e8e
					title:         	//（可选项）按钮标题，字符串类型，默认空字符串
					titleSize:      //（可选项）按钮标题字体大小，数字类型，默认12
					titleColor:     //（可选项）按钮标题颜色，支持 rgb，rgba，#，默认#ffffff
					highlightColor: //（可选项）按钮选中时的颜色值,支持 rgb，rgba，#，默认无
					icon          	//（可选项）按钮标题前图标图片路径，图标大小20*20，默认无，支持本地协议路径，如widget：//、fs://等
				}]
}]
```

fixedOn：

- 类型：字符串
- 默认值：当前主窗口的名字
- 描述：（可选项）将此模块视图添加到指定窗口的名字

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
    eventType:      	 //事件类型，取值范围如下：
                            rightBtn   //点击右边按钮
                            content：  //点击的item内容
                            avatar：   //点击的item的头像
    index:             //点击item的下标
    data：             //当前操作的item的数据，内部字段与open里datas元素一致
    rightBtn：         //点击item下的侧滑按钮，eventType非rightBtn时此字段无意义
           内部字段：{
             index：   //按钮下标，数字类型，从右向左顺序排列
             selected：//布尔类型，按钮点击状态，true为点击状态，false为取消点击/未点击状态
            }
}
```

##示例代码

```js

var goodsList = api.require('goodsList');

var datas = []; // 数据源.

var imgs = ['widget://image/goodsList/avatar.png',
    'widget://image/goodsList/avatar.png',
    'widget://image/goodsList/avatar.png',
    'widget://image/goodsList/avatar.png',
    'http://abfc6f80482f86f9ccf4.b0.upaiyun.com/apicloud/948bec8a4df2adb27581319d8a8c014e.png',
    'http://abfc6f80482f86f9ccf4.b0.upaiyun.com/apicloud/3cd8bd01f9f474664ff0b2f41611797e.png',
    'http://abfc6f80482f86f9ccf4.b0.upaiyun.com/apicloud/5b67af4da9ce31f101c3326fbef10e5e.png',
    'http://abfc6f80482f86f9ccf4.b0.upaiyun.com/apicloud/3531bbb5db7f920a4f17887449aa5d7d.png',
    'http://abfc6f80482f86f9ccf4.b0.upaiyun.com/apicloud/cbf1074f44df8e0f40ca277e31f559ce.png',
    'http://abfc6f80482f86f9ccf4.b0.upaiyun.com/apicloud/87a9ad42f49140f1168b0caebf0cb6c3.png',
    'http://abfc6f80482f86f9ccf4.b0.upaiyun.com/apicloud/da1cdf8ecba5775f8b54f12cd2a00735.png',
    'http://abfc6f80482f86f9ccf4.b0.upaiyun.com/apicloud/a4db2d1809fa57cc91d0173e1c33caf9.png',
    'http://abfc6f80482f86f9ccf4.b0.upaiyun.com/apicloud/3e0afb28a7cb0437ea860087cef39fd3.png',
    'http://abfc6f80482f86f9ccf4.b0.upaiyun.com/apicloud/893e222cdd8158391f7a01aee3723784.png',
    'http://abfc6f80482f86f9ccf4.b0.upaiyun.com/apicloud/59ea90c458f3708279de79b0c7a60693.png',
    'http://abfc6f80482f86f9ccf4.b0.upaiyun.com/apicloud/69bff6064593e92c8e4102f174d0bdbf.png',
    'http://abfc6f80482f86f9ccf4.b0.upaiyun.com/apicloud/ca2aa9b8246bc0bfd97ba284dc087e62.png',
    'http://file.apicloud.com/mcm/A6965066817858/d7d1d308fe165b984c09728e7118e9f1.jpg',
    'http://file.apicloud.com/mcm/A6965066817858/83dede361c4597ccfe2d815a76a7b1c2.png',
    'http://file.apicloud.com/mcm/A6965066817858/f23301da3bd6c2c214a464b27c9897c2.jpg'];

for(var i = 0; i < 20; i ++){ // 使用1000条数据,进行极限测试.
    var data =     {
        uId:1000+i,
        img: imgs[i], // 头像图片路径,支持本地和网络路径
        title: '刘德华' + i, // 标题.
        subTitle: '100' + i, // 子标题.
        mark:'10' + i,
        tag:'支付' + i,
        rightBtn: [
            {
                bg:  '#556B2F',  //按钮背景色，支持 rgb，rgba，#，默认#ee8262.
                title: '结束', //按钮名字，字符串类型，默认‘按钮’
                titleSize: 13,      //按钮标题大小，默认12
                titleColor: '#000000', // 按钮标题颜色，支持 rgb，rgba，#，默认#ffffff
                selectedColor: '#FFFFFF',  //按钮选中时候的颜色值,支持 rgb，rgba，#
                icon:'widget://image/goodsList/delete.png'
            },
            {
                bg:  '#4EEE94',  //按钮背景色，支持 rgb，rgba，#，默认#ee8262.
                title: '取消置顶', //按钮名字，字符串类型，默认‘按钮’
                titleSize: 13,      //按钮标题大小，默认12
                titleColor: '#000000', // 按钮标题颜色，支持 rgb，rgba，#，默认#ffffff
                selectedColor: 'ffffff',  //按钮选中时候的颜色值,支持 rgb，rgba，#
                icon:'widget://image/goodsList/delete.png'
            }
        ] // 左滑单元格露出的按钮组.
    };
    datas.push(data);
}

goodsList.open({
    x: 0, // 横坐标, 默认 0.
    y: 64, // 纵坐标, 默认 0.
    w: 320, // 宽度, 默认设备屏幕宽度.
    h: 320, // 高度, 默认 视图高度 + 100.
    itemSlipDistance:60,
    datas: datas,
    itemStyle: {
            tagSize: 10,
            tagColor: 'rgba(255,0,0,0.5)',
            rightBgColor: 'rgba(0,0,0,0.5)',
            tagHeight: 30,
            height: 200,
            avatarH: 90,
            avatarW: 90
    }
}, function(ret, err){   
    if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##补充说明

打开列表视图

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**setFrame**<div id="2"></div>

重设模块视图的y，和h

setFrame({params})

##params

anim：

- 类型：布尔
- 默认值：false
- 描述：（可选项）改变模块视图的 frame 时是否添加动画效果

y：

- 类型：数字类型
- 默认值：无
- 描述：（可选项）重设模块视图的y值
- 备注：若不传则保持原值不变

h：

- 类型：数字类型
- 默认值：无
- 描述：（可选项）重设模块视图的h值
- 备注：若不传则保持原值不变


##示例代码

```
var goodsList = api.require('goodsList');
goodsList.setFrame({
	anim: true,
	y: 40
});
```js

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**getIndex**<div id="3"></div>

根据唯一标识查找该item在列表中的下标

getIndex({params}, callBack(ret, err))

##params

key：

- 类型：字符串
- 默认值：无
- 描述：唯一标识的 key

value：

- 类型：字符串
- 默认值：无
- 描述：每条 item 数据的唯一标识

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

	{
	    index:          	//点击item的下标
	    data：            //当前操作的item的数据，内部字段与open里datas元素一致
	}

##示例代码

```
var goodsList = api.require('goodsList');
goodsList.getIndex({
    key:'uid',
    value:'00000001'
}, function(ret, err){   
    if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```js

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**getData**<div id="4"></div>

根据 item 的索引获取 item 的数据

getData({params}, callBack(ret, err))

##params

index：

- 类型：数字
- 默认值：0
- 描述：（可选项）要获取数据的 item 的索引

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

	{
		data：//操作的item的data内部字段跟传进来的data一致
	}

##示例代码

```js
var goodsList = api.require('goodsList');
goodsList.getData({
  index: 0
}, function(ret, err){    
  if( ret ){
    alert( JSON.stringify( ret ) );
  }else{
    alert( JSON.stringify( err ) );
  }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setRightButtons**<div id="5"></div>

设置指定索引的 item 的侧滑按钮

setRightButtons({params})

##params

index：

- 类型：数字
- 默认值：0
- 描述：（可选项）要设置侧滑按钮的item的索引

rightBtn：

- 类型：数组对象
- 默认值：无
- 描述：（可选项）往左滑动item露出的按钮样式重设
- 备注：若不传或传空则表示item不可向左滑动
- 内部字段：

```js
	[{
		bg:         	   //（可选项）按钮背景色，支持 rgb，rgba，#，默认#388e8e
		title:         	 //（可选项）按钮标题，字符串类型，默认空字符串
		titleSize:       //（可选项）按钮标题字体大小，数字类型，默认12
		titleColor:      //（可选项）按钮标题颜色，支持 rgb，rgba，#，默认#ffffff
		highlightColor:  //（可选项）按钮选中时的颜色值,支持 rgb，rgba，#，默认无
		icon          	 //（可选项）按钮标题前图标图片路径，图标大小20*20，默认无，支持本地协议路径，如widget：//、fs://等
	}]
```

##示例代码

```js
var goodsList = api.require('goodsList');
goodsList.setRightButtons({
   index: 0,
   rightBtn: [{
     bg: '#556B2F',            //按钮背景色，支持 rgb，rgba，#，默认#ee8262.
     title: '取消',             //按钮名字，字符串类型，默认‘按钮’
     titleSize: 13,             //按钮标题大小，默认12
     titleColor: '#000000',     // 按钮标题颜色，支持 rgb，rgba，#，默认#ffffff
     selectedColor: '#FFFFFF',  //按钮选中时候的颜色值,支持 rgb，rgba，#
     icon:'widget://image/goodsList/ok.png'
   }, {
     bg: '#4EEE94',            //按钮背景色，支持 rgb，rgba，#，默认#ee8262.
     title: '确定',             //按钮名字，字符串类型，默认‘按钮’
     titleSize: 13,             //按钮标题大小，默认12
     titleColor: '#000000',     // 按钮标题颜色，支持 rgb，rgba，#，默认#ffffff
     selectedColor: 'ffffff',   //按钮选中时候的颜色值,支持 rgb，rgba，#
     icon:'widget://image/goodsList/ok.png'
   }]
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**close**<div id="6"></div>

关闭列表视图

close()

##示例代码

```js
var goodsList = api.require('goodsList');
goodsList.close();
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**reloadData**<div id="7"></div>

刷新列表数据

reloadData({params})

##params

datas：

- 类型：数组对象
- 默认值：无
- 描述：（可选项）列表数据源，若不传则仅停止下拉刷新状态

内部字段：

```js
[{
   img:       //（可选项）头像图片路径,支持本地和网络路径资源,网络图片会被缓存到本地
   title:     //（可选项）标题，字符串类型，不传或传空时不显示
   subTitle   //（可选项）子标题，字符串类型，不传或传空时不显示
   mark:      //（可选项）子标题，字符串类型，不传或传空时不显示 
   tag：      //（可选项）头像上的标签，字符串类型，不传或传空时不显示
   rightBtn：	//（可选项）数组对象,往左滑动item露出的按钮信息组成的数组，无默认值，不传或传空时表示item不可向左滑动
				内部字段：
				[{
					bg:         	//（可选项）按钮背景色，支持 rgb，rgba，#，默认#388e8e
					title:         	//（可选项）按钮标题，字符串类型，默认空字符串
					titleSize:      //（可选项）按钮标题字体大小，数字类型，默认12
					titleColor:     //（可选项）按钮标题颜色，支持 rgb，rgba，#，默认#ffffff
					highlightColor:  //（可选项）按钮选中时的颜色值,支持 rgb，rgba，#，默认无
					icon          	//（可选项）按钮标题前图标图片路径，图标大小20*20，默认无，支持本地协议路径，如widget：//、fs://等
				}]
}]
```

##示例代码

```js
var datas = []; // 数据源.

var imgs = ['http://abfc6f80482f86f9ccf4.b0.upaiyun.com/apicloud/e4dba38175efac7d07adcae8be8d1223.png',
    'http://abfc6f80482f86f9ccf4.b0.upaiyun.com/apicloud/9c212a6c2753103e4deed8aa47bda909.png',
    'http://abfc6f80482f86f9ccf4.b0.upaiyun.com/apicloud/be9ced29de96129b6a1e2f19c40de85e.png',
    'http://abfc6f80482f86f9ccf4.b0.upaiyun.com/apicloud/94a135721ae675fbccd2484f616a98e1.png',
    'http://abfc6f80482f86f9ccf4.b0.upaiyun.com/apicloud/948bec8a4df2adb27581319d8a8c014e.png',
    'http://abfc6f80482f86f9ccf4.b0.upaiyun.com/apicloud/3cd8bd01f9f474664ff0b2f41611797e.png',
    'http://abfc6f80482f86f9ccf4.b0.upaiyun.com/apicloud/5b67af4da9ce31f101c3326fbef10e5e.png',
    'http://abfc6f80482f86f9ccf4.b0.upaiyun.com/apicloud/3531bbb5db7f920a4f17887449aa5d7d.png',
    'http://abfc6f80482f86f9ccf4.b0.upaiyun.com/apicloud/cbf1074f44df8e0f40ca277e31f559ce.png',
    'http://abfc6f80482f86f9ccf4.b0.upaiyun.com/apicloud/87a9ad42f49140f1168b0caebf0cb6c3.png',
    'http://abfc6f80482f86f9ccf4.b0.upaiyun.com/apicloud/da1cdf8ecba5775f8b54f12cd2a00735.png',
    'http://abfc6f80482f86f9ccf4.b0.upaiyun.com/apicloud/a4db2d1809fa57cc91d0173e1c33caf9.png',
    'http://abfc6f80482f86f9ccf4.b0.upaiyun.com/apicloud/3e0afb28a7cb0437ea860087cef39fd3.png',
    'http://abfc6f80482f86f9ccf4.b0.upaiyun.com/apicloud/893e222cdd8158391f7a01aee3723784.png',
    'http://abfc6f80482f86f9ccf4.b0.upaiyun.com/apicloud/59ea90c458f3708279de79b0c7a60693.png',
    'http://abfc6f80482f86f9ccf4.b0.upaiyun.com/apicloud/69bff6064593e92c8e4102f174d0bdbf.png',
    'http://abfc6f80482f86f9ccf4.b0.upaiyun.com/apicloud/ca2aa9b8246bc0bfd97ba284dc087e62.png',
    'http://file.apicloud.com/mcm/A6965066817858/d7d1d308fe165b984c09728e7118e9f1.jpg',
    'http://file.apicloud.com/mcm/A6965066817858/83dede361c4597ccfe2d815a76a7b1c2.png',
    'http://file.apicloud.com/mcm/A6965066817858/f23301da3bd6c2c214a464b27c9897c2.jpg'];

for(var i = 0; i < 20; i ++){ // 使用1000条数据,进行极限测试.
    var data =     {
        uId:1000+i,
        img: imgs[i], // 头像图片路径,支持本地和网络路径
        title: '张学友' + i, // 标题.
        subTitle: '200' + i, // 子标题.
        mark:'20' + i,
        tag:'已支付',
        rightBtn: [
	        {
		        bg:  '#556B2F',  //按钮背景色，支持 rgb，rgba，#，默认#ee8262.
		        title: '结束', //按钮名字，字符串类型，默认‘按钮’
		        titleSize: 13,      //按钮标题大小，默认12
		        titleColor: '#000000', // 按钮标题颜色，支持 rgb，rgba，#，默认#ffffff
		        selectedColor: '#FFFFFF',  //按钮选中时候的颜色值,支持 rgb，rgba，#
		        icon:'widget://image/goodsList/delete.png'
	        },
	        {
		        bg:  '#4EEE94',  //按钮背景色，支持 rgb，rgba，#，默认#ee8262.
		        title: '取消置顶', //按钮名字，字符串类型，默认‘按钮’
		        titleSize: 13,      //按钮标题大小，默认12
		        titleColor: '#000000', // 按钮标题颜色，支持 rgb，rgba，#，默认#ffffff
		        selectedColor: 'ffffff',  //按钮选中时候的颜色值,支持 rgb，rgba，#
		        icon:'widget://image/goodsList/delete.png'
	        }
        ] // 左滑单元格露出的按钮组.
    };
    datas.push(data);
}
var goodsList = api.require('goodsList');
goodsList.reloadData({
   datas:datas
 });
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**deleteItem**<div id="8"></div>

删除指定索引的数据

deleteItem({params})

##params

index：

- 类型：数字
- 默认值：列表最后一条数据的索引
- 描述：（可选项）要删除的数据的索引

##示例代码

```js
var goodsList = api.require('goodsList');
goodsList.deleteItem({
   index:0
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**insertItem**<div id="9"></div>

插入指定索引的数据

insertItem({params})

##params

index：

- 类型：数字
- 默认值：无
- 描述：（可选项）要插入的数据的索引下标
- 备注：若不传或传空则拼接到最后一条数据

datas：

- 类型：数组对象
- 默认值：无
- 描述：列表数据源

内部字段：

```js
[{
   img:       //（可选项）头像图片路径,支持本地和网络路径资源,网络图片会被缓存到本地
   title:     //（可选项）标题，字符串类型，不传或传空时不显示
   subTitle   //（可选项）子标题，字符串类型，不传或传空时不显示
   mark:      //（可选项）子标题，字符串类型，不传或传空时不显示
   tag：      //（可选项）头像上的标签，字符串类型，不传或传空时不显示 
   rightBtn：	//（可选项）数组对象,往左滑动item露出的按钮信息组成的数组，无默认值，不传或传空时表示item不可向左滑动
	内部字段：
	[{
		bg:         	//（可选项）按钮背景色，支持 rgb，rgba，#，默认#388e8e
		title:         	//（可选项）按钮标题，字符串类型，默认空字符串
		titleSize:      //（可选项）按钮标题字体大小，数字类型，默认12
		titleColor:     	//（可选项）按钮标题颜色，支持 rgb，rgba，#，默认#ffffff
		highlightColor  //（可选项）按钮选中时的颜色值,支持 rgb，rgba，#，默认无
		icon          	//（可选项）按钮标题前图标图片路径，图标大小20*20，默认无，支持本地协议路径，如widget：//、fs://等
	}]
}]
```

##示例代码

```js
var goodsList = api.require('goodsList');
goodsList.insertItem({
    index:2,
    data:{
      uId:'00000000121',
      img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
      title:'123456',
      subTitle:'APICloud粉丝交流会',
      mark:'100',
      tag:'未支付',
      rightBtn: [
	      {
		      bg:  '#556B2F',            //按钮背景色，支持 rgb，rgba，#，默认#ee8262.
		      title: '结束',             //按钮名字，字符串类型，默认‘按钮’
		      titleSize: 13,             //按钮标题大小，默认12
		      titleColor: '#000000',     // 按钮标题颜色，支持 rgb，rgba，#，默认#ffffff
		      selectedColor: '#FFFFFF',  //按钮选中时候的颜色值,支持 rgb，rgba，#
		      icon:'widget://image/goodsList/delete.png'
	      },
	      {
		      bg:  '#4EEE94',            //按钮背景色，支持 rgb，rgba，#，默认#ee8262.
		      title: '取消置顶',         //按钮名字，字符串类型，默认‘按钮’
		      titleSize: 13,             //按钮标题大小，默认12
		      titleColor: '#000000',     // 按钮标题颜色，支持 rgb，rgba，#，默认#ffffff
		      selectedColor: 'ffffff',   //按钮选中时候的颜色值,支持 rgb，rgba，#
		      icon:'widget://image/goodsList/delete.png'
	      }
      ] // 左滑单元格露出的按钮组.
     }
 });
```
##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**refreshItem**<div id="10"></div>

刷新指定index条目的数据

refreshItem({params})

##params

index：

- 类型：数字
- 默认值：0
- 描述：（可选项）要刷新数据的 item 索引下标

datas：

- 类型：数组对象
- 默认值：无
- 描述：列表数据源

内部字段：

```js
[{
   img:       //（可选项）头像图片路径,支持本地和网络路径资源,网络图片会被缓存到本地
   title:     //（可选项）标题，字符串类型，不传或传空时不显示
   subTitle   //（可选项）子标题，字符串类型，不传或传空时不显示
   mark:      //（可选项）子标题，字符串类型，不传或传空时不显示 
   tag：      //（可选项）头像上的标签，字符串类型，不传或传空时不显示
}]
```

##示例代码

```js
var goodsList = api.require('goodsList');
 goodsList.refreshItem({
    index:2,
    data:{
      uId:'00000000121',
      img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
      title:'789708',
      subTitle:'-100',
      mark:'-10',
      tag:'未知'
    }
 });
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**appendData**<div id="11"></div>

往列表拼接数据

appendData({params})

##params

datas：

- 类型：数组对象
- 默认值：无
- 描述：（可选项）列表数据源，若不传则仅停止上拉加载更多状态

内部字段：

```js
[{
   img:       //（可选项）头像图片路径,支持本地和网络路径资源,网络图片会被缓存到本地
   title:     //（可选项）标题，字符串类型，不传或传空时不显示
   subTitle   //（可选项）子标题，字符串类型，不传或传空时不显示
   mark:      //（可选项）子标题，字符串类型，不传或传空时不显示
   tag：      //（可选项）头像上的标签，字符串类型，不传或传空时不显示 
   rightBtn：	//（可选项）数组对象,往左滑动item露出的按钮信息组成的数组，无默认值，不传或传空时表示item不可向左滑动
	内部字段：
	[{
		bg:         	    //（可选项）按钮背景色，支持 rgb，rgba，#，默认#388e8e
		title:         	  //（可选项）按钮标题，字符串类型，默认空字符串
		titleSize:        //（可选项）按钮标题字体大小，数字类型，默认12
		titleColor:     	//（可选项）按钮标题颜色，支持 rgb，rgba，#，默认#ffffff
		highlightColor    //（可选项）按钮选中时的颜色值,支持 rgb，rgba，#，默认无
		icon          	  //（可选项）按钮标题前图标图片路径，图标大小20*20，默认无，支持本地协议路径，如widget：//、fs://等
	}]
}]
```

##示例代码

```js
var goodsList = api.require('goodsList');
 goodsList.appendData({
  datas:[{
    uId:'00000000141',
    img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
    title:'APICloud',
    subTitle:'+100',
    mark:'+10',
    tag:'确定'
  },{
    uId:'00000000141',
    img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
    title:'APICloud',
    subTitle:'+100',
    mark:'+10',
    tag:'确定'
  },{
    uId:'00000000141',
    img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
    title:'APICloud',
    subTitle:'+100',
    mark:'+10',
    tag:'确定'
  },{
    uId:'00000000141',
    img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
    title:'APICloud',
    subTitle:'+100',
    mark:'+10',
    tag:'确定'
  }]
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setRefreshHeader**<div id="12"></div>

设置下拉刷新样式

setRefreshHeader({params}, callback(ret, err))

##params

loadingImg：

- 类型：字符串
- 默认值：无
- 描述：（可选项）下拉刷新的小箭头本地图片的路径

bgColor:

- 类型：字符串
- 默认值：#f5f5f5
- 描述：（可选项）下拉刷新视图的背景色，支持 rgb，rgba，#

textColor：

- 类型：字符串
- 默认值：#8e8e8e
- 描述：（可选项）提示文字颜色，支持 rgb，rgba，#

textDown：

- 类型;字符串
- 默认值：下拉可以刷新…
- 描述：（可选项）提示文字

textUp：

- 类型：字符串
- 默认值:松开开始刷新…
- 描述：（可选项）提示文字

showTime：

- 类型：布尔值
- 默认值：true
- 描述：（可选项）是否显示刷新时间

##callback(ret, err)

//触发下拉刷新事件

##示例代码

```js
var loadingImgae = 'widget://res/goodsList_arrow.png';//刷新的小箭头
var bgColor = '#F5F5F5';//下拉刷新的背景颜色，有默认值，可为空
var textColor= '#8E8E8E';//提示语颜色，有默认值，可为空
var textDown= '下拉可以刷新...';//尚未触发刷新时间的提示语，有默认值，可为空
var textUp= '松开开始刷新...';//触发刷新事件的提示语，有默认值，可为空
var showTime= true;//是否显示时间，有默认值，可为空
var goodsList = api.require('goodsList');
goodsList.setRefreshHeader({
   loadingImg : loadingImgae,
   bgColor:bgColor,
   textColor:textColor,
   textDown:textDown,
   textUp:textUp,
   showTime : showTime
},function(ret,err){
//触发加载事件
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setRefreshFooter**<div id="13"></div>

设置上拉加载更多样式

setRefreshFooter({params} ,callback(ret, err))

##callback(ret, err)

//触发加载更多事件

##params

loadingImg：

- 类型：字符串
- 默认值：无
- 描述：（可选项）上拉加载更多的小箭头本地图片的路径

bgColor:

- 类型：字符串
- 默认值：#f5f5f5
- 描述：（可选项）上拉加载视图的背景色，支持 rgb，rgba，#

textColor：

- 类型：字符串
- 默认值：#8e8e8e
- 描述：（可选项）提示文字颜色，支持 rgb，rgba，#

textDown：

- 类型;字符串
- 默认值：上拉可以加载更多…
- 描述：（可选项）提示文字

textUp：

- 类型：字符串
- 默认值:松开开始加载…
- 描述：（可选项）提示文字

showTime：

- 类型：布尔值
- 默认值：true
- 描述：（可选项）是否显示加载时间

##示例代码

```js
var loadingImgae = 'widget://res/goodsList_arrow.png';//刷新的小箭头
var bgColor = '#F5F5F5';//下拉刷新的背景颜色，有默认值，可为空
var textColor= '#8E8E8E';//提示语颜色，有默认值，可为空
var textDown= '上拉可加载更多...';//尚未触发刷新时间的提示语，有默认值，可为空
var textUp= '松开开始加载...';//触发刷新事件的提示语，有默认值，可为空
var showTime= true;//是否显示时间，有默认值，可为空
var goodsList = api.require('goodsList');
goodsList.setRefreshFooter({
   loadingImg : loadingImgae,
   bgColor:bgColor,
   textColor:textColor,
   textDown:textDown,
   textUp:textUp,
   showTime : showTime
},function(ret,err){
        //触发加载事件
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**show**<div id="14"></div>

显示goodsList列表视图

show()

##示例代码

	var goodsList = api.require('goodsList');
	goodsList.show();

##补充说明

显示已隐藏的列表视图

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**hide**<div id="15"></div>

隐藏goodsList列表视图

hide()

##示例代码

```js
var goodsList = api.require('goodsList');
goodsList.hide();
```

##补充说明

隐藏 goodsList，并没有从内存里清除

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本