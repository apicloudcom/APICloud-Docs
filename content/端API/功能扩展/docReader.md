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

open({params},callback(ret,err))

##params

path：

- 类型：字符串
- 描述：打开文档的路径，要求本地路径（widget://，fs://）

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	status: true		//布尔类型；操作成功状态值，true|false
}
```
err：

- 类型：JSON对象
- 内部字段：

```js
{
	code: ''          //数字类型；错误描述码，取值范围如下：
	                  //-1（未知错误）
	                  //1（文件不存在）
	                  //2（文件格式不支持）
}
```

##示例代码

```js
var docReader = api.require('docReader');
docReader.open({
    path: 'widget://res/test.docx'
},function( ret, err ){		
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##补充说明

打开文件

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
