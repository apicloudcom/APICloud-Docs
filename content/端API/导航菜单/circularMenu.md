/*
Title: circularMenu
Description: circularMenu
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#a1)

[close](#a2)

[hide](#a3)

[show](#a4)
</div>

#**概述**

circularMenu 是一个转盘菜单。本模块是原生实现的，动画流畅，开发者可自定义菜单上按钮的个数和样式。简单几行代码即可开发出转盘效果的炫酷UI

![图片说明](/img/docImage/circularMenu.jpg)

#**open**<div id="a1"></div>

打开转盘菜单

open({params}, callback(ret, err))

##params

centerX：

- 类型：数字
- 默认值：0
- 描述：（可选项）环形菜单的圆心 X 坐标（相对于所属的 Window 或 Frame）

centerY：

- 类型：数字
- 默认值：0
- 描述：（可选项）环形菜单的圆心 Y 坐标（相对于所属的 Window 或 Frame）

radius：

- 类型：数字
- 默认值：150
- 描述：（可选项）环形菜单的圆半径

centerBtnRadius：

- 类型：数字
- 默认值：radius/3.0
- 描述：（可选项）环形菜单中间圆形按钮的半径

bgImg：

- 类型：字符串
- 描述：（可选项）环形菜单的背景图片

centerBtnImg：

- 类型：字符串
- 描述：（可选项）环形菜单的中间按钮的背景图片

indicatorPosition：

- 类型：字符串
- 默认值：left
- 描述：（可选项）环形菜单的指针位置，取值范围如下：
	- left		//左边
	- right		//右边
	- up		//上边
	- down		//下边

items：

- 类型：数组
- 描述：子菜单信息组成的数组
- 内部字段：

```js
[{
	normal:             //字符串类型；按钮常态背景图片路径，要求本地路径（widget://、fs://）
	highlight:          //（可选项）字符串类型；按钮高亮背景图片路径，要求本地路径（widget://、fs://）
	title:              //（可选项）字符串类型；按钮标题
	titleColor:         //（可选项）字符串类型；标题字体颜色，支持 rgb、rgba、#；默认：#919191
	titleSize:          //（可选项）数字类型；标题字体大小；默认：13
}]
```

fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    click：				//布尔值，判断是否是点击事件的callBack
	index:    			//数字类型；用户点击按钮的下标，中间按钮的下标为最大
	indicatorIndex: 	//数字类型；旋转停止后指针所指位置下的按钮的下标
}
```

##示例代码

```js
var circularMenu = api.require('circularMenu');
circularMenu.open({
	items: [{
            normal: 'widget://res/circularMenu/1.png',
            highlight: 'widget://res/circularMenu/1light.png',
            title: '账户明细'
        },
        {
            normal: 'widget://res/circularMenu/2.png',
            highlight: 'widget://res/circularMenu/2light.png',
            title: '转账汇款'
        },
        {
            normal: 'widget://res/circularMenu/3.png',
            highlight: 'widget://res/circularMenu/3light.png',
            title: '投资理财'
        },
        {
            normal: 'widget://res/circularMenu/4.png',
            highlight: 'widget://res/circularMenu/4light.png',
            title: '特色服务'
        },
        {
            normal: 'widget://res/circularMenu/5.png',
            highlight: 'widget://res/circularMenu/5light.png',
            title: '安全中心'
        },
        {
            normal: 'widget://res/circularMenu/6.png',
            highlight: 'widget://res/circularMenu/6light.png',
            title: '信用卡'
        }
    ],
    centerX: api.frameWidth / 2,
    centerY: api.frameHeight / 2,
    bgImg: 'widget://res/circularMenu/bg.png',
    centerBtnImg: 'widget://res/circularMenu/center.png',
	fixedOn: api.frameName
}, function(ret, err){		
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


#**close**<div id="a2"></div>

关闭环形菜单

close()

##示例代码

```js
var circularMenu = api.require('circularMenu');
circularMenu.close();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**hide**<div id="a3"></div>

隐藏环形菜单

hide()

##示例代码

```js
var circularMenu = api.require('circularMenu');
circularMenu.hide();
```

##补充说明

隐藏环形菜单，并没有从内存清除

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

#**show**<div id="a4"></div>

显示已隐藏的环形菜单

show()

##示例代码

```js
var circularMenu = api.require('circularMenu');
circularMenu.show();
```

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本
</div>
