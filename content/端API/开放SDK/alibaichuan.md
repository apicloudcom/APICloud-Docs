/*
Title: alibaichuan
Description: alibaichuan
*/

<div class="outline">

* [initTaeSDK](#initTaeSDK)

* [showLogin](#1)

* [getUserInfo](#2)

* [logout](#3)

* [openMyCart](#4)

* [myOrdersPage](#5)

* [showTaokeItemById](#6)

* [showTaokeItemByOpenId](#7)

* [错误码](#8)

</div>

##**概述**

百川是阿里巴巴旗下的无线开放平台，基于世界级的后端服务和成熟的商业组件，快速搭建App和提供卓越用户体验，开拓广告、商品、生活服务等无线新商业。

>使用须知

V1.0.1

更新时间：2016-03-17

更新日志：

1、添加了初始化的接口initTaeSDK

2、将模块与安全图片分离，使用时候需要添加模块，并去[https://github.com/bringmehome/Alibaichuan](https://github.com/bringmehome/Alibaichuan)下载Custom Module模块，导入到自定义模块，两个模块配合使用（打包时候仍然是测试版）

3、使用步骤参考[接入指南](https://github.com/bringmehome/Alibaichuan/#bindyilai)


V1.0.0

>>1. 使用前需要去阿里百川注册并关联阿里妈妈，获取阿里妈妈淘客PID, [传送门](http://baichuan.taobao.com), 流程请参考[接入指南](https://github.com/bringmehome/Alibaichuan)

>>2. 不同的账号注册会生成不同的SDK，并得到不一样的 __"安全图片文件yw_1222.jpg"__ ，所以此版本为测试版本，在APICloud创建项目时候使用默认证书，生成apk时候也请选择测试版。

>>3. 打包成正式版本时候，如果因为各种原因无法调用手淘的授权登录页，请联系作者邮箱（rocke@feeling.life）,作者会在第一时间回复。

>>4. 此版本实现了阿里百川的基础功能：手淘授权登陆、退出登陆、获取登录者的信息、打开购物车、打开我的订单、通过itemid打开宝贝详情、通过openid打开宝贝详情。


#**initTaeSDK**<div id="initTaeSDK"></div>

    初始化模块信息，打开页面require完成就去执行

    initTaeSDK(function(ret, err))

##callback(ret,err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    code : 0              //正确码
    message:"success"     //初始化成功信息
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    code : 1000                     //错误码
    message:"user is not exist"     //错误描述
}
```

##示例代码

```js
var alibaichuan = null;
apiready = function() {
    alibaichuan = api.require('alibaichuan');
    initSDK();
};

function initSDK() {
    alibaichuan.initTaeSDK(function(ret, err) {
        if (ret) {
            alert(JSON.stringify(ret));
        } else {
            alert(JSON.stringify(err));
        }
    });
}
```

##补充说明

    无

##可用性

    Android系统

    可提供的1.0.0及更高版本


#**showLogin**<div id="1"></div>

    打开手淘授权登陆

    showLogin(function(ret, err))

##callback(ret,err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    userNick:"rocke"                //用户昵称
    avatarUrl:"http://..."          //用户头像
    authCode:"2mp9..."              //授权码
    loginTime:"1449932770044s"      //登陆时间
    otherInfo:""                    //其他
    userId:"AAE..."                 //用户ID
    isLogin:true                    //是否登陆，true/false
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    code : 1000                     //错误码
    message:"user is not exist"     //错误描述
}
```

##示例代码

```js
var alibaichuan = api.require('alibaichuan');
alibaichuan.showLogin(function(ret, err) {
    if (ret) {
        alert("登录success:" + JSON.stringify(ret));
    } else {
        alert("登录error:" + JSON.stringify(ret));
    }
});
```

##补充说明

    无

##可用性

    Android系统

    可提供的1.0.0及更高版本


#**getUserInfo**<div id="2"></div>

    获取已经登陆的用户的相关信息

    getUserInfo(function(ret, err))

##callback(ret,err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    userNick:"rocke"                //用户昵称
    avatarUrl:"http://..."          //用户头像
    authCode:"2mp9..."              //授权码
    loginTime:"1449932770044s"      //登陆时间
    otherInfo:""                    //其他
    userId:"AAE..."                 //用户ID
    isLogin:true                    //是否登陆，true/false
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    code : 90000                //错误码
    message:"Not logged in"     //错误描述
}
```

##示例代码

```js
var alibaichuan = api.require('alibaichuan');
alibaichuan.getUserInfo(function(ret, err) {
    if (ret) {
        alert("用户信息 ret - " + JSON.stringify(ret));
    } else {
        alert("用户信息 err - " + JSON.stringify(err));
    }
});
```

##补充说明

    无

##可用性

    Android系统

    可提供的1.0.0及更高版本


#**logout**<div id="3"></div>

    退出登陆

    logout(function(ret, err))

##callback(ret,err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    code : 0              //正确码
    message:"success"     //描述
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    code : 90000                //错误码
    message:"Not logged in"     //错误描述
}
```

##示例代码

```js
var alibaichuan = api.require('alibaichuan');
alibaichuan.logout(function(ret, err) {
    if (ret) {
        alert("ret - " + JSON.stringify(ret));
    } else {
        alert("err - " + JSON.stringify(err));
    }
});
```

##补充说明

    无

##可用性

    Android系统

    可提供的1.0.0及更高版本


#**openMyCart**<div id="4"></div>

    打开我的购物车

    openMyCart(function(ret, err))

##callback(ret,err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    code : 0              //正确码
    message:"success"     //描述
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    code : 90000                //错误码
    message:"Not logged in"     //错误描述
}
```

##示例代码

```js
var alibaichuan = api.require('alibaichuan');
alibaichuan.openMyCart(function(ret, err) {
    if (ret) {
        alert("ret - " + JSON.stringify(ret));
    } else {
        alert("err - " + JSON.stringify(err));
    }
});
```

##补充说明

    无

##可用性

    Android系统

    可提供的1.0.0及更高版本


#**myOrdersPage**<div id="5"></div>

    打开我的订单

    myOrdersPage(function(ret, err))

##callback(ret,err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    code : 0              //正确码
    message:"success"     //描述
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    code : 90000                //错误码
    message:"Not logged in"     //错误描述
}
```

##示例代码

```js
var alibaichuan = api.require('alibaichuan');
alibaichuan.myOrdersPage(function(ret, err) {
    if (ret) {
        alert("ret - " + JSON.stringify(ret));
    } else {
        alert("err - " + JSON.stringify(err));
    }
});
```

##补充说明

    无

##可用性

    Android系统

    可提供的1.0.0及更高版本


#**showTaokeItemById**<div id="6"></div>

    通过itemid打开宝贝

    showTaokeItemById({params}, function(ret, err))

##params

itemid：

- 类型：字符串
- 默认值：无
- 描述：宝贝的id，itemid为打开宝贝详情后，看到浏览器里有id一项，如"https://item.taobao.com/item.htm?id=45535180986",这里的id就是itemid

mmpid：

- 类型：字符串
- 默认值：无
- 描述：阿里妈妈的pid，如果你还没有开通 [阿里妈妈-淘宝联盟账号](http://media.alimama.com/user/limit_status.htm?spm=0.0.0.0.yoiYny)，要去阿里妈妈开通账号并且补全账号信息以及绑定支付宝, 因为分销的商品最后是返回到阿里妈妈的账号，并通过支付宝提现拿到的


##callback(ret,err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    code : 0              //正确码
    message:"success"     //描述
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    code : 90001                    //错误码
    message:"Parameter is null"     //错误描述
}
```

##示例代码

```js
var alibaichuan = api.require('alibaichuan');
var param = {
    itemid : "522997347023",
    mmpid : "mm_14421418_0_0"
};
alibaichuan.showTaokeItemById(param, function(ret, err) {
    if (ret) {
        alert("ret - " + JSON.stringify(ret));
    } else {
        alert("err - " + JSON.stringify(err));
    }
});
```

##补充说明

    无

##可用性

    Android系统

    可提供的1.0.0及更高版本


#**showTaokeItemByOpenId**<div id="7"></div>

    打开我的订单

    showTaokeItemById({params}, function(ret, err))

##params

openid：

- 类型：字符串
- 默认值：无
- 描述：商品openId，eg.AAHd5d-HAAeGwJedwSnHktBI

mmpid：

- 类型：字符串
- 默认值：无
- 描述：阿里妈妈的pid，如果你还没有开通 [阿里妈妈-淘宝联盟账号](http://media.alimama.com/user/limit_status.htm?spm=0.0.0.0.yoiYny)，要去阿里妈妈开通账号并且补全账号信息以及绑定支付宝, 因为分销的商品最后是返回到阿里妈妈的账号，并通过支付宝提现拿到的


##callback(ret,err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    code : 0              //正确码
    message:"success"     //描述
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    code : 90001                    //错误码
    message:"Parameter is null"     //错误描述
}
```

##示例代码

```js
var alibaichuan = api.require('alibaichuan');
var param = {
    openid : "AAGMLk9FACJvEVXfLXXUtbjt",
    mmpid : "mm_14421418_0_0"
};
alibaichuan.showTaokeItemByOpenId(param, function(ret, err) {
    if (ret) {
        alert("ret - " + JSON.stringify(ret));
    } else {
        alert("err - " + JSON.stringify(err));
    }
});
```

##补充说明

    无

##可用性

    Android系统

    可提供的1.0.0及更高版本


#**错误码**<div id="8"></div>

1. 0        请求成功

2. 90000    用户未登陆

3. 90001    参数为空

4. 其他，阿里返回的code和错误提示