/*
Title: brightness
Description: brightness
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[setBrightness](#a1)


</div>

#**概述**

brightness封装了android调节当前窗体亮度的功能，使用此模块可轻松实现对窗体亮度调节的功能


#**setBrightness**<div id="a1"></div>

设置窗体亮度

setBrightness({params})

##params



Brightness：

- 类型：数字
- 默认值：无
- 描述：不能为空，表示亮度(0--255)



##示例代码

```js
var brightness = api.require('brightness');


brightness.setBrightness({Brightness:100});
```

##补充说明

无

##可用性

Android系统

可提供的1.0.0及更高版本

