/*
Title: baiduNavigation
Description: baiduNavigation
*/

<p style="color: #ccc;margin-bottom: 30px;">来自于：开发者</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">

[start](#a1)

</div>

#**概述**

baiduNavigation 模块封装了百度导航的 sdk，支持语音导航功能。用户可自行选择路线类型。开发者只需输入起点终点经纬度即可轻松集成百度导航功能，本模块是由第三方模块开发者提供，使用本模块需在线云编译安装包。

在集成此模块之前需先配置config文件。在config里添加如下字段：

```js
名称：baiduNavigation
参数：android_api_key、ios_api_key
描述：百度开放平台的安全码获取需要区分移动平台，意味着如果你的同一个App需要同时支持IOS和Android平台，那么，您必须为这两个平台单独申请apiKey，即同一个App申请两个apiKey，并将这两个apiKey同时配置在config文件中。	
```

配置示例：

```js
<feature name="baiduNavigation">
	<param name="android_api_key" value="2kyNa3maO5mXcASnUe5EwVoM" />
	<param name="ios_api_key" value="IvbnWLuuTnbmjOOg17zpbe0O" />
</feature>
```

字段描述：

```js
1、android_api_key：android版本的apiKey
2、ios_api_key：Ios版本的apiKey
```

详情参考[百度开放平台接入指南](http://docs.apicloud.com/APICloud/%E5%BC%80%E6%94%BE%E5%B9%B3%E5%8F%B0%E6%8E%A5%E5%85%A5%E6%8C%87%E5%8D%97/baidu)文档，与baiduMap配置相似。


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
    position: {      //（可选项）JSON对象；起点经纬度（百度坐标系），可与 address 配合不传
	   lon: ,        //数字类型；起点经度
	   lat:          //数字类型；起点纬度
	} ,
    title: ,         //（可选项）字符串类型；起点描述信息
    address:         //（可选项）字符串类型；起点地址信息，可与 position 配合不传
}
```

goBy：

- 类型：数组
- 描述：（可选项）途经点位置信息，可输入1-3个途经点
- 内部字段：

```js
[{
	position: {     //（可选项）JSON对象；途经点经纬度（百度坐标系），可与 address 配合不传
	   lon: ,       //数字类型；途经点经度
	   lat:         //数字类型；途经点纬度
	},
    title:  ,       //（可选项）字符串类型；途经点描述信息
    address:        //（可选项）字符串类型；途经点地址信息，可与 position 配合不传
}]
```

end：

- 类型：JSON 对象
- 描述：终点信息
- 内部字段：


```js
{
    position: {      //（可选项）JSON对象；终点经纬度（百度坐标系），可与 address 配合不传
	   lon: ,        //数字类型；终点经度
	   lat:          //数字类型；终点纬度
	} ,
    title: ,         //（可选项）字符串类型；终点描述信息
    address:         //（可选项）字符串类型；终点地址信息，可与 position 配合不传
}
```

routeMode：

- 类型：字符串
- 描述：导航路线类型，取值范围见[路线类型](!Constant)，可为空
- 默认值：recommend
- 取值范围：
	- ###ios专用类型（对android无效）
	- recommend :           //推荐
	- highway   :           //高速优先
	- noHighway :           //少走高速
	- ###android专用类型（对ios无效）
	- min_time	:	        //最短时间
	- min_dist	:	        //最短距离
	- min_toll	:	        //最少收费
	- avoid_trafficJam	:	//躲避拥堵

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```
{
	status:         //布尔类型：导航成功状态值，true|false
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
	msg: ,      //字符串类型；错误描述
	code:       //数字类型；错误码，取值范围如下：
	            //###ios
				//- 1	:获取地理位置失败
				//- 2	:定位服务未开启
				//- 3	:线路取消
				//- 4	:退出导航
				//- 5	:退出导航声明页面
				//###android
				//- 1	:验证权限失败
				//- 2	:导航引擎初始化失败
				//- 3	:导航失败
				//- 4	:退出导航界面
}
```

##示例代码

```js
var baiduNavigation = api.require('baiduNavigation');
baiduNavigation.start({
    start: { // 起点信息.
        position: { // 经纬度，与address配合可为空
			lon: 112.47723797622677, // 经度.
			lat: 34.556480000000015 // 纬度.
        },
        title: "中国四大石窟之一", // 描述信息
        address: "龙门石窟" // 地址信息，与position配合为空
    },
	goBy: [{ // 途经点位置信息.
        position: { // 经纬度，与address配合可为空
		lon: 109.77539000000002, // 经度
		lat: 33.43144 // 纬度.
        },
        title: "释源", // 描述信息
        address: "白马寺" // 地址信息，与position配合为空
    }],
    end: { // 终点信息.
        position: { // 经纬度，与address配合可为空
		lon: 111.57062599999995, // 经度
		lat: 33.784214 // 纬度
        },
        title: "龙蛇之窟", // 描述信息
        address: "鸡冠洞" // 地址信息，与position配合为空
    }
}, function(ret, err){
	if(ret.status){
		api.alert({
            title: "提示",
			msg:'导航成功'
        });
    }else{
        var msg = "未知错误";
        if(1 == err.code){
            msg = "获取地理位置失败";
        }
        if(2 == err.code){
            msg = "定位服务未开启";
        }
        if(3 == err.code){
            msg = "线路取消";
        }
        if(4 == err.code){
            msg = "退出导航";
        }
        if(5 == err.code){
            msg = "退出导航声明页面";
        }
        api.alert({
            title: "导航出错",
            msg: msg
        });
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本