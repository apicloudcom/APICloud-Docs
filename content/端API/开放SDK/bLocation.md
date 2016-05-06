/*
Title: bLocation
Description: bLocation
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>
<div id="method-content">

<div class="outline">
[startLocation](#a1)

[stopLocation](#a2)
</div>

#**概述**

bLocation 封装了百度地图定位的 SDK。百度地图定位 SDK 是为移动端应用提供的一套简单易用的LBS定位服务接口，专注于为广大开发者提供最好的综合定位服务，通过使用百度定位SDK，开发者可以轻松为应用程序实现智能、精准、高效的定位功能。该套SDK免费对外开放，接口使用无次数限制。在使用前，您需先申请密钥（ak）才可使用。任何非营利性应用请直接使用，商业目的产品使用前请参考[使用须知](http://lbsyun.baidu.com/index.php?title=open/question)。在您使用百度地图 SDK之前，请先阅读[百度地图API使用条款](http://lbsyun.baidu.com/index.php?title=open/law)。

开发者使用本模块之前需先去[百度地图开放平台](http://lbsyun.baidu.com)申请开发者账号，创建自己的 APP 从而获取 ak，本模块所需的 ak 与 baiduMap 模块、bMap 模块所需的密钥可以相同。

***使用此模块之前 ios 必须先配置 config 文件，配置方法如下：***

- 名称：bLocation
- 参数：apiKey
- 配置示例:

```xml
  <feature name="bLocation">
    <param name="ios_api_key" value="81qz3dBYB5q2nGji4IYrawr1" />
  </feature>
```

- 字段描述:

    **apiKey**：在百度地图开放平台申请的 ak

***使用此模块之前 android 必须先配置 config 文件，配置方法如下：***

- 配置示例:

```xml
 <meta-data
     name="com.baidu.lbsapi.API_KEY"
     value="您的百度ak" />
```

- 字段描述:

    **apiKey**：在百度地图开放平台申请的 ak

**后台定位功能：**

本模块支持后台定位功能。由于系统限制，在 iOS 和 android 平台上表现有所不同。在 iOS 平台上，定位功能必须在 app 为当前激活使用状态，或者后台运行状态时。若将 app 从后台杀死，则本 app 的所有功能都被关闭，包括后台定位功能。若要集成后台定位功能，必须得[配置 config 文件](http://docs.apicloud.com/APICloud/技术专题/app-config-manual#14-2)，然后云编译或自定义 loader 方可。配置实例如下：

```xml
//配置一个后台定位功能：
<preference name="backgroundMode" value="location"/>

//配置多个后台运行功能，各值之间用竖线 | 隔开：
<preference name="backgroundMode" value="location | audio"/>
```
***注意：后台定位功能的缺点是耗电量大***

**后台上报功能：**

本模块支持在 app 进入后台后将定位信息持续上报给指定服务器功能，开发者只需配合使用 startLocation 接口内 autoStop 、 serviceUrl、interval 参数即可。上报数据为 JSON 格式，如下：

```js
{
    location: {                      //JSON对象；上报的当前位置信息
	    longitude: 116.213,          //数字类型；经度
	    latitude: 39.213             //数字类型；纬度
    },
    userId: '',                     //字符串类型；开发者自定义的用户id（通过startLocation接口传入模块）
    timestamp: 1396068155591        //数字类型；定位此位置信息时的时间戳
}
```

##**模块接口** 

**后台定位功能：**

本模块支持后台定位功能。由于系统限制，在 iOS 和 android 平台上表现有所不同。在 iOS 平台上，定位功能必须在 app 为当前激活使用状态，或者后台运行状态时。若将 app 从后台杀死，则本 app 的所有功能都被关闭，包括后台定位功能。若要集成后台定位功能，必须得[配置 config 文件](http://docs.apicloud.com/APICloud/技术专题/app-config-manual#14-2)，然后云编译或自定义 loader 方可。配置实例如下：

```xml
//配置一个后台定位功能：
<preference name="backgroundMode" value="location"/>

//配置多个后台运行功能，各值之间用竖线 | 隔开：
<preference name="backgroundMode" value="location | audio"/>
```
***注意：后台定位功能的缺点是耗电量大***

**后台上报功能：**

本模块支持在 app 进入后台后将定位信息持续上报给指定服务器功能，开发者只需配合使用 startLocation 接口内 autoStop 、 serviceUrl、interval 参数即可。上报数据为 JSON 格式，如下：

```js
{
    location: {                      //JSON对象；上报的当前位置信息
	    longitude: 116.213,          //数字类型；经度
	    latitude: 39.213             //数字类型；纬度
    },
    userId: '',                     //字符串类型；开发者自定义的用户id（通过startLocation接口传入模块）
    timestamp: 1396068155591        //数字类型；定位此位置信息时的时间戳
}
```

##**模块接口** 

#**startLocation**<div id="a1"></div>

开始定位

startLocation({params}, callback(ret, err))

##params

accuracy：

- 类型：字符串
- 描述：（可选项）定位精度，**信号不稳定时，定位精度过高，在 iOS 平台上会偶现定位失败的问题**
- 默认值：device_sensors
- 取值范围：
	- battery_saving：低功耗模式
	- device_sensors：仅设备（Gps）模式
	- hight_accuracy：高精度模式

filter：

- 类型：数字
- 描述：（可选项）位置更新所需最小距离（单位米）
- 默认值：1.0

autoStop：

- 类型：布尔
- 描述：（可选项）获取到位置信息后是否自动停止定位
- 默认值：true

report：

- 类型：JSON 对象
- 描述：（可选项）当 autoStop 为 false 时，本参数表示将当前位置信息上报的配置，若 autoStop 为 true，则本参数无意义。
- 内部字段：

```js
{      
    serverUrl: '',       //字符串类型；要上报的服务器地址
    userId: '',          //字符串类型；上报数据时携带的用户id（用于服务器端唯一标识用户）
    type: 'post'         //（可选项）字符串类型；上报的方式；默认值：post；取值范围如下：
                         // post：将位置信息已 post 的方式发送到指定服务器
                         // get：将位置信息放入 params 里，以get的形式发送给服务器
}
```

interval：

- 类型：数字类型
- 描述：（可选项）当 autoStop 为 false 时，本参数表示将当前位置信息上报给指定服务器和向前端回调的间隔时间，单位为妙（s）若 autoStop 为 true，则本参数无意义。
- 默认：30.0

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true,                //布尔类型；操作成功状态值，true|false
    location: {                  //JSON对象；上报的当前位置信息
	    longitude: 116.213,      //数字类型；经度
	    latitude: 39.213,        //数字类型；纬度
    },
    timestamp: 1396068155591    //数字类型；定位时的时间戳
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
    msg: '',                  //字符串类型；错误描述
    code:1                    //数字类型；错误码，取值范围如下：
                              //1：The operation couldn't be completed. (kCLErrorDomain error 1.
}
```

##示例代码

```js
var bLocation = api.require('bLocation');
bLocation.startLocation({
    accuracy: 'device_sensors',
    filter:1,
    autoStop: false,
    report: {
       userId:'123456789',
       serverUrl: "http://182.92.224.208/bjappcms/jeeadmin/jeecms/test.do?param=",
       type:'get'
    },
    interval: 100
}, function(ret, err){
    var sta = ret.status;
    if(sta){
	    var lat = ret.location.latitude;
	    var lon = ret.location.longitude;
	    var t = ret.timestamp;
        var str = '经度：'+ lon +'<br>';
        str += '纬度：'+ lat +'<br>';
        str += '更新时间：'+ t +'<br>';
        api.alert({msg: str});
    } else{
        api.alert({msg:err.msg});
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**stopLocation**<div id="a2"></div>

停止定位，当调用 startLocation 接口时 autoStop 参数传 false，则调用本接口可停止定位功能

stopLocation()

##示例代码

```js
var bLocation = api.require('bLocation');
bLocation.stopLocation();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本