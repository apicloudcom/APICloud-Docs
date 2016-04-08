/*
Title: touchID
Description: touchID
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

#**概述**

touchID封装了iphone5s以后版本的手机特有的指纹识别功能，调用此模块可实现用户指纹输入验证登陆app 。使用本模块需要支持指纹识别的手机和ios8.0以上的操作系统

![图片说明](/img/docImage/touchID.jpg)

#**verify**

弹出验证界面，验证用户指纹

verify()

##params

title：

- 类型：字符串
- 默认值：验证指纹密码
- 描述：验证界面的标题

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	status:  //布尔类型；是否验证通过，true|false
	code:    //数字类型；返回验证未通过信息，参数说明如下：
	          0：    //用户选中手动输入
              1：    //用户取消验证
              2：    //验证三次失败
              3：    //多次验证失败
              4：    //验证失败，未知错误
              5：    //用户未开启指纹验证设备
}
```

##示例代码

```js
var obj = api.require('touchID');
obj.verify(
function(ret,err){
	if(ret.status){
		api.alert({msg:"验证通过"});
	}else{
		if(ret.index==0){
			api.alert({msg:"用户选择手动输入"});
		}else if(ret.index==1){
			api.alert({msg:"用户取消验证"});
		}else if(ret.index==2){
			api.alert({msg:"验证三次失败"});
		}else if(ret.index==3){
			api.alert({msg:"多长验证失败请锁定手机"});
		} else {
			api.alert({msg:"验证失败，未知错误"});
        }
    }
});
```

##可用性

iOS8及以上系统

可提供的1.0.0及更高版本
