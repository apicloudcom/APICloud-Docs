/*
Title: brightness2016
Description: brightness2016
*/

<div class="outline">

[setBrightness](#a1)
[getBrightness](#a2)
[setAppBrightness](#a3)
</div>

#**概述**

brightness2016实现了获取和设置系统屏幕亮度的方法。

<div id="a1"></div>
#**setBrightness**

设置系统屏幕亮度。

setBrightness({params})

##params

brightness：

- 类型：数字
- 描述：表示亮度，取值范围：0--255 暗->亮

##示例代码

```js

	var brightness = api.require('brightness2016');
	brightness.setBrightness({brightness:100});

```

##可用性
Android系统1.0.0及更高版本

iOS系统 5.0以上版本

<div id="a2"></div>
#**getBrightness**

获取系统屏幕亮度。

getBrightness(callback(ret,err))

##callback(ret,err)

brightness：

- 类型：数字
- 描述：表示亮度，取值范围：0--255 暗->亮

##示例代码

```js

var brightness = api.require('brightness2016');
brightness.getBrightness(function(ret){
    alert(JSON.stringify(ret));
});

```

##可用性
Android系统1.0.0及更高版本

iOS系统 5.0以上版本

<div id="a3"></div>
#**setAppBrightness**

设置当前App屏幕亮度。

setAppBrightness({params})

##params

brightness：

- 类型：数字
- 描述：表示亮度，取值范围：0--255 暗->亮

##示例代码

```js

var brightness = api.require('brightness2016');
brightness.setAppBrightness({brightness:100});

```

##可用性
Android系统1.0.0及更高版本

