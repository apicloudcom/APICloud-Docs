/*
Title: pdfReader
Description: pdfReader
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">
<div class="outline">
[open](#1)

[clearCache](#2)
</div>

#**概述**

pdfReader 封装了一个简单的 pdf 阅读器，支持添加标签、以九宫格形式查看、打印等功能，本模块只支持阅读 pdf 格式的文档，本模块支持对网络 pdf 文件的阅读，当传入一个网络路径，模块内部会先下载文件到本地缓存文件，然后再打开读取。用户再次打开相同路径的网络文件时，则先读取缓存在本地的文件。

#**open**<div id="1"></div>

打开一个 pdf 格式的文档

open({params})

##params

path：

- 类型：字符串
- 描述：文档的路径，支持 widget://、fs://、http:// 等本地和网络协议

##示例代码

```js
var pdfReader = api.require('pdfReader');
pdfReader.open({
    path: 'widget://res/test.pdf'
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="2"></div>
#**clearCache**

清除缓存到本地的文件，**本接口只清除本模块缓存的数据，若要清除本app缓存的所有数据这调用api.clearCache**

clearCache()

##示例代码

```js
var pdfReader = api.require('pdfReader');
pdfReader.clearCache();
```

##可用性

IOS系统，Android系统

可提供的1.0.0及更高版本