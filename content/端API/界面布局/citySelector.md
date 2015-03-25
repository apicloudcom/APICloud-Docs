/*
Title: citySelector
Description: citySelector
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[hidden](#2)

[hide](#5)

[show](#3)

[close](#4)
</div>

#**概述**

citySelector是一个城市选择器，以选择器的形式将中国各个省市级城市弹出，供用户选择，开发者可自定义该选择器的样式

![图片说明](/img/docImage/citySelector.jpg)

#**open**<div id="1"></div>

打开城市选择器

open({params}, callback(ret, err))

##params

y：

- 类型：数字
- 默认值：当前设备屏幕下边缘减244
- 描述：选择器视图上边缘距离当前设备屏幕顶部距离，可为空

<del>height：</del>

- <del>类型：数字</del>
- <del>默认值：244</del>
- <del>描述：选择器视图的高，可为空</del>

cancelImg：

- 类型：字符串
- 默认值：默认图标
- 描述：取消按钮的背景图片的路径（本地），可为空

enterImg：

- 类型：字符串
- 默认值：默认图标
- 描述：确定按钮的背景图片的路径（本地），可为空

titleImg：

- 类型：字符串
- 默认值：默认图片
- 描述：选择器顶端导航条背景图片的路径（本地），可为空

bgImg：

- 类型：字符串
- 默认值：默认图片
- 描述：选择器背景图片的路径（本地），可为空

fontColor：

- 类型：字符串
- 默认值：#000000
- 描述：选择器字体颜色，可为空

selectedColor：

- 类型：字符串
- 默认值：#8B0000
- 描述：选中字体颜色，可为空

<del>animation：</del>

- <del>类型：布尔</del>
- <del>默认值：false</del>
- <del>描述：是否添加弹出动画，可为空</del>

anim：

- 类型：布尔
- 默认值：false
- 描述：是否添加弹出动画，可为空

fixedOn：

- 类型：字符串
- 默认值：当前主窗口的名字
- 描述：将此模块视图添加到指定窗口的名字，可为空

##callback(ret, err)

ret：

类型：JSON对象

内部字段：

```js
{
	province:               //选中的省
	city：					//选中的市
	county                  //选中的县
}
```

##示例代码

```js
var obj = api.require('citySelector');
obj.open({
},function(ret,err){
	api.alert({msg:'选了'+ret.city+ret.province+ret.county});
});
```

##补充说明

打开选择器

##可用性

IOS系统，安卓系统

可提供的0.0.1及更高版本



#**<del>hidden</del>**<div id="2"></div>

<del>隐藏选择器</del>

<del>hidden(params)</del>

##<del>params</del>

<del>animation：</del>

- <del>类型：布尔</del>
- <del>默认值：false</del>
- <del>描述：是否添加动画，可为空</del>

##<del><del>示例代码</del>

	var obj = api.require('citySelector');
	obj.hidden();

##<del>补充说明</del>

<del>隐藏选择器，只是移除到屏幕之外，还在内存里没有清除</del>

##<del>可用性</del>

<del>IOS系统，安卓系统</del>

<del>可提供的0.0.1及更高版本</del>

#**hide**<div id="5"></div>

隐藏选择器

hide(params)

##params

anim：

- 类型：布尔
- 默认值：false
- 描述：是否添加动画，可为空

##示例代码

	var obj = api.require('citySelector');
	obj.hide();

##补充说明

隐藏选择器，只是移除到屏幕之外，还在内存里没有清除

##可用性

IOS系统，安卓系统

可提供的0.0.1及更高版本


#**show**<div id="3"></div>

显示选择器

show(parmas)

##params

<del>animation：</del>

- <del>类型：布尔</del>
- <del>默认值：false</del>
- <del>描述：是否添加动画，可为空</del>

anim：

- 类型：布尔
- 默认值：false
- 描述：是否添加动画，可为空

##示例代码

	var obj = api.require('citySelector');
	obj.show();

##补充说明

显示选择器，从屏幕外移动到屏幕内

##可用性

IOS系统，安卓系统

可提供的0.0.1及更高版本



#**close**<div id="4"></div>

关闭选择器

close(parmas)

##params

<del>animation：</del>

- <del>类型：布尔</del>
- <del>默认值：false</del>
- <del>描述：是否添加动画，可为空</del>

anim：

- 类型：布尔
- 默认值：false
- 描述：是否添加动画，可为空

##示例代码

	var obj = api.require('citySelector');
	obj.close();

##补充说明

关闭选择器，意味着从内存里清除

##可用性

IOS系统，安卓系统

可提供的0.0.1及更高版本


