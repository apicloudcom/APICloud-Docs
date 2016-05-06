/*
Title: baiduLocation
Description: baiduLocation
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>
<div id="method-content">


<div class="outline">
[startLocation](#a1)

[stopLocation](#a2)

[getLocation](#a3)
</div>

#**概述**

baiduLocation 封装了百度地图定位的 SDK。百度地图定位 SDK 是为移动端应用提供的一套简单易用的LBS定位服务接口，专注于为广大开发者提供最好的综合定位服务，通过使用百度定位SDK，开发者可以轻松为应用程序实现智能、精准、高效的定位功能。该套SDK免费对外开放，接口使用无次数限制。在使用前，您需先申请密钥（ak）才可使用。任何非营利性应用请直接使用，商业目的产品使用前请参考[使用须知](http://lbsyun.baidu.com/index.php?title=open/question)。在您使用百度地图Android SDK之前，请先阅读[百度地图API使用条款](http://lbsyun.baidu.com/index.php?title=open/law)。

开发者使用本模块之前需先去[百度地图开放平台](http://lbsyun.baidu.com)申请开发者账号，创建自己的 APP 从而获取 ak，本模块所需的 ak 与 baiduMap 模块、bMap 模块所需的密钥可以共用。

***使用此模块之前必须先配置  config 文件，配置方法如下：***

- 名称：baiduLocation
- 参数：apiKey
- 配置示例:

```xml
  <feature name="baiduLocation">
    <param name="apiKey" value="f7Is0dWLom2q6rV3ZfFPZ1aa" />
  </feature>
```

- 字段描述:

    **apiKey**：在百度地图开放平台申请的 ak

如果不配置 [config.xml](/APICloud/技术专题/app-config-manual) 则模块会去读 baiduMap 模块的 key（其实两个key都是在百度地图开放平台申请的同一个key）。但 baiduMap 模块现已停止更新，用bMap模块替换。所以最好还是每个模块单独配置每个模块的key，模块之间相互独立，互不干涉依赖。

注意：getLocation 接口无法设置 accuracy、filter、autoStop 这些参数，当调用getLocation 时，模块底层会先做个判断，如果已经调用过 startLocation 并且已经定位成功获取位置信息，则将此位置信息返回（所以这个位置信息有很大可能不是实时的）。若没调用过startLocation 则模块内部自己先 startLocation，此时 accuracy、filter、autoStop 这些参数取默认值。定位到信息后则返回定位到的信息。所以建议先调用 startLocation 再getLocation。

##**模块接口**

#**startLocation**<div id="a1"></div>

开始定位

startLocation({params}, callback(ret, err))
##params
accuracy：

- 类型：字符串
- 默认值：100m
- 描述：精度（详见[精度](!Constant)常量），不能为空

filter：

- 类型：数字
- 默认值：1.0
- 描述：位置更新所需最小距离（单位米）

autoStop：

- 类型：布尔
- 默认值：true
- 描述：获取到位置信息后是否自动停止定位

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
    status:true                //操作成功状态值
    longitude:116.213          //经度
    latitude:39.213            //纬度
    timestamp:1396068155591    //时间戳
}
```

err：

- 类型：JSON 对象

内部字段：

```js
{
    msg:""    //错误描述
}
```

##示例代码

```js
var baiduLocation = api.require('baiduLocation');
baiduLocation.startLocation({
    accuracy: '100m',
    filter: 1,
    autoStop: true
}, function(ret, err){        
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##补充说明

开始定位

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**stopLocation**<div id="a2"></div>

停止定位

stopLocation()

##示例代码

```js
var baiduLocation = api.require('baiduLocation');
baiduLocation.stopLocation();
```

##补充说明

停止定位

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**getLocation**<div id="a3"></div>

获取位置信息

getLocation(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
    longitude:116.213           //经度
    latitude:39.213             //纬度
    timestamp:1396068155591     //时间戳
}
```

err：

- 类型：JSON 对象

内部字段：

```js
{
    msg:""    //错误描述
}
```

##示例代码

```js
var baiduLocation = api.require('baiduLocation');
baiduLocation.getLocation(function(ret, err){     
    if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##补充说明

获取位置信息

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
</div>

<div id="const-content">
<div class="outline">
[精度](#a100)
</div>

#**精度**<div id="a100"></div>

定位精度，定位时只返回精度范围内的坐标。字符串类型

##取值范围：

- 10m
- 100m
- 1km
- 3km
</div>