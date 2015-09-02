/*
Title: aMap
Description: 高德地图
*/

##基础类

<div class="outline">
[open](#m1)

[close](#m2)

[show](#a5)

[hide](#a6)

[getLocation](#m4)

[stopLocation](#m5)

[getCoordsFromName](#m31)

[getNameFromCoords](#m32)

[getDistance](#a3)

[getResolution](#a10)

[showUserLocation](#m13)

[panBy](#a9)

[setCenter](#n1)

[setZoomLevel](#n2)

[setMapAttr](#m3)

[setRotation](#n3)

[setOverlook](#n4)

[setBounds](#a1)

[getBounds](#a2)

[transCoords](#m7)

[interconvertCoords](#a8)

[zoomIn](#m15)

[zoomOut](#m14)

[addEventListener](#m35)

[removeEventListener](#m36)
</div>

##标注、气泡类

<div class="outline">
[addAnnotations](#m16)

[setBubble](#m17)

[popupBubble](#a7)

[addBillboard](#m18)

[removeAnnotations](#m20)
</div>

##覆盖物类

<div class="outline">
[addLine](#m21)

[addPolygon](#m22)

[addCircle](#m23)

[addImg](#m24)

[removeOverlay](#m25)
</div>

##搜索类

<div class="outline">
[addRoute](#m26)

[setRoutePlan](#m260)

[removeRoute](#m27)

[getRouteFromBusLine](#m33)

[removeBusRoute](#m34)

[autocomplete](#a4)

[searchInCity](#m28)

[searchNearby](#m29)

[searchInBounds](#m30)   
</div>

#**概述**

aMap 模块封装了高德地图的 SDK，集成了高德地图常用接口；使用此模块可实现高德地图常用的定位、关键字搜索、周边搜索、自定义标注及气泡、查公交路线等功能；用于实现高德地图常用功能。**带动画效果的接口不可同时调用，需要设置延迟（`setTimeout`）**。

**使用此模块之前必须先配置  config 文件，配置方法如下：**

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

<div id="m1"></div>

#**open**

打开高德地图

open({params}, callback(ret, err))

##params

rect：

- 类型：JSON对象
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

i18n：

- 类型：字符串
- 描述：（可选项）地图的语言类型
- 默认值：'zh_cn'
- 取值范围：
    - zh_cn（中文）
    - zh_en（中英文对照）
    - en（英文）

fixedOn：

- 类型：字符串
- 描述：（可选项）模块所属的 Window 或 Frame 的名字
- 默认值：当前 Window 的名字

fixed:

- 类型：布尔
- 描述：（可选项）模块是否随所属 Window 或 Frame 滚动
- 默认值：true（不随之滚动）

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true	 //布尔型；true||false
}
```

##示例代码

```js
var map = api.require('aMap');
map.open({
    rect: {
        x: 0,
        y: 0,
        w: 320,
        h: 300
    },
    center: {
        lon: 39.9994480000,
        lat: 116.4021310000,
    },
	zoomLevel: 10,
    showUserLocation: true,
    fixedOn: '',
    fixed: true
}, function(ret){
	if(ret.status){
        alert('地图打开成功');
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
var map = api.require('aMap');
map.close();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="a5"></div>

#**show**

显示高德地图

show()

##示例代码

```js
var map = api.require('aMap');
map.show();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="a6"></div>

#**hide**

隐藏高德地图

hide()

##示例代码

```js
var map = api.require('aMap');
map.hide();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m4"></div>

#**getLocation**

开始定位，**无需调用 open 接口即可定位**

getLocation({params}, callback(ret, err))

##params

accuracy：

- 类型：字符串
- 描述：（可选项）定位精度
- 默认值：'100m'
- 取值范围：
    - 10m
    - 100m
    - 1km
    - 3km

autoStop：

- 类型：布尔
- 描述：（可选项）获取到位置信息后是否自动停止定位
- 默认值：true

filter：

- 类型：数字
- 描述：（可选项）位置更新所需的最小距离（单位米），autoStop 为 true 时，此参数有效
- 默认值：1.0

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true,               //布尔型；true||false
    lon: 116.213,               //数字类型；经度
    lat: 39.213,                //数字类型；纬度
    timestamp: 1396068155591    //数字类型；时间戳
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
    code: 0,         //数字类型；错误码
    msg: ''          //字符串类型；错误信息说明
}
```

##示例代码

```js
var aMap = api.require('aMap');
aMap.getLocation({
    accuracy: '100m',
    autoStop: true,
    filter: 1
}, function(ret, err){
    if(ret.status){
        alert(JSON.stringify(ret));
    }else{
        alert(err.code);
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m5"></div>

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


<div id="m31"></div>

#**getCoordsFromName**

根据地址查找经纬度，**无需调用 open 接口即可使用**

getCoordsFromName({params}, callback(ret, err))

##params

city：

- 类型：字符串
- 描述：地址所在城市

address：

- 类型：字符串
- 描述：地址信息

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true,        //布尔型；true||false
    lon: 116.351,        //数字类型；地址所在经度
    lat: 39.283          //数字类型；地址所在纬度
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
    code: 1           //数字类型；错误码
                      //1（检索词有岐义）
                      //2（检索地址有岐义）
                      //3（没有找到检索结果）
                      //4（key错误）
                      //5（网络连接错误）
                      //6（网络连接超时）
                      //7（还未完成鉴权，请在鉴权通过后重试）
}
```

##示例代码

```js
var map = api.require('aMap');
map.getCoordsFromName({
    city: '北京',
    address: '天安门'
},function(ret,err){
    if(ret.status){
       alert(JSON.stringify(ret));
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m32"></div>

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

- 类型：JSON对象
- 内部字段：

```js
{
    status: true,              //布尔型；true||false
    lon: 116.351,              //数字类型；经度
    lat: 39.283,               //数字类型；纬度
    address: '',               //字符串类型；地址信息
    province: '',              //字符串类型；省份
    city: '',                  //字符串类型；城市
    district: '',              //字符串类型；县区
    streetName: '',            //字符串类型；街道名
    streetNumber: ''           //字符串类型；街道号
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
    code: 1           //数字类型；错误码
                      //1（检索词有岐义）
                      //2（检索地址有岐义）
                      //3（没有找到检索结果）
                      //4（key错误）
                      //5（网络连接错误）
                      //6（网络连接超时）
                      //7（还未完成鉴权，请在鉴权通过后重试）
}
```

##示例代码

```js
var map = api.require('aMap');
map.getNameFromCoords({
    lon: 116.384767,
    lat: 39.989539
},function(ret,err){
    if(ret.status){
        alert(JSON.stringify(ret));
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="a3"></div>

#**getDistance**

获取地图两点之间的距离，**无需调用 open 接口即可使用**

getDistance({params}, callback(ret, err))

##params

start：

- 类型：JSON对象
- 描述：起点经纬度
- 内部字段：

```js
{
    lon: 106.486654,    //数字类型；起点的经度
    lat: 29.490295      //数字类型；起点的纬度
}
```

end：

- 类型：JSON对象
- 描述：终点经纬度
- 内部字段：

```js
{
    lon: 106.581515,    //数字类型；终点的经度
    lat: 29.615467      //数字类型；终点的纬度
}
```

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true,              //布尔型；true||false
    distance: 16670.90         //数字类型；两点之间的距离，单位：米
}
```

##示例代码

```js
var map = api.require('aMap');
map.getDistance({
    start: {
        lon: 106.486654,
        lat: 29.490295
    },
    end: {
        lon: 106.581515,
        lat: 29.615467
    }
},function(ret){
    if(ret.status){
        alert(ret.distance);
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="a10"></div>

#**getResolution**

获取地图地面分辨率

getResolution(callback(ret, err))

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true,     //布尔型；true||false
    resolution: 500   //数字类型；地图地面分辨率，单位：米/像素
}
```

##示例代码

```js
var map = api.require('aMap');
map.getResolution(function(ret){
    if(ret.status){
        alert(JSON.stringify(ret));
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m13"></div>

#**showUserLocation**

是否在地图上显示用户位置

showUserLocation({params})

##params

isShow：

- 类型：布尔
- 描述：（可选项）是否显示用户位置
- 默认值：true

trackingMode：

- 类型：字符串
- 描述：（可选项）用户当前位置显示形式
- 默认值：none
- 取值范围：
    - none（标准模式）
    - follow（跟踪模式）
    - compass（罗盘模式）

##示例代码

```js
var map = api.require('aMap');
map.showUserLocation({
    isShow: true,
    trackingMode: 'none'
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="a9"></div>

#**panBy**

根据设置的像素值平移地图

panBy({params})

##params

x：

- 类型：数字
- 描述：水平移动的像素值，正值为向右移动，负值为向左移动

y：

- 类型：数字
- 描述：垂直移动的像素值，正值为向下移动，负值为向上移动

##示例代码

```js
var map = api.require('aMap');
map.panBy({
    x: 50,
    y: 100
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="n1"></div>

#**setCenter**

根据经纬度设置高德地图中心点，**此接口可带动画效果**

setCenter({params})

##params

coords：

- 类型：JSON对象
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
var map = api.require('aMap');
map.setCenter({
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

<div id="n2"></div>

#**setZoomLevel**

设置高德地图缩放等级，**此接口自带动画效果**

setZoomLevel({params})

##params

level：

- 类型：数字
- 描述：（可选项）地图比例尺级别，取值范围：3-18级
- 默认值：10

##示例代码

```js
var map = api.require('aMap');
map.setZoomLevel({
    level: 10
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m3"></div>

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
    - trafficOn（打开实时路况）
    - trafAndsate（实时路况和卫星地图）
    - satellite（卫星地图）

zoomEnable：

- 类型：布尔
- 描述：（可选项）捏合手势是否可以缩放地图
- 默认值：true

scrollEnable：

- 类型：布尔
- 描述：（可选项）拖动手势是否可以移动地图
- 默认值：ture

##示例代码

```js
var map = api.require('aMap');
map.setMapAttr({
    type: 'standard'
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="n3"></div>

#**setRotation**

设置高德地图旋转角度，**此接口自带动画效果**

setRotation({params})

##params

degree：

- 类型：数字
- 描述：（可选项）地图旋转角度，取值范围：-180° - 180°
- 默认值：0

##示例代码

```js
var map = api.require('aMap');
map.setRotation({
    degree: 30
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="n4"></div>

#**setOverlook**

设置高德地图俯视角度，**此接口自带动画效果**

setOverlook({params})

##params

degree：

- 类型：数字
- 描述：（可选项）地图俯视角度，取值范围：-45° - 0°
- 默认值：0

##示例代码

```js
var map = api.require('aMap');
map.setOverlook({
    degree: -30
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="a1"></div>

#**setRegion**

设置地图显示范围（矩形区域），**此接口可带动画效果**

setRegion({params})

##params

center：

- 类型：JSON对象
- 描述：中心点的经纬度
- 内部字段：

```js
{
    lon: 116.404,       //数字类型；设置中心点的经度
    lat: 39.915         //数字类型；设置中心点的纬度
}
```

region：

- 类型：JSON对象
- 描述：（可选项）设置地图的区域大小
- 内部字段：

```js
{
    w: 1000,           //（可选项）数字类型；设置地图区域的宽，单位：米
    h: 1000            //（可选项）数字类型；设置地图区域的高度，单位：米
}
```

animation：

- 类型：布尔类型
- 描述：（可选项）设置地图的区域时，是否带动画效果
- 默认：true

##示例代码

```js
var map = api.require('aMap');
map.setRegion({
    center: {
        lon: 116.404,       //数字类型；设置中心点的经度
        lat: 39.915         //数字类型；设置中心点的纬度
    }, 
    region:{
	     w: 900,            //（可选项）数字类型；设置地图区域的宽，单位：米
	     h: 900             //（可选项）数字类型；设置地图区域的高度，单位：米
    }, 
    animation: true
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="a2"></div>

#**getRegion**

获取地图显示范围（矩形区域）

getRegion(callback(ret))

##callback

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true,                //布尔型；true||false
    center: ,                    //JSON 对象；矩形区域对角线点经纬度，内部字段如下：
                                   {
                                      lat:   //数字类型；纬度
                                      lon:   //数字类型；经度
                                   }
    region:                      //JSON 对象；矩形区域的宽和高，内部字段如下：
                                   {
                                      w:     //数字类型；宽
                                      h:     //数字类型；高
                                   }
}
```

##示例代码

```js
var map = api.require('aMap');
map.getRegion(function(ret){
    if(ret.status){
        alert(JSON.stringify(ret));
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m7"></div>

#**transCoords**

将其它类型的地理坐标转换为高德坐标。**无需调用 open 接口即可使用**

transCoords({params}, callback(ret, err))

##params

type：

- 类型：字符串
- 描述：原始地理坐标类型
- 默认值：common
- 取值范围：
     - gps（GPS设备采集的原始GPS坐标）
     - common（google、soso、aliyun、mapabc、amap和高德地图所用坐标）

lon：

- 类型：数字
- 描述：原始地理坐标经度

lat：

- 类型：数字
- 描述：原始地理坐标纬度

mcode：

- 类型：字符串
- 描述：到[高德地图开放平台](http://lbsyun.baidu.com/apiconsole/key)获取的安全码，点击应用的设置按钮 -> 设置界面 -> 安全码（数字签名+;+包名）

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true,  //布尔型；true||false
    lon: 116.213,  //数字类型；转换后的高德地理坐标经度
    lat: 39.213    //数字类型；转换后的高德地理坐标纬度
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
    code: 1         //数字类型；错误码
                    //1：（参数非法）
                    //2：（转换失败）
}
```

##示例代码

```js
var map = api.require('aMap');
map.transCoords({
    type: "common",
    lon: 116.351,
    lat: 39.283,
    mcode: '0B:13:25:D7:85:46:0A:67:12:F3:29:88:64:56:63:10:7A:9C:C4:59;com.apicloud.A6985734480360'
}, function(ret, err){
    alert(JSON.stringify(ret));
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="a8"></div>

#**interconvertCoords**

经纬度坐标与地图容器像素坐标相互转换，经纬度和x，y值传一种即可。

interconvertCoords({params}, callback(ret))

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

- 类型：JSON对象
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
var map = api.require('aMap');
map.interconvertCoords({
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

<div id="m15"></div>

#**zoomIn**

缩小地图，放大视角，放大一级比例尺，**此接口自带动画效果**

zoomIn()

##示例代码

```js
var map = api.require('aMap');
map.zoomIn();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m14"></div>

#**zoomOut**

放大地图，缩小视角，缩小一级比例尺，**此接口自带动画效果**

zoomOut()

##示例代码

```js
var map = api.require('aMap');
map.zoomOut();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m35"></div>

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
    - dbclick（双击事件）

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true,           //布尔型；true||false
    lon: 116.351,           //数字类型；触发事件的地点的经度（longPress，click，dbclick），地图中心的经度（viewChange）
    lat: 39.283,            //数字类型；触发事件的地点的纬度（longPress，click，dbclick），地图中心的经度（viewChange）
    zoom: 30,               //数字类型；地图缩放角度
    rotate: 30,             //数字类型；地图旋转角度
    overlook: 30            //数字类型；视角倾斜度
}
```

##示例代码

```js
var map = api.require('aMap');
map.addEventListener({
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

<div id="m36"></div>

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
    - dbclick（双击事件）

##示例代码

```js
var map = api.require('aMap');
map.removeEventListener({
    name: 'longPress'
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m16"></div>

#**addAnnotations**

在地图上添加标注信息

addAnnotations({params}, callback(ret))

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
    icon: 'widget://'          //（可选项）字符串类型；指定的标注图标，要求本地路径（fs://，widget://），若不传则显示公用的 bgImg 图标
}]
```

icon：

- 类型：字符串
- 描述：（可选项）公用的标注图标，要求本地路径（fs://，widget://）
- 默认值：红色大头针

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    id: 10      //数字类型；用户点击标注返回的id
}
```

##示例代码

```js
var map = api.require('aMap');
map.addAnnotations({
    annotations: [{
        id: 1, lon: 116.297, lat: 40.109
    },
    {
        id: 2, lon: 116.29, lat: 40.109
    },
    {
        id: 3, lon: 116.298, lat: 40.11
    }],
    icon: 'widget://'
}, function(ret){
    if(ret){
        alert(ret.id);
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m17"></div>

#**setBubble**

设置点击标注时弹出的气泡信息

setBubble({params}, callback(ret))

##params

id：

- 类型：数字
- 描述：要设置的气泡的 id

bgImg：

- 类型：字符串
- 描述：（可选项）弹出气泡的背景图片（160*60规格），要求本地路径（fs://，widget://）
- 默认值：默认气泡样式

content：

- 类型：JSON对象
- 描述：弹出气泡的内容
- 内部字段：

```js
{
    title: '',             //（可选项）字符串类型；弹出气泡的标题
    subTitle: '',          //（可选项）字符串类型；弹出气泡的概述内容 
    illus: ''              //（可选项）字符串类型；弹出气泡的配图，支持http://、https://、widget://、fs://等协议
}
```

styles：

- 类型：JSON对象
- 描述：弹出气泡的样式
- 内部字段：

```js
{
    titleColor: '#000',             //（可选项）字符串类型；气泡标题的文字颜色；默认：'#000'
    titleSize: 16,                  //（可选项）数字类型；气泡标题的文字大小；默认：16
    subTitleColor: '#999',          //（可选项）字符串类型；气泡概述内容的文字颜色；默认：'#999'
    subTitleSize: 12,               //（可选项）数字类型；气泡概述内容的文字大小；默认：16
    illusAlign: 'left'              //（可选项）字符串类型；气泡配图的显示位置；默认：'left'
                                    //取值范围：
                                    //left（图片居左）
                                    //right（图片居右）
}
```

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    id: 10,                     //数字类型；用户点击气泡返回的id
    eventType: 'clickContent',   //字符串类型；交互事件类型
                                //取值范围：
                                //clickContent（点击气泡文本内容）
                                //clickIllus（点击配图）
}
```

##示例代码

```js
var map = api.require('aMap');
map.setBubble({
    id: 2,
    bgImg: 'widget://res/bubble_bg.png',
    content: {
        title: '大标题',
        subTitle: '概述内容',
        illus: 'http://example.com/a.jpg'
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

<div id="a7"></div>

#**popupBubble**

弹出气泡信息

popupBubble({params})

##params

id：

- 类型：数字
- 描述：气泡的 id

##示例代码

```js
var map = api.require('aMap');
map.popupBubble({
    id: 2
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m18"></div>

#**addBillboard**

在地图上添加布告牌

addBillboard({params})

##params

coords：

- 类型：JSON对象
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
- 描述：布告牌的背景图片（160*60规格），要求本地路径（fs://，widget://）

content：

- 类型：JSON对象
- 描述：布告牌的内容
- 内部字段：

```js
{
    title: '',             //（可选项）字符串类型；布告牌的标题
    subTitle: '',          //（可选项）字符串类型；布告牌的概述内容 
    illus: ''              //（可选项）字符串类型；布告牌的配图，支持http://、https://、widget://、fs://等协议
}
```

styles：

- 类型：JSON对象
- 描述：布告牌的样式
- 内部字段：

```js
{
    titleColor: '#000',             //（可选项）字符串类型；布告牌标题的文字颜色；默认：'#000'
    titleSize: 16,                  //（可选项）数字类型；布告牌标题的文字大小；默认：16
    subTitleColor: '#999',          //（可选项）字符串类型；布告牌概述内容的文字颜色；默认：'#999'
    subTitleSize: 12,               //（可选项）数字类型；布告牌概述内容的文字大小；默认：16
    illusAlign: 'left'              //（可选项）字符串类型；布告牌配图的显示位置；默认：'left'
                                    //取值范围：
                                    //left（图片居左）
                                    //right（图片居右）
}
```

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    id: 10,                     //数字类型；用户点击布告牌返回的id
    eventType: 'clickContent',   //字符串类型；交互事件类型
                                //取值范围：
                                //clickContent（点击布告牌文本内容）
                                //clickIllus（点击配图）
}
```

##示例代码

```js
var map = api.require('aMap');
map.addBillboard({
    coords: {
        lon: 116.233,
        lat: 39.134
    },
    bgImg: 'widget://res/bubble_bg.png',
    content: {
        title: '大标题',
        subTitle: '概述内容',
        illus: 'http://example.com/a.jpg'
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

<div id="m20"></div>

#**removeAnnotations**

移除指定id的标注或布告牌

removeAnnotations({params})

##params

ids：

- 类型：数组
- 描述：要移除的标注或布告牌id（数字）

##示例代码

```js
var map = api.require('aMap');
map.removeAnnotations({
    idArray: [1,3,5,7]
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m21"></div>

#**addLine**

在地图上添加直线

addLine({params})

##params

id：

- 类型：数字
- 描述：直线的 id

styles：

- 类型：JSON对象
- 描述：（可选项）直线的样式
- 内部字段：

```js
{
    borderColor: '#000',            //（可选项）字符串类型；直线的颜色，支持rgb、rgba、#；默认值：'#000'
    borderWidth: 3                  //（可选项）数字类型；直线的宽度，默认：2
}
```

points：

- 类型：数组
- 描述：直线的两个点组成的数组
- 内部字段：

```js
[{
    lon: 116.297,     //数字类型；经度
    lat: 40.109       //数字类型；纬度
}]
```

##示例代码

```js
var map = api.require('aMap');
map.addLine({
    id: 100,
    styles: {
        borderColor: '#FF0000',
        borderWidth: 3
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

<div id="m22"></div>

#**addPolygon**

在地图上添加多边形

addPolygon({params})

##params

id：

- 类型：数字
- 描述：多边形的 id

styles：

- 类型：JSON对象
- 描述：（可选项）多边形的样式
- 内部字段：

```js
{
    borderColor: '#000',    //（可选项）字符串类型；多边形的边框颜色，支持rgb、rgba、#；默认：'#000'
    borderWidth: 3          //（可选项）数字类型；多边形的边框宽度，默认：2
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
var map = api.require('aMap');
map.addPolygon({
    id: 100,
    styles: {
        borderColor: '#FF0000',
        borderWidth: 3
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

<div id="m23"></div>

#**addCircle**

在地图上添加圆形

addCircle({params})

##params

id：

- 类型：数字
- 描述：圆形的 id

center：

- 类型：JSON对象
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

- 类型：JSON对象
- 描述：（可选项）圆形的样式
- 内部字段：

```js
{
    borderColor: '#000',          //（可选项）字符串类型；圆形的边框颜色，支持rgb、rgba、#；默认：'#000'
    borderWidth: 3                //（可选项）数字类型；圆形的边框宽度，默认：2
}
```

##示例代码

```js
var map = api.require('aMap');
map.addCircle({
    id: 101,
    center: {
        lon: 116.298,
        lat: 40.11,
    },
    radius: 500,
    styles: {
        borderColor: '#FF0000',
        borderWidth: 3
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m24"></div>

#**addImg**

在地图上添加图片

addImg({params})

#**params**

id：

- 类型：数字
- 描述：图片 id

imgPath：

- 类型：字符串
- 描述：图片的路径，要求本地路径（fs://，widget://）

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
var map = api.require('aMap');
map.addImg({
    id: 200,
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

<div id="m25"></div>

#**removeOverlay**

移除指定 id 的覆盖物

removeOverlay({params})

##params

ids：

- 类型：数组
- 描述：要移除的 id（数字）组成的数组

##示例代码

```js
var map = api.require('aMap');
map.removeOverlay({
    ids: [1, 3, 5, 7]
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m26"></div>

#**addRoute**

添加路线方案

addRoute({params}, callback(ret, err))

##params

id：

- 类型：数字
- 描述：路线 id

type：

- 类型：字符串
- 描述：路线类型
- 取值范围：
    - drive（开车）
    - transit（公交）
    - walk（步行）

policy：

- 类型：字符串
- 描述：路线策略
- 默认值：'ebus_time_first'
- 取值范围：
    - ecar_fee_first（驾乘检索策略常量：较少费用）
    - ecar_dis_first（驾乘检索策略常量：最短距离）
    - ecar_time_first（驾乘检索策略常量：时间优先）
    - ecar_avoid_jam（驾车策略：躲避拥堵）
    - ebus_no_subway（公交检索策略常量：不含地铁）
    - ebus_time_first（公交检索策略常量：时间优先）
    - ebus_transfer_first（公交检索策略常量：最少换乘）
    - ebus_walk_first（公交检索策略常量：最少步行距离）

start：

- 类型：JSON对象
- 描述：起点信息，**可以通过经纬度坐标或城市名加地名确定**
- 内部字段：

```js
{
    city: '北京',        //字符串类型；起点城市
    name: '天安门',      //（可选项）字符串类型；起点名
    lon: 116.213,        //（可选项）数字类型；起点经度
    lat: 39.213          //（可选项）数字类型；起点纬度
}
```

end：

- 类型：JSON对象
- 描述：终点信息，**可以通过经纬度坐标或城市名加地名确定**
- 内部字段：

```js
{
    city: '北京',         //字符串类型；终点城市
    name: '泰翔商务楼',   //（可选项）字符串类型；终点名
    lon: 116.213,         //（可选项）数字类型；终点经度
    lat: 39.213           //（可选项）数字类型；终点纬度
}
```

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true,    //布尔型；true||false
    steps: [],       //数组类型；路线每个站点的信息
    plans: []        //数组类型；路线方案描述，包含该方案的总时间和距离
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
    code: 0,            //数字类型；
                        //错误码：
                        //0（检索结果正常）
                        //1（检索词有歧义）
                        //2（检索地址有歧义）
                        //3（该城市不支持公交搜索）
                        //4（不支持跨城市公交）
                        //5（没有找到检索结果）
                        //6（起终点太近）
    //数组类型；建议起点信息，若传入的起点信息不明确，则返回该字段
    suggestStarts: [{   
        name: '',       //字符串类型；地点名
        city: '',       //字符串类型；地点所在城市
        lon: 116.213,   //数字类型；地点经度
        lat: 39.213     //数字类型；地点纬度
    }],
    //数组类型；建议终点信息，若传入的终点信息不明确，则返回该字段
    suggestEnds: [{     
        name: '',       //字符串类型；地点名
        city: '',       //字符串类型；地点所在城市
        lon: 116.213,   //数字类型；地点经度  
        lat: 39.213     //数字类型；地点纬度
    }]
}
```

##示例代码

```js
var map = api.require('aMap');
map.addRoute({
    id: 300,
    type: 'drive',
    policy: 'ecar_fee_first',
    start: {
        city: '北京',
        name: '史各庄南',
        lon: 116.213,
        lat: 39.213
    },
    end: {
        city: '北京',
        name: '龙翔路',
        lon: 116.384,
        lat: 39.989
    }
}, function(ret, err){
    if(ret.status){
        api.alert({msg:"路线添加完成"});
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m260"></div>

#**setRoutePlan**

设置已添加路线的方案，**此接口须在调用 addRoute 接口之后才可调用**

setRoutePlan({params}, callback(ret, err))

##params

planIndex：

- 类型：数字
- 描述：添加路线时返回的所有方案的索引
- 默认值：0

##示例代码

```js
var map = api.require('aMap');
map.setRoutePlan({
    planIndex: 1
});
```

##可用性

Android系统

可提供的1.0.0及更高版本

<div id="m27"></div>

#**removeRoute**

移除指定 id 的路线

removeRoute({params})

##params

ids：

- 类型：数组
- 描述：所要移除的 id（数字）组成的数组

##示例代码

```js
var map = api.require('aMap');
map.removeRoute({
    ids: [300, 301, 302]
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m33"></div>

#**getRouteFromBusLine**

根据公交线路号查询路线详情并显示在地图上

getRouteFromBusLine({params}, callback(ret, err))

##params

city：

- 类型：字符串
- 描述：城市

line：

- 类型：字符串
- 描述：公交线路号

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true,              //布尔型；true||false
    busName: '',               //字符串类型；公交名字
    busCompany: '',            //字符串类型；公交公司
    startTime: '',             //字符串类型；最早发车时间
    endTime: '',               //字符串类型；最晚班车时间
    stopInfo: []               //数组类型；所有站点信息
}
```

##示例代码

```js
var map = api.require('aMap');
map.getRouteFromBusLine({
    city: '北京',
    line: '345'
},function(ret){
    if(ret.status){
        alert(JSON.stringify(ret));
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m34"></div>

#**removeBusRoute**

移除地图上显示的公交线路

removeBusRoute()

##示例代码

```js
var map = api.require('aMap');
map.removeBusRoute();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="a4"></div>

#**autocomplete**

根据关键字返回10条提示词条

autocomplete({params}, callback(ret))

##params

keyword：

- 类型：字符串
- 描述：关键字

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true,           //布尔型；true||false
    results: [{             //数组类型；返回搜索结果
        address: '',        //字符串类型；地点信息
        district: ''        //字符串类型；地点所在区
    }]             
}
```

##示例代码

```js
var map = api.require('aMap');
map.autocomplete({
    keyword: '北京西站'
},function(ret){
    if(ret.status){
        alert(JSON.stringify(ret.results)); 
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m28"></div>

#**searchInCity**

根据单个关键字搜索兴趣点

searchInCity({params}, callback(ret, err))

##params

city：

- 类型：字符串
- 描述：要搜索的城市

keyword：

- 类型：字符串
- 描述：搜索的关键字

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true,           //布尔型；true||false
    totalNum: 10,           //数字类型；本次搜索的总结果数
    currentNum: 5,          //数字类型；当前页的结果数
    totalPage: 10,          //数字类型；本次搜索的总页数
    pageIndex: 1,           //数字类型；当前页的索引
    results: [{             //数组类型；返回搜索结果列表
        lon: 116.213,       //数字类型；当前内容的经度
        lat: 39.213,        //数字类型；当前内容的纬度
        name: '',           //字符串类型；名称
        uid: 123            //数字类型；兴趣点的id
        address: '',        //字符串类型；地址
        city: '',           //字符串类型；所在城市
        phone: '',          //字符串类型；电话号码
        postCode: '',       //字符串类型；邮编
        poiType: 0          //数字类型；POI 类型
                            //取值类型：
                            //0（普通点）
                            //1（公交站）
                            //2（公交线路）
                            //3（地铁站）
                            //4（地铁线路）
    }]             
}
```

##示例代码

```js
var map = api.require('aMap');
map.searchInCity({
    city: '北京',
    keyword: '学校'
},function(ret){
    if(ret.status){
       alert(JSON.stringify(ret)); 
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m29"></div>

#**searchNearby**

根据单个关键字在圆形区域内搜索兴趣点

searchNearby({params}, callback(ret, err))

##params

keyword：

- 类型：字符串
- 描述：搜索关键字

lon：

- 类型：数字
- 描述：指定区域中心点的经度

lat：

- 类型：数字
- 描述：指定区域中心点的纬度

radius：

- 类型：数字
- 描述：指定区域的半径，单位为 m（米）

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true,           //布尔型；true||false
    totalNum: 20,           //数字类型；本次搜索的总结果数
    currentNum: 5,          //数字类型；当前页的结果数
    totalPage: 3,           //数字类型；本次搜索的总页数
    pageIndex: 1,           //数字类型；当前页的索引
    results: [{             //数组类型；返回搜索结果列表
        lon: 116.213,       //数字类型；当前内容的经度
        lat: 39.213,        //数字类型；当前内容的纬度
        name: '',           //字符串类型；名称
        uid: 123            //数字类型；兴趣点id
        address: '',        //字符串类型；地址
        city: '',           //字符串类型；所在城市
        phone: '',          //字符串类型；电话号码
        postCode: '',       //字符串类型；邮编
        poiType: 0          //数字类型；POI 类型
                            //取值类型：
                            //0（普通点）
                            //1（公交站）
                            //2（公交线路）
                            //3（地铁站）
                            //4（地铁线路）
    }]  
}
```

##示例代码

```js
var map = api.require('aMap');
map.searchNearby({
    keyword: 'KTV',
    lon: 116.384767,
    lat: 39.989539,
    radius: 2000
},function(ret,err){
    if(ret.status){
        alert(JSON.stringify(ret));
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m30"></div>

#**searchInBounds**

根据单个关键字在方形区域内搜索兴趣点

searchInBounds({params}, callback(ret, err))

##params

keyword：

- 类型：字符串
- 描述：搜索关键字

lbLon：

- 类型：数字
- 描述：矩形左下角的经度

lbLat：

- 类型：数字
- 描述：矩形左下角的纬度

rtLon：

- 类型：数字
- 描述：矩形右上角的经度

rtLat：

- 类型：数字
- 描述：矩形右上角的纬度

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true,           //布尔型；true||false
    totalNum: 20,           //数字类型；本次搜索的总结果数
    currentNum: 5,          //数字类型；当前页的结果数
    totalPage: 3,           //数字类型；本次搜索的总页数
    pageIndex: 1,           //数字类型；当前页的索引
    results: [{             //数组类型；返回搜索结果列表
        lon: 116.213,       //数字类型；当前内容的经度
        lat: 39.213,        //数字类型；当前内容的纬度
        name: '',           //字符串类型；名称
        uid: 123            //数字类型；兴趣点id
        address: '',        //字符串类型；地址
        city: '',           //字符串类型；所在城市
        phone: '',          //字符串类型；电话号码
        postCode: '',       //字符串类型；邮编
        poiType: 0          //数字类型；POI 类型
                            //取值类型：
                            //0（普通点）
                            //1（公交站）
                            //2（公交线路）
                            //3（地铁站）
                            //4（地铁线路）
    }]
}
```

##示例代码

```js
var map = api.require('aMap');
map.searchInBounds({
    keyword: '图书馆', 
    lbLon: 112.47723797622677, 
    lbLat: 34.556480000000015, 
    rtLon: 109.77539000000002, 
    rtLat: 33.43144 
},function(ret,err){
    if(ret.status){
        alert(JSON.stringify(ret));
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本