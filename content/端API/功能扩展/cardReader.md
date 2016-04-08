/*
Title: cardReader
Description: cardReader
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

#**概述**

cardReader封装了PayPal的cardio识别库，用户只需用摄像头扫描信用卡即可实现卡号的输入

注意：本模块在ios上仅支持ios6（含）以上版本

![图片说明](/img/docImage/cardReader.jpg)

#**open**

打开信用卡识别器

open(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：
```js
{
    status:true                 //操作成功状态值
    cardNum:                    //卡号
    expiryMonth:                //过期日期的月
    expiryYear:                 //过期日期的年
    cvv:                        //cvv号
}
```
err：

- 类型：JSON对象

内部字段：
```js
{
	msg：	//错误信息
}
```
##示例代码

```js
var cardReader = api.require('cardReader');
cardReader.open(function( ret, err ){		
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##补充说明

打开信用卡识别器

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
