/*
Title: docReader
Description: docReader
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">
<div class="outline">
[open](#1)
</div>

#**概述**

docReader模块封装了对文档阅读的功能，开发者直接传进来一个文档，即可读出文档的内容显示出来，目前支持的文档格式主要有excel，doc，pdf等

#**open**<div id="1"></div>

打开一个文档，文档类型可以是excel，doc，pdf等格式

open({params})

##params

path：

- 类型：字符串
- 默认值：无
- 描述：文档的路径（支持的路径协议：widget://，fs://，cache://），不能为空

##示例代码

```js
var obj = api.require('docReader');
obj.open({
    path:'widget://res/test1.docx'
});
```

##补充说明

打开文件

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
