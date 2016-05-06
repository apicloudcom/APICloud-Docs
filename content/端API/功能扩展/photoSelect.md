/*
Title: photoSelect
Description: photoSelect
*/

<p style="color: #ccc;margin-bottom: 30px;">来自于：开发者</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">
<div class="outline">
[openAblum](#a1)
[clearoom](#a2)
</div>

#**概述**

photoSelect 封装了读取安卓系统相册功能，使用此模块可实现相册的单选多选，并可以限制选择图片的数量。暂仅支持 Android 平台


#**openAblum**<div id="a1"></div>

调用相册

openAblum( param, callback)

##params

permitnum

- 类型：字符串
- 描述：限制选择图片数量 最小为 1，没有限制最大，但建议不要太大，一般最大为 9


##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	selectpic: [],            		//数组类型；返回用户所选图片的地址的数组
	selectnum: 9    			  	//数字类型；返回的选择的图片的总数
}
```



##示例代码

```js
var photoSelect = api.require('photoSelect');
photoSelect.openAblum({
	permitnum: '9'
}, function(ret, err){		
	if( ret ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```

##可用性

Android 系统

可提供的1.0.0及更高版本


#**clearoom**<div id="a1"></div>

清除图片

clearoom()


##示例代码

```js
var photoSelect = api.require('photoSelect');
photoSelect.clearoom();
```

##补充说明

清除使用相册的图片垃圾,可以在选择完图片，并做完对图片的处理之后再清理图片垃圾，或者可以不使用。

##可用性

Android 系统

可提供的1.0.0及更高版本