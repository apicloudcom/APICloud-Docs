/*
Title: maketionCardReader
Description: maketionCardReader
*/

<p style="color: #ccc;margin-bottom: 30px;">来自于：脉可寻</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[auth](#1)

[isAuth](#2)

[clearAuth](#3)

[open](#4)

[getDataWithUuid](#5)

[getDataWithTime](#6)

[uploadImg](#7)

[getCardImg](#8)
</div>

#**概述**

maketionCardReader模块封装了脉可寻名片识别的sdk，可通过摄像头扫描名片读取名片信息。

在集成此模块之前可先配置config文件，也可不配置config文件直接从前端js将apiKey和apiSecret传入模块原生代码。在config里添加如下字段：

- 名称：maketionCardReader
- 参数：apiKey、apiSecret
- 描述：apiKey即是从脉可寻云名片识别服务器申请获得的appkey，apiSecret即是从脉可寻云名片识别服务器申请获得的secure	

配置示例：

```js
<feature name="maketionCardReader">
					<param name="apiKey" value=" AD1B0E942E0D7240CCFD355A28476E7E" />
					<param name="apiSecret" value="b2235093fac07c7bb4fdace94ca97007cd336ba8fccbcdf3e8e575e60e28d23e5fb3d972a203fd7e4553380a1233f6ff96e034650228c557cf6313de7c3ee9f7" />
</feature>
```

字段描述：

1、apiKey：申请获得的appKey

2、apiSecret：申请获得的secure


#**auth**<div id="1"></div>

授权

auth({params}, callback(ret, err))

##params

uid：

- 类型：字符串
- 默认值：12345
- 描述：合作伙伴客户标识，可为空

apiKey：

- 类型：字符串
- 默认值：无
- 描述：从脉可寻名片识别服务器申请获得，可为空，若为空则从[config.xml](/APICloud/技术专题/app-config-manual)读取

apiSecret：

- 类型：字符串
- 默认值：无
- 描述：从脉可寻名片识别服务器申请获得，可为空，若为空则从[config.xml](/APICloud/技术专题/app-config-manual)读取

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	status: //授权成功状态值
	uid：  //统用户标识(获取数据可根据此标识来获取)
}
```

err：

- 类型：JSON 对象

内部字段：

```js
{
	msg: //错误描述
	code：//错误码
}
```

##示例代码

```js
var maketionCardReader = api.require('maketionCardReader');
maketionCardReader.auth({
    uid:123456
}, function(ret, err){
    if(ret.status){
        api.alert({
            title: "提示",
            msg:ret.uid
        });
    }else{
        api.alert({
            title: "出错了",
            msg: err.msg
        });
    }
});
```

##补充说明

授权用户

##可用性

iOS系统

可提供的1.0.0及更高版本

#**isAuth**<div id="2"></div>

判断是否授权验证通过

isAuth(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	status:       //是否授权验证成功
}
```

##示例代码

```js
var maketionCardReader = api.require('maketionCardReader');

maketionCardReader.isAuth(function(ret, err){
    if(ret.status){
        api.alert({
            title: "提示",
            msg:"验证成功"
        });
    }
});
```

##补充说明

判断是否授权

##可用性

iOS系统

可提供的1.0.0及更高版本

#**clearAuth**<div id="3"></div>

清除验证信息

clearAuth(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	status:       //是否清除成功
}
```

##示例代码

```js
var maketionCardReader = api.require('maketionCardReader');

maketionCardReader.clearAuth(function(ret, err){
    if(ret.status){
        api.alert({
            title: "提示",
            msg:"清除验证成功"
        });
    }
});
```

##补充说明

清除验证信息

##可用性

iOS系统

可提供的1.0.0及更高版本

#**open**<div id="4"></div>

拍照并上传脉可寻云识别服务器

open(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	state：  //上传图片状态值，字符串类型，取值范围：
	uploading：开始上传
	uploaded：上传完成
	err：    上传错误
	uuid：         //图片标识，上传完成后可以根据UUID获取数据
}
```

err：

- 类型：JSON 对象

内部字段：

```js
{
	msg:       //错误描述
}
```

##示例代码

```js
var maketionCardReader = api.require('maketionCardReader');

maketionCardReader.open(function(ret, err){
    api.alert({
        title: "提示",
        msg:ret.state+'*'+ret.uuid
    });
});
```

##补充说明

打开摄像头拍照并上传

##可用性

iOS系统

可提供的1.0.0及更高版本


#**getDataWithUuid**<div id="5"></div>

根据uuid获取数据

getDataWithUuid({params}, callback(ret, err))

##params

uuids：

- 类型：数组对象
- 默认值：无
- 描述：拍照上传后获取的标识组成的数组，不可为空

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	status:       //获取数据成功状态值
	datas：		  //用户名片数据组成的数组
}
```

err：

- 类型：JSON 对象

内部字段：

```js
{
	msg:       //错误描述
	code：	   //错误码
}
```

##示例代码

```js
var maketionCardReader = api.require('maketionCardReader');

maketionCardReader.getDataWithUuid({
    uuids:['987654']
}, function(ret, err){
    if(ret.status){
        api.alert({
            title: "提示",
            msg:ret.datas
        });
    }else{
        api.alert({
            title: "出错了",
            msg: err.msg
        });
    }
});
```

##补充说明

无

##可用性

iOS系统

可提供的1.0.0及更高版本

#**getDataWithTime**<div id="6"></div>

根据时间获取数据

getDataWithTime({params}, callback(ret, err))

##params

time：

- 类型：字符串
- 默认值：0
- 描述：为时间戳，当前时间距1970年秒数，可为空，若0表示全部数据

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	status:       //获取数据成功状态值
	datas：		  //用户名片数据组成的数组
}
```

err：

- 类型：JSON 对象

内部字段：

```js
{
	msg:       //错误描述
	code：//错误码
}
```

##示例代码

```js
var maketionCardReader = api.require('maketionCardReader');

maketionCardReader.getDataWithTime({
    time: 187656
}, function(ret, err){
    if(ret.status){
        api.alert({
            title: "提示",
            msg:ret.datas
        });
    }else{
        api.alert({
            title: "出错了",
            msg: err.msg
        });
    }
});
```

##补充说明

无

##可用性

iOS系统

可提供的1.0.0及更高版本

#**uploadImg**<div id="7"></div>

用户图片上传错误，重新上传

uploadImg(params,callback(ret, err))

##params

uuid：

- 类型：字符串
- 默认值：无
- 描述：图片标识，上次上传过程事件返回，不可为空

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	state：  //上传图片状态值，字符串类型，取值范围：
	uploading：开始上传
	uploaded：上传完成
	err：    上传错误
	uuid：         //图片标识，上传完成后可以根据UUID获取数据
}
```

err：

- 类型：JSON 对象

内部字段：

```js
{
	msg:       //错误描述
}
```

##示例代码

```js
var maketionCardReader = api.require('maketionCardReader');

maketionCardReader.uploadImg(function(ret, err){
    api.alert({
        title: "提示",
        msg:ret.state+'*'+ret.uuid
    });
});
```

##补充说明

无

##可用性

iOS系统

可提供的1.0.0及更高版本

#**getCardImg**<div id="8"></div>

获取名片原图

getCardImg(params,callback(ret, err))

##params

uuid：

- 类型：字符串
- 默认值：无
- 描述：图片上传过程事件返回或获取名片数据中，不可为空

save：

- 类型：JSON 对象
- 默认值：见内部字段
- 描述：获取的图片保存位置，可为空

内部字段：

```js
{
	album:            //布尔值，是否保存到系统相册，默认false，可为空
	imgPath:          //保存的文件路径,字符串类型，无默认值,可为空,空则不保存若路径不存在文件夹则创建此目录
	imgName:         //保存的图片名字，字符串类型，无默认值,可为空,空则不保存支持png和jpg格式，若不指定格式，则默认png
}
```

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	status：  //获取图片状态值
}
```
err：

- 类型：JSON 对象

内部字段：

```js
{
	msg:       //错误描述
}
```

##示例代码

```js
var maketionCardReader = api.require('maketionCardReader');

maketionCardReader.getCardImg({
    uuid: "989898",
    save: "fs://test.png"
},function(ret, err){
    api.alert({
        title: "提示",
        msg:ret.status
    });
});
```

##补充说明

无

##可用性

iOS系统

可提供的1.0.0及更高版本
