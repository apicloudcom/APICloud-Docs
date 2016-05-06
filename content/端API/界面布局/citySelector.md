/*
Title: citySelector
Description: citySelector
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

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

citySelector是一个城市选择器，以选择器的形式将中国各个省市级城市弹出，供用户选择，开发者可自定义该选择器的样式。若想自定义数据源，可用[customSelector 模块](http://docs.apicloud.com/端API/界面布局/customSelector)或者[UIActionSelector](http://docs.apicloud.com/端API/界面布局/UIActionSelector)自定义。

![图片说明](/img/docImage/citySelector.jpg)

#**open**<div id="1"></div>

打开城市选择器

open({params}, callback(ret, err))

##params

y：

- 类型：数字
- 默认值：当前设备屏幕下边缘减244
- 描述：选择器视图上边缘距离当前设备屏幕顶部距离，可为空

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

anim：

- 类型：布尔
- 默认值：false
- 描述：是否添加弹出动画，可为空

fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window

##callback(ret, err)

ret：

类型：JSON 对象

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
var citySelector = api.require('citySelector');
citySelector.open({
    y: api.frameHeight / 1.6,
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

打开选择器

##可用性

iOS系统，安卓系统

可提供的0.0.1及更高版本


#**hide**<div id="5"></div>

隐藏选择器

hide({params})

##params

anim：

- 类型：布尔
- 默认值：false
- 描述：是否添加动画，可为空

##示例代码

```js
	var citySelector = api.require('citySelector');
	citySelector.hide();
```

##补充说明

隐藏选择器，只是移除到屏幕之外，还在内存里没有清除

##可用性

iOS系统，安卓系统

可提供的0.0.1及更高版本


#**show**<div id="3"></div>

显示选择器

show(parmas)

##params

anim：

- 类型：布尔
- 默认值：false
- 描述：是否添加动画，可为空

##示例代码

```js
var citySelector = api.require('citySelector');
citySelector.show();
```

##补充说明

显示选择器，从屏幕外移动到屏幕内

##可用性

iOS系统，安卓系统

可提供的0.0.1及更高版本



#**close**<div id="4"></div>

关闭选择器

close(parmas)

##params

anim：

- 类型：布尔
- 默认值：false
- 描述：是否添加动画，可为空

##示例代码

```js
var citySelector = api.require('citySelector');
citySelector.close();
```

##补充说明

关闭选择器，意味着从内存里清除

##可用性

iOS系统，安卓系统

可提供的0.0.1及更高版本


