/*
Title: dayinji
Description: dayinji
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">方法</a></li>
</ul>
<div id="method-content">

<div class="outline">

[startActivityForResult](#startActivityForResult)

</div>

## 概述 ##

本模块一款实现手机蓝牙打印的功能

## startActivityForResult (params)<div id="startActivityForResult"></div>
入口

startActivityForResult(params)

## params ##
appParam：

- 类型：字符串
- 默认值：无
- 描述：需要打印的字，可以对打印的字排版，\b空格，\n换行

### 示例代码 ###

```js		
var dayinji = api.require('dayinji');

var param = {appParam:"aaaaaaaaa"}; 
    
dayinji.startActivityForResult(param);
```	


### 可用性 ###

Android 系统

可提供的 1.0.0 及更高版本
