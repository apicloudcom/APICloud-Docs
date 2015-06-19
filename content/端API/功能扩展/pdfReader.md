/*
Title: pdfReader
Description: pdfReader
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">
<div class="outline">
[open](#1)
</div>

#**概述**

pdfReader封装了一个简单的pdf阅读器，支持添加标签、以九宫格形式查看、打印等功能，本模块只支持阅读pdf格式的文档

#**open**<div id="1"></div>

打开一个pdf格式的文档

open({params})

##params

path：

- 类型：字符串
- 默认值：无
- 描述：文档的路径（支持的路径协议：widget://,fs://，file://），不能为空

##示例代码

```js
var obj = api.require('pdfReader');
obj.open({
    path:'文件路径'
});
```

##补充说明

打开pdf文件

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
