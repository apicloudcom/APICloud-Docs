/*
Title: yzxVerification
Description: yzxVerification
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">方法</a></li>
</ul>

<div class="outline">
[getSign](#getSign)

[getVerificationCode](#getVerificationCode)

[doVerificationCode](#doVerificationCode)

</div>

#**概述**

YzxVerification封装了云之讯开放平台的智能验证SDK，使用此模块可以实现智能验证功能.

注意: 云之讯官方智能验证产品线路调整为rest通用接口,此模块将在10天后停止维护与更新. 开发者朋友可继续选择使用此模块已有功能, 或选择通过 api.ajax 使用云之讯智能验证的rest接口来完成相关功能.

##getSign<div id="getSign"></div>

获得签名

getSign({params}, callback(ret, err))

##params

phonenum：

- 类型：字符串
- 默认值：无
- 描述：手机号码，不能为空

url：

- 类型：字符串
- 默认值：无
- 描述：AS服务器地址（详见[地址类型](!Constant)常量），不能为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:true           //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    result:0    //服务器返回结果
    msg:""    //错误描述
}
```

## 示例代码

```js
var uzyzxVerification = api.require("yzxVerification");

uzyzxVerification.getSign({
    url: 'https://mid.ucpaas.com/vfs/demo/reg.do',
    phonenum: '18612345678'
},function(ret,err){
    if(ret.status){
        api.alert({msg:'获得签名成功 sign='+ret.sign});
    }else{
        api.alert({msg:'获取签名失败 返回值:'+err.result});
    }
});
```

##补充说明

获得签名，获得的签名会保存在native层，获取验证码时需要提交签名，云之讯服务器会比对签名是否正确

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

## getVerificationCode<div id="getVerificationCode"></div>

获得验证码

getVerificationCode({params}, callback(ret, err))

##params

phonenum：

- 类型：字符串
- 默认值：无
- 描述：手机号码，不能为空

sid：

- 类型：字符串
- 默认值：无
- 描述：开发者id，不能为空

appid：

- 类型：字符串
- 默认值：无
- 描述：应用id，不能为空

appname：

- 类型：字符串
- 默认值：无
- 描述：应用名称，可以为空

##callback(ret, err)

seconds：

- 类型：整形
- 默认值：60
- 描述：有效时间，可以为空

##callback(ret, err)


ret：

- 类型：JSON对象

内部字段：

```js
{
	status:true           //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    code:0    //错误码
    msg:""    //错误描述
}
```

```js
var uzyzxVerification = api.require("yzxVerification");

uzyzxVerification.getVerificationCode({
    phonenum: 18612345678,
    sid: "4c1990a5c1ad2674bc94bc39a6fd0699",
    appid: "efb7e1de9da649fa83881afea2841cd7",
    appname: "yzxverification"
},function(ret,err){
    if(ret.status){
        switch (ret.type){
            case 0:
                api.alert({msg:'验证成功'});
                break;
            case 1:
                api.alert({msg:'等待短信下发验证码'});
                break;
            case 2:
                api.alert({msg:'等待语音下发验证码'});
                break;
        }
    }else{
        api.alert({msg:'获取验证码失败 错误码:'+err.code});
    }
});
```

##补充说明

获得签名

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

## doVerificationCode<div id="doVerificationCode"></div>

获得验证码

doVerificationCode({params}, callback(ret, err))

##params

phonenum：

- 类型：字符串
- 默认值：无
- 描述：手机号码，不能为空

verifycode：

- 类型：字符串
- 默认值：无
- 描述：验证码，不能为空

sid：

- 类型：字符串
- 默认值：无
- 描述：开发者id，不能为空

appid：

- 类型：字符串
- 默认值：无
- 描述：应用id，不能为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:true           //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    code:0    //错误码
    msg:""    //错误描述
}
```

```js
var uzyzxVerification = api.require("yzxVerification");

uzyzxVerification.doVerificationCode({
    phonenum: "18612345678",
    verifycode: "12345",
    sid: "4c1990a5c1ad2674bc94bc39a6fd0699",
    appid: "efb7e1de9da649fa83881afea2841cd7"
},function(ret,err){
    if(ret.status){
        api.alert({msg:'验证成功'});
    }else{
        api.alert({msg:'验证失败 错误码:'+err.code});
    }
});
```

##补充说明

对验证码进行验证

##可用性

iOS系统，Android系统

可提供的 1.0.0 及更高版本