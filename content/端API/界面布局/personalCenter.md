/*
Title: personalCenter
Description: personalCenter
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[updateValue](#2)

[close](#3)

[setSelect](#4)

[show](#5)

[hide](#6)
</div>

#**概述**

personalCenter是一个带有图片模糊效果的个人信息展示中心，开发者只需配置相关接口参数即可实现一个原生效果的个人展示中心

![图片说明](/img/docImage/personalCenter.jpg)

#**open**<div id="1"></div>

打开个人中心

open({params},callback(ret,err))

##params

y ：

- 类型：数字
- 默认值：0
- 描述：（可选项）个人中心视图上边距屏幕位置

<del>height ：</del>

- <del>类型：数字</del>
- <del>默认值：220</del>
- <del>描述：视图的高，可为空</del>

h ：

- 类型：数字
- 默认值：220
- 描述：（可选项）视图的高

imgPath：

- 类型：字符串
- 默认值：无
- 描述：头像图片的路径（如果为网络路径,图片会被缓存到本地），支持http，https，widget，file，fs协议

<del>placeHoldImg：</del>

- <del>类型：字符串</del>
- <del>默认值：无</del>
- <del>描述：头像占位图片的路径，支持widget，file，fs协议，可为空</del>

placeholderImg：

- 类型：字符串
- 默认值：无
- 描述：（可选项）头像占位图片的路径，支持widget，file，fs协议

<del>username ：</del>

- <del>类型：字符串</del>
- <del>默认值：username</del>
- <del>描述：用户名，可为空</del>

userName ：

- 类型：字符串
- 默认值：空
- 描述：（可选项）用户名

userNameSize ：

- 类型：数字类型
- 默认值：13
- 描述：（可选项）用户名字体大小

userColor：

- 类型：字符串
- 默认值：#FFFFFF
- 描述：（可选项）用户名和积分字体颜色

<del>count ：</del>

- <del>类型：字符串</del>
- <del>默认值：0</del>
- <del>描述：积分，可为空</del>

subTitle ：

- 类型：字符串
- 默认值：空
- 描述：（可选项）用户名下边的小标题

subTitleSize ：

- 类型：字符串
- 默认值：13
- 描述：（可选项）用户名下边的小标题字体大小

subTitleColor：

- 类型：字符串
- 默认值：#FFFFFF
- 描述：（可选项）用户名下边的小标题字体颜色

showLeftBtn：

- 类型：布尔值
- 默认值：true
- 描述：（可选项）是否显示左上交修改按钮

showRightBtn：

- 类型：布尔值
- 默认值：true
- 描述：（可选项）是否显示右上角设置按钮

modButton：

- 类型：json对象
- 默认值：无
- 描述：（可选项）修改按钮参数
- 备注：若不传则不显示修改按钮
- 内部字段：

```js
{
	bgImg:      	//字符串，按钮背景图片，不可为空
	lightImg:     	//字符串，按钮点击效果图路径，可为空
}
```

btnArray：

- 类型：数组
- 默认值：默认按钮
- 描述：（可选项）下边按钮的参数信息
- 内部字段：

```js
[{
    bgImg:                   //按钮背景图片，字符串
    selectedImg:             //（可选项）按钮点击图片，字符串
    lightImg:                //（可选项）按钮选中后图片，字符串
    title:                   //（可选项）按钮上的标题，字符串
    count:                   //（可选项）按钮上的数据，字符串
    titleColor:              //（可选项）按钮上的标题颜色，字符串，默认#AAAAAA
    titleLightColor:         //（可选项）按钮选中标题的颜色，字符串，默认#A4D3EE
    countColor:              //（可选项）按钮上数字颜色，字符串，默认#FFFFFF
    countLightColor:         //（可选项）按钮上数字选中颜色，字符串，默认#A4D3EE
}]
```

fixedOn：

- 类型：字符串
- 默认值：当前主窗口的名字
- 描述：（可选项）将视图添加到指定的视图的名字

clearBtn：

- 类型：布尔值
- 默认值：false
- 描述：（可选项）是否将个人中心下边按钮清除

fixed:
- 类型：布尔
- 默认值：true
- 描述：（可选项）是否将模块视图固定到窗口上，不跟随窗口上下滚动

##callback(ret,err)

ret:

- 类型：json对象

内部字段：

```js
{
    click:          // 点击的按钮的index----对应下边按钮数字的下标，
                    // 如果存在修改按钮，则其index是按钮数组总下标加一，
                    // 若存在左上角按钮，则其index是按钮数组总下标加二，
                    // 若存在右上角按钮，则其inidex是按钮数组总下标加三
}
```

##示例代码

```js
var personalCenter = api.require('personalCenter');

personalCenter.open({
    imgPath:'http://h.hiphotos.baidu.com/image/pic/item/42166d224f4a20a40155f84e92529822730ed0f4.jpg',
    placeholderImg: 'widget://res/filterMe.png',
    btnArray:[
        {
            bgImg:'widget://res/personal_btn_nor.png',
    selectedImg:'widget://res/personal_btn_sele.png'
    },
{
    bgImg:'widget://res/personal_btn_nor.png',
    selectedImg:'widget://res/personal_btn_sele.png'
    },
    {
        bgImg:'widget://res/personal_btn_nor.png',
        selectedImg:'widget://res/personal_btn_sele.png'
        }
    ]
    },function(ret,err){
    api.alert({
        msg:ret.click
    });
});
```

##补充说明

打开个人中心

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**updateValue**<div id="2"></div>

刷新个人中心显示数据

updateValue({params})

##params

<del>username ：</del>

- <del>类型：字符串</del>
- <del>默认值：无</del>
- <del>描述：用户名，可为空，若为空，则显示之前的数据</del>

userName ：

- 类型：字符串
- 默认值：无
- 描述：（可选项）用户名
- 备注：若不传则不刷新

<del>count ：</del>

- <del>类型：字符串</del>
- <del>默认值：无</del>
- <del>描述：积分，可为空，若为空，则显示之前的数据</del>

subTile ：

- 类型：字符串
- 默认值：无
- 描述：(可选项)用户名下的小标题
- 备注：若不传则不刷新

imgPath：

- 类型：字符串
- 默认值：无
- 描述：(可选项)头像地址，可为空，若为空则刷新占位图的图片，若placehodlmg也为空则不刷新头像

<del>placeHoldImg：</del>

- <del>类型：字符串</del>
- <del>默认值：无</del>
- <del>描述：头像占位图地址，可为空</del>

btnArray：

- 类型：数组
- 默认值：无
- 描述：（可选项）下边按钮显示的数据
- 备注：为空则不刷新
- 内部字段:

```js
[{
      count:’123’       //字符串，按钮上的数据大小，不可为空
}]
```

##示例代码

```js
var obj = api.require('personalCenter');
obj.updateValue({
	imgPath:'widget://res/filterMe.png',
	userName:'柚子科技',
	count:'2014',
	btnArray:[{
		count:'123'
	},{
	    count:'123'
	},{
		count:'123'
	}]
});
```

##补充说明

刷新个人中心显示数据

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**close**<div id="3"></div>

关闭个人中心

close()

##示例代码

    var obj = api.require('personalCenter');
    obj.close();

##补充说明

关闭个人中心

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**setSelect**<div id="4"></div>

设置选中按钮

setSelect()

##示例代码

```js
var obj = api.require('personalCenter');
obj.setSelect({
	index:1
});
```

##补充说明

设置指定按钮为选中状态

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**show**<div id="5"></div>

显示个人中心

show()

##示例代码

	var obj = api.require('personalCenter');
	obj.show();

##补充说明

显示个人中心

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**hide**<div id="6"></div>

隐藏个人中心

hide()

##示例代码

	var obj = api.require('personalCenter');
	obj.hide();

##补充说明

隐藏个人中心，并没有从内存里清除

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
