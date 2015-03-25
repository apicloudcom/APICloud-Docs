/*
Title: ksisdk
Description: ksisdk
*/
<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">方法</a></li>
</ul>
<div id="method-content">

<div class="outline">

[signfortext](#signfortext)

[signforhash](#signforhash)

[verifyfortext](#verifyfortext)

[verifyforhash](#verifyforhash)

</div>

## 概述

爱立示无钥签名 是电子数据的电子标签（签名），以纯数学算法检验及证明电子数据的签名时间、起源和数据完整性，证明数据的可靠性和不可抵赖性。爱立示所创立的无钥签名 技术已经在多个地区被成功应用于电子政务、通讯、金融、云计算、物联网、版权保护等领域。任何电子数据都可通过本地计算提取电子指纹，电子指纹经过分布式网络基础设施运算获得无钥签名 。无钥签名 技术使得对数据完整性的验证和证明仅仅依赖于数学运算，不再需要基于对人或机构的信任。无钥签名 可以由任何人独立验证，且验证永不失效，同时对量子破解免疫。 爱立示致力于帮助社会建立公共诚信机制，让信任更简单！

暂仅支持 Andorid 系统

## signfortext <div id="signfortext"></div>

为纯文本参数签名

signfortext(params, callback)


### params

content

- 类型: 字符串
- 默认值: 无
- 描述: 待签名的文本内容，不可为空


### callback(ret, err)

ret:

- 类型：JSON 对象

内部字段：

```js
{  res_code:0,//请求成功时的响应码，签名成功时为0   res_message:”Signature created and   stored”,//请求成功时的响应信息}
```

err:

- 类型：JSON 对象

内部字段：

```js
{
	msg: 签名异常，请稍后重试！//请求错误时的返回信息
}
```

### 示例代码

```js
signfortext = api.require('signfortext');var params = {content:”测试文本” };	signfortext.signfortext(params,function(ret, err){       if(ret.res_message!=null&&ret.res_code!=null){			alert("["+ret.res_code+"]:"+ret.res_message);	   }else if(err.msg!=null){			alert(err.msg);	   }} );
```

### 可用性

Android 系统

可提供的 1.0.0 及更高版本

## signforhash <div id="signforhash"></div>

为已经计算好的hash值进行签名

signforhash(params, callback)

### params

hashcode:

- 类型：字符串
- 默认值：无
- 描述：待签名的hash值，不可为空

### callback(ret, err)

ret:

- 类型：JSON 对象

内部字段：

```js
{
   res_code:0,//请求成功时的响应码，签名成功时为0   res_message:”OK”,//请求成功时的响应信息
}
```

err:

- 类型：JSON 对象

内部字段：

```js
{
	msg: 签名异常，请稍后重试！//请求错误时的返回信息
}

```

### 示例代码

```js
signforhash = api.require('signforhash');var params = {hashcode:”测试hash值“ }signforhash.signforhash(params,function(ret, err){		if(ret.res_message&&ret.res_code){			alert(" ["+ret.res_code+"]:"+ret.res_message);		}else if(err.msg!=null){			alert(err.msg);		}}  );
```

### 可用性

Android 系统

可提供的 1.0.0 及更高版本

## verifyfortext <div id="verifyfortext"></div>

为纯文本参数进行验证

verifyfortext(params, callback)


### params

content

- 类型: 字符串
- 默认值: 无
- 描述: 待验证的文本内容，不可为空

### callback(ret, err)

ret:

- 类型：JSON 对象

内部字段：

```js
{
   res_code:0,//请求成功时的响应码，验证成功时为0   res_message:”Signature created and stored”,//请求成功时的响应信息    registered_time:”Sat Feb 28 2015 17:04:55 GMT+0800 (CST)”,//签名时间,验证成功时返回    hash_value:””,//验证hash值，验证成功时返回    hash_algorithm:” SHA256”,//hash算法，验证成功时返回}
```

err:

- 类型：JSON 对象

内部字段：

```js
{	msg: 验证出现异常，请稍后重试！//请求错误时的返回信息}

```

### 示例代码

```js
verifyfortext = api.require(verifyfortext);var params = {content:”测试文本” };	verifyfortext. verifyfortext (params,function(ret, err){       if(ret.res_message!=null&&ret.res_code!=null){			alert("["+ret.res_code+"]:"+ret.res_message);	   }else if(err.msg!=null){			alert(err.msg);	   }} );
```

### 可用性

Android 系统

可提供的 1.0.0 及更高版本

## verifyforhash <div id="verifyforhash"></div>

为已经计算好的hash值进行验证

verifyforhash(params, callback)

### params

hashcode:

- 类型：字符串
- 默认值：无
- 描述：待签名的hash值，不可为空

### callback(ret, err)

ret:

- 类型：JSON 对象

内部字段：

```js
{   res_code:0,//请求成功时的响应码，验证成功时为0   res_message:”Signature created and stored”,//请求成功时的响应信息   registered_time:”Sat Feb 28 2015 17:04:55 GMT+0800 (CST)”,//签名时间,验证成功时返回   hash_value:””,//验证hash值，验证成功时返回   hash_algorithm:” SHA256”,//hash算法，验证成功时返回}
```

err:

- 类型: JSON对象
- 内部字段:

```js
{
  msg: 验证出现异常，请稍后重试！//请求错误时的返回信息
}
```

### 示例代码

```js
verifyforhash = api.require('verifyforhash');var params = {hashcode:”测试hash值“ }verifyforhash. verifyforhash(params,function(ret, err){		if(ret.res_message&&ret.res_code){			alert(" ["+ret.res_code+"]:"+ret.res_message);		}else if(err.msg!=null){			alert(err.msg);		}}  );
```

### 可用性

Android 系统

可提供的 1.0.0 及更高版本
