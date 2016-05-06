/*
Title: aMapNavigation
Description: aMapNavigation
*/

<p style="color: #ccc;margin-bottom: 30px;">来自于：开发者</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>
<div id="method-content">

<div class="outline">

[start](#a1)

[close](#a2)

</div>

#**概述**

aMapNavigation 模块封装了高德导航的sdk，支持语音导航功能。用户可自行算路策略类型。开发者只需输入起点终点经纬度即可轻松集成高德导航功能，本模块是由第三方模块开发者提供，使用本模块需在线云编译安装包。

**在集成此模块之前需先配置 config 文件。在 config 里添加如下字段：**

- 名称：aMap
- 参数：android_api_key、ios_api_key
- 备注：同一个 App 需要同时支持 iOS 和 Android 平台，必须单独申请各自的 apiKey，并同时配置在 config 文件中
- 配置示例:

```xml
  <feature name="aMapNavigation">
    <param name="android_api_key" value="f7Is0dWLom2q6rV3ZfFPZ1aa" />
    <param name="ios_api_key" value="81qz3dBYB5q2nGji4IYrawr1" />
  </feature>
```

- 字段描述:

    **android_api_key**：在高德地图开放平台申请的 Android 端 AK

    **ios_api_key**：在高德地图开放平台申请的 IOS 端 AK


#**start**<div id="a1"></div>

开始导航

start({params}, callback(ret, err))

##params

start：

- 类型：JSON 对象
- 描述：起点信息
- 内部字段：

```js
{
	lon：  //数字类型；起点经度
	lat：  //数字类型；起点纬度
}
```

wayPoint：

- 类型：数组
- 描述：（可选项）途经点位置信息，当 type 为 walk 时本参数无效
- 内部字段：

```js
[{
	lon：   //数字类型；起点经度
	lat：   //数字类型；起点纬度
}]
```

end：

- 类型：JSON 对象
- 描述：终点信息
- 内部字段：

```
{
   lon：  //数字类型；起点经度
   lat：  //数字类型；起点纬度
}
```

type:

- 类型：字符串
- 描述：（可选项）导航路线类型
- 默认值：drive
- 取值范围：
    - drive：驾驶
	- walk：步行

strategy：

- 类型：字符串
- 描述：（可选项）算路策略，仅当 type 为 drive 时有效
- 默认值：fast
- 取值范围：
    - fast：速度优先
	- fee：费用优先
	- distance：距离优先
	- highway：普通路优先（不走快速路、高速路）
	- jam：时间优先，躲避拥堵
	- feeJam：躲避拥堵且不走收费道路
	- multipleRoutes：多路径算路（IOS 平台不支持本字段）
	
mode：

- 类型：字符串
- 描述：（可选项）导航模式
- 默认值：GPS
- 取值范围：
    - GPS：GPS实时导航
	- emulator：模拟导航

styles：

- 类型：JSON 对象
- 描述：（可选项）模块各部分的样式
- 内部字段：

```js
{
		image: {            //（可选项）JSON对象；标注图标配置
			start: ,        //（可选项）字符串类型；起点图标路径，要求本地路径（fs://、widget://），若不传则显示公用的图标
			end: ,          //（可选项）字符串类型；终点图标路径，要求本地路径（fs://、widget://），若不传则显示公用的 图标
			way: ,          //（可选项）字符串类型；途经点图标路径，要求本地路径（fs://、widget://），若不传则显示公用的图标
			camera:         //（可选项）字符串类型；摄像头图标（只适用于驾车导航）路径，要求本地路径（fs://、widget://），若不传则显示公用的图标
		},
		preference: {       //（可选项）JSON对象；偏好设置
		    night: false,   //（可选项）布尔类型；是否显示黑夜模式；默认：false
		    compass: false, //（可选项）布尔类型；是否显示指南针；默认：false
		    crossImg: false,//（可选项）布尔类型；是否显示路口放大图，只适用于驾车导航；默认：false
		    degree: 30,     //（可选项）数字类型；地图倾角大小，范围[0,60]，大于40会显示蓝天；默认：30
		    yawReCal: false,//（可选项）数字类型；偏航时是否重新计算路径；默认：false
		    alwaysBright: , //（可选项）数字类型；导航状态下屏幕是否一直开启；默认：false
		    jamReCal: false,//（可选项）数字类型；前方拥堵时是否重新计算路径，暂仅支持Android平台；默认：false
		    allowsBackgroundLocationUpdates: ''  //（可选项）布尔类型；是否允许后台定位，暂仅支持 IOS 平台且只在iOS 9.0及之后起作用；默认：false，为 true 时必须保证 conifg.xml 文件内把后台定位和后台音频播放打开，否则会异常，具体操作见 config.xml 文件配置文档	    }
}
```	

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```
{
	eventType: '',        //字符串类型；导航事件，取值范围：
	                      //calculateSuc  路径规划成功
	                      //calculateFai  路径规划失败
	                      //naviFai       导航发生错误
				          //naviStart     导航页面推出并开始导航
			              //naviEnd       达到目的地导航结束
			              //naviClose     用户关闭导航页面
	routeInfo: {          //JSON对象；导航的路线信息，仅当 eventType 为 calculateSuc 时有值
       length: ,          //数字类型；导航路径总长度（单位：米）
       time: ,            //数字类型；导航路径所需要的时间（单位：秒）
       segmentCount: ,    //数字类型；导航路线上分段的总数
       trafficLightCount:,//数字类型；导航路线上红绿灯的总数
       tollCost:          //数字类型；导航路线的花费金额（单位：元）
	}
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
	 code:      //		数字类型；错误码，取值范围如下：
				//2 	网络超时或网络失败
				//3 	起点错误
				//4 	协议解析错误
				//6 	终点错误
				//10 	起点没有找到道路
				//11 	没有找到通向终点的道路
				//12 	没有找到通向途经点的道路
				//13 	路径长度超过限制
				//14 	其他错误
}
```

##示例代码

```js
var aMapNavigation = api.require('aMapNavigation');
aMapNavigation.start({
    start: { 
		lon: 112.47723797622677, 
		lat: 34.556480000000015 
    },
	wayPoint: [
	   { 
		lon: 109.77539000000002, 
		lat: 33.43144 
       }
    ],
    end: { 
		lon: 111.57062599999995, 
		lat: 33.784214 
    },
    type: 'drive',
    strategy: 'fast',
    mode: 'GPS',
    styles: {
       image: {            
			start: 'fs://nav/start.png',        
			end: 'fs://nav/end.png',          
			way: 'fs://nav/way.png',          
			camera: 'fs://nav/camera.png'        
		},
		preference: {       
		    night: false,   
		    compass: false, 
		    crossImg: false,
		    degree: 30,       
		    yawReCal: false,
		    jamReCal: false,
		    alwaysBright: false
		}
    }
}, function(ret, err){		
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

#**close**<div id="a2"></div>

关闭导航

close({params}, callback(ret, err))


##示例代码

```js
var aMapNavigation = api.require('aMapNavigation');
aMapNavigation.close();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本