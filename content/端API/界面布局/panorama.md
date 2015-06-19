/*
Title: panorama
Description: panorama
*/

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

panorama封装了用openGL实现的一个全景展示的库，开发者自需传入一张全景的图片，即可实现拖动查看全景图的功能

![图片说明](/img/docImage/panorama.jpg)

#**open**<div id="1"></div>

打开全景展示视图

open({params},callback(ret,err))

##params


x：

- 类型：数字
- 默认值：0
- 描述：视图左上角坐标点，可为空

y：

- 类型：数字
- 默认值：0
- 描述：视图左上角坐标点，可为空

<del>width：</del>

- <del>类型：数字</del>
- <del>默认值：屏幕宽度</del>
- <del>描述：视图的宽，可为空</del>

<del>height：</del>

- <del>类型：数字</del>
- <del>默认值：屏幕的高的一半</del>
- <del>描述：视图的高，可为空</del>

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

- 类型：字符串
- 默认值：当前主窗口的名字
- 描述：将此模块视图添加到指定窗口的名字，可为空


callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:true          //操作成功状态值
	id:                  //视图的id，据此id关闭该视图
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:“”		//错误描述
}
```

##示例代码

```js
var obj = api.require('panorama');
obj.open({
	x:0,
	y:64,
	w:320,
	h:300,
	imgPath:'widget://res/360viewtest.jpg'
},function(ret,err){
	if(ret.status){
		api.alert({msg:'视图的id是'+ret.id});
	}else{
		api.alert({msg:ret.msg});
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
var obj = api.require('panorama');
obj.close({
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
var obj = api.require('panorama');
obj.hide({
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
var obj = api.require('panorama');
obj.show({
	id:1
});
```

##补充说明

显示已隐藏的视图

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本
