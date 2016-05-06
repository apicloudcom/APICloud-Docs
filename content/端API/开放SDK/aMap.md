/*
Title: aMap
Description: 高德地图
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

##基础类

<div class="outline">
[open](#m1)
[close](#m2)
[show](#m3)
[hide](#m4)
[setRect](#m44)
[getLocation](#m5)
[stopLocation](#m501)
[getCoordsFromName](#m6)
[getNameFromCoords](#m7)
[getDistance](#m8)
[showUserLocation](#m9)
[setTrackingMode](#m10)
[setCenter](#m11)
[getCenter](#m111)
[setZoomLevel](#m12)
[getZoomLevel](#m13)
[setMapAttr](#m14)
[setRotation](#m15)
[getRotation](#m16)
[setOverlook](#m17)
[getOverlook](#m18)
[setRegion](#m19)
[getRegion](#m20)
[setScaleBar](#m21)
[setCompass](#m22)
[setLogo](#n22)
[isPolygonContainsPoint](#m23)
[interconvertCoords](#m24)
[addEventListener](#m25)
[removeEventListener](#m26)
</div>

##标注、气泡类

<div class="outline">
[addAnnotations](#m27)
[getAnnotationCoords](#m28)
[setAnnotationCoords](#m29)
[annotationExist](#m30)
[setBubble](#m31)
[popupBubble](#m32)
[addBillboard](#m33)
[addMobileAnnotations](#m34)
[moveAnnotation](#m35)
[removeAnnotations](#m36)
</div>

##覆盖物类

<div class="outline">
[addLine](#m37)
[addCircle](#m38)
[addPolygon](#m39)
[addImg](#m40)
[removeOverlay](#m41)
</div>

##搜索类

<div class="outline">
[searchRoute](#m43)
[drawRoute](#m44)
[removeRoute](#m45)
[searchBusRoute](#m46)
[drawBusRoute](#m47)
[removeBusRoute](#m48)
[searchInCity](#m49)
[searchNearby](#m50)
[searchInPolygon](#m51)  
[autocomplete](#m52)  
</div>

##离线地图类

<div class="outline">
[getProvinces](#m53)
[getMunicipalities](#m54)
[getNationWide](#m55)
[getAllCities](#m56)
[getVersion](#m57)
[downloadRegion](#m58)
[isDownloading](#m59)
[pauseDownload](#m60)
[cancelAllDownload](#m61)  
[clearDisk](#m62)
[checkNewestVersion](#m63)
[reloadMap](#m64)
</div>

#**概述**

**高德地图简介**

高德地图 是国内一流的免费地图导航产品，也是基于位置的生活服务功能最全面、信息最丰富的手机地图，由国内最大的电子地图、导航和LBS服务解决方案提供商高德软件（纳斯达克AaMap）提供。高德地图采用领先的技术为用户打造了最好用的“活地图”，不管在哪、去哪、找哪、怎么去、想干什么一图在手，统统搞定，省电省流量更省钱，堪称最完美的生活出行软件。地图数据覆盖中国大陆及香港澳门,遍及337个地级2857个县级以上行政区划单位；导航支持GPS、基站、网络等多种方式一键定位。美食、酒店、演出、商场等各种深度POI点达2600多万条，衣食住行吃喝玩乐全方位海量生活信息可供搜索查询。自动生成“最短”“最快”“最省钱”等多种路线规划以供选择，可根据实时路况选择最优公交/驾车出行路线。

**高德地图特色功能**

动态导航

交通路况实时播报，智能计算到达目的地所需的时间，避堵路线方案规划

离线下载

3D离线地图，分地区下载地图包，全国地图包、全国概要图

地图搜索

热门地点、线路搜索，公交、自驾出行线路规划，公交、火车、天气查询服务

全新引擎

最新3D版本，360度旋转视角，矢量数据传送，观看更流畅、更清晰。

兴趣点

餐饮、住宿、优惠、演出、团购全覆盖，海量兴趣点随意搜

**模块概述**

aMap 模块封装了高德地图的原生 SDK，集成了高德地图常用基本接口；手机版原生地图，不同于 js 地图，相对于js地图而言，本模块封装的原生手机地图更加流畅迅速、动画效果更加逼真。使用此模块可轻松把高德地图集成到自己的app内，实现高德地图常用的定位、关键字搜索、周边搜索、自定义标注及气泡、查公交路线等各种功能；另外本模块已支持高德地图离线版本。

若某些带UI的接口不能满足开发设计需求，开发者（借助于原生开发者）可在本模块基础上修改少量原生代码，随心所欲的自定义高德地图所具有的原生功能，简单、轻松、快捷、高效、迅速集成高德地图，将自己的 app 和高德地图实现无缝链接。模块原生代码开源地址为：[https://github.com/apicloudcom/moduleCode/aMap](https://github.com/apicloudcom/aMap)

**模块使用攻略**

***注意事项***

本模块内带动画效果的接口不可同时调用（两个以上），需要设置延迟（`setTimeout`）处理。

***使用此模块之前必须先配置  config 文件，配置方法如下：***

- 名称：aMap
- 参数：android_api_key、ios_api_key
- 备注：同一个 App 需要同时支持 iOS 和 Android 平台，必须单独申请各自的 apiKey，并同时配置在 config 文件中
- 配置示例:

```xml
  <feature name="aMap">
    <param name="android_api_key" value="f7Is0dWLom2q6rV3ZfFPZ1aa" />
    <param name="ios_api_key" value="81qz3dBYB5q2nGji4IYrawr1" />
  </feature>
```

- 字段描述:

    **android_api_key**：在高德地图开放平台申请的 Android 端 AK

    **ios_api_key**：在高德地图开放平台申请的 IOS 端 AK
    
##**模块接口**

<div id="m1"></div>

#**open**

打开高德地图

open({params}, callback(ret, err))

##params

rect：

- 类型：JSON 对象
- 描述：（可选项）模块的位置及尺寸
- 内部字段：

```js
{
    x: 0,   //（可选项）数字类型；地图左上角的 x 坐标（相对于所属的 Window 或 Frame）；默认：0
    y: 0,   //（可选项）数字类型；地图左上角的 y 坐标（相对于所属的 Window 或 Frame）；默认：0
    w: 320, //（可选项）数字类型；地图的宽度；默认：所属的 Window 或 Frame 的宽度
    h: 480  //（可选项）数字类型；地图的高度；默认：所属的 Window 或 Frame 的高度
}
```

center：

- 类型：数字
- 描述：（可选项）打开地图时设置的中心点经纬度，若不传则默认打开北京市为中心的地图
- 内部字段：

```js
{
    lon: 116.213,       //数字类型；打开地图时设置的中心点经度
    lat: 39.213         //数字类型；打开地图时设置的中心点纬度
}
```

zoomLevel：

- 类型：数字
- 描述：（可选项）设置高德地图缩放等级，取值范围：3-18级
- 默认值：10

showUserLocation：

- 类型：布尔
- 描述：（可选项）是否在地图上显示用户位置
- 默认值：true

fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window

fixed:

- 类型：布尔
- 描述：（可选项）模块是否随所属 window 或 frame 滚动
- 默认值：true（不随之滚动）

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true	 //布尔型；true||false
}
```

##示例代码

```js
var aMap = api.require('aMap');
aMap.open({
    rect: {
        x: 0,
        y: 0,
        w: 320,
        h: 300
    },
    showUserLocation: true,
    zoomLevel: 11,
    center: {
       lon: 116.4021310000,
       lat: 39.9994480000
    },
    fixedOn: api.frameName,
    fixed: true
}, function(ret, err){        
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m2"></div>

#**close**

关闭高德地图

close()

##示例代码

```js
var aMap = api.require('aMap');
aMap.close();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m3"></div>

#**show**

显示高德地图

show()

##示例代码

```js
var aMap = api.require('aMap');
aMap.show();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m4"></div>

#**hide**

隐藏高德地图

hide()

##示例代码

```js
var aMap = api.require('aMap');
aMap.hide();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m44"></div>

#**setRect**

重设地图的显示区域

setRect({params})

##params

rect：

- 类型：JSON 对象
- 描述：（可选项）模块的位置及尺寸
- 内部字段：

```js
{
    x: 0,   //（可选项）数字类型；地图左上角的 x 坐标（相对于所属的 Window 或 Frame）；默认：原值
    y: 0,   //（可选项）数字类型；地图左上角的 y 坐标（相对于所属的 Window 或 Frame）；默认：原值
    w: 320, //（可选项）数字类型；地图的宽度；默认：原值
    h: 480  //（可选项）数字类型；地图的高度；默认：原值
}
```

##示例代码

```js
var aMap = api.require('aMap');
aMap.setRect({
    rect: {
        x: 0,
        y: 0,
        w: 320,
        h: 300
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m5"></div>

#**getLocation**

获取当前位置信息，若要支持后台定位需[配置 [config.xml](/APICloud/技术专题/app-config-manual) 文件 location 字段](http://docs.apicloud.com/APICloud/技术专题/app-config-manual#14-2)。**调用本接口需先 open，在ios 平台上 showUserLocation 为 false 时此接口不可用**

getLocation({params}, callback(ret, err))

##params

autoStop：

- 类型：布尔
- 描述：（可选项）获取到位置信息后是否自动停止定位
- 默认值：true

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true,               //布尔型；true||false
    lon: 116.213,               //数字类型；经度
    lat: 39.213,                //数字类型；纬度
    timestamp: 1396068155591,   //数字类型；时间戳
    heading:200,                //数字类型；设备方向，取值范围：0.0（正北） - 359.9 
}
```

##示例代码

```js
var aMap = api.require('aMap');
aMap.getLocation(function(ret, err){      
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m501"></div>

#**stopLocation**

停止定位

stopLocation()

##示例代码

```js
var aMap = api.require('aMap');
aMap.stopLocation();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m6"></div>

#**getCoordsFromName**

根据地址查找经纬度，**无需调用 open 接口即可使用**

getCoordsFromName({params}, callback(ret, err))

##params

city：

- 类型：字符串
- 描述：所要搜索的地址所在的城市，cityname（中文或中文全拼）、citycode、adcode

address：

- 类型：字符串
- 描述：完整的地址信息

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true,        //布尔型；true||false
    lon: 116.351,        //数字类型；地址所在经度
    lat: 39.283          //数字类型；地址所在纬度
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
    code: 1           //数字类型；错误码
    msg:              //字符串类型；错误描述
}
```

##示例代码

```js
var aMap = api.require('aMap');
aMap.getCoordsFromName({
    city: '北京',
    address: '天安门'
}, function(ret, err){     
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m7"></div>

#**getNameFromCoords**

根据经纬度查找地址信息，**无需调用 open 接口即可使用**

getNameFromCoords({params}, callback(ret, err))

##params

lon：

- 类型：数字
- 描述：经度

lat：

- 类型：数字
- 描述：纬度

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true,              //布尔型；true||false
    address: '',               //字符串类型；地址信息
    state: '',                 //字符串类型；省份
    city: '',                  //字符串类型；城市
    district: '',              //字符串类型；县区
    street: '',                //字符串类型；街道名
    number: ''                 //字符串类型；门牌号
    thoroughfare: ''           //字符串类型；大道
}
```

##示例代码

```js
var aMap = api.require('aMap');
aMap.getNameFromCoords({
    lon: 116.384767,
    lat: 39.989539
}, function(ret, err){     
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m8"></div>

#**getDistance**

获取地图两点之间的距离，**无需调用 open 接口即可使用**

getDistance({params}, callback(ret, err))

##params

start：

- 类型：JSON 对象
- 描述：起点经纬度
- 内部字段：

```js
{
    lon: 106.486654,    //数字类型；起点的经度
    lat: 29.490295      //数字类型；起点的纬度
}
```

end：

- 类型：JSON 对象
- 描述：终点经纬度
- 内部字段：

```js
{
    lon: 106.581515,    //数字类型；终点的经度
    lat: 29.615467      //数字类型；终点的纬度
}
```

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true,              //布尔型；true||false
    distance: 16670.90         //数字类型；两点之间的距离，单位：米
}
```

##示例代码

```js
var aMap = api.require('aMap');
aMap.getDistance({
    start: {
        lon: 106.486654,
        lat: 29.490295
    },
    end: {
        lon: 106.581515,
        lat: 29.615467
    }
}, function(ret, err){     
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m9"></div>

#**showUserLocation**

是否在地图上显示用户位置

showUserLocation({params})

##params

isShow：

- 类型：布尔
- 描述：（可选项）是否显示用户位置
- 默认值：true

##示例代码

```js
var aMap = api.require('aMap');
aMap.showUserLocation({
    isShow: true
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m10"></div>

#**setTrackingMode**

设置跟踪类型

setTrackingMode({params})

##params

trackingMode：

- 类型：字符串
- 描述：（可选项）用户当前位置显示形式
- 默认值：none
- 取值范围：
    - none（不追踪用户的 location 更新）
    - follow（追踪用户的 location 更新）
    - heading（追踪用户的 location 与 heading 更新）

animation：

- 类型：布尔类型
- 描述：（可选项）设置地图的当前位置标记的追踪状态时，是否带动画效果，**暂仅支持  IOS 平台**
- 默认：true

##示例代码

```js
var aMap = api.require('aMap');
aMap.setTrackingMode({
    animation: false,
    trackingMode: 'none'
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m11"></div>

#**setCenter**

根据经纬度设置高德地图中心点

setCenter({params})

##params

coords：

- 类型：JSON 对象
- 描述：（可选项）中心点的经纬度
- 内部字段：

```js
{
    lon: 116.404,       //（可选项）数字类型；设置中心点的经度
    lat: 39.915         //（可选项）数字类型；设置中心点的纬度
}
```

animation：

- 类型：布尔类型
- 描述：（可选项）设置地图的中心点时，是否带动画效果
- 默认：true

##示例代码

```js
var aMap = api.require('aMap');
aMap.setCenter({
    coords: {
        lon: 116.404,
        lat: 39.915
    },
    animation:false
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m111"></div>

#**getCenter**

获取高德地图中心点坐标

getCenter(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    lon: 116.404,       //数字类型；地图中心点的经度
    lat: 39.915         //数字类型；地图中心点的纬度
}
```

##示例代码

```js
var aMap = api.require('aMap');
aMap.getCenter(function(ret, err){        
    if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m12"></div>

#**setZoomLevel**

设置高德地图缩放等级

setZoomLevel({params})

##params

level：

- 类型：数字
- 描述：（可选项）地图比例尺级别，取值范围：0.01-20
- 默认值：10

animation：

- 类型：布尔类型
- 描述：（可选项）地图缩放时，是否带动画效果
- 默认：true

##示例代码

```js
var aMap = api.require('aMap');
aMap.setZoomLevel({
    level: 10,
    animation: true
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m13"></div>

#**getZoomLevel**

获取地图缩放级别（0.01-20）

getZoomLevel(callback(ret, err))

##callback

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    level: 11           //数字类型；地图当前缩放级别
}
```

##示例代码

```js
var aMap = api.require('aMap');
aMap.getZoomLevel(function(ret, err){     
    if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m14"></div>

#**setMapAttr**

设置高德地图相关属性

setMapAttr({params})

##params

type:

- 类型：字符串
- 描述：（可选项）设置地图类型
- 默认值：'standard'
- 取值范围：
    - standard（标准地图）
    - satellite（卫星地图）
    - night（夜间模式）

trafficOn：

- 类型：布尔
- 描述：（可选项）是否打开实时路况
- 默认值：false

zoomEnable：

- 类型：布尔
- 描述：（可选项）捏合手势是否可以缩放地图
- 默认值：true

scrollEnable：

- 类型：布尔
- 描述：（可选项）拖动手势是否可以移动地图
- 默认值：ture

overlookEnabled：

- 类型：布尔
- 描述：（可选项）是否支持俯视旋转
- 默认值：ture


rotateEnabled：

- 类型：布尔
- 描述：（可选项）是否支持平面旋转
- 默认值：ture

building：

- 类型：布尔
- 描述：（可选项）是否隐藏楼块，**俯视角度不为零时的楼快效果，Android 平台上默认打开状态，且不可改变**
- 默认值：false

##示例代码

```js
var aMap = api.require('aMap');
aMap.setMapAttr({
    type: 'standard',
    trafficOn: true,
    zoomEnable: false,
    scrollEnable: false,
    building: true,
    overlookEnabled: false,
    rotateEnabled: false
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m15"></div>

#**setRotation**

设置高德地图旋转角度(逆时针为正向)

setRotation({params})

##params

degree：

- 类型：数字
- 描述：（可选项）地图旋转角度，取值范围：-180° - 180°
- 默认值：0

animation：

- 类型：布尔
- 描述：（可选项）地图旋转时，是否带动画效果
- 默认：true

duration：

- 类型：数字
- 描述：（可选项）地图旋转动画时长，单位秒（s）
- 默认：0.3

##示例代码

```js
var aMap = api.require('aMap');
aMap.setRotation({
    degree: 30,
    animation: true,
    duration: 0.3
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m16"></div>

#**getRotation**

获取地图当前旋转角度

getRotation(callback(ret, err))

##callback

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    rotation: 11           //数字类型；地图当前旋转角度
}
```

##示例代码

```js
var aMap = api.require('aMap');
aMap.getRotation(function(ret){
    alert(JSON.stringify(ret.level));
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m17"></div>

#**setOverlook**

设置地图俯视角度(范围为[0.f, 60.f])

setOverlook({params})

##params

degree：

- 类型：数字
- 描述：（可选项）地图俯视角度，取值范围：0° - 60°
- 默认值：0

animation：

- 类型：布尔
- 描述：（可选项）地图俯视角度转动时，是否带动画效果
- 默认：true

duration：

- 类型：数字
- 描述：（可选项）地图俯视角度转动动画时长，单位秒（s）
- 默认：0.3

##示例代码

```js
var aMap = api.require('aMap');
aMap.setOverlook({
    degree: 30,
    animation: true,
    duration: 0.3
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m18"></div>

#**getOverlook**

获取地图当前俯视角度

getOverlook(callback(ret, err))

##callback

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    overlook: 11           //数字类型；地图当前俯视角度
}
```

##示例代码

```js
var aMap = api.require('aMap');
aMap.getOverlook(function(ret){
    alert(JSON.stringify(ret.level));
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m19"></div>

#**setRegion**

设置地图显示范围（矩形区域）

setRegion({params})

##params

lbLon：

- 类型：数字
- 描述：矩形区域左下角的经度

lbLat：

- 类型：数字
- 描述：矩形区域左下角的纬度

rtLon：

- 类型：数字
- 描述：矩形区域右上角的经度

rtLat：

- 类型：数字
- 描述：矩形区域右上角的纬度

animation：

- 类型：布尔类型
- 描述：（可选项）设置地图的区域时，是否带动画效果
- 默认：true

##示例代码

```js
var aMap = api.require('aMap');
aMap.setRegion({
    lbLon: 116.027143, 
    lbLat: 39.772348, 
    rtLon: 116.832025, 
    rtLat: 40.126349,
    animation: true
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m20"></div>

#**getRegion**

获取地图显示范围（矩形区域）

getRegion(callback(ret, err))

##callback

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true,                //布尔型；true||false
    lbLon: 116.027143,           //数字类型；矩形区域左下角的经度
    lbLat: 39.772348,            //数字类型；矩形区域左下角的纬度
    rtLon: 116.832025,           //数字类型；矩形区域右上角的经度
    rtLat: 40.126349             //数字类型；矩形区域右上角的纬度  
}
```

##示例代码

```js
var aMap = api.require('aMap');
aMap.getRegion(function(ret){
    if(ret.status){
        alert(JSON.stringify(ret));
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m21"></div>

#**setScaleBar**

设置高德地图比例尺

setScaleBar({params})

##params

show：

- 类型：布尔
- 描述：（可选项）是否显示比例尺
- 默认值：false

position：

- 类型：JSON 对象
- 描述：（可选项）比例尺的位置，设定坐标以地图左上角为原点，**在 Android 平台上为固定位置，本参数无效**
- 内部字段：
```js
{ 
    x: 0,   //（可选项）数字类型；比例尺左上角的 x 坐标（相对于地图）；默认：0
    y: 0    //（可选项）数字类型；比例尺左上角的 y 坐标（相对于地图）；默认：0
}
```

##示例代码

```js
var aMap = api.require('aMap');
aMap.setScaleBar({
    show: true,
    position: {
      x:100,
      y:100
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m22"></div>

#**setCompass**

设置高德地图指南针

setCompass({params})

##params

show：

- 类型：布尔
- 描述：（可选项）是否显示指南针
- 默认值：false

position：

- 类型：JSON 对象
- 描述：（可选项）指南针的位置，设定坐标以地图左上角为原点，**在 Android 平台上为固定位置，本参数无效**
- 内部字段：
```js
{ 
    x: 0,   //（可选项）数字类型；指南针左上角的 x 坐标（相对于地图）；默认：0
    y: 0    //（可选项）数字类型；指南针左上角的 y 坐标（相对于地图）；默认：0
}
```

img：

- 类型：布尔
- 描述：（可选项）自定义指南针图标图片路径，要求本地路径（fs://、widget://），**Android 平台上忽略本参数**
- 默认值：高德地图默认图标

##示例代码

```js
var aMap = api.require('aMap');
aMap.setCompass({
    show: true,
    img: 'widget://res/compass.png',
    position: {
      x:100,
      y:100
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="n22"></div>

#**setLogo**

设置高德地图 logo 的位置

setLogo({params})

##params

position：

- 类型：字符串
- 默认：right
- 描述：（可选项）高德地图 logo 的位置，取值范围如下：
	- left：地图左下角
	- center：地图底部居中
	- right：地图右下角

##示例代码

```js
var aMap = api.require('aMap');
aMap.setLogo({
    position: 'right'
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m23"></div>

#**isPolygonContainsPoint**

判断已知点是否在指定的多边形区域内

isPolygonContainsPoint({params}, callback(ret, err))

##params

point：

- 类型：JSON 对象
- 描述：已知点的地理坐标
- 内部字段：

```js
{
    lon: 116.297,      //数字类型；经度
    lat: 40.109        //数字类型；纬度
}
```

points：

- 类型：数组
- 描述：多边形的各个点组成的数组
- 内部字段：

```js
[{
    lon: 116.297,      //数字类型；经度
    lat: 40.109        //数字类型；纬度
}]
```
##params

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true      //布尔类型；目标点是否在指定区域内，true || false      
}
```


##示例代码

```js
var aMap = api.require('aMap');
aMap.isPolygonContainsPoint({
    point: {
	     lon:116.39432327,
	     lat:39.98963192
	 },
	 points: [{
	     lon:116.39432327,
	     lat:39.98963192
	 },{
	     lon: 116.49432328,
	     lat: 39.98963192
	 },{
	     lon: 116.39432327,
	     lat: 39.88933191
	 }]
},function(ret){
     alert(ret.status);
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m24"></div>

#**interconvertCoords**

经纬度坐标与地图容器像素坐标相互转换，经纬度和x，y值传一种即可。

interconvertCoords({params}, callback(ret, err))

##params

lon：

- 类型：数字
- 描述：（可选项）原始地理坐标经度

lat：

- 类型：数字
- 描述：（可选项）原始地理坐标纬度

x：

- 类型：数字
- 描述：（可选项）地图容器的 x 坐标

y：

- 类型：数字
- 描述：（可选项）地图容器的 y 坐标

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true,           //布尔型；true||false
    x: 334.00004622221184,  //数字类型；传经纬度时，返回转换后的地图容器x坐标
    y: 207.00000925440887,  //数字类型；传经纬度时，返回转换后的地图容器y坐标
    lon: 116.213,           //数字类型；传x，y值时，返回转换后的地理坐标经度
    lat: 39.213             //数字类型；传x，y值时，返回转换后的地理坐标纬度
}
```

##示例代码

```js
var aMap = api.require('aMap');
aMap.interconvertCoords({
    lon: 116.351,
    lat: 39.283
}, function(ret, err){
    if(ret.status){
        alert(JSON.stringify(ret));
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m25"></div>

#**addEventListener**

监听地图相关事件

addEventListener({params}, callback(ret, err))

##params

name:

- 类型：字符串
- 描述：地图相关事件名称
- 取值范围：
    - longPress（长按事件）
    - viewChange（视角改变事件）
    - click（单击事件）
    - trackingMode（userTrackingMode 改变事件，暂仅支持 IOS 平台）

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true,           //布尔型；true||false
    lon: 116.351,           //数字类型；触发事件的地点的经度（longPress，click），地图中心的经度（viewChange）
    lat: 39.283,            //数字类型；触发事件的地点的纬度（longPress，click），地图中心的纬度（viewChange）
    zoom: 11,               //数字类型；地图缩放角度
    rotate: 30,             //数字类型；地图旋转角度
    overlook: 30,           //数字类型；视角倾斜度
    trackingMode:follow     //字符串类型；当前位置标注图标显示的跟踪类型（trackingMode）
-                             取值范围：
                               none（不追踪用户的 location 更新）
                               follow（追踪用户的 location 更新）
                               heading（追踪用户的 location 与 heading 更新）
}
```

##示例代码

```js
var aMap = api.require('aMap');
aMap.addEventListener({
    name: 'longPress'
},function(ret){
    if(ret.status){
        alert(JSON.stringify(ret));
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m26"></div>

#**removeEventListener**

停止监听地图相关事件

removeEventListener({params})

##params

name:

- 类型：字符串
- 描述：地图相关事件名称
- 取值范围：
    - longPress（长按事件）
    - viewChange（视角改变事件）
    - click（单击事件）
    - trackingMode（userTrackingMode 改变事件）

##示例代码

```js
var aMap = api.require('aMap');
aMap.removeEventListener({
    name: 'longPress'
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m27"></div>

#**addAnnotations**

在地图上添加标注信息，标注大小为 icons 内第一张图片大小的二分之一。**图标中轴线的下边缘点为坐标基准点**

addAnnotations({params}, callback(ret, err))

##params

annotations：

- 类型：数组
- 描述：图标标注信息组成的数组
- 内部字段：

```js
[{
    id: 1,                     //数字类型；图标标注的唯一标识
    lon: 116.233,              //数字类型；图标标注所在位置的经度
    lat: 39.134,               //数字类型；图标标注所在位置的纬度
    icons: 'widget://',        //（可选项）数组类型；指定的标注图标路径组成的数组，若包含多张图片，则此标注显示为多图联动的 gif 动画效果，要求本地路径（fs://、widget://），若不传则显示公用的 icons 图标
    draggable: true            //（可选项）布尔类型；所添加的标注是否可被拖动，若不传则以公用的 draggable 为准
}]
```

icons：

- 类型：数组
- 描述：（可选项）指定的标注图标路径组成的数组，若包含多张图片，则此标注显示为多图联动的 gif ，要求本地路径（fs://、widget://）
- 默认值：红色大头针


draggable：

- 类型：布尔
- 描述：（可选项）所添加的标注是否可被拖动
- 默认值：false

timeInterval：

- 类型：数字
- 描述：（可选项）若添加的标注为动态图，则本参数表示动态图循环播放一次的时间，单位为秒（s），否则本参数无效
- 默认值：3.0

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    id: 10                      //数字类型；相应事件的标注的
    eventType: 'click',         //字符串类型；交互事件类型
                                //取值范围：
                                //click（用户点击标注事件）
                                //drag（用户拖动标注事件）
    dragState: 'starting'       //字符串类型；标注被拖动的状态，当 eventType 为 drag 时本字段有值，
                                //取值范围：
                                //starting（开始拖动）
                                //dragging （拖动中）
                                //ending （拖动结束）
}
```

##示例代码

```js
var aMap = api.require('aMap');
aMap.addAnnotations({
    annotations: [{
        id: 1, lon: 116.297, lat: 40.109
    },
    {
        id: 2, lon: 116.29, lat: 40.109
    },
    {
        id: 3, lon: 116.298, lat: 40.11
    }],
    icons:['widget://'] ,
    draggable: true,
    timeInterval: 2.0
}, function(ret){
    if(ret.eventType == 'click'){
        alert(ret.id);
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m28"></div>

#**getAnnotationCoords**

获取指定标注的经纬度

getAnnotationCoords({params}, callback(ret, err))

##params

id：

- 类型：数字
- 描述：指定的标注 id

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    lon: 116.213,      //数字类型；标注的经度
    lat: 39.213        //数字类型；标注的纬度
}
```

##示例代码

```js
var aMap = api.require('aMap');
aMap.getAnnotationCoords({
    id: 2
}, function(ret){
    if(ret){
        api.alert({msg:JSON.stringify(ret)});
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m29"></div>

#**setAnnotationCoords**

设置某个已添加标注的经纬度

setAnnotationCoords(callback(ret, err))

##params

id：

- 类型：数字
- 描述：指定的标注 id

lon：

- 类型：数字
- 描述：设置的经度

lat：

- 类型：数字
- 描述：设置的纬度

##示例代码

```js
var aMap = api.require('aMap');
aMap.setAnnotationCoords({
    id: 2,
    lon: 116.39,
    lat: 40.209
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m30"></div>

#**annotationExist**

判断标注是否存在

annotationExist({params}, callback(ret, err))

##params

id：

- 类型：数字
- 描述：指定的标注 id

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true      //布尔类型；标注是否存在，true || false
}
```

##示例代码

```js
var aMap = api.require('aMap');
aMap.annotationExist({
    id: 2
}, function(ret){
    if(ret.status){
        api.alert({msg:'存在'});
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m31"></div>

#**setBubble**

设置点击标注时弹出的气泡信息

setBubble({params}, callback(ret, err))

##params

id：

- 类型：数字
- 描述：要设置气泡的标注 id

bgImg：

- 类型：字符串
- 描述：（可选项）弹出气泡的背景图片（160*90规格），要求本地路径（fs://、widget://），中轴线下边缘点为气泡弹出点，**若本字段为空，则 content 内的 title 长度大于105时，气泡宽度会根据 title 长度自适应**
- 默认值：默认气泡背景图片

content：

- 类型：JSON 对象
- 描述：弹出气泡的内容
- 内部字段：

```js
{
    title: '',             //字符串类型；弹出气泡的标题，若 bgImg 为默认图片，则标题长度大于105时，气泡宽度会根据标题长度自适应
    subTitle: '',          //（可选项）字符串类型；弹出气泡的概述内容，若不传则 title 在上下位置居中显示
    illus: ''              //（可选项）字符串类型；弹出气泡的配图（30*40规格），支持http://、https://、widget://、fs://等协议，若不传则不显示插图，标题和子标题忽略插图显示
}
```

styles：

- 类型：JSON 对象
- 描述：弹出气泡的样式
- 内部字段：

```js
{
    titleColor: '#000',             //（可选项）字符串类型；气泡标题的文字颜色，支持 rgb、rgba、#；默认：'#000'
    titleSize: 16,                  //（可选项）数字类型；气泡标题的文字大小；默认：16
    subTitleColor: '#000',          //（可选项）字符串类型；气泡概述内容的文字颜色，支持 rgb、rgba、#；默认：'#000'
    subTitleSize: 14,               //（可选项）数字类型；气泡概述内容的文字大小；默认：14
    illusAlign: 'left'              //（可选项）字符串类型；气泡配图的显示位置；默认：'left'
                                    //取值范围：
                                    //left（图片居左）
                                    //right（图片居右）
}
```

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    id: 10,                     //数字类型；用户点击气泡返回的id
    eventType: 'clickContent',  //字符串类型；交互事件类型
                                //取值范围：
                                //clickContent（点击气泡文本内容）
                                //clickIllus（点击配图）
}
```

##示例代码

```js
var aMap = api.require('aMap');
aMap.setBubble({
    id: 2,
    bgImg: 'widget://res/bubble_bg.png',
    content: {
        title: '大标题',
        subTitle: '概述内容',
        illus: 'http://ico.ooopic.com/ajax/iconpng/?id=145044.png'
    },
    styles: {
        titleColor: '#000',
        titleSize: 16,
        subTitleColor: '#999',
        subTitleSize: 12,
        illusAlign: 'left'
    }
}, function(ret){
    if(ret){
        alert(JSON.stringify(ret));
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m32"></div>

#**popupBubble**

弹出指定标注的气泡

popupBubble({params})

##params

id：

- 类型：数字
- 描述：气泡的 id

##示例代码

```js
var aMap = api.require('aMap');
aMap.popupBubble({
    id: 2
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m33"></div>

#**addBillboard**

在地图上添加布告牌

addBillboard({params})

##params

id：

- 类型：数字
- 描述：布告牌的 id，**注意：本 id 不可与 addAnnotations 接口内的 id 相同**

coords：

- 类型：JSON 对象
- 描述：布告牌所在位置的坐标
- 内部字段：

```js
{
    lon: 116.233,            //数字类型；布告牌所在位置的经度
    lat: 39.134              //数字类型；布告牌所在位置的纬度
}
```

bgImg：

- 类型：字符串
- 描述：布告牌的背景图片（120*75规格），要求本地路径（fs://、widget://）

content：

- 类型：JSON 对象
- 描述：布告牌的内容
- 内部字段：

```js
{
    title: '',             //（可选项）字符串类型；布告牌的标题
    subTitle: '',          //（可选项）字符串类型；布告牌的概述内容 
    illus: ''              //（可选项）字符串类型；布告牌的配图（35*50规格），支持http://、https://、widget://、fs://等协议
}
```
draggable：

- 类型：布尔
- 描述：（可选项）所添加的布告牌是否可被拖动
- 默认值：false

styles：

- 类型：JSON 对象
- 描述：布告牌的样式
- 内部字段：

```js
{
    titleColor: '#000',             //（可选项）字符串类型；布告牌标题的文字颜色，支持 rgb、rgba、#；默认：'#000'
    titleSize: 14,                  //（可选项）数字类型；布告牌标题的文字大小；默认：16
    subTitleColor: '#000',          //（可选项）字符串类型；布告牌概述内容的文字颜色，支持 rgb、rgba、#；默认：'#000'
    subTitleSize: 12,               //（可选项）数字类型；布告牌概述内容的文字大小；默认：16
    illusAlign: 'left'              //（可选项）字符串类型；布告牌配图的显示位置；默认：'left'
                                    //取值范围：
                                    //left（图片居左）
                                    //right（图片居右）
}
```

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    id: 4,                     //数字类型；用户点击布告牌返回的id
    eventType: 'click',        //字符串类型；交互事件类型
                                //取值范围：
                                //click（用户点击布告牌事件）
                                //drag（用户拖动布告牌事件）
    dragState: 'starting'       //字符串类型；布告牌被拖动的状态，当 eventType 为 drag 时本字段有值，
                                //取值范围：
                                //starting（开始拖动）
                                //dragging （拖动中）
                                //ending （拖动结束）
}
```

##示例代码

```js
var aMap = api.require('aMap');
aMap.addBillboard({
    id: 4,
    draggable: true,
    coords: {
        lon: 116.233,
        lat: 39.134
    },
    bgImg: 'widget://image/aMapTest.png',
    content: {
        title: '大标题大标题大标题大标题',
        subTitle: '概述内容概述内容概述内容',
        illus: 'http://ico.ooopic.com/ajax/iconpng/?id=145044.png'
    },
    styles: {
        titleColor: '#000',
        titleSize: 16,
        subTitleColor: '#999',
        subTitleSize: 12,
        illusAlign: 'left'
    }
}, function(ret){
    if(ret){
        alert(JSON.stringify(ret));
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m34"></div>

#**addMobileAnnotations**

在地图上添加可移动、旋转的标注图标，**注意：本 id 不可与 addAnnotations、addBillboard 接口内的 id 相同**

addMobileAnnotations({params}, callback(ret, err))

##params

annotations：

- 类型：数组
- 描述：图标标注信息组成的数组
- 内部字段：

```js
[{
    id: 10,                    //数字类型；图标标注的唯一标识
    lon: 116.233,              //数字类型；图标标注所在位置的经度
    lat: 39.134,               //数字类型；图标标注所在位置的纬度
    icon: 'widget://',          //字符串类型；指定的标注图标，要求本地路径（fs://、widget://），图标的锚点即是坐标点。
    draggable: true            //布尔类型；所添加的可移动的标注是否可被拖动；默认：false
}]
```
##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    id: 4,                     //数字类型；交互标注对象的 id
    dragState: 'starting'       //字符串类型；标注被拖动的状态
                                //取值范围：
                                //starting（开始拖动）
                                //dragging （拖动中）
                                //ending （拖动结束）
}
```
##示例代码

```js
var aMap = api.require('aMap');
        aMap.addMobileAnnotations({
            annotations: [{
                id: 10, lon: 116.297, lat: 40.109, icon:'widget://image/aMap_car1.png', draggable: true
            },{
                id: 11, lon: 116.98, lat: 40.109, icon:'widget://image/aMap_car2.png', draggable: true
            },{
                id: 12, lon: 115.30, lat: 40.109, icon:'widget://image/aMap_car3.png', draggable: true
            },{
                id: 13, lon: 116.297, lat: 39.109, icon:'widget://image/aMap_car1.png', draggable: true
            },{
                id: 14, lon: 116.98, lat: 39.109, icon:'widget://image/aMap_car2.png', draggable: true
            },{
                id: 15, lon: 115.30, lat: 39.109, icon:'widget://image/aMap_car3.png', draggable: true
            }]
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="35"></div>

#**moveAnnotation**

移动地图上已添加的可移动、旋转的标注图标，**在移动动画开始前，会先做 0.3 秒的旋转动画，使所移动的图标中间轴线顶端对准终点坐标点。在 Android 平台上，如果标注添加到地图当前可视区域以外的区域，则不可以移动该标注**

moveAnnotation({params}, callback(ret, err))

##params

id：

- 类型：数字
- 描述：要移动的标注的 id 

duration：

- 类型：数字
- 描述：（可选项）标注图标移动动画的时间，单位为秒（s），**不包括旋转动画时间**
- 默认值：1.0（s）

end：

- 类型：JSON 对象
- 描述：终点经纬度
- 内部字段：

```js
{
    lon: 116.581515,    //数字类型；终点的经度
    lat: 29.615467      //数字类型；终点的纬度
}
```
##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    id:         //数字类型；移动动画结束的标注的 id
}
```

##示例代码

```js
	var aMap = api.require('aMap');
	for (var i=0; i<6; i++) {
	  aMap.moveAnnotation({
	      id: 10+i,
	      duration: 6,
	      end:{
	          lon:116.3843839609304,
	          lat:39.98964439091298
	      }
	  }, function(ret, err){
	      alert(ret.id + '移动结束')
	  });
	}
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m36"></div>

#**removeAnnotations**

移除指定 id 的标注（可移动、不可移动）或布告牌

removeAnnotations({params})

##params

ids：

- 类型：数组
- 描述：要移除的标注或布告牌id（数字）

##示例代码

```js
var aMap = api.require('aMap');
aMap.removeAnnotations({
    ids: [1,3,5,7]
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m37"></div>

#**addLine**

在地图上添加线

addLine({params})

##params

id：

- 类型：数字
- 描述：线的 id

styles：

- 类型：JSON 对象
- 描述：（可选项）直线的样式
- 内部字段：

```js
{
    type: 'arrow',            //（可选项）字符串类型；线的末端类型；默认：round；取值范围如下：
                              //round：圆头线，在Android 上无效，显示为普通方头线条
                              //square：方头线
                              //arrow：带箭头的线    
    lineDash: false,          //（可选项）布尔类型；是否绘制成虚线，当 type 为 arrow 时，本参数无效；默认：false
    borderColor: '#000',      //（可选项）字符串类型；线的颜色，支持 rgb、rgba、#；默认值：'#000'
    borderWidth: 3,           //（可选项）数字类型；线的宽度，默认：2
    strokeImg:'fs://arrow.png'//（可选项）字符串类型；组成纹理画线的图片路径，要求本地路径（fs://、widget://），若本参数不为空，则本接口忽略 type、lineDash、borderColor 参数   
}
```

points：

- 类型：数组
- 描述：线的两个点组成的数组
- 内部字段：

```js
[{
    lon: 116.297,     //数字类型；经度
    lat: 40.109       //数字类型；纬度
}]
```

##示例代码

```js
var aMap = api.require('aMap');
aMap.addLine({
    id: 1,
    styles: {
        type: 'arrow',
        borderColor: '#FF0000',
        borderWidth: 3,
        lineDash: true,
        strokeImg: ''
    },
    points: [{
        lon: 116.297, lat: 40.109
    },
    {
        lon: 116.298, lat: 40.109
    }]
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m38"></div>

#**addCircle**

在地图上添加圆形

addCircle({params})

##params

id：

- 类型：数字
- 描述：圆形的 id，**不可与 addLine 接口内的 id 相同**

center：

- 类型：JSON 对象
- 描述：圆形中心点的经纬度
- 内部字段：

```js
{
    lon: 116.297,       //数字类型；圆形中心点的经度
    lat: 40.109         //数字类型；圆形中心点的纬度
}
```

radius：

- 类型：数字
- 描述：圆形的半径

styles：

- 类型：JSON 对象
- 描述：（可选项）圆形的样式
- 内部字段：

```js
{
    borderColor: '#000',          //（可选项）字符串类型；圆形的边框颜色，支持 rgb、rgba、#；默认：'#000'
    borderWidth: 3 ,              //（可选项）数字类型；圆形的边框宽度，默认：2  
    lineDash: false,              //（可选项）布尔类型；是否绘制成虚线，Android 平台不支持；默认：false
    fillColor: '#ff0'             //（可选项）字符串类型；圆形填充颜色，支持 rgb、rgba、#；默认：'rgba(1,0.8,0,0.8)'
}
```

##示例代码

```js
var aMap = api.require('aMap');
aMap.addCircle({
    id: 2,
    center: {
        lon: 116.298,
        lat: 40.11,
    },
    radius: 500,
    styles: {
        borderColor: '#FF0000',
        borderWidth: 3,
        lineDash: true,
        fillColor: 'rgba(1,0.8,0,0.8)'
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m39"></div>

#**addPolygon**

在地图上添加多边形

addPolygon({params})

##params

id：

- 类型：数字
- 描述：多边形的 id，**不可与 addLine、addCircle、addArc 接口内的 id 相同**

styles：

- 类型：JSON 对象
- 描述：（可选项）多边形的样式
- 内部字段：

```js
{
    borderColor: '#000',    //（可选项）字符串类型；多边形的边框颜色，支持 rgb、rgba、#；默认：'#000'
    borderWidth: 3,         //（可选项）数字类型；多边形的边框宽度，默认：2
    lineDash: false,       //（可选项）布尔类型；是否绘制成虚线，Android 平台不支持本参数；默认：false
    fillColor: '#ff0'      //（可选项）字符串类型；圆形填充颜色，支持 rgb、rgba、#；默认：'rgba(1,0.8,0,0.8)'
}
```

points：

- 类型：数组
- 描述：多边形的各个点组成的数组
- 内部字段：

```js
[{
    lon: 116.297,      //数字类型；经度
    lat: 40.109        //数字类型；纬度
}]
```

##示例代码

```js
var aMap = api.require('aMap');
aMap.addPolygon({
    id: 4,
    styles: {
        borderColor: '#FF0000',
        borderWidth: 3,
        lineDash:false,
        fillColor:'#ff0'
    },
    points: [{
        lon: 116.297, lat: 40.109
    },
    {
        lon: 116.298, lat: 40.109
    },
    {
        lon: 116.298, lat: 40.11
    }]
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


<div id="m40"></div>

#**addImg**

在地图上添加图片

addImg({params})

##params

id：

- 类型：数字
- 描述：图片 id，**不可与 addLine、addCircle、addArc、addPolygon 接口内的 id 相同**

imgPath：

- 类型：字符串
- 描述：图片的路径，要求本地路径（fs://、widget://）

lbLon：

- 类型：数字
- 描述：左下角点的经度

lbLat：

- 类型：数字
- 描述：左下角点的纬度

rtLon：

- 类型：数字
- 描述：右上角点的经度

rtLat：

- 类型：数字
- 描述：右上角点的纬度

##示例代码

```js
var aMap = api.require('aMap');
aMap.addImg({
    id: 5,
    imgPath: 'widget://res/over_img.png',
    lbLon: 116.297,
    lbLat: 40.109,
    rtLon: 116.298,
    rtLat: 40.11
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m41"></div>

#**removeOverlay**

移除指定 id 的覆盖物

removeOverlay({params})

##params

ids：

- 类型：数组
- 描述：要移除的 id（数字）组成的数组

##示例代码

```js
var aMap = api.require('aMap');
aMap.removeOverlay({
    ids: [1, 2, 3, 4, 5]
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m43"></div>

#**searchRoute**

搜索路线方案，**无需调用 open 接口即可使用**

searchRoute({params}, callback(ret, err))

##params

type：

- 类型：字符串
- 描述：（可选项）路线类型
- 默认值：transit
- 取值范围：
    - drive（开车）
    - transit（公交）
    - walk（步行）

strategy：

- 类型：字符串
- 描述：（可选项）路线策略，**type 为 walk（步行）时，此参数可不传**
- 默认值：'drive_time_first/transit_time_first'
- 取值范围：
    - drive_time_first：速度优先（时间）
    - drive_fee_first：费用优先（不走收费路段的最快道路）
    - drive_dis_first：距离优先
    - drive_highway_no：不走高速
    - drive_jam_no：结合实时交通（躲避拥堵）
    - drive_highway_fee_no：不走高速且避免收费
    - drive_highway_jam_no：不走高速且躲避拥堵
    - drive_fee_jam_no：躲避收费和拥堵
    - drive_highway_fee_jam_no：不走高速且躲避收费和拥堵
    - transit_time_first：最快捷模式
    - transit_fee_first：最经济模式
    - transit_transfer_first：最少换乘模式
    - transit_walk_first：最少步行模式
    - transit_comfort_first：最舒适模式
    - transit_subway_no：不乘地铁模式

start：

- 类型：JSON 对象
- 描述：起点信息
- 内部字段：

```js
{
    lon: 116.403838,    //数字类型；起点经度
    lat: 39.914437      //数字类型；起点纬度
}
```

waypoints：

- 类型：JSON 对象
- 描述：（可选项）途经点信息组成的数组，仅当 type 为 drive 时有效
- 内部字段：

```js
[{
    lon: 116.403838,    //数字类型；起点经度
    lat: 39.914437      //数字类型；起点纬度
}]
```
nightflag：

- 类型：布尔
- 描述：（可选项）是否包含夜班车，仅当 type 为 transit 时有效
- 默认：false

city：

- 类型：字符串
- 描述：（可选项）搜索公交路线时所在的城市，仅当 type 为 transit 时有效且必传

end：

- 类型：JSON 对象
- 描述：终点信息
- 内部字段：

```js
{
    lon: 116.384852,    //数字类型；终点经度
    lat: 39.989576      //数字类型；终点纬度
}
```

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true,               //布尔型；true||false
    start:{                     //JSON对象；起点信息
       lon: 116.384852,         //数字类型；起点经度
       lat: 39.989576           //数字类型；起点纬度
    },
    end:{                       //JSON对象；终点信息
       lon: 116.384852,         //数字类型；终点经度
       lat: 39.989576           //数字类型；终点纬度
    },
    taxiCost: 50,               //数字类型；出租车费用（单位：元）
    paths: [{                   //数组类型；步行、驾车方案列表数组
        steps:[{                //数组类型；路段基本信息组成的数组
			instruction:'左转',  //字符串类型；行走指示
			orientation:'北',    //字符串类型；方向
			road:'光明路',        //字符串类型；道路名称
			distance:'2000',     //数字类型；此路段长度（单位：米）
			duration:'1000',     //数字类型；此路段预计耗时（单位：秒）
			action:'go',         //字符串类型；导航主要动作
			assistantAction:'go',//字符串类型；导航辅助动作
			tolls:'5',           //数字类型；此段收费（单位：元）
			tollDistance:'500',  //数字类型；收费路段长度（单位：米）
			tollRoad:''          //字符串类型；主要收费路段
            enterLoc:{          //JSON对象；入口经纬度，Android 平台上无此字段
               lon:,            //数字类型；入口经度
               lat:             //数字类型；入口纬度
            },
            exitLoc:{          //JSON对象；出口经纬度，入口经纬度，Android 平台上无此字段
               lon:,            //数字类型；出口经度
               lat:             //数字类型；出口纬度
            }
        }],
	    distance: 1000,          //数字类型；路线长度，单位：米
	    duration: 10,            //数字类型；路线耗时，单位：秒
	    strategy: 1000,          //字符串类型；导航策略
	    tolls: 1000,             //数字类型；此方案费用（单位：元）
	    tollDistance: 1000       //数字类型；此方案收费路段长度（单位：米）
    }],
    transits:[{                 //数组类型；公交换乘方案列表数组
        cost: 50,               //数字类型；此公交方案价格（单位：元）
        duration: 36000,        //数字类型；此换乘方案预期时间（单位：秒）
        nightflag: false ,      //布尔类型；是否是夜班车
        walkingDistance: 100,   //数字类型；此方案总步行距离（单位：米）
        busDistance: 100,       //数字类型；此方案公交路线距离（单位：米），IOS 平台上无此参数
        segments:[{             //数组类型；换乘路段组成的数组
            enterName:'',       //字符串类型；公交换乘路段入口名称
            exitName:'',        //字符串类型；公交换乘路段出口名称
            busline:{           //JSON对象；路段可供选择的公交线路
               type:'',         //字符串类型；公交类型
               name:'',         //字符串类型；公交线路名称
               uid:''           //字符串类型；公交线路ID
            },
            enterLoc:{          //JSON对象；入口经纬度
               lon:,            //数字类型；入口经度
               lat:             //数字类型；入口纬度
            },
            exitLoc:{          //JSON对象；出口经纬度
               lon:,            //数字类型；出口经度
               lat:             //数字类型；出口纬度
            },
            walking:{           //JSON对象；此路段步行导航信息
               distance:,       //数字类型；起点和终点的步行距离（单位：米）
               duration:        //数字类型；步行预计时间
            }
        }]
    }]    
}
```

##示例代码

```js
var aMap = api.require('aMap');
aMap.searchRoute({
    id: 1,
    type: 'drive',
    policy: 'drive_time_first',
    start: {
        lon: 116.403838,
        lat: 39.914437
    },
    end: {
        lon: 116.384852,
        lat: 39.989576
    },
    city:'北京',
    nightflag: false,
    waypoints:[]
}, function(ret, err){
    if(ret.status){
        api.alert({msg:JSON.stringify(ret)});
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m44"></div>

#**drawRoute**

在地图上绘制显示 searchRoute 搜索到的指定路线，**调用本接口前，必须保证已经调用过 open 和 searchRoute 接口**

drawRoute({params})

##params

id：

- 类型：数字
- 描述：绘制路线分配的 id ，removeRoute 时使用此 id 移除路线

autoresizing：

- 类型：布尔
- 描述：路线渲染结束是否自动调整地图可视区域，**为 true 时自带 0.3 秒地图移动动画效果**
- 默认值：true

index：

- 类型：数字类型
- 描述：路线方案的索引，在 searchRoute 时返回的多个路线方案组成的数组中的索引
- 默认值：0

styles：

- 类型：JSON 对象
- 描述：路线样式设置
- 内部字段：

```js
{
    walkLine:{                    //（可选项）JSON对象；步行路线样式
        width: 3,                 //（可选项）数字类型；步行路线的线条宽度；默认：3
        color:'#698B22',          //（可选项）字符串类型；步行路线的线条颜色，支持 rgb、rgba、#；默认：#698B22
        lineDash:false,           //（可选项）布尔类型；步行路线的线条是否为虚线，Android 平台暂不支持；默认：false
        strokeImg:'fs://arrow.png'//（可选项）字符串类型；组成纹理画线的图片路径，要求本地路径（fs://、widget://），若本参数不为空，则忽略 color、dashed 参数 。Android 平台暂不支持
    },
    driveLine:{                   //（可选项）JSON对象；驾车路线样式
        width: 6,                 //（可选项）数字类型；驾车路线的线条宽度；默认：5
        color:'#0000EE',          //（可选项）字符串类型；驾车路线的线条颜色，支持 rgb、rgba、#；默认：#00868B
        lineDash:false,           //（可选项）布尔类型；驾车路线的线条是否为虚线，Android 平台暂不支持；默认：false
        strokeImg:'fs://arrow.png'//（可选项）字符串类型；组成纹理画线的图片路径，要求本地路径（fs://、widget://），若本参数不为空，则忽略 color、dashed 参数。Android 平台暂不支持
    },
    busLine:{                     //（可选项）JSON对象；公交路线样式
        width: 4,                 //（可选项）数字类型；公交路线的线条宽度；默认：4
        color:'#00BFFF',          //（可选项）字符串类型；公交路线的线条颜色，支持 rgb、rgba、#；默认：#00BFFF
        lineDash:false,           //（可选项）布尔类型；公交路线的线条是否为虚线，Android 平台暂不支持；默认：false
        strokeImg:'fs://arrow.png'//（可选项）字符串类型；组成纹理画线的图片路径，要求本地路径（fs://、widget://），若本参数不为空，则忽略 color、dashed 参数。Android 平台暂不支持  
    },
    icons: {                     //（可选项）JSON对象；路线结点标注图标
       start: '',                //（可选项）字符串类型；起点图标路径，要求本地路径（fs://、widget://）；默认：默认起点图标
       end: '',                  //（可选项）字符串类型；终点图标路径，要求本地路径（fs://、widget://）；默认：默认终点图标
       bus: '',                  //（可选项）字符串类型；公交路线结点提示图标路径，要求本地路径（widget://、fs://）默认：默认公交图标
       car: '',                  //（可选项）字符串类型；驾车路线结点提示图标路径，要求本地路径（widget://、fs://）默认：默认公交图标
       man: ''                   //（可选项）字符串类型；步行路线结点提示图标路径，要求本地路径（widget://、fs://）默认：默认公交图标
    }
}
```

##示例代码

```js
var aMap = api.require('aMap');
aMap.searchRoute({
    type: 'drive',
    policy: 'drive_fee_first',
    start: {
        lon: 116.403838,
        lat: 39.914437
    },
    end: {
        lon: 116.384852,
        lat: 39.989576
    }
}, function(ret, err){
    if(ret.status){
	    aMap.drawRoute({
		    id: 1,
            autoresizing:false,
		    index: 0,
		    styles: {
               walkLine:{                   
			        width: 3,                 
			        color:'#698B22',         
			        lineDash:false,          
			        strokeImg:''
			   },
		       driveLine:{               
			        width: 6,                 
			        color:'#0000EE',         
			        lineDash:false,           
			        strokeImg:''
		       },
		       busLine:{                    
			        width: 4,                 
			        color:'#00BFFF',          
			        lineDash:false,           
			        strokeImg:''
		       },
		       icons: {                     
			       start: '',                
			       end: '',                  
			       bus: '',                  
			       car: '',                  
			       man: ''                   
		      }
	        }
	    });
    } else {
       api.alert({msg:JSON.stringify(ret)});
    }
});
```

##可用性

IOS 系统，Android系统

可提供的1.0.0及更高版本

<div id="m45"></div>

#**removeRoute**

移除指定 id 的路线

removeRoute({params})

##params

ids：

- 类型：数组
- 描述：所要移除的 id（数字）组成的数组

##示例代码

```js
var aMap = api.require('aMap');
aMap.removeRoute({
    ids: [1, 2, 3]
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m46"></div>

#**searchBusRoute**

根据关键字搜索公交、地铁线路，**无需调用 open 接口即可搜索**

searchBusRoute({params}, callback(ret, err))

##params

city：

- 类型：字符串
- 描述：城市

line：

- 类型：字符串
- 描述：公交、地铁线路号（例如：1路，1号线）


offset：

- 类型：数字
- 描述：（可选项）每页记录数，取值为1－50
- 默认：20


page：

- 类型：数字
- 描述：（可选项）当前页数，取值为1-100
- 默认：1


##callback(ret，err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
      status: true,           //布尔型；true||false
      buslines: [{            //数组类型；公交线路信息组成的数组
        uid: '',              //字符串类型；公交线路ID
        type: '',             //字符串类型；公交类型
        name: '',             //字符串类型；公交线路名称
        startStop: '',        //字符串类型；首发站
        endStop: '',          //字符串类型；终点站
        startTime: '',        //字符串类型；首班车时间
        endTime: '',          //字符串类型；末班车时间
        company: '',          //字符串类型；所属公交公司
        distance: '',         //数字类型；此线路的全程距离，单位为千米
        basicPrice: '',       //数字类型；起步价
        totalPrice: '',       //数字类型；全程票价
        busStops: [{          //数组类型；途径公交站
            uid:'',           //字符串类型；公交站点ID
            name:'',          //字符串类型；公交站名
            lat: ,            //数字类型；公交站坐标纬度
            lon:              //数字类型；公交站坐标经度
        }]          
      }] ,
      suggestion:{               //JSON对象；关键字建议列表和城市建议列表
          keywords:['','','',''],//数组类型；字符串类型的关键字组成的建议列表
          cities:['','','','']   //数组类型；字符串类型的城市名组成的城市建议列表
      }
}
```

##示例代码

```js
var aMap = api.require('aMap');
aMap.searchBusRoute({
    city: '北京',
    line: '110',
    offset:20,
    page:1
},function(ret, err){
    if(ret.status){
        alert(JSON.stringify(ret));
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m47"></div>

#**drawBusRoute**

根据 searchBusRoute 搜索返回的公交信息，将指定线路绘制在地图上

drawBusRoute({params})

##params

id：

- 类型：数字
- 描述：地图上显示的公交、地铁路线的 id，**removeBusRoute 时使用此 id**

autoresizing：

- 类型：布尔
- 描述：路线渲染结束是否自动调整地图可视区域
- 默认值：true

index：

- 类型：数字类型
- 描述：路线方案的索引，在 searchBusRoute 时返回的多个公交路线组成的数组中的索引
- 默认值：0

styles：

- 类型：JSON 对象
- 描述：路线样式设置
- 内部字段：

```js
{
    line:{                        //（可选项）JSON对象；公交路线样式
        width: 4,                 //（可选项）数字类型；公交路线的线条宽度；默认：4
        color:'#00BFFF',          //（可选项）字符串类型；公交路线的线条颜色，支持 rgb、rgba、#；默认：#00BFFF
        lineDash:false,           //（可选项）布尔类型；公交路线的线条是否为虚线；默认：false
        strokeImg:'fs://arrow.png'//（可选项）字符串类型；组成纹理画线的图片路径，要求本地路径（fs://、widget://），若本参数不为空，则忽略 color、dashed 参数  
    },
    icons: {                     //（可选项）JSON对象；路线结点标注图标
       start: '',                //（可选项）字符串类型；起点图标路径，要求本地路径（fs://、widget://）；默认：默认起点图标
       end: '',                  //（可选项）字符串类型；终点图标路径，要求本地路径（fs://、widget://）；默认：默认终点图标
       bus: ''                   //（可选项）字符串类型；公交路线结点提示图标路径，要求本地路径（widget://、fs://）默认：默认公交图标
    }
}
```

##示例代码

```js
var aMap = api.require('aMap');
aMap.searchBusRoute({
    city: '北京',
    line: '110',
    offset: 20,
    page: 1
},function(ret, err){
    if(ret.status){
        aMap.drawBusRoute({
                id: 1,
                autoresizing: true,
                index: 0,
                styles: {
                    line:{                     
				        width: 4,                 
				        color:'#00BFFF',         
				        lineDash:false,          
				        strokeImg:'fs://arrow.png'
				    },
				    icons: {                     
				       start: '',                
				       end: '',                  
				       bus: ''                   
				    }
                }
        });  
    } 
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m48"></div>

#**removeBusRoute**

移除地图上显示的公交、地铁线路

removeBusRoute({params})

##params

ids：

- 类型：数组
- 描述：所要移除的公交、地铁线路的 id（数字）组成的数组

##示例代码

```js
var aMap = api.require('aMap');
aMap.removeBusRoute({
   ids:[1, 2, 3]
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m49"></div>

#**searchInCity**

根据单个关键字搜索兴趣点，**无需调用 open 接口即可搜索**

searchInCity({params}, callback(ret, err))

##params

city：

- 类型：字符串
- 描述：要搜索的城市，可选值：cityname（中文或中文全拼）、citycode、adcode

keyword：

- 类型：字符串
- 描述：搜索的关键字，多个关键字用“|”分割

offset：

- 类型：数字
- 描述：（可选项）每页记录数，取值为1－50
- 默认：20

page：

- 类型：数字
- 描述：（可选项）当前页数，取值为1-100
- 默认：1

sortrule：

- 类型：数字
- 描述：（可选项）排序规则，0-距离排序；1-综合排序,Android 平台上忽略本参数
- 默认：0

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true,             //布尔型；true||false
    pois:[{                   //数组类型；搜索的兴趣点信息组成的数组
      uid: '',                //字符串类型；兴趣点全局唯一ID
      name: '',               //字符串类型；兴趣点名称
      type: '',               //字符串类型；兴趣点类型
      lat: ,                  //数字类型；兴趣点纬度
      lon: ,                  //数字类型；兴趣点经度
      address: '',            //字符串类型；兴趣点地址
      tel: '',                //字符串类型；兴趣点电话
      distance:               //数字类型；兴趣点距离中心点距离
    }],
    suggestion:{              //JSON对象；关键字建议列表和城市建议列表
       keywords:['','','',''],//数组类型；字符串类型的关键字组成的建议列表
       cities:['','','','']   //数组类型；字符串类型的城市名组成的城市建议列表
    }
}
```

##示例代码

```js
var aMap = api.require('aMap');
aMap.searchInCity({
    city: '北京',
    keyword: '学校',
    offset: 20,
    page: 1,
    sortrule: 0
},function(ret){
    if(ret.status){
       alert(JSON.stringify(ret)); 
    }
});
```
##补充说明

searchInCity、searchNearby、searchInPolygon 三者不可并发执行，在接口未响应前 ，最后一次调用的接口会覆盖之前调用的所有接口

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m50"></div>

#**searchNearby**

根据单个关键字在圆形区域内搜索兴趣点，**无需调用 open 接口即可搜索**

searchNearby({params}, callback(ret, err))

##params

keyword：

- 类型：字符串
- 描述：搜索关键字，多个关键字用“|”分割

lon：

- 类型：数字
- 描述：指定区域中心点的经度

lat：

- 类型：数字
- 描述：指定区域中心点的纬度

radius：

- 类型：数字
- 描述：（可选项）指定区域的半径，单位为 m（米），范围：0-50000
- 默认：3000

offset：

- 类型：数字
- 描述：（可选项）每页记录数，取值为1－50
- 默认：20

page：

- 类型：数字
- 描述：（可选项）当前页数，取值为1-100
- 默认：1

sortrule：

- 类型：数字
- 描述：（可选项）排序规则，0-距离排序；1-综合排序,Android 平台上忽略本参数
- 默认：0

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true,             //布尔型；true||false
    pois:[{                   //数组类型；搜索的兴趣点信息组成的数组
      uid: '',                //字符串类型；兴趣点全局唯一ID
      name: '',               //字符串类型；兴趣点名称
      type: '',               //字符串类型；兴趣点类型
      lat: ,                  //数字类型；兴趣点纬度
      lon: ,                  //数字类型；兴趣点经度
      address: '',            //字符串类型；兴趣点地址
      tel: '',                //字符串类型；兴趣点电话
      distance:               //数字类型；兴趣点距离中心点距离
    }],
    suggestion:{              //JSON对象；关键字建议列表和城市建议列表
       keywords:['','','',''],//数组类型；字符串类型的关键字组成的建议列表
       cities:['','','','']   //数组类型；字符串类型的城市名组成的城市建议列表
    }
}
```

##示例代码

```js
var aMap = api.require('aMap');
aMap.searchNearby({
    keyword: 'KTV',
    lon: 116.384767,
    lat: 39.989539,
    radius: 2000,
    offset: 20,
    page: 1,
    sortrule: 0
},function(ret,err){
    if(ret.status){
        alert(JSON.stringify(ret));
    }
});
```
##补充说明

searchInCity、searchNearby、searchInPolygon 三者不可并发执行，在接口未响应前 ，最后一次调用的接口会覆盖之前调用的所有接口

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m51"></div>

#**searchInPolygon**

根据单个关键字在指定的多边形区域内搜索兴趣点，**无需调用 open 接口即可搜索**

searchInPolygon({params}, callback(ret, err))

##params

keyword：

- 类型：字符串
- 描述：搜索关键字

points：

- 类型：数组
- 描述：能确定一个多边形的坐标点集合
- 内部字段：

```js
[{
    lat: ,     //数字类型；坐标点的纬度
    lon:       //数字类型；坐标点的经度
}]
```

offset：

- 类型：数字
- 描述：（可选项）每页记录数，取值为1－50
- 默认：20

page：

- 类型：数字
- 描述：（可选项）当前页数，取值为1-100
- 默认：1

sortrule：

- 类型：数字
- 描述：（可选项）排序规则，0-距离排序；1-综合排序,Android 平台上忽略本参数
- 默认：0


##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true,             //布尔型；true||false
    pois:[{                   //数组类型；搜索的兴趣点信息组成的数组
      uid: '',                //字符串类型；兴趣点全局唯一ID
      name: '',               //字符串类型；兴趣点名称
      type: '',               //字符串类型；兴趣点类型
      lat: ,                  //数字类型；兴趣点纬度
      lon: ,                  //数字类型；兴趣点经度
      address: '',            //字符串类型；兴趣点地址
      tel: '',                //字符串类型；兴趣点电话
      distance:              //数字类型；兴趣点距离中心点距离
    }],
    suggestion:{              //JSON对象；关键字建议列表和城市建议列表
       keywords:['','','',''],//数组类型；字符串类型的关键字组成的建议列表
       cities:['','','','']   //数组类型；字符串类型的城市名组成的城市建议列表
    }
}
```

##示例代码

```js
var aMap = api.require('aMap');
aMap.searchInPolygon({
    keyword: '图书馆', 
    points:[{
      lat: 34.55648,
      lon: 112.47723
    },{
      lat: 34.13144,
      lon: 112.87723
    },{
      lat: 34.13144,
      lon: 112.47723
    }],
    offset: 20,
    page: 1,
    sortrule: 0
},function(ret,err){
    if(ret.status){
        alert(JSON.stringify(ret));
    }
});
```

##补充说明

searchInCity、searchNearby、searchInPolygon 三者不可并发执行，在接口未响应前 ，最后一次调用的接口会覆盖之前调用的所有接口

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


<div id="m52"></div>

#**autocomplete**

根据关键字返回建议搜索关键字，**无需调用 open 接口即可搜索**

autocomplete({params}, callback(ret, err))

##params

keyword：

- 类型：字符串
- 描述：关键字

city：

- 类型：字符串
- 描述：要搜索的城市，查询城市，中文或中文全拼

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true,           //布尔型；true||false
    tips: [{                //数组类型；返回建议搜索关键字组成的数组
       uid: '',             //字符串类型；提示点的id,Android 平台上忽略本参数
       name: '',            //字符串类型；提示点的名字
       adcode: '',          //字符串类型；提示点所在区域编码
       district: '',        //字符串类型；提示的所属区域
       lat: ,               //数字类型；提示点纬度,Android 平台上忽略本参数
       lon:                 //数字类型；提示点经度,Android 平台上忽略本参数
    }]                       
}
```

##示例代码

```js
var aMap = api.require('aMap');
aMap.autocomplete({
    keyword: '北京',
    city: '北京'
},function(ret){
    if(ret.status){
        alert(JSON.stringify(ret)); 
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m53"></div>

#**getProvinces**

获取省份列表，**无需调用 open 接口**

getProvinces(callback(ret, err))


##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true,           //布尔型；true||false
    provinces : [           //数组类型；返回全国省份的信息
    [{                      //数组类型；返回组成该省份的各个城市信息 
        name: '',           //字符串类型；区域名称
        adcode: '',         //字符串类型；区域编码
        cityCode:  ,        //字符串类型；城市编码，android 平台暂不支持本字段
        jianpin: '',        //字符串类型；区域简拼
        pinyin: '',         //字符串类型；区域拼音
        size: ,             //数字类型；该区域离线包数据大小，单位：byte
        downloadSize: ,     //数字类型；已下载离线包数据大小，单位：byte，android 平台暂不支持本字段
        status:             //数字类型；城市离线数据状态，取值范围如下：
                            // 0：不存在
                            // 1：缓存状态
                            // 2：已安装
                            // 3：已过期  
    },{}...],[{},{}...]...
    ]                      
}
```

##示例代码

```js
var aMap = api.require('aMap');
aMap.getProvinces(function(ret){
    if(ret.status){
        alert(JSON.stringify(ret)); 
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m54"></div>

#**getMunicipalities**

获取直辖市列表，**无需调用 open 接口。Android 平台不支持此接口**

getMunicipalities(callback(ret, err))


##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true,           //布尔型；true||false
    municipalities : [{     //数组类型；返回全国直辖市信息 
        name: '',           //字符串类型；区域名称
        adcode: '',         //字符串类型；区域编码
        cityCode:  ,        //字符串类型；城市编码
        jianpin: '',        //字符串类型；区域简拼
        pinyin: '',         //字符串类型；区域拼音
        size: ,             //数字类型；该区域离线包数据大小，单位：byte
        downloadSize: ,     //数字类型；已下载离线包数据大小，单位：byte
        status:             //数字类型；城市离线数据状态，取值范围如下：
                            // 0：不存在
                            // 1：缓存状态
                            // 2：已安装
                            // 3：已过期 
    }]                        
}
```

##示例代码

```js
var aMap = api.require('aMap');
aMap.getMunicipalities(function(ret){
    if(ret.status){
        alert(JSON.stringify(ret)); 
    }
});
```

##可用性

iOS系统

可提供的1.0.0及更高版本

<div id="m55"></div>

#**getNationWide**

获取全国概要图信息，**无需调用 open 接口。Android 平台不支持此接口**

getNationWide(callback(ret, err))


##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true,           //布尔型；true||false
    nationWide : {            //JSON对象；全国概要图信息 
        name: '',           //字符串类型；区域名称
        adcode: '',         //字符串类型；区域编码
        cityCode:  ,        //字符串类型；城市编码
        jianpin: '',        //字符串类型；区域简拼
        pinyin: '',         //字符串类型；区域拼音
        size: ,             //数字类型；该区域离线包数据大小，单位：byte
        downloadSize: ,     //数字类型；已下载离线包数据大小，单位：byte
        status:             //数字类型；城市离线数据状态，取值范围如下：
                            // 0：不存在
                            // 1：缓存状态
                            // 2：已安装
                            // 3：已过期  
    }                      
}
```

##示例代码

```js
var aMap = api.require('aMap');
aMap.getNationWide(function(ret){
    if(ret.status){
        alert(JSON.stringify(ret)); 
    }
});
```

##可用性

iOS系统

可提供的1.0.0及更高版本

<div id="m56"></div>

#**getAllCities**

获取全国所有离线地图城市信息，**无需调用 open 接口**

getAllCities(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true,           //布尔型；true||false
    cities : [{             //JSON对象；全国所有离线城市信息 
        name: '',           //字符串类型；区域名称
        adcode: '',         //字符串类型；区域编码
        cityCode:  ,        //字符串类型；城市编码
        jianpin: '',        //字符串类型；区域简拼
        pinyin: '',         //字符串类型；区域拼音
        size: ,             //数字类型；该区域离线包数据大小，单位：byte
        downloadSize: ,     //数字类型；已下载离线包数据大小，单位：byte
        status:             //数字类型；城市离线数据状态，取值范围如下：
                            // 0：不存在
                            // 1：缓存状态
                            // 2：已安装
                            // 3：已过期   
    }]                      
}
```

##示例代码

```js
var aMap = api.require('aMap');
aMap.getAllCities(function(ret){
    if(ret.status){
        alert(JSON.stringify(ret)); 
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m57"></div>

#**getVersion**

获取离线数据的版本号，**无需调用 open 接口。Android 平台不支持此接口**

getVersion(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true,         //布尔型；true||false
    versioin: '20130715'  //字符串类型；离线数据的版本号，由年月日组成, 如@"20130715"                 
}
```

##示例代码

```js
var aMap = api.require('aMap');
aMap.getVersion(function(ret){
    if(ret.status){
        alert(JSON.stringify(ret)); 
    }
});
```

##可用性

iOS系统

可提供的1.0.0及更高版本

<div id="m58"></div>

#**downloadRegion**

启动下载指定 adcode 区域的离线地图，**无需调用 open 接口**

downloadRegion({params}, callback(ret, err))

##params

adcode:

- 类型：字符串
- 描述：指定的区域的 adcode 码

shouldContinueWhenAppEntersBackground:

- 类型：布尔
- 描述：（可选项）进入后台是否允许继续下载
- 默认：false

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: 0,           //数字类型；取值范围如下：
                         // 0：以插入队列，等待中
                         // 1：开始下载
                         // 2：下载过程中
                         // 3：下载成功
                         // 4：取消
                         // 5：解压缩
                         // 6：全部顺利完成
                         // 7：发生错误 
    info: {              //JSON对象；离线包信息，仅当 status 为2时有值
        expectedSize: ,  //数字类型；离线包大小，单位：byte
        receivedSize:    //数字类型；已下载到本地离线包大小，单位：byte
    }              
}
```

##示例代码

```js
var aMap = api.require('aMap');
aMap.downloadRegion({
    adcode: '110000',
    shouldContinueWhenAppEntersBackground: true
}, function(ret){
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m59"></div>

#**isDownloading**

检测指定 adcode 的区域是否正在下载，**无需调用 open 接口**

isDownloading({params}, callback(ret, err))

##params

adcode:

- 类型：字符串
- 描述：指定的区域的 adcode 码

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true           //布尔型；是否正在下载，true||false                  
}
```

##示例代码

```js
var aMap = api.require('aMap');
aMap.isDownloading({
    adcode: '110000'
}, function(ret){
    if(ret.status){
        alert('正在下载'); 
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m60"></div>

#**pauseDownload**

暂停下载指定 adcode 区域的离线地图，**无需调用 open 接口，android端会暂停所有下载**

pauseDownload({params})

##params

adcode:

- 类型：字符串
- 描述：指定的区域的 adcode 码

##示例代码

```js
var aMap = api.require('aMap');
aMap.pauseDownload({
    adcode: '110000'
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m61"></div>

#**cancelAllDownload**

取消全部下载，**无需调用 open 接口，android端会取消所有下载**

cancelAllDownload()

##示例代码

```js
var aMap = api.require('aMap');
aMap.cancelAllDownload();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m62"></div>

#**clearDisk**

清除所有保存在磁盘上的离线地图数据, 之后调用 reloadMap 会使其立即生效

clearDisk()

##示例代码

```js
var aMap = api.require('aMap');
aMap.clearDisk();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m63"></div>

#**checkNewestVersion**

监测新版本，**Android 平台不支持此接口**

checkNewestVersion(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true           //布尔型；是否有新版本，true||false                  
}
```

##示例代码

```js
var aMap = api.require('aMap');
aMap.checkNewestVersion(function(ret) {
   if(ret.status) {
      alert ('有新版本');
   } else {
      alert ('无新版本');
   }
});
```

##可用性

iOS系统

可提供的1.0.0及更高版本

<div id="m64"></div>

#**reloadMap**

将离线地图下载解压、移除后，调用此函数使离线数据生效，**Android 平台不支持此接口**

reloadMap()

##示例代码

```js
var aMap = api.require('aMap');
aMap.reloadMap();
```

##可用性

iOS系统

可提供的1.0.0及更高版本