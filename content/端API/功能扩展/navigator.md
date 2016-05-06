/*
Title: navigator
Description: navigator
*/

<p style="color: #ccc;margin-bottom: 30px;">来自于：开发者</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>
<div id="method-content">

<div class="outline">

 [installed](#a1)
 
 [bMapNavigation](#a2)
 
 [aMapNavigation](#a3)
 
 [aMapPath](#a4)
 
 [gMapNavigation](#a5)
 
 [appleNavigation](#a6)
</div>

#**概述**

navigator 模块集成了打开高德、百度、谷歌地图导航的相关接口，在 iOS 平台上支持打开系统自带地图导航。亦可通过本模块相应接口判断当前设备是否已安装高德、百度、谷歌地图，本模块是个人开发者提交模块，需云编译或自定义 loader 使用。
   
    
#**install**<div id="a1"></div>

判断当前设备是否已安装高德、谷歌、百度地图

installed({params}, callback(ret, err))

##params

target：

- 类型：字符串
- 默认值：bMap
- 描述：判断的对象，取值范围如下：
	- bMap：百度地图
	- aMap：高德地图
	- gMap：谷歌地图

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status:       //布尔类型；是否安装指定的地图，true|false
}
```


##示例代码

```js
var navigator = api.require('navigator');
navigator.installed({
    target: 'aMap'
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

#**bMapNavigation**<div id="a2"></div>

打开百度地图并开始导航

bMapNavigation({params})

##params

start：

- 类型：JSON 对象
- 描述：起点信息，**地址和经纬度信息，不能同时为空（不传）**
- 内部字段：

```js
{
   lon:          //（可选项）数字类型；起点经度，经纬度参数同时存在或同时为空，视为有效参数，与起点名称合为空
   lat:          //（可选项）数字类型；起点纬度，经纬度参数同时存在或同时为空，视为有效参数，与起点名称配合为空
   name:         //（可选项）字符串类型；起点名称，与经纬度参数配合为空
}
```

end：

- 类型：JSON 对象
- 描述：终点信息，**地址和经纬度信息，不能同时为空（不传）**
- 内部字段：

```js
{
    lon:         //（可选项）数字类型；终点经度，经纬度参数同时存在或同时为空，视为有效参数，与终点名称配合为空
    lat:         //（可选项）数字类型；终点纬度，经纬度参数同时存在或同时为空，视为有效参数，与终点名称配合为空
    name:        //（可选项）字符串类型；终点名称，与经纬度参数配合为空
}
```

mode：

- 类型：字符串
- 默认值：driving
- 描述：（可选项）导航路线类型，取值范围如下：
	- driving：驾车
	- transit：公交
	- walking：步行

##示例代码

```js
var navigator = api.require('navigator');
navigator.bMapNavigation({
    start: {				 	// 起点信息.
		lon: 112.4772379, 		// 经度.
		lat: 34.55648, 			// 纬度.
        name: ''
    },
    end: { 						// 终点信息.
		lon: 112.57062599, 		// 经度
		lat: 33.784214,			// 纬度
        name: ''
    },
    mode: 'driving'
});
```
##补充说明

若起点或终点都传了经纬度和地址信息，则以经纬度信息为准

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**aMapNavigation**<div id="a3"></div>

打开高德地图并开始从当前位置导航，**IOS 平台上导航结束可跳转回本应用（确保config 配置无误）**

aMapNavigation({params})

##params

end：

- 类型：JSON 对象
- 描述：终点信息
- 内部字段：

```js
{
     lon:         //数字类型；终点经度
     lat:         //数字类型；终点纬度
}
```

dev：

- 类型：布尔
- 描述：是否偏移（国测加密，wgs84 坐标系）
- 默认值：false（ lat 和 lon 是已经加密后的，不需要国测加密，gcj02 坐标系）

strategy：

- 类型：字符串
- 默认值：fast
- 描述：导航路线策略，取值范围如下：
	- fast： 			速度最快
	- fee： 			费用最少
	- distance： 		距离最短
	- highway： 		不走高速
	- jam： 			躲避拥堵
	- highwayFee： 		不走高速且避免收费
	- highwayJam： 		不走高速且躲避拥堵
	- feeJam： 			躲避收费和拥堵
	- highwayFeeJam： 	不走高速躲避收费和拥堵

##示例代码

```js
var navigator = api.require('navigator');
navigator.aMapNavigation({
    end:{
		lon: 112.570,
		lat: 33.784214
    },
    dev: 0,
    strategy: 'fast'
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**aMapPath**<div id="a4"></div>

打开高德地图并开始路线规划

aMapPath({params})

##params

start：

- 类型：JSON 对象
- 描述：（可选项）起点信息
- 内部字段：

```js
{
    lon:           //（可选项）数字类型；起点经度，经纬度参数同时存在或同时为空，视为有效参数，与起点名称配合为空
    lat:           //（可选项）数字类型；起点纬度，经纬度参数同时存在或同时为空，视为有效参数，与起点名称配合为空

    name:          //（可选项）字符串类型；起点名称，与经纬度信息配合为空
}
```

end：

- 类型：JSON 对象
- 描述：终点信息
- 内部字段：

```js
{
    lon:           //（可选项）数字类型；终点经度，经纬度参数同时存在或同时为空，视为有效参数，与终点名称配合为空
    lat:           //（可选项）数字类型；终点纬度，经纬度参数同时存在或同时为空，视为有效参数，与终点名称配合为空

    name:          //（可选项）字符串类型；终点名称，与经纬度信息配合为空
}
```

mode：

- 类型：字符串
- 默认值：driving
- 描述：导航路线类型，取值范围如下：
	- driving：驾车
	- transit：公交
	- walking：步行

strategy：

- 类型：字符串
- 默认值：drive_fast/transit_fast
- 描述：导航路线策略，取值范围如下：
	- drive_fast：			驾车速度最快
	- drive_fee： 			驾车费用最少
	- drive_distance： 		驾车距离最短
	- drive_highway： 		驾车不走高速
	- drive_jam： 			驾车躲避拥堵
	- drive_highwayFee： 	驾车不走高速且避免收费
	- drive_highwayJam： 	驾车不走高速且躲避拥堵
	- drive_feeJam： 		驾车躲避收费和拥堵
	- drive_highwayFeeJam： 驾车不走高速躲避收费和拥堵
	- transit_fast： 		公交最快捷
	- transit_transfer： 	公交最少换乘
	- transit_step： 		公交最少步行
	- transit_subwayNo： 	公交不乘地铁
	- transit_subway： 		只坐地铁
	- transit_time： 		公交时间短

##示例代码

```js
var navigator = api.require('navigator');
navigator.aMapPath({
    start: { 
		lon: 112.477237 , 
		lat: 34.55648
    },
    end: {
		lon: 112.5706259 , 
		lat: 33.784214
    },
    mode: 'driving',
    strateggy: 'drive_fast'
});
```
##补充说明

1. 起点经纬度参数不为空，则路线以此坐标发起路线规划 。 
2. 起点经纬度参数为空，且起点名称不为空，则以此名称发起路线规划。
3. 起点经纬度参数为空，且起点名称为空，则以“我的位置”发起路线规划。 
4. 终点经纬度参数不为空，则路线以此坐标发起路线规划 。 
5. 终点经纬度参数为空，且终点名称不为空，则以此名称发起路线规划。 
6. 终点经纬度参数为空，且终点点名称为空，则以“我的位置”发起路线规划。

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**gMapNavigation**<div id="a5"></div>

打开谷歌地图并开始导航

gMapNavigation({params})

##params

start：

- 类型：JSON 对象
- 描述：（可选项）起点信息，**若不传则已当前位置为起点**
- 内部字段：

```js
{
    lon:         //数字类型；起点经度
    lat:         //数字类型；起点纬度
}
```

end：

- 类型：JSON 对象
- 描述：终点信息
- 内部字段：

```js
{
    lon:         //数字类型；终点经度
    lat:         //数字类型；终点纬度
}
```

mode：

- 类型：字符串
- 默认值：driving
- 描述：导航路线类型，取值范围如下：
	- driving：驾车
	- transit：公交
	- walking：步行

##示例代码

```js
var navigator = api.require('navigator');
navigator.gMapNavigation({
    start: {
		lon: 112.47723797622677, 
		lat: 34.556480000000015 
    },
    end: {
			lon: 111.57062599999995,
			lat: 33.784214
    },
    mode: 'driving'
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**appleNavigation**<div id="a5"></div>

打开苹果自带地图并开始导航

appleNavigation({params})

##params

start：

- 类型：JSON 对象
- 描述：（可选项）起点信息，**若不传 则以当前位置为起点**
- 内部字段：

```js
{
        lon: ,        //数字类型；起点经度
        lat: ,        //数字类型；起点纬度
        name:         //（可选项）字符串类型；起点名；默认：起点
}
```

end：

- 类型：JSON 对象
- 描述：终点信息
- 内部字段：

```js
{
        lon:  ,       //数字类型；终点经度
        lat:   ,      //数字类型；终点纬度
        name:         //（可选项）字符串类型；起点名；默认：起点
}
```

mode：

- 类型：字符串
- 默认值：driving
- 描述：导航路线类型，取值范围如下：
	- driving：驾车
	- transit：公交
	- walking：步行

##示例代码

```js
var navigator = api.require('navigator');
navigator.appleNavigation({
    start: {
		lon: 112.47723797622677, 
		lat: 34.556480000000015,
		name: '起点'
    },
    end: {
		lon: 111.57062599999995, 
		lat: 33.784214 ,
		name: '终点'
    },
    mode: 'driving'
});
```

##可用性

iOS系统

可提供的1.0.0及更高版本

</div>