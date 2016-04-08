/*
Title: trans
Description: trans
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[parse](#1)

[saveImage](#2)

[decodeImgToBase64](#3)
</div>

#**概述**

trans是一个数据格式转换工具，可以实现不同格式数据间的转换，如 XML -> JSON、图片<--> base64字符串

#**parse**<div id="1"></div>

将xml文件或数据解析成JSON对象

parse({params}, callback(ret, err))

##params

path：

- 类型：字符串
- 描述：（可选项）xml文件路径，要求本地路径（fs://、widget），与 data 配合使用，data 和 path 不可都不传，若都传则以 data 为准

data：

- 类型：字符串
- 描述：（可选项）xml数据，与 path 配合使用，data 和 path 不可都不传，若都传则以 data 为准

customKey：

- 类型：字符串
- 默认值：plainText
- 描述：所解析的xml值无对应的key时，需要填充一个自定义key

##callback(ret, err)

ret：

- 类型：JSON对象
- 描述：xml解析成的JSON数据

err：

- 类型：JSON对象
- 内部字段：

```js
{
	msg:            //字符串类型；错误信息
}
```

##示例代码

```js
var trans = api.require('trans');
trans.parse({
	path: 'widget://res/file/test.xml'
},function( ret, err ){		
	if( ret ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```

##补充说明

path和data不能同时为空，如果都不为空，则使用data的值；

如果xml数据中出现类似以下内容：

```js
<author email="'123@api.com'">
	api
</author>
则author节点被解析成以下格式，其中plainText为约定好的字段
{
	email:'123@api.com',
	plainText:'api'
}
```
##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**saveImage**<div id="2"></div>

将base64字符串保存为图片

parse({params}, callback(ret, err))

##params

base64Str：

- 类型：字符串
- 描述：要转换成为图片的字符串

album：

- 类型：布尔值
- 默认值：false
- 描述：（可选项）转换后的图片是否保存到系统相册

imgPath：

- 类型：字符串
- 描述：（可选项）转换后的图片保存路径，若不传则不保存

imgName：

- 类型：字符串
- 默认值：apicloud.png
- 描述：（可选项）转换后的图片保存名字，若imgPath下已存在同名图片则覆盖，若imgPath为空则此参数无意义

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```JS
{
	status：		//布尔类型；是否保存成功，true|false
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
	msg:		   //字符串类型；错误信息
}
```

##示例代码

```js
var trans = api.require('trans');
trans.saveImage({
	base64Str: 'test'
},function( ret, err ){		
	if( ret.status ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

#**decodeImgToBase64**<div id="3"></div>

将图片转换为base64字符串，**暂仅支持 png、jpg 格式的图片**

parse({params}, callback(ret, err))

##params

imgPath：

- 类型：字符串
- 描述：要转换的图片路径

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	status：			//布尔类型；是否转换成功，true|false
	base64Str:    	//字符串类型；转换后的base64字符串
} 
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
	msg:            //字符串类型；错误信息
}
```

##示例代码

```js
var trans = api.require('trans');
trans.decodeImgToBase64({
	imgPath: 'widget://res/img/apicloud.png'
},function( ret, err ){        
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

