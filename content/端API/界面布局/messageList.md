/*
Title: messageList
Description: messageList
*/

<p style="color: #ccc;margin-bottom: 30px;">来自于：开发者</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[setFrame](#2)

[setBadge](#3)

[showBadge](#4)

[hideBadge](#5)

[getIndex](#6)

[getData](#7)

[setTopItemStyle](#8)

[cancelTopItemStyle](#9)

[setRightButtons](#10)

[getTopStyleItems](#11)

[close](#12)

[reloadData](#13)

[deleteItem](#14)

[insertItem](#15)

[refreshItem](#16)

[appendData](#17)

[setRefreshHeader](#18)

[setRefreshFooter](#19)

[show](#20)

[hide](#21)

[slip](#22)
</div>

#**概述**

messageList 封装了一个列表控件，可实现一个可左右拖动 item 的列表视图。开发者可根据需求自定义列表的元素布局，亦可自定义相关字段的样式。支持设置下拉刷新和上拉加载更多事件。支持删除、刷新、插入指定下标（index）的item数据。可动态设置item侧滑按钮图标、头像 badge。本模块是由第三方模块开发者提供，使用本模块需在线云编译安装包。

#**open**<div id="1"></div>

打开

open({params}, callback(ret, err))

##params

x：

- 类型：数字
- 默认值：0
- 描述：列表视图的左上角点的坐标，可为空

y：

- 类型：数字
- 默认值：64
- 描述：列表视图的左上角点的坐标，可为空

w：

- 类型：数字
- 默认值：当前设备屏幕宽度
- 描述：列表视图的宽，可为空

h：

- 类型：数字
- 默认值：w+100
- 描述：列表视图的高，可为空

itemStyle：

- 类型：JSON 对象
- 默认值：见内部字段
- 描述：item样式配置，可为空
- 内部字段：

```js
{
	borderColor:  			//item间分割线颜色，支持 rgb，rgba，#，默认#696969，可为空
	bgColor:     			//item背景色，支持 rgb，rgba，#，默认#AFEEEE，可为空
    selectedColor 			//item背景选中色,支持 rgb，rgba，#，默认#f5f5f5可为空
    height:       			//一条item的高度，数字类型，默认55，可为空
    avatarH：				//头像（上下居中）的高(不可超过height)，数字类型，默认45，可为空
    avatarW:     			//头像（距左边框距离和上下相等）的宽，数字类型，默认45，可为空
	placeholderImg			//头像为网络资源时的占位图,仅支持本地路径协议,有默认图标，可为空
    titleSize：				//标题字体大小，数字类型，默认13，可为空
    titleColor     			//标题字体颜色，支持 rgb,rgba,#，默认：#696969,可为空
    subTitleSize   			//子标题字体大小，数字类型，默认13，可为空
    subTitleColor  			//子标题字体颜色，支持 rgb,rgba,#，默认：#000000,可为空
	badge：{					//头像徽章设置背景色，可为空
       	bg：					//背景设置，支持 rgb，rgba，#，默认#ff0000，可为空
       	size：     			//徽章上的字体大小，数字类型，默认10，可为空
        color：				//徽章上的字体颜色，支持支持 rgb，rgba，#，默认#000000，可为空
		xPercentage			//badge视图中心锚点坐标x在父视图（头像视图）的宽的百分比，数字类型，取值范围 0-100，默认100
       	yPercentage			//badge视图中心锚点坐标y在父视图（头像视图）的高的百分比，数字类型，取值范围 0-100，默认0
     }
	itemSlipDistance:		//向左滑动露出右边按钮时，item的滑动距离咱item宽的百分比，默认50，取值范围30-100，可为空
}
```

datas：

- 类型：数组对象
- 默认值：无
- 描述：数据源，可为空
- 内部字段：

```js
[{
	img:       	//头像图片路径,支持本地和网络路径资源,网络图片会被缓存到本地,可为空
	title:      //标题，字符串类型，可为空，为空时不显示
	subTitle    //子标题，字符串类型，可为空，为空时不显示
   	badge:     	//头像徽章，字符串类型，可为空，为空则不显示
 	icons：		//用户名后面的图标路径组成的数组,可为空,为空则不显示,支持本地图片
    rightBtn：	//数组对象,往左滑动item露出的按钮信息组成的数组，无默认值，可为空，为空时表示item不可向左滑动
				内部字段：
				[{
					bg:         	//按钮背景色，支持 rgb，rgba，#，默认#388e8e，可为空
					title:         	//按钮标题，字符串类型，默认空字符串，可为空
					titleSize:      //按钮标题字体大小，数字类型，默认12，可为空
					titleColor:     	//按钮标题颜色，支持 rgb，rgba，#，默认#ffffff，可为空
					highlightColor  //按钮选中时的颜色值,支持 rgb，rgba，#，可为空,为空则无选中变化
					icon          	//按钮标题前图标图片路径，图标大小20*20，默认无，可为空，支持本地协议路径，如widget：//、fs://等
				}]
}]
```

fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window

clearBg：

- 类型：布尔
- 默认值：false
- 描述：当列表数据为零时，是否将列表背景置为透明，可为空

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
    eventType:      	//事件类型，取值范围如下：
	                    rightBtn			//点击右边按钮
	                    content：			//点击的item内容
	                    avatar：			//点击的item的头像
    index:          	//用户所点击的item的下标
    data：			//当前操作的item的数据，内部字段与open里datas元素一致
  	rightBtn：		//点击item下的侧滑按钮，eventType非rightBtn时此字段无意义
					内部字段：
					{
						index：		//按钮下标，数字类型，从右向左顺序排列
						selected：	//布尔类型，按钮点击状态，true为点击状态，false为取消点击/未点击状态
					}
}
```

##示例代码

```js
var messageList = api.require('messageList');
var datas = []; // 数据源.
var imgs = ['widget://image/messageList/avatar.png',
    'widget://image/messageList/avatar.png',
    'widget://image/messageList/avatar.png',
    'widget://image/messageList/avatar.png',
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
        subTitle: 'apicloud粉丝见面会' + i, // 子标题.
        badge:i,
        icons:['widget://image/messageList/placeholder.png','widget://image/messageList/placeholder.png','widget://image/messageList/placeholder.png']
    };
    datas.push(data);
}
var dataT =     {
uId:1100,
title: '这是标题', // 标题.
subTitle: '这是子标题', // 子标题.
badge:'1'
};
datas.push(dataT);
var data =     {
uId:1101,
    img: imgs[4], // 头像图片路径,支持本地和网络路径
    title: '这是标题', // 标题.
    subTitle: '这是子标题',  // 子标题.
    badge:'2'
};
datas.push(data);
var data =     {
uId:1102,
img: imgs[4], // 头像图片路径,支持本地和网络路径
title: '这是标题', // 标题.
subTitle: '这是子标题', // 子标题.
badge:'3'
};
datas.push(data);
var data =     {
uId:1103,
img: imgs[4], // 头像图片路径,支持本地和网络路径
title: '这是标题', // 标题.
badge:'4'
};
datas.push(data);

messageList.open({
    x: 0, // 横坐标, 默认 0.
    y: 64, // 纵坐标, 默认 0.
    w: 320, // 宽度, 默认设备屏幕宽度.
    h: 320, // 高度, 默认视图高度 + 100.
    rightBtn: [
        {
            bg:  '#556B2F',  //按钮背景色，支持 rgb，rgba，#，默认#ee8262.
            title: '结束', //按钮名字，字符串类型，默认‘按钮’
            titleSize: 13,      //按钮标题大小，默认12
            titleColor: '#000000', // 按钮标题颜色，支持 rgb，rgba，#，默认#ffffff
            selectedColor: '#FFFFFF',  //按钮选中时候的颜色值,支持 rgb，rgba，#
            icon:'widget://image/messageList/delete.png'
        },
        {
            bg:  '#4EEE94',  //按钮背景色，支持 rgb，rgba，#，默认#ee8262.
            title: '取消置顶', //按钮名字，字符串类型，默认‘按钮’
            titleSize: 13,      //按钮标题大小，默认12
            titleColor: '#000000', // 按钮标题颜色，支持 rgb，rgba，#，默认#ffffff
            selectedColor: 'ffffff',  //按钮选中时候的颜色值,支持 rgb，rgba，#
            icon:'widget://image/messageList/delete.png'
        }
    ], // 左滑单元格露出的按钮组.
    itemStyle: {
        borderColor: '#696969', // 单元格间分割线颜色，支持 rgb，rgba，#，默认#696969
        bgColor: '#AFEEEE', // 单元格背景色，支持 rgb，rgba，#，默认#AFEEEE
        selectedColor: '#f5f5f5',  // item背景选中色,支持 rgb，rgba，#，默认#f5f5f5
        height: 65,       // 单元格高度，默认55
        avatarH: 45,    //头像的高度，默认45
        avatarW: 45,     //头像的宽度，默认45
        placeholderImg: 'widget://image/messageList/placeholder.png',//头像为网络资源时的占位图,仅支持本地路径协议,有默认图标，可为空
        titleSize: 15, //标题字体大小，默认13
        titleColor: '#000000', // 标题字体颜色，支持 rgb,rgba,#，默认：#696969
        subTitleSize: 10,  // 子标题字体大小，默认13
        subTitleColor: '#696969', // 子标题字体颜色，支持 rgb,rgba,#，默认：#000000
        badge:{
        bg:'#ff0000',
        size:12,
        color:'#ffffff'
        },
        itemSlipDistance:80
    }, // 单元格样式配置.
    datas: datas
},function(ret,err){
   alert(JSON.stringify(ret));
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
- 描述：改变模块视图的frame时是否添加动画效果,可为空

y：

- 类型：数字类型
- 默认值：无
- 描述：重设模块视图的y值，可为空，若为空，则保持原值不变

h：

- 类型：数字类型
- 默认值：无
- 描述：重设模块视图的h值，可为空，若为空，则保持原值不变

##示例代码

```js
var messageList = api.require('messageList');
messageList.setFrame({
	anim: true,
	y: 0
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setBadge**<div id="3"></div>

给item设置徽章

setBadge({params})

##params

index：

- 类型：数字
- 默认值：0
- 描述：要设置徽章的item的下标,可为空

value：

- 类型：字符串
- 默认值：无
- 描述：要设置徽章的内容，可为空，若为空，则清除徽章

##示例代码

```js
var messageList = api.require('messageList');
messageList.setBadge({
    index: 1,
    value: 'test'
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**showBadge**<div id="4"></div>

显示指定下标的 item 的徽章

showBadge({params})

##params

index：

- 类型：数字
- 默认值：0
- 描述：要设置徽章的 item 的下标,可为空

##示例代码

```js
var messageList = api.require('messageList');
messageList.showBadge({
    index: 1
});
```
##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**hideBadge**<div id="5"></div>

隐藏指定下标的item的徽章

hideBadge({params})

##params

index：

- 类型：数字
- 默认值：0
- 描述：要设置徽章的 item 的下标,可为空

##示例代码

```js
var messageList = api.require('messageList');
messageList.hideBadge({
    index: 1
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**getIndex**<div id="6"></div>

根据唯一标识查找该 item 在列表中的下标

getIndex({params}, callBack(ret, err))

##params

key：

- 类型：字符串
- 默认值：无
- 描述：唯一标识的 key,不可为空

value：

- 类型：字符串
- 默认值：无
- 描述：每条 item 数据的唯一标识,不可为空

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

	{
	    index:          	//点击item的下标
	    data：//当前操作的item的数据，内部字段与open里datas元素一致
	}

##示例代码

```js
var messageList = api.require('messageList');
messageList.getIndex({
    key: 'uid',
    value: '00000001'
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

#**getData**<div id="7"></div>

根据item的索引获取item的数据

getData({params}, callBack(ret, err))

##params

index：

- 类型：数字
- 默认值：0
- 描述：要获取数据的item的索引,可为空

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

	{
		data：//操作的item的data内部字段跟传进来的data一致
	}

##示例代码

```js
var messageList = api.require('messageList');
messageList.getData({
   index:0
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

#**setTopItemStyle**<div id="8"></div>

设置指定索引 index 的 item 的样式

setTopItemStyle({params})

##params

index：

- 类型：数字
- 默认值：0
- 描述：要设置的 item 的索引,可为空

itemStyle：

- 类型：JSON 对象
- 默认值：见内部字段
- 描述：item样式重设，可为空，为空则仅把该条item置为顶部

内部字段：

	{ 
		bgColor:           //item背景色，支持 rgb，rgba，#可为空，为空则显示open时的值
	    selectedColor      // item背景选中色,支持 rgb，rgba，#可为空，为空则显示open时的值
	}

#示例代码

```js
var messageList = api.require('messageList');
messageList.setTopItemStyle({
    index: 0,
    itemStyle: {
        bg: '#ff0000'
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**cancelTopItemStyle**<div id="9"></div>

取消指定索引 item 的置顶状态

cancelTopItemStyle({params})

##params

index：

- 类型：数字
- 默认值：0
- 描述：要取消置顶状态的 item 索引,可为空

##示例代码

```js
var messageList = api.require('messageList');
messageList.cancelTopItemStyle({
    index: 0
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setRightButtons**<div id="10"></div>

设置指定索引的item的侧滑按钮

setRightButtons({params})

##params

index：

- 类型：数字
- 默认值：0
- 描述：要设置侧滑按钮的item的索引,可为空

rightBtn：

- 类型：数组对象
- 默认值：无
- 描述：往左滑动item露出的按钮样式重设，可为空，为空时表示item不可向左滑动
- 内部字段：

```js
	[{
		bg:         	//按钮背景色，支持 rgb，rgba，#，默认#388e8e，可为空
	    title:         //按钮标题，字符串类型，默认空字符串，可为空
	    titleSize:      //按钮标题字体大小，数字类型，默认12，可为空
	    titleColor:     //按钮标题颜色，支持 rgb，rgba，#，默认#ffffff，可为空
	    highlightColor  //按钮选中时的颜色值,支持 rgb，rgba，#，可为空,为空则无选中变化
	    icon          //按钮标题前图标图片路径，图标大小自适应文字大小，默认无，可为空，支持本地协议路径，如widget：//、fs://等
	}]
```

##示例代码

```js
var messageList = api.require('messageList');
messageList.setRightButtons({
     index:0,
     rightBtn: [{
            bg:  '#556B2F',  //按钮背景色，支持 rgb，rgba，#，默认#ee8262.
            title: '取消', //按钮名字，字符串类型，默认‘按钮’
            titleSize: 13,      //按钮标题大小，默认12
            titleColor: '#000000', // 按钮标题颜色，支持 rgb，rgba，#，默认#ffffff
            selectedColor: '#FFFFFF',  //按钮选中时候的颜色值,支持 rgb，rgba，#
            icon:'widget://image/messageList/delete.png'
        }, {
            bg:  '#4EEE94',  //按钮背景色，支持 rgb，rgba，#，默认#ee8262.
            title: '取消置顶', //按钮名字，字符串类型，默认‘按钮’
            titleSize: 13,      //按钮标题大小，默认12
            titleColor: '#000000', // 按钮标题颜色，支持 rgb，rgba，#，默认#ffffff
            selectedColor: 'ffffff',  //按钮选中时候的颜色值,支持 rgb，rgba，#
            icon:'widget://image/messageList/delete.png'
        }]
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**getTopStyleItems**<div id="11"></div>

获取置顶状态样式的item的

getTopStyleItems(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：
	
	{
		datas：//所有置顶状态的item的数据，内部字段跟open接口里的datas一致
		indexs：//所有置顶状态的item的下标组成的数组，跟datas按序对应
	}

##示例代码

```js
var messageList = api.require('messageList');
messageList.getTopStyleItems(function(ret, err){      
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

#**close**<div id="12"></div>

关闭列表视图

close()

##示例代码

```js
var messageList = api.require('messageList');
messageList.close();
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**reloadData**<div id="13"></div>

刷新列表数据

reloadData({params})

##params

datas：

- 类型：数组对象
- 默认值：无
- 描述：数据源，可为空，为空时仅停止下拉刷新状态

内部字段：

```js
[{
   	img:       //头像图片路径,支持本地和网络路径资源,网络图片会被缓存到本地,可为空
   	title:       //标题，字符串类型，可为空，为空时不显示
   	subTitle    //子标题，字符串类型，可为空，为空时不显示
   	badge:     //头像徽章，字符串类型，可为空，为空则不显示
	icons：//用户名后面的图标路径组成的数组，可为空，为空则不显示
    rightBtn：//数组对象,往左滑动item露出的按钮信息组成的数组，无默认值，可为空，为空时表示item不可向左滑动
      内部字段：
	[{
		bg:         	//按钮背景色，支持 rgb，rgba，#，默认#388e8e，可为空
		title:         //按钮标题，字符串类型，默认空字符串，可为空
		titleSize:      //按钮标题字体大小，数字类型，默认12，可为空
		titleColor:     //按钮标题颜色，支持 rgb，rgba，#，默认#ffffff，可为空
		highlightColor  //按钮选中时的颜色值,支持 rgb，rgba，#，可为空,为空则无选中变化
		icon          //按钮标题前图标图片路径，图标大小20*20，默认无，可为空，支持本地协议路径，如widget：//、fs://等
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
        subTitle: 'apicloud见面会' + i, // 子标题.
        badge:1+i,
        icons:['widget://image/messageList/placeholder.png','widget://image/messageList/placeholder.png','widget://image/messageList/placeholder.png']
    };
    datas.push(data);
}
var messageList = api.require('messageList');
messageList.reloadData({
   datas:datas
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**deleteItem**<div id="14"></div>

删除指定索引的数据

deleteItem({params})

##params

index：

- 类型：数字
- 默认值：无
- 描述：要删除的数据的索引下标，可为空，为空则删除最后一条数据

##示例代码

```js
var messageList = api.require('messageList');
messageList.deleteItem({
    index: 0
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**insertItem**<div id="15"></div>

插入指定索引的数据

insertItem({params})

##params

index：

- 类型：数字
- 默认值：无
- 描述：要插入的数据的索引下标，可为空，为空则拼接到最后一条数据

data：

- 类型：JSON 对象
- 默认值：无
- 描述：数据源，不可为空

内部字段：

```js
{
   	img:       //头像图片路径,支持本地和网络路径资源,网络图片会被缓存到本地,可为空
   	title:       //标题，字符串类型，可为空，为空时不显示
   	subTitle    //子标题，字符串类型，可为空，为空时不显示
	badge:     //头像徽章，字符串类型，可为空，为空则不显示
	icons：//用户名后面的图标路径组成的数组，可为空，为空则不显示
	rightBtn：//数组对象,往左滑动item露出的按钮信息组成的数组，无默认值，可为空，为空时表示item不可向左滑动
      内部字段：
	[{
		bg:         	//按钮背景色，支持 rgb，rgba，#，默认#388e8e，可为空
		title:         //按钮标题，字符串类型，默认空字符串，可为空
		titleSize:      //按钮标题字体大小，数字类型，默认12，可为空
		titleColor:     //按钮标题颜色，支持 rgb，rgba，#，默认#ffffff，可为空
		highlightColor  //按钮选中时的颜色值,支持 rgb，rgba，#，可为空,为空则无选中变化
		icon          //按钮标题前图标图片路径，图标大小20*20，默认无，可为空，支持本地协议路径，如widget：//、fs://等
	}]

}
```

##示例代码

```js
var messageList = api.require('messageList');
messageList.insertItem({
    index: 2,
    data: {
        uId: '00000000121',
        img: 'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
        title: '123456',
        subTitle: 'APICloud粉丝交流会'
	}
});
```
##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**refreshItem**<div id="16"></div>

刷新指定index条目的数据

refreshItem({params})

##params

index：

- 类型：数字
- 默认值：无
- 描述：要刷新数据的item索引下标，可为空，为空则不刷新

data：

- 类型：JSON 对象
- 默认值：无
- 描述：数据源，不可为空

内部字段：

```js
{
	img:       //头像图片路径,支持本地和网络路径资源,网络图片会被缓存到本地,可为空为空则显示之前的头像
	title:       //标题，字符串类型，可为空，为空时不显示
	subTitle    //子标题，字符串类型，可为空，为空时不显示
	badge:     //头像徽章，字符串类型，可为空，为空则不显示
	icons：//用户名后面的图标路径组成的数组，可为空，为空则不显示
  	rightBtn：//数组对象,往左滑动item露出的按钮信息组成的数组，无默认值，可为空，为空时表示item不可向左滑动
      内部字段：
	[{
		bg:         	//按钮背景色，支持 rgb，rgba，#，默认#388e8e，可为空
		title:         //按钮标题，字符串类型，默认空字符串，可为空
		titleSize:      //按钮标题字体大小，数字类型，默认12，可为空
		titleColor:     //按钮标题颜色，支持 rgb，rgba，#，默认#ffffff，可为空
		highlightColor  //按钮选中时的颜色值,支持 rgb，rgba，#，可为空,为空则无选中变化
		icon          //按钮标题前图标图片路径，图标大小20*20，默认无，可为空，支持本地协议路径，如widget：//、fs://等
	}]
}
```

##示例代码

```js
var messageList = api.require('messageList');
messageList.refreshItem({
    index: 2,
    data: {
        uId: '00000000121',
        img: 'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
        title: '789708',
        subTitle: '粉丝交流会'
	}
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**appendData**<div id="17"></div>

往列表拼接数据

appendData({params})

##params

datas：

- 类型：数组对象
- 默认值：无
- 描述：数据源，可为空，为空时仅停止上拉加载更多状态

内部字段：

```js
[{
   	img:       //头像图片路径,支持本地和网络路径资源,网络图片会被缓存到本地,可为空
   	title:       //标题，字符串类型，可为空，为空时不显示
   	subTitle    //子标题，字符串类型，可为空，为空时不显示
   	badge:     //头像徽章，字符串类型，可为空，为空则不显示
	icons：//用户名后面的图标路径组成的数组，可为空，为空则不显示
    rightBtn：//数组对象,往左滑动item露出的按钮信息组成的数组，无默认值，可为空，为空时表示item不可向左滑动
      内部字段：
	[{
		bg:         	//按钮背景色，支持 rgb，rgba，#，默认#388e8e，可为空
		title:         //按钮标题，字符串类型，默认空字符串，可为空
		titleSize:      //按钮标题字体大小，数字类型，默认12，可为空
		titleColor:     //按钮标题颜色，支持 rgb，rgba，#，默认#ffffff，可为空
		highlightColor  //按钮选中时的颜色值,支持 rgb，rgba，#，可为空,为空则无选中变化
		icon          //按钮标题前图标图片路径，图标大小20*20，默认无，可为空，支持本地协议路径，如widget：//、fs://等
	}]
}]
```

##示例代码

```js
var messageList = api.require('messageList');
 messageList.appendData({
  datas:[{
      uId:'00000000141',
  img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
  title:'APICloud',
  subTitle:'APICloud粉丝交流会'
},{ 
      uId:'00000000140',
  img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
  title: 'APICloud',
  subTitle:'APICloud粉丝交流会'
},{
      uId:'00000000139',
  img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
  title: 'APICloud',
  subTitle:'APICloud粉丝交流会'
},{ 
      uId:'00000000138',
  img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
  title: 'APICloud',
  subTitle:'APICloud粉丝交流会'
},{
      uId:'00000000137',
  img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
  title: 'APICloud',
  subTitle:'APICloud粉丝交流会'
},{
      uId:'00000000136',
  img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
  title: 'APICloud',
  subTitle:'APICloud粉丝交流会'
},{
      uId:'00000000135',
  img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
  title: 'APICloud',
  subTitle:'APICloud粉丝交流会'
},{ 
      uId:'000000001334',
  img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
  title: 'APICloud',
  subTitle:'APICloud粉丝交流会'
},{
      uId:'00000000133',
  img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
  title: 'APICloud',
  subTitle:'APICloud粉丝交流会'
},{ 
      uId:'00000000132',
  img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
  title: 'APICloud',
  subTitle:'APICloud粉丝交流会'
},{ 
      uId:'00000000131',
  img:'http://img1.3lian.com/gif/more/11/201206/a5194ba8c27b17def4a7c5495aba5e32.jpg',
  title: 'APICloud',
  subTitle:'APICloud粉丝交流会'
    }]
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setRefreshHeader**<div id="18"></div>

设置下拉刷新样式

setRefreshHeader({params}, callback(ret, err))

##params

loadingImg：

- 类型：字符串
- 默认值：无
- 描述：下拉刷新的小箭头本地图片的路径，可为空，为空则不显示箭头图标

bgColor:

- 类型：字符串
- 默认值：#f5f5f5
- 描述：下拉刷新视图的背景色，支持 rgb，rgba，#，可为空

textColor：

- 类型：字符串
- 默认值：#8e8e8e
- 描述：提示文字颜色，支持 rgb，rgba，#，可为空

textDown：

- 类型;字符串
- 默认值：下拉可以刷新…
- 描述;提示文字，可为空

textUp：

- 类型：字符串
- 默认值:松开开始刷新…
- 描述;提示文字，可为空

showTime：

- 类型：布尔值
- 默认值：true
- 描述：是否显示刷新时间，可为空

##callback(ret, err)

//触发下拉刷新事件

##示例代码

```js
var loadingImgae = 'widget://res/messageList_arrow.png';//刷新的小箭头
var bgColor = '#F5F5F5';//下拉刷新的背景颜色，有默认值，可为空
var textColor= '#8E8E8E';//提示语颜色，有默认值，可为空
var textDown= '下拉可以刷新...';//尚未触发刷新时间的提示语，有默认值，可为空
var textUp= '松开开始刷新...';//触发刷新事件的提示语，有默认值，可为空
var showTime= true;//是否显示时间，有默认值，可为空
var messageList = api.require('messageList');
messageList.setRefreshHeader({
             loadingImg : loadingImgae,
             bgColor:bgColor,
             textColor:textColor,
             textDown:textDown,
             textUp:textUp,
             showTime : showTime
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

#**setRefreshFooter**<div id="19"></div>

设置上拉加载更多样式

setRefreshFooter({params}, callback(ret, err))

##callback(ret, err)

//触发加载更多事件

##params

loadingImg：

- 类型：字符串
- 默认值：无
- 描述：上拉加载更多的小箭头本地图片的路径，可为空，为空则不显示该图标

bgColor:

- 类型：字符串
- 默认值：#f5f5f5
- 描述：上拉加载视图的背景色，支持 rgb，rgba，#，可为空

textColor：

- 类型：字符串
- 默认值：#8e8e8e
- 描述：提示文字颜色，支持 rgb，rgba，#，可为空

textDown：

- 类型;字符串
- 默认值：上拉可以加载更多…
- 描述;提示文字，可为空

textUp：

- 类型：字符串
- 默认值:松开开始加载…
- 描述;提示文字，可为空

showTime：

- 类型：布尔值
- 默认值：true
- 描述：是否显示加载时间，可为空

##示例代码

```js
var loadingImgae = 'widget://res/messageList_arrow.png';//刷新的小箭头
var bgColor = '#F5F5F5';//下拉刷新的背景颜色，有默认值，可为空
var textColor= '#8E8E8E';//提示语颜色，有默认值，可为空
var textDown= '上拉可加载更多...';//尚未触发刷新时间的提示语，有默认值，可为空
var textUp= '松开开始加载...';//触发刷新事件的提示语，有默认值，可为空
var showTime= true;//是否显示时间，有默认值，可为空
var messageList = api.require('messageList');
messageList.setRefreshFooter({
    loadingImg : loadingImgae,
    bgColor:bgColor,
    textColor:textColor,
    textDown:textDown,
    textUp:textUp,
    showTime: showTime
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


#**show**<div id="20"></div>

显示messageList列表视图

show()

##示例代码

```js
var messageList = api.require('messageList');
messageList.show();
```

##补充说明

显示已隐藏的列表视图

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

#**hide**<div id="21"></div>

隐藏messageList列表视图

hide()

##示例代码

```js
var messageList = api.require('messageList');
messageList.hide();
```

##补充说明

隐藏messageList，并没有从内存里清除

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

#**slip**<div id="22"></div>

禁止/打开item向左滑动功能

slip()

forbid：

- 类型：布尔类型
- 默认值：true
- 描述：（可选项）是否禁用item侧滑


##示例代码

```js
var messageList = api.require('messageList');
messageList.slip();
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本