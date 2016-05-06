/*
Title: panorama
Description: panorama
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[close](#2)

[hide](#3)

[show](#4)
</div>

#**概述**

panorama 封装了用 openGL 实现的一个全景展示的库，开发者自需传入一张全景的图片，即可实现拖动查看全景图的功能

![图片说明](/img/docImage/panorama.jpg)

#**open**<div id="1"></div>

打开全景展示视图

open({params}, callback(ret, err))

##params


x：

- 类型：数字
- 默认值：0
- 描述：视图左上角坐标点，可为空

y：

- 类型：数字
- 默认值：0
- 描述：视图左上角坐标点，可为空

w：

- 类型：数字
- 默认值：屏幕宽度
- 描述：视图的宽，可为空

h：

- 类型：数字
- 默认值：屏幕的高的一半
- 描述：视图的高，可为空

imgPath：

- 类型：字符串
- 默认值：无
- 描述：要展示的360度全景图片的路径，不可为空

fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window


##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	status:true          //操作成功状态值
	id:                  //视图的id，据此id关闭该视图
}
```

err：

- 类型：JSON 对象

内部字段：

```js
{
	msg:“”		//错误描述
}
```

##示例代码

```js
var panorama = api.require('panorama');
panorama.open({
	x: 0,
	y: 64,
	w: api.winWidth,
	h: 300,
	imgPath: 'widget://res/img/ic/360viewtest.jpg',
    fixedOn: api.frameName
}, function(ret, err){
	if( ret ){
         alert( JSON.stringify( ret ) );
    }else{
         alert( JSON.stringify( err ) );
    }
});
```

##补充说明

打开全景展示

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**close**<div id="2"></div>

关闭全景展示视图

close({params})

##params

id：

- 类型：数字
- 默认值：无
- 描述：要关闭的视图的id，不能为空

##示例代码

```js
var panorama = api.require('panorama');
panorama.close({
	id:1
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

#**hide**<div id="3"></div>

隐藏全景展示视图

hide({params})

##params

id：

- 类型：数字
- 默认值：无
- 描述：要关闭的视图的id，不能为空

##示例代码

```js
var panorama = api.require('panorama');
panorama.hide({
	id:1
});
```

##补充说明

隐藏视图，并没有从内存里清除

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

#**show**<div id="4"></div>

显示全景展示视图

show({params})

##params

id：

- 类型：数字
- 默认值：无
- 描述：要关闭的视图的id，不能为空

##示例代码

```js
var panorama = api.require('panorama');
panorama.show({
	id:1
});
```

##补充说明

显示已隐藏的视图

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本
