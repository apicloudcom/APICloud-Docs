/*
Title: superID
Description: superID
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>

<div id="method-content">

<div class="outline">

[registerApp](#a1)
[obtainLoginView](#a2)
[logoutCurrentAccount](#a3)
[queryUserState](#a4)
[cancelAuthorization](#a5)
[updateAppUid](#a6)
[updateAppUserInfo](#a7)
[obtainFaceFeatureView](#a8)

</div>

#**概述**

superID封装了一登人脸登录的SDK，使用此模块可为应用提供「刷脸登录」功能，简化注册、登录流程。

十分钟让你的应用可以刷脸登录,一登刷脸登录SDK，可以为您的应用提供「刷脸登录」的功能。应用接入后，可以让用户体验更简单有趣的登录方式。应用可获得用户的昵称、头像、性别等用户资料，减少注册登录的流程。

一登SDK提供的所有接口调用均免费。


#配置

在```config.xml```中配置下列字段：

```
<feature name="SuperID">
    <param name="AppID" value="Swq1l7lzkZGBNYWFAwUV9S6o" />
    <param name="AppSecret" value="JnV6eFkzVPQ181rrkthQdwT6" />
</feature>
```

其中```AppID```和```AppSecret```为一登开发者中心（https://center.superid.me/developer/queryUserState）创建应用后获得


#**registerApp**<div id="a1"></div>

注册应用：```registerApp()```

##示例代码

```js
var superID = api.require('superID');
superID.registerApp();
```

##补充说明

注册应用，执行完```require```后必须马上执行

#**obtainLoginView**<div id="a2"></div>

弹出刷脸登录界面：```obtainLoginView({params}, callback(ret, err))```

##params

phone：

- 类型：数字
- 默认值：无
- 描述：传入用户的手机号码，作为一登账号，可不填

##callback(ret, err)

ret：

- 类型：JSON对象  用户信息说明

内部字段：

```js
{
  "userInfo": {
    "email": "yourtion@gmail.com",//邮箱
    "phone": 185XXXXXXXX; // 用户手机号
    "regioncode": "86",// 用户国家
    "avatar": "http://7rflwo.com5.z0.glb.qiniucdn.com/avatar/2015/06/01/zhvqog8pygb39kj.jpg", // 头像地址
    "name": "Yourtion", //用户昵称
    "persona": { // 用户画像信息
      "gender": "male",
      "tags": [
        "eyeglasses"
      ],
      "generation": "90s",
      "character": "reserved",
      "location": {
        "country": "CN",
        "province": "北京",
        "city": "北京"
      }
    }
  },
  "uid": "idbsapMIaW7sVXdCDs8UxD40AZ" //用户的uid
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    code:0       //错误码（详见错误码常量）
    Msg: ""      //错误描述
}
```

##示例代码

```js
var superID = api.require('superID');
superID.registerApp();
superID.obtainLoginView(callBack);
function callBack(ret, err){
    var msg = "登录成功：" + ret.userInfo.name;
    api.toast({
        Msg:msg
    });
}
```

##补充说明

调用此接口前应确保调用过一次registerApp接口，此接口需要访问网络，所以需要一段时间才能callBack得到结果

#**logoutCurrentAccount**<div id="a3"></div>

退出登录：```logoutCurrentAccount()```

##示例代码

```js
var superID = api.require('superID');
superID.logoutCurrentAccount();
```

#**queryUserState**<div id="a4"></div>

检查用户授权状态：```queryUserState({params}, callback(ret, err))```

##params

uid：

- 类型：字符串
- 默认值：无
- 描述：检测该uid是否已经授权，必填


##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
  State : "" //授权状态（UserHasAuth、UserNoAuth）
}

```

err：

- 类型：JSON对象

内部字段：

```js
{
    Msg:""      //错误描述
}
```

##示例代码

```js
var param = {
    uid:"idCIXkfV8BOeM7u2AjbK0MVihY!"
};
var superID = api.require('superID');
superID.registerApp();
superID.queryUserState(param,function(ret, err){
    api.toast({
        msg:ret.State
    });
});
```

##补充说明

调用此接口前应确保调用过一次registerApp接口，此接口需要访问网络，所以需要一段时间才能callBack得到结果


#**cancelAuthorization**<div id="a5"></div>

取消授权：```cancelAuthorization(callback)```

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
  Msg : "Succeed" //取消授权成功
}

```

err：

- 类型：JSON对象

内部字段：

```js
{
    code:0       //错误码（详见错误码常量）
    Msg: ""      //错误描述
}
```

##示例代码

```js
var superID = api.require('superID');
superID.registerApp();
superID.cancelAuthorization(function(ret, err){
    api.toast({
        msg:ret.Msg
    });
});
```

##补充说明

调用此接口前应确保调用过一次registerApp接口，此接口需要访问网络，所以需要一段时间才能callBack得到结果

#**updateAppUid**<div id="a6"></div>

更新uid：```updateAppUid({params},callback)```

##params

uid：

- 类型：字符串
- 默认值：无
- 描述：检测该uid是否已经授权，必填

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
  Msg : "Succeed" //取消授权成功
}

```

err：

- 类型：JSON对象

内部字段：

```js
{
    Msg: ""      //错误描述
}
```

##示例代码

```js
var param = {
    uid:"idCIXkfV8BOeM7u2AjbK0MVihY!"
};
var superID = api.require('superID');
superID.registerApp();
superID.queryUserState(param,function(ret, err){
    api.toast({
        msg:ret.State
    });
});
```

##补充说明

调用此接口前应确保调用过一次registerApp接口，此接口需要访问网络，所以需要一段时间才能callBack得到结果

#**updateAppUserInfo**<div id="a7"></div>

更新用户信息：```updateAppUserInfo({params},callback)```

##params

info：

- 类型：对象
- 默认值：无
- 描述：用户信息对象，必填

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
  Msg : "Succeed" //更新成功
}

```

err：

- 类型：JSON对象

内部字段：

```js
{
    Msg: ""      //错误描述
}
```

##示例代码

```js
var param = {
	info:{
		name: "SuperID",
		age: 25
	}
};
var superID = api.require('superID');
superID.registerApp();
superID.updateAppUserInfo(param,function(ret, err){
    api.toast({
        msg:ret.State
    });
});
```

##补充说明

调用此接口前应确保调用过一次registerApp接口，此接口需要访问网络，所以需要一段时间才能callBack得到结果

#**obtainFaceFeatureView**<div id="a8"></div>

获取人脸信息：```obtainFaceFeatureView(callback)```

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    "smiling": {
        "result": 0, 
        "score": 0.001059
    }, 
    "male": {
        "result": 1, 
        "score": 0.999986
    }, 
    "eyeglasses": {
        "result": 0, 
        "score": 0.001633
    }, 
    "sunglasses": {
        "result": 0, 
        "score": 0.005324
    }, 
    "age": 26.85, 
    "mustache": {
        "result": 0, 
        "score": 0.00102
    }, 
    "emotions": {
        "angry": 0.007319, 
        "calm": 0.792951, 
        "confused": 0.160389, 
        "disgust": 0.004511, 
        "happy": 0.016296, 
        "sad": 0.015238, 
        "surprised": 0.003295
    }, 
    "attractive": {
        "result": 0, 
        "score": 0.117668
    }, 
    "orientation": {
        "yaw": 3.852539, 
        "pitch": -0.84375, 
        "roll": -4.250381
    }, 
    "blink": {
        "result": 1, 
        "score": 0.515972
    }, 
    "mouth_open": {
        "result": 0, 
        "score": 0.409592
    }, 
    "components": {
        "left_eye": [
            170.37178, 
            327.428619
        ], 
        "right_eye": [
            295.026978, 
            332.592041
        ], 
        "nose": [
            222.983948, 
            385.265198
        ], 
        "mouth_left": [
            176.645065, 
            466.788452
        ], 
        "mouth_right": [
            276.454803, 
            468.780487
        ]
    }, 
    "position": {
        "top": 264, 
        "left": 134, 
        "right": 408, 
        "bottom": 538
    }, 
}

```


err：

- 类型：JSON对象

内部字段：

```js
{
    code:0       //错误码（详见错误码常量）
    Msg: ""      //错误描述
}
```

##示例代码

```js
var superID = api.require('superID');
superID.registerApp();
superID.obtainFaceFeatureView(function(ret, err){
    api.toast({
        msg:ret.age
    });
});
```
##补充说明

调用此接口前应确保调用过一次registerApp接口，此接口需要访问网络，所以需要一段时间才能callBack得到结果

开发者注册后，可申请开通的高级功能有【性别】、【年龄】、【微笑】、【带眼镜】、【胡须密度】、【表情】、【颜值】、【动作】、【闭眼】、【张嘴】、【人脸关键点】、【人脸检测框】、【国际短信】等，申请高级接口的流程如下：

1. 注册成为一登开发者

2. 在一登开发者中心创建应用

3. 在应用栏目中的【功能权限】勾选你需要的功能权限，填写信息，即可申请开通
 
</div>



<div id="const-content">

#**用户信息说明：**

参数  								| 说明
------------- 					  | -------------
name  						     | 一登用户的昵称，开发者可直接使用作为新用户注册时
avatar					     | 一登用户的头像 url，开发者可直接使用作为用户注册时的头像
phone								| 一登用户的手机号码
persona							| 一登用户的用户画像

参数  								| 说明
------------- 					| -------------
gender（性别）						| 男、女
generation（年代）				| 60后、70后、80后、90后、00后
character （性格）				| 含蓄、活泼、成熟、风趣、严肃、和蔼
location （常驻）					| 国家+城市
tags (外貌标签)					| 美、戴眼镜、有胡子..

#**人脸属性参数解析:**

人脸属性  			| 解析
------------- 	| -------------
smiling  			| 【微笑值】 result=1表示微笑，score表示微笑的程度
male  			  | 【性别】 result=1表示男性，score表示为男性的可信度，result=0表示女性
eyeglasses	   | 【是否戴眼镜】 result=1表示有戴，0表示没戴
sunglasses		| 【是否戴太阳眼镜】 result=1表示有戴，0表示没戴
age			  		| 【年龄】
mustache		  	| 【胡须密度】result=1表示有胡须，0表示没胡须，score表示有胡须的程度
emotions   	   | 【表情】包含生气、平静、困惑、愤怒、快乐、悲伤、惊喜7种情绪所占的分值，可以取最大值作为当前人脸的表情
attractive		| 【颜值】取值范围为0~1
orientation	  	| 【人脸旋转角】，是人脸眼中间和嘴中间的连线，与垂线的夹角
blink     	   | 【闭眼】 result=1表示闭眼，score表示闭眼的程度
mouth_open		| 【嘴巴张开度】 result=1表示嘴巴张开，score表示嘴巴张开的程度
components		| 【人脸关键点】 
position	  	   | 【人脸框】

